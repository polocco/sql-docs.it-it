---
title: PDO::exec | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 359a87c6-c13a-4518-8f23-a922e7f3b171
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6f46342631124114f70d50c2980fbd703f9b25b
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919346"
---
# <a name="pdoexec"></a>PDO::exec
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Prepara ed esegue un'istruzione SQL in una sola chiamata di funzione, restituendo il numero di righe interessate dall'istruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int PDO::exec ($statement)  
```  
  
#### <a name="parameters"></a>Parametri  
*$statement*: stringa contenente l'istruzione SQL da eseguire.  
  
## <a name="return-value"></a>Valore restituito  
Valore intero che segnala il numero di righe interessate.  
  
## <a name="remarks"></a>Osservazioni  
Se *$statement* contiene più istruzioni SQL, il numero delle righe interessate viene segnalato solo per l'ultima istruzione.  
  
PDO::exec non restituisce risultati per un'istruzione SELECT.  
  
Gli attributi seguenti influiscono sul comportamento di PDO::exec:  
  
-   PDO::ATTR_DEFAULT_FETCH_MODE  
  
-   PDO::SQLSRV_ATTR_ENCODING  
  
-   PDO::SQLSRV_ATTR_QUERY_TIMEOUT  
  
Per altre informazioni, vedere [PDO::setAttribute](../../connect/php/pdo-setattribute.md). 
  
Nella versione 2.0 dei [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]è stato aggiunto il supporto per PDO.  
  
## <a name="example"></a>Esempio  
Questo esempio elimina le righe di Table1 contenenti 'xxxyy' in col1. L'esempio quindi segnala il numero di righe eliminate.  
  
```  
<?php  
   $c = new PDO( "sqlsrv:server=(local)");  
  
   $c->exec("use Test");  
   $ret = $c->exec("delete from Table1 where col1 = 'xxxyy'");  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>Vedere anche  
[Classe PDO](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
