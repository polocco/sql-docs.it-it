---
title: Advanced Connection Properties | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4edfab68-7e68-45e8-a3f3-a0049ff7eb9e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a7a5744aa2adcaab74ca09bbb962c8c69d985b79
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62771517"
---
# <a name="advanced-connection-properties"></a>Advanced Connection Properties
  Utilizzare la finestra di dialogo **Advanced Connection Properties** per aggiungere ulteriori parametri di connessione alla stringa di connessione.  
  
 Può trattarsi di qualsiasi parametro di connessione ODBC supportato dall'istanza del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in uso.  
  
 I parametri aggiunti utilizzando la finestra di dialogo **Advanced Connection Properties** vengono aggiunti ai parametri selezionati nella finestra di dialogo **Connect to SQL Server** .  
  
 L'ultima istanza di ogni parametro specificato sostituisce eventuali istanze precedenti del parametro stesso. I parametri aggiunti utilizzando la finestra di dialogo **Advanced Connection Parameters** seguono e sostituiscono i parametri specificati nella finestra di dialogo **SQL Server Connection** . Ad esempio, se nella finestra di dialogo **Connessione SQL Server** si specifica SERVER1 come nome del server e la pagina **Parametri aggiuntivi per la connessione** contiene ;SERVER=SERVER2, la connessione viene stabilita con SERVER2.  
  
 I parametri aggiunti utilizzando la finestra di dialogo **Advanced Connection Properties** vengono passati come testo normale.  
  
> [!IMPORTANT]  
>  Non includere le credenziali di accesso nella finestra di dialogo **Advanced Connection Properties** , non verranno crittografate quando vengono passate in rete.  
  
## <a name="see-also"></a>Vedere anche  
 [Accedere a CDC Designer Console](access-the-cdc-designer-console.md)   
 [Connessione di SQL Server per la creazione dell'istanza](sql-server-connection-for-instance-creation.md)  
  
  
