---
title: Partizioni (Analysis Services Dati multidimensionali) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- incremental updates [Analysis Services]
- data sources [Analysis Services], partitions
- data storage [Analysis Services]
- aggregations [Analysis Services], partitions
- OLAP objects [Analysis Services], partitions
- storing data [Analysis Services], partitions
- partitions [Analysis Services], about partitions
- cubes [Analysis Services], partitions
- partitions [Analysis Services]
- remote partitions [Analysis Services]
- measure groups [Analysis Services], partitions
ms.assetid: cd10ad00-468c-4d49-9f8d-873494d04b4f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 86057c14655b3fd2f0322387beb16a4a94717b68
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545263"
---
# <a name="partitions-analysis-services---multidimensional-data"></a>Partizioni (Analysis Services - Dati multidimensionali)
  Una partizione è un contenitore di una parte di dati dei gruppi di misure. Le partizioni non vengono individuate dalle query MDX. Tutte le query riflettono l'intero contenuto del gruppo di misure, indipendentemente dal numero di partizioni definite per esso. Il contenuto dei dati di una partizione è definito dalle associazioni di query della partizione e dall'espressione di sezionamento.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.Partition> semplice è composto da informazioni di base, dalla definizione di sezionamento, dalla progettazione delle aggregazioni e altro. Le informazioni di base includono il nome della partizione, la modalità di archiviazione, la modalità di elaborazione e altro. La definizione di sezionamento è un'espressione MDX che specifica una tupla o un set. La definizione di sezionamento ha le stesse restrizioni della funzione MDX StrToSet. Se utilizzata con il parametro CONSTRAINED, la definizione di sezionamento può utilizzare nomi, chiavi e nomi univoci di membri, livelli, gerarchie e dimensioni e altri oggetti denominati nel cubo, ma non le funzioni MDX. La progettazione delle aggregazioni è una raccolta di definizioni di aggregazione che possono essere condivise tra più partizioni. L'impostazione predefinita deriva dalla progettazione delle aggregazioni del cubo padre.  
  
 Le partizioni vengono utilizzate da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per gestire e archiviare dati e aggregazioni per un gruppo di misure in un cubo. Ogni gruppo di misure dispone di almeno una partizione, che viene creata al momento della definizione del gruppo di misure. Quando si crea una nuova partizione, questa viene aggiunta al set di partizioni già esistenti per il gruppo di misure. Il gruppo di misure riflette i dati combinati di tutte le relative partizioni. È pertanto necessario verificare che i dati di una partizione in un gruppo di misure siano esclusivi rispetto ai dati di qualsiasi altra partizione nel gruppo di misure, in modo da garantire che i dati vengano riflessi nel gruppo di misure una sola volta. La partizione originale per un gruppo di misure si basa su un'unica tabella dei fatti nella vista origine dati del cubo. Se sono presenti più partizioni per lo stesso gruppo di misure, ogni partizione può fare riferimento a una tabella diversa nella vista origine dati oppure nell'origine dei dati relazionali sottostante per il cubo. È possibile che più partizioni in un gruppo di misure facciano riferimento alla stessa tabella, se ogni partizione viene limitata a righe diverse della tabella.  
  
 Le partizioni sono uno strumento potente e flessibile per la gestione dei cubi, soprattutto se di grandi dimensioni. Ad esempio, un cubo contenente informazioni relative alle vendite può includere una partizione per i dati di ogni anno passato e quattro partizioni per ogni trimestre dell'anno corrente. Quando vengono aggiunte informazioni correnti al cubo deve essere elaborata soltanto la partizione del trimestre corrente. L'elaborazione di una quantità inferiore di dati migliorerà le prestazioni dell'elaborazione riducendone i tempi. Alla fine dell'anno, è possibile unire le quattro partizioni relative ai trimestri in un'unica partizione relativa all'intero anno e creare una nuova partizione per il primo trimestre del nuovo anno. Questo processo di creazione di una nuova partizione può inoltre essere automatizzato nell'ambito delle procedure di caricamento di data warehouse e di elaborazione dei cubi.  
  
 Le partizioni non sono visibili agli utenti aziendali del cubo. Gli amministratori possono tuttavia configurare, aggiungere o eliminare le partizioni. Ogni partizione viene archiviata in un set di file distinto. I dati aggregati di ogni partizione possono essere archiviati nell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stata definita la partizione, in un'altra istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]oppure nell'origine dei dati utilizzata per fornire i dati di origine della partizione. Le partizioni consentono di distribuire i dati di origine e i dati aggregati di un cubo tra più dischi rigidi e tra più computer server. Per un cubo di dimensioni medio-grandi, le partizioni consentono di migliorare sensibilmente le prestazioni di query e carichi, nonché di semplificare le operazioni di manutenzione dei cubi. Per altre informazioni sulle partizioni remote, vedere [Partizioni remote](partitions-remote-partitions.md).  
  
 La modalità di archiviazione di ogni partizione può essere configurata indipendentemente dalle altre partizioni incluse nel gruppo di misure. Le partizioni possono essere archiviate utilizzando qualsiasi combinazione di opzioni per la posizione dei dati di origine, la modalità di archiviazione, la memorizzazione nella cache attiva e la progettazione delle aggregazioni. Le opzioni relative a OLAP in tempo reale e memorizzazione nella cache attiva consentono di bilanciare la velocità di esecuzione delle query rispetto alla latenza quando si progetta una partizione. Le opzioni di archiviazione possono inoltre essere applicate alle dimensioni correlate e ai fatti inclusi in un gruppo di misure. Questa flessibilità consente all'utente di definire le strategie di archiviazione dei cubi più appropriate per le proprie esigenze. Per ulteriori informazioni, vedere [modalità di archiviazione delle partizioni e elaborazione](partitions-partition-storage-modes-and-processing.md), [aggregazioni e progettazioni di aggregazioni](aggregations-and-aggregation-designs.md) e [memorizzazione nella cache attiva &#40;partizioni&#41;](partitions-proactive-caching.md).  
  
