---
title: File di configurazione ReportingServicesService | Microsoft Docs
description: Informazioni sul percorso dei file, sulle linee guida per la modifica e sulle impostazioni di configurazione di ReportingServicesService.exe.config usate per la funzionalità di traccia in Reporting Services.
ms.date: 05/30/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- traces [Reporting Services]
- Report Server Windows service, ReportingServicesService configuration file
- ReportingServicesService configuration file
ms.assetid: 40f4a401-cb61-4c42-b1ec-01acdacdacd1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bb3b4d6c7591385f332daab9102613f05f0e5dfc
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84535353"
---
# <a name="reportingservicesservice-configuration-file"></a>ReportingServicesService - file di configurazione

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)]
  
Il file ReportingServicesService.exe.config contiene impostazioni di configurazione della funzionalità di traccia.  
  
## <a name="file-location"></a>Percorso del file  
Questo file può trovarsi in uno dei percorsi seguenti:  

``` Paths  
\Reporting Services\Report Server\Bin  
\Program Files\Microsoft SQL Server Reporting Services\SSRS\ReportServer\bin  
```  
 
## <a name="editing-guidelines"></a>Linee guida per la modifica  
 È possibile modificare questo file per rinominare il file di log oppure per aumentare o ridurre i livelli di traccia. Non modificare altre impostazioni. Per le istruzioni, vedere [Modificare un file di configurazione di Reporting Services &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md). Per altre informazioni sui log di traccia, vedere [Log di traccia del servizio del server di report](../../reporting-services/report-server/report-server-service-trace-log.md).  
  
## <a name="example-configuration"></a>Configurazione di esempio  
 Nell'esempio seguente vengono illustrati i valori predefiniti e le impostazioni contenuti nel file ReportingServicesService.exe.config.  
  
```  
<configSections>  
      <section name="RStrace" type="Microsoft.ReportingServices.Diagnostics.RSTraceSectionHandler,Microsoft.ReportingServices.Diagnostics" />  
</configSections>  
\<system.diagnostics>  
      <switches>  
          <add name="DefaultTraceSwitch" value="3" />  
      </switches>  
\</system.diagnostics>  
<RStrace>  
      <add name="FileName" value="ReportServerService_" />  
      <add name="FileSizeLimitMb" value="32" />  
      <add name="KeepFilesForDays" value="14" />  
      <add name="Prefix" value="tid, time" />  
      <add name="TraceListeners" value="debugwindow, file" />  
      <add name="TraceFileMode" value="unique" />  
      <add name="Components" value="all" />  
</RStrace>  
<runtime>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
             <dependentAssembly>  
                    <assemblyIdentity name="Microsoft.ReportingServices.Interfaces"  
                        publicKeyToken="89845dcd8080cc91"  
                        culture="neutral" />  
                    <bindingRedirect oldVersion="8.0.242.0"  
                                     newVersion="10.0.0.0"/>  
                    <bindingRedirect oldVersion="9.0.242.0"  
                                     newVersion="10.0.0.0"/>  
             </dependentAssembly>  
      </assemblyBinding>  
      <gcServer enabled="true" />  
</runtime>  
```  
  
## <a name="configuration-settings"></a>Impostazioni di configurazione  
 Nella tabella seguente sono incluse informazioni su impostazioni specifiche. Le impostazioni sono elencate nell'ordine in cui vengono visualizzate nel file di configurazione.  
  
|Impostazione|Descrizione|  
|-------------|-----------------|  
|**RStrace**|Specifica gli spazi dei nomi utilizzati per errori e traccia.|  
|**DefaultTraceSwitch**|Specifica il livello delle informazioni da includere nel log di traccia ReportServerService. Ogni livello include anche le informazioni raccolte da tutti i livelli inferiori. Non è consigliabile disabilitare la funzionalità di traccia. I valori validi includono:<br /><br /> 0= Disabilita la funzionalità di traccia<br /><br /> 1= Eccezioni e riavvii<br /><br /> 2= Eccezioni, riavvii, avvisi<br /><br /> 3= Eccezioni, riavvii, avvisi, messaggi di stato (valore predefinito)<br /><br /> 4= Modalità dettagliata|  
|**FileName**|Specifica la prima parte del nome file di log. Il resto del nome viene completato con il valore specificato da **Prefix** . Per impostazione predefinita, il nome è ReportServerService_.|  
|**FileSizeLimitMb**|Specifica il limite massimo per le dimensioni del log di traccia. Il file è misurato in megabyte. I valori validi sono compresi tra 0 e il valore integer massimo. Il valore predefinito è (32).|  
|**KeepFilesForDays**|Specifica dopo quanti giorni un file di log di traccia viene eliminato. I valori validi sono compresi tra 0 e il valore integer massimo. Il valore predefinito è 14.|  
|**Prefix**|Specifica un valore generato che distingue ogni istanza del log dalle altre. Per impostazione predefinita, ai nomi file dei log di traccia vengono aggiunti valori timestamp. Questo valore è impostato su "tid, time". Non modificare questa impostazione.|  
|**TraceListeners**|Specifica una destinazione per l'output del contenuto del log di traccia. È possibile specificare più destinazioni, separandole con una virgola. I valori validi includono:<br /><br /> DebugWindow (valore predefinito)<br /><br /> File (valore predefinito)<br /><br /> StdOut|  
|**TraceFileMode**|Specifica se i log di traccia devono contenere dati per un periodo di 24 ore. È consigliabile utilizzare un solo log di traccia al giorno per ogni componente. Questo valore è impostato su "Unique" (valore predefinito). Non modificare questo valore.|  
|**Componenti**|Specifica per quali componenti devono essere creati log di traccia. Il valore predefinito è **all**. Anche i nomi dei componenti interni sono valori validi per questa impostazione. Non modificare questo valore.|  
|**Runtime**|Specifica le impostazioni di configurazione che supportano la compatibilità con la versione precedente. Le impostazioni di run-time vengono utilizzate per reindirizzare le richieste relative alla versione precedente di Microsoft.ReportingServices.Interfaces alla nuova versione.<br /><br /> Tutte le impostazioni di configurazione di questa sezione vengono descritte nella documentazione di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . Per ulteriori informazioni, ricercare la voce "Runtime Schema Settings" nel sito Web MSDN o nella documentazione di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .|  
  
## <a name="see-also"></a>Vedere anche  
[File di configurazione di Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)  
[Log di traccia del servizio del server di report](../../reporting-services/report-server/report-server-service-trace-log.md)  
  
