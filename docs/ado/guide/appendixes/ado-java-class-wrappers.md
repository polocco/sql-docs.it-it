---
description: Wrapper di classe Java ADO
title: Wrapper della classe Java ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- class wrappers [ADO]
ms.assetid: 1fc09dc1-9e32-412e-9f43-b8eb8bb483ca
author: rothja
ms.author: jroth
ms.openlocfilehash: 1694c3782aa57993cee39ea4f449e7b280fccdf6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991191"
---
# <a name="ado-java-class-wrappers"></a>Wrapper di classe Java ADO
Questo codice dichiara un'istanza del wrapper della classe [Recordset](../../reference/ado-api/recordset-object-ado.md) ADO e la inizializza, all sulla stessa riga di codice. Dichiara inoltre le variabili per ogni argomento nel metodo [Open](../../reference/ado-api/open-method-ado-recordset.md) , specialmente per [LockType](../../reference/ado-api/locktype-property-ado.md) e [CursorType](../../reference/ado-api/cursortype-property-ado.md) (perché Java non supporta i tipi enumerati). Viene aperto e chiuso l'oggetto **Recordset** . Impostando RS1 su NULL si pianifica semplicemente la variabile da rilasciare quando Java esegue la versione sistematica e intermittente degli oggetti inutilizzati.  
  
```java
public static void main( String args[])  
{  
   msado15._Recordset   Rs1 = new msado15.Recordset();  
   Variant Source     = new Variant( "SELECT * FROM Authors" );  
   Variant Connect    = new Variant( "DSN=AdoDemo;UID=admin;PWD=;" );  
   int     LockType   = msado15.CursorTypeEnum.adOpenForwardOnly;  
   int     CursorType = msado15.LockTypeEnum.adLockReadOnly;  
   int     Options    = -1;  
  
   Rs1.Open( Source, Connect, LockType,  CursorType, Options );  
   Rs1.Close();  
   Rs1 = null;  
  
   System.out.println( "Success!\n" );  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Microsoft SDK per Java](./using-the-microsoft-sdk-for-java.md)