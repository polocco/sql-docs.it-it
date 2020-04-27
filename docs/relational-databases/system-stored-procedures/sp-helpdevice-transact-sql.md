---
title: sp_helpdevice (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpdevice
- sp_helpdevice_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdevice
ms.assetid: 1a5eafa7-384e-4691-ba05-978eb73bbefb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0db0242e5bdd9e04d3d7c424382933121c2e0ac2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "67902987"
---
# <a name="sp_helpdevice-transact-sql"></a>sp_helpdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza informazioni sui dispositivi di backup di Microsoft® SQL Server™.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]È consigliabile utilizzare invece la vista del catalogo [sys. backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md)  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpdevice [ [ @devname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @devname = ] 'name'`Nome del dispositivo di backup per cui vengono segnalate le informazioni. Il valore di *Name* è sempre di **tipo sysname**.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**device_name**|**sysname**|Nome logico del dispositivo.|  
|**physical_name**|**nvarchar(260)**|Nome fisico del file.|  
|**Descrizione**|**nvarchar(255)**|Descrizione del dispositivo.|  
|**Stato**|**int**|Numero che corrisponde alla descrizione dello stato nella colonna **Descrizione** .|  
|**cntrltype**|**smallint**|Tipo di controller del dispositivo:<br /><br /> 2 = dispositivo disco<br /><br /> 5 = dispositivo nastro|  
|**size**|**int**|Dimensioni del dispositivo espresse in pagine da 2 KB.|  
  
## <a name="remarks"></a>Osservazioni  
 Se si specifica *Name* , **sp_helpdevice** Visualizza informazioni sul dispositivo di dump specificato. Se il *nome* non è specificato, **sp_helpdevice** Visualizza le informazioni su tutti i dispositivi di dump nella vista del catalogo **sys. backup_devices** .  
  
 I dispositivi di dump vengono aggiunti al sistema utilizzando **sp_addumpdevice**.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono visualizzate le informazioni su tutti i dispositivi di dump in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_helpdevice;  
```  
  
## <a name="see-also"></a>Vedi anche  
 [sp_addumpdevice &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [Stored procedure di motore di database &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
