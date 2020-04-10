---
title: PDO::beginTransaction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4d5db438-9df7-4d22-9907-3ddc63bd2220
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ec1b4149b882e520eb58a8789516461c83c01de
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919395"
---
# <a name="pdobegintransaction"></a>PDO::beginTransaction
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Disattiva la modalità di commit automatico e avvia una transazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
bool PDO::beginTransaction();  
```  
  
## <a name="return-value"></a>Valore restituito  
true se la chiamata al metodo ha avuto esito positivo; in caso contrario, false.  
  
## <a name="remarks"></a>Osservazioni  
La transazione avviata con PDO::beginTransaction termina quando viene chiamato [PDO::commit](../../connect/php/pdo-commit.md) o [PDO::rollback](../../connect/php/pdo-rollback.md).  
  
PDO::beginTransaction non è influenzato da e non influisce sul valore di PDO::ATTR_AUTOCOMMIT.  
  
Non è consentito chiamare PDO::beginTransaction prima di terminare la chiamata PDO::beginTransaction precedente con PDO::rollback o PDO::commit.  
  
Se questo metodo ha esito negativo, la connessione torna alla modalità di commit automatico.  
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
Nell'esempio seguente viene usato un database denominato Test e una tabella denominata Table1. Viene avviata una transazione quindi, vengono generati comandi per aggiungere due righe e poi per eliminare una riga. I comandi vengono inviati al database e la transazione viene terminata in modo esplicito con `PDO::commit`.  
  
```  
<?php  
   $conn = new PDO( "sqlsrv:server=(local); Database = Test", "", "");  
   $conn->beginTransaction();  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'b') ");  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'c') ");  
   $ret = $conn->exec("delete from Table1 where col1 = 'a' and col2 = 'b'");  
   $conn->commit();  
   // $conn->rollback();  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
