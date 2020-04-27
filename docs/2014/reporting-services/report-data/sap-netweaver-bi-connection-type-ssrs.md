---
title: Tipo di connessione SAP NetWeaver BI (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f985856b-31d5-4e56-844b-8a8ee38da67e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1ccdd085b4beb757e0f16e973ad02c9e27a3dafb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66107105"
---
# <a name="sap-netweaver-bi-connection-type-ssrs"></a>Tipo di connessione SAP NetWeaver BI (SSRS)
  Per includere dati da un'origine dati esterna SAP NetWeaver® Business Intelligence nel report, è necessario disporre di un set di dati basato su un'origine dati del report di tipo [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)]. Questo tipo di origine dati incorporata si basa sull'estensione per i dati per il provider di dati [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 1.0 per [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)].  
  
 Questa estensione per i dati consente di recuperare dati multidimensionali da InfoCube, MultiProvider (InfoCube virtuali) e da query Web definite in un'origine dati esterna [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] .  
  
 Usare le informazioni presenti in questo argomento per compilare un'origine dati. Per istruzioni dettagliate, vedere [aggiungere e verificare una connessione dati o un'origine dati &#40;Generatore report e SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
##  <a name="supported-versions"></a><a name="support"></a>Versioni supportate  
 Il provider di dati è stato sviluppato e verificato per SAP BW 3.5 e 7.0.  
  
-   Pacchetto di supporto 20 per SAP BW 3.5 e 7.0  
  
 Per l'autenticazione integrata di Windows, il provider è stato sviluppato e verificato per i sistemi seguenti.  
  
-   SAP Portals 6.40 pacchetto di supporto 20  
  
-   SAP Portals 7.0 pacchetto di supporto 11  
  
-   SAP Duet 1.0  
  
##  <a name="connection-string"></a><a name="Connection"></a>Stringa di connessione  
 Contattare l'amministratore del database per ottenere le informazioni di connessione e le credenziali da utilizzare per connettersi all'origine dati. Nella stringa di connessione di esempio seguente viene specificata un'origine dati [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] in un server usando la porta 8000 e XMLA (XML for Analysis Services) in Internet tramite SOAP:  
  
