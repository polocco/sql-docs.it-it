---
title: Tipo di connessione Hyperion Essbase (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 108a00b6-799f-4066-b796-da59e95c09fd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8a0c38487f58a6db6e80d48c2b39b09e3ed93106
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66107266"
---
# <a name="hyperion-essbase-connection-type-ssrs"></a>Tipo di connessione Hyperion Essbase (SSRS)
  Per includere dati da un'origine dati esterna [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] nel report, è necessario disporre di un set di dati basato su un'origine dati del report di tipo [!INCLUDE[extEssbase](../../includes/extessbase-md.md)]. Questo tipo di origine dati predefinito è basato sull'estensione per i dati di [!INCLUDE[extEssbase](../../includes/extessbase-md.md)]che consente di recuperare dati multidimensionali da un'origine dati esterna [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .  
  
 Usare le informazioni presenti in questo argomento per compilare un'origine dati. Per istruzioni dettagliate, vedere [aggiungere e verificare una connessione dati o un'origine dati &#40;Generatore report e SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="connection-string"></a><a name="Connection"></a> Stringa di connessione  
 Nella stringa di connessione di esempio seguente viene specificata un'origine dati [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] in un server che utilizza la porta 13080 e XMLA (XML for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ) in Internet tramite SOAP, connettendosi a un catalogo di esempio:  
  
```  
Data Source=http://localhost:13080/aps/XMLA; Initial Catalog=Sample  
```  
  
 Per altre informazioni ed esempi di stringhe di connessione, vedere [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
  
##  <a name="credentials"></a><a name="Credentials"></a> Credenziali  
 Le credenziali sono necessarie per eseguire query, nonché per visualizzare l'anteprima del report in locale e dal server di report.  
  
 Dopo aver pubblicato il report, potrebbe essere necessario modificare le credenziali per l'origine dati affinché quando il report viene eseguito nel server di report, le autorizzazioni per il recupero dei dati risultino valide.  
  
 Per ulteriori informazioni, vedere [connessioni dati, origini dati e stringhe di connessione in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) o [specificare le credenziali in Generatore report](../specify-credentials-in-report-builder.md).  
  
  
##  <a name="queries"></a><a name="Query"></a> Query  
 È possibile specificare una query nei modi seguenti:  
  
-   Compilare una query in modo interattivo. Utilizzare la finestra Progettazione query con interfaccia grafica in modalità progettazione o query per cercare i metadati nell'origine dati esterna e generare una query nella sintassi MDX (Multidimensional Expression).  
  
    -   **Visualizzazione Progettazione** Trascinare dimensioni, membri, proprietà dei membri, misure e indicatori di prestazioni chiave (KPI) dal riquadro Visualizzatore metadati nel riquadro **Dati** per compilare una query MDX. Trascinare i membri calcolati dal riquadro Membri calcolati al riquadro Dati per definire altri campi del set di dati.  
  
    -   **Visualizzazione Query** Trascinare dimensioni, membri, proprietà dei membri, misure e indicatori di prestazioni chiave (KPI) dal riquadro Visualizzatore metadati al riquadro Query per compilare una query MDX. È possibile modificare il testo MDX direttamente nel riquadro Query. Trascinare i membri calcolati dal riquadro Membri calcolati al riquadro Query per definire altri campi del set di dati.  
  
     Per altre informazioni, vedere [Interfaccia utente di Progettazione query Hyperion Essbase &#40;Generatore report&#41;](../hyperion-essbase-query-designer-user-interface-report-builder.md).  
  
-   Importare una query MDX esistente da un report. Usare il pulsante di query **Importa** per cercare un file con estensione rdl e importare una query. È possibile importare una query da un report che contiene un set di dati incorporato basato sull'origine dati [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] . L'importazione di una query MDX direttamente da un file con estensione mdx non è supportata.  
  
 In fase di progettazione eseguire la query per visualizzare un set di risultati. Dopo aver compilato la query, visualizzare la raccolta dei campi del set di dati generata dai metadati nel riquadro dei dati del report. Quando viene eseguito il report, vengono restituiti i dati effettivi dall'origine dati esterna.  
  
 L'estensione per l'elaborazione dati di [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] supporta proprietà estese dei campi del set di dati. Si tratta di valori che sono disponibili nell'origine dati esterna e non nel riquadro dei dati del report. Per altre informazioni, vedere [Proprietà di campo estese](#Extended) più avanti in questo argomento.  
  
  
##  <a name="parameters"></a><a name="Parameters"></a> Parametri  
 Per includere parametri di query, creare un filtro nell'area del filtro in Progettazione query e contrassegnarlo come parametro. Viene creato automaticamente un set di dati per fornire i valori disponibili di ogni filtro. Per impostazione predefinita, tali set di dati non vengono visualizzati nel riquadro dei dati del report. Per altre informazioni, vedere [Visualizzazione di set di dati nascosti per i valori dei parametri di dati multidimensionali &#40;Generatore report e SSRS&#41;](show-hidden-datasets-for-parameter-values-multidimensional-data.md).  
  
 Per impostazione predefinita, i dati di ogni parametro di report sono di tipo **Text**. Dopo aver creato i parametri di report, potrebbe essere necessario modificare i valori predefiniti. Per ulteriori informazioni, vedere la pagina relativa al [Parametri report &#40;Generatore report e Progettazione report&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
  
##  <a name="extended-field-properties"></a><a name="Extended"></a> Proprietà di campo estese  
 L'estensione per l'elaborazione dati di [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] supporta proprietà di campo estese. Le proprietà di campo estese sono proprietà aggiuntive rispetto a `Value` e `IsMissing` definite per un campo del set di dati dall'estensione per l'elaborazione dei dati. Le proprietà estese includono proprietà predefinite e proprietà personalizzate. Le proprietà predefinite sono comuni a più origini dei dati, mentre quelle personalizzate sono specifiche di ogni origine dei dati.  
  
 Le proprietà di campo estese non vengono visualizzate nel riquadro Dati report come elementi che è possibile trascinare nel layout del report. È invece possibile trascinare nel report il campo padre della proprietà e quindi modificare la proprietà predefinita da `Value` alla proprietà desiderata.  
  
 Il nome di una proprietà di campo estesa viene visualizzato nella descrizione comandi quando il puntatore del mouse passa su un campo nel riquadro dei metadati di Progettazione query. Per altre informazioni sulle finestre Progettazione query che è possibile usare per esplorare i dati sottostanti, vedere [Interfaccia utente di Progettazione query Hyperion Essbase](hyperion-essbase-query-designer-user-interface.md).  
  
> [!NOTE]  
>  I valori per le proprietà di campo estese sono disponibili solo se vengono inclusi nell'espressione MDX e vengono forniti dall'origine dati quando il report viene eseguito e vengono recuperati i dati per i relativi set di dati. È quindi possibile fare riferimento a tali valori delle proprietà `Field` in qualsiasi espressione utilizzando la sintassi descritta nella sezione seguente. Poiché, tuttavia, questi campi sono specifici del provider di dati in uso e non fanno parte del linguaggio RDL, eventuali modifiche apportate a tali valori non vengono salvate con la definizione del report.  
  
  
### <a name="predefined-field-properties"></a>Proprietà di campo predefinite  
 Proprietà di campo generalmente supportate da più provider di dati e incluse nella query MDX sottostante relativa a un set di dati di report. La proprietà delle dimensioni MDX MEMBER_UNIQUE_NAME è ad esempio mappata alla proprietà di campo predefinita del set di dati del report `UniqueName`. Per includere il valore del nome univoco in una casella di testo, usare l'espressione `=Fields!` *\<FieldName>* `.UniqueName`.  
  
 Nella tabella seguente viene riportato un elenco delle proprietà di campo predefinite che è possibile utilizzare per un'origine dati [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .  
  
|**Proprietà**|**Tipo**|**Descrizione o valore previsto**|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|Specifica il valore dei dati del campo.<br /><br /> Per una proprietà delle dimensioni, viene eseguito il mapping a MEMBER_CAPTION. Per una misura, viene eseguito il mapping a un valore dei dati.|  
|`IsMissing`|`Boolean`|Indica se il campo è stato trovato nel set di dati risultante.|  
|`FormattedValue`|`String`|Restituisce un valore formattato per una cifra chiave.<br /><br /> Mapping eseguito da FORMATTED_VALUE nell'espressione MDX.|  
|`BackgroundColor`|`String`|Restituisce il colore di sfondo definito nel database per il campo.<br /><br /> Mapping eseguito da BACK_COLOR nell'espressione MDX.|  
|`Color`|`String`|Restituisce il colore di primo piano definito nel database per l'elemento.<br /><br /> Mapping eseguito da FORE_COLOR nell'espressione MDX.|  
|`UniqueName`|`String`|Restituisce il nome completo di un livello.<br /><br /> Mapping eseguito da MEMBER_UNIQUE_NAME nell'espressione MDX.|  
  
 Per altre informazioni sull'uso di campi e proprietà di campo in un'espressione, vedere [Raccolte predefinite nelle espressioni &#40;Generatore report e SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
  
### <a name="custom-properties"></a>Proprietà personalizzate  
 Proprietà di campo personalizzate supportate da un provider di dati e incluse nella query MDX sottostante relativa al set di dati di un report, ma non nel riquadro Set di dati del report come campi nel set di dati. **Long Names** è ad esempio una proprietà del membro definita per un livello di dimensione. Per includere il valore in una casella di testo, usare l'espressione `=Fields!` * \<FieldName>* `("Long Names")`. Per i nomi dei campi nell'espressione viene fatta distinzione tra maiuscole e minuscole.  
  
 Per fare riferimento alle proprietà estese personalizzate in un'espressione, utilizzare la sintassi seguente:  
  
-   *Campi! FieldName ("PropertyName")*  
  
 Nella tabella seguente viene illustrata la proprietà di campo che è possibile utilizzare per un'origine dati [!INCLUDE[extEssbase](../../includes/extessbase-md.md)] .  
  
|**Proprietà**|**Type**|**Descrizione o valore previsto**|  
|------------------|--------------|---------------------------------------|  
|`FORMAT_STRING`|`String`|Definita in una misura. Si tratta del valore `FormattedValue` disponibile come tipo stringa.|  
  
  
##  <a name="remarks"></a>Osservazioni su <a name="Remarks"></a>  
 Non tutte le modalità di recapito report sono supportate da questo provider di dati. Il recapito di report tramite sottoscrizioni guidate dai dati non è supportato per questa estensione per l'elaborazione dati. Per altre informazioni, vedere [Usare un'origine dati esterna per i dati del Sottoscrittore &#40;sottoscrizione guidata dai dati&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md) nella documentazione relativa a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclusa nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Documentazione online](https://go.microsoft.com/fwlink/?linkid=121312) di .  
  
 Per altre informazioni, vedere [Using SQL Server 2005 Reporting Services with Hyperion Essbase](https://go.microsoft.com/fwlink/?LinkId=81970)(Uso di SQL Server 2005 Reporting Services con Hyperion Essbase).  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a>Procedure  
 Questa sezione contiene istruzioni dettagliate per l'utilizzo di connessioni dati, origini dati e set di dati:  
  
 [Aggiungere e verificare una connessione dati o un'origine dati &#40;Generatore report e SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [Creare un set di dati condiviso o un set di dati incorporato &#40;Generatore report e SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [Aggiungere un filtro a un set di dati &#40;Generatore report e SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="related-sections"></a><a name="Related"></a>Sezioni correlate  
 In queste sezioni della documentazione sono incluse informazioni concettuali approfondite sui dati dei report, nonché le informazioni necessarie sulle procedure per definire, personalizzare e usare parti di un report correlate ai dati.  
  
 [Aggiungere dati a un report &#40;Generatore report e SSRS&#41;](report-datasets-ssrs.md)  
 Viene fornita una panoramica sull'accesso ai dati del report.  
  
 [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 Vengono fornite informazioni sulle connessioni dati e sulle origini dati.  
  
 [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 Vengono fornite informazioni sui set di dati incorporati e condivisi.  
  
 [Raccolta di campi del set di dati &#40;Generatore report e SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)  
 Vengono fornite informazioni sulla raccolta di campi generata dalla query del set di dati.  
  
 [Origini dati supportate da Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) nella documentazione relativa a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclusa nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [documentazione online](https://go.microsoft.com/fwlink/?linkid=121312) di .  
 Vengono fornite informazioni dettagliate sul supporto delle piattaforme e delle versioni per ogni estensione per i dati.  
  
 [Using SQL Server 2005 Reporting Services with Hyperion Essbase](https://go.microsoft.com/fwlink/?LinkId=81970)  
 Vengono fornite informazioni dettagliate sull'utilizzo di questa estensione per i dati.  
  
  
## <a name="see-also"></a>Vedi anche  
 [Parametri del report &#40;Generatore report e Progettazione report&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtrare, raggruppare e ordinare i dati &#40;Generatore report e SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Espressioni &#40;Generatore report e SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
