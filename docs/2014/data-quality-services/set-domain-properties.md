---
title: Impostare le proprietà di un dominio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dm.domainproperties.f1
ms.assetid: 8a3c88ca-31d6-4f75-9aca-cf027c6d9845
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 38b04dc1e7cf9d6bcb6a098faaffd4d53fb1fac3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "65481092"
---
# <a name="set-domain-properties"></a>Impostare le proprietà di un dominio
  In questo argomento viene descritto come impostare le proprietà di un dominio in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Prerequisiti  
 Per impostare le proprietà per un dominio, è necessario avere creato una Knowledge Base e un dominio.  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
 È necessario disporre del ruolo dqs_kb_editor o dqs_administrator nel database DQS_MAIN per impostare le proprietà in un dominio.  
  
##  <a name="set-domain-properties"></a><a name="Set"></a>Impostare le proprietà del dominio  
  
1.  Impostare le proprietà in un dominio esistente aprendo una Knowledge Base nell'attività Gestione dominio (vedere [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)) e selezionando quindi il dominio appropriato nell'elenco **Dominio** . Per impostazione predefinita, verrà visualizzata la pagina Proprietà dominio.  
  
2.  Impostare le proprietà in un nuovo dominio dopo averlo creato come descritto in [Create a Domain](../../2014/data-quality-services/create-a-domain.md).  
  
3.  Fare clic su **Fine** per completare l'attività di gestione del dominio, come descritto in [Sospensione dell'attività di gestione del dominio](../../2014/data-quality-services/end-the-domain-management-activity.md).  
  
