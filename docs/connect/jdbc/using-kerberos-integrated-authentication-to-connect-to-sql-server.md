---
title: Uso dell'autenticazione integrata Kerberos per la connessione a SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4494931e0ee189e785ed057471e5560f4737ecc0
ms.sourcegitcommit: 37a3e2c022c578fc3a54ebee66d9957ff7476922
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2020
ms.locfileid: "82922316"
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Uso dell'autenticazione integrata Kerberos per la connessione a SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

A partire da [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], per un'applicazione è possibile usare la proprietà di connessione **authenticationScheme** per specificare una connessione a un database tramite l'autenticazione integrata Kerberos di tipo 4. Per altre informazioni sulle proprietà delle connessioni, vedere [Impostazione delle proprietà delle connessioni](../../connect/jdbc/setting-the-connection-properties.md). Per altre informazioni su Kerberos, vedere [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkID=100758).

Quando si usa l'autenticazione integrata con il modulo Java **Krb5LoginModule**, è possibile configurare il modulo usando la [classe Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] imposta le proprietà seguenti per ambienti Java Virtual Machine IBM:

- **useDefaultCcache = true**
- **moduleBanner = false**

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] imposta le proprietà seguenti per tutti gli altri ambienti Java Virtual Machine:

- **useTicketCache = true**
- **doNotPrompt = true**

## <a name="remarks"></a>Osservazioni

