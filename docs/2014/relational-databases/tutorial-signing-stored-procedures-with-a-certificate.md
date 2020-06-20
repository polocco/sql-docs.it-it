---
title: 'Esercitazione: Firma di stored procedure con un certificato | Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- signing stored procedures tutorial [SQL Server]
ms.assetid: a4b0f23b-bdc8-425f-b0b9-e0621894f47e
author: rothja
ms.author: jroth
ms.openlocfilehash: 6fe387c43431436ba5fba5bcab879584ecdad533
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85002507"
---
# <a name="tutorial-signing-stored-procedures-with-a-certificate"></a>Esercitazione: Firma di stored procedure tramite un certificato
  In questa esercitazione viene illustrata la firma di stored procedure tramite un certificato generato da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Per eseguire il codice dell'esercitazione deve essere configurata la sicurezza a modalità mista e deve essere installato il database [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] . Scenario  
  
 La firma di stored procedure tramite un certificato si rivela utile quando si desidera richiedere autorizzazioni per la stored procedure ma non concedere esplicitamente tali diritti all'utente. Nonostante sia possibile completare questa attività in altri modi, ad esempio mediante l'istruzione EXECUTE AS, l'utilizzo di un certificato consente di disporre di una traccia per individuare il chiamante originale della stored procedure. Ciò offre un elevato livello di controllo, in particolare durante operazioni DDL (Data Definition Language) o di sicurezza.  
  
 È possibile creare un certificato nel database master per concedere autorizzazioni a livello di server oppure in qualsiasi database utente per concedere autorizzazioni a livello di database. In questo scenario, un utente che non dispone di diritti per le tabelle di base deve accedere a una stored procedure nel database [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] e si desidera controllare l'itinerario di accesso agli oggetti. Anziché utilizzare altri metodi delle catene di proprietà, verranno creati un account utente del server e del database senza alcun diritto per gli oggetti di base e un account utente del database con diritti per una tabella e una stored procedure. Sia la stored procedure che il secondo account utente del database verranno protetti con un certificato. Il secondo account del database disporrà dell'accesso a tutti gli oggetti e concederà l'accesso alla stored procedure al primo account utente del database.  
  
 In questo scenario, verranno innanzitutto creati un certificato del database, una stored procedure e un utente e quindi verrà testato il processo eseguendo la procedura seguente:  
  
1.  Configurare l'ambiente.  
  
2.  Creare un certificato.  
  
3.  Creare e firmare una stored procedure utilizzando il certificato.  
  
4.  Creare un account del certificato utilizzando il certificato.  
  
5.  Concedere i diritti per il database dell'account del certificato.  
  
6.  Visualizzare il contesto di accesso.  
  
