---
title: Metodo SetExtendedProtectionSettings (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0583632b9c9b8548e16b7a74718b48cad8066ced
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098035"
---
# <a name="setextendedprotectionsettings-method-wmi-msreportserver_configurationsetting"></a>Metodo SetExtendedProtectionSettings (MSReportServer_ConfigurationSetting WMI)
  Il metodo SetExtendedProtectionSettings viene usato per impostare le proprietà RSWindowsExtendedProtectionLevel e RSWindowsExtendedProtectionScenario nel file di configurazione RSReportServer.config di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *ExtendedProtectionLevel*  
 Imposta RSWindowsExtendedProtectionLevel nel file RSRreportserver.config. Il valore obbligatorio non supporta la distinzione tra maiuscole e minuscole.  
  
 Nell'elenco seguente sono indicati i valori validi:  
  
 `"Off | Allow | Require"`  
  
 *ExtendedProtectionScenario*  
 Imposta RSWindowsExtendedProtectionScenario nel file RSReportserver.config. Il valore obbligatorio non supporta la distinzione tra maiuscole e minuscole.  
  
 Nell'elenco seguente sono indicati i valori validi:  
  
 `"Any" | "Proxy" | "Direct"`  
  
## <a name="remarks"></a>Osservazioni  
 Le proprietà RSWindowsExtendedProtectionLevel e RSWindowsExtendedProtectionScenario si applicano quando i tipi di autenticazione nel file RSReportServer.config includono RSWindowNTLM, RSWindowsNegotiate o RSWindowsKerberos. L'impostazione di queste proprietà ha effetto sulla modalità di autenticazione degli utenti e del software client nel server di report. Prima di impostare ExtendedProtectionLevel su `Allow` o su `Require` è consigliabile leggere la documentazione relativa alla protezione estesa.  
  
 Per impostare ExtendedProtectionLevel, è necessario che l'utente sia un membro del gruppo BUILTIN\Administrators nel server di report.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà RSWindowsExtendedProtectionScenario &#40;MSReportServer_ConfigurationSetting WMI&#41;](rswindowsextendedprotectionscenario-property.md)   
 [Proprietà RSWindowsExtendedProtectionLevel &#40;MSReportServer_ConfigurationSetting WMI&#41;](rswindowsextendedprotectionlevel-property.md)   
 [Protezione estesa per l'autenticazione con Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [File di configurazione RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  
