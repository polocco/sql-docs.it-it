---
title: Stored procedure di convalida (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 89e0b57501eb948d0c67a6dc0a055051b7d19b18
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "65481335"
---
# <a name="validation-stored-procedure-master-data-services"></a>Stored procedure di convalida (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]convalidare una versione per applicare regole di business a tutti i membri nella versione del modello.  
  
 In questo argomento viene illustrato come usare la stored procedure **mdm.udpValidateModel** per convalidare i dati. Se si è un amministratore nell'applicazione Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , è possibile eseguire la convalida nell'interfaccia utente. Per altre informazioni, vedere [Convalidare una versione usando le regole di business &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).  
  
> [!NOTE]  
>  Se si richiama la convalida prima del completamento del processo di gestione temporanea, i membri che non hanno completato la gestione temporanea non saranno convalidati.  
  
## <a name="example"></a>Esempio  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## <a name="parameters"></a>Parametri  
 I parametri di questa procedura sono i seguenti:  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|UserID|L'ID utente.|  
|Model_ID|L'ID modello.|  
|Version_ID|L'ID versione.|  
  
## <a name="see-also"></a>Vedi anche  
 [Importazione dati &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Convalidare una versione usando le regole di business &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md)  
  
  
