---
title: Editor attività Trasferisci oggetti SQL Server (pagina oggetti) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfersqlserverobjects.objects.f1
helpviewer_keywords:
- Transfer SQL Server Objects Task Editor
ms.assetid: 8cc09118-70ac-4013-8308-d87f8411ca0c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6fc54343ef930d4fbca1bbe25f2e03ba4e539d44
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439908"
---
# <a name="transfer-sql-server-objects-task-editor-objects-page"></a>Editor attività Trasferisci oggetti di SQL Server (pagina Oggetti)
  Utilizzare la pagina **Oggetti** della finestra di dialogo **Editor attività Trasferisci oggetti di SQL Server** per impostare le proprietà relative alla copia di uno o più oggetti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] da un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a un'altra. Tabelle, viste, stored procedure e funzioni definite dall'utente rappresentano solo alcuni esempi di oggetti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] che è possibile copiare. Per ulteriori informazioni su questa attività, vedere [Transfer SQL Server Objects Task](control-flow/transfer-sql-server-objects-task.md).  
  
> [!NOTE]  
>  L'utente che crea l'attività Trasferisci oggetti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] deve disporre di autorizzazioni sufficienti per gli oggetti del server di origine per selezionarli e copiarli, nonché dell'autorizzazione per l'accesso al database del server di destinazione in cui gli oggetti verranno trasferiti.  
  
## <a name="static-options"></a>Opzioni statiche  
 **SourceConnection**  
 Selezionare una gestione connessione SMO nell'elenco oppure fare clic su **\<New connection...>** per creare una nuova connessione al server di origine.  
  
 **SourceDatabase**  
 Consente di selezionare un database nel server di origine dal quale verranno copiati gli oggetti.  
  
 **DestinationConnection**  
 Selezionare una gestione connessione SMO nell'elenco oppure fare clic su **\<New connection...>** per creare una nuova connessione al server di destinazione.  
  
 **DestinationDatabase**  
 Consente di selezionare un database nel server di destinazione nel quale verranno copiati gli oggetti.  
  
 **DropObjectsFirst**  
 Consente di indicare se gli oggetti selezionati verranno eliminati nel server di destinazione prima della copia.  
  
 **IncludeExtendedProperties**  
 Consente di indicare se le proprietà estese devono essere incluse nella copia degli oggetti dal server di origine a quello di destinazione.  
  
 **CopyData**  
 Consente di indicare se i dati devono essere inclusi nella copia degli oggetti dal server di origine a quello di destinazione.  
  
 **ExistingData**  
 Consente di specificare la modalità di copia dei dati nel server di destinazione. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente:  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**Sostituire**|I dati nel server di destinazione verranno sovrascritti.|  
|**Append**|I dati copiati dal server di origine verranno accodati a quelli esistenti nel server di destinazione.|  
  
> [!NOTE]  
>   L'opzione **ExistingData** è disponibile solo se **CopyData** è impostata su **True**.  
  
 **CopySchema**  
 Consente di indicare se lo schema deve essere copiato durante l'attività Trasferisci oggetti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  **CopySchema** è disponibile solo per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **UseCollation**  
 Consente di indicare se il trasferimento degli oggetti deve includere le regole di confronto specificate nel server di origine.  
  
 **IncludeDependentObjects**  
 Consente di indicare se la copia degli oggetti selezionati deve essere propagata in modo da includere eventuali oggetti dipendenti da quelli selezionati.  
  
 **CopyAllObjects**  
 Consente di indicare se, durante l'attività, devono essere copiati tutti gli oggetti nel database di origine specificato o solo quelli selezionati.  Se questa opzione viene impostata su False, è possibile selezionare gli oggetti da trasferire e vengono visualizzate le opzioni dinamiche nella sezione **CopyAllObjects**.  
  
 **ObjectsToCopy**  
 Espandere **ObjectsToCopy** per specificare quali oggetti devono essere copiati dal database di origine a quello di destinazione.  
  
> [!NOTE]  
>  **ObjectsToCopy** è disponibile solo se **CopyAllObjects** è impostata su **False**.  
  
 Le opzioni per la copia dei tipi di oggetti seguenti sono supportate solo in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
 Assembly  
  
 Funzioni di partizione  
  
 Schemi di partizione  
  
 Schemi  
  
 Funzioni di aggregazione definite dall'utente  
  
 Tipi definiti dall'utente  
  
 Raccolte di XML Schema  
  
 **CopyDatabaseUsers**  
 Consente di indicare se gli utenti del database devono essere inclusi nel trasferimento.  
  
 **CopyDatabaseRoles**  
 Consente di indicare se i ruoli del database devono essere inclusi nel trasferimento.  
  
 **CopySqlServerLogins**  
 Consente di indicare se gli account di accesso di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] devono essere inclusi nel trasferimento.  
  
 **CopyObjectLevelPermissions**  
 Consente di indicare se le autorizzazioni a livello di oggetto devono essere incluse nel trasferimento.  
  
 **CopyIndexes**  
 Consente di indicare se gli indici devono essere inclusi nel trasferimento.  
  
 **CopyTriggers**  
 Consente di indicare se i trigger devono essere inclusi nel trasferimento.  
  
 **CopyFullTextIndexes**  
 Consente di indicare se gli indici full-text devono essere inclusi nel trasferimento.  
  
 **CopyPrimaryKeys**  
 Consente di indicare se le chiavi primarie devono essere incluse nel trasferimento.  
  
 **CopyForeignKeys**  
 Consente di indicare se le chiavi esterne devono essere incluse nel trasferimento.  
  
 **GenerateScriptsInUnicode**  
 Consente di indicare se gli script di trasferimento generati sono in formato Unicode.  
  
