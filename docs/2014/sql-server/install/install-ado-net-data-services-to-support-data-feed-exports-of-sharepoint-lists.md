---
title: Installare ADO.NET Data Services per supportare esportazioni di feed di dati di elenchi SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: f32527ae-f623-4e08-adfb-6d3262f5c2ac
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fb47804daee38427f48baefdf3997edda5fb90b1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054757"
---
# <a name="install-adonet-data-services-to-support-data-feed-exports-of-sharepoint-lists"></a>Installare ADO.NET Data Services per supportare esportazioni di feed di dati di elenchi SharePoint
  ADO.NET Data Services è necessario per un'esportazione dei feed di dati di elenchi SharePoint. SharePoint 2010 non include questo componente nel programma di installazione essenziale di SharePoint, pertanto è necessario installarlo manualmente.  
  
 Senza questo prerequisito, si otterrà l'errore seguente quando si tenta di utilizzare un elenco SharePoint esportato come feed di dati: "Per motivi di sicurezza, la dichiarazione DTD non è consentita in questo documento XML. Per abilitare l'elaborazione DTD impostare la proprietà ProhibitDtd in XmlReaderSettings su false e passare le impostazioni al metodo XmlReader.Create".  
  
 Utilizzare le istruzioni seguenti per installare ADO.NET Data Services in ogni server SharePoint per il quale si desidera l'esportazione degli elenchi come feed di dati.  
  
### <a name="download-and-install-adonet-data-services"></a>Scaricare e installare ADO.NET Data Services  
  
1.  Vedere la documentazione sui requisiti hardware e software per SharePoint 2010, [requisiti hardware e software (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734)  
  
2.  Per **accedere al software applicabile**, trovare il collegamento per ADO.NET Data Services 3,5 che corrisponde al sistema operativo in uso (windows Server 2008 SP2 o windows Server 2008 R2).  
  
3.  Fare clic sul collegamento ed eseguire il programma di installazione che consente di installare il servizio.  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di PowerPivot per SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
