---
title: Failover forzato di SQL Server per i gruppi di disponibilità
description: Failover forzato per i gruppi di disponibilità con tipo di cluster NONE
services: ''
author: MikeRayMSFT
ms.topic: include
ms.date: 02/05/2018
ms.author: mikeray
ms.custom: include file
ms.openlocfilehash: aa0b00ec24c96aea37901cc03aac2dda9b20bed2
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/20/2020
ms.locfileid: "88655221"
---
Ogni gruppo di disponibilità include solo una replica primaria, che consente operazioni di lettura e scrittura. Per modificare la replica primaria, è possibile effettuare il failover. In un gruppo di disponibilità per disponibilità elevata, il processo di failover è automatizzato da Gestione cluster. In un gruppo di disponibilità con tipo di cluster NONE, il processo di failover è manuale. 

Esistono due modi per effettuare il failover della replica primaria in un gruppo di disponibilità con tipo di cluster NONE:

- Failover manuale forzato con perdita di dati
- Failover manuale senza perdita di dati

### <a name="forced-manual-failover-with-data-loss"></a>Failover manuale forzato con perdita di dati

Usare questo metodo quando la replica primaria non è disponibile e non può essere recuperata. 

Per forzare il failover con perdita di dati, connettersi all'istanza di SQL Server che ospita la replica secondaria di destinazione ed eseguire quindi il comando seguente:

```SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

Quando viene recuperata la replica primaria precedente, questa assume anche il ruolo primario. Per assicurarsi che la replica primaria precedente passi a un ruolo secondario, eseguire il comando seguente nella replica primaria precedente.

```SQL
ALTER AVAILABILITY GROUP [ag1]  SET (ROLE = SECONDARY);
```

### <a name="manual-failover-without-data-loss"></a>Failover manuale senza perdita di dati

Usare questo metodo quando la replica primaria è disponibile, ma è necessario modificare temporaneamente o definitivamente la configurazione e l'istanza SQL Server che ospita la replica primaria. Per evitare una potenziale perdita di dati, prima di effettuare il failover manuale, verificare che la replica secondaria di destinazione sia aggiornata. 

Per effettuare il failover manuale senza perdita di dati:

1. Impostare la replica primaria corrente e la replica secondaria di destinazione come `SYNCHRONOUS_COMMIT`.

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        MODIFY REPLICA ON N'<node2>' 
        WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```

1. Per verificare che per le transazioni attive venga eseguito il commit della replica primaria e di almeno una replica secondaria sincrona, eseguire la query seguente: 

   ```SQL
   SELECT ag.name, 
      drs.database_id, 
      drs.group_id, 
      drs.replica_id, 
      drs.synchronization_state_desc, 
      ag.sequence_number
   FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
   WHERE drs.group_id = ag.group_id; 
   ```

   La replica secondaria è sincronizzata quando `synchronization_state_desc` è `SYNCHRONIZED`.

1. Aggiornare `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` su 1.

   Lo script seguente imposta `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` su 1 in un gruppo di disponibilità denominato `ag1`. Prima di eseguire lo script seguente, sostituire `ag1` con il nome del gruppo di disponibilità:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = 1);
   ```

   Questa impostazione assicura che per ogni transazione attiva venga eseguito il commit della replica primaria e di almeno una replica secondaria sincrona. 
   >[!NOTE]
   >Questa impostazione non è specifica del failover e deve essere impostata in base ai requisiti dell'ambiente.
   
1. Portare offline la replica primaria in preparazione delle modifiche del ruolo.
   ```SQL
   ALTER AVAILABILITY GROUP [ag1] OFFLINE
   ```

1. Alzare il livello della replica secondaria di destinazione a replica primaria. 

   ```SQL
   ALTER AVAILABILITY GROUP ag1 FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ``` 

1. Aggiornare il ruolo della replica primaria precedente in `SECONDARY`, quindi eseguire il comando seguente nell'istanza di SQL Server che ospita la replica primaria precedente:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (ROLE = SECONDARY); 
   ```

   > [!NOTE] 
   > Per eliminare un gruppo di disponibilità, usare [DROP AVAILABILITY GROUP](https://docs.microsoft.com/sql/t-sql/statements/drop-availability-group-transact-sql). Per un gruppo di disponibilità creato con il tipo di cluster NONE o EXTERNAL, eseguire il comando su tutte le repliche che fanno parte del gruppo di disponibilità.

1. Riprendere lo spostamento dati, eseguire il comando seguente per ogni database nel gruppo di disponibilità nell'istanza di SQL Server che ospita la replica primaria: 

   ```sql
   ALTER DATABASE [db1]
        SET HADR RESUME
   ```

1. Ricreare ogni listener creato a scopo di scalabilità in lettura e che non rientra nella gestione cluster. Se il listener originale punta alla replica primaria precedente, rimuoverlo e ricrearlo in modo che punti a quella nuova.
