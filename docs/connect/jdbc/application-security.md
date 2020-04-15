---
title: Sicurezza dell'applicazione | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 940879b4-aa0f-41ce-a369-6cfc0e78e01d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2f7d9c9a1610b5ebcd086bec1cc11d0ec85f7358
ms.sourcegitcommit: 54cfeb36c9caa51ec68fa8f4a1918e305db5e00a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219440"
---
# <a name="application-security"></a>Sicurezza dell'applicazione
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si usa [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], è importante adottare tutte le misure necessarie per garantire la sicurezza delle applicazioni. Nelle sezioni seguenti vengono fornite informazioni relative alle procedure da implementare a questo scopo.  
  
## <a name="using-java-policy-permissions"></a>Uso di autorizzazioni basate sui criteri Java  
 Quando si usa [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], è importante specificare le autorizzazioni basate sui criteri Java necessarie richieste dal driver JDBC. Java Runtime Environment (JRE) offre un modello di sicurezza completo utilizzabile in fase di esecuzione per determinare se un thread dispone dei diritti di accesso a una risorsa. L'accesso può essere gestito grazie ai file dei criteri di sicurezza, i quali, a loro volta, sono gestiti dal distributore e dal ruolo sysadmin del contenitore. Le autorizzazioni elencate in questo argomento sono quelle che influiscono sul driver JDBC.  
  
 Di seguito è riportato un esempio di autorizzazione tipica disponibile nel file dei criteri:  
  
```  
// Example policy file entry.  
grant [signedBy <signer>,] [codeBase <code source>] {  
   permission  <class>  [<name> [, <action list>]];  
};  
```  
  
 La base di codice seguente deve essere limitata alla base del codice del driver JDBC in modo da concedere il livello minore possibile di privilegi.  
  
```  
grant codeBase "file:/install_dir/lib/-" {  
  
// Grant access to data source.  
permission java.util.PropertyPermission "java.naming.*", "read,write";  
  
// Specify which hosts can be connected to.  
permission java.net.socketPermission "host:port", "connect";  
  
// Logger permission to take advantage of logging.  
permission java.util.logging.LoggingPermission;  
  
// Grant listen/connect/accept permissions to the driver if   
// connecting to a named instance as the client driver.   
// This connects to a udp service and listens for a response.  
permission java.net.SocketPermission "*", "listen, connect, accept";   
};   
```  
  
> [!NOTE]  
>  Il codice "file:/install_dir/lib/-" fa riferimento alla directory di installazione del driver JDBC.  
  
## <a name="protecting-server-communication"></a>Protezione delle comunicazioni con il server  
 Quando si usa il driver JDBC per comunicare con un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile proteggere il canale di comunicazione usando il protocollo IPSec (Internet Protocol Security) o Transport Layer Security (TLS), noto in precedenza come SSL (Secure Sockets Layer), oppure entrambi.  
  
 Il supporto di TLS può essere usato per fornire un livello aggiuntivo di protezione oltre a IPSec. Per altre informazioni sull'uso di TLS, vedere [Uso della crittografia](../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione delle applicazioni del driver JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
