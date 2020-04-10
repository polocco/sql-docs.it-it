---
title: Metodo setTrustServerCertificate (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- setTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 6c37b518-147e-4cd9-9eff-b48a3f5888c6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a5c2ea95878abc101032eb662a601a65047c1e1
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80902014"
---
# <a name="settrustservercertificate-method-sqlserverdatasource"></a>Metodo setTrustServerCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta un valore **Boolean** che indica se la proprietà trustServerCertificate è abilitata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### <a name="parameters"></a>Parametri  
 *trustServerCertificate*  
  
 **true** se il certificato Secure Sockets Layer (SSL) del server deve essere considerato automaticamente attendibile quando il livello di comunicazione viene crittografato tramite SSL. In caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Se la proprietà trustServerCertificate è impostata su **true**, il certificato SSL di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene automaticamente considerato attendibile quando il livello di comunicazione è crittografato tramite SSL. In altri termini, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] non convalida il certificato SSL di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il valore predefinito è **false**.  
  
 Se la proprietà trustServerCertificate è impostata su **false**, il certificato SSL del server viene convalidato da [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
