---
title: Pubblicare dati da Excel a MDS (Componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 89fce454-a816-4b33-a26a-d1b9741d269b
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ffb122b96182b1079c95adf13d26c9a4949f6ddf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "65478799"
---
# <a name="publish-data-from-excel-to-mds-mds-add-in-for-excel"></a>Pubblicare dati da Excel in MDS (componente aggiuntivo MDS per Excel)
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]è possibile pubblicare i dati nel repository MDS se dopo aver usato Excel si vuole salvare le modifiche perché altri utenti possano accedervi.  
  
> [!NOTE]
>  -   Quando si pubblicano le modifiche, vengono eliminati i commenti sulle celle gestite da MDS.  
> -   Una formula non è supportata in una cella gestita da MDS. Una formula in una cella gestita da MDS viene gestita come valore di testo.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
-   Il foglio di lavoro attivo deve contenere dati gestiti da MDS ed è necessario avere apportato modifiche o aggiunte ai dati gestiti da MDS.  
  
-   Se si aggiungono membri, non è necessario specificare un valore **Code** se i codici per l'entità vengono generati automaticamente. Per ulteriori informazioni, vedere [creazione automatica di codice &#40;Master Data Services&#41;](../automatic-code-creation-master-data-services.md).  
  
### <a name="to-publish-data-to-the-mds-repository"></a>Per pubblicare dati al repository MDS  
  
1.  Nel gruppo **Pubblica e convalida** fare clic su **Pubblica**.  
  
2.  Facoltativo. Se viene visualizzata la finestra di dialogo **Pubblicazione e annotazione** , scegliere di condividere la stessa annotazione (commento) per tutti gli aggiornamenti o annotare individualmente ogni modifica.  
  
3.  Facoltativo. Selezionare la casella di controllo **Non visualizzare più questa finestra di dialogo** . È possibile mostrare sempre la finestra di dialogo in futuro scegliendo **Impostazioni** e selezionando la finestra di dialogo **Mostra la finestra di dialogo Pubblicazione e annotazione durante la pubblicazione** .  
  
4.  Fare clic su **Pubblica**.  
  
> [!NOTE]  
>  Se si aggiungono i nuovi membri (righe) al foglio di lavoro e non è possibile pubblicarli correttamente nel repository MDS, è possibile che non si disponga dell'autorizzazione **Update** per tutti gli attributi nel foglio di lavoro. Nella scheda **Verifica** nel gruppo **Modifiche** fare clic su **Rimuovi protezione foglio** e tentare di nuovo la pubblicazione.  
  
## <a name="next-steps"></a>Passaggi successivi  
 [Applicare le regole di business &#40;componente aggiuntivo MDS per Excel&#41;](apply-business-rules-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Vedi anche  
 [Pubblicazione dei dati &#40;Componente aggiuntivo MDS per Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)   
 [Convalida dei dati &#40;componente aggiuntivo MDS per Excel&#41;](validating-data-mds-add-in-for-excel.md)  
  
  
