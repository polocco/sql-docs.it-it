---
title: Esempio di proprietà AbsolutePosition e CursorLocation (JScript) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- AbsolutePosition property [ADO], JScript example
- CursorLocation property [ADO], JScript example
ms.assetid: bff98617-a6ba-4f41-9c5f-915161e3ea31
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9f80cd4683928bcb1be74af9f80c00f4324ebfac
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "67921791"
---
# <a name="absoluteposition-and-cursorlocation-properties-example-jscript"></a>Esempio di proprietà AbsolutePosition e CursorLocation (JScript)
In questo esempio viene illustrato il modo in cui la proprietà [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) è in grado di tenere traccia dello stato di avanzamento di un ciclo che enumera tutti i record di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Usa la proprietà [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) per abilitare la proprietà **AbsolutePosition** impostando il cursore su un cursore client. Tagliare e incollare il codice seguente nel blocco note o in un altro editor di testo e salvarlo come **AbsolutePositionJS. asp**.  
  
```  
<!-- BeginAbsolutePositionJS -->  
<%@LANGUAGE="JScript" %>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<html>  
  
<head>  
<title>AbsolutePosition and CursorLocation Properties Example (JScript)</title>  
<style>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</head>  
  
<body>  
<h1>AbsolutePosition and CursorLocation Properties Example (JScript)</h1>  
<%  
    // connection and recordset variables  
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='Northwind';Integrated Security='SSPI';";  
    var rsEmployee = Server.CreateObject("ADODB.Recordset");  
        // display string  
    var strMessage;          
  
    try  
    {  
        // Open a recordset on the Employee table using  
        // a client-side cursor to enable AbsolutePosition property.  
        rsEmployee.CursorLocation = adUseClient;  
        rsEmployee.Open("employees", strCnxn, adOpenStatic, adLockOptimistic, adCmdTable);  
  
        // Write beginning of table to the document.  
        Response.Write('<table border="0" align="center">');  
        Response.Write('<tr class="thead2">');  
        Response.Write("<th>AbsolutePosition</th><th>Name</th><th>Hire Date</th></tr>");  
  
        while (!rsEmployee.EOF)  
        {  
            strMessage = "";  
  
            // Start a new table row.  
            strMessage = '<tr class="tbody">';  
  
            // First column in row contains AbsolutePosition value.  
            strMessage += "<td>" + rsEmployee.AbsolutePosition + " of " + rsEmployee.RecordCount + "</td>"  
  
            // First and last name are in first column.  
            strMessage += "<td>" + rsEmployee.Fields("FirstName") + " ";  
            strMessage += rsEmployee.Fields("LastName") + " " + "</td>";  
  
            // Hire date in second column.  
            strMessage += "<td>" + rsEmployee.Fields("HireDate") + "</td>";  
  
            // End the row.  
            strMessage += "</tr>";  
  
            // Write line to document.  
            Response.Write(strMessage);  
  
            // Get next record.  
            rsEmployee.MoveNext;  
        }  
  
        // Finish writing document.  
        Response.Write("</table>");  
    }  
    catch (e)  
    {  
        Response.Write(e.message);  
    }  
    finally  
    {  
        // 'clean up  
        if (rsEmployee.State == adStateOpen)  
            rsEmployee.Close;  
        rsEmployee = null;  
    }  
%>  
  
</html>  
<!-- EndAbsolutePositionJS -->  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [Proprietà CursorLocation (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)   
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
