---
title: Proprietà state (classe SqlService) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- State Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cc1484a09929f4e4a8534b2c2acac2089adfbb97
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62912186"
---
# <a name="state-property-sqlservice-class"></a>Proprietà State (classe SqlService)
  Ottiene o imposta lo stato corrente del servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.State [= value]  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe SqlService](sqlservice-class.md) che rappresenta il servizio.  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore uint32 che specifica lo stato del servizio.  
  
 I valori possibili sono i seguenti:  
  
 1  
 Arrestato. Il servizio è stato arrestato.  
  
 2  
 In attesa dell'avvio. Il servizio è in attesa di essere avviato.  
  
 3  
 In attesa dell'arresto. Il servizio è in attesa di essere arrestato.  
  
 4  
 In esecuzione. Il servizio è in esecuzione.  
  
 5  
 In attesa della ripresa. Il servizio è in attesa di essere ripreso.  
  
 6  
 In attesa della sospensione. Il servizio è in attesa di essere sospeso.  
  
 7  
 (sospeso) Il servizio è stato sospeso.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedi anche  
 [Avvio e arresto di servizi](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
