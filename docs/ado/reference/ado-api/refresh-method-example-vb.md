---
description: Esempio del metodo Refresh (VB)
title: Esempio di metodo Refresh (VB) | Microsoft Docs
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
- Refresh method [ADO], Visual Basic example
ms.assetid: f5375fa1-4711-4f7e-9ba4-54c427f71325
author: rothja
ms.author: jroth
ms.openlocfilehash: 168bdaa7736c5f9d3c974d0a5f6aa4fae2b323bc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442343"
---
# <a name="refresh-method-example-vb"></a>Esempio del metodo Refresh (VB)
Questo esempio illustra l'uso del metodo [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) per aggiornare la raccolta [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) per un oggetto stored procedure [comando](../../../ado/reference/ado-api/command-object-ado.md) .  
  
```vb
'BeginRefreshVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection strings  
  
    ' connection and recordset variables  
    Dim Cnxn As ADODB.Connection  
    Dim cmdByRoyalty As ADODB.Command  
    Dim rstByRoyalty As ADODB.Recordset  
    Dim rstAuthors As ADODB.Recordset  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
     ' record variables  
    Dim intRoyalty As Integer  
    Dim strAuthorID As String  
    Dim strRoyalty As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Open a command object for a stored procedure  
    ' with one parameter  
    Set cmdByRoyalty = New ADODB.Command  
    Set cmdByRoyalty.ActiveConnection = Cnxn  
    cmdByRoyalty.CommandText = "byroyalty"  
    cmdByRoyalty.CommandType = adCmdStoredProc  
    cmdByRoyalty.Parameters.Refresh  
  
    ' Get parameter value, execute the command  
    ' and store the results in a recordset  
    strRoyalty = InputBox("Enter royalty:")  
    If strRoyalty = "" Then  
        Err.Raise 1, , "You either didn't enter royalty or canceled the input box. Exit the application"  
    End If  
  
    intRoyalty = Trim(strRoyalty)  
    cmdByRoyalty.Parameters(1) = intRoyalty  
    Set rstByRoyalty = cmdByRoyalty.Execute()  
  
    ' Open the Authors table to get author names for display  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenForwardOnly, adLockPessimistic, adCmdTable  
  
    ' Print current data in the recordset  
    ' and add author names  
    Debug.Print "Authors with " & intRoyalty & " percent royalty"  
  
    Do Until rstByRoyalty.EOF  
        strAuthorID = rstByRoyalty!au_id  
        Debug.Print "   " & rstByRoyalty!au_id & ", ";  
        rstAuthors.Filter = "au_id = '" & strAuthorID & "'"  
        Debug.Print rstAuthors!au_fname & " "; rstAuthors!au_lname  
        rstByRoyalty.MoveNext  
    Loop  
  
    ' clean up  
    rstByRoyalty.Close  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstByRoyalty = Nothing  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstByRoyalty Is Nothing Then  
        If rstByRoyalty.State = adStateOpen Then rstByRoyalty.Close  
    End If  
    Set rstByRoyalty = Nothing  
  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndRefreshVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Raccolta Parameters (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Metodo Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)