## <a name="dynamic-options"></a>Opzioni dinamiche  
  
### <a name="copyallobjects--false"></a>CopyAllObjects = False  
 **CopyAllTables**  
 Consente di indicare se, durante l'attività, verranno copiate tutte le tabelle nel database di origine specificato o solo le tabelle selezionate.  
  
 **TablesList**  
 Fare clic per aprire la finestra di dialogo **Selezione tabelle** .  
  
 **CopyAllViews**  
 Consente di indicare se, durante l'attività, verranno copiate tutte le viste nel database di origine specificato o solo quelle selezionate.  
  
 **ViewsList**  
 Fare clic per aprire la finestra di dialogo **Selezione viste** .  
  
 **CopyAllStoredProcedures**  
 Consente di indicare se, durante l'attività, verranno copiate tutte le stored procedure definite dall'utente nel database di origine specificato o solo le stored procedure selezionate.  
  
 **StoredProceduresList**  
 Fare clic per aprire la finestra di dialogo **Selezione stored procedure** .  
  
 **CopyAllUserDefinedFunctions**  
 Consente di indicare se, durante l'attività, verranno copiate tutte le funzioni definite dall'utente nel database di origine specificato o solo le funzioni selezionate.  
  
 **UserDefinedFunctionsList**  
 Fare clic per aprire la finestra di dialogo **Selezione funzioni definite dall'utente** .  
  
 **CopyAllDefaults**  
 Consente di indicare se, durante l'attività, verranno copiati tutti i valori predefiniti nel database di origine specificato o solo i valori predefiniti selezionati.  
  
 **DefaultsList**  
 Fare clic per aprire la finestra di dialogo **Selezione valori predefiniti** .  
  
 **CopyAllUserDefinedDataTypes**  
 Consente di indicare se, durante l'attività, verranno copiati tutti i tipi di dati definiti dall'utente nel database di origine specificato o solo i tipi selezionati.  
  
 **UserDefinedDataTypesList**  
 Fare clic per aprire la finestra di dialogo **Selezione tipi di dati definiti dall'utente** .  
  
 **CopyAllPartitionFunctions**  
 Consente di indicare se, durante l'attività, verranno copiate tutte le partizioni definite dall'utente nel database di origine specificato o solo le partizioni selezionate. Opzione supportata solo in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **PartitionFunctionsList**  
 Fare clic per aprire la finestra di dialogo **Selezione funzioni di partizione** .  
  
 **CopyAllPartitionSchemes**  
 Consente di indicare se, durante l'attività, verranno copiati tutti gli schemi di partizione nel database di origine specificato o solo gli schemi selezionati. Opzione supportata solo in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **PartitionSchemesList**  
 Fare clic per aprire la finestra di dialogo **Selezione schemi di partizione** .  
  
 **CopyAllSchemas**  
 Consente di indicare se, durante l'attività, verranno copiati tutti gli schemi nel database di origine specificato o solo quelli selezionati. Opzione supportata solo in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **SchemasList**  
 Fare clic per aprire la finestra di dialogo **Seleziona schemi** .  
  
 **CopyAllSqlAssemblies**  
 Consente di indicare se, durante l'attività, verranno copiati tutti gli assembly SQL nel database di origine specificato o solo quelli selezionati. Opzione supportata solo in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **SqlAssembliesList**  
 Fare clic per aprire la finestra di dialogo **Select SQL Assemblies** (Selezione assembly SQL).  
  
 **CopyAllUserDefinedAggregates**  
 Consente di indicare se, durante l'attività, verranno copiate tutte le funzioni di aggregazione definite dall'utente nel database di origine specificato o solo le funzioni selezionate. Opzione supportata solo in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **UserDefinedAggregatesList**  
 Fare clic per aprire la finestra di dialogo **Selezione funzioni di aggregazione definite dall'utente** .  
  
 **CopyAllUserDefinedTypes**  
 Consente di indicare se, durante l'attività, verranno copiati tutti i tipi definiti dall'utente nel database di origine specificato o solo quelli selezionati. Opzione supportata solo in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **UserDefinedTypes**  
 Fare clic per aprire la finestra di dialogo **Selezione tipi definiti dall'utente** .  
  
 **CopyAllXmlSchemaCollections**  
 Consente di indicare se, durante l'attività, verranno copiate tutte le raccolte di XML Schema nel database di origine specificato o solo le raccolte di XML Schema selezionate. Opzione supportata solo in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 **XmlSchemaCollectionsList**  
 Fare clic per aprire la finestra di dialogo **Selezionare le raccolte XML Schema** .  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services riferimento a errori e messaggi](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Attività Integration Services](control-flow/integration-services-tasks.md)   
 [Editor attività Trasferisci oggetti SQL Server &#40;pagina generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Pagina espressioni](expressions/expressions-page.md)   
 [Formati di dati per l'importazione o l'esportazione bulk &#40;SQL Server&#41;](../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md)   
 [Considerazioni sulla sicurezza per un'installazione di SQL Server](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
