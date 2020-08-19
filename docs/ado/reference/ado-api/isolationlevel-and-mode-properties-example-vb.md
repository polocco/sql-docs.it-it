---
description: Esempio di proprietà IsolationLevel e Mode (VB)
title: Esempio di proprietà IsolationLevel e Mode (VB) | Microsoft Docs
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
- Mode property [ADO], Visual Basic example
- IsolationLevel property [ADO], Visual Basic example
ms.assetid: 3382fd41-0aa1-4091-97d3-624403111e07
author: rothja
ms.author: jroth
ms.openlocfilehash: acbf64eca7aa7b0ccbd943d261968f8a70c8f9e1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443443"
---
# <a name="isolationlevel-and-mode-properties-example-vb"></a>Esempio di proprietà IsolationLevel e Mode (VB)
In questo esempio viene utilizzata la proprietà [mode](../../../ado/reference/ado-api/mode-property-ado.md) per aprire una connessione esclusiva e la proprietà [IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md) per aprire una transazione eseguita in isolamento di altre transazioni.  
  
```  
'BeginIsolationLevelVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim Cnxn As ADODB.Connection  
    Dim rstTitles As ADODB.Recordset  
    Dim strCnxn As String  
    Dim strSQLTitles As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Mode = adModeShareExclusive  
    Cnxn.IsolationLevel = adXactIsolated  
    Cnxn.Open strCnxn  
  
     ' open Titles table  
    Set rstTitles = New ADODB.Recordset  
    strSQLTitles = "titles"  
    rstTitles.Open strSQLTitles, Cnxn, adOpenDynamic, adLockPessimistic, adCmdTable  
  
    Cnxn.BeginTrans  
  
    ' Display connection mode  
    If Cnxn.Mode = adModeShareExclusive Then  
        MsgBox "Connection mode is exclusive."  
    Else  
        MsgBox "Connection mode is not exclusive."  
    End If  
  
    ' Display isolation level  
    If Cnxn.IsolationLevel = adXactIsolated Then  
        MsgBox "Transaction is isolated."  
    Else  
        MsgBox "Transaction is not isolated."  
    End If  
  
    ' Change the type of psychology titles  
    Do Until rstTitles.EOF  
        If Trim(rstTitles!Type) = "psychology" Then  
            rstTitles!Type = "self_help"  
            rstTitles.Update  
        End If  
        rstTitles.MoveNext  
    Loop  
  
    ' Print current data in recordset  
    rstTitles.Requery  
    Do While Not rstTitles.EOF  
        Debug.Print rstTitles!Title & " - " & rstTitles!Type  
        rstTitles.MoveNext  
    Loop  
  
    ' clean up  
    rstTitles.Close  
    Cnxn.RollbackTrans  
    Cnxn.Close  
    Set rstTitles = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstTitles Is Nothing Then  
        If rstTitles.State = adStateOpen Then rstTitles.Close  
    End If  
    Set rstTitles = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then  
            Cnxn.RollbackTrans  
            Cnxn.Close  
        End If  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndIsolationLevelVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [IsolationLevel (proprietà)](../../../ado/reference/ado-api/isolationlevel-property.md)   
 [Proprietà Mode (ADO)](../../../ado/reference/ado-api/mode-property-ado.md)
