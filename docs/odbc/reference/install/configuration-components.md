---
description: Componenti di configurazione
title: Componenti di configurazione | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], configuring
ms.assetid: 0b68ff48-12e4-41aa-b9e2-b39ed5023ea7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a8a4b0f0b0a7a99409b5bb9caea53f23b62457e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487434"
---
# <a name="configuration-components"></a>Componenti di configurazione
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. È consigliabile installare solo in modo esplicito ODBC nelle versioni precedenti di Windows.  
  
 Le origini dati vengono configurate tramite la DLL del programma di installazione, che a sua volta chiama le DLL di installazione del driver e le DLL di installazione del convertitore. La DLL del programma di installazione viene richiamata direttamente dal pannello di controllo o caricata e chiamata da un altro programma, noto come *programma di amministrazione*. Nella figura seguente viene illustrata la relazione tra i componenti di configurazione di.  
  
 ![Relazione tra componenti di configurazione](../../../odbc/reference/install/media/pr30.gif "pr30")  
  
 Per ulteriori informazioni su questi componenti, vedere gli argomenti seguenti alla fine di questa sezione.  
  
-   [Programma di installazione](../../../odbc/reference/install/setup-program.md)  
  
-   [DLL di installazione](../../../odbc/reference/install/installer-dll.md)  
  
-   [DLL di installazione driver](../../../odbc/reference/install/driver-setup-dll.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti di installazione](../../../odbc/reference/install/installation-components.md)
