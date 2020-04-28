---
title: Valutazione degli schemi Oracle per la conversione (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Analyzing Conversion Problems
ms.assetid: 4de9bcf6-1346-4740-87f9-7f24a8226357
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 0ff56be1b7da0376250c7ed021ae78d7144a7645
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68264547"
---
# <a name="assessing-oracle-schemas-for-conversion-oracletosql"></a>Valutazione degli schemi Oracle per la conversione (OracleToSQL)
Prima di caricare oggetti e migrare i [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dati in, è necessario determinare la complessità della migrazione e il tempo necessario per la migrazione. SSMA è in grado di creare un report di valutazione che mostra la percentuale di oggetti che verranno convertiti correttamente. SSMA consente inoltre di visualizzare i problemi specifici che provocano errori di conversione.  
  
## <a name="creating-assessment-reports"></a>Creazione di report di valutazione  
Quando crea il report di valutazione, SSMA converte gli oggetti di database Oracle selezionati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in sintassi, quindi Visualizza i risultati.  
  
**Per creare un report di valutazione**  
  
1.  In Esplora metadati Oracle selezionare gli schemi da valutare.  
  
2.  Per omettere singoli oggetti, deselezionare le caselle di controllo accanto a tali oggetti.  
  
3.  Fare clic con il pulsante destro del mouse su **schemi**e quindi scegliere **Crea report**.  
  
    È anche possibile analizzare singoli oggetti facendo clic con il pulsante destro del mouse su un oggetto e quindi scegliendo **Crea report**.  
  
    SSMA indicherà lo stato di avanzamento nella barra di stato nella parte inferiore della finestra. Se il riquadro di output è visibile, i messaggi vengono visualizzati anche nel riquadro di output.  
  
    Al termine della valutazione, verrà visualizzata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la finestra di Migration Assistant per Oracle: valutazione del report.  
  
## <a name="using-assessment-reports"></a>Utilizzo dei report di valutazione  
La finestra report di valutazione contiene tre riquadri:  
  
-   Il riquadro sinistro contiene la gerarchia di oggetti inclusi nel report di valutazione. È possibile esplorare la gerarchia e selezionare oggetti e categorie di oggetti per visualizzare le statistiche di conversione e il codice.  
  
-   Il contenuto del riquadro destro dipende dall'elemento selezionato nel riquadro sinistro.  
  
    Se si seleziona un gruppo di oggetti, ad esempio uno schema o se è selezionata una tabella, il riquadro destro contiene un riquadro delle statistiche di conversione e un riquadro oggetti per categorie. Il riquadro statistiche di conversione Mostra le statistiche di conversione per gli oggetti selezionati. Il riquadro oggetti per categorie Mostra le statistiche di conversione per l'oggetto o le categorie di oggetti.  
  
    Se è selezionata una funzione, un pacchetto, una procedura, una sequenza o una vista, il riquadro destro contiene le statistiche, il codice sorgente e il codice di destinazione.  
  
    -   L'area superiore mostra le statistiche complessive per l'oggetto. Potrebbe essere necessario espandere **statistiche** per visualizzare queste informazioni.  
  
    -   L'area di origine Mostra il codice sorgente dell'oggetto selezionato nel riquadro sinistro. Le aree evidenziate mostrano codice sorgente problematico.  
  
    -   Nell'area di destinazione viene visualizzato il codice convertito. Il testo rosso Mostra codice problematico e messaggi di errore.  
  
-   Il riquadro inferiore mostra i messaggi di conversione raggruppati per numero di messaggio. È possibile fare clic su **errori**, **avvisi**o **informazioni** per visualizzare le categorie di messaggi, quindi espandere un gruppo di messaggi. Fare clic su un singolo messaggio per selezionare l'oggetto nel riquadro a sinistra e visualizzare i dettagli nel riquadro di destra.  
  
## <a name="analyzing-conversion-problems-by-using-the-assessment-report"></a>Analisi dei problemi di conversione tramite il report di valutazione  
Il riquadro statistiche di conversione Mostra le statistiche di conversione. Se la percentuale di una categoria è inferiore al 100%, è necessario determinare il motivo per cui la conversione non è riuscita.  
  
**Per visualizzare i problemi di conversione**  
  
1.  Creare il report di valutazione utilizzando le istruzioni riportate nella procedura precedente.  
  
2.  Nel riquadro sinistro espandere schemi o cartelle con un'icona di errore rossa. Continuare a espandere gli elementi fino a quando non si seleziona un singolo elemento che non è riuscito a convertire.  
  
3.  Nella parte superiore del riquadro di origine fare clic su **problema successivo**.  
  
    Il codice problematico è evidenziato, così come il codice correlato nel riquadro di spostamento di destinazione.  
  
4.  Esaminare tutti i messaggi di errore e quindi determinare cosa si vuole fare con l'oggetto che ha causato il problema di conversione:  
  
    -   Aggiornare la sintassi Oracle in SSMA. È possibile aggiornare la sintassi per procedure, funzioni, trigger, funzioni in pacchetto e procedure in pacchetto. Per aggiornare la sintassi, selezionare l'oggetto nel riquadro Oracle Metadata Explorer, fare clic sulla scheda **SQL** , quindi modificare il codice SQL. Quando ci si allontana dall'elemento, verrà richiesto di salvare la sintassi aggiornata. È possibile visualizzare gli errori segnalati per l'oggetto nella scheda **report** .  
  
    -   In Oracle è possibile modificare l'oggetto Oracle per rimuovere o rivedere il codice problematico. Per caricare il codice aggiornato in SSMA, sarà necessario aggiornare i metadati. Per ulteriori informazioni, vedere [connessione a Oracle Database &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md).  
  
    -   È possibile escludere l'oggetto dalla migrazione. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Esplora metadati e in Esplora metadati Oracle deselezionare la casella di controllo accanto all'elemento prima di caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ed eseguire la migrazione dei dati da Oracle.  
  
## <a name="next-step"></a>passaggio successivo  
[Conversione di schemi Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Oracle a SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
