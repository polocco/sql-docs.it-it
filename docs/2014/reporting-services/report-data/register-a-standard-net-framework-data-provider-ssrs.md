---
title: Registrare un provider di dati .NET Framework standard (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], data
- .NET Framework data providers for Reporting Services
- data processing extensions [Reporting Services]
- data providers [Reporting Services]
- data retrieval [Reporting Services]
- Reporting Services, data sources
ms.assetid: d92add64-e93c-4598-8508-55d1bc46acf6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 208b1363de6b1c6892ba8f265365b1d304b6ceab
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66107145"
---
# <a name="register-a-standard-net-framework-data-provider-ssrs"></a>Registrare un provider di dati .NET Framework standard (SSRS)
  Per usare un provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] di terze parti per recuperare dati per un set di dati di un report [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , è necessario distribuire e registrare l'assembly del provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] in due posizioni, ovvero nel client di creazione dei report e nel server di report. Nel client per la creazione del report, è necessario registrare il provider di dati come tipo di origine dei dati e associarlo a una finestra Progettazione query. Sarà quindi possibile selezionare il provider di dati come tipo di origine dei dati per la creazione di un set di dati di report. La finestra Progettazione query associata verrà aperta per consentire la creazione di query per il tipo di origine dei dati specifico. Nel server di report il provider di dati deve essere registrato come tipo di origine dei dati. Sarà quindi possibile elaborare i report pubblicati che recuperano i dati da un'origine mediante il provider di dati.  
  
 I provider di dati di terze parti possono non offrire tutte le funzionalità disponibili nelle estensioni per l'elaborazione dati di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Per altre informazioni, vedere [Origini dati supportate da Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md). Per informazioni sull'estensione della funzionalità di un[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provider di dati , vedere [Implementazione di un'estensione per l'elaborazione dati](../extensions/data-processing/implementing-a-data-processing-extension.md).  
  
 Per installare e registrare i provider di dati è necessario disporre di credenziali di amministratore.  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-server"></a>Registrazione di un provider di dati .NET Framework nel server di report  
 Per elaborare i report pubblicati che utilizzano il provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] nel server di report, è necessario installare l'assembly in quest'ultimo. È necessario modificare due file di configurazione. Per registrare il provider di dati, modificare rsreportserver.config. Per assegnare autorizzazioni di sicurezza dell'accesso al codice per l'assembly, modificare rssrvpolicy.config.  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-server"></a>Per installare l'assembly di un provider di dati nel server di report  
  
1.  Accedere al percorso predefinito della directory bin nel server di report in cui si vuole usare il provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . Il percorso predefinito della directory bin del server di report è *\<unità>* :\Programmi\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin.  
  
2.  Copiare l'assembly dal percorso di gestione temporanea nella directory bin del server di report. In alternativa, è possibile caricare l'assembly nella Global Assembly Cache (GAC). Per altre informazioni, vedere [Utilizzo di assembly e della Global Assembly Cache](https://go.microsoft.com/fwlink/?linkid=63912) nella documentazione di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK in MSDN.  
  
#### <a name="to-register-a-net-data-provider-on-the-report-server"></a>Per registrare un provider di dati .NET nel server di report  
  
1.  Eseguire una copia di backup del file RSReportServer.config nella directory padre di ReportServer per bin.  
  
2.  Aprire RSReportServer.config. È possibile aprire il file di configurazione con [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] o con un semplice editor di testo, ad esempio il Blocco note.  
  
3.  Individuare l'elemento `Data` nel file RSReportServer.config. Una voce relativa al provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] dovrà essere inserita nella posizione seguente:  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  Aggiungere una voce per il provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
    |Attributo|Descrizione|  
    |---------------|-----------------|  
    |`Name`|Specificare un nome univoco per il provider di dati, ad esempio **ProviderDatiNET**. La lunghezza massima consentita per l'attributo `Name` è di 255 caratteri. Il nome deve essere univoco all'interno di tutte le voci dell'elemento `Extension` di un file di configurazione. Il valore indicato qui viene inserito nell'elenco a discesa dei tipi di origini dei dati per la creazione di una nuova origine.|  
    |`Type`|Immettere un elenco delimitato da virgole che includa lo spazio dei nomi completo della classe che implementa l'interfaccia <xref:System.Data.IDbConnection> , seguito dal nome dell'assembly del provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , senza l'estensione dll.|  
  
     La voce relativa a una DLL distribuita nella directory bin del server di report potrebbe essere analoga alla seguente:  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     Se si carica l'assembly nella Global Assembly Cache (GAC), è necessario impostare le proprietà del nome sicuro. Ad esempio:  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly,Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider"></a>Per impostare criteri di gruppo di codice per un provider di dati .NET.  
  
1.  Eseguire una copia di backup del file rssrvpolicy.config nella directory padre di ReportServer per bin.  
  
2.  Aprire file rssrvpolicy. config. È possibile aprire il file di configurazione [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] con o con un semplice editor di testo, ad esempio Blocco note.  
  
3.  Individuare l'elemento `CodeGroup` nel file rssrvpolicy.config.  
  
4.  Aggiungere un gruppo di codice relativo all'assembly del provider di dati che assegni l'autorizzazione `FullTrust`. Il gruppo di codice potrà avere l'aspetto seguente:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 L'appartenenza URL è solo una delle diverse condizioni di appartenenza selezionabili per il provider di dati.  
  
### <a name="verifying-the-deployment-and-registration"></a>Verifica della distribuzione e della registrazione  
 È possibile verificare se la distribuzione del provider di dati nel server di report ha avuto esito positivo aprendo Gestione report e controllando che sia incluso nell'elenco delle origini dati disponibili. Per altre informazioni su Gestione report e sulle origini dati, vedere [Creare, modificare ed eliminare origini dati condivise &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).  
  
## <a name="registering-a-net-framework-data-provider-on-the-report-designer-client"></a>Registrazione di un provider di dati .NET Framework nel client di Progettazione report  
 Per creare report che utilizzino il provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] per un'origine dei dati, è necessario installare l'assembly nel computer client che esegue Progettazione report. È necessario modificare due file di configurazione. Modificare RSReportDesigner.config per registrare il provider di dati come origine dei dati e per utilizzare la finestra Progettazione query standard. Modificare RSPreviewPolicy.config per assegnare autorizzazioni di sicurezza dell'accesso al codice per l'assembly del provider di dati.  
  
#### <a name="to-install-a-data-provider-assembly-on-the-report-designer-client"></a>Per installare l'assembly di un provider di dati nel client di Progettazione report  
  
1.  Accedere al percorso predefinito della directory PrivateAssemblies nel client di Progettazione report in cui si vuole usare il provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . Il percorso predefinito della directory PrivateAssemblies è * \<unità>*: \Programmi\Microsoft Visual Studio 9.0 \ Common7\IDE\PrivateAssemblies.  
  
2.  Copiare l'assembly dal percorso di gestione temporanea nella directory PrivateAssemblies del client di Progettazione report. In alternativa, è possibile caricare l'assembly nella Global Assembly Cache (GAC). Per altre informazioni, vedere [Utilizzo di assembly e della Global Assembly Cache](https://go.microsoft.com/fwlink/?linkid=63912) nella documentazione di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK in MSDN.  
  
#### <a name="to-register-a-net-data-provider-on-the-report-designer-client"></a>Per registrare un provider di dati .NET nel client di Progettazione report  
  
1.  Eseguire una copia di backup del file RSReportDesigner.config nella directory PrivateAssemblies.  
  
2.  Aprire RSReportDesigner.config con [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] o con un semplice editor di testo, ad esempio Blocco note.  
  
3.  Individuare l'elemento `Data` nel file RSReportDesigner.config. Una voce relativa al provider di dati dovrà essere inserita nella posizione seguente:  
  
    ```  
    <Extensions>  
       <Data>  
          <Extension Your data provider configuration information goes here />  
       </Data>  
    </Extensions>  
    ```  
  
4.  Aggiungere una voce per il provider di dati.  
  
    |Attributo|Descrizione|  
    |---------------|-----------------|  
    |`Name`|Specificare un nome univoco per il provider di dati, ad esempio **ProviderDatiNET**. La lunghezza massima consentita per l'attributo `Name` è di 255 caratteri. Il nome deve essere univoco all'interno di tutte le voci dell'elemento `Extension` di un file di configurazione. Il valore indicato qui viene inserito nell'elenco a discesa dei tipi di origini dei dati per la creazione di una nuova origine.|  
    |`Type`|Immettere un elenco delimitato da virgole che includa lo spazio dei nomi completo della classe che implementa l'interfaccia <xref:System.Data.IDbConnection> , seguito dal nome dell'assembly del provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , senza l'estensione dll.|  
  
     Ad esempio, la voce per una DLL distribuita nella directory PrivateAssemblies di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] può essere simile alla seguente:  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly" />   
    ```  
  
     Se si carica l'assembly nella cache di assembly globale (CAG), è necessario impostare le proprietà del nome sicuro. Ad esempio:  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="CompanyName.ExtensionName.DataProviderConnectionClass, DataProviderAssembly, Version=1.0.0.0, Culture=neutral, PublicKeyToken=MyPublicToken"/>  
    ```  
  
5.  Individuare l'elemento `Designer` nel file RSReportDesigner.config. Una voce relativa al provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] dovrà essere inserita nella posizione seguente:  
  
    ```  
    <Extensions>  
       <Designer>  
          <Your data provider configuration information goes here>  
       </Designer>  
    </Extensions>  
    ```  
  
6.  Aggiungere la voce seguente al file RSReportDesigner.config nell'elemento `Designer`. È necessario sostituire solo l'attributo `Name` con il nome specificato nelle voci precedenti.  
  
    ```  
    <Extension Name="MyNETDataProvider" Type="Microsoft.ReportingServices.QueryDesigners.GenericQueryDesigner,Microsoft.ReportingServices.QueryDesigners"/>  
    ```  
  
#### <a name="to-set-the-code-group-policy-for-a-net-data-provider-on-the-report-designer-client"></a>Per impostare criteri di gruppo di codice per un provider di dati .NET nel client di Progettazione report  
  
1.  Eseguire una copia di backup del file RSPreviewPolicy.config file nella directory PrivateAssemblies.  
  
2.  Aprire RSPreviewPolicy.config con [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] o con un semplice editor di testo, ad esempio il Blocco note.  
  
3.  Individuare l'elemento `CodeGroup` nel file RSPreviewPolicy.config.  
  
4.  Aggiungere un gruppo di codice relativo all'assembly del provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] che assegni l'autorizzazione `FullTrust`. Il gruppo di codice potrà avere l'aspetto seguente:  
  
    ```  
    <CodeGroup class="UnionCodeGroup"  
       version="1"  
       PermissionSetName="FullTrust"  
       Name="ThisDataProviderCodeGroup"  
       Description="Code group for the .NET data provider">  
          <IMembershipCondition class="UrlMembershipCondition"  
             version="1"  
             Url=  
    " C:\Program Files\Microsoft Visual Studio 9\Common7\IDE\PrivateAssemblies\DataProviderAssembly.dll"  
           />  
    </CodeGroup>  
    ```  
  
 L'appartenenza URL è solo una delle diverse condizioni di appartenenza selezionabili per il provider di dati.  
  
### <a name="verifying-the-deployment-and-registration-on-the-report-designer-client"></a>Verifica della distribuzione e della registrazione nel client di Progettazione report  
 Per poter verificare la distribuzione, è necessario chiudere tutte le istanze di [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] nel computer locale. Dopo aver chiuso tutte le sessioni correnti, è possibile verificare se la distribuzione del provider di dati in Progettazione report è riuscita creando un nuovo progetto di report in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Quando si crea un nuovo set di dati per il report il provider di dati dovrebbe essere incluso nell'elenco dei tipi di origini dei dati disponibili.  
  
## <a name="platform-considerations"></a>Considerazioni relative alla piattaforma  
 In una piattaforma a 64 bit (x64) [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] viene eseguito in modalità WOW a 32 bit. Quando si creano report su una piattaforma x64, per visualizzarne l'anteprima è necessario che i provider di dati a 32 bit siano installati nel client per la creazione di report. Se si pubblica il report sul medesimo sistema, per poterlo visualizzare in Gestione report saranno necessari i provider di dati x64.  
  
 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] non è supportato per le piattaforme con processore [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)].  
  
 Le estensioni per l'elaborazione dati installate con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] devono essere compilate in modo nativo per ogni piattaforma e installate nei percorsi corretti. Se si registra un provider di dati personalizzato o un provider di dati [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] standard, sarà necessario compilarlo in modo nativo per la piattaforma appropriata e installarlo nei percorsi adeguati. Se si esegue una piattaforma a 32 bit, il provider di dati deve essere compilato per tale tipo di piattaforma. Se si esegue una piattaforma a 64 bit, il provider di dati deve essere invece compilato di conseguenza per tale tipo di piattaforma. Non è possibile utilizzare un provider di dati a 32 bit di cui è stato eseguito il wrapping con interfacce a 64 bit su una piattaforma a 64 bit. Per informazioni relative al funzionamento del provider di dati sulla piattaforma installata, vedere la documentazione del software di terze parti. Per altre informazioni sui provider di dati e sulle piattaforme supportate, vedere [Origini dati supportate da Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
## <a name="see-also"></a>Vedi anche  
 [Configurare e amministrare un server di report &#40;modalità nativa SSRS&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)   
 [Implementazione di un'estensione per l'elaborazione dati](../extensions/data-processing/implementing-a-data-processing-extension.md)   
 [File di configurazione di Reporting Services](../report-server/reporting-services-configuration-files.md)   
 [Sicurezza dall'accesso di codice in Reporting Services](../extensions/secure-development/code-access-security-in-reporting-services.md)  
  
  
