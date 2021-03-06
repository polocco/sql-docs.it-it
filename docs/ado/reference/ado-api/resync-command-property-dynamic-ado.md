---
description: Proprietà dinamica Resync Command (ADO)
title: Proprietà del comando di risincronizzazione-Dynamic (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Resync Command property [ADO]
ms.assetid: 4e2bb601-0fe8-4d61-b00e-38341d85a6bb
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e882a9c65bf0d54dc9bd9e160edbc67f4e7996b
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989512"
---
# <a name="resync-command-property-dynamic-ado"></a>Proprietà dinamica Resync Command (ADO)
Specifica una stringa di comando fornita dall'utente che il metodo di [Risincronizzazione](./resync-method.md) emette per aggiornare i dati nella tabella denominata nella proprietà dinamica della [tabella univoca](./unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) .  
  
## <a name="settings-and-return-values"></a>Impostazioni e valori restituiti  
 Imposta o restituisce un valore **stringa** che è una stringa di comando.  
  
## <a name="remarks"></a>Osservazioni  
 L'oggetto [Recordset](./recordset-object-ado.md) è il risultato di un'operazione di join eseguita in più tabelle di base. Le righe interessate dipendono dal parametro *AffectRecords* del metodo [Resync](./resync-method.md) . Il metodo di **Risincronizzazione** standard viene eseguito se le proprietà [univoche](./unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) del comando della tabella e della **Risincronizzazione** non sono impostate.  
  
 La stringa di comando della proprietà del **comando resync** è un comando con parametri o stored procedure che identifica in modo univoco la riga da aggiornare e restituisce una singola riga contenente lo stesso numero e l'ordine delle colonne della riga da aggiornare. La stringa di comando contiene un parametro per ogni colonna chiave primaria nella **tabella univoca**. in caso contrario, viene restituito un errore di run-time. I parametri vengono compilati automaticamente con i valori di chiave primaria della riga da aggiornare.  
  
 Di seguito sono riportati due esempi basati su SQL:  
  
 1 \) il **Recordset** è definito da un comando:  
  
```  
SELECT * FROM Customers JOIN Orders ON   
   Customers.CustomerID = Orders.CustomerID  
   WHERE city = 'Seattle'  
   ORDER BY CustomerID  
```  
  
 La proprietà del **comando resync** è impostata su:  
  
```  
"SELECT * FROM   
   (SELECT * FROM Customers JOIN Orders   
   ON Customers.CustomerID = Orders.CustomerID  
   city = 'Seattle' ORDER BY CustomerID)  
WHERE Orders.OrderID = ?"  
```  
  
 La **tabella univoca** è *Orders* e la relativa chiave primaria, *OrderID*, è parametrizzata. La sub-SELECT fornisce un modo semplice per garantire a livello di codice il numero e l'ordine delle colonne restituiti dal comando originale.  
  
 2 \) il **Recordset** è definito da un stored procedure:  
  
```  
CREATE PROC Custorders @CustomerID char(5) AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID   
WHERE Customers.CustomerID = @CustomerID  
```  
  
 Il metodo di **Risincronizzazione** deve eseguire i stored procedure seguenti:  
  
```  
CREATE PROC CustordersResync @ordid int AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID  
WHERE Orders.ordid  = @ordid  
```  
  
 La proprietà del **comando resync** è impostata su:  
  
```  
"{call CustordersResync (?)}"  
```  
  
 Ancora una volta, la **tabella univoca** è *Orders* e la relativa chiave primaria, *OrderID*, è parametrizzata.  
  
 **Il comando di risincronizzazione** è una proprietà dinamica aggiunta alla raccolta delle [proprietà](./properties-collection-ado.md) dell'oggetto **Recordset** quando la proprietà [CursorLocation](./cursorlocation-property-ado.md) è impostata su **adUseClient**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](./recordset-object-ado.md)