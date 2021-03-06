---
description: Modificare il nome di un server registrato o di un gruppo di server registrati
title: Modificare il nome di un server registrato o di un gruppo di server
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 10e1546b-9edb-400c-8676-2ea1192d6134
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 08/02/2016
ms.openlocfilehash: c02287203533d75038a909bd962c9afc70858d2b
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037632"
---
# <a name="change-the-name-of-registered-server-or-registered-server-group"></a>Modificare il nome di un server registrato o di un gruppo di server registrati

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

In questo argomento viene descritto come modificare il nome di un server registrato o un gruppo di server registrati in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. È possibile modificare il nome in qualunque momento. La modifica del nome di un server nella finestra Server registrati consente solo di modificare il nome visualizzato. Per connettersi a un server diverso, è necessario modificare le proprietà di connessione del server registrato.  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Con SQL Server Management Studio

Dal menu passare a **Visualizza\\server registrati** per aprire il riquadro **Server registrati**.

### <a name="to-change-the-name-of-a-server"></a>Per modificare il nome di un server

1. In **Server registrati**espandere **Motore di database** , quindi **Gruppi di server locali**.  

2. Fare clic con il pulsante destro del mouse su un server e selezionare **Proprietà** per aprire la finestra di dialogo **Modifica proprietà registrazione server** .

3. Nella casella di testo **Nome server registrato** immettere il nuovo nome per la registrazione del server e quindi fare clic su **Salva**.  

### <a name="to-change-the-name-of-a-server-group"></a>Per modificare il nome di un gruppo di server  

1. In **Server registrati**espandere **Motore di database** , quindi **Gruppi di server locali**.  

2. Fare clic con il pulsante destro del mouse su un gruppo di server e selezionare **Proprietà** per aprire la finestra di dialogo **Modifica proprietà gruppo di server** . 

3. Nella casella di testo **Nome gruppo** immettere il nuovo nome per il gruppo di server e quindi fare clic su **Salva**.  

## <a name="see-also"></a>Vedere anche

[Modifica della registrazione di un server &#40;SQL Server Management Studio&#41;](./change-a-server-s-registration-sql-server-management-studio.md)