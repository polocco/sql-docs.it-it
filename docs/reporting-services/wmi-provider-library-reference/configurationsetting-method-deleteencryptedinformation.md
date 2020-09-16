---
description: Metodo DeleteEncryptedInformation (MSReportServer_ConfigurationSetting WMI)
title: Metodo DeleteEncryptedInformation (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DeleteEncryptedInformation method
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6dea15e9dfe817d13b7a1178406b45ab4d8321f4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497954"
---
# <a name="configurationsetting-method---deleteencryptedinformation"></a>Metodo di ConfigurationSetting - DeleteEncryptedInformation
  Elimina le informazioni crittografate dal database del server di report.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parametri  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
 *ExtendedErrors[]*  
 [out] Matrice di stringhe che contiene errori aggiuntivi restituiti dalla chiamata.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene richiamato questo metodo, i seguenti dati vengono eliminati:  
  
-   Informazioni sulle origini dati crittografate, tra cui nome utente e password.  
  
-   Dati della sottoscrizione crittografati tramite le interfacce dell'estensione per il recapito.  
  
-   Tutte le informazioni della tabella delle chiavi nel database del server di report.  
  
 Una volta richiamato questo metodo, l'utente deve inizializzare ogni computer che utilizza il database del server di report.  
  
 La chiamata al metodo DeleteEncryptedInformation non influisce sul file di configurazione del server di report.  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
