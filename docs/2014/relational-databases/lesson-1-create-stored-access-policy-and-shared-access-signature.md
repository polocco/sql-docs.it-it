---
title: Lezione 2. Creare un criterio per il contenitore e generare una chiave di firma di accesso condiviso | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 80bd9c253adfcf1d1a677953fef183d9109534ef
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "75231819"
---
# <a name="lesson-2-create-a-policy-on-container-and-generate-a-shared-access-signature-sas-key"></a>Lezione 2. creare i criteri per il contenitore e generare una chiave di firma di accesso condivisa (SAS, Shared Access Signature)
  In questa lezione, verrà illustrato come creare criteri del contenitore BLOB e generare una chiave SAS.  
  
 I criteri di accesso archiviati forniscono un livello di controllo aggiuntivo sulle firme di accesso condivise sul lato server. Una firma di accesso condivisa è un URI che concede diritti di accesso limitati a contenitori, BLOB, code e tabelle. Quando si utilizza questa nuova funzionalità avanzata, è necessario creare i criteri in un contenitore con diritti di lettura, scrittura ed elenco.  
  
 È possibile creare i criteri e una firma di accesso condivisa utilizzando uno dei metodi seguenti:  
  
-   Operazioni dell'API REST di Azure: [create container](https://msdn.microsoft.com/library/azure/dd179468.aspx), [set Container ACL](https://msdn.microsoft.com/library/azure/dd179391.aspx)e [Get Container ACL](https://msdn.microsoft.com/library/azure/dd179469.aspx).  
  
-   [Metodo CloudBlobContainer. GetSharedAccessSignature](https://docs.microsoft.com/dotnet/api/microsoft.azure.storage.blob.cloudblobcontainer.getsharedaccesssignature) in Azure SDK.  
  
    ```  
  
       string signature = blob.GetSharedAccessSignature(new SharedAccessPolicy()   
        {   
            // Specify the expiration time for the signature.   
            SharedAccessExpiryTime = DateTime.Now.Years(1),   
            // Specify the permissions granted by the signature.    
            Permissions = SharedAccessPermissions.Write | SharedAccessPermissions.Read   
        });  
  
    ```  
  
-   Uno strumento di Azure Explorer di terze parti, ad esempio [Azure Storage Explorer](https://azurestorageexplorer.codeplex.com/).  
  
 **Lezione successiva:**  
  
 [Lezione 3: Creare le credenziali di SQL Server](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
