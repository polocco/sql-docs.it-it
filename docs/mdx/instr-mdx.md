---
title: InStr (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 201580b71086dfe39e669966070dae2dca72e3eb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68105306"
---
# <a name="instr-mdx"></a>Instr (MDX)


  Restituisce la posizione della prima occorrenza di una stringa all'interno di un'altra stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
InStr([start, ]searched_string, search_string[, compare])  
```  
  
## <a name="arguments"></a>Argomenti  
 *start*  
 (Facoltativo) Espressione numerica che imposta la posizione iniziale per ciascuna ricerca. Se questo valore viene omesso, la ricerca inizia in corrispondenza della posizione del primo carattere. Se start è Null, il valore restituito dalla funzione è indefinito.  
  
 *searched_string*  
 Espressione stringa in cui eseguire la ricerca.  
  
 *search_string*  
 Espressione stringa di cui eseguire la ricerca.  
  
 *Confronta*  
 (Facoltativo) Valore intero. Questo argomento viene sempre ignorato. Viene definito per la compatibilità con altre funzioni **InStr** in altri linguaggi.  
  
## <a name="return-value"></a>Valore restituito  
 Valore intero con la posizione iniziale di *string2* in *String1*.  
  
 Inoltre, la funzione **InStr** restituisce i valori elencati nella tabella seguente, a seconda della condizione:  
  
|Condizione|Valore restituito|  
|---------------|------------------|  
|String1 ha una lunghezza zero|zero (0)|  
|String1 è Null|Non definito|  
|String2 ha una lunghezza zero|start|  
|String2 è Null|Non definito|  
|String2 non trovato|zero (0)|  
|start è maggiore di Len(String2)|zero (0)|  
  
## <a name="remarks"></a>Osservazioni  
  
> [!WARNING]  
>  **InStr** esegue sempre un confronto senza distinzione tra maiuscole e minuscole.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo della funzione **InStr** e vengono visualizzati diversi scenari di risultato.  
  
```  
with   
    member [Date].[Date].[Results] as "Results"  
    member measures.[lowercase found in lowercase string] as InStr( "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[uppercase found in lowercase string] as InStr( "abcdefghijklmnñopqrstuvwxyz", "O")  
    member measures.[searched string is empty]            as InStr( "", "o")  
    member measures.[searched string is null]             as iif(IsError(InStr( null, "o")), "Is Error", iif(IsNull(InStr( null, "o")), "Is Null","Is undefined"))  
    member measures.[search string is empty]              as InStr( "abcdefghijklmnñopqrstuvwxyz", "")  
    member measures.[search string is empty start 10]     as InStr(10, "abcdefghijklmnñopqrstuvwxyz", "")  
    member measures.[search string is null]               as iif(IsError(InStr( null, "o")), "Is Error", iif(IsNull(InStr( null, "o")), "Is Null","Is undefined"))  
    member measures.[found from start 10]                 as InStr( 10, "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[NOT found from start 17]             as InStr( 17, "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[NULL start]                          as iif(IsError(InStr( null, "abcdefghijklmnñopqrstuvwxyz", "o")), "Is Error", iif(IsNull(InStr( null, "abcdefghijklmnñopqrstuvwxyz", "o")), "Is Null","Is undefined"))  
    member measures.[start greater than searched length]  as InStr( 170, "abcdefghijklmnñopqrstuvwxyz", "o")  
  
select  [Results] on columns,  
       { measures.[lowercase found in lowercase string]  
       , measures.[uppercase found in lowercase string]  
       , measures.[searched string is empty]  
       , measures.[searched string is null]  
       , measures.[search string is empty]  
       , measures.[search string is empty start 10]  
       , measures.[search string is null]  
       , measures.[found from start 10]  
       , measures.[NOT found from start 17]  
       , measures.[NULL start]   
       , measures.[start greater than searched length]  
       } on rows  
  
from [Adventure Works]  
```  
  
 Nella tabella seguente vengono illustrati i risultati ottenuti.  
  
|||  
|-|-|  
||Risultati|  
|carattere minuscolo trovato in stringa minuscola|16|  
|carattere maiuscolo trovato in stringa minuscola|16|  
|stringa ricercata vuota|0|  
|stringa ricercata Null|Non definito|  
|stringa di ricerca vuota|1|  
|stringa di ricerca vuota start 10|10|  
|stringa di ricerca Null|Non definito|  
|trovato da start 10|16|  
|NOT trovato da start 17|0|  
|start NULL|Non definito|  
|start maggiore della lunghezza ricercata|0|  
  
  
