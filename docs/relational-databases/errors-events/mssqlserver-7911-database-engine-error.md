---
title: MSSQLSERVER_7911 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7911 (Database Engine error)
ms.assetid: dd8390f3-0f77-4fb2-ba94-631a56e42bc6
author: MashaMSFT
ms.author: mathoma
robots: noindex,nofollow
ms.openlocfilehash: 11de06ae76c02e2079a790d451bcc3037f470fb1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85793130"
---
# <a name="mssqlserver_7911"></a>MSSQLSERVER_7911
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Dettagli  
  
| Attributo | valore |  
| :-------- | :---- |  
|Nome prodotto|SQL Server|  
|ID evento|7911|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC2_REPAIR_PAGE_DEALLOCATED|  
|Testo del messaggio|Correzione: la pagina P_ID è stata deallocata all'oggetto con ID O_ID, indice con ID I_ID, partizione con ID PN_ID, unità allocazione con ID A_ID (tipo TYPE).|  
  
## <a name="explanation"></a>Spiegazione  
Si tratta di un messaggio informativo generato dall'istruzione REPAIR in cui viene indicato che una pagina è stata deallocata dalla matrice di slot a pagina singola di una mappa di allocazione degli indici (IAM, Index Allocation Map).  
  
## <a name="user-action"></a>Azione dell'utente  
nessuno  
  
