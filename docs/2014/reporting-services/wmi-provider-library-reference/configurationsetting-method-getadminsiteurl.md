---
title: Metodo GetAdminSiteUrl (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetAdminSiteUrl method
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9012a5cbc130ac79963e033c8c3d93807d946445
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098440"
---
# <a name="getadminsiteurl-method-wmi"></a>Metodo GetAdminSiteUrl (WMI)
  Ottiene l'URL assoluto per il sito Web di Amministrazione centrale per la farm di Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]o [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] con la quale il server di report è integrato.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub GetAdminSiteUrl(ByRef AdminSiteUrl as String, _  
ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GetAdminSiteUrl(out string AdminSiteUrl, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *AdminSiteUrl*  
 [out] Stringa che contiene l'URL assoluto per il sito Web di Amministrazione centrale per la farm di SharePoint con la quale il server di report è integrato.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-methods.md)  
  
  
