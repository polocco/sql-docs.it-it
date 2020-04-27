---
title: 'Procedura: Debug di assembly personalizzati | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services], debugging
- debugging custom assemblies [Reporting Services]
- troubleshooting [Reporting Services], custom assemblies
ms.assetid: 3a3215b3-548c-4474-81ba-3a98dd3912bf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 64a61e044c7ff6efe051eb316cb9f653f0993b68
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63265054"
---
# <a name="how-to-debug-custom-assemblies"></a>Procedura: Eseguire il debug di assembly personalizzati
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] sono disponibili diversi strumenti di debug che consentono di analizzare il codice assembly personalizzato e di individuare gli errori. Per ogni attività specifica è disponibile uno strumento appropriato. In questo esempio viene utilizzato [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)].  
  
 Il modo migliore per progettare, sviluppare e testare assembly personalizzati per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] consiste nel creare una soluzione che contiene sia i report di test che l'assembly personalizzato.  
  
### <a name="to-debug-assemblies-using-a-single-instance-of-visual-studio"></a>Per eseguire il debug di assembly utilizzando un'unica istanza di Visual Studio  
  
1.  Creare un nuovo progetto report utilizzando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
     Quando viene creato un progetto report, in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] viene creata anche una soluzione che lo contenga.  
  
2.  Aggiungere un nuovo progetto Libreria di classi alla soluzione esistente. Verificare che il progetto report venga impostato come progetto di avvio. Per ulteriori informazioni sull'esecuzione di questa operazione, vedere la documentazione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
3.  Selezionare la soluzione in Esplora soluzioni.  
  
4.  Nel menu **Visualizza** fare clic su **Pagine delle proprietà**.  
  
     Viene visualizzata la finestra di dialogo **Pagine delle proprietà** della soluzione.  
  
5.  Nel riquadro sinistro espandere **Proprietà comuni**, se necessario, quindi fare clic su **Dipendenze progetto**. Selezionare il progetto report dall'elenco a discesa **Progetto**. Selezionare il progetto assembly dall'elenco **Dipendente da**.  
  
6.  Scegliere **OK** per salvare le modifiche e chiudere la finestra di dialogo **Pagine delle proprietà**.  
  
7.  In Esplora soluzioni selezionare il progetto assembly personalizzato.  
  
8.  Nel menu **Visualizza** fare clic su **Pagine delle proprietà**.  
  
     Viene visualizzata la finestra di dialogo **Pagine delle proprietà** del progetto.  
  
9. Fare clic sulla scheda **Compilazione** se il progetto attivo è un progetto C# o sulla scheda **Compila** se il progetto è un progetto [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
10. Nella pagina**Compila** compilazione immettere il percorso della cartella Progettazione report. **Build**/ Per impostazione predefinita, il percorso è C:\Programmi\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE) nella casella di testo **Percorso output**. In tal modo verrà compilata e distribuita una versione aggiornata dell'assembly personalizzato direttamente in Progettazione report prima che il report venga eseguito.  
  
11. Dopo avere progettato il report e sviluppato l'assembly personalizzato, impostare i punti di interruzione nel codice assembly personalizzato.  
  
12. Eseguire il report in modalità **DebugLocal** premendo F5. Durante l'esecuzione del report nella finestra popup di anteprima, il debugger rileva tutti i punti di interruzione che corrispondono a codice eseguibile nell'assembly. Utilizzare F11 per passare al codice assembly personalizzato.  
  
### <a name="to-debug-assemblies-using-two-instances-of-visual-studio"></a>Per eseguire il debug di assembly utilizzando due istanze di Visual Studio  
  
1.  Avviare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e aprire il progetto assembly personalizzato.  
  
2.  Compilare il progetto e distribuire l'assembly personalizzato e il file pdb associato in Progettazione report. Per altre informazioni sulla distribuzione, vedere [Distribuzione di un assembly personalizzato](deploying-a-custom-assembly.md).  
  
3.  Aprire un progetto report che utilizza l'assembly personalizzato lasciando il codice assembly personalizzato aperto in un'altra istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
4.  Passare all'istanza di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] contenente il progetto assembly personalizzato e impostare alcuni punti di interruzione nel codice.  
  
5.  Con il progetto assembly personalizzato nella finestra attiva fare clic su **Connetti a processo** dal menu **Debug**.  
  
     Verrà visualizzata la finestra di dialogo **Connetti a processo**.  
  
6.  Nell'elenco di processi selezionare il processo devenv.exe che corrisponde al progetto report e fare clic su **Connetti**.  
  
7.  Definire le espressioni che verranno utilizzate nel report dall'assembly personalizzato e progettare il report.  
  
8.  Dopo avere completato la progettazione del report, fare clic sulla scheda **Anteprima**.  
  
     Il report verrà eseguito. Il codice assembly personalizzato dovrebbe interrompersi in corrispondenza dei punti di interruzione definiti in precedenza.  
  
    > [!NOTE]  
    >  Usando la scheda **Anteprima** le autorizzazioni relative al codice dell'assembly non vengono applicate. Per un test completo, che includa gli errori di sicurezza dall'accesso di codice, avviare il progetto report con l'impostazione di configurazione **DebugLocal**.  
  
9. Esaminare il codice istruzione per istruzione premendo F11 Per ulteriori informazioni sull'esecuzione del debug in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vedere la documentazione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedi anche  
 [Utilizzo di assembly personalizzati con i report](using-custom-assemblies-with-reports.md)  
  
  
