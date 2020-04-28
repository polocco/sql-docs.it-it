---
title: Impostazioni progetto (mapping dei tipi) (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access data types
- data types, default mappings
- default data type mappings
- Project Settings dialog box, Type Mapping
- SQL Server data types
- Type Mapping settings
ms.assetid: b87b9683-abed-4677-8c50-18bdba704655
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 01154cf477435e9dc5335606d0c11a05aecc492b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68066666"
---
# <a name="project-settings-type-mapping-accesstosql"></a>Impostazioni progetto (mapping dei tipi) (AccessToSQL)
Le impostazioni del progetto di mapping dei tipi consentono di impostare i mapping dei tipi predefiniti per il progetto SSMA. È inoltre possibile specificare i mapping dei tipi per singoli oggetti di database. Per ulteriori informazioni, vedere [mapping di tipi di dati di origine e di destinazione](mapping-source-and-target-data-types-accesstosql.md).  
  
Il mapping dei tipi è disponibile nelle finestre di dialogo **Impostazioni** progetto e **Impostazioni progetto predefinite** :  
  
-   Utilizzare la finestra di dialogo **Impostazioni progetto** per impostare le opzioni di configurazione per il progetto corrente. Per accedere alle impostazioni del mapping dei tipi, scegliere **Impostazioni progetto**dal menu **strumenti** e quindi fare clic su **mapping dei tipi** nel riquadro sinistro.  
  
-   Utilizzare la finestra di dialogo **Impostazioni progetto predefinite** per impostare le opzioni di configurazione per tutti i progetti. Per accedere alle impostazioni del mapping dei tipi, nel menu **strumenti** selezionare **Impostazioni progetto predefinite**, selezionare il tipo di progetto di migrazione per cui è necessario visualizzare le impostazioni/changed dall'elenco a discesa **versione destinazione migrazione** e quindi fare clic su **mapping dei tipi** nel riquadro sinistro.  
  
## <a name="options"></a>Opzioni  
**Tipo di origine**  
Tipo di dati di accesso da mappare.  
  
**Tipo di destinazione**  
Tipo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati di destinazione o SQL Azure per il tipo di dati di accesso specificato.  
  
Nella tabella seguente viene illustrato il mapping predefinito tra i tipi di dati di origine e di destinazione.  
  
|Tipo di dati Access|Tipo di dati di SQL Server|  
|--------------------|------------------------|  
|**binario [\*.. \*]**|**varbinary [\*]**|  
|**boolean**|**bit**|  
|**byte**|**tinyint**|  
|**valuta**|**money**|  
|**date**|**datetime**|  
|**decimal**|**float**|  
|**double**|**float**|  
|**GUID**|**uniqueidentifier**|  
|**integer**|**smallint**|  
|**long**|**int**|  
|**LongBinary**|**varbinary(max)**|  
|**memo**|**nvarchar(max)**|  
|**Memo** : per l'accesso 97|**ntext**|  
|**single**|**real**|  
|**testo [\*.. \*]**|**nvarchar [\*]**|  
|**testo [\*.. ] \*** -per Access 97|**varchar [\*]**|  
  
**Aggiungere**  
Fare clic su questo pulsante per aggiungere un tipo di dati all'elenco di mapping.  
  
**Modifica**  
Fare clic per modificare un tipo di dati nell'elenco mapping.  
  
**Rimuovi**  
Fare clic per rimuovere il mapping dei tipi di dati selezionati dall'elenco mapping.  
  
**Ripristina predefiniti**  
Fare clic per reimpostare tutti i mapping dei tipi di dati sulle impostazioni predefinite SSMA.  
  
## <a name="see-also"></a>Vedere anche  
[Mapping dei tipi di dati origine e destinazione](mapping-source-and-target-data-types-accesstosql.md)  
[Guida di riferimento all'interfaccia utente (accesso)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
