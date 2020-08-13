---
title: Spostarsi all'interno dei percorsi di SQL Server PowerShell | Microsoft Docs
description: Informazioni su come usare i cmdlet di PowerShell per spostarsi nelle strutture dei percorsi che rappresentano la gerarchia di oggetti supportati da un provider PowerShell.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: d68aca48-d161-45ed-9f4f-14122ed30218
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 93055cda4e87e36ff430486842d4aa86073e5c50
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86904512"
---
# <a name="navigate-sql-server-powershell-paths"></a>Spostarsi all'interno dei percorsi di SQL Server PowerShell
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Il provider [!INCLUDE[ssDE](../includes/ssde-md.md)] PowerShell espone il set di oggetti in un'istanza di SQL Server in una struttura analoga a un percorso di file. È possibile utilizzare cmdlet di Windows PowerShell per spostarsi all'interno del percorso del provider e creare unità personalizzate per rendere più breve il percorso da digitare.  

> [!NOTE]
> Esistono due moduli SQL Server PowerShell: **SqlServer** e **SQLPS**. Il modulo **SQLPS** è incluso nell'installazione di SQL Server (per la compatibilità con le versioni precedenti), ma non viene più aggiornato. Il modulo PowerShell più aggiornato è il modulo **SqlServer**. Il modulo **SqlServer** contiene versioni aggiornate dei cmdlet di **SQLPS** e include anche nuovi cmdlet per il supporto delle funzionalità SQL più recenti.  
> Le versioni precedenti del modulo **SqlServer** *erano* incluse con SQL Server Management Studio (SSMS), ma solo con le versioni 16.x di SQL Server Management Studio. Per usare PowerShell con SSMS 17.0 e versioni successive, è necessario installare il modulo **SqlServer** da PowerShell Gallery.
> Per installare il modulo **SqlServer**, vedere [Installare il modulo PowerShell SqlServer](download-sql-server-ps-module.md).
  
Windows PowerShell implementa cmdlet per spostarsi all'interno della struttura del percorso che rappresenta la gerarchia di oggetti supportati da un provider PowerShell. Quando si passa a un nodo nel percorso, è possibile utilizzare altri cmdlet per eseguire operazioni di base sull'oggetto corrente. Poiché vengono utilizzati frequentemente, i cmdlet dispongono di alias brevi e canonici. È inoltre presente un set di alias che esegue il mapping dei cmdlet a comandi simili del prompt dei comandi e un altro set per i comandi della shell di UNIX.  
  
 Il provider [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] implementa un subset di cmdlet del provider, illustrato nella tabella seguente:  
  
|Cmdlet|Alias canonico|Alias cmd|Alias di shell di UNIX|Descrizione|  
|------------|---------------------|---------------|----------------------|-----------------|  
|**Get-Location**|**gl**|**pwd**|**pwd**|Consente di ottenere il nodo corrente.|  
|**Set-Location**|**sl**|**cd, chdir**|**cd, chdir**|Consente di modificare il nodo corrente.|  
|**Get-ChildItem**|**gci**|**dir**|**ls**|Consente di visualizzare un elenco degli oggetti archiviati nel nodo corrente.|  
|**Get-Item**|**gi**|||Restituisce le proprietà dell'elemento corrente.|  
|**Rename-Item**|**rni**|**rn**|**ren**|Consente di rinominare un oggetto.|  
|**Remove-Item**|**ri**|**del, rd**|**rm, rmdir**|Consente di rimuovere un oggetto.|  
  
> [!IMPORTANT]  
>  Alcuni identificatori (nomi di oggetto) di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contengono caratteri non supportati da Windows PowerShell nei nomi dei percorsi. Per altre informazioni sull'uso dei nomi che contengono questi caratteri, vedere [Identificatori di SQL Server in PowerShell](sql-server-identifiers-in-powershell.md).  
  
### <a name="sql-server-information-returned-by-get-childitem"></a>Informazioni su SQL Server restituite da Get-ChildItem  
 Le informazioni restituite da **Get-ChildItem** (o dai relativi alias **dir** e **ls** ) dipendono dalla posizione in un percorso SQLSERVER.  
  
