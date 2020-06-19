---
title: Installare ADOMD.NET nei server front-end Web che eseguono Amministrazione centrale | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4acc6888e88a4186a48a6047d8d21fffc9a0f3ec
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054767"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a>Installare ADOMD.NET in server front-end Web in cui viene eseguita Amministrazione centrale
  Se si installa PowerPivot per SharePoint in una farm che dispone della topologia di Amministrazione centrale, senza Excel Services o PowerPivot per SharePoint, scaricare e installare la libreria client Microsoft ADOMD.NET se si desidera l'accesso completo ai report incorporati nel dashboard di gestione PowerPivot. Alcuni report nel dashboard utilizzano ADOMD.NET per accedere a dati interni relativi all'integrità del server e all'elaborazione query di PowerPivot nella farm.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010  
  
 Per SharePoint 2013, il provider è incluso nel Feature Pack di SQL Server. Per informazioni su come scaricare spPowerPivot.msi, vedere [Microsoft SQL Server Feature Pack di 2014](https://www.microsoft.com/download/details.aspx?id=35577)  
  
### <a name="download-and-install-the-client-library"></a>Scaricare e installare la libreria client  
  
1.  Nella [pagina SQL Server 2014 Feature Pack](https://go.microsoft.com/fwlink/?LinkID=296473)trovare Microsoft ADOMD.NET.  
  
2.  Scaricare il pacchetto per x64 del programma di installazione `SQL_AS_ADOMD.msi`.  
  
3.  Eseguire il file con estensione msi per installare la libreria.  
  
4.  Reimpostare IIS dopo aver completato l'installazione. Aprire un prompt dei comandi amministrativo e digitare **iisreset**.  
  
### <a name="verify-installation"></a>Verificare l'installazione  
  
1.  Spostarsi su Windows\Assembly.  
  
2.  Fare clic con il pulsante destro del mouse su Microsoft. AnalysisServices. AdomdClient e scegliere **Proprietà**.  
  
3.  Fare clic su **Versione**.  
  
4.  Verificare che la versione includa 12,00.\<build number> e che la descrizione sia Microsoft. AnalysisService. AdomdClient.  
  
## <a name="see-also"></a>Vedere anche  
 [Dati di utilizzo e dashboard di gestione PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data)  
  
  