7.  Reimpostare l'ambiente.  
  
 Ogni blocco di codice dell'esempio è illustrato sulla stessa riga. Per copiare l'esempio completo, vedere [Esempio completo](#CompleteExample) alla fine dell'esercitazione.  
  
## <a name="1-configure-the-environment"></a>1. Configurazione dell'ambiente  
 Per impostare il contesto iniziale dell'esempio, in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] aprire una nuova query ed eseguire il codice seguente per aprire il database [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] . Con questo codice, il contesto di database viene modificato in `AdventureWorks2012` e viene creato un nuovo account di accesso al server e utente del database (`TestCreditRatingUser`) con una password.  
  
```  
USE AdventureWorks2012;  
GO  
-- Set up a login for the test user  
CREATE LOGIN TestCreditRatingUser  
   WITH PASSWORD = 'ASDECd2439587y'  
GO  
CREATE USER TestCreditRatingUser  
FOR LOGIN TestCreditRatingUser;  
GO  
```  
  
 Per altre informazioni sull'istruzione CREATE USER, vedere [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql). Per altre informazioni sull'istruzione CREATE LOGIN, vedere [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).  
  
## <a name="2-create-a-certificate"></a>2. Creazione di un certificato  
 È possibile creare certificati nel server utilizzando il database master come contesto, un database utente o entrambi. Per la sicurezza del certificato sono disponibili più opzioni. Per altre informazioni sui certificati, vedere [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql).  
  
 Eseguire questo codice per creare un certificato del database e proteggerlo tramite una password.  
  
```  
CREATE CERTIFICATE TestCreditRatingCer  
   ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
      WITH SUBJECT = 'Credit Rating Records Access',   
      EXPIRY_DATE = '12/05/2014';  
GO  
```  
  
## <a name="3-create-and-sign-a-stored-procedure-using-the-certificate"></a>3. Creazione e firma di una stored procedure utilizzando il certificato  
 Utilizzare il codice seguente per creare una stored procedure che selezioni i dati dalla tabella `Vendor` nello schema di database `Purchasing` , limitando l'accesso alle sole aziende con posizione creditizia 1. Si noti che nella prima sezione della stored procedure viene visualizzato il contesto dell'account utente che esegue la stored procedure, al solo scopo di dimostrare i concetti. Non è necessario per soddisfare i requisiti.  
  
```  
CREATE PROCEDURE TestCreditRatingSP  
AS  
BEGIN  
   -- Show who is running the stored procedure  
   SELECT SYSTEM_USER 'system Login'  
   , USER AS 'Database Login'  
   , NAME AS 'Context'  
   , TYPE  
   , USAGE   
   FROM sys.user_token     
  
   -- Now get the data  
   SELECT AccountNumber, Name, CreditRating   
   FROM Purchasing.Vendor  
   WHERE CreditRating = 1  
END  
GO  
```  
  
 Eseguire questo codice per firmare la stored procedure con il certificato del database, utilizzando una password.  
  
```  
ADD SIGNATURE TO TestCreditRatingSP   
   BY CERTIFICATE TestCreditRatingCer  
    WITH PASSWORD = 'pGFD4bb925DGvbd2439587y';  
GO  
```  
  
 Per altre informazioni sulle stored procedure, vedere [Stored procedure &#40;motore di database&#41;](stored-procedures/stored-procedures-database-engine.md).  
  
 Per altre informazioni sulla firma di stored procedure, vedere [ADD SIGNATURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/add-signature-transact-sql).  
  
## <a name="4-create-a-certificate-account-using-the-certificate"></a>4. Creazione di un account del certificato utilizzando il certificato  
 Eseguire questo codice per creare un utente del database (`TestCreditRatingcertificateAccount`) dal certificato. Tale account non dispone di accesso server e controllerà l'accesso alle tabelle sottostanti.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE USER TestCreditRatingcertificateAccount  
   FROM CERTIFICATE TestCreditRatingCer;  
GO  
```  
  
## <a name="5-grant-the-certificate-account-database-rights"></a>5. Concessione dei diritti per il database dell'account del certificato  
 Eseguire questo codice per concedere a `TestCreditRatingcertificateAccount` diritti per la tabella di base e la stored procedure.  
  
```  
GRANT SELECT   
   ON Purchasing.Vendor   
   TO TestCreditRatingcertificateAccount;  
GO  
  
GRANT EXECUTE   
   ON TestCreditRatingSP   
   TO TestCreditRatingcertificateAccount;  
GO  
```  
  
 Per altre informazioni sulla concessione di autorizzazioni per gli oggetti, vedere [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).  
  
## <a name="6-display-the-access-context"></a>6. Visualizzazione del contesto di accesso  
 Per visualizzare i diritti associati all'accesso alla stored procedure, eseguire il codice seguente per concedere i diritti per l'esecuzione della stored procedure all'utente `TestCreditRatingUser` .  
  
```  
GRANT EXECUTE   
   ON TestCreditRatingSP   
   TO TestCreditRatingUser;  
GO  
```  
  
 Eseguire quindi il codice seguente per eseguire la stored procedure con l'account di accesso dbo utilizzato nel server. Osservare l'output delle informazioni sul contesto utente. L'account dbo verrà riportato come contesto con diritti propri e non tramite l'appartenenza a un gruppo.  
  
```  
EXECUTE TestCreditRatingSP;  
GO  
```  
  
 Eseguire il codice seguente per utilizzare l'istruzione `EXECUTE AS` per eseguire la stored procedure tramite l'account `TestCreditRatingUser` In questo caso, il contesto utente sarà impostato sul contesto USER MAPPED TO CERTIFICATE.  
  
```  
EXECUTE AS LOGIN = 'TestCreditRatingUser';  
GO  
EXECUTE TestCreditRatingSP;  
GO  
```  
  
 Ciò illustra il livello di controllo disponibile grazie alla firma della stored procedure.  
  
> [!NOTE]  
>  Usare EXECUTE AS per cambiare contesto all'interno di un database.  
  
## <a name="7-reset-the-environment"></a>7. Reimpostazione dell'ambiente  
 Nel codice seguente viene utilizzata l'istruzione `REVERT` per ripristinare dbo come contesto dell'account corrente e quindi viene reimpostato l'ambiente.  
  
```  
REVERT;  
GO  
DROP PROCEDURE TestCreditRatingSP;  
GO  
DROP USER TestCreditRatingcertificateAccount;  
GO  
DROP USER TestCreditRatingUser;  
GO  
DROP LOGIN TestCreditRatingUser;  
GO  
DROP CERTIFICATE TestCreditRatingCer;  
GO  
```  
  
 Per altre informazioni sull'istruzione REVERT, vedere [REVERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/revert-transact-sql).  
  
##  <a name="complete-example"></a><a name="CompleteExample"></a>Esempio completo  
 In questa sezione è riportato il codice completo dell'esempio.  
  
```  
/* Step 1 - Open the AdventureWorks2012 database */  
USE AdventureWorks2012;  
GO  
-- Set up a login for the test user  
CREATE LOGIN TestCreditRatingUser  
   WITH PASSWORD = 'ASDECd2439587y'  
GO  
CREATE USER TestCreditRatingUser  
FOR LOGIN TestCreditRatingUser;  
GO  
  
/* Step 2 - Create a certificate in the AdventureWorks2012 database */  
CREATE CERTIFICATE TestCreditRatingCer  
   ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
      WITH SUBJECT = 'Credit Rating Records Access',   
      EXPIRY_DATE = '12/05/2014';  
GO  
  
/* Step 3 - Create a stored procedure and  
sign it using the certificate */  
CREATE PROCEDURE TestCreditRatingSP  
AS  
BEGIN  
   -- Shows who is running the stored procedure  
   SELECT SYSTEM_USER 'system Login'  
   , USER AS 'Database Login'  
   , NAME AS 'Context'  
   , TYPE  
   , USAGE   
   FROM sys.user_token;     
  
   -- Now get the data  
   SELECT AccountNumber, Name, CreditRating   
   FROM Purchasing.Vendor  
   WHERE CreditRating = 1;  
END  
GO  
  
ADD SIGNATURE TO TestCreditRatingSP   
   BY CERTIFICATE TestCreditRatingCer  
    WITH PASSWORD = 'pGFD4bb925DGvbd2439587y';  
GO  
  
/* Step 4 - Create a database user for the certificate.   
This user has the ownership chain associated with it. */  
USE AdventureWorks2012;  
GO  
CREATE USER TestCreditRatingcertificateAccount  
   FROM CERTIFICATE TestCreditRatingCer;  
GO  
  
/* Step 5 - Grant the user database rights */  
GRANT SELECT   
   ON Purchasing.Vendor   
   TO TestCreditRatingcertificateAccount;  
GO  
  
GRANT EXECUTE  
   ON TestCreditRatingSP   
   TO TestCreditRatingcertificateAccount;  
GO  
  
/* Step 6 - Test, using the EXECUTE AS statement */  
GRANT EXECUTE   
   ON TestCreditRatingSP   
   TO TestCreditRatingUser;  
GO  
  
-- Run the procedure as the dbo user, notice the output for the type  
EXEC TestCreditRatingSP;  
GO  
  
EXECUTE AS LOGIN = 'TestCreditRatingUser';  
GO  
EXEC TestCreditRatingSP;  
GO  
  
/* Step 7 - Clean up the example */  
REVERT;  
GO  
DROP PROCEDURE TestCreditRatingSP;  
GO  
DROP USER TestCreditRatingcertificateAccount;  
GO  
DROP USER TestCreditRatingUser;  
GO  
DROP LOGIN TestCreditRatingUser;  
GO  
DROP CERTIFICATE TestCreditRatingCer;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Centro sicurezza per il motore di Database di SQL Server e il Database SQL di Azure](security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
  
