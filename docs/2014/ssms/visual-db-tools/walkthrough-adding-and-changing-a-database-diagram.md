---
title: 'Scenario: Aggiunta e modifica di un diagramma di database | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- database diagrams [SQL Server], about database diagrams
- database diagrams [SQL Server], designing
- database diagrams [SQL Server], creating
ms.assetid: 228caa0d-8f24-46ab-86d1-b6d8631322bc
author: stevestein
ms.author: sstein
ms.openlocfilehash: c7314598bffe53b6db1c24ecaaec2cf32ee06cb7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85008596"
---
# <a name="walkthrough-adding-and-changing-a-database-diagram"></a>Scenario: Aggiunta e modifica di un diagramma di database
  In questo scenario viene illustrato come creare e modificare un diagramma di database e apportare modifiche al database tramite il componente per i diagrammi di database. Verrà descritto come aggiungere tabelle ai diagrammi, creare relazioni tra le tabelle, creare vincoli e indici su colonne e modificare il livello delle informazioni visualizzate per ogni tabella.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per completare questo scenario, saranno necessari gli elementi seguenti:  
  
-   Accedere a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
-   Un account con privilegi `dbo` di proprietario del database.  
  
> [!NOTE]  
>  Se si tenta di apportare modifiche quando si utilizza un account senza privilegi sufficienti ad apportare modifiche alle tabelle, verrà visualizzato un messaggio di errore.  
  
## <a name="creating-a-diagram"></a>Creazione di un diagramma  
  
#### <a name="to-create-a-new-database-diagram"></a>Per creare un nuovo diagramma di database  
  
1.  Dal menu **Visualizza** fare clic su **Esplora oggetti**.  
  
