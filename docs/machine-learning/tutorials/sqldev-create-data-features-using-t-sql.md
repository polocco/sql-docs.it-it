---
title: 'Esercitazione su R + T-SQL: Caratteristiche dei dati'
description: Esercitazione che illustra come aggiungere calcoli alle stored procedure per l'uso nei modelli di Machine Learning di R.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 10/19/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c5b588f9cb94d39753040e3251d9a4b2e1f12d49
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85670961"
---
# <a name="lesson-2-create-data-features-using-r-and-t-sql"></a>Lezione 2: Creare caratteristiche dei dati con R e T-SQL
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Questo articolo fa parte di un'esercitazione per sviluppatori SQL sull'uso di R in SQL Server.

In questo passaggio si apprenderà come creare funzionalità dai dati non elaborati tramite una funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] . Tale funzione verrà quindi chiamata da una stored procedure per creare una tabella contenente i valori della funzionalità.

## <a name="about-feature-engineering"></a>Progettazione delle caratteristiche

Dopo varie sessioni di esplorazione dei dati si sono raccolte alcune informazioni relative ai dati e si è pronti a passare alla *progettazione di funzionalità*. Questo processo di creazione di caratteristiche significative a partire da dati non elaborati è un passaggio fondamentale nella creazione di modelli di analisi.

In questo set di dati, i valori di distanza si basano sulla distanza registrata dal tassametro e non rappresentano necessariamente la distanza geografica o la distanza effettivamente percorsa. Pertanto è necessario calcolare la distanza diretta tra i punti di inizio e fine della corsa, usando le coordinate disponibili nel set di dati di origine NYC Taxi. È possibile farlo usando la [formula dell'emisenoverso](https://en.wikipedia.org/wiki/Haversine_formula) in una funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] personalizzata.

Si userà una funzione T-SQL personalizzata, _fnCalculateDistance_, per calcolare la distanza con la formula dell'emisenoverso e una seconda funzione T-SQL personalizzata, _fnEngineerFeatures_, per creare una tabella contenente tutte le funzionalità.

Il processo generale è il seguente:

- Creare la funzione T-SQL che esegue i calcoli

- Chiamare la funzione che consente di generare i dati della caratteristica

- Salvare i dati della caratteristica in una tabella

## <a name="calculate-trip-distance-using-fncalculatedistance"></a>Calcolare la distanza della corsa usando fnCalculateDistance

La funzione _fnCalculateDistance_ deve essere scaricata e registrata con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nell'ambito delle attività di preparazione di questa esercitazione. Dedicare un attimo di tempo a esaminare il codice.
  
1. In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]espandere **Programmabilità**, **Funzioni** e quindi **Funzioni a valori scalari**.   

2. Fare clic con il pulsante destro del mouse su _fnCalculateDistance_e selezionare **Modifica** per aprire lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] in una nuova finestra Query.
  
    ```sql
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)  
    -- User-defined function that calculates the direct distance between two geographical coordinates.  
    RETURNS float  
    AS  
    BEGIN  
      DECLARE @distance decimal(28, 10)  
      -- Convert to radians  
      SET @Lat1 = @Lat1 / 57.2958  
      SET @Long1 = @Long1 / 57.2958  
      SET @Lat2 = @Lat2 / 57.2958  
      SET @Long2 = @Long2 / 57.2958  
      -- Calculate distance  
      SET @distance = (SIN(@Lat1) * SIN(@Lat2)) + (COS(@Lat1) * COS(@Lat2) * COS(@Long2 - @Long1))  
      --Convert to miles  
      IF @distance <> 0  
      BEGIN  
        SET @distance = 3958.75 * ATAN(SQRT(1 - POWER(@distance, 2)) / @distance);  
      END  
      RETURN @distance  
    END
    GO
    ```
  
    - La funzione è una funzione con valori scalari che restituisce un singolo valore di dati di un tipo predefinito.
  
    - Accetta come input valori di latitudine e longitudine, ottenuti dalle località di inizio e fine della corsa. La formula dell'emisenoverso converte le posizioni in radianti e usa tali valori per calcolare la distanza diretta in miglia tra queste due posizioni.

## <a name="generate-the-features-using-_fnengineerfeatures_"></a>Generare le caratteristiche usando _fnEngineerFeatures_

Per aggiungere il valore calcolato a una tabella da usare per il training del modello, è possibile usare un'altra funzione, _fnEngineerFeatures_. La nuova funzione chiama la funzione T-SQL _fnCalculateDistance_ creata in precedenza per ottenere la distanza diretta tra i punti di inizio e fine della corsa. 

1. Osservare il codice della funzione T-SQL personalizzata _fnEngineerFeatures_, creata in preparazione a questa procedura dettagliata.
  
    ```sql
    CREATE FUNCTION [dbo].[fnEngineerFeatures] (  
    @passenger_count int = 0,  
    @trip_distance float = 0,  
    @trip_time_in_secs int = 0,  
    @pickup_latitude float = 0,  
    @pickup_longitude float = 0,  
    @dropoff_latitude float = 0,  
    @dropoff_longitude float = 0)  
    RETURNS TABLE  
    AS
      RETURN
      (
      -- Add the SELECT statement with parameter references here
      SELECT
        @passenger_count AS passenger_count,
        @trip_distance AS trip_distance,
        @trip_time_in_secs AS trip_time_in_secs,
        [dbo].[fnCalculateDistance](@pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude) AS direct_distance
  
      )
    GO
    ```

    + È una funzione con valori di tabella che accetta come input più colonne e restituisce una tabella con più colonne di funzionalità.

    + Scopo della funzione è la creazione di nuove caratteristiche da usare nella compilazione di un modello.

2.  Per verificare che la funzione operi in modo corretto, usarla per calcolare la distanza geografica per i viaggi in cui la distanza sul tassametro era pari a 0 ma i punti di inizio e fine corsa erano diversi.
  
    ```sql
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,
        trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance
        FROM nyctaxi_sample
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0
        ORDER BY trip_time_in_secs DESC
    ```
  
    Come si può notare, la distanza indicata dal tassametro non corrisponde sempre alla distanza geografica. Ecco perché la progettazione delle funzionalità è così importante. È possibile usare queste caratteristiche dei dati migliorate per eseguire il training di un modello di Machine Learning con R.

## <a name="next-lesson"></a>Lezione successiva

[Lezione 3: Eseguire il training e il salvataggio di un modello usando T-SQL](sqldev-train-and-save-a-model-using-t-sql.md)

## <a name="previous-lesson"></a>Lezione precedente

[Lezione 1: Esplorare e visualizzare i dati con R e stored procedure](sqldev-explore-and-visualize-the-data.md)
