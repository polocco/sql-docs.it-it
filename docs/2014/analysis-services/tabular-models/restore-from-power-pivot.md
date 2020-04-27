---
title: Ripristinare da PowerPivot | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f90ea08269e79e57c623af41fc2f0fbc09e2fb42
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66066640"
---
# <a name="restore-from-powerpivot"></a>Ripristina da PowerPivot
  È possibile utilizzare la funzionalità Ripristina da PowerPivot in SQL Server Management Studio per creare un nuovo database modello tabulare in un'istanza di Analysis Services (in esecuzione in modalità tabulare) o eseguire il ripristino in un database esistente da una cartella di lavoro di PowerPivot (con estensione xlsx).  
  
> [!NOTE]  
>  Il modello di progetto Importa da PowerPivot in SQL Server Data Tools offre funzionalità simili. Per ulteriori informazioni, vedere [importazione da PowerPivot &#40;SSAS tabulare&#41;](import-from-power-pivot-ssas-tabular.md).  
  
 Quando si utilizza Ripristina da PowerPivot, si tenga in considerazione quanto riportato di seguito:  
  
-   Per poter utilizzare Ripristina da PowerPivot, è necessario aver eseguito l'accesso come membro del ruolo di amministratori del server per l'istanza di Analysis Services.  
  
-   L'account del servizio dell'istanza di Analysis Services deve disporre di autorizzazioni di lettura per il file della cartella di lavoro da cui eseguire il ripristino.  
  
-   Per impostazione predefinita, quando si ripristina un database da PowerPivot, la proprietà Impostazioni di rappresentazione origine dati del database modello tabulare è impostata sul valore predefinito, tramite cui viene specificato l'account del servizio dell'istanza di Analysis Services. Si consiglia di impostare le credenziali di rappresentazione su un account utente di Windows nelle proprietà del database. Per altre informazioni, vedere [Rappresentazione &#40;SSAS tabulare&#41;](impersonation-ssas-tabular.md).  
  
-   I dati nel modello di dati PowerPivot verranno copiati in un nuovo database modello tabulare o in uno esistente nell'istanza di Analysis Services. Se nella cartella di lavoro di PowerPivot sono contenute tabelle collegate, queste verranno ricreate come tabelle senza un'origine dati, simili a tabelle create utilizzando Incolla in nuova tabella.  
  
### <a name="to-restore-from-powerpivot"></a>Per ripristinare da PowerPivot  
  
1.  In SSMS, nell'istanza Active Directory che si desidera ripristinare, fare clic con il pulsante destro del mouse su **database**, quindi scegliere **Ripristina da PowerPivot**.  
  
2.  Nella finestra di dialogo **Ripristina da PowerPivot** , in **origine ripristino**, in **file di backup**fare clic su **Sfoglia**, quindi selezionare un file con estensione abf o xslx da cui eseguire il ripristino.  
  
3.  In **Destinazione ripristino**in **Ripristina database**digitare un nome per un nuovo database o per uno esistente. Se non si specifica un nome, viene utilizzato quello della cartella di lavoro.  
  
4.  In **Percorso di archiviazione**fare clic su **Sfoglia**, quindi selezionare un percorso per l'archiviazione del database.  
  
5.  Nella casella **Opzioni**lasciare **Includi informazioni di sicurezza** selezionato. Quando si esegue il ripristino da una cartella di lavoro di PowerPivot, questa impostazione non è applicabile.  
  
## <a name="see-also"></a>Vedi anche  
 [Database modello tabulare &#40;SSAS tabulare&#41;](tabular-model-databases-ssas-tabular.md)   
 [Importazione da PowerPivot &#40;SSAS tabulare&#41;](import-from-power-pivot-ssas-tabular.md)  
  
  
