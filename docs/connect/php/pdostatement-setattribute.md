---
title: PDOStatement::setAttribute
description: Informazioni di riferimento sulle API per la funzione PDOStatement::setAttribute nel driver Microsoft PDO_SQLSRV per PHP per SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 33bd5d23ab35eda7fc6416dc18cf720eabd71f58
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646531"
---
# <a name="pdostatementsetattribute"></a>PDOStatement::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Imposta un valore di attributo, ovvero un attributo PDO predefinito o un attributo personalizzato del driver.  
  
## <a name="syntax"></a>Sintassi  
  
```  
bool PDOStatement::setAttribute ($attribute, $value );  
```  
  
#### <a name="parameters"></a>Parametri  
$*attribute*: un Integer, una delle costanti PDO::ATTR_* o PDO::SQLSRV_ATTR_\*. Per l'elenco degli attributi disponibili, vedere la sezione Osservazioni.  
  
$*value*: valore (misto) da impostare per $*attribute*.  
  
## <a name="return-value"></a>Valore restituito  
TRUE in caso di esito positivo; in caso contrario, FALSE.  
  
## <a name="remarks"></a>Osservazioni  
Nella tabella seguente sono elencati gli attributi disponibili:  
  
|Attributo|Valori|Descrizione|  
|-------------|----------|---------------|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|1 per il limite di memoria PHP.|Consente di configurare le dimensioni del buffer che contiene il set di risultati per un cursore sul lato client.<br /><br />Il valore predefinito è 10.240 KB (10 MB).<br /><br />Per altre informazioni sui cursori sul lato client, vedere [Tipi di cursore &#40;PDO_SQLSRV Driver&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_DATA_CLASSIFICATION|true o false|Specifica se recuperare i metadati di classificazione dei dati quando si chiama [PDOStatement::getColumnMeta](../../connect/php/pdostatement-getcolumnmeta.md). Il valore predefinito è false.|
|PDO::SQLSRV_ATTR_DECIMAL_PLACES|Numero intero compreso tra 0 e 4 inclusi|Specifica il numero di posizioni decimali per la formattazione dei valori money recuperati.<br /><br />Qualsiasi numero intero negativo o valore maggiore di 4 verrà ignorato.<br /><br />Questa opzione funziona solo quando PDO::SQLSRV_ATTR_FORMAT_DECIMALS è true.<br /><br />Questa opzione può anche essere impostata a livello di connessione. In questo caso, questa opzione eseguirà l'override dell'opzione a livello di connessione.<br /><br />Per altre informazioni, vedere [Formattazione di stringhe decimali e valori money (driver PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).|
|PDO::SQLSRV_ATTR_ENCODING|Integer<br /><br />PDO::SQLSRV_ENCODING_UTF8 (impostazione predefinita)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|Consente di impostare la codifica del set di caratteri usata dal driver per comunicare con il server.|  
|PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE|true o false|Specifica se recuperare i tipi di data e ora come oggetti [DateTime PHP](http://php.net/manual/en/class.datetime.php). Se false, il comportamento predefinito è restituirli come stringhe.<br /><br />Questa opzione può anche essere impostata a livello di connessione. In questo caso, questa opzione eseguirà l'override dell'opzione a livello di connessione.<br /><br />Per altre informazioni, vedere [Procedura: Recuperare i tipi di data e ora come oggetti DateTime PHP usando il driver PDO_SQLSRV](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md).|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|true o false|Gestisce i recuperi numerici dalle colonne con tipi SQL numerici (bit, integer, smallint, tinyint, float o real).<br /><br />Quando il flag dell'opzione di connessione ATTR_STRINGIFY_FETCHES è attivato, il valore restituito è una stringa, anche quando è attivato SQLSRV_ATTR_FETCHES_NUMERIC_TYPE.<br /><br />Quando il tipo PDO restituito nella colonna di associazione è PDO_PARAM_INT, il valore restituito da una colonna integer è un valore int anche se SQLSRV_ATTR_FETCHES_NUMERIC_TYPE è disattivato.|  
|PDO::SQLSRV_ATTR_FORMAT_DECIMALS|true o false|Specifica se aggiungere zeri iniziali alle stringhe decimali quando appropriato. Se impostata, questa opzione abilita l'opzione PDO::SQLSRV_ATTR_DECIMAL_PLACES per la formattazione dei tipi money. Se false, viene usato il comportamento predefinito di restituire la precisione esatta e di omettere gli zeri iniziali per valori inferiori a 1.<br /><br />Questa opzione può anche essere impostata a livello di connessione. In questo caso, questa opzione eseguirà l'override dell'opzione a livello di connessione.<br /><br />Per altre informazioni, vedere [Formattazione di stringhe decimali e valori money (driver PDO_SQLSRV)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md).| 
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Integer|Imposta il timeout in secondi della query.<br /><br />Per impostazione predefinita, il driver attende i risultati per un periodo illimitato. I numeri negativi non sono consentiti.<br /><br />0 indica nessun timeout.|  
  
## <a name="example"></a>Esempio  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets'=>false )  );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
echo $stmt->getAttribute( constant( "PDO::ATTR_CURSOR" ) );  
  
echo "\n";  
  
$stmt->setAttribute(PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 2);  
echo $stmt->getAttribute( constant( "PDO::SQLSRV_ATTR_QUERY_TIMEOUT" ) );  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
