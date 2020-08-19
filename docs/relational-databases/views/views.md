---
description: Viste
title: Viste | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], about views
ms.assetid: ada83c28-e8b7-45d9-b53c-b3d67c8820c8
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: dda5e49aa6f51382beb390ae48a544565e2703d9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88418925"
---
# <a name="views"></a>Viste
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  Una vista è una tabella virtuale il cui contenuto è definito da una query. In modo analogo a una tabella, una vista è costituita da un set di colonne e righe di dati denominate. A meno che non sia indicizzata, una vista non esiste come set archiviato di valori di dati in un database. Le righe e le colonne di dati provengono da tabelle a cui fa riferimento la query che definisce la vista e sono prodotte dinamicamente quando si fa riferimento alla vista.  
  
 Una vista esegue operazioni di filtro sulle tabelle sottostanti a cui fa riferimento. La query che definisce la vista può provenire da una o più tabelle o da altre viste del database corrente o di altri database. È inoltre possibile utilizzate le query distribuite per definire viste che utilizzano dati provenienti da più origini eterogenee. Questa caratteristica è utile, ad esempio, se si desidera combinare dati strutturati in modo simile e provenienti da server diversi, ognuno dei quali archivia i dati di una diversa area dell'organizzazione.  
  
 Tramite le viste è possibile analizzare, semplificare e personalizzare la visualizzazione del database per ogni singolo utente. Le viste rappresentano un meccanismo di sicurezza grazie al quale è possibile consentire agli utenti di accedere ai dati tramite una vista, senza concedere loro le autorizzazioni di accesso alle tabelle di base sottostanti. Le viste consentono di fornire un'interfaccia compatibile con le versioni precedenti tramite la quale è possibile emulare una tabella precedente il cui schema è stato modificato oppure possono essere utilizzate per migliorare le prestazioni e per partizionare i dati quando si copiano dati in e da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="types-of-views"></a>Tipi di viste  
 Oltre alle viste di base definite dall'utente, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono disponibili i seguenti tipi di viste utilizzate per scopi specifici in un database.  
  
 Viste indicizzate  
 Una vista indicizzata è una vista precedentemente materializzata. Ciò significa che è stata calcolata la definizione della vista e che i dati risultanti sono stati archiviati come una tabella. Per indicizzare una vista, è necessario creare su di essa un indice cluster univoco. Le viste indicizzate possono migliorare notevolmente le prestazioni di alcuni tipi di query. e risultano ideali per le query che prevedono l'aggregazione di molte righe. Non sono invece adatte per i set di dati sottostanti che vengono aggiornati di frequente.  
  
 Viste partizionate  
 Una vista partizionata unisce i dati partizionati orizzontalmente di un set di tabelle membro in uno o più server. In tal modo i dati risulteranno appartenenti a un'unica tabella. Una vista che unisce tabelle membro nella stessa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] costituisce una vista partizionata locale.  
  
 Viste di sistema  
 Le visualizzazioni di sistema espongono metadati del catalogo. È possibile utilizzare visualizzazioni di sistema per ottenere informazioni sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o gli oggetti definiti nell'istanza. Ad esempio, è possibile eseguire una query sulla vista del catalogo sys.databases per ottenere informazioni sui database definiti dall'utente disponibili nell'istanza. Per altre informazioni, vedere [Viste di sistema &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90).  
  
## <a name="common-view-tasks"></a>Attività comuni delle viste  
 Nella tabella riportata di seguito vengono forniti i collegamenti ad attività comuni associate alla creazione o alla modifica di una vista.  
  
|Attività relative alle viste|Argomento|  
|----------------|-----------|  
|Viene descritto come creare una vista.|[Creare viste](../../relational-databases/views/create-views.md)|  
|Viene descritto come creare una vista indicizzata.|[Creazione di viste indicizzate](../../relational-databases/views/create-indexed-views.md)|  
|Viene descritto come modificare la definizione di una vista.|[Modificare viste](../../relational-databases/views/modify-views.md)|  
|Viene descritto come modificare dati tramite una vista.|[Modificare i dati tramite una vista](../../relational-databases/views/modify-data-through-a-view.md)|  
|Viene descritto come eliminare una vista.|[Eliminare viste](../../relational-databases/views/delete-views.md)|  
|Viene descritto come ottenere informazioni su una vista quale la definizione della vista.|[Ottenere informazioni su una vista](../../relational-databases/views/get-information-about-a-view.md)|  
|Viene descritto come rinominare una vista.|[Rinominare viste](../../relational-databases/views/rename-views.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Creare viste su colonne XML](../../relational-databases/xml/create-views-over-xml-columns.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)  
  
  
