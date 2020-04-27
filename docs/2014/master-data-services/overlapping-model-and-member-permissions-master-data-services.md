---
title: Autorizzazioni per modelli e membri sovrapposte (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], effective permissions
- permissions [Master Data Services], model and member overlaps
- members [Master Data Services], effective permissions
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ca57d34a3dda2880f3882d1940c6852af0729fb7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "65482737"
---
# <a name="overlapping-model-and-member-permissions-master-data-services"></a>Autorizzazioni per modelli e membri sovrapposte (Master Data Services)
  Le autorizzazioni assegnate a un membro possono sovrapporsi alle autorizzazioni assegnate a un oggetto modello. Quando si verificano sovrapposizioni, viene applicata l'autorizzazione più restrittiva.  
  
 Se un membro dispone di autorizzazione diversa da quella del relativo oggetto modello corrispondente, si applicano le regole seguenti:  
  
-   **Nega** esegue l'override di tutte le altre autorizzazioni.  
  
-   **Aggiornamento** **di sola lettura** esegue l'override di.  
  
 Nell'immagine seguente viene indicato quali autorizzazioni vengono applicate a ogni singolo valore di attributo quando le autorizzazioni per gli attributi sono diverse dalle autorizzazioni per i membri.  
  
 ![mds_conc_security_member_overlap_table](../../2014/master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")  
  
## <a name="example-1"></a>Esempio 1  
 ![mds_conc_overlap_model_1](../../2014/master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")  
  
 Nella scheda **Modelli** all'entità Product è stata assegnata l'autorizzazione **Aggiorna** . Tutti gli attributi nell'entità ereditano questa autorizzazione.  
  
 Nella scheda **Membri gerarchia** il nodo della sottocategoria Mountain Bikes in una gerarchia derivata dispone dell'autorizzazione **Aggiorna** .  
  
 Risultato: in **Esplora**l'utente dispone dell'autorizzazione **Aggiorna** per tutti i valori di attributo per tutti i membri nel nodo Mountain Bike. Tutti gli altri membri e attributi sono nascosti.  
  
 ![mds_conc_overlap_model_example_1](../../2014/master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")  
  
## <a name="example-2"></a>Esempio 2  
 ![mds_conc_overlap_model_2](../../2014/master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")  
  
 Nella scheda **Modelli** all'attributo Subcategory è assegnata l'autorizzazione **Aggiorna** .  
  
 Nella scheda **membri gerarchia** , al nodo della sottocategoria Mountain Bikes in una gerarchia derivata viene assegnata in modo esplicito l'autorizzazione **di sola lettura** .  
  
 Risultato: in **Esplora**l'utente dispone dell'autorizzazione di sola **lettura** per i valori dell'attributo Subcategory per i membri del nodo Mountain Bikes. Tutti gli altri membri e attributi sono nascosti.  
  
 ![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## <a name="example-3"></a>Esempio 3  
 ![mds_conc_overlap_model_3](../../2014/master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")  
  
 Nella scheda **modelli** all'attributo Subcategory è stata assegnata l'autorizzazione di sola **lettura** .  
  
 Nella scheda **Membri gerarchia** alla sottocategoria Mountain Bikes in una gerarchia derivata è stata assegnata in modo esplicito l'autorizzazione **Aggiorna** .  
  
 Risultato: in **Esplora**l'utente dispone dell'autorizzazione di sola **lettura** per i valori dell'attributo. Tutti gli altri membri e attributi sono nascosti.  
  
 ![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## <a name="see-also"></a>Vedi anche  
 [Modalità di determinazione delle autorizzazioni &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)   
 [Autorizzazioni utenti e gruppi sovrapposte &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  
