---
title: MSSQLSERVER_1904 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1904 (Database Engine error)
ms.assetid: 2a35d57d-74e2-45a2-8f67-3f2e51d69712
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 119ff7b3bb46e0ea05f1e3cbe87f497132468713
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62869372"
---
# <a name="mssqlserver_1904"></a>MSSQLSERVER_1904
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|1904|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|KEYCOUNT|  
|Testo del messaggio|Per l'oggetto %S_MSG '%.*ls' nella tabella '%.\*ls' sono presenti %d nomi di colonna nell'elenco chiavi %S_MSG. Il limite massimo per l'elenco delle colonne chiave per indici o statistiche è di %d.|  
  
## <a name="explanation"></a>Spiegazione  
 Il numero di colonne chiave nell'elenco per le statistiche o l'indice specificato supera il numero massimo di colonne consentite.  
  
## <a name="user-action"></a>Azione dell'utente  
 Modificare l'elenco delle colonne chiave in modo da non includere un numero di colonne superiore a quello specificato.  
  
 Per gli indici non cluster, utilizzare la clausola INCLUDE nell'istruzione CREATE INDEX per aggiungere colonne all'indice come colonne non chiave. In questo modo si evita di superare la limitazione relativa alla dimensione di indice corrente che consente al massimo 16 colonne chiave. Per altre informazioni, vedere [Creare indici con colonne incluse](../indexes/create-indexes-with-included-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql)  
  
  
