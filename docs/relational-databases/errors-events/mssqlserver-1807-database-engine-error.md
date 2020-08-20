---
description: MSSQLSERVER_1807
title: MSSQLSERVER_1807 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5b6b4d42d13539d62f7afc7cc341f2b7b1bee44f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456313"
---
# <a name="mssqlserver_1807"></a>MSSQLSERVER_1807
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Dettagli  
  
| Attributo | valore |  
| :-------- | :---- |  
|Nome prodotto|SQL Server|  
|ID evento|1807|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|CANNOT_EX_LOCK|  
|Testo del messaggio|Impossibile ottenere il blocco esclusivo sul database '%.*ls'. Ripetere l'operazione in un secondo momento.|  
  
## <a name="explanation"></a>Spiegazione  
Non è possibile ottenere l'accesso esclusivo al database necessario per l'esecuzione di un'operazione.  
  
## <a name="user-action"></a>Azione dell'utente  
Disconnettere tutte le connessioni al database oppure eseguire nuovamente la query in un secondo momento.  
  
