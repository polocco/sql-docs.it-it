---
title: Entità (motore di database) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.roleproperties.selectroll.f1
- sql12.swb.databaseuser.permissions.user.f1--May use common.permissions
helpviewer_keywords:
- certificates [SQL Server], principals
- roles [SQL Server], principals
- permissions [SQL Server], principals
- '##MS_SQLAuthenticatorCertificate##'
- principals [SQL Server]
- '##MS_SQLResourceSigningCertificate##'
- groups [SQL Server], principals
- '##MS_AgentSigningCertificate##'
- authentication [SQL Server], principals
- schemas [SQL Server], principals
- principals [SQL Server], about principals
- security [SQL Server], principals
- users [SQL Server], principals
- '##MS_SQLReplicationSigningCertificate##'
ms.assetid: 3f7adbf7-6e40-4396-a8ca-71cbb843b5c2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 808c8516b3ed9e95ea4c724736461cb00923a7fb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85016243"
---
# <a name="principals-database-engine"></a>Entità (Motore di database)
  Le*entità* possono richiedere risorse di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Analogamente ad altri componenti del modello di autorizzazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , le entità possono essere organizzate in una gerarchia. Il campo di influenza di un'entità dipende dall'ambito della definizione dell'entità (Windows, server o database) e dal tipo di entità (indivisibile o raccolta). Un account di accesso di Windows è un esempio di entità indivisibile mentre un gruppo di Windows è un esempio di entità costituita da una raccolta. Ogni entità dispone di un ID di sicurezza (SID).  
  
 **Entità a livello di Windows**  
  
-   Account di dominio di Windows  
  
-   Account di accesso locale di Windows  
  
 **SQL Server** - **level** **entità** di livello  
  
-   Account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
  
-   Ruolo server  
  
 **Entità a livello di database**  
  
-   Utente di database  
  
-   Ruolo del database  
  
-   Ruolo applicazione  
  
## <a name="the-sql-server-sa-login"></a>Account di accesso sa di SQL Server  
 L'account di accesso sa di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è un'entità a livello di server. Per impostazione predefinita, questo account viene creato durante l'installazione di un'istanza. A partire da [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], il database predefinito di sa è il database master. diversamente da quanto consentito nelle versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="public-database-role"></a>Ruolo di database public  
 Ogni utente di database appartiene al ruolo di database public. Quando a un utente non sono state concesse o negate autorizzazioni specifiche per un'entità a protezione diretta, l'utente eredita le autorizzazioni concesse al ruolo public su tale entità a protezione diretta.  
  
## <a name="information_schema-and-sys"></a>INFORMATION_SCHEMA e sys  
 Ogni database comprende due entità che appaiono come utenti in viste di catalogo: INFORMATION_SCHEMA e sys. Queste entità sono richieste da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], e non posso essere modificate o eliminate.  
  
## <a name="certificate-based-sql-server-logins"></a>Account di accesso basati su certificati di SQL Server  
 Le entità del server i cui nomi sono racchiusi tra due simboli di cancelletto (##) sono solo per uso interno di sistema. Al momento dell'installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono create le seguenti entità che non devono essere eliminate.  
  
-   \##MS_SQLResourceSigningCertificate##  
  
-   \##MS_SQLReplicationSigningCertificate##  
  
-   \##MS_SQLAuthenticatorCertificate##  
  
-   \##MS_AgentSigningCertificate##  
  
-   \##MS_PolicyEventProcessingLogin##  
  
-   \##MS_PolicySigningCertificate##  
  
-   \##MS_PolicyTsqlExecutionLogin##  
  
## <a name="the-guest-user"></a>L'utente Guest  
 Ogni database include un **guest**. Le autorizzazioni garantite all'utente **guest** sono ereditate dagli utenti che hanno accesso al database ma non dispongono di un account utente nel database. Non è possibile eliminare l'utente **Guest** , ma è possibile disabilitarlo revocando l' `CONNECT` autorizzazione. `CONNECT`È possibile revocare l'autorizzazione eseguendo `REVOKE CONNECT FROM GUEST` all'interno di qualsiasi database diverso da master o tempdb.  
  
## <a name="client-and-database-server"></a>Client e server di database  
 Per definizione, un client e un server di database sono entità di sicurezza e possono essere protetti. È possibile autenticare queste entità mutuamente prima che sia stabilita una connessione di rete sicura. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]supporta il protocollo di autenticazione [Kerberos](https://go.microsoft.com/fwlink/?LinkId=100758) , che definisce il modo in cui i client interagiscono con un servizio di autenticazione di rete.  
  
## <a name="related-tasks"></a>Attività correlate  
 In questa sezione della documentazione online di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , sono inclusi i seguenti argomenti:  
  
-   [Procedure per la gestione di account di accesso, utenti e schemi](managing-logins-users-and-schemas-how-to-topics.md)  
  
-   [Ruoli a livello di server](server-level-roles.md)  
  
-   [Ruoli a livello di database](database-level-roles.md)  
  
-   [Ruoli applicazione](application-roles.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza di SQL Server](../securing-sql-server.md)   
 [sys. database_principals &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-database-principals-transact-sql)   
 [sys. server_principals &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql)   
 [sys. sql_logins &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql)   
 [sys. database_role_members &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-database-role-members-transact-sql)   
 [Ruoli a livello di server](server-level-roles.md)   
 [Ruoli a livello di database](database-level-roles.md)  
  
  
