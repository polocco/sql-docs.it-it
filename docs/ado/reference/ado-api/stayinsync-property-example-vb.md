---
title: Esempio di proprietà StayInSync (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- StayInSync property [ADO], Visual Basic example
ms.assetid: b682bcc3-04b3-42b0-86f4-c17e0cd29baf
author: rothja
ms.author: jroth
ms.openlocfilehash: 5fa4c09a56f164ca8c0d2b6d6222b9d827c1ee45
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759677"
---
# <a name="stayinsync-property-example-vb"></a>Esempio della proprietà StayInSync (VB)
In questo esempio viene illustrato il modo in cui la proprietà [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) facilita l'accesso alle righe in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)gerarchico.  
  
 Il ciclo esterno Visualizza il nome, lo stato e l'identificazione di ogni autore. Il **Recordset** aggiunto per ogni riga viene recuperato dalla raccolta [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) e assegnato automaticamente a **rstTitleAuthor** dalla proprietà **StayInSync** ogni volta che il **Recordset** padre si sposta in una nuova riga. Il ciclo interno Visualizza quattro campi da ogni riga del Recordset accodato.  
  
```  
'BeginStayInSyncVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim Cnxn As ADODB.Connection  
    Dim rst As ADODB.Recordset  
    Dim rstTitleAuthor As New ADODB.Recordset  
    Dim strCnxn As String  
  
    ' Open the connection with Data Shape attributes  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider=MSDataShape;Data Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Create a recordset  
    Set rst = New ADODB.Recordset  
    rst.StayInSync = True  
    rst.Open "SHAPE {select * from Authors} " & _  
                   "APPEND ( { select * from titleauthor} AS chapTitleAuthor " & _  
                   "RELATE au_id TO au_id) ", Cnxn, , , adCmdText  
  
    Set rstTitleAuthor = rst("chapTitleAuthor").Value  
    Do Until rst.EOF  
        Debug.Print rst!au_fname & " " & rst!au_lname & " " & _  
                   rst!State & " " & rst!au_id  
  
        Do Until rstTitleAuthor.EOF  
            Debug.Print rstTitleAuthor(0) & " " & rstTitleAuthor(1) & " " & _  
                   rstTitleAuthor(2) & " " & rstTitleAuthor(3)  
            rstTitleAuthor.MoveNext  
        Loop  
  
        rst.MoveNext  
    Loop  
  
    ' Clean up  
    rst.Close  
    Cnxn.Close  
    Set rst = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' Clean up  
    If Not rst Is Nothing Then  
        If rst.State = adStateOpen Then rst.Close  
    End If  
    Set rst = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndStayInSyncVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Oggetto recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Proprietà StayInSync](../../../ado/reference/ado-api/stayinsync-property.md)