## <a name="partition-structure"></a>Struttura delle partizioni  
 La struttura di una partizione deve corrispondere alla struttura del relativo gruppo di misure. Le misure che definiscono il gruppo di misure devono pertanto essere definite anche nella partizione, con tutte le dimensioni correlate. Pertanto, quando viene creata, una partizione eredita automaticamente lo stesso set di misure e dimensioni correlate definite per il gruppo di misure.  
  
 Ogni partizione in un gruppo di misure può tuttavia disporre di una diversa tabella dei fatti e tali tabelle dei fatti possono provenire da origini dei dati diverse. Quando più partizioni in un gruppo di misure dispongono di tabelle dei fatti diverse, le tabelle devono essere sufficientemente simili da mantenere la struttura del gruppo di misure, ovvero la query di elaborazione deve restituire le stesse colonne e gli stessi tipi di dati per tutte le tabelle dei fatti di tutte le partizioni.  
  
 Se le tabelle dei fatti per le diverse partizioni provengono da origini dei dati diverse, le tabelle di origine per qualsiasi dimensione correlata e le tabelle dei fatti intermedie devono inoltre essere presenti in tutte le origini dei dati e disporre della stessa struttura in tutti i database. Tutte le colonne delle tabelle delle dimensioni utilizzate per definire gli attributi delle dimensioni dei cubi correlati al gruppo di misure devono inoltre essere presenti in tutte le origini dei dati. Non è necessario definire tutti i join tra la tabella di origine di una partizione e una tabella delle dimensioni correlata se la tabella di origine della partizione ha la stessa struttura della tabella di origine del gruppo di misure.  
  
 Le colonne non utilizzate per la definizione delle misure nel gruppo di misure possono essere presenti in alcune tabelle dei fatti, ma assenti in altre. Analogamente, le colonne non utilizzate per la definizione degli attributi nelle tabelle delle dimensioni correlate possono essere presenti in alcuni database, ma assenti in altri. Le tabelle non utilizzate per le tabelle dei fatti o per le tabelle delle dimensioni correlate possono essere presenti in alcuni database, ma assenti in altri.  
  
## <a name="data-sources-and-partition-storage"></a>Origini dei dati e archiviazione delle partizioni  
 Una partizione si basa su una tabella o vista in un'origine dei dati oppure su una tabella o query denominata in una vista origine dati. La posizione in cui vengono archiviati i dati della partizione viene definita dall'associazione all'origine dei dati. In genere, è possibile partizionare un gruppo di misure orizzontalmente o verticalmente:  
  
-   In un gruppo di misure partizionato orizzontalmente ogni partizione in un gruppo di misure si basa su una tabella distinta. Questo tipo di partizionamento è appropriato nei casi in cui i dati sono suddivisi in più tabelle. Ad esempio, alcuni database relazionali hanno una tabella distinta per i dati di ogni mese.  
  
-   In un gruppo di misure partizionato verticalmente, il gruppo di misure è basato su un'unica tabella e ogni partizione è basata su una query sul sistema di origine che filtra i dati per la partizione. Se ad esempio un'unica tabella contiene i dati relativi a più mesi, il gruppo di misure potrebbe ancora essere partizionato per mese applicando una clausola WHERE di Transact SQL in grado di restituire i dati di un mese distinto per ogni partizione.  
  
 Ogni partizione dispone di impostazioni di archiviazione che determinano se i dati e le aggregazioni della partizione vengono archiviati nell'istanza locale di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oppure in una partizione remota che utilizza un'altra istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Nelle impostazioni di archiviazione è inoltre possibile specificare la modalità di archiviazione e l'eventuale utilizzo della memorizzazione nella cache attiva per controllare la latenza di una partizione. Per altre informazioni, vedere [modalità di archiviazione delle partizioni e elaborazione](partitions-partition-storage-modes-and-processing.md), [memorizzazione nella cache attiva &#40;partizioni&#41;](partitions-proactive-caching.md)e [partizioni remote](partitions-remote-partitions.md).  
  
## <a name="incremental-updates"></a>Aggiornamenti incrementali  
 Quando si creano e gestiscono partizioni in gruppi di misure con più partizioni, è necessario adottare alcune particolari precauzioni per garantire l'accuratezza dei dati del cubo. Sebbene tali precauzioni non siano in genere applicabili ai gruppi di misure con un'unica partizione, in caso di aggiornamento incrementale delle partizioni sono valide anche per questo tipo di gruppo. In caso di aggiornamento incrementale di una partizione, viene creata una nuova partizione temporanea con la stessa struttura della partizione di origine. La partizione temporanea viene elaborata e quindi unita alla partizione di origine. È pertanto necessario verificare che la query di elaborazione con cui viene popolata la partizione temporanea non determini la duplicazione di dati già presenti in una partizione esistente.  
  
## <a name="see-also"></a>Vedere anche  
 [Configura proprietà misura](../multidimensional-models/configure-measure-properties.md)   
 [Cubi nei modelli multidimensionali](../multidimensional-models/cubes-in-multidimensional-models.md)  
  
  
