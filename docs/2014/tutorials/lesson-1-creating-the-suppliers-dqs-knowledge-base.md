---
title: 'Lezione 1: creazione della Knowledge Base DQS Suppliers | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 78825ccb-30fc-463c-8140-435532e2ecd2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e9421f568dae28895eb40b397d5e2589fafe0186
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054327"
---
# <a name="lesson-1-creating-the-suppliers-dqs-knowledge-base"></a>Lezione 1: Creazione di una Knowledge Base DQS Suppliers
  In questa lezione verrà creata una Knowledge Base DQS denominata **Suppliers** con le informazioni (metadati) sui dati del fornitore. È possibile utilizzare la Knowledge Base per effettuare attività di pulizia e di corrispondenza nei dati di input del fornitore. Tramite l'attività di pulizia è possibile identificare i dati errati/non validi, correggere i dati errati, proporre correzioni/suggerimenti, standardizzare i dati, nonché arricchire i dati con ulteriori informazioni. Tramite l'attività di corrispondenza è possibile confrontare i dati e identificare in essi i record simili, ma leggermente diversi, al fine di rimuovere i dati duplicati.  
  
 È possibile utilizzare sia processi interattivi sia computerizzati per creare, compilare e gestire una Knowledge Base. Le informazioni in una Knowledge Base sono mantenute in domini, ognuno dei quali è specifico per un campo dati nei dati che si desidera pulire e/o di cui di desidera individuarne le corrispondenze.  
  
 In questa lezione vengono eseguite le attività seguenti per creare la Knowledge base **Suppliers** :  
  
-   Creare una Knowledge Base DQS denominata **Suppliers**. È possibile creare una Knowledge Base in diversi modi. Ad esempio, è possibile compilare una Knowledge Base nuova o basata su una esistente oppure importando un file DQS (con estensione dqs) contenente una Knowledge Base predefinita ed esportata o, ancora, effettuando un'attività di individuazione delle informazioni nei dati di esempio. In questa esercitazione si crea una Knowledge Base nuova.  
  
-   Creare domini nella Knowledge base **Suppliers** utilizzati per la pulizia dei dati e la corrispondenza dei dati per identificare i duplicati. Creazione di domini per i campi dati da utilizzare per le attività di pulizia e di corrispondenza, non per tutti i campi dati nei dati.  
  
-   Aggiunta di valori a un dominio inserendoli manualmente (importando i valori da un file di Excel), effettuando un'attività di individuazione delle informazioni sui dati di esempio, nonché importando i valori del progetto da un progetto di pulizia. Inoltre, possibilità di importare valori di dominio importando un file DQS contenente proprietà e valori di dominio, non utilizzati nell'esercitazione.  
  
-   Impostazione delle regole per un dominio. Una regola di dominio è una condizione utilizzata da DQS per convalidare, correggere e standardizzare i valori di dominio.  
  
-   Impostazione di relazioni basate su termini per un dominio. Una relazione basata su termini consente di effettuare una correzione a un termine che fa parte di un valore in un dominio, Ad esempio, nel valore **Contoso Inc., Inc.** è un termine che può essere definito come incorporato. In questo modo la standardizzazione dei dati e l'identificazione di duplicati risultano operazioni semplici. Ad esempio, **Contoso Inc.** e **Contoso Incorporated** possono essere considerati duplicati.  
  
-   Specifica di sinonimi nei valori di dominio. È possibile impostare due o più valori come sinonimi e impostare uno di essi come valore iniziale, che sostituisce i relativi valori sinonimi durante l'attività di pulizia per la standardizzazione dei dati.  
  
-   Creazione di un dominio composito denominato Address Validation comprendente i domini Address line, City, State e Zip. Un dominio composito è un dominio costituito da uno o più singoli domini mediante il quale è possibile creare una regola che interessa più domini, È ad esempio possibile definire una regola: se City è Los Angeles, State deve essere CA, dove City e State sono due domini separati.  
  
-   Configurazione e utilizzo di un servizio dati di riferimento. La funzionalità relativa ai servizi dati di riferimento in Data Quality Services (DQS) consente di sottoscrivere a provider di dati di riferimento di terze parti per pulire e arricchire i dati aziendali convalidandoli mediante confronto con dati di alta qualità. È possibile utilizzare i servizi offerti da provider DQS leader dall'interno di DQS, in modo da standardizzare, correggere o arricchire i dati durante il processo di pulizia. Questa esercitazione illustra come configurare l'ambiente DQS per l'uso di un servizio dati di riferimento in Azure Marketplace e usare il servizio associato al dominio composito Address Validation per pulire i dati degli indirizzi.  
  
-   Pubblicazione della Knowledge Base in modo da poterla utilizzare nelle attività di pulizia e di corrispondenza.  
  
## <a name="next-step"></a>passaggio successivo  
 [Attività 1: Creazione di una Knowledge Base e dei domini](../../2014/tutorials/task-1-creating-a-knowledge-base-and-domains.md)  
  
  
