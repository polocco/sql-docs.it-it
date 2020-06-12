---
title: Esempio di configurazione con privilegi minimi per PowerPivot per SharePoint 2013 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c1e09e6c-52d3-48ab-8c70-818d5d775087
author: minewiskan
ms.author: owend
ms.openlocfilehash: b00bbdf6063bc0451244792ee423825b4f74cc40
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543863"
---
# <a name="example-of-a-minimum-privilege-configuration-for-powerpivot-for-sharepoint-2013"></a>Esempio di una configurazione con privilegi minimi per PowerPivot per SharePoint 2013
  In questo argomento viene illustrata una configurazione di esempio di PowerPivot per SharePoint 2013 con privilegi minimi. Nella configurazione viene utilizzato un account diverso per ognuno dei tre componenti e ogni account dispone del livello minimo di privilegi.  
  
## <a name="summary-of-accounts"></a>Riepilogo degli account  
 PowerPivot per SharePoint 2013 supporta l'utilizzo dell'account Servizio di rete per l'account del servizio Analysis Services. L'account Servizio di rete non è supportato con SharePoint 2010. Per ulteriori informazioni sugli account del servizio, vedere [configurare account di servizio e autorizzazioni di Windows](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) ( https://msdn.microsoft.com/library/ms143504.aspx) .  
  
 Nella tabella seguente sono riepilogati i tre account utilizzati nell'esempio di configurazione con privilegi minimi.  
  
|Scope|Nome|  
|-----------|----------|  
|Account amministratore di SharePoint|**SPAdmin**|  
|Account farm SharePoint|**SPFarm**|  
|Account del servizio Analysis Services|**SPsvc**|  
  
### <a name="the-sharepoint-administrator-account-spadmin"></a>Account amministratore di SharePoint (SpAdmin)  
 **SPAdmin** è un account di dominio usato per installare e configurare la farm. Si tratta dell'account utilizzato per eseguire la configurazione guidata SharePoint e dello strumento di configurazione PowerPivot per SharePoint 2013. l'account **SPAdmin** è l'unico account che richiede diritti di amministratore locale. Prima di eseguire lo strumento di configurazione PowerPivot, concedere i privilegi dell'account **SPAdmin** all'istanza del database di SQL Server in cui SharePoint crea il contenuto e i database di configurazione. Per configurare l'account SPAdmin in uno scenario con privilegi minimi, l'account deve essere un membro dei ruoli **securityadmin** e **dbcreator**.  
  
### <a name="the-farm-account-spfarm"></a>Account farm (SPFarm)  
 **SPFarm** è un account di dominio usato dal servizio Timer di SharePoint e dall'applicazione Web per Amministrazione centrale per accedere al database del contenuto di SharePoint. Per questo account non è necessario essere un amministratore locale. Tramite la Configurazione guidata SharePoint vengono concessi i privilegi minimi appropriati nel database back-end di SQL Server. La configurazione di privilegi minimi di SQL Server è l'appartenenza ai ruoli **securityadmin** e **dbcreator**.  
  
### <a name="the-service-account-for-powerpivot-service-spsvc"></a>Account del servizio per il servizio PowerPivot (SPscv)  
 Se una nuova farm di SharePoint non viene configurata prima dell'esecuzione dello strumento di configurazione di PowerPivot, tramite quest'ultimo, per impostazione predefinita, verranno creati gli elementi seguenti:  
  
-   Applicazione di servizio PowerPivot.  
  
-   Applicazione Excel Services.  
  
-   Applicazione di archiviazione sicura.  
  
 Tramite lo strumento di configurazione di PowerPivot vengono configurate tutte e tre le applicazioni di servizio nel pool di applicazioni predefinito. Il pool di applicazioni viene in genere configurato per l'esecuzione come account SPFarm, tramite cui è possibile accedere a molte risorse non richieste da un account del servizio. Per garantire all'ambiente i privilegi minimi, configurare l'utilizzo di un nuovo account di dominio da parte del pool di applicazioni e dell'applicazione Web appropriati.  
  
 **Per creare un nuovo account di dominio SPsvc da utilizzare come account del servizio SharePoint:**  
  
1.  In Amministrazione centrale SharePoint fare clic su **sicurezza**.  
  
2.  Fare clic su **Configura account di servizio**  
  
3.  Fare clic su **Registra nuovo account gestito**.  
  
 L'account **SPSvc** non include i privilegi di amministratore locale e SPsvc non avrà alcun privilegio nel database di SharePoint. Gli unici privilegi richiesti da SPsvc sono i diritti di amministratore per l'istanza di PowerPivot di Analysis Services.  
  
 **Per configurare il pool di applicazioni appropriato per l'utilizzo dell'account SPsvc:**  
  
1.  In Amministrazione centrale SharePoint fare clic su **sicurezza**.  
  
2.  Fare clic su **Configura account di servizio**.  
  
3.  Selezionare il pool di applicazioni del servizio utilizzato dall'applicazione di servizio PowerPivot. Successivamente, selezionare l'account SPSvc.  
  
 **Per concedere l'accesso all'applicazione Web con PowerShell:**  
  
1.  Eseguire la shell di gestione di SharePoint 2013 con privilegi di amministratore.  
  
2.  Eseguire il codice PowerShell riportato di seguito:  
  
    ```powershell
    $webApp = Get-SPWebApplication "http://<servername>"  
    $webApp.GrantAccessToProcessIdentity("DOMAIN\<ServiceAccountName>")
    ```  
