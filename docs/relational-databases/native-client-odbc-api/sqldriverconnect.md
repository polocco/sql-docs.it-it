---
title: Proprietà SQLDriverConnect . Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8d1455f0b91313ea137ec9c13a2d318fba0807b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302552"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client definisce attributi di connessione che sostituiscono o migliorano le parole chiave della stringa di connessione. Per diverse parole chiave della stringa di connessione sono disponibili valori predefiniti specificati dal driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 Per un elenco delle parole [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chiave disponibili nel driver ODBC Native Client, vedere Utilizzo di parole chiave della stringa di [connessione con SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Per ulteriori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informazioni sugli attributi di connessione e sui comportamenti predefiniti del driver, vedere [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 Per una descrizione delle parole chiave [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] della stringa di connessione valide per Native Client, vedere Utilizzo di parole chiave della stringa di [connessione con SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Quando il valore del parametro **SQLDriverConnect**_DriverCompletion_ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE o SQL_DRIVER_COMPLETE_REQUIRED, il driver ODBC Native Client recupera i valori delle parole chiave dalla finestra di dialogo visualizzata. Se il valore della parola chiave viene passato nella stringa di connessione e l'utente non modifica il valore per la parola chiave nella finestra di dialogo, il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client utilizza il valore dalla stringa di connessione. Se il valore non è impostato nella stringa di connessione e l'utente non esegue alcuna assegnazione nella finestra di dialogo, il driver utilizza il valore predefinito.  
  
 **SQLDriverConnect** deve essere assegnato un *oggetto WindowHandle* valido quando qualsiasi valore *DriverCompletion* richiede (o potrebbe richiedere) la visualizzazione della finestra di dialogo di connessione del driver. Un handle non valido restituisce SQL_ERROR.  
  
 Specificare la parola chiave DRIVER o DSN. ODBC dichiara che un driver utilizza la parola chiave più a sinistra tra le due e ignora l'altra se sono specificate entrambe. Se DRIVER viene specificato o è la più a sinistra dei due e il **sqlDriverConnect**_DriverCompletion_ valore del parametro è SQL_DRIVER_NOPROMPT, la parola chiave SERVER e un valore appropriato sono necessari.  
  
 Quando si specifica SQL_DRIVER_NOPROMPT, le parole chiave di autenticazione utente devono essere presenti con valori. Il driver garantisce la presenza della stringa "Trusted_Connection=yes" o delle parole chiave UID e PWD.  
  
 Se il *DriverCompletion* valore del parametro è SQL_DRIVER_NOPROMPT o SQL_DRIVER_COMPLETE_REQUIRED e il linguaggio o database proviene dalla stringa di connessione e uno dei contrari non è valido, **SQLDriverConnect** restituisce SQL_ERROR.  
  
 Se il valore del parametro *DriverCompletion* è SQL_DRIVER_NOPROMPT o SQL_DRIVER_COMPLETE_REQUIRED e la lingua o il database proviene dalle definizioni dell'origine dati ODBC e non è valido, **SQLDriverConnect** utilizza il linguaggio o il database predefinito per l'ID utente specificato e restituisce SQL_SUCCESS_WITH_INFO.  
  
 Se il valore del parametro *DriverCompletion* è SQL_DRIVER_COMPLETE o SQL_DRIVER_PROMPT e se la lingua o il database non è valido, **SQLDriverConnect** visualizza nuovamente la finestra di dialogo.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>Supporto di SQLDriverConnect per il ripristino di emergenza a disponibilità elevata  
 Per altre informazioni sull'uso di [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] **SQLDriverConnect** per connettersi a un cluster, vedere Supporto di SQL Server Native Client per la disponibilità elevata, il ripristino di [emergenza](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>Supporto di SQLDriverConnect per nomi SPN (Service Principal Name)  
 SQLDDriverConnect utilizzerà la finestra di dialogo di accesso ODBC quando la richiesta è abilitata. Ciò consente di immettere i nomi SPN per il server principale e per il relativo partner di failover.  
  
 SQLDriverConnect accetterà le nuove parole chiave della stringa di connessione **ServerSPN** e **FailoverPartnerSPN**e riconoscerà i nuovi attributi di connessione SQL_COPT_SS_SERVER_SPN e SQL_COPT_SS_FAILOVER_PARTNER_SPN.  
  
 Quando un attributo di connessione viene specificato più di una volta, un valore impostato a livello di programmazione ha la precedenza sul valore in un DSN e su un valore in una stringa di connessione. Un valore in un DSN ha la precedenza su un valore in una stringa di connessione.  
  
 Quando si apre una connessione, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client imposta SQL_COPT_SS_MUTUALLY_AUTHENTICATED e SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD sul metodo di autenticazione utilizzato per aprire la connessione.  
  
 Per ulteriori informazioni sui nomi SPN, vedere [Nomi delle entità servizio &#40;nomi &#40;NOMI SPN&#41; in Connessioni client &#40;&#41;ODBC ](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="examples"></a>Esempi  
 La chiamata seguente illustra la quantità minima di dati necessari per **SQLDriverConnect:**  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 Le stringhe di connessione seguenti illustrano i dati minimi richiesti quando il valore del parametro DriverCompletion è SQL_DRIVER_NOPROMPT:The following connection strings illustrate minimum required data when the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT:  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLDriverConnectSQLDriverConnect Function](https://go.microsoft.com/fwlink/?LinkId=59340)   
 [Dettagli di implementazione dell'API ODBCODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SET ANSI_NULLS &#40;transact-SQLTransact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING &#40;&#41;Transact-SQL](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
