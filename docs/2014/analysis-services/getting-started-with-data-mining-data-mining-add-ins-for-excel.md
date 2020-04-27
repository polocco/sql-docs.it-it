---
title: Introduzione con data mining (componenti aggiuntivi Data mining per Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cbe10a19-e194-408e-a65b-5fdf3fb1e880
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e5a24a158681c3f596355b1b9abca6ada990531
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66080941"
---
# <a name="getting-started-with-data-mining-data-mining-add-ins-for-excel"></a>Introduzione al data mining (componenti aggiuntivi Data mining per Excel)
  Il data mining è il processo di individuazione di modelli significativi nei dati. È un complemento naturale del processo di esplorazione e comprensione dei dati tramite gli strumenti tradizionali di Business Intelligence. Gli algoritmi automatici sono in grado di elaborare grandi quantità di dati e di individuare modelli e tendenze altrimenti non evidenti.  
  
 Per eseguire data mining, raccogliere i dati rilevanti per una domanda specifica, ad esempio "chi sono i miei clienti?" o "quali prodotti sono stati acquistati?" quindi applicare un algoritmo per trovare le correlazioni statistiche nei dati. I modelli e le tendenze individuati tramite l'analisi vengono archiviati come modello di data mining. Il modello di data mining può quindi essere applicato ai nuovi dati in scenari aziendali come i seguenti:  
  
-   Si utilizzano tendenze precedenti per prevedere le vendite del successivo trimestre, i requisiti di inventario, la soddisfazione del cliente.  
  
-   Si applica la conoscenza dei clienti correnti per analizzare nuovi clienti e indicare nuovi prodotti o opportunità.  
  
-   Si trovano correlazioni tra gli eventi precedenti per stimare errori o inattività del server.  
  
-   Si analizzano i prodotti che vengono acquistati dai clienti e si utilizzano le informazioni per consigliare i pacchetti o pianificare la posizione del prodotto.  
  
 Il metodo di analisi scelto dipende dagli obiettivi. I componenti aggiuntivi Data mining supportano questi tipi di analisi:  
  
-   Apprendimento supervisionato e non supervisionato  
  
-   Clustering (segmentazione)  
  
-   Analisi dei fattori con Bayes reti neurali  
  
-   Analisi delle serie temporali  
  
-   Analisi di associazione, indicazioni e analisi di tipo Market basket analysis  
  
-   Valutazione di risultati binari  
  
-   Linear Regression  
  
 Inoltre, i componenti aggiuntivi semplificano la fase di preparazione dei dati: selezione, esplorazione e pulizia.  
  
## <a name="define-your-goal"></a>Definire l'obiettivo  
 Prima di iniziare, considerare la domanda a cui si desidera effettivamente trovare risposta. L'esplorazione è già esemplificativa di per sé, ma se i risultati devono essere applicati a nuovi dati, si deve essere in grado di indicare chiaramente quali siano le aspettative relative ai risultati del modello e in quale modo verrà valutato se il modello soddisfa gli obiettivi.  
  
 Ad esempio, anziché l'obiettivo di "trovare nuovi clienti", chiarire l'obiettivo a qualcosa di più concreto, ad esempio "identificare i dati demografici dei clienti che probabilmente acquisteranno il prodotto, con una probabilità pari almeno al 65%".  
  
-   Il set di dati deve contenere almeno un attributo "result" che è possibile usare per il training e la stima. Se non è presente tale attributo, è possibile etichettare manualmente i dati di training oppure utilizzare altre colonne per creare un proxy per il risultato.  
  
     Se, ad esempio, si desidera stimare "i migliori Prospect", è necessario applicare una regola business in anticipo per etichettare i clienti esistenti, in modo che data mining possa apprendere dagli esempi forniti.  
  
-   Se si utilizza un valore che cambia nel tempo e si desiderano stimare le tendenze future, è necessario determinare il livello di granularità dei risultati desiderati. Le stime devono essere mensili, giornaliere o su base annuale? I dati devono essere analizzati utilizzando le stesse unità che devono essere stimate.  
  
     Con i modelli ciclici, se non si ottengono risultati soddisfacenti con i dati giornalieri, provare diversi intervalli di tempo oppure provare a usare giorni della settimana, mesi o persino festivi.  
  
-   Prima di avviare una procedura guidata per individuare le nuove correlazioni nei dati, esaminare ulteriormente i dati e considerare che specie di relazioni potrebbero essere presenti nel set di dati. Sono presenti variabili contraddittorie? Sono presenti duplicati o proxy?  
  
-   Quali sono le metriche in base alle quali verrà valutato il successo del modello? Come si saprà che il modello è "abbastanza valido"?  
  
-   Si desidera eseguire stime in base al modello di data mining o soltanto cercare modelli e associazioni interessanti?  
  
## <a name="explore-your-data-and-explore-the-model"></a>Esplorare i dati ed esplorare il modello  
 Anche quando si ha un'ampia conoscenza dei dati e del dominio, è importante esplorare i dati tenendo a mente la creazione di un modello.  
  
 È opportuno osservare la distribuzione dei valori e identificare i problemi potenziali, ad esempio valori o segnaposto mancanti.  
  
 Se si prevede di eseguire data mining in base a un set di dati di grandi dimensioni o complessi che non è stato possibile analizzare con altri metodi, prendere in considerazione il campionamento o la riduzione dei dati.  
  
-   Come sono distribuiti i dati?  
  
-   Che tipo di relazione esiste tra le colonne o, se esistono più tabelle, tra le tabelle?  
  
-   Mancano dei valori? Sono presenti valori che richiedono la conversione o la pre-elaborazione?  
  
-   I dati sono composti principalmente da testo, da numeri o da una combinazione di questi?  
  
-   I dati a disposizione sono sufficienti a supportare l'analisi dei risultati di destinazione? Se si analizzano le associazioni tra i prodotti, potrebbero essere necessari molti più dati. Se si effettua la stima di un risultato binario, saranno necessari meno dati perché si può presupporre che il set di dati sia bilanciato.  
  
 Una volta completato il modello, esaminare i risultati e identificare le modalità per modificare i dati od ottenere risultati migliori. Veramente di rado il primo modello fornisce tutte le risposte. Il data mining è di norma un processo iterativo.  
  
 Quando si prova a suddividere i dati in modi diversi o si aggiungono nuove colonne, ricordarsi di utilizzare la procedura guidata **modello di documento** per acquisire uno snapshot dei metadati e dei risultati di ogni modello. La disponibilità di un record semplifica la traccia dello stato di avanzamento nell'esplorazione.  
  
 [Esplorazione e pulizia dei dati](exploring-and-cleaning-data.md)  
  
## <a name="validate-your-model"></a>Convalidare il modello  
 Quando si esegue una procedura guidata o uno strumento, l'algoritmo analizza il contenuto dei dati e determina se esiste un modello statisticamente valido. Se l'algoritmo non riesce a trovare modelli validi, verrà ricevuto un messaggio di errore. Tuttavia, anche se un modello è stato creato correttamente, è opportuno testare il modello per verificare se i presupposti sono convalidati. È possibile utilizzare strumenti come il [grafico di accuratezza &#40;SQL Server componenti aggiuntivi Data mining&#41;](accuracy-chart-sql-server-data-mining-add-ins.md) o la [convalida incrociata &#40;SQL Server componenti aggiuntivi Data mining&#41;](cross-validation-sql-server-data-mining-add-ins.md) per produrre misure statistiche della qualità del modello.  
  
 Una volta valutati i risultati del primo modello, è opportuno porsi le domande seguenti:  
  
-   Quali generi di modelli sono stati trovati? Quali sono le probabilità e i valori di supporto?  
  
-   Le ipotesi formulate sulle tendenze si sono rivelate corrette o sono state riscontrate correlazioni inaspettate?  
  
-   Sono stati raccolti sufficienti dati? La creazione di contenitori per i dati produrrebbe modelli più chiari?  
  
-   Il set di dati viene bilanciato? La convalida incrociata può testare la rappresentatività dei dati.  
  
 [Strumenti di analisi tabelle per Excel](table-analysis-tools-for-excel.md)  
  
 [Client di data mining per Excel &#40;SQL Server componenti aggiuntivi Data mining&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
 [Scelta di un modello](choosing-a-model.md)  
  
## <a name="explore-and-refine"></a>Esplorare e perfezionare  
 Se il modello si dimostra valido, è possibile utilizzarlo per effettuare stime, offrire indicazioni, dedurre informazioni essenziali o pianificare strategie aziendali.  
  
-   Utilizzare il browser di data mining nel Client di data mining per Excel per esplorare e interagire con il modello.  
  
-   Utilizzare Excel per ridisporre e filtrare i risultati.  
  
-   Utilizzare Visio per creare presentazioni ed evidenziare le relazioni individuate nei dati.  
  
 Spesso dalla prima analisi si scopre come migliorare l'analisi stessa o ci si rende conto che occorre trovare nuovi dati e più utili. Dal momento che i modelli che si creano utilizzando i componenti aggiuntivi Data Mining per Excel possono essere salvati in un'istanza di Analysis Services, è relativamente semplice aggiornarli con nuovi dati e continuare a perfezionare e a riutilizzare i modelli che hanno avuto successo.  
  
 Un utilizzo importante dei modelli di data mining consiste nel generare stime e indicazioni. I componenti aggiuntivi Data Mining per Excel includono strumenti che semplificano la generazione di query di stime anche complesse, per la conversione delle informazioni essenziali in risultati effettivamente utilizzabili. Tutti questi strumenti sono pienamente integrati con Excel.  
  
 [Visualizzazione di modelli &#40;componenti aggiuntivi Data mining per Office&#41;](viewing-models-data-mining-add-ins-for-office.md)  
  
 [Convalida di modelli e utilizzo di modelli per la stima &#40;componenti aggiuntivi Data mining per Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
## <a name="see-also"></a>Vedi anche  
 [Cosa è incluso nei componenti aggiuntivi Data mining per Office](what-s-included-in-the-data-mining-add-ins-for-office.md)   
 [Guida di riferimento tecnico &#40;componenti aggiuntivi Data mining per Excel&#41;](technical-reference-data-mining-add-ins-for-excel.md)  
  
  
