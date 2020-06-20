---
title: Rimuovere istruzioni che modificano oggetti di sistema | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 526181bc4bf7ab81df2eaa25f19e7627c9b7af10
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059156"
---
# <a name="remove-statements-that-modify-system-objects"></a>Rimuovere le istruzioni che modificano oggetti di sistema
  Sono state rilevate istruzioni che aggiornano il catalogo di sistema. Gli aggiornamenti diretti del catalogo di sistema non sono consentiti. Modificare gli script SQL in modo che utilizzino API ufficiali e documentate.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Descrizione  
 Gli aggiornamenti diretti del catalogo di sistema non sono consentiti. Qualsiasi tentativo di eseguire questa operazione restituirà l'errore seguente:  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a>Azione correttiva  
 Modificare gli script SQL in modo che utilizzino API ufficiali e documentate. Utilizzare, ad esempio, ALTER DATABASE *database_name* set Emergency anziché eseguire un'istruzione Update sulla tabella di sistema **sysdatabases** .  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 preparazione aggiornamento &#91;nuova&#93;](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
