---
title: Altre annotazioni (SQLXML)
description: Consente di visualizzare un elenco di annotazioni SQLXML con una descrizione del modo in cui ognuno viene interpretato dal caricamento bulk XML.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 30e59d3fc049d56e8142f241dc5c75c054db837c
ms.sourcegitcommit: 6593b3b6365283bb76c31102743cdccc175622fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2020
ms.locfileid: "84306260"
---
# <a name="annotation-interpretation---other-annotations"></a>Interpretazione delle annotazioni - Altre annotazioni
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Oltre alle annotazioni descritte negli argomenti precedenti di questa sezione, il caricamento bulk XML interpreta queste altre annotazioni, come segue:  
  
 **sql:id-prefix**  
 Se lo schema specifica i prefissi dei dati XML, il caricamento bulk XML rimuove i prefissi prima di inviare i dati a Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **sql:use-cdata**  
 Il caricamento bulk XML legge il testo archiviato nelle sezioni CDATA e lo invia a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **sql:url-encode**  
 Il caricamento bulk XML non supporta questa annotazione. Non è possibile ad esempio specificare un URL nei dati XML di input e prevedere che il caricamento bulk XML legga i dati da tale posizione per archiviarli nel database.  
  
 **sql:is-mapping-schema**  
 Il caricamento bulk XML non supporta questa annotazione né supporta **SQL: ID**.  
  
> [!NOTE]  
>  Il caricamento bulk XML non supporta schemi di mapping inline.  
  
 **sql:key-fields**  
 Il caricamento bulk XML ignora sempre questa annotazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interpretazione dell'annotazione &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sqlxml-4-0.md)  
  
  
