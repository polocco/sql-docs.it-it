---
title: Connettersi al database SQL di Azure (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connect to SQL Azure dialog box
ms.assetid: bf44b236-d9be-41ae-a5fd-bd73038e505f
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 0b26ddaef1373544e0df2fd9186cdf56fdafd801
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68040635"
---
# <a name="connect-to-azure-sql-db-accesstosql"></a>Connettersi al database SQL di Azure (AccessToSQL)
Utilizzare la finestra di dialogo Connetti a SQL Azure per connettersi al database di SQL Azure di cui si desidera eseguire la migrazione.  
  
Per accedere a questa finestra di dialogo, scegliere **Connetti a SQL Azure**dal menu **file** . Se è già stata effettuata la connessione, il comando viene **riconnesso a SQL Azure.**  
  
## <a name="options"></a>Opzioni  
**Nome del server**  
  
Selezionare o immettere il nome del server per la connessione a SQL Azure.  
  
**Database**  
  
Selezionare, immettere o **esplorare** il nome del database.  
  
> [!IMPORTANT]  
> SSMA per Access non supporta la connessione al database master in SQL Azure.  
  
**Nome utente**  
  
Immettere il nome utente che SSMA utilizzerà per connettersi al database di SQL Azure  
  
**Password**  
  
Immettere il nome utente e la password  
  
**Encrypt**  
  
SSMA consiglia la connessione crittografata a SQL Azure.  
  
## <a name="create-azure-database"></a>Creare un database di Azure  
Per creare un nuovo database di Azure, attenersi alla procedura seguente:  
  
1.  fare clic sul pulsante Sfoglia presente nella finestra di dialogo Connetti a SQL Azure  
  
2.  Se non sono presenti database, vengono visualizzate due voci di menu  
  
    1.  **(nessun database trovato)** disabilitato e disattivato per sempre  
  
    2.  **Creare un nuovo database** che è sempre abilitato, consentendo all'utente di creare un nuovo database di Azure nell'account SQL Azure. Quando si fa clic su questa voce di menu, la finestra di dialogo Crea database di Azure è disponibile con nome e dimensioni del database.  
  
3.  Al momento della creazione del database, questi due parametri vengono forniti come input.  
  
    1.  **Nome database:** Immettere il nome del database.  
  
    2.  **Dimensioni database:** Selezionare le dimensioni del database che è necessario creare in SQL Azure account.  
  
