---
title: Editor di query e di testo (SSMS)
description: Informazioni su come usare gli editor di SQL Server Management Studio (SSMS) per eseguire query, modificare e testare i file in modo interattivo.
ms.custom: seo-lt-2019
ms.prod: sql
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio]
- Code Editor [SQL Server Management Studio], about Query Editor
- Query Editor [SQL Server Management Studio], full screen mode
- Query Editor [Database Engine], templates
- full screen mode [SQL Server Management Studio]
- SQL Server Management Studio [SQL Server], templates
- writing scripts
- modifying scripts
- SQL Server Management Studio [SQL Server], query editor
- Query Editor [SQL Server Management Studio], about Query Editor
- writing queries
- SQL Server Management Studio [SQL Server], editor
- scripts [SQL Server], SQL Server Management Studio
- queries [SQL Server], SQL Server Management Studio
ms.assetid: 062051e4-4b77-4969-98ae-d2547c24ce3e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.date: 03/14/2017
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6a7d8a708c33b2d44c101afce2e62113e599b5b9
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86000908"
---
# <a name="query-and-text-editors-sql-server-management-studio"></a>Editor di query e di testo (SQL Server Management Studio)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  È possibile utilizzare uno degli editor di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per modificare e testare interattivamente uno script [!INCLUDE[tsql](../../includes/tsql-md.md)], MDX, DMX o XML/A oppure per modificare un file XML o un file di testo normale. Ogni editor è supportato da un servizio specifico del linguaggio che assegna un colore alle parole chiave e controlla il codice per rilevare eventuali errori di sintassi e utilizzo. L'editor di query del [!INCLUDE[ssDE](../../includes/ssde-md.md)] include un debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] che è possibile utilizzare per correggere i problemi nel codice [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
## <a name="sql-server-management-studio-editors"></a>Editor di SQL Server Management Studio

 I quattro editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] condividono un'architettura comune. L'editor di testo implementa il livello di base della funzionalità e può essere utilizzato come editor di base per i file di testo. Gli altri tre editor, ossia gli editor di query, estendono questa base di funzionalità includendo un servizio di linguaggio che definisce la sintassi di uno dei linguaggi supportati in SQL Server. Gli editor di query implementano inoltre vari livelli di supporto per caratteristiche dell'editor quali IntelliSense il debug. Gli editor di query includono l'editor di query del Motore di database per l'utilizzo nella compilazione di script che contengono istruzioni Transact-SQL e XQuery, l'editor MDX per il linguaggio MDX, l'editor DMX per il linguaggio DMX e l'editor XML/A per il linguaggio XML for Analysis.  
  
## <a name="common-components"></a>Componenti comuni

 Tutti gli editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] condividono questi componenti:  
  
 **Riquadro del codice**  
 Area in cui è possibile immettere query o testo. Negli editor di query sono incluse le caratteristiche di compilazione delle istruzioni disponibili per il linguaggio di programmazione in uso. L'ambiente di modifica del testo offre il supporto per operazioni di ricerca e sostituzione, creazione di commenti bulk e caratteri e colori personalizzati.  
  
 È possibile impostare opzioni che determinano le caratteristiche del testo nel riquadro del codice, tra cui rientri, tabulazioni, trascinamento del testo e così via. Le finestre Query possono essere configurate come schede della finestra del documento o all'interno di documenti distinti.  
  
 **Margine selezione**  
 Colonna di spazio vuoto tra la barra indicatori e il testo del codice in cui è possibile fare clic per selezionare righe di testo. È possibile nascondere o visualizzare il margine di selezione.  
  
 **Barre di scorrimento orizzontale e verticale**  
 Consentono di scorrere il riquadro del codice orizzontalmente e verticalmente in modo da visualizzare il codice che si estende oltre l'area visibile sullo schermo.  
  
 **Numeri di riga**  
 Visualizza i numeri di riga a sinistra del testo o del codice nell'editor. È possibile passare a numeri di riga specifici.  
  
 **A capo automatico**  
 Visualizza le righe lunghe di testo o di codice su più righe per consentire la visualizzazione di tutto il testo. L'opzione A capo automatico non modifica l'aspetto del testo quando viene eseguito o stampato. È possibile attivarla nella finestra di dialogo **Strumenti**, **Opzioni** , nella pagina Editor di testo, Tutti i linguaggi, Generale o in una pagina specifica dell'editor.  
  
