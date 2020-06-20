---
title: Regole di business (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], about business rules
- business rules [Master Data Services]
ms.assetid: a9f9e41a-2461-4845-b947-58b3a205543f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 84871fb62e07cd49d0e63335c6a6b78b9e3ba0ae
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972121"
---
# <a name="business-rules-master-data-services"></a>Regole business (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]una regola business è una regola utilizzata per garantire la qualità e l'accuratezza dei dati master. È possibile utilizzare una regola business per aggiornare automaticamente i dati, inviare posta elettronica o per avviare un processo aziendale o un flusso di lavoro.  
  
## <a name="create-and-publish-business-rules"></a>Creare e pubblicare regole business  
 Le regole business sono istruzioni `If/Then` create in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Se un valore di attributo soddisfa una condizione specificata, viene eseguita una determinata azione. Tra le possibili azioni è inclusa l'impostazione di un valore predefinito o la modifica di un valore. Queste azioni possono essere combinate con l'invio di una notifica tramite posta elettronica.  
  
 Le regole business possono essere basate su valori di attributo specifici, ad esempio eseguire un'azione se Color=Blue, o quando i valori di attributo vengono modificati, ad esempio eseguire un'azione se l'attributo Color viene modificato. Per altre informazioni sul rilevamento di modifiche non specifiche, vedere [Rilevamento modifiche &#40;Master Data Services&#41;](change-tracking-master-data-services.md).  
  
 Per utilizzare regole business, è necessario prima crearle e pubblicarle, quindi applicare le regole pubblicate ai dati. È possibile applicare regole a subset di dati o a tutti i dati di una versione convalidando la versione. Il commit di una versione non può essere eseguito finché tutti gli attributi non hanno superato la convalida tramite regole business.  
  
 Se un utente tenta di aggiungere un valore di attributo che non ha superato la convalida tramite una regola business, tale valore può comunque essere salvato. È possibile controllare e correggere i problemi di convalida visualizzati in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Quando si crea un pacchetto di distribuzione di modelli, se si desidera includere regole business è necessario includere i dati della versione contenuta nel pacchetto.  
  
 Se si crea una regola business che utilizza l'operatore **OR** , è necessario creare una regola separata per ogni istruzione condizionale che può essere valutata indipendentemente. È quindi possibile escludere regole in base alle esigenze, offrendo maggiore flessibilità e una più facile risoluzione dei problemi.  
  
## <a name="how-business-rules-are-applied"></a>Come vengono applicate le regole business  
 È possibile impostare l'ordine di priorità di esecuzione delle regole. Tuttavia, prima che la priorità venga presa in considerazione, le regole business vengono applicate in base al tipo di azioni che la regola esegue. L'ordine è il seguente:  
  
1.  **Valore predefinito**  
  
2.  **Modifica valore**  
  
3.  **Convalida**  
  
4.  **Azione esterna**  
  
 In questi gruppi, le azioni vengono applicate con ordine di priorità crescente, dalla più bassa alla più elevata. Di conseguenza, ad esempio, quattro regole separate potrebbero avere le azioni **Valore predefinito** . L'azione **Valore predefinito** che viene eseguita per prima dipende dall'ordine di priorità specificato nell'interfaccia utente Web.  
  
 Altre note importanti sull'applicazione delle regole:  
  
-   Se una regola business è esclusa o non è pubblicata con lo stato **Attiva**, la regola è comunque disponibile ma non sarà inclusa quando vengono applicate le regole business.  
  
-   Le regole business si applicano ai valori di attributo per tutti i membri foglia oppure per quelli consolidati, non entrambi.  
  
-   Le regole business possono essere applicate a qualsiasi versione di un modello, cioè **Apri** o **Bloccato**.  
  
-   Le modifiche apportate ai dati, quando le regole business vengono applicate, non vengono registrate come transazioni.  
  
-   Una regola business non può contenere più di un'azione **avvia flusso di lavoro** .  
  
## <a name="system-settings"></a>Impostazioni sistema  
 In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] sono disponibili due impostazioni che influiscono sulle regole business. È possibile regolare tali impostazioni in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] o direttamente nella tabella Impostazioni sistema. Per altre informazioni, vedere [Impostazioni di sistema &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Creare e pubblicare una nuova regola business.|[Creare e pubblicare una regola business &#40;Master Data Services&#41;](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|Aggiungere più condizioni a una regola business.|[Aggiungere più condizioni a una regola business &#40;Master Data Services&#41;](../../2014/master-data-services/add-multiple-conditions-to-a-business-rule-master-data-services.md)|  
|Creare una regola business affinché gli attributi dispongano di valori.|[Richiedere valori di attributo &#40;Master Data Services&#41;](../../2014/master-data-services/require-attribute-values-master-data-services.md)|  
|Creare una regola business per eseguire un'azione basata su modifiche dei valori di attributo.|[Inizializzare azioni basate su modifiche dei valori di attributo &#40;Master Data Services&#41;](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
|Modificare il nome di una regola business esistente.|[Modificare il nome di una regola business &#40;Master Data Services&#41;](../../2014/master-data-services/change-a-business-rule-name-master-data-services.md)|  
|Configurare [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] per inviare notifiche quando vengono applicate le regole business.|[Configurare le regole di business per l'invio di notifiche &#40;Master Data Services&#41;](../../2014/master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
|Applicare le regole business a membri specifici.|[Convalidare membri specifici rispetto a regole business &#40;Master Data Services&#41;](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|Escludere una regola business in modo che non venga utilizzata.|[Escludere una regola business &#40;Master Data Services&#41;](../../2014/master-data-services/exclude-a-business-rule-master-data-services.md)|  
|Eliminare una regola business esistente.|[Eliminare una regola di business &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-business-rule-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Panoramica di Master Data Services](master-data-services-overview-mds.md)  
  
-   [Versioni &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md)  
  
-   [Convalida &#40;Master Data Services&#41;](../../2014/master-data-services/validation-master-data-services.md)  
  
-   [Rilevamento modifiche &#40;Master Data Services&#41;](change-tracking-master-data-services.md)  
  
  
