---
title: Proprietà NumberOfFlags (classe ClientNetworkProtocol) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- NumberOfFlags Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- NumberOfFlags property
ms.assetid: 7a656644-2154-419f-9787-99877f597770
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 9a47f6e17a85fdf9cec169a611b9fe205ba02543
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63192040"
---
# <a name="numberofflags-property-clientnetworkprotocol-class"></a>Proprietà NumberOfFlags (classe ClientNetworkProtocol)
  Ottiene il numero di opzioni del flag richieste dal protocollo di rete del client specificato dal [Metodo SetOrderValue (classe ClientNetworkProtocol)](clientnetworkprotocol-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object  
.NumberofFlags [= value]  
```  
  
## <a name="parts"></a>Parti  
 *oggetto*  
 Oggetto della [classe ClientNetworkProtocol](clientnetworkprotocol-class.md) che rappresenta il protocollo di rete utilizzato dal client di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Valore proprietà/Valore restituito  
 Valore `Uint32` che specifica il numero di opzioni del flag richieste dal protocollo di rete del client a cui fa riferimento la proprietà `OrderValue`.  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedi anche  
 [configurazione di protocolli client](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
