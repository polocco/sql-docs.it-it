---
title: Elemento &lt;xsd:redefine&gt; | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e9fa3dedafc05406dcc521429130f98a215d294
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62679971"
---
# <a name="the-ltxsdredefinegt-element"></a>Elemento &lt;xsd:redefine&gt;
  L'elemento **redefine** dello schema XSD W3C rende disponibile il supporto per la ridefinizione dei componenti di schema. Tuttavia, il supporto per questa direttiva è potenzialmente costoso per le prestazioni e richiede anche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che vengano rivalide tutte le istanze `xml` del tipo di dati associate allo schema ridefinito. Di conseguenza, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta questo elemento. XML Schema che includono l'elemento **\<xsd:redefine>** verranno rifiutati dal server.  
  
 In alternativa, per aggiornare uno schema o i relativi componenti, è possibile eseguire le operazioni seguenti.  
  
1.  Creare una nuova raccolta XML Schema con i componenti di schema modificati.  
  
2.  Riscrivere tutti i tipi di dati `xml` (XML DT) che usano la raccolta XML Schema da ridefinire per usare in sostituzione la nuova raccolta XML Schema. A questo scopo, utilizzare l'opzione ALTER COLUMN del comando ALTER TABLE per riscrivere colonne o modificare i vincoli della raccolta XML Schema su variabili o parametri.  
  
3.  Eliminare la versione obsoleta della raccolta XML Schema.  
  
## <a name="see-also"></a>Vedere anche  
 [Requisiti e limitazioni per le raccolte di XML Schema nel server](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
