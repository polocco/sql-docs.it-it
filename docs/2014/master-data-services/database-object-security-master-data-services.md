---
title: Sicurezza di oggetti di database (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], object security
- security [Master Data Services], database objects
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9713f615a190beee5054ee55471e0db387a8a9e7
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971641"
---
# <a name="database-object-security-master-data-services"></a>Sicurezza di oggetti di database (Master Data Services)
  Nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] i dati vengono archiviati in più tabelle di database e sono visibili tramite viste. Le informazioni eventualmente protette nell'applicazione Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] sono visibili agli utenti che dispongono dell'accesso al database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 In particolare è possibile che informazioni relative allo stipendio dei dipendenti siano contenute in un modello Employee o che informazioni finanziarie sulla società siano incluse in un modello Account. È possibile negare a un utente l'accesso a questi modelli nell'interfaccia utente di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . I dati, tuttavia, saranno visibili agli utenti con accesso al database.  
  
 È possibile concedere autorizzazioni a oggetti di database per rendere disponibili dati specifici agli utenti. Per altre informazioni sulla concessione delle autorizzazioni, vedere [GRANT - autorizzazioni per oggetti &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql). Per altre informazioni sulla sicurezza del server SQL, vedere [Sicurezza di SQL Server](../relational-databases/security/securing-sql-server.md).  
  
 Per le attività seguenti viene richiesto l'accesso al database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] :  
  
-   [Gestione temporanea dei dati](#Staging)  
  
-   [Convalida dei dati rispetto a regole business](#rules)  
  
-   [Eliminazione di versioni](#Versions)  
  
-   [Applicazione immediata di autorizzazioni per membri della gerarchia](#Hierarchy)  
  
-   [Modifica dell'account amministratore di sistema](#SysAdmin)  
  
-   [Configurazione di impostazioni di sistema](#SysSettings)  
  
##  <a name="staging-data"></a><a name="Staging"></a> Dati di gestione temporanea  
 Nella tabella seguente, in ogni entità a protezione diretta la parola "name" fa parte del nome. Viene indicato il nome della tabella di staging specificato quando viene creata un'entità. Per ulteriori informazioni, vedere [importazione dati &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
|Azione|Entità a protezione diretta|Autorizzazioni|  
|------------|----------------|-----------------|  
|Caricare membri foglia e i relativi attributi nella tabella di staging.|stg.name_Leaf|Obbligatoria: INSERT<br /><br /> Facoltative: SELECT e UPDATE|  
|Caricare i dati dalla tabella di staging Foglia nelle tabelle di database MDS appropriate.|stg.udp_name_Leaf|EXECUTE|  
|Caricare membri consolidati e i relativi attributi nella tabella di staging.|stg.name_Consolidated|Obbligatoria: INSERT<br /><br /> Facoltative: SELECT e UPDATE|  
|Caricare i dati dalla tabella di staging Consolidata nelle tabelle di database MDS appropriate.|stg.udp_name_Consolidated|EXECUTE|  
|Caricare le relazioni foglia e membri consolidati tra loro in una gerarchia esplicita nella tabella di staging.|stg.name_Relationship|Obbligatoria: INSERT<br /><br /> Facoltative: SELECT e UPDATE|  
|Caricare i dati dalla tabella di staging Relazione nelle tabelle di database MDS appropriate.|stg.udp_name_Relationship|EXECUTE|  
|Visualizzare gli errori che si verificati quando i dati delle tabelle di staging sono stati inseriti nelle tabelle di database MDS.|stg.udp_name_Relationship|SELECT|  
  
 Per altre informazioni, vedere [Importazione dati &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
##  <a name="validating-data-against-business-rules"></a><a name="rules"></a>Convalida dei dati rispetto a regole business  
  
|Azione|Entità a protezione diretta|Autorizzazioni|  
|------------|---------------|-----------------|  
|Convalidare una versione di dati rispetto a regole business|mdm.udpValidateModel|EXECUTE|  
  
 Per altre informazioni, vedere [Stored procedure di convalida &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).  
  
##  <a name="deleting-versions"></a><a name="Versions"></a>Eliminazione di versioni  
  
|Azione|Entità a protezione diretta|Autorizzazioni|  
|------------|----------------|-----------------|  
|Determinare l'ID della versione che si desidera eliminare|mdm.viw_SYSTEM_SCHEMA_VERSION|SELECT|  
|Eliminare una versione di un modello|mdm.udpVersionDelete|EXECUTE|  
  
 Per altre informazioni, vedere [Eliminare una versione &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-version-master-data-services.md).  
  
##  <a name="immediately-applying-hierarchy-member-permissions"></a><a name="Hierarchy"></a>Applicazione immediata di autorizzazioni membri gerarchia  
  
|Azione|Entità a protezione diretta|Autorizzazioni|  
|------------|----------------|-----------------|  
|Applicare immediatamente autorizzazioni per membri|mdm.udpSecurityMemberProcessRebuildModel|EXECUTE|  
  
 Per altre informazioni, vedere [Applicare immediatamente autorizzazioni membri &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
##  <a name="changing-the-system-administrator-account"></a><a name="SysAdmin"></a>Modifica dell'account amministratore di sistema  
  
|Azione|Entità a protezione diretta|Autorizzazioni|  
|------------|----------------|-----------------|  
|Determinare il SID del nuovo amministratore|mdm.tblUser|SELECT|  
|Modificare l'account amministratore di sistema|mdm.udpSecuritySetAdministrator|EXECUTE|  
  
 Per ulteriori informazioni, vedere [modificare l'account amministratore di sistema &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
##  <a name="configuring-system-settings"></a><a name="SysSettings"></a>Configurazione delle impostazioni di sistema  
 È possibile configurare alcune impostazioni di sistema per controllare il comportamento in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Queste impostazioni possono essere modificate in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] oppure, se si dispone dell'autorizzazione di accesso UPDATE, direttamente nella tabella di database mdm.tblSystemSetting. Per altre informazioni, vedere [Impostazioni di sistema &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza &#40;Master Data Services&#41;](../../2014/master-data-services/security-master-data-services.md)  
  
  
