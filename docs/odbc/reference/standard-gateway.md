---
title: Gateway standard | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 67551845c0dd8c6a28c0c4bc1c50f54ee8232df1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280074"
---
# <a name="standard-gateway"></a>Gateway standard
Un *gateway* è un componente software che fa sì che un DBMS sia simile a un altro. Questo significa che il gateway accetta l'interfaccia di programmazione, la grammatica SQL e il protocollo del flusso di dati di un singolo DBMS e lo converte nell'interfaccia di programmazione, nella grammatica SQL e nel protocollo di flusso dei dati del sistema DBMS nascosto. Ad esempio, le applicazioni scritte per usare Microsoft® SQL Server™ possono anche accedere ai dati DB2 tramite il gateway DecisionWare DB2 micro. Questo prodotto causa l'aspetto di DB2 come SQL Server. Quando si usano i gateway, è necessario scrivere un altro gateway per ogni database di destinazione.  
  
 Sebbene i gateway siano limitati dalle differenze di architettura tra DBMS, sono un buon candidato per la standardizzazione. Tuttavia, se tutti i sistemi DBMS devono standardizzare l'interfaccia di programmazione, la grammatica SQL e il protocollo del flusso di dati di un singolo DBMS, il cui DBMS deve essere scelto come standard? Certamente nessun fornitore del sistema DBMS commerciale è probabile che accetti di standardizzare il prodotto di un concorrente. Se vengono sviluppate un'interfaccia di programmazione standard, una grammatica SQL e un protocollo del flusso di dati, non è necessario alcun gateway.
