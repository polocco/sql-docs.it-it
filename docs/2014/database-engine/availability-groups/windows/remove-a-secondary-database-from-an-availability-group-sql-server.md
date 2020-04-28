---
title: Rimuovere un database secondario da un gruppo di disponibilità (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.unjoindb.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], databases
ms.assetid: 4e51a570-58d7-4f01-9390-4198f3602576
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 85cd7335290a619a7dd7b5e2cfcb729879bdaf6f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "72782946"
---
# <a name="remove-a-secondary-database-from-an-availability-group-sql-server"></a>Rimuovere un database secondario da un gruppo di disponibilità (SQL Server)
  In questo argomento viene illustrato come rimuovere un database secondario da un gruppo di disponibilità AlwaysOn utilizzando [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]o PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
-   **Prima di iniziare:**  
  
     [Prerequisiti](#Prerequisites)  
  
     [Sicurezza](#Security)  
  
-   **Per rimuovere un database secondario tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   **Completamento:**  [Dopo la rimozione di un database secondario da un gruppo di disponibilità](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a>   
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a>Prerequisiti e restrizioni  
  
-   Questa attività è supportata solo sulle repliche secondarie. È necessario essere connessi all'istanza del server che ospita la replica secondaria da cui verrà rimosso il database.  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER per il database.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 **Per rimuovere un database secondario da un gruppo di disponibilità**  
  
1.  In Esplora oggetti connettersi all'istanza del server che ospita la replica secondaria da cui si desidera rimuovere uno o più database secondari ed espandere l'albero del server.  
  
2.  Espandere il nodo **Disponibilità elevata AlwaysOn** e il nodo **Gruppi di disponibilità** .  
  
3.  Selezionare il gruppo di disponibilità ed espandere il nodo **Database di disponibilità** .  
  
4.  Questo passaggio dipende dalla scelta di rimuovere uno o più database:  
  
    -   Per rimuovere più database, utilizzare il riquadro **Dettagli Esplora oggetti** per visualizzare e selezionare tutti i database che si desidera rimuovere. Per altre informazioni, vedere [Utilizzare Dettagli Esplora oggetti per monitorare Gruppi di disponibilità &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).  
  
    -   Per rimuovere un singolo database, selezionarlo nel riquadro **Esplora oggetti** o **Dettagli Esplora oggetti** .  
  
5.  Fare clic con il pulsante destro del mouse sul database o sui database selezionati e scegliere **Rimuovi database secondario** nel menu dei comandi.  
  
6.  Nella finestra di dialogo **Rimuovi database dal gruppo di disponibilità** scegliere **OK**per rimuovere tutti i database elencati. Se non si desidera rimuovere tutti i database elencati, fare clic su **Annulla**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per rimuovere un database secondario da un gruppo di disponibilità**  
  
1.  Connettersi all'istanza del server che ospita la replica secondaria.  
  
2.  Utilizzare la [clausola SET HADR dell'istruzione ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr) come indicato di seguito:  
  
     ALTER DATABASE *nome_database* SET HADR OFF  
  
     dove *nome_database* è il nome di un database secondario da rimuovere dal gruppo di disponibilità a cui appartiene.  
  
     L'esempio seguente mostra come rimuovere il database secondario locale *MyDb2* dal relativo gruppo di disponibilità.  
  
    ```sql
    ALTER DATABASE MyDb2 SET HADR OFF;  
    GO  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Utilizzo di PowerShell  
 **Per rimuovere un database secondario da un gruppo di disponibilità**  
  
1.  Impostare la directory (`cd`) sull'istanza del server in cui viene ospitata la replica secondaria.  
  
2.  Usare il cmdlet **Remove-SqlAvailabilityDatabase** specificando il nome del database di disponibilità da rimuovere dal gruppo di disponibilità. Quando si è connessi a un'istanza del server che ospita una replica secondaria, solo il database secondario locale verrà rimosso dal gruppo di disponibilità.  
  
     Ad esempio, il comando seguente rimuove il database secondario `MyDb8` dalla replica secondaria ospitata dall'istanza del server denominata `SecondaryComputer\Instance`. La sincronizzazione dei dati con i database secondari rimossi viene terminata. Questo comando non influisce sul database primario né su nessun altro database secondario.  
  
    ```powershell
    Remove-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\SecondaryComputer\InstanceName\AvailabilityGroups\MyAg\Databases\MyDb8  
    ```  
  
    > [!NOTE]  
    >  Per visualizzare la sintassi di un cmdlet, utilizzare il cmdlet `Get-Help` nell'ambiente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Per altre informazioni, vedere [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Per impostare e utilizzare il provider PowerShell per SQL Server**  
  
-   [Provider PowerShell per SQL Server](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-a-secondary-database-from-an-availability-group"></a><a name="FollowUp"></a>Completamento: dopo la rimozione di un database secondario da un gruppo di disponibilità  
 Quando un database secondario viene rimosso, non è più unito in join al gruppo di disponibilità e tutte le informazioni relative al database secondario rimosso vengono ignorate dal gruppo di disponibilità. Il database secondario rimosso viene posto nello stato RESTORING.  
  
> [!TIP]  
>  Per un breve intervallo di tempo dopo avere rimosso un database secondario, è possibile riavviare la sincronizzazione dei dati AlwaysOn sul database creando nuovamente un join al gruppo di disponibilità. Per altre informazioni, vedere [Creare un join di un database secondario a un gruppo di disponibilità &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
 A questo punto sono disponibili modi alternativi per gestire un database secondario rimosso:  
  
-   Se il database secondario non è più necessario, è possibile eliminarlo.  
  
     Per altre informazioni, vedere [DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) o [Eliminare un database](../../../relational-databases/databases/delete-a-database.md).  
  
-   Se si desidera accedere a un database secondario dopo che è stato rimosso dal gruppo di disponibilità, è possibile recuperare il database. Tuttavia, se si recupera un database secondario rimosso, saranno online due database indipendenti e divergenti con lo stesso nome. È necessario assicurarsi che i client possano accedere solo al database primario corrente.  
  
     Per altre informazioni, vedere [Recupero di un database senza ripristino dei dati &#40;Transact-SQL&#41;](../../../relational-databases/backup-restore/recover-a-database-without-restoring-data-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Rimuovere un database primario da un gruppo di disponibilità &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
