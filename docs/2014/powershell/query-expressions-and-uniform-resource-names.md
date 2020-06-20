---
title: Espressioni di query e Uniform Resource Name | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- query expressions
- unique resource names
- URN
ms.assetid: e0d30dbe-7daf-47eb-8412-1b96792b6fb9
author: stevestein
ms.author: sstein
ms.openlocfilehash: e53b659fdd5d572d4f76e9a1979e6639ea33d060
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84960184"
---
# <a name="query-expressions-and-uniform-resource-names"></a>Espressioni di query e Uniform Resource Name
  I modelli SMO ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object) e gli snap-in PowerShell per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] usano due tipi di stringhe di espressione simili alle espressioni XPath. Le espressioni di query sono stringhe che specificano un set di criteri utilizzato per enumerare uno o più oggetti in una gerarchia del modello a oggetti. Un Unique Resource Name (URN) è un tipo specifico di stringa di espressione di query che identifica un singolo oggetto in modo univoco.  
  
## <a name="syntax"></a>Sintassi  
  
```
      Object1  
      [<FilterExpression1>]/ ... /ObjectN[<FilterExpressionN>]<FilterExpression>::=  
<PropertyExpression> [and <PropertyExpression>][...n]  
  
<PropertyExpression>::=@BooleanPropertyName=true()  
 | @BooleanPropertyName=false()  
 | contains(@StringPropertyName, 'PatternString')  
  | @StringPropertyName='String'  
 | @DatePropertyName=datetime('DateString')  
 | is_null(@PropertyName)  
 | not(<PropertyExpression>)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Object*  
 Specifica il tipo di oggetto che è rappresentato in corrispondenza del nodo della stringa di espressione. Ciascun oggetto rappresenta una classe di raccolte dai seguenti spazi dei nomi del modello a oggetti SMO:  
  
 <xref:Microsoft.SqlServer.Management.Smo>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Agent>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Broker>  
  
 <xref:Microsoft.SqlServer.Management.Smo.Mail>  
  
 <xref:Microsoft.SqlServer.Management.Dmf>  
  
 <xref:Microsoft.SqlServer.Management.Facets>  
  
 <xref:Microsoft.SqlServer.Management.RegisteredServers>  
  
 <xref:Microsoft.SqlServer.Management.Smo.RegSvrEnum>  
  
 Ad esempio, specificare Server per la classe **ServerCollection** , Database per la classe **DatabaseCollection** .  
  
 \@*PropertyName*  
 Specifica il nome di una delle proprietà della classe associato all'oggetto specificato in *Object*. Il nome della proprietà deve essere preceduto dal carattere \@. Ad esempio, specificare \@ IsAnsiNull per la proprietà della classe di **database** **IsAnsiNull**.  
  
 \@*BooleanPropertyName*=true()  
 Enumera tutti gli oggetti in cui la proprietà Boolean specificata è impostata su TRUE.  
  
 \@*BooleanPropertyName*=false()  
 Enumera tutti gli oggetti in cui la proprietà Boolean specificata è impostata su FALSE.  
  
 Contains ( \@ *StringtPropertyName*,'*PatternString*')  
 Enumera tutti gli oggetti in cui la proprietà della stringa specificata contiene almeno un'occorrenza del set di caratteri specificato in '*PatternString*'.  
  
 \@*StringPropertyName*='*PatternString*'  
 Enumera tutti gli oggetti in cui il valore della proprietà della stringa specificata è esattamente uguale al modello di caratteri specificato in '*PatternString*'.  
  
 \@*DatePropertyName*= datetime('*DateString*')  
 Enumera tutti gli oggetti in cui il valore della proprietà Date specificata corrisponde alla data specificata in '*DateString*'. *DateString* deve essere nel formato aaaa-mm-gg oo:mi:ss.mmm  
  
|||  
|-|-|  
|aaaa|Anno espresso a quattro cifre.|  
|MM|Mese a due cifre (da 01 a 12)|  
|gg|Data a due cifre (da 01 a 31)|  
|hh|Ora a 2 cifre nel formato a 24 ore (da 01 a 23)|  
|mi|Minuti a due cifre (da 01 a 59)|  
|ss|Secondi a due cifre (da 01 a 59)|  
|mmm|Numero di millisecondi (da 001 a 999).|  
  
 Le date specificate in questo formato possono essere valutate rispetto a qualsiasi formato della data archiviato in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 is_null ( \@ *PropertyName*)  
 Enumera tutti gli oggetti in cui la proprietà specificata è impostata su NULL.  
  
 Not ( \<*PropertyExpression*> )  
 Nega il valore della valutazione della *PropertyExpression*, enumerando tutti gli oggetti che non corrispondono alla condizione specificata nella *PropertyExpression*. Ad esempio, not(contains(\@Name, 'xyz')) enumera tutti gli oggetti i cui nomi non contengono la stringa xyz.  
  
## <a name="remarks"></a>Commenti  
 Le espressioni di query sono stringhe che enumerano i nodi in una gerarchia del modello SMO. Ciascun nodo dispone di un'espressione di filtro che specifica i criteri per determinare quali oggetti in corrispondenza di un dato nodo sono enumerati. Le espressioni di query vengono modellate sul linguaggio delle espressioni XPath. Le espressioni di query implementano un piccolo subset delle espressioni che sono supportate da XPath; inoltre dispongono di alcune estensioni che non si trovano in XPath. Le espressioni XPath sono stringhe che specificano un set di criteri che vengono utilizzati per enumerare uno o più tag in un documento XML. Per altre informazioni su XPath, vedere [W3C XPath Language](http://www.w3.org/TR/xpath20/).  
  
 Le espressioni di query devono iniziare con un riferimento assoluto all'oggetto Server. Le espressioni relative con un carattere "/" iniziale non sono consentite. La sequenza di oggetti che sono specificati in un'espressione di query deve seguire la gerarchia di oggetti Collection nel modello a oggetti associato. Ad esempio, un'espressione di query che fa riferimento a oggetti nello spazio dei nomi Microsoft.SqlServer.Management.Smo deve iniziare con un nodo Server seguito da un nodo Database e così via.  
  
 Se *\<FilterExpression>* non si specifica un oggetto per un oggetto, vengono enumerati tutti gli oggetti in tale nodo.  
  
## <a name="uniform-resource-names-urn"></a>Unique Resource Name (URN)  
 Gli URN sono un subset di espressioni di query. Ciascun URN rappresenta un riferimento completo a un oggetto singolo. Il tipico URN utilizza la proprietà Name per identificare un singolo oggetto in corrispondenza di ciascun nodo. Ad esempio, questo URN si riferisce a una colonna specifica:  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']/Table[@Name='SalesPerson' and @Schema='Sales']/Column[@Name='SalesPersonID']  
```  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-enumerating-objects-using-false"></a>R. Enumerazione di oggetti utilizzando false()  
 Questa espressione di query enumera tutti i database il cui attributo **AutoClose** è impostato su False nell'istanza predefinita in **MyComputer**.  
  
