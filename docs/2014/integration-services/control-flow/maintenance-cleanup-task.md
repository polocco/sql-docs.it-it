---
title: Attività Pulizia file manutenzione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.maintenancecleanuptask.f1
helpviewer_keywords:
- deleting files
- removing files
- Maintenance Cleanup task
ms.assetid: 73ad3cd6-9a6d-44cf-905f-c56aa658bf42
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d8b3c3aa4f63018e91370c4e01dada40c35a5f2f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62830800"
---
# <a name="maintenance-cleanup-task"></a>Pulizia file manutenzione - attività
  L'attività Pulizia file manutenzione consente di rimuovere i file correlati ai piani di manutenzione, inclusi i file di backup dei database e i report creati dai piani di manutenzione. Per altre informazioni, vedere [Piani di manutenzione](../../relational-databases/maintenance-plans/maintenance-plans.md) e [Backup e ripristino di database SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
 Tramite l'attività Pulizia file manutenzione un pacchetto può rimuovere dal server specificato i file di backup o i report creati dai piani di manutenzione. L'attività Pulizia file manutenzione include un'opzione che consente di rimuovere un file specifico oppure un gruppo di file in una cartella. Facoltativamente è possibile specificare l'estensione dei file da eliminare.  
  
 Quando si configura l'attività Pulizia file manutenzione per la rimozione dei file di backup, l'estensione predefinita è BAK per i file di database e TXT per i file di report. Tali estensioni possono essere modificate in base alle esigenze, purché abbiano una lunghezza inferiore a 256 caratteri.  
  
 Poiché in genere è necessario rimuovere i file obsoleti non più utilizzati, l'attività Pulizia file manutenzione può essere configurata per l'eliminazione dei file che hanno raggiunto un periodo di memorizzazione specificato. È ad esempio possibile configurare l'attività in modo da eliminare i file che hanno più di quattro settimane. Il periodo di memorizzazione dei file da eliminare può essere specificato in giorni, settimane, mesi o anni. Se non viene specificato il periodo di memorizzazione minimo dei file da eliminare, verranno eliminati tutti i file del tipo specificato.  
  
 Diversamente dalle precedenti versioni dell'attività Pulizia file manutenzione, la versione disponibile in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non elimina automaticamente i file presenti nelle sottodirectory della directory specificata. Questo vincolo riduce la superficie esposta a qualsiasi attacco che potrebbe sfruttare le funzionalità dell'attività Pulizia file manutenzione per eliminare file senza disporre della relativa autorizzazione. Per eliminare le sottocartelle di primo livello è necessario scegliere esplicitamente di eseguire l'operazione selezionando l'opzione **Includi sottocartelle di primo livello** nella finestra di dialogo **Attività Pulizia file manutenzione** .  
  
## <a name="configuration-of-the-maintenance-cleanup-task"></a>Configurazione dell'attività Pulizia file manutenzione  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Questa attività è disponibile nella sezione **Attività di manutenzione** della **casella degli strumenti** di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Attività Pulizia file manutenzione &#40;Piano di manutenzione&#41;](../../relational-databases/maintenance-plans/maintenance-cleanup-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a>Attività correlate  
 Per informazioni dettagliate su come impostare queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vedere [Impostazione delle proprietà di un'attività o di un contenitore](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di Integration Services](integration-services-tasks.md)   
 [Flusso di controllo](control-flow.md)  
  
  
