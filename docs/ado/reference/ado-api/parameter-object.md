---
description: Oggetto Parameter
title: Oggetto Parameter | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameter
helpviewer_keywords:
- Parameter object [ADO]
ms.assetid: e010e794-7f0f-4026-8b5b-37328e437d63
author: rothja
ms.author: jroth
ms.openlocfilehash: 123ca1553ede61735565a6f82cb36b0035c56dcb
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990172"
---
# <a name="parameter-object"></a>Oggetto Parameter
Rappresenta un parametro o un argomento associato a un oggetto [Command](./command-object-ado.md) basato su una query con parametri o stored procedure.  
  
## <a name="remarks"></a>Osservazioni  
 Molti provider supportano i comandi con parametri. Si tratta di comandi in cui l'azione desiderata viene definita una volta, ma le variabili o i parametri vengono usati per modificare alcuni dettagli del comando. Ad esempio, un'istruzione SQL SELECT può utilizzare un parametro per definire i criteri di corrispondenza di una clausola WHERE e un altro per definire il nome della colonna per una clausola SORT BY.  
  
 Gli oggetti **Parameter** rappresentano i parametri associati alle query con parametri o gli argomenti in/out e i valori restituiti delle stored procedure. A seconda della funzionalità del provider, alcune raccolte, metodi o proprietà di un oggetto **Parameter** potrebbero non essere disponibili.  
  
 Con le raccolte, i metodi e le proprietà di un oggetto **Parameter** , è possibile eseguire le operazioni seguenti:  
  
-   Impostare o restituire il nome di un parametro con la proprietà [Name](./name-property-ado.md) .  
  
-   Imposta o restituisce il valore di un parametro con la proprietà [value](./value-property-ado.md) . **Value** è la proprietà predefinita dell'oggetto **Parameter** .  
  
-   Impostare o restituire le caratteristiche dei parametri con le proprietà [Attributes](./attributes-property-ado.md), [Direction](./direction-property.md), [Precision](./precision-property-ado.md), [NumericScale](./numericscale-property-ado.md), [size](./size-property-ado-parameter.md)e [Type](./type-property-ado.md) .  
  
-   Passare dati di tipo carattere o binario lungo a un parametro con il metodo [AppendChunk](./appendchunk-method-ado.md) .  
  
-   Accedere agli attributi specifici del provider tramite la raccolta [Properties](./properties-collection-ado.md) .  
  
 Se si conoscono i nomi e le proprietà dei parametri associati alla stored procedure o alla query con parametri che si vuole chiamare, è possibile usare il metodo [CreateParameter](./createparameter-method-ado.md) per creare oggetti **Parameter** con le impostazioni delle proprietà appropriate e usare il metodo [Append](./append-method-ado.md) per aggiungerli alla raccolta [Parameters](./parameters-collection-ado.md) . In questo modo è possibile impostare e restituire i valori dei parametri senza dover chiamare il metodo [Refresh](./refresh-method-ado.md) sulla raccolta **Parameters** per recuperare le informazioni sui parametri dal provider, un'operazione che richiede un utilizzo intensivo di risorse.  
  
 L'oggetto **Parameter** non è sicuro per lo scripting.  
  
 Questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto Parameter](./parameter-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Command (ADO)](./command-object-ado.md)   
 [Metodo CreateParameter (ADO)](./createparameter-method-ado.md)   
 [Raccolta Parameters (ADO)](./parameters-collection-ado.md)   
 [Raccolta Properties (ADO)](./properties-collection-ado.md)