---
title: Specifica di valori XML come parametri
description: Dimostrazione di come passare i dati XML come parametro a un comando.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 2c4d08b8-fc29-4614-97fa-29c8ff7ca5b3
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: f53811919e6bec8e1d5c5985c303e282ce81ed07
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919997"
---
# <a name="specifying-xml-values-as-parameters"></a>Specifica di valori XML come parametri

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Se una query richiede un parametro il cui valore è una stringa XML, è possibile fornire tale valore con un'istanza del tipo di dati **SqlXml**. L'operazione è semplicissima in quanto le colonne XML in SQL Server accettano valori di parametro esattamente come altri tipi di dati.  
  
## <a name="example"></a>Esempio  
L'applicazione console seguente crea una nuova tabella nel database **AdventureWorks**. La nuova tabella include la colonna **SalesID** e la colonna XML **SalesInfo**.  
  
> [!NOTE]
>  Per impostazione predefinita, il database di esempio **AdventureWorks** non viene installato insieme a SQL Server. Per installarlo, è sufficiente eseguire il programma di installazione di SQL Server.  
  
Nell'esempio viene preparato un oggetto <xref:Microsoft.Data.SqlClient.SqlCommand> per inserire una riga nella nuova tabella. Successivamente, i dati XML per la colonna **SalesInfo** vengono forniti da un file salvato.  
  
Per creare il file necessario per l'esecuzione dell'esempio, creare un nuovo file di testo nella stessa cartella del progetto. Denominare il file MyTestStoreData.xml. Aprire il file nel Blocco note e copiare e incollare il testo seguente:  
  
```xml  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>International Bank</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1970</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>7000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>T1</Internet>  
  <NumberEmployees>2</NumberEmployees>  
</StoreSurvey>  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.Data.SqlClient;  
using System.Xml;  
using System.Data.SqlTypes;  
  
class Class1  
{  
    static void Main()  
    {  
        using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
       {  
        connection.Open();  
        //  Create a sample table (dropping first if it already  
        //  exists.)  
  
        string commandNewTable =   
            "IF EXISTS (SELECT * FROM dbo.sysobjects " +   
            "WHERE id = " +  
                  "object_id(N'[dbo].[XmlDataTypeSample]') " +   
            "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " +   
            "DROP TABLE [dbo].[XmlDataTypeSample];" +   
            "CREATE TABLE [dbo].[XmlDataTypeSample](" +   
            "[SalesID] [int] IDENTITY(1,1) NOT NULL, " +   
            "[SalesInfo] [xml])";  
        SqlCommand commandAdd =   
                   new SqlCommand(commandNewTable, connection);  
        commandAdd.ExecuteNonQuery();  
        string commandText =   
            "INSERT INTO [dbo].[XmlDataTypeSample] " +   
            "([SalesInfo] ) " +   
            "VALUES(@xmlParameter )";  
        SqlCommand command =   
                  new SqlCommand(commandText, connection);  
  
        //  Read the saved XML document as a   
        //  SqlXml-data typed variable.  
        SqlXml newXml =   
            new SqlXml(new XmlTextReader("MyTestStoreData.xml"));  
  
        //  Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml);  
  
        int result = command.ExecuteNonQuery();  
        Console.WriteLine(result + " row was added.");  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,              
        // you can retrieve it from a configuration file.   
        return "Data Source=(local);Integrated Security=true;" +  
        "Initial Catalog=AdventureWorks; ";  
    }  
}  
```  
  
## <a name="next-steps"></a>Passaggi successivi
- <xref:System.Data.SqlTypes.SqlXml>
- [Dati XML in SQL Server](xml-data-sql-server.md)