2.  Aprire il nodo Database e quindi il nodo [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
3.  Fare clic con il pulsante destro del mouse sul nodo Diagrammi database e scegliere **Nuovo diagramma database**.  
  
     Se il database non include gli oggetti necessari alla creazione dei diagrammi, verrà visualizzato il messaggio seguente: **Per il database non sono disponibili uno o più oggetti di supporto necessari per l'utilizzo dei diagrammi. Creare tali oggetti?** Scegliere **Sì**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi tabella** .  
  
4.  Selezionare **AddressType (Person)** (Tipo indirizzo (Persona) e **Address (Person)** (Indirizzo (Persona) e fare clic su **Aggiungi**.  
  
     Al diagramma verranno aggiunte due tabelle.  
  
5.  Chiudere la finestra di dialogo **Aggiungi tabella** .  
  
#### <a name="to-view-different-column-data"></a>Per visualizzare dati di colonne diverse  
  
1.  Fare clic con il pulsante destro del mouse sulla tabella `Address` . Nel menu di scelta rapida scegliere **Vista tabella**e fare clic su **Standard**.  
  
     Nella griglia della tabella sono visualizzate tre colonne: **Nome colonna**, **Tipo di dati**e **Consenti valori Null**.  
  
2.  Fare clic con il pulsante destro del mouse sulla tabella `Address` , fare clic su **Vista tabella** e scegliere **Chiavi**.  
  
     Nella griglia della tabella è visualizzata una colonna, con i nomi delle colonne della tabella. Sono visualizzate solo le colonne incluse negli indici.  
  
## <a name="creating-new-tables"></a>Creazione di nuove tabelle  
  
#### <a name="to-create-tables-within-diagram-designer"></a>Per creare tabelle all'interno di Progettazione diagrammi  
  
1.  Fare clic con il pulsante destro del mouse su Progettazione diagrammi all'esterno delle tabelle esistenti e scegliere **Nuova tabella**.  
  
2.  Nella finestra di dialogo **Scegli nome** fare clic su **OK** per accettare il nome predefinito `Table1` .  
  
     Verrà visualizzata una nuova griglia della tabella con tre colonne: **Nome colonna**, **Tipo di dati**e **Consenti valori Null**.  
  
3.  Aggiungere le informazioni seguenti a `Table1` :  
  
    |**Nome colonna**|**Tipo di dati**|**Consenti valori NULL**|  
    |---------------------|-------------------|---------------------|  
    |`T1col1`|`int`|checked|  
    |`T1col2`|`varchar(50)`|checked|  
    |`T1col3`|`float`|selezionata|  
  
4.  Fare clic con il pulsante destro del mouse su `T1col1` e selezionare **Imposta chiave primaria**.  
  
     Accanto al nome della colonna verrà visualizzata un'icona a forma di chiave.  
  
5.  Scegliere **Salva Diagram1** dal menu **File**.  
  
6.  Nella finestra di dialogo **Scegli nome** fare clic su **OK** per accettare il nome predefinito `Diagram1` .  
  
7.  Verrà visualizzata la finestra di dialogo **Salva** con un messaggio che indica che `Table1` verrà salvata nel database. Fare clic su **Sì**.  
  
## <a name="modifying-table-structure"></a>Modifica della struttura della tabella  
 È possibile aggiungere vincoli CHECK e creare relazioni tra le tabelle in Progettazione diagrammi.  
  
#### <a name="to-create-check-constraints"></a>Per creare vincoli CHECK  
  
1.  In `Table1`fare clic con il pulsante destro del mouse sulla riga `T1col3` e scegliere **Vincoli CHECK**.  
  
     Verrà visualizzata la finestra di dialogo **Vincoli CHECK** .  
  
2.  Scegliere **Aggiungi**.  
  
     Verrà visualizzato un nuovo vincolo nell'elenco **Selected Check Constraint** (Vincolo CHECK selezionato), con il nome predefinito `CK_Table1`.  
  
3.  Selezionare la riga **Espressione** nella griglia e fare clic sul pulsante con i puntini di sospensione.  
  
     Verrà visualizzata la finestra di dialogo **Espressione vincolo CHECK**.  
  
4.  Digitare `T1col3 > 5` e fare clic su **OK**.  
  
     `Table1` include ora un vincolo in base al quale tutti i valori immessi in `T1col3` devono essere maggiori di 5.  
  
5.  Fare clic su **Close**.  
  
#### <a name="to-create-relationships-between-tables"></a>Per creare relazioni tra le tabelle  
  
1.  Creare una nuova tabella in Progettazione diagrammi denominata `Table2` con le colonne seguenti:  
  
    |**Nome colonna**|**Tipo di dati**|**Consenti valori NULL**|  
    |---------------------|-------------------|---------------------|  
    |`T2col1`|`int`|non selezionata|  
    |`T2col2`|`varchar(50)`|checked|  
    |`T2col3`|`xml`|checked|  
  
    > [!NOTE]  
    >  Le colonne della chiave primaria di una relazione di chiave esterna devono far parte di un vincolo UNIQUE o PRIMARY KEY.  
  
2.  Trascinare `T2col1` in `T1col1`.  
  
     Verranno visualizzate due finestre di dialogo: **Relazione chiavi esterne** sullo sfondo e **Tabelle e colonne** in primo piano.  
  
3.  Fare clic su **OK** per salvare la nuova relazione.  
  
4.  Fare di nuovo clic su **OK** .  
  
## <a name="creating-indexes"></a>Creazione di indici  
 È possibile creare indici per la maggioranza dei tipi di dati, inclusi i dati XML.  
  
#### <a name="to-create-a-standard-index"></a>Per creare un indice standard  
  
1.  Fare clic con il pulsante destro del mouse su `Table1` e scegliere **Indici/chiavi**.  
  
     Verrà visualizzata la finestra di dialogo **Indici/chiavi** .  
  
2.  Scegliere **Aggiungi**.  
  
     Verrà visualizzato un nuovo indice nell'elenco **Chiave o indice primario/univoco selezionato** , con un nome predefinito simile a `IX_Table1`.  
  
3.  Selezionare la riga **Colonne** e fare clic sul pulsante con i puntini di sospensione.  
  
     Verrà visualizzata la finestra di dialogo **Colonne indice** .  
  
4.  Fare clic sulla freccia a discesa in **Nome colonna** e selezionare `T1col2`.  
  
    > [!NOTE]  
    >  È possibile aggiungere colonne aggiuntive all'indice selezionando la cella sotto `T1col2` e scegliendo un altro nome di colonna.  
  
5.  Fare clic su **OK** per salvare l'indice.  
  
6.  Fare clic su **Chiudi** nella finestra di dialogo **Indici/chiavi** .  
  
#### <a name="to-create-an-xml-index"></a>Per creare un indice XML  
  
1.  Fare clic con il pulsante destro del mouse su `T2col1` e selezionare **Imposta chiave primaria**.  
  
    > [!NOTE]  
    >  Per l'aggiunta di un indice XML è necessario che un'altra colonna nella tabella sia impostata come chiave primaria cluster.  
  
2.  Fare clic con il pulsante destro del mouse sulla riga `T2col3` in `Table2` e scegliere **Indici XML**.  
  
     Verrà visualizzata la finestra di dialogo **Indici XML** .  
  
3.  Scegliere **Aggiungi**.  
  
     Un indice XML con valori predefiniti verrà aggiunto all'elenco **Selected XML Index** (Indice XML selezionato).  
  
4.  Fare clic su **Close**.  
  
    > [!NOTE]  
    >  Gli indici XML vengono creati per colonna. Il primo indice XML è primario, eventuali indici aggiuntivi sono secondari.  
  
## <a name="saving-the-diagram"></a>Salvataggio del diagramma  
 Tutte le modifiche apportate a un diagramma non vengono inviate al database fino al salvataggio. Nel caso in cui siano presenti problemi o conflitti, verrà visualizzata una finestra di dialogo con ulteriori informazioni.  
  
#### <a name="to-save-a-database-diagram"></a>Per salvare un diagramma di database  
  
1.  Dal menu **File** selezionare **Salva Diagram1**.  
  
     Verrà visualizzata la finestra di dialogo **Salva** . Se l'opzione **Avvisa in caso le tabelle siano modificate** è selezionata, vengono indicate informazioni sulle tabelle nuove o modificate.  
  
2.  Fare clic su **OK**.  
  
3.  Se si sono verificati errori, verrà visualizzata la finestra di dialogo **Notifiche postsalvataggio** con gli errori e le relative cause. Correggere gli errori e salvare nuovamente il diagramma.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Si tratta di un diagramma di base con due tabelle esistenti e due tabelle nuove, che illustra comunque le potenzialità della creazione di diagrammi per un database esistente o di creazione di un nuovo schema in modo visivo. Alcuni suggerimenti per un'analisi più ampia dell'argomento includono:  
  
-   Creazione di nuovi diagrammi che contengono gruppi di tabelle correlate  
  
-   Personalizzazione della quantità di informazioni visualizzate per ogni tabella  
  
-   Modifica del layout e aggiunta di annotazioni  
  
-   Copia del diagramma in una bitmap  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzare la quantità di informazioni visualizzate nei diagrammi &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Configurare Progettazione diagrammi di database &#40;Visual Database Tools&#41;](set-up-database-diagram-designer-visual-database-tools.md)   
 [Aggiunta di tabelle a diagrammi &#40;Visual Database Tools&#41;](add-tables-to-diagrams-visual-database-tools.md)   
 [Creazione di relazioni tra tabelle in un diagramma &#40;Visual Database Tools&#41;](create-relationships-between-tables-on-a-diagram-visual-database-tools.md)   
 [Creazione di indici XML](../../relational-databases/xml/create-xml-indexes.md)   
 [Copiare un'immagine di un diagramma di database negli Appunti &#40;Visual Database Tools&#41;](copy-an-image-of-a-database-diagram-to-the-clipboard-visual-database-tools.md)   
 [Utilizzare il layout di un diagramma &#40;Visual Database Tools&#41;](work-with-diagram-layout-visual-database-tools.md)  
  
  
