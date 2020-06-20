---
title: Panoramica degli attributi personalizzati dell'integrazione con CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- custom attributes [CLR integration]
- attributes [CLR integration]
- common language runtime [SQL Server], attributes
- database objects [CLR integration], custom attributes
- building database objects [CLR integration], custom attributes
ms.assetid: ecf5c097-0972-48e2-a9c0-b695b7dd2820
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 43db9f034a759e9c041f5cc6ab95baa5af4d7353
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933459"
---
# <a name="overview-of-clr-integration-custom-attributes"></a>Panoramica degli attributi personalizzati dell'integrazione con CLR
  Common Language Runtime (CLR) di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] consente l'utilizzo di parole chiave descrittive, chiamate attributi. Questi attributi forniscono informazioni aggiuntive per molti elementi quali metodi e classi. Gli attributi vengono salvati nell'assembly con i metadati dell'oggetto e possono essere utilizzati per descrivere il codice ad altri strumenti di sviluppo o per influire sul comportamento in fase di esecuzione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Quando si registra una routine CLR con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deriva un set di proprietà sulla routine. Queste proprietà della routine determinano le funzionalità della routine, incluso se la routine può essere indicizzata. Impostando ad esempio la proprietà `DataAccess` su `DataAccessKind.Read` sarà possibile accedere ai dati dalle tabelle utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in una funzione CLR. Nell'esempio seguente viene illustrato un caso semplice in cui la `DataAccess` proprietà è impostata in modo da facilitare l'accesso ai dati da una tabella utente **Tabella1**.  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public partial class UserDefinedFunctions  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static string func1()  
    {  
        // Open a connection and create a command  
        SqlConnection conn = new SqlConnection("context connection = true");  
        conn.Open();  
        SqlCommand cmd = conn.CreateCommand();  
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10";  
        // where table1 is a user table  
        // Execute this command   
        SqlDataReader rd = cmd.ExecuteReader();  
        // Set string ret_val to str_val returned from the query  
        string ret_val = rd.GetValue(0).ToString();  
        rd.Close();  
        return ret_val;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public partial Class UserDefinedFunctions  
    <SqlFunction(DataAccess = DataAccessKind.Read)> _   
    Public Shared Function func1() As String  
        ' Open a connection and create a command  
        Dim conn As SqlConnection = New SqlConnection("context connection = true")   
        conn.Open()  
        Dim cmd As SqlCommand =  conn.CreateCommand()   
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10"  
        ' where table1 is a user table  
        ' Execute this command   
        Dim rd As SqlDataReader =  cmd.ExecuteReader()   
        ' Set string ret_val to str_val returned from the query  
        Dim ret_val As String =  rd.GetValue(0).ToString()   
        rd.Close()  
        Return ret_val  
    End Function  
End Class  
```  
  
 Per le routine [!INCLUDE[tsql](../../includes/tsql-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deriva le proprietà della routine direttamente dalla definizione di routine. Per le routine CLR, il server non analizza il corpo della routine per derivare queste proprietà. È possibile invece utilizzare gli attributi personalizzati per classi e membri della classe implementati in un linguaggio di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
 Gli attributi personalizzati necessari per routine CLR, tipi definiti dall'utente e aggregazioni vengono definiti nello spazio dei nomi `Microsoft.SqlServer.Server`.  
  
## <a name="see-also"></a>Vedere anche  
 [Attributi personalizzati per routine CLR](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)  
  
  
