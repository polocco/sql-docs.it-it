---
description: 'Passaggio 4: Popolare la casella di riepilogo Details'
title: 'Passaggio 4: popolare la casella di testo Dettagli | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
author: rothja
ms.author: jroth
ms.openlocfilehash: 868066b8225a3e87a2aad37ddd7569cc5be6bd75
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979482"
---
# <a name="step-4-populate-the-details-text-box"></a>Passaggio 4: Popolare la casella di riepilogo Details
Per popolare la casella di testo dettagli, creare una nuova subroutine denominata **recFields** e inserire il codice seguente:  
  
```  
Sub recFields(r As Record, l As ListBox, t As TextBox)  
    Dim f As Field  
    Dim s As Stream  
    Set s = New Stream  
    Dim str As String  
  
    For Each f In r.Fields  
        l.AddItem f.Name & ": " & f.Value  
    Next  
    t.Text = ""  
    If r!RESOURCE_CONTENTCLASS = "text/plain" Then  
        s.Open r, adModeRead, adOpenStreamFromRecord  
        str = s.ReadText(1)  
        s.Position = 0  
        If Asc(Mid(str, 1, 1)) = 63 Then '//63 = "?"  
            s.Charset = "ascii"  
            s.Type = adTypeText  
        End If  
        t.Text = s.ReadText(adReadAll)  
    End If  
End Sub  
```  
  
 Questo codice viene popolato `lstDetails` con i campi e i valori del record semplice passato a `recFields` . Se la risorsa è un file di testo, viene aperto un flusso di testo dal record di risorse. Il codice determina se il set di caratteri è ASCII e copia il contenuto del flusso in `txtDetails` .  
  
## <a name="see-also"></a>Vedere anche  
 [Scenario di pubblicazione Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Passaggio 3: Popolare la casella di riepilogo Fields](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
