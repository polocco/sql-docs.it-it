---
title: Utilizzo di server collegati in SMO | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- linked servers [SQL Server], SMO
ms.assetid: 0ea8837b-2596-4df1-b065-3bb717c9f22c
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c55ef4914c02aca954a15930e754194e5b3419cc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "70148388"
---
# <a name="using-linked-servers-in-smo"></a>Utilizzo di server collegati in SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Un server collegato rappresenta un'origine dati OLE DB in un server remoto. Le origini dati OLE DB remote vengono collegate all'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tramite l'oggetto <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>.  
  
 I server di database remoti possono essere collegati all'istanza [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] corrente di tramite un provider OLE DB. In SMO i server collegati sono rappresentati dall'oggetto <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. La proprietà <xref:Microsoft.SqlServer.Management.Smo.LinkedServer.LinkedServerLogins%2A> fa riferimento a una raccolta di oggetti <xref:Microsoft.SqlServer.Management.Smo.LinkedServerLogin> in cui sono archiviate le credenziali di accesso necessarie per stabilire una connessione con il server collegato.  
  
## <a name="ole-db-providers"></a>Provider OLE DB  
 In SMO i provider OLE DB installati sono rappresentati da una raccolta di oggetti <xref:Microsoft.SqlServer.Management.Smo.OleDbProviderSettings>.  
  
## <a name="example"></a>Esempio  
 Per gli esempi di codice seguenti, è necessario selezionare l'ambiente, il modello e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un progetto Visual C&#35; SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-visual-c"></a>Creazione di un collegamento a un server del provider OLE DB in Visual C#  
 Nell'esempio di codice viene illustrato come creare un collegamento a un'origine dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB eterogenea tramite l'oggetto <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. Specificando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come nome di prodotto, è possibile accedere ai dati nel server collegato tramite il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client, ovvero il provider OLE DB ufficiale per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```csharp  
//Connect to the local, default instance of SQL Server.   
{   
   Server srv = new Server();   
   //Create a linked server.   
   LinkedServer lsrv = default(LinkedServer);   
   lsrv = new LinkedServer(srv, "OLEDBSRV");   
   //When the product name is SQL Server the remaining properties are   
   //not required to be set.   
   lsrv.ProductName = "SQL Server";   
   lsrv.Create();   
}   
```  
  
## <a name="creating-a-link-to-an-ole-db-provider-server-in-powershell"></a>Creazione di un collegamento a un server del provider OLE DB in PowerShell  
 Nell'esempio di codice viene illustrato come creare un collegamento a un'origine dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB eterogenea tramite l'oggetto <xref:Microsoft.SqlServer.Management.Smo.LinkedServer>. Specificando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come nome di prodotto, è possibile accedere ai dati nel server collegato tramite il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client, ovvero il provider OLE DB ufficiale per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```powershell  
#Get a server object which corresponds to the default instance  
$svr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a linked server object which corresponds to an OLEDB type of SQL server product  
$lsvr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.LinkedServer -argumentlist $svr,"OLEDBSRV"  
  
#When the product name is SQL Server the remaining properties are not required to be set.   
$lsvr.ProductName = "SQL Server"  
  
#Create the Database Object  
$lsvr.Create()   
```  
  
  
