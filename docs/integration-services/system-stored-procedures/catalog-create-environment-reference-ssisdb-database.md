---
description: catalog.create_environment_reference (database SSISDB)
title: catalog.create_environment_reference (database SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 48069bea-31cb-4a0e-9849-a07edc94088f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dcca4fd25fd201c9b278107dce188b6cab12d866
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88477124"
---
# <a name="catalogcreate_environment_reference-ssisdb-database"></a>catalog.create_environment_reference (database SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Viene creato un riferimento all'ambiente per un progetto nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
catalog.create_environment_reference [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @environment_name = ] environment_name  
     , [ @reference_type = ] reference_type  
  [  , [ @environment_folder_name = ] environment_folder_name ]  
  [  , [ @reference_id = ] reference_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @folder_name = ] *folder_name*  
 Nome della cartella del progetto che fa riferimento all'ambiente. *folder_name* è di tipo **nvarchar(128)** .  
  
 [ @project_name = ] *project_name*  
 Nome del progetto che fa riferimento all'ambiente. *project_name* è di tipo **nvarchar(128)** .  
  
 [ @environment_name = ] *environment_name*  
 Nome dell'ambiente a cui viene fatto riferimento. *environment_name* è di tipo **nvarchar(128)** .  
  
 [ @reference_type = ] *reference_type*  
 Viene indicato se l'ambiente può essere individuato nella stessa cartella del progetto (riferimento relativo) o in una cartella diversa (riferimento assoluto). Utilizzare il valore `R` per indicare un riferimento relativo. Utilizzare il valore `A` per indicare un riferimento assoluto. *reference_type* è di tipo **char(1)** .  
  
 [ @environment_folder_name = ] *environment_folder_name*  
 Nome della cartella in cui si trova l'ambiente a cui viene fatto riferimento. Questo valore è richiesto per i riferimenti assoluti. *environment_folder_name* è di tipo **nvarchar(128)** .  
  
 [ @reference_id = ] *reference_id*  
 Viene restituito l'identificatore univoco per il nuovo riferimento. Questo parametro è facoltativo e, *reference_id* è di tipo **bigint**.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 0 (esito positivo)  
  
## <a name="result-sets"></a>Set di risultati  
 nessuno  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa stored procedure è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazioni READ e MODIFY sul progetto e autorizzazione READ sull'ambiente  
  
-   Appartenenza al ruolo del database **ssis_admin**  
  
-   Appartenenza al ruolo del server **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errori e avvisi  
 Nell'elenco seguente vengono descritte alcune condizioni che possono generare un errore o un avviso:  
  
-   Nome della cartella non valido  
  
-   Nome del progetto non valido  
  
-   Utente senza autorizzazioni appropriate  
  
-   Un riferimento assoluto è specificato tramite il carattere `A` nel parametro *reference_location*, ma il nome della cartella non è stato specificato con il parametro *environment_folder_name*.  
  
## <a name="remarks"></a>Osservazioni  
 Un progetto può disporre di riferimenti all'ambiente relativi o assoluti. I riferimenti relativi fanno riferimento all'ambiente in base al nome. Per tali riferimenti è necessario che l'ambiente si trovi nella stessa cartella del progetto. I riferimenti assoluti fanno riferimento all'ambiente in base al nome e alla cartella e possono fare riferimento ad ambienti che si trovano in una cartella di destinazione diversa da quella del progetto. Un progetto può fare riferimento a più ambienti.  
  
  
