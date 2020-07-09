---
title: NEWSEQUENTIALID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- NEWSEQUENTIALID
- NEWSEQUENTIALID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- NEWSEQUENTIALID function
- GUIDs [SQL Server]
ms.assetid: e06d2cab-f1ff-42f1-8550-6aaec57be36f
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: c4daa39922e25c67479ad4f49c28fa860303e6d4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784387"
---
# <a name="newsequentialid-transact-sql"></a>NEWSEQUENTIALID (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Crea un GUID maggiore di qualsiasi GUID generato in precedenza da questa funzione in un computer specificato dall'avvio di Windows. Dopo avere riavviato Windows, è possibile avviare di nuovo il GUID da un intervallo inferiore, ma ancora globalmente univoco. Quando una colonna GUID viene utilizzata come identificatore di riga, l'utilizzo di NEWSEQUENTIALID può essere più veloce rispetto all'utilizzo della funzione NEWID, poiché la funzione NEWID causa un'attività casuale e utilizza un numero inferiore di pagine di dati memorizzate nella cache. L'utilizzo di NEWSEQUENTIALID consente inoltre di completare le pagine di dati e di indice.  
  
> [!IMPORTANT]  
>  In caso di problemi di riservatezza, non utilizzare questa funzione. È possibile intuire il valore del GUID che verrà generato successivamente e accedere ai dati associati a tale GUID.  
  
 NEWSEQUENTIALID è un wrapper sulla funzione [UuidCreateSequential](https://go.microsoft.com/fwlink/?LinkId=164027) di Windows, a cui è [applicata una riproduzione casuale](https://blogs.msdn.microsoft.com/dbrowne/2012/07/03/how-to-generate-sequential-guids-for-sql-server-in-net/).
  
> [!WARNING]  
>  La funzione UuidCreateSequential ha dipendenze hardware. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si possono sviluppare cluster di valori sequenziali quando i database (ad esempio, i database indipendenti) vengono spostati in altri computer. Quando si usa Always On in [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)], si possono sviluppare cluster di valori sequenziali se si effettua il failover del database in un computer diverso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
NEWSEQUENTIALID ( )  
```  
  
## <a name="return-type"></a>Tipo restituito  
 **uniqueidentifier**  
  
## <a name="remarks"></a>Osservazioni  
 La funzione NEWSEQUENTIALID() può essere usata solo con vincoli DEFAULT su colonne di tabella di tipo **uniqueidentifier**. Ad esempio:  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT NEWSEQUENTIALID());   
```  
  
 Quando viene specificata in espressioni DEFAULT, la funzione NEWSEQUENTIALID() non può essere utilizzata in combinazione con altri operatori scalari. Ad esempio, la seguente operazione non è valida:  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT dbo.myfunction(NEWSEQUENTIALID()));  
```  
  
 Nell'esempio precedente `myfunction()` è una funzione scalare definita dall'utente che accetta e restituisce un valore `uniqueidentifier`.  
  
 Non è possibile fare riferimento a NEWSEQUENTIALID all'interno di query.  
  
 È possibile usare NEWSEQUENTIALID per generare GUID in modo da ridurre le divisioni di pagina e le operazioni di I/O casuali a livello foglia degli indici.  
  
 Ogni GUID generato usando NEWSEQUENTIALID è univoco nel computer. I GUID generati usando NEWSEQUENTIALID sono univoci in più computer solo se il computer di origine dispone di una scheda di rete.  
  
## <a name="see-also"></a>Vedere anche  
 [NEWID &#40;Transact-SQL&#41;](../../t-sql/functions/newid-transact-sql.md)   
 [Operatori di confronto &#40;Transact-SQL&#41;](../../t-sql/language-elements/comparison-operators-transact-sql.md)  
  
  
