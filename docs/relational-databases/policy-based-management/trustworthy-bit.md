---
description: Bit relativo alla proprietà trustworthy
title: Bit relativo alla proprietà trustworthy | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: de262aed0eb2a731dac17dbb018883211eda11ee
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88380277"
---
# <a name="trustworthy-bit"></a>Bit relativo alla proprietà trustworthy
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Questa regola consente di determinare se il ruolo dbo per un database è assegnato al ruolo predefinito del server sysadmin e se per il database il bit relativo alla proprietà trustworthy è impostato su ON.  
  
 Se queste condizioni vengono soddisfatte, un utente di database con privilegi potrà elevare il livello di privilegi al ruolo sysadmin. In questo ruolo l'utente può creare ed eseguire assembly non protetti che potrebbero danneggiare il sistema.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Disattivare il bit relativo alla proprietà trustworthy o revocare le autorizzazioni sysadmin al ruolo del database dbo.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
