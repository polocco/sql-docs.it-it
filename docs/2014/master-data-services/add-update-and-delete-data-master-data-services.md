---
title: Aggiungere, aggiornare ed eliminare dati (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b6295ead-bd2f-49dd-8756-35c6afb59648
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 2212e7424f22ecca2619ef7215bf94b0dbb62875
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054270"
---
# <a name="add-update-and-delete-data-master-data-services"></a>Aggiungere, aggiornare ed eliminare dati (Master Data Services)
  È possibile aggiungere dati e apportare modifiche ai dati in bulk a un modello in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
 **Prerequisiti**  
  
-   È necessario avere l'autorizzazione per inserire dati nella tabella stg.\<name>_Leaf, stg.\<name>_Consolidated o stg.\<name>_Relationship del database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
-   È necessario avere l'autorizzazione per eseguire la stored procedure stg.udp_\<name>_Leaf, stg.udp\_\<name>_Consolidated o stg.udp\_\<name>_Relationship nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
-   Il modello non deve avere uno stato di **Commit completato**.  
  
 **Per aggiungere, aggiornare ed eliminare dati nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]**  
  
1.  Preparare i membri da importare nella tabella di staging appropriata del database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], ad esempio fornire valori per i campi obbligatori. Per una panoramica delle tabelle di staging, vedere [importazione di dati &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
    -   Per i membri foglia la tabella è stg.\<name>_Leaf, dove \<name> si riferisce all'entità corrispondente. Per informazioni sui campi obbligatori, vedere [Tabella di gestione temporanea dei membri foglia &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md)  
  
    -   Per i membri consolidati la tabella è stg.\<name>_Consolidated. Per informazioni sui campi obbligatori, vedere [Tabella di gestione temporanea di membri consolidati &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
    -   Per spostare la posizione dei membri nelle gerarchie esplicite, la tabella è stg.\<name>_Relationship. Per informazioni sui campi obbligatori, vedere [Tabella di gestione temporanea delle relazioni &#40;Master Data Services&#41;](../../2014/master-data-services/relationship-staging-table-master-data-services.md).  
  
         Per una panoramica sullo stato di trasferimento di membri nelle gerarchie esplicite, vedere [&#40;di importazione dati Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
    -   Usare il valore del campo **ImportType** per specificare che si stanno creando nuovi membri, disattivando membri o eliminando membri. Per altre informazioni sui valori, vedere [Tabella di gestione temporanea dei membri foglia &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-member-staging-table-master-data-services.md) e [Tabella di gestione temporanea di membri consolidati &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md).  
  
         Per una panoramica sulla disattivazione e l'eliminazione di membri, vedere [importazione di dati &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
2.  Aprire [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] e connettersi all'istanza del motore di database per il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
     Per ulteriori informazioni, vedere [SQL Server Management Studio](../ssms/sql-server-management-studio-ssms.md).  
  
3.  Importare dati nelle tabelle di staging usando l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
     Per altre informazioni, vedere [SQL Server Import and Export Wizard](../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
4.  Caricare i dati dalle tabelle di staging nelle tabelle di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], effettuando una delle operazioni seguenti  
  
    -   Eseguire la stored procedure di staging che corrisponde alla tabella di staging in cui spostare i dati.  
  
         Per una panoramica sulle stored procedure di staging e sulle tabelle di staging, vedere [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md). Per altre informazioni sui parametri delle stored procedure di gestione temporanea e un esempio di codice, vedere [Stored procedure di gestione temporanea &#40;Master Data Services&#41;](../../2014/master-data-services/staging-stored-procedure-master-data-services.md).  
  
    -   Usare l'area funzionale **Gestione integrazione** di Gestione dati master.  
  
         Nella pagina **Batch di gestione temporanea** selezionare dall'elenco a discesa il modello al quale si aggiungeranno dati e quindi fare clic su **Avvia batch**. Lo stato dell'elaborazione batch è indicato nel campo **Stato** . Per altre informazioni sugli stati, vedere [Stati di importazione &#40;Master Data Services&#41;](../../2014/master-data-services/import-statuses-master-data-services.md).  
  
         ![Batch di gestione temporanea in Gestione dati master](../../2014/master-data-services/media/mds-staging-batches.png "Batch di gestione temporanea in Gestione dati master")  
  
         Il processo di gestione temporanea viene avviato a intervalli determinati dall'impostazione **Intervallo batch di gestione temporanea** in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Per altre informazioni, vedere [Impostazioni di sistema &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
5.  Visualizzare gli errori che si sono verificati durante la gestione temporanea. Per ulteriori informazioni, vedere [visualizzare gli errori che si verificano durante il processo di gestione temporanea &#40;Master Data Services&#41;e gli](view-errors-that-occur-during-staging-master-data-services.md) [errori del processo di gestione temporanea &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).  
  
6.  Convalidare i dati rispetto a regole di business.  
  
     In Gestione dati master passare all'area funzionale **Visualizzatore** per il modello e quindi applicare le regole di business per convalidare i dati. Per altre informazioni, vedere [Convalidare membri specifici rispetto a regole di business &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md). È anche possibile usare una stored procedure per convalidare i dati. Per altre informazioni, vedere [Stored procedure di convalida &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).  
  
     Quando si caricano dati dalle tabelle di staging, i dati non vengono convalidati automaticamente rispetto alle regole di business. Per altre informazioni sulla convalida e sulla sua esecuzione, vedere [Convalida &#40;Master Data Services&#41;](../../2014/master-data-services/validation-master-data-services.md).  
  
## <a name="see-also"></a>Vedi anche  
 [Importazione dati &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)  
  
  