|Posizione nel percorso|Risultati di Get-ChildItem|  
|-------------------|----------------------------|  
|SQLSERVER:\SQL|Restituisce il nome del computer locale. Se per la connessione a istanze del [!INCLUDE[ssDE](../includes/ssde-md.md)] in altri computer è stato usato SMO o WMI, vengono elencati anche tali computer.|  
|SQLSERVER:\SQL\\*NomeComputer*|Elenco delle istanze di [!INCLUDE[ssDE](../includes/ssde-md.md)] nel computer.|  
|SQLSERVER:\SQL\\*NomeComputer*\\*NomeIstanza*|Elenco dei tipi di oggetto di primo livello nell'istanza, ad esempio Endpoint, Certificati e Database.|  
|Nodo della classe di oggetto, ad esempio Database|Elenco di oggetti del tipo, ad esempio l'elenco di database: master, model, AdventureWorks2008R2.|  
|Nodo del nome dell'oggetto, ad esempio AdventureWorks2012|Elenco dei tipi di oggetto contenuti all'interno dell'oggetto. Per un database, ad esempio, vengono elencati tipi di oggetto come tabelle e viste.|  
  
 Per impostazione predefinita, **Get-ChildItem** non elenca oggetti di sistema. Usare il parametro *Force* per visualizzare gli oggetti di sistema, ad esempio gli oggetti nello schema **sys** .  
  
### <a name="custom-drives"></a>Unità personalizzate  
 Windows PowerShell consente agli utenti di definire unità virtuali, definite come unità di PowerShell. Per tali unità viene eseguito il mapping ai nodi iniziali di un'istruzione di percorso. Tali unità vengono in genere utilizzate per abbreviare percorsi digitati con frequenza. I percorsi SQLSERVER: possono diventare lunghi, occupando spazio nella finestra di Windows PowerShell e richiedendo molta digitazione. Se si prevede di lavorare molto in un particolare nodo del percorso, è possibile definire un'unità di Windows PowerShell personalizzata di cui è stato eseguito il mapping a tale nodo.  
  
## <a name="use-powershell-cmdlet-aliases"></a>Utilizzare alias di cmdlet di PowerShell  
 **Utilizzare un alias di cmdlet**  
  
-   Anziché digitare il nome completo di un cmdlet, digitare un alias più breve o uno con mapping a un comando comune del prompt dei comandi.  
  
### <a name="alias-example-powershell"></a>Esempio di alias (PowerShell)  
 È ad esempio possibile utilizzare uno dei set di cmdlet o alias seguenti per recuperare un elenco delle istanze di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] disponibili passando alla cartella SQLSERVER:\SQL e richiedendo l'elenco di elementi figlio per la cartella:  
  
```  
## Shows using the full cmdet name.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## Shows using canonical aliases.  
sl SQLSERVER:\SQL  
gci  
  
## Shows using command prompt aliases.  
cd SQLSERVER:\SQL  
dir  
  
## Shows using Unix shell aliases.  
cd SQLSERVER:\SQL  
ls  
```  
  
## <a name="use-get-childitem"></a>Utilizzare Get-ChildItem  
 **Restituire informazioni utilizzando Get-ChildItem**  
  
1.  Passare al nodo per il quale si vuole ottenere un elenco di elementi figlio  
  
2.  Eseguire Get-ChildItem per ottenere l'elenco.  
  
### <a name="get-childitem-example-powershell"></a>Esempio di Get-ChildItem (PowerShell)  
 In questi esempi sono illustrate le informazioni restituite da Get-ChildItem per i nodi diversi in un percorso del provider SQL Server.  
  
```  
## Return the current computer and any computer  
## to which you have made a SQL or WMI connection.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## List the instances of the Database Engine on the local computer.  
  
Set-Location SQLSERVER:\SQL\localhost  
Get-ChildItem  
  
## Lists the categories of objects available in the  
## default instance on the local computer.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT  
Get-ChildItem  
  
## Lists the databases from the local default instance.  
## The force parameter is used to include the system databases.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-ChildItem -force  
```  
  
## <a name="create-a-custom-drive"></a>Creare un'unità personalizzata  
 **Creare e utilizzare un'unità personalizzata**  
  
1.  Usare **New-PSDrive** per definire un'unità personalizzata. Usare il parametro **Root** per specificare il percorso rappresentato dal nome di unità personalizzato.  
  
2.  Fare riferimento al nome di unità personalizzata nei cmdlet di navigazione come **Set-Location**.  
  
### <a name="custom-drive-example-powershell"></a>Esempio di unità personalizzata (PowerShell)  
 Questo esempio crea un'unità virtuale denominata AWDB con mapping al nodo di una copia distribuita del database di esempio di AdventureWorks2012. L'unità virtuale è utilizzata quindi per passare a una tabella nel database.  
  
```  
## Create a new virtual drive.  
New-PSDrive -Name AWDB -Root SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
  
## Use AWDB: to navigate to a specific table.  
Set-Location AWDB:\Tables\Purchasing.Vendor  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Provider PowerShell per SQL Server](sql-server-powershell-provider.md)   
 [Utilizzo di percorsi di SQL Server PowerShell](work-with-sql-server-powershell-paths.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  
