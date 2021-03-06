---
description: Finestra di dialogo Importa criteri
title: Finestra di dialogo Importa criteri | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql13.swb.dmf.importpolicy.f1
ms.assetid: 78ab5f6e-2f13-4788-937e-8892ef4e2345
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8cd6f4223d3cf23d9ccd98f5b8e4f787872132f3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423695"
---
# <a name="import-policies-dialog-box"></a>Finestra di dialogo Importa criteri
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Utilizzare questa finestra di dialogo per importare nell'istanza corrente del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] i criteri salvati come file XML e le relative condizioni di riferimento.  
  
## <a name="options"></a>Opzioni  
 **File da importare**  
 Per importare i criteri da un file XML, digitare il percorso e il nome del file oppure usare il pulsante Sfoglia (**...**).  
  
 **Sostituisci duplicati con gli elementi importati**  
 Selezionare questa opzione per sovrascrivere eventuali criteri o condizioni con lo stesso nome che esistono già nell'istanza corrente del [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Non è possibile sovrascrivere una condizione con criteri dipendenti, a meno che non vengano sovrascritti anche questi ultimi. Se questa opzione non viene selezionata, una condizione esistente che utilizza la stessa espressione di condizione non genererà un errore.  
  
 **Stato criteri**  
 Consente di selezionare lo stato desiderato per i criteri importati:  
  
-   **Mantieni lo stato dei criteri durante l'importazione**  
  
-   **Abilita tutti i criteri durante l'importazione**  
  
-   **Disabilita tutti i criteri durante l'importazione**  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione di server tramite la gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Importare i criteri della gestione basata su criteri](../../relational-databases/policy-based-management/import-a-policy-based-management-policy.md)   
 [Esportare i criteri della gestione basata su criteri](../../relational-databases/policy-based-management/export-a-policy-based-management-policy.md)  
  
  
