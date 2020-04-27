---
title: Compilazione di applicazioni tramite servizio Web e .NET Framework | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Report Server Web service, application building
- .NET Framework [Reporting Services]
- XML Web service [Reporting Services], client creation
- reports [Reporting Services], building
- Web service [Reporting Services], application building
- Report Server Web service, client creation
- client configuration [Reporting Services]
- XML Web service [Reporting Services], application building
- Web service [Reporting Services], client creation
ms.assetid: 92a9678c-bc4f-4d7a-ba44-85989bfe27ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5136c67077ff90e7bbbd66ae72fed891267ba7a3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62520346"
---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a>Compilazione di applicazioni tramite servizio Web e .NET Framework
  Con, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]è possibile utilizzare costrutti di programmazione familiari, ad esempio metodi, tipi primitivi e tipi complessi definiti dall'utente per lavorare con i servizi Web. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] include un'infrastruttura e strumenti che è possibile utilizzare per creare i client del servizio Web che possono chiamare qualsiasi servizio Web conforme agli standard del World Wide Web Consortium (W3C).  
  
 Un client del servizio Web ReportServer è qualsiasi componente o applicazione che comunica con un server di report utilizzando messaggi SOAP (Simple Object Access Protocol).  
  
 **Per creare un client del servizio Web ReportServer utilizzando .NET Framework, effettuare i passaggi di base seguenti:**  
  
1.  Creare una classe proxy per il servizio Web.  
  
     A tale scopo, aggiungere una classe proxy o un riferimento Web al progetto di sviluppo, fare riferimento alla classe proxy nel codice client e creare un'istanza del proxy. Per altre informazioni vedere [Creazione del proxy del servizio Web](creating-the-web-service-proxy.md).  
  
2.  Autenticare il client del servizio Web con il server di report.  
  
     A tale scopo, impostare la proprietà <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> dell'oggetto servizio in modo che corrisponda alle credenziali di un utente autenticato nel server di report. Per altre informazioni, vedere [Autenticazione del servizio Web](web-service-authentication.md).  
  
3.  Chiamare il metodo della classe proxy che corrisponde all'operazione del servizio Web che si desidera richiamare.  
  
     A tale scopo, chiamare un metodo del servizio Web e fornire gli argomenti necessari. Per altre informazioni sui metodi del servizio Web, vedere [Metodi del servizio Web ReportServer](../methods/report-server-web-service-methods.md). Per altre informazioni sulla chiamata, vedere [Chiamata ai metodi del servizio Web](calling-web-service-methods.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Creazione del proxy del servizio Web](creating-the-web-service-proxy.md)|Vengono descritte le modalità di aggiunta di una classe proxy al progetto [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]utilizzando.|  
|[Autenticazione del servizio Web](web-service-authentication.md)|Viene descritto in che modo vengono autenticate le chiamate al servizio Web ReportServer.|  
|[Chiamata ai metodi del servizio Web](calling-web-service-methods.md)|Viene descritto come utilizzare l'API SOAP per chiamare i metodi del servizio [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]Web in.|  
|[Impostazione della proprietà Url del servizio Web](setting-the-url-property-of-the-web-service.md)|Viene illustrato come indirizzare a livello di programmazione il proxy del servizio Web a un nuovo URL del server dopo avere creato il riferimento Web.|  
|[Impostazione degli argomenti dei metodi del servizio Web](supplying-web-service-method-arguments.md)|Viene descritto come richiamare un metodo del servizio Web e come fornire gli argomenti del metodo.|  
|[Omissione di valori per gli oggetti del servizio Web facoltativi](omitting-values-for-optional-web-service-objects.md)|Viene descritto come omettere i valori per gli oggetti del servizio Web facoltativi.|  
|[Utilizzo di metodi del servizio Web protetti](using-secure-web-service-methods.md)|Viene descritta l'impostazione **SecureConnectionLevel** e in che modo influisce sull'uso dell'API SOAP di Reporting Services.|  
|[Passaggio delle impostazioni relative alle informazioni sul dispositivo alle estensioni per il rendering](passing-device-information-settings-to-rendering-extensions.md)|Vengono descritte le impostazioni relative alle informazioni sul dispositivo utilizzate per eseguire il rendering dei report in formati diversi.|  
|[Impostazioni delle estensioni per il recapito di Reporting Services](reporting-services-delivery-extension-settings.md)|Vengono descritte le impostazioni utilizzate per recapitare i report utilizzando il servizio di posta elettronica del server di report.|  
|[Utilizzo di intestazioni SOAP di Reporting Services](../../report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|Viene illustrato l'utilizzo delle intestazioni SOAP in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Introduzione alla gestione delle eccezioni in Reporting Services](../../report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|Vengono fornite informazioni sulla modalità di gestione degli errori in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Vedi anche  
 [Servizio Web ReportServer](../report-server-web-service.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  
