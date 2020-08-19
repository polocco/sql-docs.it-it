---
description: Esecuzione di test case (SybaseToSQL)
title: Esecuzione di test case (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester Component,Execution Steps
ms.assetid: 195ffdef-cfde-4bf4-a3ae-e7402bb07972
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: ea2b250f59a29a16bc77ad23e28b0823461a8ace
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468755"
---
# <a name="running-test-cases-sybasetosql"></a>Esecuzione di test case (SybaseToSQL)
Quando SSMA tester esegue un test case, esegue gli oggetti selezionati per il test e crea un report sui risultati della verifica. Se i risultati sono identici su entrambe le piattaforme, il test ha avuto esito positivo. La corrispondenza degli oggetti tra Sybase e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene determinata in base alle impostazioni di mapping dello schema per il progetto SSMA corrente.  
  
Un requisito necessario per un test riuscito è che tutti gli oggetti Sybase vengono convertiti e caricati nel database di destinazione. Inoltre, è necessario eseguire la migrazione dei dati della tabella in modo da sincronizzare il contenuto delle tabelle in entrambe le piattaforme.  
  
## <a name="run-test-case"></a>Esegui test case  
Per eseguire il test case preparato:  
  
1.  Fare clic sul pulsante **Esegui**.  
  
2.  Nella finestra di dialogo **Connetti a Sybase** immettere le informazioni di connessione e quindi fare clic su **Connetti**.  
  
Al termine del test, viene creato il report del test case. Fare clic sul pulsante **report** per visualizzare i [report dei test Case di visualizzazione &#40;&#41;SybaseToSQL ](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md). Il risultato del test (report test case) viene archiviato automaticamente nell'uso dei [repository di test &#40;SybaseToSQL&#41;](../../ssma/sybase/using-test-repositories-sybasetosql.md) per un uso successivo.  
  
## <a name="test-case-execution-steps"></a>Passaggi di esecuzione del test case  
  
### <a name="prerequisites"></a>Prerequisiti  
SSMA tester verifica se tutti i prerequisiti sono soddisfatti per l'esecuzione dei test prima dell'avvio del test. Se alcune condizioni non vengono soddisfatte, viene visualizzato un messaggio di errore.  
  
### <a name="initialization"></a>Inizializzazione  
A questo punto, SSMA tester crea oggetti ausiliari (tabelle, trigger e visualizzazioni) sia in Sybase che in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Consentono la traccia delle modifiche apportate alle tabelle interessate selezionate per la verifica se la modalità di confronto tabella è **solo modifiche**.  
  
Si supponga che la tabella verificata sia denominata USER_TABLE. Per una tabella di questo tipo, vengono creati gli oggetti ausiliari seguenti in Sybase.  
  
Gli oggetti seguenti vengono creati in Sybase nel database SSMATESTER2005db o SSMATESTER2008db e in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel database di ssmatesterdb_syb.  
  
|Nome|Type|Descrizione|  
|--------|--------|---------------|  
|USER_TABLE $ Trg|Trigger|Attivare il controllo delle modifiche nella tabella verificata.|  
|USER_TABLE $ AUD|Tabella|Tabella in cui vengono salvate le righe eliminate e sovrascritte.|  
|USER_TABLE $ AudId|Tabella|Tabella in cui vengono salvate le righe nuove e modificate.|  
|USER_TABLE|Visualizza|Rappresentazione semplificata delle modifiche della tabella.|  
|USER_TABLE $ New|Visualizza|Rappresentazione semplificata delle righe inserite e sovrascritte.|  
|USER_TABLE $ new_id|Visualizza|Identificazione delle righe inserite e modificate.|  
|USER_TABLE $ Old|Visualizza|Rappresentazione semplificata delle righe eliminate e sovrascritte.|  
  
Il seguente oggetto viene creato nel database della tabella verificata in Sybase e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Nome|Type|Descrizione|  
|--------|--------|---------------|  
|USER_TABLE $ Trg|Trigger|Attivare il controllo delle modifiche nella tabella verificata.|  
  
### <a name="test-object-calls"></a>Test delle chiamate all'oggetto  
In questo passaggio, SSMA tester richiama ogni oggetto selezionato per il test, confronta i risultati e visualizza il report.  
  
### <a name="finalization"></a>Finalizzazione  
Durante la finalizzazione, SSMA tester pulisce gli oggetti ausiliari creati al passaggio di **inizializzazione** .  
  
## <a name="next-step"></a>passaggio successivo  
[Visualizzazione dei report del test case &#40;SybaseToSQL&#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Selezione e configurazione degli oggetti da testare &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md)  
[Selezione e configurazione degli oggetti interessati &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
[Test di oggetti di database migrati &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
