---
title: Opzione Annulla (strumento di amministrazione Riesecuzione distribuita) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
author: stevestein
ms.author: sstein
ms.openlocfilehash: d132fbf5ce541a2bdab82e44dc55e6fc92df536d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85007745"
---
# <a name="cancel-option-distributed-replay-administration-tool"></a>Opzione cancel (strumento di amministrazione Distributed Replay)
  Lo [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] strumento di amministrazione riesecuzione distribuita, `DReplay.exe` , è uno strumento da riga di comando che è possibile utilizzare per comunicare con il controller di riesecuzione distribuita. Questo argomento descrive l'opzione della riga di comando **cancel** e la sintassi corrispondente.

 L'opzione **cancel** annulla l'operazione corrente in esecuzione nel controller.

 ![Icona di collegamento all'argomento](../../database-engine/media/topic-link.gif "Icona di collegamento a un argomento") Per altre informazioni sulle convenzioni relative alla sintassi dello strumento di amministrazione, vedere [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).

## <a name="syntax"></a>Sintassi

```

dreplay cancel [-mcontroller] [-q] 
```

#### <a name="parameters"></a>Parametri
 **-m** *controller* nome computer del controller. È possibile utilizzare "`localhost`" o "`.`" per fare riferimento al computer locale.

 Se il parametro **-m** non è specificato, viene usato il computer locale.

 **-q** Modalità non interattiva. Non viene richiesta alcuna conferma da parte dell'utente.

 Il parametro **-q** è facoltativo.

## <a name="examples"></a>Esempi
 Nell'esempio seguente viene inviata una richiesta di annullamento in modalità non interattiva. Il valore `localhost` indica che il servizio controller viene eseguito nello stesso computer dello strumento di amministrazione.

```
dreplay cancel -m localhost -q
```

## <a name="permissions"></a>Autorizzazioni
 È necessario eseguire lo strumento di amministrazione come utente interattivo, scegliendo tra utente locale e account utente di dominio. Per utilizzare un account utente locale, lo strumento di amministrazione e il controller devono essere eseguiti nello stesso computer.

 Per altre informazioni, vedere [Sicurezza di Distributed Replay](distributed-replay-security.md).

## <a name="see-also"></a>Vedere anche
 [SQL Server Distributed Replay](sql-server-distributed-replay.md)


