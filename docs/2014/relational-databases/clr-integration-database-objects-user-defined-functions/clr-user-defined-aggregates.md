---
title: Funzioni di aggregazione CLR definite dall'utente | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 59666e90a47d88762c6fc3bd1fabc0e71ea18f94
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62919585"
---
# <a name="clr-user-defined-aggregates"></a>Aggregazioni CLR definite dall'utente
  Le funzioni di aggregazione eseguono un calcolo su un set di valori e restituiscono un singolo valore. Tradizionalmente [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ha supportato solo funzioni di aggregazione predefinite, ad `SUM` esempio `MAX`o, che operano su un set di valori scalari di input e generano un singolo valore di aggregazione da tale set. L'integrazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con il CLR [!INCLUDE[msCoName](../../includes/msconame-md.md)] di .NET Framework consente ora agli sviluppatori di creare funzioni di aggregazione personalizzate in codice gestito e di rendere accessibili queste funzioni a [!INCLUDE[tsql](../../includes/tsql-md.md)] o all'altro codice gestito.  
  
 Nella tabella seguente vengono elencati gli argomenti disponibili in questa sezione.  
  
 [Requisiti per le aggregazioni CLR definite dall'utente](clr-user-defined-aggregates-requirements.md)  
 Viene fornita una panoramica dei requisiti per l'implementazione di funzioni di aggregazione CLR definite dall'utente.  
  
 [Chiamata di funzioni di aggregazione CLR definite dall'utente](clr-user-defined-aggregate-invoking-functions.md)  
 Viene illustrato come richiamare aggregazioni definite dall'utente.  
  
  
