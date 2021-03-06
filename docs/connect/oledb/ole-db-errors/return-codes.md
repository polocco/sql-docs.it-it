---
title: Codici restituiti (OLE DB Driver)
description: Informazioni sui codici restituiti per le funzioni membro di OLE DB Driver per SQL Server e su come ottenere altre informazioni sui risultati oltre all'esito positivo.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB error handling, return codes
- OLE DB Driver for SQL Server, errors
- failed function [OLE DB]
- successful function [OLE DB]
- S_FALSE
- IS_ERROR macro
- DB_S_ERRORSOCCURRED return
- return codes [OLE DB]
- S_OK
- FAILED macro
- errors [OLE DB], return codes
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe59f14e43a32d6c6b3239c24f1be665e7bbad82
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727183"
---
# <a name="return-codes"></a>Codici restituiti
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Al livello più elementare, una funzione membro può avere esito positivo o negativo. A un livello più approfondito, una funzione può avere esito positivo, ma tale esito potrebbe non corrispondere alle previsioni dello sviluppatore dell'applicazione.  
  
 Per altre informazioni sui codici restituiti OLE DB, vedere [Codici restituiti (OLE DB)](/previous-versions/windows/desktop/ms725451(v=vs.85)).  
  
 Quando una funzione membro di OLE DB Driver per SQL Server restituisce S_OK, significa che la funzione ha avuto esito positivo.  
  
 Quando una funzione membro del driver OLE DB per SQL Server non restituisce S_OK, le macro FAILED e IS_ERROR che decomprimono HRESULT OLE/COM possono determinare l'esito positivo o negativo complessivo di una funzione.  
  
 Se FAILED o IS_ERROR restituisce TRUE, il consumer del driver OLE DB per SQL Server ha la conferma dell'esito negativo dell'esecuzione della funzione membro. Se FAILED o IS_ERROR restituisce FALSE e il valore HRESULT è diverso da S_OK, il consumer di OLE DB Driver per SQL Server ha la conferma dell'esito positivo della funzione. Il consumer può recuperare informazioni dettagliate su questa restituzione di "esito positivo con informazioni" dalle interfacce di errore del driver OLE DB per SQL Server. Anche nel caso in cui una funzione abbia un esito chiaramente negativo (la macro FAILED restituisce TRUE), le interfacce di errore del driver OLE DB per SQL Server rendono disponibili informazioni dettagliate sull'errore.  
  
 I consumer di OLE DB Driver per SQL Server in genere ricevono il valore HRESULT di "esito positivo con informazioni" di DB_S_ERRORSOCCURRED. Le funzioni membro che restituiscono DB_S_ERRORSOCCURRED definiscono in genere uno o più parametri che forniscono al consumer i valori di stato. Poiché è possibile che le uniche informazioni a disposizione del consumer siano quelle restituite nei parametri dei valori di stato, è necessario implementare la logica dell'applicazione per il recupero dei valori di stato quando sono disponibili.  
  
 Le funzioni membro di OLE DB Driver per SQL Server non restituiscono il codice di esito positivo S_FALSE. Tutte le funzioni membro di OLE DB Driver per SQL Server restituiscono sempre S_OK per indicare l'esito positivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori](../../oledb/ole-db-errors/errors.md)  
  
