---
title: Mapping dei tipi di dati di Sybase ASE e SQL Server (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Mapping Sybase ASE Schemas to SQL Server Schemas
- Type Mapping Settings
ms.assetid: 784365d3-df4e-47ab-8ee0-d8392b52f510
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 79313d2344f6feb978a064f3fbd92e1f7bc7dce5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68028888"
---
# <a name="mapping-sybase-ase-and-sql-server-data-types-sybasetosql"></a>Mapping dei tipi di dati di Sybase ASE e SQL Server (SybaseToSQL)
I tipi di database di Sybase Adaptive Server Enterprise (ASE) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] differiscono da o SQL Azure tipi di database. Quando si convertono oggetti di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dell'ambiente del servizio app in oggetti o SQL Azure, è necessario specificare come eseguire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il mapping dei tipi di dati da ASE a o SQL Azure. È possibile accettare i mapping dei tipi di dati predefiniti oppure personalizzare i mapping, come illustrato nelle sezioni seguenti.  
  
## <a name="default-mappings"></a>Mapping predefiniti  
SSMA dispone di un set predefinito di mapping dei tipi di dati. Per l'elenco dei mapping predefiniti, vedere [Impostazioni progetto &#40;mapping dei tipi&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
## <a name="type-mapping-inheritance"></a>Ereditarietà del mapping dei tipi  
È possibile personalizzare i mapping dei tipi a livello di progetto, di categoria dell'oggetto, ad esempio tutte le stored procedure, o a livello di oggetto. Le impostazioni vengono ereditate dal livello superiore a meno che non venga sottoposto a override a un livello inferiore. Se, ad esempio, si esegue il mapping di **smallmoney** a **Money** a livello di progetto, tutti gli oggetti del progetto utilizzeranno questo mapping a meno che non si Personalizza il mapping a livello di categoria di oggetto o di oggetto.  
  
Quando si visualizza la scheda **mapping dei tipi** in SSMA, lo sfondo è codificato a colori per visualizzare i mapping dei tipi ereditati. Lo sfondo di un mapping dei tipi è giallo per qualsiasi mapping di tipi ereditati e bianco per qualsiasi mapping specificato al livello corrente.  
  
## <a name="customizing-data-type-mappings"></a>Personalizzazione dei mapping dei tipi di dati  
Nella procedura riportata di seguito viene illustrato come eseguire il mapping dei tipi di dati a livello di progetto, database o oggetto.  
  
**Per eseguire il mapping dei tipi di dati**  
  
1.  Per personalizzare il mapping dei tipi di dati per l'intero progetto, aprire la finestra di dialogo **Impostazioni progetto** :  
  
    1.  Scegliere **Impostazioni progetto**dal menu **strumenti** .  
  
    2.  Nel riquadro sinistro selezionare mapping dei **tipi**.  
  
        Il grafico del mapping dei tipi e i pulsanti vengono visualizzati nel riquadro di destra.  
  
    In alternativa, per personalizzare il mapping dei tipi di dati a livello di database, tabella, vista o stored procedure, selezionare database, categoria oggetto o oggetto in Esplora metadati Sybase:  
  
    1.  In Sybase Metadata Explorer selezionare la cartella o l'oggetto che si desidera personalizzare.  
  
    2.  Nel riquadro di destra fare clic sulla scheda **mapping dei tipi** .  
  
2.  Per aggiungere un nuovo mapping, eseguire le operazioni seguenti:  
  
    1.  Fare clic su **Aggiungi**.  
  
    2.  In **tipo di origine**selezionare il tipo di dati dell'ambiente del servizio app da mappare.  
  
    3.  Se il tipo richiede una lunghezza, specificare la lunghezza minima dei dati per il mapping nella casella **da** e specificare la lunghezza massima dei dati per il mapping nella casella **a** .  
  
        In questo modo è possibile personalizzare il mapping dei dati per valori più piccoli e più grandi dello stesso tipo di dati.  
  
    4.  In **tipo di destinazione**selezionare il tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di dati di destinazione o SQL Azure.  
  
        Alcuni tipi richiedono una lunghezza del tipo di dati di destinazione. Se necessario, immettere la nuova lunghezza dei dati nella casella **Sostituisci con** .  
  
    5.  Fare clic su **OK**.  
  
3.  Per modificare un mapping dei tipi di dati, eseguire le operazioni seguenti:  
  
    1.  Fare clic su **Edit**.  
  
    2.  In **tipo di origine**selezionare il tipo di dati dell'ambiente del servizio app da mappare.  
  
    3.  Se il tipo richiede una lunghezza, specificare la lunghezza minima dei dati per il mapping nella casella **da** e specificare la lunghezza massima dei dati per il mapping nella casella **a** .  
  
        In questo modo è possibile personalizzare il mapping dei dati per valori più piccoli e più grandi dello stesso tipo di dati.  
  
    4.  In **tipo di destinazione**selezionare il tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di dati di destinazione o SQL Azure.  
  
        Alcuni tipi richiedono una lunghezza del tipo di dati di destinazione. Se necessario, immettere la nuova lunghezza dei dati nella casella **Sostituisci con** , quindi fare clic su **OK**.  
  
4.  Per rimuovere un mapping del tipo di dati personalizzato, eseguire le operazioni seguenti:  
  
    1.  Selezionare la riga nell'elenco mapping dei tipi che contiene il mapping del tipo di dati che si desidera rimuovere.  
  
    2.  Scegliere **Rimuovi**.  
  
        Non è possibile rimuovere i mapping ereditati. Tuttavia, i mapping ereditati vengono sottoposti a override da mapping personalizzati in un oggetto o una categoria di oggetti specifici.  
  
## <a name="next-steps"></a>Passaggi successivi  
Il passaggio successivo del processo di migrazione consiste nel [creare un report di valutazione](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md) o [convertire gli oggetti di database Sybase ASE nella sintassi SQL Server o SQL Azure](converting-sybase-ase-database-objects-sybasetosql.md). Se si crea un report di valutazione, gli oggetti di Sybase ASE vengono convertiti automaticamente durante la valutazione.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione dei database Sybase ASE a SQL Server-database SQL di Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
