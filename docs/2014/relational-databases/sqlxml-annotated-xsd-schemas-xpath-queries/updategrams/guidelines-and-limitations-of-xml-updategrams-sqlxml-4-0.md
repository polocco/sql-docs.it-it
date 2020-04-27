---
title: Linee guida e limitazioni degli updategram XML (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 953fc5b7c203faa8fa6a9820993a3d0fd7a7de40
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66014832"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Linee guida e limitazioni per gli updategram XML (SQLXML 4.0)
  Quando si utilizzano updategram XML, tenere presenti le considerazioni seguenti:  
  
-   Se si utilizza un updategram per un'operazione di inserimento con una sola coppia di ** \<prima di>** e ** \<dopo>** blocchi, il ** \<blocco before>** può essere omesso. Viceversa, nel caso di un'operazione di eliminazione, il ** \<blocco after>** può essere omesso.  
  
-   Se si utilizza un updategram con più ** \<prima di>** e ** \<dopo>** blocchi nel tag di ** \<>di sincronizzazione** , è necessario specificare sia ** \<prima** dei blocchi>che ** \<dopo** i blocchi>per formare ** \<prima>** e **dopo \<** le coppie di>.  
  
-   Gli aggiornamenti in un updategram vengono applicati alla vista XML fornita da XML Schema. Ai fini della corretta esecuzione del mapping predefinito, è pertanto necessario specificare il nome del file dello schema nell'updategram o, se il nome di file non viene fornito, i nomi di elemento e di attributo devono corrispondere ai nomi di tabella e di colonna nel database.  
  
-   SQLXML 4.0 richiede che tutti i valori di colonna in un updategram vengano mappati in modo esplicito nello schema (XDR o XSD) fornito per creare la vista XML per i relativi elementi figlio. Questo comportamento differisce dalle versioni precedenti di SQLXML, che consentono la presenza di un valore per una colonna di cui non sia stato eseguito il mapping nello schema se definita in modo implicito come parte della chiave esterna in un'annotazione `sql:relationship`. Si noti che questa modifica non influisce sulla propagazione dei valori di chiave primaria negli elementi figlio, che si verifica tuttora per SQLXML 4.0 se non viene specificato in modo esplicito alcun valore per l'elemento figlio.  
  
-   Se si utilizza un updategram per modificare i dati in una colonna binaria, ad esempio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` il tipo di dati, è necessario fornire uno schema di mapping in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cui è necessario specificare il tipo `sql:datatype="image"`di dati (ad esempio,) e il tipo `dt:type="binhex"` di `dt:type="binbase64`dati XML (ad esempio, o). I dati per la colonna binaria devono essere specificati nell'updategram. L'annotazione `sql:url-encode` specificata nello schema di mapping viene ignorata dall'updategram.  
  
-   Quando si scrive uno schema XSD, se il valore specificato per l'annotazione `sql:relation` o `sql:field` include un carattere speciale, ad esempio uno spazio (come nel nome di tabella "Dettagli ordine"), questo valore deve essere racchiuso tra parentesi, ad esempio "[Dettagli ordine]".  
  
-   Quando si utilizzano updategram, le relazioni a catena non sono supportate. Se, ad esempio, le tabelle A e C sono correlate tramite una relazione a catena che utilizza la tabella B, si verifica l'errore seguente quando si tenta di eseguire l'updategram:  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Anche se lo schema e l'updategram sono entrambi altrimenti corretti e hanno un formato valido, l'errore si verifica se è presente una relazione a catena.  
  
-   Gli updategram non permettono il passaggio del tipo di dati `image` come parametri durante gli aggiornamenti.  
  
-   I tipi BLOB (Binary Large Object) `text/ntext` come le ** \<** immagini e non devono essere utilizzati nel blocco before>in quando si utilizzano updategram, perché verranno inclusi per l'utilizzo nel controllo della concorrenza. Ciò può provocare problemi con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a causa delle limitazioni applicate al confronto per i tipi BLOB. La parola chiave LIKE, ad esempio, viene utilizzata nella clausola WHERE per il confronto tra colonne del tipo di dati `text`. I confronti, tuttavia, hanno esito negativo in presenza di tipi BLOB in cui le dimensioni dei dati sono maggiori di 8K.  
  
-   La presenza di caratteri speciali nei dati `ntext` può provocare problemi con SQLXML 4.0 a causa delle limitazioni applicate al confronto per i tipi BLOB. Ad esempio, l'utilizzo di "[Serializable]" nel blocco ** \<before>** di uno updategram se utilizzato nel controllo della concorrenza di una colonna di `ntext` tipo avrà esito negativo con la descrizione di errore SQLOLEDB seguente:  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>Vedi anche  
 [Considerazioni sulla sicurezza degli updategram &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
