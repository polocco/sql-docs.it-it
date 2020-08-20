---
description: MSSQLSERVER_8525
title: MSSQLSERVER_8525 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "8525"
helpviewer_keywords:
- 8525 (Database Engine error)
ms.assetid: 297867c1-691e-4d6b-a3be-a7575015ecfa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eb5b5812aac0cf4e6a15d45806b84c68294398dc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482703"
---
# <a name="mssqlserver_8525"></a>MSSQLSERVER_8525
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Dettagli  
  
| Attributo | valore |  
| :-------- | :---- |  
|Nome prodotto|SQL Server|  
|ID evento|8525|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico||  
|Testo del messaggio|La transazione distribuita è stata completata. Integrare questa sessione in una nuova transazione o nella transazione NULL.|  
  
## <a name="explanation"></a>Spiegazione  
Il modello di programmazione per l'uso di Distributed Transaction Coordinator con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] richiede alle applicazioni l'integrazione esplicita in una transazione distribuita o l'esclusione esplicita da essa.  
  
Questo errore si verifica quando vengono soddisfatte le quattro condizioni seguenti:  
  
-   L'applicazione è stata integrata in una transazione distribuita.  
  
-   La transazione di cui è stato eseguito il commit o il rollback, è stata interrotta per un motivo qualsiasi.  
  
-   L'applicazione utente non è stata esclusa in modo esplicito da una transazione distribuita o integrata in modo esplicito in una nuova transazione distribuita.  
  
-   L'applicazione tenta di eseguire qualsiasi operazione transazionale, ad eccezione dell'esclusione da una transazione distribuita esistente o dell'integrazione in una nuova transazione distribuita, ad esempio l'esecuzione di una query o l'avvio di una transazione locale.  
  
Lo stato di errore 1 viene utilizzato quando l'applicazione esegue un'operazione che consente di creare transazioni locali. Lo stato 2 viene utilizzato quando l'applicazione tenta l'integrazione in una sessione associata.  
  
## <a name="user-action"></a>Azione dell'utente  
Dopo l'integrazione in una transazione distribuita, l'applicazione deve essere esclusa in modo esplicito dalla transazione distribuita o integrata in un'altra transazione distribuita. Ciò determina l'esclusione implicita da una transazione inclusa in precedenza. Per informazioni sulla sintassi esatta da utilizzare per l'esclusione da una transazione distribuita o l'inclusione in essa, vedere il manuale dell'interfaccia di programmazione per l'applicazione.  
  
