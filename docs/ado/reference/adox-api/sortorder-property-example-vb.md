---
description: Esempio della proprietà SortOrder (VB)
title: Esempio di proprietà SortOrder (VB) | Microsoft Docs
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
- SortOrder property [ADOX]
ms.assetid: d9502254-d89b-4bcb-94f1-6418f89e7f30
author: rothja
ms.author: jroth
ms.openlocfilehash: 089c4e7f402e374ab4af43c683270ad488c0f8bb
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769360"
---
# <a name="sortorder-property-example-vb"></a>Esempio della proprietà SortOrder (VB)
In questo esempio viene illustrata la proprietà [SortOrder](./sortorder-property-adox.md) di una [colonna](./column-object-adox.md) aggiunta alla raccolta [Columns](./columns-collection-adox.md) di un [Indice](./index-object-adox.md). Il codice aggiunge un indice crescente alla colonna Country della tabella **Employees** , quindi Visualizza i record. Il codice aggiunge quindi un indice decrescente alla colonna Country della tabella **Employees** e visualizza nuovamente i record. Viene visualizzata la differenza tra gli indici crescente e decrescente.  
  
```  
' BeginSortOrderVB  
Sub Main()  
    On Error GoTo SortOrderXError  
  
    Dim cnn As New ADODB.Connection  
    Dim catNorthwind As New ADOX.Catalog  
    Dim idxAscending As New ADOX.Index  
    Dim idxDescending As New ADOX.Index  
    Dim rstEmployees As New ADODB.Recordset  
  
    ' Connect to the catalog.  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
    Set catNorthwind.ActiveConnection = cnn  
  
    ' Append Country column to new index.  
    idxAscending.Columns.Append "Country"  
    idxAscending.Columns("Country").SortOrder = adSortAscending  
    idxAscending.Name = "Ascending"  
    idxAscending.IndexNulls = adIndexNullsAllow  
  
    'Append new index to Employees table.  
    catNorthwind.Tables("Employees").Indexes.Append idxAscending  
  
    rstEmployees.Index = idxAscending.Name  
    rstEmployees.Open "Employees", cnn, adOpenKeyset, _  
        adLockOptimistic, adCmdTableDirect  
  
    With rstEmployees  
        .MoveFirst  
        Debug.Print "Index = " & .Index  
        Debug.Print "  Country - Name"  
  
        ' Enumerate the Recordset. The value of the  
        ' IndexNulls property will determine if the newly  
        ' added record appears in the output.  
        Do While Not .EOF  
            Debug.Print "    " & !Country & " - " & _  
                !FirstName & " " & !LastName  
            .MoveNext  
        Loop  
  
        .Close  
    End With  
  
    ' Append Country column to new index.  
    idxDescending.Columns.Append "Country"  
    idxDescending.Columns("Country").SortOrder = adSortDescending  
    idxDescending.Name = "Descending"  
    idxDescending.IndexNulls = adIndexNullsAllow  
  
    'Append descending index to Employees table.  
    catNorthwind.Tables("Employees").Indexes.Append idxDescending  
  
    rstEmployees.Index = idxDescending.Name  
    rstEmployees.Open "Employees", cnn, adOpenKeyset, _  
        adLockOptimistic, adCmdTableDirect  
  
    With rstEmployees  
        .MoveFirst  
        Debug.Print "Index = " & .Index  
        Debug.Print "  Country - Name"  
  
        ' Enumerate the Recordset. The value of the  
        ' IndexNulls property will determine if the newly  
        ' added record appears in the output.  
        Do While Not .EOF  
            Debug.Print "    " & !Country & " - " & _  
                !FirstName & " " & !LastName  
            .MoveNext  
        Loop  
  
        .Close  
    End With  
  
    ' Delete new indexes because this is a demonstration.  
    catNorthwind.Tables("Employees").Indexes.Delete idxAscending.Name  
    catNorthwind.Tables("Employees").Indexes.Delete idxDescending.Name  
  
    'Clean up  
    cnn.Close  
    Set catNorthwind = Nothing  
    Set idxAscending = Nothing  
    Set idxDescending = Nothing  
    Set rstEmployees = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
SortOrderXError:  
  
    Set catNorthwind = Nothing  
    Set idxAscending = Nothing  
    Set idxDescending = Nothing  
  
    If Not rstEmployees Is Nothing Then  
        If rstEmployees.State = adStateOpen Then rstEmployees.Close  
    End If  
    Set rstEmployees = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndSortOrderVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Column (ADOX)](./column-object-adox.md)   
 [Raccolta Columns (ADOX)](./columns-collection-adox.md)   
 [Oggetto index (ADOX)](./index-object-adox.md)   
 [Proprietà SortOrder (ADOX)](./sortorder-property-adox.md)