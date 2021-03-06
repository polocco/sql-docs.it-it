---
description: Metodo Append (raccolta Users ADOX)
title: Metodo Append (utenti ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Users::raw_Append
- Users::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: b80bc5d5-78ca-4f75-956b-2ac658029cc7
author: rothja
ms.author: jroth
ms.openlocfilehash: 14b0c573b3ccf8a03b1c2f6513cdac67303fb4bf
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985432"
---
# <a name="append-method-adox-users"></a>Metodo Append (raccolta Users ADOX)
Aggiunge un nuovo oggetto [utente](./user-object-adox.md) alla raccolta [Users](./users-collection-adox.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Users.Append User[,Password]  
```  
  
#### <a name="parameters"></a>Parametri  
 *User*  
 Valore **Variant** che contiene l'oggetto **utente** da accodare o il nome dell'utente da creare e accodare.  
  
 *Password*  
 Facoltativa. Valore **stringa** che contiene la password per l'utente. Il parametro *password* corrisponde al valore specificato dal metodo [ChangePassword](./changepassword-method-adox.md) di un oggetto **utente** .  
  
## <a name="remarks"></a>Osservazioni  
 La raccolta **Users** di un [Catalogo](./catalog-object-adox.md) rappresenta tutti gli utenti del catalogo. La raccolta **Users** per un [gruppo](./group-object-adox.md) rappresenta solo gli utenti che dispongono di un'appartenenza al gruppo specifico.  
  
 Se il provider non supporta la creazione di utenti, si verificherà un errore.  
  
> [!NOTE]
>  Prima di aggiungere un oggetto **utente** alla raccolta **Users** di un oggetto **gruppo** , deve esistere già un oggetto **utente** con lo stesso [nome](./name-property-adox.md) di quello da accodare nella raccolta **Users** del **Catalogo**.  
  
## <a name="applies-to"></a>Si applica a  
 [Raccolta Users (ADOX)](./users-collection-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Accodamento di gruppi e utenti, esempio di Metodi ChangePassword (VB)](./groups-and-users-append-changepassword-methods-example-vb.md)   
 [Metodo Append (colonne ADOX)](./append-method-adox-columns.md)   
 [Metodo Append (gruppi ADOX)](./append-method-adox-groups.md)   
 [Metodo Append (indici ADOX)](./append-method-adox-indexes.md)   
 [Metodo Append (chiavi ADOX)](./append-method-adox-keys.md)   
 [Metodo Append (routine ADOX)](./append-method-adox-procedures.md)   
 [Metodo Append (tabelle ADOX)](./append-method-adox-tables.md)   
 [Metodo Append (raccolta Views ADOX)](./append-method-adox-views.md)