Nelle versioni precedenti a [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], per le applicazioni è possibile specificare l'autenticazione integrata (tramite Kerberos o NTLM, a seconda dell'autenticazione disponibile) usando la proprietà di connessione **integratedSecurity** e facendo riferimento a **mssql-jdbc_auth-\<versione>-\<arch>.dll**, come descritto in [Compilazione dell'URL della connessione](../../connect/jdbc/building-the-connection-url.md).

A partire da [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], per un'applicazione è possibile usare la proprietà di connessione **authenticationScheme** per specificare una connessione a un database tramite l'autenticazione integrata Kerberos e l'implementazione Kerberos Java pura:

- Se si vuole usare l'autenticazione integrata con **Krb5LoginModule**, è comunque necessario specificare la proprietà di connessione **integratedSecurity=true**. Sarà quindi necessario specificare anche la proprietà di connessione **authenticationScheme=JavaKerberos**.

- Per continuare a usare l'autenticazione integrata con **mssql-jdbc_auth-\<versione>-\<arch>.dll**, è sufficiente specificare la proprietà di connessione **integratedSecurity=true** e, facoltativamente, **authenticationScheme=NativeAuthentication**.

- Se si specifica **authenticationScheme=JavaKerberos**, ma senza specificare anche **integratedSecurity=true**, la proprietà di connessione **authenticationScheme** verrà ignorata dal driver che cercherà le credenziali di nome utente e password nella stringa di connessione.

Quando si usa un'origine dati per creare connessioni, è possibile impostare a livello di codice lo schema di autenticazione usando **setAuthenticationScheme** e (facoltativamente) impostare il nome dell'entità servizio per le connessioni Kerberos usando **setServerSpn**.

È stato aggiunto un nuovo logger per supportare l'autenticazione Kerberos: com.microsoft.sqlserver.jdbc.internals.KerbAuthentication. Per altre informazioni, vedere [Creazione di tracce](../../connect/jdbc/tracing-driver-operation.md).

Le linee guida seguenti consentono di configurare Kerberos:

1. Impostare **AllowTgtSessionKey** su 1 nel Registro di sistema di Windows. Per altre informazioni, vedere [Voci del Registro di sistema del protocollo Kerberos e chiavi di configurazione KDC in Windows Server 2003](https://support.microsoft.com/kb/837361).
2. Assicurarsi che la configurazione di Kerberos (krb5.conf in ambienti UNIX) punti all'area di autenticazione e al servizio KDC corretti per l'ambiente.
3. Inizializzare la cache TGT tramite kinit o accedendo al dominio.
4. Quando un'applicazione in cui **authenticationScheme=JavaKerberos** viene eseguita nel sistema operativo Windows Vista o Windows 7, è consigliabile usare un account utente standard. Se tuttavia si usa un account amministratore, l'applicazione deve essere eseguita con privilegi di amministratore.

> [!NOTE]  
> L'attributo di connessione serverSpn è supportato solo da Microsoft JDBC Driver 4.2 e versioni successive.

## <a name="service-principal-names"></a>Nomi dell'entità servizio

Un nome dell'entità servizio (SPN) è il nome con cui un client identifica in modo univoco un'istanza di un servizio.

È possibile specificare il nome dell'entità servizio usando la proprietà di connessione **serverSpn** o lasciare che sia il driver a crearlo automaticamente (impostazione predefinita). Il formato della proprietà è: "MSSQLSvc/fqdn:porta\@AREADIAUTENTICAZIONE" dove fqdn è il nome di dominio completo, porta è il numero di porta e AREADIAUTENTICAZIONE è l'area di autenticazione Kerberos di SQL Server in lettere maiuscole. La parte dell'area di autenticazione di questa proprietà è facoltativa se l'area di autenticazione predefinita della configurazione di Kerberos è la stessa area di autenticazione del server e non è inclusa per impostazione predefinita. Se si desidera supportare uno scenario di autenticazione tra diverse aree di autenticazione, in cui l'area di autenticazione predefinita nella configurazione di Kerberos è diversa dall'area di autenticazione del server, è necessario impostare il nome dell'entità servizio con la proprietà serverSpn.

Ad esempio, il nome dell'entità servizio potrebbe essere simile al seguente: "MSSQLSvc/some-server.zzz.corp.contoso.com:1433\@ZZZZ.CORP.CONTOSO.COM"

Per ulteriori informazioni sui nomi dell'entità servizio (SPN), vedere:

- [Utilizzo dell'autenticazione Kerberos in SQL Server](https://support.microsoft.com/kb/319723)

- [Utilizzo di Kerberos con SQL Server](https://docs.microsoft.com/archive/blogs/sql_protocols/using-kerberos-with-sql-server)

> [!NOTE]  
> Per le versioni precedenti alla 6.2 del driver JDBC, per un uso corretto di Kerberos tra diverse aree di autenticazione è necessario impostare **serverSpn** in modo esplicito.
>
> A partire dalla versione 6.2, il driver può compilare **serverSpn** per impostazione predefinita, anche quando Kerberos viene usato tra diverse aree di autenticazione. È comunque possibile usare **serverSpn** in modo esplicito.

## <a name="creating-a-login-module-configuration-file"></a>Creazione di un file di configurazione del modulo di accesso

È eventualmente possibile specificare un file di configurazione Kerberos. Se non si specifica un file di configurazione, vengono utilizzate le impostazioni seguenti:

JVM Sun  
 com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;

JVM IBM  
 com.ibm.security.auth.module.Krb5LoginModule required useDefaultCcache = true;

Se si sceglie di creare un file di configurazione del modulo di accesso, per il file è necessario utilizzare il formato seguente:

```java
<name> {  
    <LoginModule> <flag> <LoginModule options>;  
    <optional_additional_LoginModules, flags_and_options>;  
};  
```

Un file di configurazione di accesso è costituito da una o più voci, ciascuna indicante la tecnologia di autenticazione sottostante da utilizzare per un'applicazione o più applicazioni specifiche. Ad esempio,

```java
SQLJDBCDriver {  
   com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;  
};  
```

Di conseguenza, ogni voce del file di configurazione del modulo di accesso è costituita da un nome seguito da una o più voci specifiche di LoginModule, in cui ogni voce termina con un punto e virgola e l'intero gruppo di voci è racchiuso tra parentesi graffe. Ogni voce del file di configurazione termina con un punto e virgola.

Oltre a consentire al driver di acquisire credenziali Kerberos tramite le impostazioni specificate nel file di configurazione del modulo di accesso, il driver può utilizzare credenziali esistenti. Questo comportamento può risultare utile quando l'applicazione deve creare connessioni con credenziali di più utenti.

Tramite il driver verrà effettuato il tentativo di utilizzare credenziali esistenti, se disponibili, prima di accedere utilizzando il modulo di accesso specificato. Di conseguenza, quando si usa il metodo `Subject.doAs` per l'esecuzione di codice in un contesto specifico viene creata una connessione con le credenziali passate alla chiamata di `Subject.doAs`.

Per altre informazioni, vedere le pagine Web relative al [file di configurazione di accesso JAAS](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html) e alla [classe Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

A partire da Microsoft JDBC Driver 6.2, il nome del file di configurazione del modulo di accesso può facoltativamente essere passato usando la proprietà di connessione `jaasConfigurationName`, in modo che ogni connessione abbia una propria configurazione di accesso.

## <a name="creating-a-kerberos-configuration-file"></a>Creazione di un file di configurazione Kerberos

Per altre informazioni sui file di configurazione Kerberos, vedere la pagina Web relativa ai [requisiti per Kerberos](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html).

L'esempio seguente visualizza un file di configurazione del dominio, in cui YYYY e ZZZZ sono i nomi di dominio.

```ini
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  

[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  

[realms]  
        YYYY.CORP.CONTOSO.COM = {  
  kdc = krbtgt/YYYY.CORP. CONTOSO.COM @ YYYY.CORP. CONTOSO.COM  
  default_domain = YYYY.CORP. CONTOSO.COM  
}  

        ZZZZ.CORP. CONTOSO.COM = {  
  kdc = krbtgt/ZZZZ.CORP. CONTOSO.COM @ ZZZZ.CORP. CONTOSO.COM  
  default_domain = ZZZZ.CORP. CONTOSO.COM  
}  

```

## <a name="enabling-the-domain-configuration-file-and-the-login-module-configuration-file"></a>Abilitazione del file di configurazione del dominio e del file di configurazione del modulo di accesso

È possibile abilitare un file di configurazione del dominio con -Djava.security.krb5.conf. È possibile abilitare un file di configurazione del modulo di accesso con **-Djava.security.auth.login.config**.

Ad esempio, è possibile usare il comando seguente per avviare l'applicazione:

```bash
Java.exe -Djava.security.auth.login.config=SQLJDBCDriver.conf -Djava.security.krb5.conf=krb5.ini <APPLICATION_NAME>  

```

## <a name="verifying-that-sql-server-can-be-accessed-via-kerberos"></a>Verifica dell'accesso a SQL Server tramite Kerberos

Eseguire la query seguente in SQL Server Management Studio:

```sql
select auth_scheme from sys.dm_exec_connections where session_id=\@\@spid
```

Assicurarsi di disporre dell'autorizzazione necessaria per l'esecuzione della query.

## <a name="constrained-delegation"></a>Delega vincolata

A partire da Microsoft JDBC Driver 6.2, il driver supporta la delega vincolata Kerberos. Le credenziali delegate possono essere passate come oggetto org.ietf.jgss.GSSCredential e usate dal driver per stabilire la connessione.

```java
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>Connessione Kerberos con nomi di entità utente e password

A partire da Microsoft JDBC Driver 6.2, il driver può stabilire una connessione Kerberos usando il nome dell'entità utente e la password passati nella stringa di connessione.

```java
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```

La proprietà nome utente non richiede l'area di autenticazione se l'utente appartiene a default_realm impostato nel file krb5.conf. Quando `userName` e `password` vengono impostati insieme alle proprietà `integratedSecurity=true;` e `authenticationScheme=JavaKerberos;`, la connessione viene stabilita con il valore nome utente come entità Kerberos insieme alla password specificata.

## <a name="using-kerberos-authentication-from-unix-machines-on-the-same-domain"></a>Uso dell'autenticazione Kerberos da computer UNIX nello stesso dominio

In questa guida si presuppone che esista già una configurazione Kerberos funzionante. Eseguire il codice seguente in un computer Windows con autenticazione Kerberos funzionante per verificare quanto illustrato in precedenza. Il codice produrrà "Schema di autenticazione: KERBEROS "nella console, se l'operazione ha esito positivo. Non sono necessari flag di esecuzione, dipendenze o impostazioni del driver aggiuntivi al di fuori di quelli specificati. Lo stesso blocco di codice può essere eseguito in Linux per verificare le connessioni riuscite.

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(1433); // change if necessary
ds.setIntegratedSecurity(true);
ds.setAuthenticationScheme("JavaKerberos");
ds.setDatabaseName("<database>");

try (Connection c = ds.getConnection(); Statement s = c.createStatement();
        ResultSet rs = s.executeQuery("select auth_scheme from sys.dm_exec_connections where session_id=@@spid")) {
    while (rs.next()) {
        System.out.println("Authentication Scheme: " + rs.getString(1));
    }
}
```

1. Aggiungere il computer client allo stesso dominio del server.
2. Impostare facoltativamente il percorso predefinito del ticket Kerberos. Questa operazione viene eseguita più facilmente impostando la variabile di ambiente `KRB5CCNAME`.
3. Ottenere il ticket Kerberos, generandone uno nuovo o inserendone uno esistente nel percorso predefinito del ticket Kerberos. Per generare un ticket, è sufficiente usare un terminale e inizializzare il ticket tramite `kinit USER@DOMAIN.AD` dove "USER" e "DOMAIN.AD "sono rispettivamente l'entità utente e il dominio. Ad esempio: `kinit SQL_SERVER_USER03@MICROSOFT.COM`. Il ticket verrà generato nel percorso predefinito del ticket o nel percorso di `KRB5CCNAME`, se impostato.
4. Immettere la password richiesta dal terminale.
5. Verificare le credenziali nel ticket tramite `klist` e verificare che le credenziali siano quelle che si intende usare per l'autenticazione.
6. Eseguire il codice di esempio precedente e verificare che l'autenticazione Kerberos sia stata completata correttamente.

## <a name="see-also"></a>Vedere anche

[Connessione a SQL Server con il driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
