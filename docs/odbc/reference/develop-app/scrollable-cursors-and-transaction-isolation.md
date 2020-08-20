---
description: Cursori scorrevoli e isolamento delle transazioni
title: Cursori scorrevoli e isolamento delle transazioni | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- isolation levels [ODBC]
- scrollable cursors [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: f0216f4a-46e3-48ae-be0a-e2625e8403a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 790b2d0c4d80c821645c3a4360d1295cc55a8a4e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476503"
---
# <a name="scrollable-cursors-and-transaction-isolation"></a>Cursori scorrevoli e isolamento delle transazioni
Nella tabella seguente sono elencati i fattori che determinano la visibilità delle modifiche.  
  
|Modifiche apportate da:|La visibilità dipende da:|  
|----------------------|----------------------------|  
|Cursore|Tipo di cursore, implementazione del cursore|  
|Altre istruzioni nella stessa transazione|Tipo di cursore|  
|Istruzioni in altre transazioni|Tipo di cursore, livello di isolamento della transazione|  
  
 Questi fattori sono illustrati nella figura seguente.  
  
 ![Fattori che controllano la visibilità delle modifiche](../../../odbc/reference/develop-app/media/pr23.gif "pr23")  
  
 Nella tabella seguente è riepilogata la possibilità di ogni tipo di cursore di rilevare le modifiche apportate da se stesso, da altre operazioni nella propria transazione e da altre transazioni. La visibilità delle ultime modifiche dipende dal tipo di cursore e dal livello di isolamento della transazione contenente il cursore.  
  
|Cursore type\action|Self|Proprio<br /><br /> Transazione|Altro<br /><br /> Transazione<br /><br /> (UR [a])|Altro<br /><br /> Transazione<br /><br /> (RC [a])|Altro<br /><br /> Transazione<br /><br /> (RR [a])|Altro<br /><br /> Transazione<br /><br /> (S [a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|Statico|||||||  
|Insert|Forse [b]|No|No|No|No|No|  
|Aggiornamento|Forse [b]|No|No|No|No|No|  
|Delete|Forse [b]|No|No|No|No|No|  
|Gestito da keyset|||||||  
|Insert|Forse [b]|No|No|No|No|No|  
|Aggiornamento|Sì|Sì|Sì|Sì|No|No|  
|Delete|Forse [b]|Sì|Sì|Sì|No|No|  
|Dinamico|||||||  
|Insert|Sì|Sì|Sì|Sì|Sì|No|  
|Aggiornamento|Sì|Sì|Sì|Sì|No|No|  
|Elimina|Sì|Sì|Sì|Sì|No|No|  
  
 [a] le lettere tra parentesi indicano il livello di isolamento della transazione contenente il cursore. il livello di isolamento dell'altra transazione, in cui è stata apportata la modifica, è irrilevante.  
  
 UR: lettura di cui non è stato eseguito il commit  
  
 RC: Read Committed  
  
 RR: lettura ripetibile  
  
 S: serializzabile  
  
 [b] dipende dalla modalità di implementazione del cursore. Se il cursore è in grado di rilevare tali modifiche viene segnalato tramite l'opzione SQL_STATIC_SENSITIVITY in **SQLGetInfo**.
