---
title: Interfaccia ISQLServerResultSet | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 002496f7-8ec0-4267-b4e6-ba095e2ef306
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eeaa9b486fc818464b6bc2f2b57552bb1f18a744
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924706"
---
# <a name="isqlserverresultset-interface"></a>Interfaccia ISQLServerResultSet
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta un set di risultati JDBC. Questa interfaccia è stata aggiunta in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** java.sql.ResultSet  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public interface ISQLServerResultSet  
```  
  
## <a name="remarks"></a>Osservazioni  
 Questa interfaccia viene implementata dalla classe [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
 Questa interfaccia espone i metodi specifici di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] seguenti:  
  
|Metodo|Per ulteriori informazioni, vedere|  
|------------|-------------------------------|  
|public microsoft.sql.DateTimeOffset getDateTimeOffset(int)|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-int-sqlserverresultset.md)|  
|public microsoft.sql.DateTimeOffset getDateTimeOffset(String)|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-java-lang-string-sqlserverresultset.md)|  
|public void updateDateTimeOffset(int, microsoft.sql.DateTimeOffset)|[updateDateTimeOffset](../../../connect/jdbc/reference/updatedatetimeoffset-int-microsoft-sql-datetimeoffset-sqlserverresultset.md)|  
|public void updateDateTimeOffset(String, microsoft.sql.DateTimeOffset)|[updateDateTimeOffset](../../../connect/jdbc/reference/updatedatetimeoffset-string-microsoft-sql-datetimeoffset-sqlserverresultset.md)|  
  
 Questa interfaccia espone i campi specifici di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] seguenti:  
  
|Campo|Per ulteriori informazioni, vedere|  
|-----------|-------------------------------|  
|public static final int CONCUR_SS_OPTIMISTIC_CC|[CONCUR_SS_OPTIMISTIC_CC](../../../connect/jdbc/reference/concur-ss-optimistic-cc-field-sqlserverresultset.md)|  
|public static final int CONCUR_SS_OPTIMISTIC_CCVAL|[CONCUR_SS_OPTIMISTIC_CCVAL](../../../connect/jdbc/reference/concur-ss-optimistic-ccval-field-sqlserverresultset.md)|  
|public static final int CONCUR_SS_SCROLL_LOCKS|[CONCUR_SS_SCROLL_LOCKS](../../../connect/jdbc/reference/concur-ss-scroll-locks-field-sqlserverresultset.md)|  
|public static final int TYPE_SS_DIRECT_FORWARD_ONLY|[TYPE_SS_DIRECT_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-direct-forward-only-field-sqlserverresultset.md)|  
|public static final int TYPE_SS_SCROLL_DYNAMIC|[TYPE_SS_SCROLL_DYNAMIC](../../../connect/jdbc/reference/type-ss-scroll-dynamic-field-sqlserverresultset.md)|  
|public static final int TYPE_SS_SCROLL_KEYSET|[TYPE_SS_SCROLL_KEYSET](../../../connect/jdbc/reference/type-ss-scroll-keyset-field-sqlserverresultset.md)|  
|public static final int TYPE_SS_SCROLL_STATIC|[TYPE_SS_SCROLL_STATIC](../../../connect/jdbc/reference/type-ss-scroll-static-field-sqlserverresultset.md)|  
|public static final int TYPE_SS_SERVER_CURSOR_FORWARD_ONLY|[TYPE_SS_SERVER_CURSOR_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-server-cursor-forward-only-field-sqlserverresultset.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sull'API del driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