## <a name="code-editor-components"></a>Componenti dell'editor del codice

 Gli editor del codice contengono queste caratteristiche oltre a quelle condivise con gli editor di testo e XML:  
  
 **Risultati**  
 Questa finestra consente di visualizzare i risultati di una query I risultati nella finestra possono essere visualizzati in una griglia o sotto forma di testo, oppure è possibile indirizzarli in un file. È possibile visualizzare le griglie dei risultati come finestre a schede distinte.  
  
 **IntelliSense**  
 Negli editor scegliere **IntelliSense** dal menu **Modifica**per visualizzare le opzioni di IntelliSense di [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **Codifica a colori**  
 Visualizza colori diversi per ogni tipo di elemento di sintassi, migliorando la leggibilità di istruzioni complesse.  
  
 **Struttura del codice**  
 Visualizza i gruppi di codici con linee di suddivisione della struttura a sinistra del codice. È possibile comprimere ed espandere i gruppi di codici per facilitarne la consultazione.  
  
 **Modello**  
 I modelli sono file che includono la struttura di base delle istruzioni necessarie per creare gli oggetti in un database. È possibile utilizzarli per velocizzare la creazione di script.  
  
 **Messaggi**  
 In questa finestra vengono visualizzati errori, avvisi e messaggi informativi restituiti dal server quando viene eseguito uno script. L'elenco di messaggi non subisce modifiche fino a quando lo script non viene eseguito di nuovo.  
  
 **Barra di stato**  
 Visualizza informazioni sul sistema associate alla finestra dell'editor di query, ad esempio l'istanza a cui è connesso l'editor di query.  
  
## <a name="database-engine-query-editor-components"></a>Componenti dell'editor di query del Motore di database

 Questi componenti sono disponibili soltanto nell'editor di query del Motore di database:  
  
 **Debugger**  
 Consente di sospendere l'esecuzione di codice su specifiche istruzioni. È pertanto possibile visualizzare dati e informazioni sul sistema per individuare errori nel codice.  
  
 **Elenco errori**  
 Visualizza errori semantici e di sintassi rilevati da IntelliSense. L'elenco di errori viene modificato dinamicamente durante la modifica degli script [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 **Showplan grafico**  
 Visualizza i passaggi logici compilati nel piano di esecuzione di un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 **Statistiche client**  
 In questa finestra vengono visualizzate informazioni relative all'esecuzione delle query, raggruppate in categorie. Quando si seleziona l'opzione **Includi statistiche client** dal menu **Query** , durante l'esecuzione della query viene visualizzata una finestra **Statistiche client** . Le statistiche delle successive esecuzioni delle query vengono elencate insieme ai valori medi. Per reimpostare la media, selezionare **Reimposta statistiche client** dal menu **Query** .  
  
 **Frammenti di codice**  
 Modelli che è possibile utilizzare come punto di partenza per l'aggiunta di istruzioni nell'editor di query del Motore di database. È possibile inserire i frammenti predefiniti forniti con SQL Server oppure aggiungere frammenti personalizzati.  
  
 **Modalità SQLCMD**  
 Esegue [!INCLUDE[tsql](../../includes/tsql-md.md)] script che includono il set di comandi supportato dall'utilità sqlcmd. Per altre informazioni, vedere [Procedure correlate a sqlcmd](https://msdn.microsoft.com/library/dd7a2d2b-6327-4d77-ac5a-580d36073ad4).  
  
## <a name="editor-tasks"></a>Attività degli editor  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Vengono descritte le modalità di visualizzazione e di utilizzo delle caratteristiche di base dell'editor di query del [!INCLUDE[ssDE](../../includes/ssde-md.md)] .|[Editor di query del Motore di database &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)|  
|Vengono descritte le modalità di visualizzazione e di utilizzo delle caratteristiche di base dell'editor di query MDX.|[Editor di query MDX &#40;Analysis Services - Dati multidimensionali&#41;](https://msdn.microsoft.com/library/777f2c23-1c1c-4b72-9d19-48a4866551f8)|  
|Vengono descritte le modalità di visualizzazione e di utilizzo delle caratteristiche di base dell'editor di query DMX.|[Editor di query DMX &#40;Analysis Services - Data mining&#41;](https://msdn.microsoft.com/library/7ac877a1-0f29-46b9-9a51-73b02172bef1)|  
|Vengono descritte le modalità di visualizzazione e di utilizzo delle caratteristiche di base dell'editor di query XML/A.|[Editor XML &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/xml-editor-sql-server-management-studio.md)|  
|Viene descritto come configurare opzioni per i vari editor, ad esempio numerazione delle righe e opzioni IntelliSense.|[Configurazione di editor &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/configure-editors-sql-server-management-studio.md)|  
|Vengono descritti i vari modi in cui è possibile avviare gli editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].|[Apertura di un editor &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/open-an-editor-sql-server-management-studio.md)|  
|Viene descritto come gestire le modalità di visualizzazione, ad esempio utilizzando il ritorno a capo automatico, la divisione di una finestra o le schede.|[Gestire l'editor e la modalità di visualizzazione](../../relational-databases/scripting/manage-the-editor-and-view-mode.md)|  
|Viene descritto come impostare le opzioni di formattazione, ad esempio testo nascosto o rientri.|[Gestire la formattazione del codice](../../relational-databases/scripting/manage-code-formatting.md)|  
|Viene descritto come spostarsi nel testo in una finestra dell'editor mediante caratteristiche come la ricerca incrementale o la funzione "vai a".|[Spostarsi nel codice e nel testo](../../relational-databases/scripting/navigate-code-and-text.md)|  
|Viene descritto come impostare le opzioni di codifica a colori per varie classi di sintassi, semplificando la lettura di istruzioni complesse.|[Codifica con colori negli editor di query](../../relational-databases/scripting/color-coding-in-query-editors.md)|  
|Viene descritto come utilizzare la struttura del codice per nascondere parti di script complessi nei momenti in cui non vengono utilizzate.|[Struttura del codice](../../relational-databases/scripting/code-outlining.md)|  
|Viene descritto come trascinare il testo da un percorso in uno script e rilasciarlo in un nuovo percorso.|[Spostare testo tramite trascinamento della selezione](../../relational-databases/scripting/drag-and-drop-text.md)|  
|Viene descritto come effettuare operazioni di ricerca e sostituzione globale, ad esempio in caso di modifica dei nomi di colonna.|[Ricerca e sostituzione](../../relational-databases/scripting/search-and-replace.md)|  
|Viene descritto come impostare segnalibri per trovare più facilmente parti importanti di codice.|[Gestire i segnalibri](../../relational-databases/scripting/manage-bookmarks.md)|  
|Viene descritto come visualizzare script o risultati in una finestra o in una griglia.|[Stampare codice e risultati](../../relational-databases/scripting/print-code-and-results.md)|  
|Vengono descritte le modalità di visualizzazione e di utilizzo delle caratteristiche di sqlcmd nell'editor di query del [!INCLUDE[ssDE](../../includes/ssde-md.md)] .|[Modificare script SQLCMD con l'editor di query](../../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md)|  
|Viene descritto come utilizzare le caratteristiche IntelliSense come il completamento automatico di nomi oggetto durante la digitazione o la verifica del corretto posizionamento dei punti di interruzione.|[IntelliSense &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/intellisense-sql-server-management-studio.md)|  
|Vengono descritte le modalità di utilizzo dei frammenti di codice nell'editor di query del [!INCLUDE[ssDE](../../includes/ssde-md.md)] . I frammenti sono modelli per istruzioni o blocchi di uso comune e possono essere personalizzati o estesi per includere frammenti specifici del sito.|[Frammenti di codice Transact-SQL](../../relational-databases/scripting/transact-sql-code-snippets.md)|  
|Viene descritto come utilizzare il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] per avanzare nel codice e visualizzare informazioni di debug, ad esempio i valori in variabili e parametri.|[Debugger Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)|  
|Viene descritto come impostare colori personalizzati per istanze diverse del [!INCLUDE[ssDE](../../includes/ssde-md.md)]e come impostarli come sfondo della barra di stato nelle finestre dell'editor di query del [!INCLUDE[ssDE](../../includes/ssde-md.md)] .|[Barra di stato &#40;editor di query del Motore di database&#41;](../../relational-databases/scripting/status-bar-database-engine-query-editor.md)|  
  
## <a name="next-steps"></a>Passaggi successivi

[Tasti di scelta rapida di SQL Server Management Studio](../../ssms/sql-server-management-studio-keyboard-shortcuts.md)