##  <a name="follow-up-after-setting-domain-properties"></a><a name="FollowUp"></a>Completamento: fasi successive all'impostazione delle proprietà del dominio  
 Dopo avere impostato le proprietà di un dominio, è possibile eseguire ulteriori attività di gestione del dominio, quali l'individuazione delle informazioni per aggiungere informazioni al dominio o l'aggiunta di criteri di corrispondenza al dominio. Per altre informazioni, vedere [Eseguire l'individuazione delle informazioni](../../2014/data-quality-services/perform-knowledge-discovery.md), [Gestione di un dominio](../../2014/data-quality-services/managing-a-domain.md) o [Creare criteri di corrispondenza](../../2014/data-quality-services/create-a-matching-policy.md).  
  
##  <a name="domain-properties"></a><a name="Properties"></a>Proprietà del dominio  
  
###  <a name="domain-name-and-description"></a><a name="Name"></a>Nome e descrizione del dominio  
 Dopo la creazione di un dominio è possibile modificarne il nome o la descrizione. Il nome del dominio deve essere univoco per la Knowledge Base. La descrizione può contenere fino a 256 caratteri.  
  
###  <a name="data-type"></a>Tipo di dati <a name="Type"></a>  
 Quando si crea il dominio, selezionare uno dei tipi di dati seguenti per i valori nel dominio: **Stringa** (valore predefinito), **Data**, **Intero**o **Decimale**. Dopo avere creato il dominio, è possibile visualizzare il tipo di dati ma non modificarli. Tramite il tipo di dati selezionato per un dominio viene definito il tipo di dati di origine di cui è possibile eseguire il mapping al dominio. Per altre informazioni sui tipi di dati supportati per ognuno dei quattro tipi di dati del dominio in DQS, vedere [Tipi di dati di SQL Server e SSIS supportati per i domini DQS](../../2014/data-quality-services/supported-sql-server-and-ssis-data-types-for-dqs-domains.md).  
  
###  <a name="use-leading-values"></a><a name="Leading"></a>Usa valori iniziali  
 Selezionare questa casella di controllo per specificare che venga restituito il valore iniziale in un gruppo di sinonimi anziché un valore di cui è sinonimo. Deselezionare **Utilizza valori iniziali** per specificare che ogni valore di sinonimo verrà restituito nella forma corretta e non verrà sostituito dal valore iniziale per il gruppo.  
  
###  <a name="normalize-string"></a><a name="Normalize"></a>Normalizza stringa  
 Se il tipo di dati è **Stringa**, fare clic per ignorare i caratteri speciali nei dati di origine per l'elaborazione della qualità dei dati da parte di DQS. In DQS vengono sostituiti internamente i caratteri speciali con un valore Null o uno spazio quando i dati vengono caricati nel dominio. I due punti, il trattino, il punto, le virgolette doppie o il punto e virgola vengono sostituiti da uno spazio. Le virgolette semplici vengono sostituite da un valore Null. L'utilizzo del valore Null raggruppa le due parti di una stringa.  
  
 Ignorando i caratteri speciali in un valore stringa è possibile aumentare la precisione della corrispondenza. Il punteggio di somiglianza tra due stringhe può essere aumentato sostituendo i caratteri speciali con un valore Null o uno spazio. I segni di punteggiatura o gli altri simboli possono essere facilmente diversi nelle varie stringhe. La sostituzione interna in DQS di caratteri speciali può consentire al punteggio di superare la soglia di corrispondenza minima, facendo sì che due stringhe vengano considerate corrispondenti laddove non lo fossero. Tuttavia, la scelta di ignorare i caratteri speciali può dipendere dal tipo di dati su cui viene eseguita la corrispondenza. Se ad esempio si utilizzano i dati nel sistema di misurazione anglosassone, ignorare le virgolette doppie e le virgolette semplici nei dati del prodotto può comportare falsi positivi se le virgolette doppie stanno per pollici e le virgolette semplici stanno per piedi.  
  
 La normalizzazione viene eseguita quando i dati vengono caricati e indicizzati nelle fasi di elaborazione dei dati delle attività di individuazione, criteri di corrispondenza, progetto corrispondente e progetto di pulizia. Se abilitate, la normalizzazione e la trasformazione delle relazioni basate su termini vengono entrambe eseguite in una fase di pre-elaborazione prima dell'analisi. Vengono eseguite su ogni dominio prima dell'applicazione di qualsiasi algoritmo che calcola la somiglianza tra stringhe. Se è richiesta l'analisi di un dominio composito, essa verrà eseguita prima della normalizzazione e della trasformazione delle relazioni basate su termini, perché l'analisi basata su delimitatore richiede l'utilizzo di simboli. Altre operazioni, quali le regole di dominio e le modifiche ai valori del dominio, verranno eseguite dopo le trasformazioni. I dati risultanti non vengono modificati dalla sostituzione interna in DQS dei caratteri speciali.  
  
###  <a name="format-output-to"></a><a name="Format"></a>Formattare l'output in  
 Selezionare la formattazione che verrà applicata alla restituzione dei valori dei dati nel dominio. La formattazione è specifica del tipo di dati selezionato, come mostrato nell'elenco seguente. Se si seleziona **Nessuno** non verrà applicato alcun formato tra quelli elencati.  
  
-   Per un valore stringa, è possibile specificare di restituire la stringa tutta in maiuscole, tutta in minuscole o solo con l'iniziale maiuscola.  
  
-   Per un valore data, è possibile specificare il formato del giorno, del mese e dell'anno.  
  
-   Per un valore intero, è possibile specificare il tipo di maschera del formato da applicare.  
  
-   Per un valore decimale, è possibile specificare la precisione e il tipo di maschera del formato da applicare.  
  
###  <a name="language"></a><a name="Language"></a>Linguaggio  
 Se il tipo di dati è **Stringa**, selezionare la lingua a cui si desidera associare il dominio per il correttore ortografico. Questa selezione è valida solo per il correttore ortografico perché i relativi risultati dipendono dalla lingua utilizzata. La selezione è valida solo per un singolo dominio con un tipo di dati stringa. La proprietà lingua non riguarda i domini compositi. La lingua per ogni parte di un dominio composito è determinata dal singolo dominio relativo.  
  
 L'inglese è la lingua predefinita. Se la proprietà **Lingua** viene impostata su **Altro** , il correttore ortografico per il dominio viene disabilitato.  
  
> [!TIP]  
>  Se la lingua non è elencata nell'elenco a discesa **Lingua** , è necessario selezionare **Altro**. Ciò garantisce che i duplicati vengano puliti ed eliminati da DQS per i dati della lingua non elencata in base alle informazioni disponibili (regole di dominio, valori di dominio, TBR, regola di corrispondenza) nel dominio.  
  
###  <a name="enable-speller"></a><a name="Speller"></a>Abilita correttore ortografico  
 Se il tipo di dati è **Stringa**, fare clic per abilitare il correttore ortografico DQS per il dominio. Il correttore ortografico funziona solo sui domini con tipo di dati stringa. La casella di controllo **Abilita correttore ortografico** abilita il correttore ortografico solo per il singolo dominio associato alla casella di controllo. La casella di controllo non è valida per un dominio composito.  
  
 Il correttore ortografico propone le correzioni di sintassi e di convalida per i valori nel dominio. Per ulteriori informazioni, vedere [Use the DQS Speller](../../2014/data-quality-services/use-the-dqs-speller.md).  
  
###  <a name="disable-syntax-error-algorithms"></a><a name="Syntax"></a>Disabilita algoritmi di errore sintassi  
 Se il tipo di dati è **Stringa**, selezionare questa opzione per specificare di non individuare gli errori di sintassi nel dominio durante la pulizia. Selezionare questa casella di controllo quando non è importante identificare gli errori di sintassi per il dominio, ad esempio per un numero di serie. Questo controllo è disponibile solo per il tipo di dati stringa. Il controllo degli errori di sintassi non verrà eseguito nei tipi di dati non stringa.  
  
  
