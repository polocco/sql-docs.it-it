---
title: PDOStatement::getColumnMeta
description: Informazioni di riferimento sulle API per la funzione PDOStatement::getColumnMeta nel driver Microsoft PDO_SQLSRV per PHP per SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c92a21cc-8e53-43d0-a4bf-542c77c100c9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b76e7c6201226c13ae057e8ac182b7ab0a9c6b13
ms.sourcegitcommit: 7eb80038c86acfef1d8e7bfd5f4e30e94aed3a75
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2020
ms.locfileid: "92082020"
---
# <a name="pdostatementgetcolumnmeta"></a>PDOStatement::getColumnMeta
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Recupera i metadati per una colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array PDOStatement::getColumnMeta ( $column );  
```  
  
#### <a name="parameters"></a>Parametri  
*$conn*: (intero) numero in base zero della colonna di cui si vuole recuperare i metadati.  
  
## <a name="return-value"></a>Valore restituito  
Una matrice associativa (chiave e valore) che contiene i metadati per la colonna. Vedere la sezione Osservazioni per una descrizione dei campi nella matrice.  
  
## <a name="remarks"></a>Osservazioni  
Nella tabella seguente sono descritti i campi della matrice restituita da getColumnMeta.  
  
|NOME|VALUES|  
|--------|----------|  
|native_type|Specifica il tipo PHP per la colonna. Sempre stringa.|  
|driver:decl_type|Specifica il tipo SQL usato per rappresentare il valore della colonna nel database. Se la colonna nel set di risultati è il risultato di una funzione, questo valore non viene restituito da PDOStatement::getColumnMeta.|  
|flags|Specifica i flag impostati per la colonna. Sempre 0.|  
|name|Specifica il nome della colonna nel database.|  
|table|Specifica il nome della tabella contenente la colonna nel database. Sempre vuoto.|  
|len|Specifica la lunghezza della colonna.|  
|precisione|Specifica la precisione numerica della colonna.|  
|pdo_type|Specifica il tipo della colonna come rappresentato dalle costanti PDO::PARAM_*. Sempre PDO::PARAM_STR (2).|  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$stmt = $conn->query("select * from Person.ContactType");  
$metadata = $stmt->getColumnMeta(2);  
var_dump($metadata);  
  
print $metadata['sqlsrv:decl_type'] . "\n";  
print $metadata['native_type'] . "\n";  
print $metadata['name'];  
?>  
```  
  
## <a name="sensitivity-data-classification-metadata"></a>Metadati di classificazione dei dati di riservatezza

A partire dalla versione 5.8.0 è disponibile un nuovo attributo di istruzione `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` che consente agli utenti di accedere ai [metadati di classificazione dei dati di riservatezza](../../relational-databases/security/sql-data-discovery-and-classification.md?tabs=t-sql#subheading-4) in Microsoft SQL Server 2019 usando `PDOStatement::getColumnMeta`, che richiede Microsoft ODBC Driver 17.4.2 o versione successiva.

L'attributo `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` è `false` per impostazione predefinita, ma se è impostato su `true`, il campo matrice `flags` citato in precedenza verrà popolato con i metadati di classificazione dei dati di riservatezza, se esistenti. 

Ad esempio prendere in considerazione una tabella Patients:

```
CREATE TABLE Patients 
      [PatientId] int identity,
      [SSN] char(11),
      [FirstName] nvarchar(50),
      [LastName] nvarchar(50),
      [BirthDate] date)
```

È possibile classificare le colonne SSN e BirthDate come illustrato di seguito:

```
ADD SENSITIVITY CLASSIFICATION TO [Patients].SSN WITH (LABEL = 'Highly Confidential - secure privacy', INFORMATION_TYPE = 'Credentials')
ADD SENSITIVITY CLASSIFICATION TO [Patients].BirthDate WITH (LABEL = 'Confidential Personal Data', INFORMATION_TYPE = 'Birthdays')
```

Per accedere ai metadati usare `PDOStatement::getColumnMeta` dopo aver impostato `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` su true, come illustrato nel frammento di codice seguente:

```
$options = array(PDO::SQLSRV_ATTR_DATA_CLASSIFICATION => true);
$tableName = 'Patients';
$tsql = "SELECT * FROM $tableName";
$stmt = $conn->prepare($tsql, $options);
$stmt->execute();
$numCol = $stmt->columnCount();

for ($i = 0; $i < $numCol; $i++) {
    $metadata = $stmt->getColumnMeta($i);
    $jstr = json_encode($metadata);
    echo $jstr . PHP_EOL;
}
```

L'output dei metadati per tutte le colonne è il seguente:

```
{"flags":{"Data Classification":[]},"sqlsrv:decl_type":"int identity","native_type":"string","table":"","pdo_type":2,"name":"PatientId","len":10,"precision":0}
{"flags":{"Data Classification":[{"Label":{"name":"Highly Confidential - secure privacy","id":""},"Information Type":{"name":"Credentials","id":""}}]},"sqlsrv:decl_type":"char","native_type":"string","table":"","pdo_type":2,"name":"SSN","len":11,"precision":0}
{"flags":{"Data Classification":[]},"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"FirstName","len":50,"precision":0}
{"flags":{"Data Classification":[]},"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"LastName","len":50,"precision":0}
{"flags":{"Data Classification":[{"Label":{"name":"Confidential Personal Data","id":""},"Information Type":{"name":"Birthdays","id":""}}]},"sqlsrv:decl_type":"date","native_type":"string","table":"","pdo_type":2,"name":"BirthDate","len":10,"precision":0}
```

Se si modifica il frammento di codice precedente impostando `PDO::SQLSRV_ATTR_DATA_CLASSIFICATION` su `false` (caso predefinito), il campo `flags` sarà sempre `0` come in precedenza, come indicato di seguito:

```
{"flags":0,"sqlsrv:decl_type":"int identity","native_type":"string","table":"","pdo_type":2,"name":"PatientId","len":10,"precision":0}
{"flags":0,"sqlsrv:decl_type":"char","native_type":"string","table":"","pdo_type":2,"name":"SSN","len":11,"precision":0}
{"flags":0,"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"FirstName","len":50,"precision":0}
{"flags":0,"sqlsrv:decl_type":"nvarchar","native_type":"string","table":"","pdo_type":2,"name":"LastName","len":50,"precision":0}
{"flags":0,"sqlsrv:decl_type":"date","native_type":"string","table":"","pdo_type":2,"name":"BirthDate","len":10,"precision":0}
```

      
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
