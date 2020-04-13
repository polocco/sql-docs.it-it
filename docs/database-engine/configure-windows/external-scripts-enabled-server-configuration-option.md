---
title: Opzione di configurazione del server external scripts enabled | Microsoft Docs
ms.date: 11/13/2017
ms.prod: sql
ms.technology: configuration
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- external scripts enabled
- external_scripts_enabled_TSQL
helpviewer_keywords:
- external scripts enabled option
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 14e3d788034fad9e26f8283e5155d29286ad7360
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664305"
---
# <a name="external-scripts-enabled-server-configuration-option"></a>Opzione di configurazione del server external scripts enabled
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
**Si applica a**: [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] e [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Usare l'opzione **external scripts enabled** per abilitare l'esecuzione di script con determinate estensioni del linguaggio remote. Questa proprietà è DISATTIVATA per impostazione predefinita. Quando **Advanced Analytics Services** è installato, il programma di installazione può impostare facoltativamente questa proprietà su true.

## <a name="remarks"></a>Osservazioni

È necessario abilitare l'opzione external script enabled prima di eseguire uno script esterno usando la procedura [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) . Usare **sp_execute_external_script** per eseguire script scritti in un linguaggio supportato, come R o Python. 

+ Per [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]

    [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] include il supporto del linguaggio di programmazione R in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], oltre a un set di strumenti per workstation R e librerie di connettività.

    Installare la funzionalità **Advanced Analytics Extensions** durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per abilitare l'esecuzione di script R. Il linguaggio di programmazione R è installato per impostazione predefinita.

+ Per [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)]

    [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] usa la stessa architettura di SQL Server 2016, ma supporta in più il linguaggio di programmazione Python.

    Installare la funzionalità **Advanced Analytics Extensions** durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per abilitare l'esecuzione di script esterni. Durante l'installazione iniziale selezionare almeno un linguaggio di programmazione: R o Python oppure entrambi. 

## <a name="additional-requirements"></a>Requisiti aggiuntivi

Dopo l'installazione, per abilitare gli script esterni eseguire lo script seguente:

```sql
sp_configure 'external scripts enabled', 1;
RECONFIGURE WITH OVERRIDE;  
```

È necessario riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per rendere effettiva questa modifica.

Per altre informazioni, vedere [Configurare SQL Server Machine Learning Services](../../machine-learning/install/sql-machine-learning-services-windows-install.md).

## <a name="see-also"></a>Vedere anche

[sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)

[RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)

[sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)

[SQL Server Machine Learning Services](../../machine-learning/index.yml)
