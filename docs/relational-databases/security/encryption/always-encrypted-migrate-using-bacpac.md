---
description: Esportare e importare database usando Always Encrypted
title: Esportare e importare database usando Always Encrypted | Microsoft Docs
ms.custom: ''
ms.date: 10/30/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Always Encrypted, configure with SSMS
ms.assetid: 29816a41-f105-4414-8be1-070675d62e84
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3fc54fedce772b267cf19a9396672b61cf6e6254
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91867771"
---
# <a name="export-and-import-databases-using-always-encrypted"></a>Esportare e importare database usando Always Encrypted 
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]

Questo articolo descrive come esportare e importare database contenenti colonne protette con [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md).

Quando si esporta un database, tutti i dati archiviati in colonne crittografate vengono recuperati dal database in formato crittografato (ciphertext) e inseriti nel file [BACPAC](../../data-tier-applications/data-tier-applications.md) risultante. Il file BACPAC risultante contiene anche i metadati per le chiavi di Always Encrypted.

Quando si importa il file BACPAC in un database, i dati crittografati del file BACPAC vengono caricati nel database e i metadati delle chiavi di Always Encrypted vengono ricreati. 

Se si usa un'applicazione configurata per eseguire query in colonne crittografate archiviate nel database di origine (quello esportato), non sono necessarie operazioni particolari per consentire all'applicazione di eseguire query sui dati crittografati nel database di destinazione, perché le chiavi presenti in entrambi i database sono le stesse.

Per informazioni dettagliate su come esportare e importare un database, vedere:
- [Esportazione di un'applicazione livello dati](../../data-tier-applications/export-a-data-tier-application.md)
- [Importare un file BACPAC per creare un nuovo database utente](../../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md)
- [Esportare un database SQL di Azure in un file BACPAC](/azure/sql-database/sql-database-export)
- [Importare un file BACPAC in un database SQL di Azure](/azure/sql-database/sql-database-import)
- [SqlPackage.exe](../../../tools/sqlpackage.md)

## <a name="permissions-for-migrating-databases-with-encrypted-columns"></a>Autorizzazioni per la migrazione di database con colonne crittografate

Sono necessarie le autorizzazioni *ALTER ANY COLUMN MASTER KEY* e *ALTER ANY COLUMN ENCRYPTION KEY* per il database di origine. Per il database di destinazione sono necessarie le autorizzazioni *ALTER ANY COLUMN MASTER KEY*, *ALTER ANY COLUMN ENCRYPTION KEY*, *VIEW ANY COLUMN MASTER KEY DEFINITION* e *VIEW ANY COLUMN ENCRYPTION DEFINITION*

Non è invece necessario avere i diritti di accesso alle chiavi master della colonna configurate per le colonne crittografate, poiché durante le operazioni di esportazione e importazione i dati rimangono crittografati.

## <a name="next-steps"></a>Passaggi successivi
- [Sviluppare applicazioni usando Always Encrypted](always-encrypted-client-development.md)

## <a name="see-also"></a>Vedere anche
- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Eseguire il backup e il ripristino di database usando Always Encrypted](always-encrypted-migrate-using-backup-restore.md)
- [Eseguire la migrazione di dati da o verso colonne usando Always Encrypted con l'Importazione/Esportazione guidata SQL Server](always-encrypted-migrate-using-import-export-wizard.md)
- [Caricamento bulk di dati crittografati in colonne tramite Always Encrypted](migrate-sensitive-data-protected-by-always-encrypted.md)