---
description: 'Esempio di codice ADOX: esempio delle proprietà NumericScale e Precision (VB)'
title: Esempio di codice di proprietà NumericScale e Precision ADOX (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Precision property [ADOX], Visual Basic example
- NumericScale property [ADOX], Visual Basic example
ms.assetid: ea2ec614-34c8-41b7-8ebd-063798bd56b4
author: rothja
ms.author: jroth
ms.openlocfilehash: 92ebc6f3d861251d197686a00df54ee88b145dd8
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88985782"
---
# <a name="adox-code-example-numericscale-and-precision-properties-example-vb"></a>Esempio di codice ADOX: esempio delle proprietà NumericScale e Precision (VB)
In questo esempio vengono illustrate le proprietà [NumericScale](./numericscale-property-adox.md) e [Precision](./precision-property-adox.md) dell'oggetto [Column](./column-object-adox.md) . Questo codice Visualizza il relativo valore per la tabella **Order Details** del database *Northwind* .  
  
```  
' BeginNumericScalePrecVB  
Sub Main()  
    On Error GoTo NumericScalePrecXError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim tblOD As ADOX.Table  
    Dim colLoop As ADOX.Column  
  
    ' Connect the catalog.  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "data source='Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
  
    ' Retrieve the Order Details table  
    Set tblOD = cat.Tables("Order Details")  
  
    ' Display numeric scale and precision of  
    ' small integer fields.  
    For Each colLoop In tblOD.Columns  
        If colLoop.Type = adSmallInt Then  
            MsgBox "Column: " & colLoop.Name & vbCr & _  
                "Numeric scale: " & _  
                colLoop.NumericScale & vbCr & _  
                "Precision: " & colLoop.Precision  
        End If  
    Next colLoop  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
NumericScalePrecXError:  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndNumericScalePrecVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Column (ADOX)](./column-object-adox.md)   
 [Proprietà NumericScale (ADOX)](./numericscale-property-adox.md)   
 [Proprietà Precision (ADOX)](./precision-property-adox.md)