```  
Server[@Name='MYCOMPUTER']/Database[@AutoClose=false()]  
```  
  
### <a name="b-enumerating-objects-using-contains"></a>B. Enumerazione di oggetti utilizzando contains  
 Questa espressione di query enumera tutti i database per quali non viene fatta distinzione tra maiuscole e minuscole e i cui nomi contengono il carattere "m".  
  
```  
Server[@Name='MYCOMPUTER']/Database[@CaseSensitive=false() and contains(@Name, 'm')]   
```  
  
### <a name="c-enumerating-objects-using-not"></a>C. Enumerazione di oggetti utilizzando not  
 Questa espressione di query enumera tutte le tabelle di [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] che non sono nello schema **Production** e i cui nomi contengono la parola History:  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']/Table[not(@Schema='Production') and contains(@Name, 'History')]  
```  
  
### <a name="d-not-supplying-a-filter-expression-for-the-final-node"></a>D. Mancata specifica di un'espressione di filtro per il nodo finale  
 Questa espressione di query enumera tutte le colonne nella tabella **AdventureWorks2012.Sales.SalesPerson** :  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[@Schema='Sales' and @Name='SalesPerson']/Columns  
```  
  
### <a name="e-enumerating-objects-using-datetime"></a>E. Enumerazione di oggetti utilizzando datetime  
 Questa espressione di query enumera tutte le tabelle create nel database [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] a un'ora specifica:  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[@CreateDate=datetime('2008-03-21 19:49:32.647')]  
```  
  
### <a name="f-enumerating-objects-using-is_null"></a>F. Enumerazione di oggetti utilizzando is_null  
 Questa espressione di query enumera tutte le tabelle nel database [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] le cui proprietà di data ultima modifica non sono impostate su NULL:  
  
```  
Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012"]/Table[Not(is_null(@DateLastModified))]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Cmdlet Invoke-PolicyEvaluation](../database-engine/invoke-policyevaluation-cmdlet.md)   
 [SQL Server Audit &#40;Database Engine&#41;](../relational-databases/security/auditing/sql-server-audit-database-engine.md)  
