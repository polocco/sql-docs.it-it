---
title: PDOStatement::rowCount
description: Informazioni di riferimento sulle API per la funzione PDOStatement::rowCount nel driver Microsoft PDO_SQLSRV per PHP per SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0569f26a-2376-4c20-8813-bd3c87d0ae9f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31671bc3db85a31cde4109cedb11f3ab44f07ea1
ms.sourcegitcommit: 331b8495e4ab37266945c81ff5b93d250bdaa6da
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/20/2020
ms.locfileid: "88646581"
---
# <a name="pdostatementrowcount"></a>PDOStatement::rowCount
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Restituisce il numero di righe aggiunte, eliminate o modificate dall'ultima istruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int PDOStatement::rowCount ();  
```  
  
## <a name="return-value"></a>Valore restituito  
Il numero di righe aggiunte, eliminate o modificate.  
  
## <a name="remarks"></a>Osservazioni  
Se l'ultima istruzione SQL eseguita da PDOStatement è un'istruzione SELECT, un cursore PDO::CURSOR_FWDONLY restituisce -1. Un cursore PDO::CURSOR_SCROLLABLE restituisce il numero di righe nel set di risultati.  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
Questo esempio mostra due usi di rowCount. Il primo restituisce il numero di righe aggiunte alla tabella. Il secondo mostra che rowCount può restituire il numero di righe in un set di risultati quando si specifica un cursore scorrevole.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$col1 = 'a';  
$col2 = 'b';  
  
$query = "insert into Table2(col1, col2) values(?, ?)";  
$stmt = $conn->prepare( $query );  
$stmt->execute( array( $col1, $col2 ) );  
print $stmt->rowCount();  
  
echo "\n\n";  
  
$con = null;  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL));  
$stmt->execute();  
print $stmt->rowCount();  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
