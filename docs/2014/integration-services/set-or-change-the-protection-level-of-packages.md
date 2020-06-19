---
title: Impostare o modificare il livello di protezione dei pacchetti | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
author: janinezhang
ms.author: janinez
ms.openlocfilehash: bcb8f4da5f39647665b3f07355ea8eed2506cda5
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963411"
---
# <a name="set-or-change-the-protection-level-of-packages"></a>Impostazione o modifica del livello di protezione dei pacchetti
  Per controllare l'accesso al contenuto dei pacchetti e ai valori sensibili contenuti, ad esempio password, impostare il valore della proprietà `ProtectionLevel`. Per poter compilare il progetto, ai pacchetti contenuti in un progetto deve essere assegnato lo stesso livello di protezione del progetto. Se si modifica l'impostazione della proprietà `ProtectionLevel` nel progetto, è necessario aggiornare manualmente l'impostazione delle proprietà per i pacchetti.  
  
 Per informazioni su come determinare le `ProtectionLevel` impostazioni appropriate per i pacchetti in fasi diverse del ciclo di vita del pacchetto, vedere [controllo di accesso per dati sensibili nei pacchetti](security/access-control-for-sensitive-data-in-packages.md). Per informazioni generali sulle funzionalità di sicurezza in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], vedere [Panoramica della sicurezza &#40;Integration Services&#41;](security/security-overview-integration-services.md).  
  
 Le procedure presenti in questo argomento descrivono come utilizzare [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] o l'utilità della riga di comando dtutil per modificare la proprietà `ProtectionLevel`.  
  
> [!NOTE]  
>  Oltre alle procedure di questo argomento, è in genere possibile impostare o modificare la proprietà `ProtectionLevel` di un pacchetto quando si importa o esporta il pacchetto. È inoltre possibile modificare la proprietà [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] di un pacchetto quando si utilizza l'importazione e l'esportazione guidata di `ProtectionLevel` per salvare un pacchetto.  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a>Per impostare o modificare il livello di protezione di un pacchetto in SQL Server Data Tools  
  
1.  Esaminare i valori disponibili per la `ProtectionLevel` proprietà nell'argomento [impostazione del livello di protezione dei pacchetti](security/access-control-for-sensitive-data-in-packages.md)e determinare il valore appropriato per il pacchetto.  
  
2.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenente il pacchetto.  
  
3.  Aprire il pacchetto nella finestra di progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
4.  Se nella finestra Proprietà non sono riportate le proprietà del pacchetto, fare clic sull'area di progettazione.  
  
5.  Nella Finestra Proprietà, nel gruppo di **sicurezza** , selezionare il valore appropriato per la `ProtectionLevel` Proprietà.  
  
     Se si seleziona un livello di protezione che richiede una password, immettere la password come valore della proprietà **PackagePassword** .  
  
6.  Per salvare il pacchetto modificato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a>Per impostare o modificare il livello di protezione dei pacchetti dal prompt dei comandi  
  
1.  Esaminare i valori disponibili per la `ProtectionLevel` proprietà nell'argomento [impostazione del livello di protezione dei pacchetti](security/access-control-for-sensitive-data-in-packages.md)e determinare il valore appropriato per il pacchetto.  
  
2.  Esaminare i mapping per l' `Encrypt` opzione nell'argomento [Utilità dtutil](dtutil-utility.md)e determinare l'intero appropriato da utilizzare come valore della `ProtectionLevel` proprietà selezionata.  
  
3.  Aprire una finestra del prompt dei comandi.  
  
4.  Al prompt dei comandi, passare alla cartella contenente il pacchetto o i pacchetti per cui si desidera impostare la proprietà `ProtectionLevel`.  
  
     Negli esempi di sintassi illustrati nel passaggio seguente si presuppone che questa cartella sia la cartella corrente.  
  
5.  Impostare o modificare il livello di protezione del pacchetto o dei pacchetti utilizzando un comando simile a quello degli esempi seguenti:  
  
    -   Il comando seguente imposta la proprietà `ProtectionLevel` di un pacchetto singolo nel file system sul livello 2, "Crittografa tutti i dati sensibili con una password", con la password "strongpassword":  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   Il comando seguente imposta la proprietà `ProtectionLevel` di tutti i pacchetti in una particolare cartella nel file system sul livello 2, "Crittografa tutti i dati sensibili con una password", con la password "strongpassword":  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         Se si utilizza un comando simile in un file batch, immettere il segnaposto del file "% f" come "%% f" nel file batch.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità dtutil](dtutil-utility.md)  
  
  
