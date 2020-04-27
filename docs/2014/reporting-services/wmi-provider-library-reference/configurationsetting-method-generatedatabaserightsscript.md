---
title: Metodo GenerateDatabaseRightsScript (MSReportServer_ConfigurationSetting WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseRightsScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseRightsScript method
ms.assetid: f2e6dcc9-978f-4c2c-bafe-36c330247fd0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 575eab878e0ef9b4357c09a0a3deedf143c237b9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098478"
---
# <a name="generatedatabaserightsscript-method-wmi-msreportserver_configurationsetting"></a>Metodo GenerateDatabaseRightsScript (MSReportServer_ConfigurationSetting WMI)
  Genera uno script SQL che può essere utilizzato per concedere a un utente i diritti per il database del server di report e per gli altri database richiesti affinché un server di report venga eseguito. Il chiamante deve connettersi al server di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ed eseguire lo script.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
Public Sub GenerateDatabaseRightsScript(ByVal UserName As String, _  
    ByVal DatabaseName As String, ByVal IsRemote As Boolean, _  
    ByVal IsWindowsUser As Boolean, ByRef Script As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GenerateDatabaseRightsScript(string UserName, string DatabaseName, bool IsRemote, bool IsWindowsUser, out string Script,   
out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parametri  
 *UserName*  
 Nome utente o ID di sicurezza (SID) di Windows dell'utente al quale lo script concederà i diritti.  
  
 *DatabaseName*  
 Nome del database al quale lo script concederà l'accesso all'utente.  
  
 *IsRemote*  
 Valore booleano a che indica se il database è remoto per il server di report.  
  
 *IsWindowsUser*  
 Valore booleano che indica se il nome utente specificato è un utente di Windows o un utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 *Script*  
 [out] Stringa che contiene lo script [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generato.  
  
 *HRESULT*  
 [out] Valore che indica se la chiamata ha avuto esito positivo o negativo.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Un valore pari a 0 indica l'esito positivo della chiamata al metodo. Un valore diverso da zero indica che si è verificato un errore.  
  
## <a name="remarks"></a>Osservazioni  
 Se *DatabaseName* è vuoto, *IsRemote* viene ignorato e per il nome del database viene usato il valore del file di configurazione del server di report.  
  
 Se *IsWindowsUser* è impostato su `true`, il *nome utente* deve essere nel \<formato dominio \\><\>nome utente.  
  
 Quando *IsWindowsUser* è impostato su `true`, lo script generato concede all'utente i diritti di accesso per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], impostando il database del server di report come database predefinito, e concede il ruolo **RSExec nel** nel database del server di report, nel database temporaneo del server di report, nel database master e nel database di sistema msdb.  
  
 Quando *IsWindowsUser* è impostato su `true`, il metodo accetta come input i SID standard di Windows. Quando viene fornito un SID standard di Windows o un nome dell'account di servizio, questo viene convertito in una stringa del nome utente. Se il database è locale, l'account viene convertito nella rappresentazione localizzata corretta dell'account. Se il database è remoto, l'account viene rappresentato come account del computer.  
  
 Nella tabella seguente vengono mostrati gli account convertiti e la relativa rappresentazione remota.  
  
|Account / SID convertito|Nome comune|Nome remoto|  
|---------------------------------------|-----------------|-----------------|  
|(S-1-5-18)|Sistema locale|\<Dominio>\\<NomeComputer\>$|  
|.\LocalSystem|Sistema locale|\<Dominio>\\<NomeComputer\>$|  
|ComputerName\LocalSystem|Sistema locale|\<Dominio>\\<NomeComputer\>$|  
|LocalSystem|Sistema locale|\<Dominio>\\<NomeComputer\>$|  
|(S-1-5-20)|Servizio di rete|\<Dominio>\\<NomeComputer\>$|  
|NT AUTHORITY\NetworkService|Servizio di rete|\<Dominio>\\<NomeComputer\>$|  
|(S-1-5-19)|Servizio locale|Errore, vedere di seguito.|  
|NT AUTHORITY\LocalService|Servizio locale|Errore, vedere di seguito.|  
  
 In [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)], se si utilizza un account predefinito e il database del server di report è remoto, viene restituito un errore.  
  
 Se l'account `LocalService` predefinito è specificato e il database del server di report è remoto, viene restituito un errore.  
  
 Quando *IsWindowsUser* è True e il valore fornito in *UserName* deve essere convertito, il provider WMI determina se il database del server di report si trova sullo stesso computer o su un computer remoto. Per determinare se l'installazione è locale, il provider WMI valuta la proprietà DatabaseServerName rispetto al seguente elenco di valori. Se viene rilevata una corrispondenza, il database è locale. In caso contrario, è remoto. Il confronto non fa distinzione tra maiuscole e minuscole.  
  
|Valore di DatabaseServerName|Esempio|  
|---------------------------------|-------------|  
|"."||  
|"(local)"||  
|"LOCAL"||  
|localhost||  
|\<Nomecomputer>|testlab14|  
|\<FQDNcomputer>|example.redmond.microsoft.com|  
|\<IndirizzoIP>|180.012.345,678|  
  
 Quando *IsWindowsUser* è impostato su `true`, il provider WMI chiama LOOKUPACCOUNTNAME per ottenere il SID per l'account e quindi chiama LookupAccountSid per ottenere il nome da inserire nello [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] script. In questo modo si garantisce che il nome account utilizzato passerà la convalida [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Quando *IsWindowsUser* è impostato su `false`, lo script generato concede il ruolo **RSExec nel** nel database del server di report, nel database temporaneo del server di report e nel database msdb.  
  
 Quando *IsWindowsUser* è impostato su `false`, l'utente SQL Server deve esistere già nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire correttamente lo script.  
  
 Se il server di report non dispone di un database del server di report specificato, la chiamata a GrantRightsToDatabaseUser restituisce un errore.  
  
 Lo script generato supporta [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 e [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Requisiti  
 **Spazio dei nomi:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
