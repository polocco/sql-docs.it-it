---
title: Uso di Posta elettronica database | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- e-mail [SMO]
- Database Mail [SMO]
- mail [SMO]
ms.assetid: 7605390f-b485-48cc-8d97-e364a066067b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2db385919c30037612f00e53b2b990c1a7df0429
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "72781860"
---
# <a name="using-database-mail"></a>Utilizzo di Posta elettronica database
  In SMO il sottosistema Posta elettronica database è rappresentato dall'oggetto <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> a cui fa riferimento la proprietà <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A>. Tramite l'oggetto <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> SMO, è possibile configurare il sottosistema Posta elettronica database e gestire profili e account di posta elettronica. L'oggetto <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> SMO appartiene all'oggetto `Server`, di conseguenza l'ambito degli account di posta elettronica è a livello del server.  
  
## <a name="examples"></a>Esempi  
 Per usare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per ulteriori informazioni, vedere [creare un Visual Basic progetto SMO in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) o [creare un progetto Visual C&#35; SMO in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
 Per i programmi che [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzano posta elettronica database, è necessario includere `Imports` l'istruzione per qualificare lo spazio dei nomi della posta. Inserire l'istruzione dopo le altre istruzioni `Imports`, ma prima di qualsiasi dichiarazione nell'applicazione, ad esempio:  
  
 `Imports Microsoft.SqlServer.Management.Smo`  
  
 `Imports Microsoft.SqlServer.Management.Common`  
  
 `Imports Microsoft.SqlServer.Management.Smo.Mail`  
  
## <a name="creating-a-database-mail-account-by-using-visual-basic"></a>Creazione di un account di Posta elettronica database tramite Visual Basic  
 In questo esempio di codice viene illustrato come creare un account di posta elettronica in SMO. Il sistema Posta elettronica database è rappresentato dall'oggetto <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> e la proprietà <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Server> fa riferimento ad esso. È possibile utilizzare SMO per configurare Posta elettronica database a livello di codice, ma non per inviare o gestire i messaggi di posta elettronica ricevuti.  
  
 VB.NET  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMail1](SMO How to#SMO_VBMail1)]  -->  
  
## <a name="creating-a-database-mail-account-by-using-visual-c"></a>Creazione di un account di Posta elettronica database tramite Visual C#  
 In questo esempio di codice viene illustrato come creare un account di posta elettronica in SMO. Il sistema Posta elettronica database è rappresentato dall'oggetto <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> e la proprietà <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Server> fa riferimento ad esso. È possibile utilizzare SMO per configurare Posta elettronica database a livello di codice, ma non per inviare o gestire i messaggi di posta elettronica ricevuti.  
  
```csharp  
{  
         //Connect to the local, default instance of SQL Server.  
         Server srv = default(Server);   
           srv = new Server();   
           //Define the Database Mail service with a SqlMail object variable   
           //and reference it using the Server Mail property.   
           SqlMail sm;   
           sm = srv.Mail;   
           //Define and create a mail account by supplying the Database Mail  
           //service, name, description, display name, and email address  
           //arguments in the constructor.   
           MailAccount a = default(MailAccount);   
           a = new MailAccount(sm, "AdventureWorks2012 Administrator", "AdventureWorks2012 Automated Mailer", "Mail account for administrative e-mail.", "dba@Adventure-Works.com");   
           a.Create();    
}  
```  
  
## <a name="creating-a-database-mail-account-by-using-powershell"></a>Creazione di un account di Posta elettronica database tramite PowerShell  
 In questo esempio di codice viene illustrato come creare un account di posta elettronica in SMO. Il sistema Posta elettronica database è rappresentato dall'oggetto <xref:Microsoft.SqlServer.Management.Smo.Mail.SqlMail> e la proprietà <xref:Microsoft.SqlServer.Management.Smo.Server.Mail%2A> dell'oggetto <xref:Microsoft.SqlServer.Management.Smo.Server> fa riferimento ad esso. È possibile utilizzare SMO per configurare Posta elettronica database a livello di codice, ma non per inviare o gestire i messaggi di posta elettronica ricevuti.
  
```powershell  
#Connect to the local, default instance of SQL Server.  
  
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Define the Database Mail; reference it using the Server Mail property.  
$sm = $srv.Mail  
  
#Define and create a mail account by supplying the Database Mail service,  
#name, description, display name, and email address arguments in the constructor.  
$a = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Mail.MailAccount -ArgumentList $sm, `  
"Adventure Works Administrator", "Adventure Works Automated Mailer",`  
 "Mail account for administrative e-mail.", "dba@Adventure-Works.com"  
$a.Create()  
```  
