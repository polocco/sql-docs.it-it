---
title: Impostare il periodo di memorizzazione cronologia (SSMS)
description: Informazioni su come impostare il periodo di memorizzazione cronologia in SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- history retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: c288daab-5181-4d4b-ba2a-8a147098e758
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: bc04a0b78c93666b4213acea3a1f59af5dc5b5fb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767653"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a>Impostazione del periodo di memorizzazione della cronologia (SQL Server Management Studio)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Specificare il periodo di memorizzazione della cronologia nella pagina **Generale** della finestra di dialogo **Proprietà database di distribuzione - \<DistributionDatabase>** . Questa impostazione controlla per quanto tempo verrà archiviata la cronologia dell'agente di replica. La pagina è accessibile dalla pagina **Generale** della finestra di dialogo **Proprietà database di distribuzione - \<Distributor>** . Per altre informazioni sull'accesso a questa finestra di dialogo, vedere [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-history-retention-period"></a>Per specificare il periodo di memorizzazione della cronologia  
  
1.  Nella pagina **Generale** della finestra di dialogo **Proprietà database di distribuzione - \<Distributor>** fare clic sul pulsante delle proprietà ( **...** ) relativo al database di distribuzione.  
  
2.  Immettere un valore nella casella **Archivia cronologia prestazioni di replica per almeno** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare la distribuzione](../../relational-databases/replication/configure-distribution.md)  
  
  
