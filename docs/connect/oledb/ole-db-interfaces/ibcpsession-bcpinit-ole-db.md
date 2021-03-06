---
title: IBCPSession::BCPInit (OLE DB Driver) | Microsoft Docs
description: Informazioni su come il metodo IBCPSession::BCPInit esegue le inizializzazioni necessarie per una copia bulk dei dati tra la workstation e SQL Server.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IBCPSession::BCPInit (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPInit method
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a6557d0df9ce36aef689bad501eedfbe0b299ac8
ms.sourcegitcommit: 7eb80038c86acfef1d8e7bfd5f4e30e94aed3a75
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2020
ms.locfileid: "92081810"
---
# <a name="ibcpsessionbcpinit-ole-db"></a>IBCPSession::BCPInit (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Inizializza la struttura della copia bulk, esegue alcune operazioni di controllo degli errori, verifica che i dati e i nomi dei file di formato siano corretti, quindi li apre.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
HRESULT BCPInit(   
      const wchar_t *pwszTable,  
      const wchar_t *pwszDataFile,  
      const wchar_t *pwszErrorFile,  
      int eDirection);  
```  
  
## <a name="remarks"></a>Osservazioni  
 Il metodo **BCPInit** deve essere chiamato prima di qualsiasi altro metodo di copia bulk. Il metodo **BCPInit** esegue le inizializzazioni necessarie per una copia bulk dei dati tra la workstation e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Il metodo **BCPInit** esamina la struttura dell'origine del database o della tabella di destinazione, non il file di dati. Specifica i valori relativi al formato dei dati per il file di dati in base a ogni colonna nella vista o nella tabella di database o nel set di risultati SELECT. Questa specifica include il tipo di dati di ogni colonna, la presenza o meno di un indicatore di lunghezza o Null e di stringhe di byte con carattere di terminazione nei dati e la larghezza dei tipi di dati a lunghezza fissa. Il metodo **BCPInit** imposta questi valori nel modo seguente:  
  
-   Il tipo di dati specificato è quello della colonna della vista o della tabella di database oppure del set di risultati SELECT. Il tipo di dati viene enumerato dai tipi di dati nativi di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specificati nel file di intestazione di OLE DB Driver per SQL Server (msoledbsql.h). I relativi valori utilizzano il modello BCP_TYPE_XXX. I dati vengono rappresentati nel relativo formato elettronico, ovvero i dati di una colonna di un tipo di dati integer vengono rappresentati da una sequenza a quattro byte, di tipo big o little endian a seconda del computer con il quale è stato creato il file di dati.  
  
-   Se un tipo di dati del database ha una lunghezza fissa, anche i dati del file di dati presenteranno una lunghezza fissa. I metodi di copia bulk che elaborano dati, ad esempio [IBCPSession::BCPExec](../../oledb/ole-db-interfaces/ibcpsession-bcpexec-ole-db.md), analizzano le righe di dati prevedendo che la lunghezza dei dati nel file sia identica alla lunghezza dei dati specificata nella vista o nella tabella di database o nell'elenco di colonne SELECT. I dati di una colonna del database definiti come `char(13)` devono, ad esempio, essere rappresentati da 13 caratteri per ogni riga di dati nel file. I dati a lunghezza fissa possono essere preceduti da un indicatore Null se la colonna del database consente valori Null.  
  
-   Quando si copiano dati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il file di dati deve includere dati per ogni colonna nella tabella di database. Quando si copiano dati da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], i dati di tutte le colonne della vista o della tabella di database o del set di risultati SELECT vengono copiati nel file di dati.  
  
-   Quando si copiano dati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la posizione ordinale di una colonna nel file di dati deve essere identica alla posizione ordinale della colonna nella tabella di database. Quando si copiano dati da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il metodo **BCPExec** dispone i dati in base alla posizione ordinale della colonna nella tabella di database.  
  
-   Se un tipo di dati del database ha una lunghezza variabile, ad esempio `varbinary(22)`, o se una colonna del database può contenere valori Null, i dati nel file di dati sono preceduti da un indicatore di lunghezza o Null. La larghezza dell'indicatore varia in base al tipo di dati e alla versione della copia bulk. L'opzione BCP_OPTION_FILEFMT del metodo [IBCPSession::BCPControl](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) fornisce compatibilità tra i file di dati di copia bulk precedenti e i server che eseguono versioni successive di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] indicando quando la larghezza degli indicatori nei dati è inferiore a quella prevista.  
  
> [!NOTE]  
>  Per modificare i valori relativi al formato dei dati specificati per un file di dati, utilizzare i metodi [IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) e [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md).  
  
 Le copie bulk in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] possono essere ottimizzate per le tabelle che non contengono indici impostando l'opzione del database **select into/bulkcopy**.  
  
## <a name="arguments"></a>Argomenti  
 *pwszTable*[in]  
 Nome della tabella di database per la copia interna o esterna. Il nome può includere il nome del database o del proprietario, ad esempio "pubs.username.titles", "pubs..titles", "username.titles".  
  
 Se l'argomento eDirection è impostato su BCP_DIRECTION_OUT, l'argomento pwszTable può essere il nome di una vista di database.  
  
 Se l'argomento eDirection è impostato su BCP_DIRECTION_OUT e viene specificata un'istruzione SELECT utilizzando il metodo **BCPControl** prima che venga chiamato il metodo **BCPExec**, è necessario impostare l'argomento *pwszTable* su NULL.  
  
 *pwszDataFile*[in]  
 Nome del file utente per la copia interna o esterna.  
  
 *pwszErrorFile*[in]  
 Nome del file degli errori in cui inserire messaggi di stato, messaggi di errore e copie delle righe che non è stato possibile copiare da un file utente in una tabella. Se l'argomento *pwszErrorFile* è impostato su NULL, non viene usato alcun file degli errori.  
  
 *eDirection*[in]  
 Direzione dell'operazione di copia, BCP_DIRECTION_IN o BCP_DIRECTION _OUT. BCP_DIRECTION _IN indica una copia da un file utente in una tabella di database e BCP_DIRECTION _OUT indica una copia da una tabella di database in un file utente.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 S_OK  
 Il metodo è riuscito.  
  
 E_FAIL  
 Si è verificato un errore specifico del provider. Per informazioni dettagliate, usare l'interfaccia [ISQLServerErrorInfo](./isqlservererrorinfo-geterrorinfo-ole-db.md).  
  
 E_OUTOFMEMORY  
 Errore di memoria insufficiente.  
  
 E_INVALIDARG  
 Uno o più argomenti non sono stati specificati correttamente, ad esempio è stato immesso un nome file non valido.  
  
## <a name="see-also"></a>Vedere anche  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Esecuzione di operazioni di copia bulk](../../oledb/features/performing-bulk-copy-operations.md)  
  
