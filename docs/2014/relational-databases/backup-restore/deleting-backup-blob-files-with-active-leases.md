---
title: Eliminazione dei file BLOB di backup con lease attivi | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 13a8f879-274f-4934-a722-b4677fc9a782
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 663bab775aff9a04a4a9d93f2bcbd0e193b18f37
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "72783059"
---
# <a name="deleting-backup-blob-files-with-active-leases"></a>Eliminazione dei file BLOB di backup con lease attivi
  Quando si esegue il backup o il ripristino da archiviazione di Azure, SQL Server acquisisce un lease infinito per bloccare l'accesso esclusivo al BLOB. Quando il processo di backup o ripristino viene completato correttamente, il lease viene rilasciato. Se il backup o il ripristino non viene completato, il processo di backup tenta di eliminare i BLOB non validi. Tuttavia, se il backup non viene completato a causa di un problema di connettività di rete che persiste nel tempo, è possibile che il processo di backup non sia in grado di accedere al BLOB e che quindi quest'ultimo rimanga orfano. Di conseguenza, il BLOB non può essere scritto o eliminato finché il lease non viene rilasciato. In questo argomento viene descritto come rilasciare il lease ed eliminare il BLOB.  
  
 Per altre informazioni sui tipi di lease, leggere questo [articolo](https://go.microsoft.com/fwlink/?LinkId=275664).  
  
 Il mancato completamento dell'operazione di backup potrebbe generare un file di backup non valido.  Anche nel file BLOB di backup potrebbe essere presente un lease attivo, impedendone l'eliminazione o la sovrascrittura.  Per eliminare o sovrascrivere questi BLOB, è innanzitutto necessario interrompere il lease. Se si verificano errori di backup, è consigliabile rimuovere i lease ed eliminare i BLOB. È inoltre possibile scegliere di effettuare rimozioni periodiche come parte delle attività di gestione della memoria.  
  
 Se si verifica un errore di ripristino, i ripristini successivi non vengono bloccati e pertanto il lease attivo potrebbe non essere un problema. L'interruzione del lease è necessaria solo quando si deve sovrascrivere o eliminare il BLOB.  
  
## <a name="managing-orphaned-blobs"></a>Gestione dei BLOB orfani  
 Nei passaggi seguenti viene descritto come effettuare una rimozione dopo un backup non riuscito o un'attività di ripristino. Tutti i passaggi possono essere effettuati utilizzando gli script di PowerShell. Nella sezione seguente è disponibile un esempio di codice:  
  
1.  **Identificazione di BLOB con lease:** se si dispone di uno script o un processo in cui vengono eseguiti i processi di backup, è possibile rilevare l'errore nello script o nel processo e usarlo per rimuovere i BLOB.   È inoltre possibile utilizzare le proprietà LeastState e LeaseStats per identificare i BLOB con lease. Dopo aver identificato i BLOB, è consigliabile rivedere l'elenco e verificare la validità del file di backup prima di eliminare il BLOB.  
  
2.  **Interruzione del lease:** tramite una richiesta autorizzata è possibile interrompere il lease senza specificare un relativo ID. Per ulteriori informazioni, vedere [qui](https://go.microsoft.com/fwlink/?LinkID=275664) .  
  
    > [!TIP]  
    >  Tramite SQL Server viene generato un ID lease per stabilire l'accesso esclusivo durante l'operazione di ripristino. L'ID lease di ripristino è BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2.  
  
3.  **Eliminazione del BLOB:** per eliminare un BLOB con un lease attivo è innanzitutto necessario interrompere il lease.  
  
###  <a name="powershell-script-example"></a><a name="Code_Example"></a>Esempio di script di PowerShell  
 ** \* Importante \* \* ** Se si esegue PowerShell 2,0, è possibile che si verifichino problemi durante il caricamento dell'assembly Microsoft WindowsAzure. storage. dll. È consigliabile effettuare l'aggiornamento a Powershell 3.0 per risolvere il problema. È inoltre possibile utilizzare la soluzione alternativa per PowerShell 2.0:  
  
-   Creare o modificare il file powershell.exe.config per caricare gli assembly .NET 2.0 e .NET 4.0 in fase di esecuzione con quanto riportato di seguito:  
  
    ```xml
    <?xml version="1.0"?>
    <configuration>
        <startup useLegacyV2RuntimeActivationPolicy="true">
            <supportedRuntime version="v4.0.30319"/>
            <supportedRuntime version="v2.0.50727"/>
        </startup>
    </configuration>
    ```  
  
 Nell'esempio seguente vengono illustrate l'identificazione dei BLOB con lease attivi e la relativa interruzione. Nell'esempio viene anche descritto come applicare i filtri per gli ID lease di rilascio.  
  
 Suggerimenti per l'esecuzione di questo script  
  
> [!WARNING]  
>  Se un backup nel servizio di archiviazione BLOB di Azure è in esecuzione contemporaneamente a questo script, il backup può avere esito negativo perché questo script interrompe il lease che il backup sta tentando di acquisire nello stesso momento. È consigliabile eseguire questo script durante un periodo di manutenzione o quando non sono previste esecuzioni di backup.  
  
1.  Quando si esegue questo script, verrà richiesto di specificare i valori per l'account di archiviazione, la chiave di archiviazione, il contenitore e i parametri del percorso e del nome dell'assembly di archiviazione di Azure. Il percorso dell'assembly di archiviazione è la directory di installazione dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il nome del file per l'assembly di archiviazione è Microsoft.WindowsAzure.Storage.dll. Di seguito è riportato un esempio delle richieste e dei valori immessi:  
  
    ```  
    cmdlet  at command pipeline position 1  
    Supply values for the following parameters:  
    storageAccount: mycloudstorageaccount  
    storageKey: 0BopKY7eEha3gBnistYk+904nf  
    blobContainer: mycontainer   
    storageAssemblyPath: C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Microsoft.WindowsAzure.Storage.dll  
    ```  
  
2.  Se non è presente alcun BLOB con lease bloccati, dovrebbe essere visualizzato il messaggio seguente:  
  
     **Nessun BLOB con stato lease bloccato**  
  
     Se sono presenti BLOB con lease bloccati, dovrebbero essere visualizzati i messaggi seguenti:  
  
     **Interruzione lease**  
  
     **Il lease nell'\<URL del BLOB> è un lease di ripristino: questo messaggio verrà visualizzato solo se è presente un BLOB con un lease di ripristino ancora attivo.**  
  
     **Il lease nell'\<URL del BLOB> non è un lease di ripristino. Interruzione lease nell'\<URL del BOB>.**  
  
```powershell
param(  
       [Parameter(Mandatory=$true)]  
       [string]$storageAccount,  
       [Parameter(Mandatory=$true)]  
       [string]$storageKey,  
       [Parameter(Mandatory=$true)]  
       [string]$blobContainer,  
       [Parameter(Mandatory=$true)]  
       [string]$storageAssemblyPath  
)  
  
# Well known Restore Lease ID  
$restoreLeaseId = "BAC2BAC2BAC2BAC2BAC2BAC2BAC2BAC2"  
  
# Load the storage assembly without locking the file for the duration of the PowerShell session  
$bytes = [System.IO.File]::ReadAllBytes($storageAssemblyPath)  
[System.Reflection.Assembly]::Load($bytes)  
  
$cred = New-Object 'Microsoft.WindowsAzure.Storage.Auth.StorageCredentials' $storageAccount, $storageKey  
$client = New-Object 'Microsoft.WindowsAzure.Storage.Blob.CloudBlobClient' "https://$storageAccount.blob.core.windows.net", $cred  
$container = $client.GetContainerReference($blobContainer)  
  
#list all the blobs  
$allBlobs = $container.ListBlobs()
  
$lockedBlobs = @()  
# filter blobs that are have Lease Status as "locked"  
foreach($blob in $allBlobs)  
{  
    $blobProperties = $blob.Properties
    if($blobProperties.LeaseStatus -eq "Locked")  
    {  
        $lockedBlobs += $blob  
    }  
}  
  
if ($lockedBlobs.Count -eq 0)  
{
    Write-Host " There are no blobs with locked lease status"  
}

if($lockedBlobs.Count -gt 0)  
{  
    Write-Host "Breaking leases"  
    foreach($blob in $lockedBlobs )
    {  
        try  
        {  
            $blob.AcquireLease($null, $restoreLeaseId, $null, $null, $null)  
            Write-Host "The lease on $($blob.Uri) is a restore lease"  
        }  
        catch [Microsoft.WindowsAzure.Storage.StorageException]  
        {  
            if($_.Exception.RequestInformation.HttpStatusCode -eq 409)  
            {  
                Write-Host "The lease on $($blob.Uri) is not a restore lease"  
            }  
        }  
  
        Write-Host "Breaking lease on $($blob.Uri)"  
        $blob.BreakLease($(New-TimeSpan), $null, $null, $null) | Out-Null  
    }  
}
```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure consigliate e risoluzione dei problemi per il backup di SQL Server nell'URL](sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
