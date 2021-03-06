---
title: Posizionamento dei file di backup in dispositivi separati rispetto ai file di database
description: Informazioni su come abilitare un criterio per controllare la posizione del file di backup rispetto alla posizione dei file di database per la gestione basata su criteri con SQL Server.
ms.custom: seo-lt-2019
ms.date: 08/31/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 5b98f8163a3564ccc4aadac6c71c30eb5cf37697
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/01/2020
ms.locfileid: "89285247"
---
# <a name="backup-files-must-be-on-separate-devices-from-the-database-files"></a>Posizionamento dei file di backup in dispositivi separati rispetto ai file di database
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Questa regola consente di controllare se i file di database si trovano in dispositivi separati rispetto ai file di backup. Se file di database e i file di backup sono archiviati nello stesso dispositivo e si verifica un errore nel dispositivo, il database e i backup non saranno disponibili. L'archiviazione dei file di database e di backup in dispositivi distinti, inoltre, consente di ottimizzare le prestazioni di I/O per l'utilizzo del database in un ambiente di produzione e per la scrittura dei backup.  
  
## <a name="best-practices-recommendations"></a>Raccomandazioni per le procedure consigliate  
 È consigliabile utilizzare come disco di backup un disco diverso da quelli in cui sono archiviati i dati di database e i log. Questa condizione è necessaria per garantire l'accesso ai backup in caso di errore del disco contenente il log o i dati.

Se file di database e i file di backup sono archiviati nello stesso dispositivo e si verifica un errore nel dispositivo, il database e i backup non saranno disponibili. L'archiviazione dei file di database e di backup in dispositivi distinti, inoltre, consente di ottimizzare le prestazioni di I/O per l'utilizzo del database in un ambiente di produzione e per la scrittura dei backup.
  
## <a name="see-also"></a>Vedere anche 
   
  
 [Dispositivi di backup](../backup-restore/backup-devices-sql-server.md)  
  
