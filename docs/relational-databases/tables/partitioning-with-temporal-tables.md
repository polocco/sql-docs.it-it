---
title: Partizionamento con le tabelle temporali | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 313714b8-4ad1-4c14-93a3-7f628a334a51
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fc76e2a2aaee2d3bc8474c8cec06b7ee85a31971
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555886"
---
# <a name="partitioning-with-temporal-tables"></a>Partizionamento con le tabelle temporali

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

È possibile usare il partizionamento in modo indipendente nella tabella di cronologia e in quella corrente. Tuttavia, il partizionamento non può essere usato per modificare il contenuto dei dati senza il controllo delle versioni di sistema.

> [!NOTE]
> Il partizionamento è una funzionalità di Enterprise Edition in SQL Server 2016 prima del Service Pack 1 e nelle versioni precedenti. Il partizionamento è supportato in tutte le edizioni di SQL Server 2016 Service Pack 1 e versioni successive.

- **Tabella corrente:**

  - **SWITCH IN** nella tabella corrente può essere usata per facilitare il caricamento di dati e l'esecuzione di query quando **SYSTEM_VERSIONING** è **ON**
  - **SWITCH OUT** non è consentita mentre **SYSTEM_VERSIONING** è **ON**

- **Tabella di cronologia:**

  - L'operazione**SWITCH OUT** dalla tabella di cronologia può essere eseguita mentre **SYSTEM_VERSIONING** è **ON** to purge portions of hètory data that è no longer relevant.
  - L'operazione**SWITCH IN** non è consentita quando **SYSTEM_VERSIONING** è **ON** since it can invalidate temporal data consètency.

## <a name="next-steps"></a>Passaggi successivi

- [Tabelle temporali](../../relational-databases/tables/temporal-tables.md)
- [Introduzione alle tabelle temporali con controllo delle versioni di sistema](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)
- [Verifiche di coerenza del sistema della tabella temporale](../../relational-databases/tables/temporal-table-system-consistency-checks.md)
- [Considerazioni e limitazioni delle tabelle temporali](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)
- [Sicurezza di una tabella temporale](../../relational-databases/tables/temporal-table-security.md)
- [Gestire la conservazione dei dati cronologici nelle tabelle temporali con controllo delle versioni di sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)
- [Tabelle temporali con controllo delle versioni di sistema con tabelle con ottimizzazione per la memoria](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)
- [Funzioni e viste per i metadati delle tabelle temporali](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)
