---
title: Configurare l'opzione di configurazione del server nested triggers | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- nested triggers option
ms.assetid: 29d7372b-d406-4a5b-80c6-a2d231d25211
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7b27e185b0833f2e51be16393ff4d59a81046970
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935604"
---
# <a name="configure-the-nested-triggers-server-configuration-option"></a>Configurare l'opzione di configurazione del server nested triggers
  In questo argomento si illustra come configurare l'opzione di configurazione del server **nested triggers** in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Con l'opzione **nested triggers** è possibile verificare se è possibile effettuare una sovrapposizione tramite un trigger AFTER, cioè eseguire un'azione con cui viene avviato un altro trigger, mediante il quale a sua volta ne viene avviato un altro e così via. Se l'opzione **nested triggers** è impostata su 0, i trigger AFTER non supportano la propagazione. Se l'opzione **nested triggers** è impostata su 1 (valore predefinito), i trigger AFTER supportano 32 livelli di propagazione. I trigger INSTEAD OF possono essere annidati indipendentemente dall'impostazione di questa opzione.  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per configurare l'opzione nested triggers tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Completamento:**  [Dopo la configurazione dell'opzione nested triggers](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
 Le autorizzazioni di esecuzione per **sp_configure** senza alcun parametro o solo con il primo parametro vengono assegnate per impostazione predefinita a tutti gli utenti. Per eseguire **sp_configure** con entrambi i parametri per la modifica di un'opzione di configurazione o per l'esecuzione dell'istruzione RECONFIGURE, a un utente deve essere concessa l'autorizzazione a livello di server ALTER SETTINGS. L'autorizzazione ALTER SETTINGS è assegnata implicitamente ai ruoli predefiniti del server **sysadmin** e **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-configure-the-nested-triggers-option"></a>Per configurare l'opzione nested triggers  
  
1.  In **Esplora oggetti**fare clic con il pulsante destro del mouse su un server, quindi scegliere **Proprietà**.  
  
2.  Nella pagina **Avanzate** impostare l'opzione **Consenti attivazione trigger da altri trigger** su **True** (impostazione predefinita) o **False**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-configure-the-nested-triggers-option"></a>Per configurare l'opzione nested triggers  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. Questo esempio illustra come usare [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) per impostare il valore dell'opzione `nested triggers` su `0`.  
  
```wmimof  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'nested triggers', 0 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Per altre informazioni, vedere [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)sia installato il servizio WMI.  
  
##  <a name="follow-up-after-you-configure-the-nested-triggers-option"></a><a name="FollowUp"></a> Completamento: Dopo la configurazione dell'opzione nested triggers  
 L'impostazione diventa effettiva immediatamente senza dover riavviare il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di trigger annidati](../../relational-databases/triggers/create-nested-triggers.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
