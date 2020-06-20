---
title: MSSQLSERVER_1418 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1418 (Database Engine error)
ms.assetid: 6e9c7241-0201-44e0-9f8b-b3c4e293f0f6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1fcac03f044aacce5e907824862eb589c97a07d2
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967961"
---
# <a name="mssqlserver_1418"></a>MSSQLSERVER_1418
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|1418|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBM_PARTNERNOTFOUND|  
|Testo del messaggio|L'indirizzo di rete del server "%.*ls" non è raggiungibile o non esiste. Controllare il nome dell'indirizzo di rete e verificare che le porte degli endpoint locale e remoto siano operative.|  
  
## <a name="explanation"></a>Spiegazione  
 L'endpoint di rete del server non ha risposto perché l'indirizzo di rete del server specificato non è raggiungibile o non esiste.  
  
> [!NOTE]  
>  Per impostazione predefinita, tutte le porte vengono bloccate dal sistema operativo [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
## <a name="user-action"></a>Azione dell'utente  
 Verificare il nome dell'indirizzo di rete ed eseguire nuovamente il comando.  
  
 È possibile che sia necessario intervenire su entrambi i partner. Se ad esempio questo messaggio viene generato mentre si sta tentando di eseguire l'istruzione SET PARTNER nell'istanza del server principale, il messaggio potrebbe implicare che è necessario intervenire solo nell'istanza del server mirror. È possibile tuttavia che l'intervento sia richiesto su entrambi i partner.  
  
### <a name="additional-corrective-actions"></a>Interventi di correzione aggiuntivi  
  
-   Verificare che il database mirror sia pronto per il mirroring.  
  
-   Verificare che il nome e la porta dell'istanza del server mirror siano corretti.  
  
-   Verificare che l'istanza del server mirror di destinazione non sia protetta da un firewall.  
  
-   Verificare che l'istanza del server principale non sia protetta da un firewall.  
  
-   Verificare che gli endpoint siano stati avviati sui partner usando la colonna **state** o **state_desc** della vista del catalogo **sys.database_mirroring_endpoints**. Se uno degli endpoint non è stato avviato, eseguire un'istruzione ALTER ENDPOINT per avviarlo.  
  
-   Verificare che l'istanza del server principale sia in attesa sulla porta assegnata al relativo endpoint del mirroring del database e che l'istanza del server mirror sia in attesa sulla relativa porta. Per ulteriori informazioni, vedere "Verifica della disponibilità delle porte" di seguito in questo argomento. Se il partner non è in attesa sulla porta assegnata, modificare l'impostazione dell'endpoint del mirroring del database affinché sia in attesa su una porta diversa.  
  
    > [!IMPORTANT]  
    >  Impostazioni di sicurezza configurate in modo non corretto possono generare un messaggio di errore generico relativo all'impostazione. L'istanza del server rimuove in genere la richiesta di connessione non valida senza alcuna risposta. Le cause di un errore di configurazione o sicurezza, dal punto di vista del chiamante, possono essere molteplici, ad esempio un database mirror inesistente o in uno stato non valido, autorizzazioni non corrette e così via.  
  
### <a name="using-the-error-log-file-for-diagnosis"></a>Utilizzo del file del log degli errori per la diagnosi  
 In alcuni casi, per eseguire analisi approfondite sono disponibili solo i file del log degli errori. In tali circostanze, verificare se il log degli errori contiene il messaggio di errore 26023 per la porta TCP dell'endpoint del mirroring del database. Questo errore, con livello di gravità 16, può indicare che l'endpoint del mirroring del database non è stato avviato. È possibile che il messaggio venga visualizzato anche se nella vista del catalogo **sys.database_mirroring_endpoints** l'endpoint risulta avviato.  
  
 Dopo aver risolto tutti i problemi riscontrati, eseguire nuovamente l'istruzione ALTER DATABASE *nome_database* SET PARTNER nel server principale.  
  
### <a name="verifying-port-availability"></a>Verifica della disponibilità delle porte  
 Quando si configura la rete per una sessione di mirroring del database, verificare che l'endpoint del mirroring del database di ogni istanza del server venga utilizzato solo dal processo di mirroring del database. Se un altro processo è in attesa sulla porta assegnata a un endpoint del mirroring del database, i processi di mirroring del database delle altre istanze del server non potranno stabilire una connessione all'endpoint.  
  
 Per visualizzare tutte le porte su cui è in attesa un server Windows, usare l'utilità della riga di comando **netstat**. La sintassi di **netstat** dipende dalla versione del sistema operativo Windows. Per ulteriori informazioni, consultare la documentazione del sistema operativo.  
  
#### <a name="windows-server-2003-service-pack-1-sp1"></a>Windows Server 2003 Service Pack 1 (SP1)  
 Per elencare le porte di attesa e i processi che mantengono aperte tali porte, digitare il comando seguente al prompt dei comandi di Windows:  
  
 **netstat -abn**  
  
#### <a name="windows-server-2003-pre-sp1"></a>Windows Server 2003 (versioni precedenti a SP1)  
 Per identificare le porte di attesa e i processi che mantengono aperte tali porte, eseguire la procedura seguente:  
  
1.  Ottenere l'ID del processo.  
  
     Per individuare l'ID del processo di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], connettersi a tale istanza e utilizzare l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente:  
  
    ```  
    SELECT SERVERPROPERTY('ProcessID')   
    ```  
  
     Per ulteriori informazioni, vedere "SERVERPROPERTY (Transact-SQL)" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Associare l'ID del processo all'output del comando **netstat** seguente:  
  
     **netstat -ano**  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)   
 [&#40;SQL Server dell'endpoint del mirroring del database&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Preparare un database mirror per il mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)   
 [Specificare un indirizzo di rete del server &#40;il mirroring del database&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md)   
 [sys. database_mirroring_endpoints &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)   
 [Risolvere i problemi relativi alla configurazione del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
