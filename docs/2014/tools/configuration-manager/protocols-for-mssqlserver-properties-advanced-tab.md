---
title: Proprietà - Protocolli per MSSQLSERVER (scheda Avanzate) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: abd5ca68-825f-4c07-b27c-3b3a79d03d74
author: stevestein
ms.author: sstein
ms.openlocfilehash: ef16a5a125883e5ce33e04d9899d0bb882d56541
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85007910"
---
# <a name="protocols-for-mssqlserver-properties-advanced-tab"></a>Proprietà - Protocolli per MSSQLSERVER (scheda Avanzate)
  Usare la scheda **Avanzate** della finestra di dialogo **Proprietà - Protocolli per MSSQLSERVER** per configurare la **protezione estesa per l'autenticazione** per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. La**protezione estesa** è una caratteristica dei componenti della rete implementati dal sistema operativo. La**protezione estesa** è disponibile in Windows 7 e Windows Server 2008 R2 ed è inclusa nei Service Pack per i sistemi operativi precedenti. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è più sicuro quando le connessioni vengono effettuate tramite **protezione estesa**. Per sfruttare alcuni vantaggi della **protezione estesa** è necessario selezionare **Forza crittografia** nella scheda **Flag** .  
  
> [!IMPORTANT]  
>  Per impostazione predefinita, in Windows la **protezione estesa** non è abilitata. Per informazioni sull'abilitazione della **protezione estesa** in Windows, vedere l'articolo della Knowledge Base, [Protezione estesa per l'autenticazione](https://go.microsoft.com/fwlink/?LinkId=178431).  
  
 Per ulteriori informazioni sulla configurazione di altri servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e una descrizione completa della **protezione estesa**, vedere le informazioni più recenti su [Microsoft.com](https://go.microsoft.com/fwlink/?LinkId=177752).  
  
 La**protezione estesa** è supportata in modo completo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client a partire da [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Al momento il supporto per **protezione estesa** non è previsto per altri provider client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Opzioni  
 **Protezione estesa**  
 I tre valori possibili sono:  
  
-   Se impostata su **Disattivata**, la **protezione estesa** è disabilitata. L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accetterà connessioni da qualsiasi client, protetto o non protetto. Il valore**Disattivata** è compatibile con i sistemi operativi precedenti e senza patch installate, sebbene sia meno sicuro. Utilizzare questa impostazione solo quando si è sicuri che i sistemi operativi dei client non supportano la protezione estesa.  
  
-   Se impostata su **Consentita**, la **protezione estesa** è obbligatoria per le connessioni da sistemi operativi che supportano la **protezione estesa**. Le connessioni da applicazioni client non protette in esecuzione su sistemi operativi client protetti vengono rifiutate. La**protezione estesa** viene ignorata per le connessioni da sistemi operativi non protetti. Sebbene sia più sicura di **Disattivata**, questa impostazione non garantisce il livello più elevato di sicurezza. È consigliabile utilizzarla negli ambienti misti, dove solo alcuni sistemi operativi o applicazioni supportano la **protezione estesa** .  
  
-   Se impostata su **Obbligatoria**, vengono accettate solo le connessioni da applicazioni protette su sistemi operativi protetti. Questa impostazione è la più sicura delle tre opzioni, ma le connessioni da sistemi operativi che non supportano la **protezione estesa** non potranno connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **SPN NTLM accettati**  
 Quando l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene identificata da più di un nome dell'entità servizio (SPN) NTLM, elencare i nomi SPN come una serie di stringhe separate da punto e virgola. Il valore **MSSQLSvc/HostName1.Contoso.com;MSSQLSvc/HostName2.Contoso.com**, ad esempio, indica che i client che tentano di connettersi ai nomi SPN denominati **MSSQLSvc/HOST1.Contoso.com** e **MSSQLSvc/HOST2.Contoso.com** sono consentiti. La lunghezza massima della variabile è di 2048 caratteri.  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione estesa per l'autenticazione con Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)  
  
  