```  
DataSource=http://mySAPNetWeaverBIServer:8000/sap/bw/xml/soap/xmla  
```  
  
 Per altri esempi di stringhe di connessione, vedere [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
  
  
##  <a name="credentials"></a><a name="Credentials"></a>Credenziali  
 Le credenziali sono necessarie per eseguire query, nonché per visualizzare l'anteprima del report in locale e dal server di report.  
  
 Dopo aver pubblicato il report, potrebbe essere necessario modificare le credenziali per l'origine dati affinché quando il report viene eseguito nel server di report, le autorizzazioni per il recupero dei dati risultino valide.  
  
 Per ulteriori informazioni, vedere [connessioni dati, origini dati e stringhe di connessione in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) o [specificare le credenziali in Generatore report](../specify-credentials-in-report-builder.md).  
  
  
  
##  <a name="queries"></a><a name="Query"></a>Query  
 È possibile utilizzare la finestra Progettazione query con interfaccia grafica in modalità progettazione o query per compilare una query MDX (Multidimensional Expression) visualizzando le strutture di dati sottostanti nell'origine dati. In fase di progettazione è possibile eseguire in modo interattivo una query dalla finestra Progettazione query, per visualizzare i relativi risultati. La query compilata definisce i campi del set di dati. In fase di esecuzione i dati effettivi vengono restituiti dall'origine dei dati. Utilizzare la finestra Progettazione query con interfaccia grafica per eseguire le operazioni seguenti:  
  
-   In modalità progettazione trascinare dimensioni, membri, proprietà dei membri e cifre chiave dall'origine dei dati al riquadro Dati per compilare una query MDX (Multidimensional Expression). Trascinare i membri calcolati dal riquadro Membri calcolati al riquadro Dati per definire ulteriori campi del set di dati.  
  
-   In modalità query trascinare dimensioni, membri, proprietà dei membri e cifre chiave nel riquadro Query oppure digitare il testo MDX direttamente nel riquadro Query. Trascinare i membri calcolati dal riquadro Membri calcolati al riquadro Dati per definire ulteriori campi del set di dati.  
  
 Nel momento in cui vengono compilate le query, Progettazione query aggiunge automaticamente le proprietà predefinite alla query MDX. Per includere proprietà diverse da quelle predefinite è necessario modificare manualmente la query MDX.  
  
 Per altre informazioni sull'utilizzo di questa finestra Progettazione query, vedere [Interfaccia utente di Progettazione query SAP NetWeaver BI &#40;Generatore report&#41;](../sap-netweaver-bi-query-designer-user-interface-report-builder.md).  
  
  
  
##  <a name="extended-field-properties"></a><a name="Extended"></a> Proprietà di campo estese  
 L'origine dati [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] supporta le proprietà di campo estese. Le proprietà di campo estese sono proprietà aggiuntive rispetto a `Value` e `IsMissing` definite per un campo del set di dati dall'estensione per l'elaborazione dei dati. Le proprietà estese includono proprietà predefinite e proprietà personalizzate. Le proprietà predefinite sono comuni a più origini dei dati, mentre quelle personalizzate sono specifiche di ogni origine dei dati.  
  
### <a name="working-with-field-properties"></a>Utilizzo delle proprietà di campo  
 Le proprietà di campo estese non vengono visualizzate nel riquadro Dati report come elementi che è possibile trascinare nel layout del report. È invece possibile trascinare nel report il campo padre della proprietà e quindi modificare la proprietà predefinita da `Value` alla proprietà desiderata. Se, ad esempio, viene creato il nome campo **Calendar Year/Month Level 01** in Progettazione query MDX trascinando un livello dal riquadro dei metadati al riquadro Query, per fare riferimento alla proprietà estesa personalizzata **Long Name** in un'espressione è possibile usare la sintassi seguente:  
  
 `=Fields!Calendar_Year_Month_Level_01("Long Name")`  
  
 Il nome di una proprietà di campo estesa viene visualizzato nella descrizione comando quando il puntatore del mouse passa su un campo nel riquadro dei metadati. Per altre informazioni sulle finestre Progettazione query che è possibile usare per esplorare i dati sottostanti, vedere [Interfaccia utente di Progettazione query SAP NetWeaver BI](sap-netweaver-bi-query-designer-user-interface.md).  
  
> [!NOTE]  
>  I valori per le proprietà di campo estese sono disponibili solo se vengono forniti dall'origine dati quando il report viene eseguito e vengono recuperati i dati per i relativi set di dati. È quindi possibile fare riferimento a tali valori delle proprietà dell'elemento `Field` in qualsiasi espressione utilizzando la sintassi descritta di seguito. Poiché, tuttavia, questi campi sono specifici del provider di dati in uso e non fanno parte del linguaggio RDL, eventuali modifiche apportate a tali valori non vengono salvate con la definizione del report.  
  
 Per fare riferimento alle proprietà estese predefinite in un'espressione, utilizzare uno dei due tipi di sintassi seguenti:  
  
-   *Fields!FieldName.PropertyName*  
  
-   *Campi! FieldName ("PropertyName")*  
  
 Per fare riferimento alle proprietà estese personalizzate in un'espressione, utilizzare la sintassi seguente:  
  
-   *Campi! FieldName ("PropertyName")*  
  
  
  
### <a name="predefined-field-properties"></a>Proprietà di campo predefinite  
 Nella tabella seguente è riportato un elenco delle proprietà di campo predefinite che è possibile usare per un'origine dati [!INCLUDE[SAP_DPE_BW_1](../../includes/sap-dpe-bw-1-md.md)] .  
  
|**Proprietà**|**Type**|**Descrizione o valore previsto**|  
|------------------|--------------|---------------------------------------|  
|`Value`|`Object`|Specifica il valore dei dati del campo.|  
|`IsMissing`|`Boolean`|Indica se il campo è stato trovato nel set di dati risultante.|  
|`FormattedValue`|`String`|Restituisce un valore formattato per una cifra chiave.|  
|`BackgroundColor`|`String`|Restituisce il colore di sfondo definito nel database per il campo.|  
|`Color`|`String`|Restituisce il colore di primo piano definito nel database per l'elemento.|  
|`Key`|`Object`|Restituisce la chiave per un livello.|  
|`LevelNumber`|`Integer`|Per gerarchie padre-figlio, questa proprietà restituisce il numero del livello o della dimensione.|  
|`ParentUniqueName`|`String`|Per gerarchie padre-figlio, restituisce un nome completo del livello padre.|  
|`UniqueName`|`String`|Restituisce il nome completo di un livello. Il `UniqueName` valore di un dipendente, ad esempio, potrebbe essere *[0D_Company]. [ 10D_Department]. [11]*.|  
  
 Per altre informazioni sull'utilizzo di campi e proprietà di campo in un'espressione, vedere [Raccolte predefinite nelle espressioni &#40;Generatore report e SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
  
  
##  <a name="remarks"></a>Osservazioni su <a name="Remarks"></a>  
 Non tutte le modalità di recapito report sono supportate da questo provider di dati. Il recapito di report tramite sottoscrizioni guidate dai dati non è supportato per questa estensione per l'elaborazione dati. Per altre informazioni, vedere [Usare un'origine dati esterna per i dati del Sottoscrittore &#40;sottoscrizione guidata dai dati&#41;](../subscriptions/use-an-external-data-source-for-subscriber-data-data-driven-subscription.md).  
  
 Per altre informazioni, vedere l'articolo relativo all' [utilizzo di SQL Server 2008 Reporting Services con SAP NetWeaver Business Intelligence](https://go.microsoft.com/fwlink/?LinkId=167352).  
  
  
  
##  <a name="how-to-topics"></a><a name="HowTo"></a>Procedure  
 In questa sezione sono contenute istruzioni dettagliate per l'utilizzo di connessioni dati, origini dati e set di dati.  
  
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
 Vengono fornite informazioni sulla raccolta di campi di set di dati generata dalla query.  
  
 [Origini dei dati supportate da Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
 Vengono fornite informazioni dettagliate sul supporto delle piattaforme e delle versioni per ogni estensione per i dati.  
  
 
  
## <a name="see-also"></a>Vedi anche  
 [Parametri del report &#40;Generatore report e Progettazione report&#41;](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [Filtrare, raggruppare e ordinare i dati &#40;Generatore report e SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Espressioni &#40;Generatore report e SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  
