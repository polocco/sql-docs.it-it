---
description: Creare self-join in modo automatico (Visual Database Tools)
title: Creare self-join in modo automatico
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 3792e29ae83d28e8c695cfebbd5fc086fe4c267b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468383"
---
# <a name="create-self-joins-automatically-visual-database-tools"></a>Creare self-join in modo automatico (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Se una tabella ha una relazione riflessiva nel database, sarà possibile metterla in join con se stessa automaticamente.  
  
### <a name="to-create-a-self-join-automatically"></a>Per creare automaticamente un self-join  
  
1.  Aggiungere la tabella appropriata al [riquadro Diagramma](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) .  
  
2.  Aggiungere nuovamente la stessa tabella in modo che venga visualizzata due volte nel riquadro Diagramma.  
  
    In [Progettazione query e Progettazione viste](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) verrà assegnato un alias alla seconda istanza aggiungendo un numero sequenziale al nome della tabella. Inoltre, verrà inserita una linea di join tra i due rettangoli che rappresentano i due diversi tipi di partecipazione della tabella nella query.  
  
## <a name="see-also"></a>Vedere anche  
[Eseguire query con join &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
