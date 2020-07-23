---
title: Generare ed eseguire lo script di registrazione supplementare | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6b78ee09c6ecdbbdb18cd48ef7d765841e3d8a60
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921601"
---
# <a name="generate-and-run-the-supplemental-logging-script"></a>Generare ed eseguire lo script di registrazione supplementare

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Utilizzare la pagina Set up Tables for Capturing Changes per eseguire uno script nel database di origine Oracle per l'impostazione della registrazione supplementare.  
  
 **Per eseguire gli script di registrazione supplementare**  
  
 Fare clic su **Run Script** per eseguire lo script di registrazione supplementare nelle tabelle definite per l'istanza di CDC. Tramite questo script verranno scritte tutte le colonne di interesse nei log delle transazioni durante la registrazione delle operazioni UPDATE nelle tabelle acquisite. Lo script viene in genere esaminato ed eseguito da un amministratore di sistema Oracle.  
  
 È anche possibile eseguire gli script manualmente tramite SQL * Plus.  
  
 **Per eseguire gli script manualmente**  
  
 Scegliere **Copy** per incollare lo script negli Appunti. Aprire SQL* Plus e accedere alla directory contenente il database di origine Oracle. Incollare lo script in SQL\*Plus per eseguirlo.  
  
 Per salvare lo script di registrazione supplementare in un file di testo, scegliere **Save as** e accedere al percorso in cui si desidera salvare il file. Assegnare un nome al file e scegliere **Save** per salvarlo.  
  
 Scegliere **Next** per [Generate Mirror Tables and CDC Capture Instances](../../integration-services/change-data-capture/generate-mirror-tables-and-cdc-capture-instances.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura di creazione dell'istanza del database delle modifiche di SQL Server](../../integration-services/change-data-capture/how-to-create-the-sql-server-change-database-instance.md)   
 [Rivedere e generare script di registrazione supplementare](../../integration-services/change-data-capture/review-and-generate-supplemental-logging-scripts.md)  
  
  
