---
title: Esempio di metodi Append e CreateParameter (JScript) | Microsoft Docs
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
- CreateParameter method [ADO], JScript example
- Append method [ADO], JScript example
ms.assetid: 37000833-68f4-45f1-b2dd-7f75893d09d9
author: rothja
ms.author: jroth
ms.openlocfilehash: 048a54ab758304bbfef50ffb1eaa98254b4fd496
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747004"
---
# <a name="append-and-createparameter-methods-example-jscript"></a>Esempio di metodi Append e CreateParameter (JScript)
In questo esempio vengono utilizzati i metodi [Append](../../../ado/reference/ado-api/append-method-ado.md) e [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) per eseguire una stored procedure con un parametro di input. Tagliare e incollare il codice seguente nel blocco note o in un altro editor di testo e salvarlo come **AppendJS. asp**.  
  
```  
<!-- BeginAppendJS -->  
<%@LANGUAGE="JScript" %>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<html>  
<head>  
    <title>Append and CreateParameter Methods Example (JScript)</title>  
<style>  
<!--  
body {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
-->  
</style>  
</head>  
  
<body>  
<h1>Append and CreateParameter Methods Example (JScript)</h1>  
<%  
    // verify user-input   
    var iRoyalty = parseInt(Request.Form("RoyaltyValue"));  
    if (iRoyalty > -1)  
    {  
  
        // connection, recordset and command variables  
        var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='pubs';Integrated Security='SSPI';";  
        var Cnxn = Server.CreateObject("ADODB.Connection");  
        var cmdByRoyalty = Server.CreateObject("ADODB.Command");  
        var rsByRoyalty = Server.CreateObject("ADODB.Recordset");  
        var rsAuthor = Server.CreateObject("ADODB.Recordset");  
        // display variables  
        var strMessage;  
  
        try  
        {  
            // open connection and set cursor location  
            Cnxn.Open(strCnxn);  
            Cnxn.CursorLocation = adUseClient;  
  
            // command object initial parameters  
            cmdByRoyalty.CommandText = "byroyalty";  
            cmdByRoyalty.CommandType = adCmdStoredProc;  
  
            // create the new parameter and append to  
            // the Command object's parameters collection  
            var prmByRoyalty = cmdByRoyalty.CreateParameter("percentage", adInteger, adParamInput);  
            cmdByRoyalty.Parameters.Append(prmByRoyalty);  
            prmByRoyalty.Value = iRoyalty;  
  
            cmdByRoyalty.ActiveConnection = Cnxn;  
  
            // execute command  
            rsByRoyalty = cmdByRoyalty.Execute();  
  
            // display results  
            rsAuthor.Open("Authors", Cnxn);  
  
            while (!rsByRoyalty.EOF)  
            {  
                rsAuthor.Filter = "au_id='" + rsByRoyalty.Fields("au_id") + "'";  
  
                // start new line  
                strMessage = "<P>";  
  
                // recordset data  
                strMessage += rsAuthor.Fields("au_fname") + " ";   
                strMessage += rsAuthor.Fields("au_lname") + " ";  
  
                // end the line  
                strMessage += "</P>";  
  
                // show result  
                Response.Write(strMessage);  
  
                // et next record  
                rsByRoyalty.MoveNext;  
            }  
        }  
        catch (e)  
        {  
            Response.Write(e.message);  
        }  
        finally  
        {  
            // clean up  
            if (rsByRoyalty.State == adStateOpen)  
                rsByRoyalty.Close;  
            if (rsAuthor.State == adStateOpen)  
                rsAuthor.Close;  
            if (Cnxn.State == adStateOpen)  
                Cnxn.Close;  
            rsByRoyalty = null;  
            rsAuthor = null;  
            Cnxn = null;  
        }  
    }  
%>  
  
<hr>  
  
<form method="POST" action="AppendJS.asp" id=form1 name=form1>  
  <p align="left">Enter royalty percentage to find (e.g., 40): <input type="text" name="RoyaltyValue" size="5"></p>  
  <p align="left"><input type="submit" value="Submit" name="B1"><input type="reset" value="Reset" name="B2"></p>  
</form>  
  
</body>  
  
</html>  
<!-- EndAppendJS -->  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Metodo CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Field (oggetto)](../../../ado/reference/ado-api/field-object.md)   
 [Raccolta Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Oggetto Parameter](../../../ado/reference/ado-api/parameter-object.md)
