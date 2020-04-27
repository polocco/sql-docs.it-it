---
title: Utilizzo di WQL e di linguaggi di scripting con il provider WMI per la gestione della configurazione | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- scripts [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
- WMI Provider for Configuration Management, scripts
ms.assetid: c1e64905-3c2b-4974-88f4-abf17cf7e289
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cc9994d4429e82f2bdd4f40797df1c5f628c6500
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "68195828"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider-for-configuration-management"></a>Utilizzo di WQL e di linguaggi di scripting con il provider WMI per la gestione della configurazione
  Le applicazioni di gestione accedono a servizi e impostazioni di rete di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando il provider di Strumentazione gestione Windows (WMI, Windows Management Instrumentation) per gli oggetti di gestione della configurazione in due modi diversi:  
  
-   Utilizzando un editor WQL o un strumento di query, ad esempio WBEMTest.exe, per eseguire una query sul set di oggetti con WQL.  
  
-   Utilizzando un linguaggio di scripting, ad esempio VBScript.  
  
 In alternativa, i servizi e le impostazioni di rete di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono essere gestiti a livello di programmazione utilizzando oggetti gestiti WMI in SMO. Per ulteriori informazioni sulla programmazione di oggetti gestiti WMI, vedere [gestione di servizi e impostazioni di rete tramite il provider WMI](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
 È possibile accedere al provider WMI per la gestione della configurazione utilizzando Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console. Per ulteriori informazioni sull'accesso al provider WMI da un'interfaccia utente, vedere procedure [per la gestione dei servizi &#40;Gestione configurazione SQL Server&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md).  
  
## <a name="see-also"></a>Vedi anche  
 [Accedere al provider WMI per la gestione della configurazione tramite WQL](access-wmi-provider-for-configuration-management-using-wql.md)   
 [Modificare le proprietà avanzate del servizio SQL Server usando VBScript](access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
