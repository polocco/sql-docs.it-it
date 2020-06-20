---
title: Proprietà server (pagina Memoria) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.memory.f1
ms.assetid: 46a77d4e-ab92-49d3-a14b-423462e50715
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0ee690ddfc4cc02769db6d07d226cb154f3c4eae
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934922"
---
# <a name="server-properties-memory-page"></a>Proprietà server (pagina Memoria)
  Utilizzare questa pagina per visualizzare o modificare le opzioni di memoria per il server. Quando l'opzione **Memoria minima per il server** è impostata su 0 e l'opzione **Memoria massima per il server** è impostata su 2147483647 MB, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può usare in ogni momento la quantità ottimale di memoria, tenendo tuttavia conto della quantità di memoria attualmente usta dal sistema operativo e da altre applicazioni. Mano a mano che il carico di lavoro del computer e di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cambia, anche la quantità di memoria allocata varia di conseguenza. È possibile limitare ulteriormente questa allocazione dinamica della memoria in base ai valori minimi e massimi specificati di seguito.  
  
## <a name="options"></a>Opzioni  
 **Memoria minima per il server (in MB)**  
 Consente di specificare che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere avviato con una quantità di memoria allocata non inferiore al valore minimo e che non deve essere rilasciata memoria al di sotto di tale valore. Impostare il valore in base alle dimensioni e all'attività dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Impostare questa opzione su un valore che non obblighi il sistema operativo a richiedere troppa memoria da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , inibendo le prestazioni di Windows.  
  
 **Memoria massima per il server (in MB)**  
 Consente di specificare la quantità massima di memoria che può essere allocata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all'avvio e durante l'esecuzione. Questa opzione di configurazione può essere impostata su un valore specifico se unitamente all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono eseguite più applicazioni e si desidera garantire a tali applicazioni una quantità di memoria sufficiente. Se tali applicazioni, ad esempio server Web o di posta elettronica, richiedono memoria soltanto quando è necessario, non impostare l'opzione. L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rilascerà la memoria necessaria al momento opportuno. Altri tipi di applicazioni utilizzano la memoria disponibile all'avvio e non richiedono ulteriore memoria, anche quando questa risulta necessaria. Se un'applicazione di questo tipo viene eseguita contemporaneamente a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nello stesso computer, impostare l'opzione su un valore adeguato per garantire che la memoria richiesta dall'altra applicazione non venga allocata dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le quantità minime di memoria che è possibile specificare per **max server memory** sono 64 megabyte (MB) per i sistemi a 32 bit e 128 MB per i sistemi a 64 bit.  
  
 **Memoria per la creazione degli indici (in KB, 0 = memoria dinamica)**  
 Consente di specificare la quantità di memoria (in KB) da utilizzare per gli ordinamenti di creazione dell'indice. Il valore predefinito zero consente di abilitare l'allocazione dinamica e dovrebbe funzionare nella maggior parte dei casi senza necessità di ulteriori regolazioni. L'utente può comunque immettere un valore diverso compreso tra 704 e 2147483647.  
  
> [!NOTE]  
>  Non sono consentiti valori compresi tra 1 e 703. Se viene immesso un valore compreso in questo intervallo, il campo sostituisce il valore digitato con 704.  
  
 **Memoria minima per le query (KB)**  
 Consente di specificare la quantità di memoria (in KB) da allocare per l'esecuzione di una query. È possibile impostare un valore compreso tra 512 e 2147483647 KB. Il valore predefinito è 1024 KB.  
  
 **Valori configurati**  
 Consente di visualizzare i valori configurati per le opzioni nel riquadro. Se si modificano i valori, fare clic su **Valori correnti** per verificare se le modifiche sono diventate effettive. In caso contrario, l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere prima riavviata.  
  
 **Valori correnti**  
 Consente di visualizzare i valori correnti per le opzioni contenute nel riquadro. I valori sono di sola lettura.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [Opzioni di configurazione del server Server Memory](server-memory-server-configuration-options.md)  
  
  
