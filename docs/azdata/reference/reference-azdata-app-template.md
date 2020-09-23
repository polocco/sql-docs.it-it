---
title: Informazioni di riferimento su azdata app template
titleSuffix: SQL Server big data clusters
description: Usare questo articolo di riferimento per comprendere i comandi SQL dello strumento azdata, in particolare i comandi app template.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 37371ec8d909115aedf1eb745a78fec7af427cc4
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733845"
---
# <a name="azdata-app-template"></a>azdata app template

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

L'articolo seguente offre informazioni di riferimento sui comandi `sql` dello strumento `azdata`. Per altre informazioni su altri comandi `azdata`, vedere [Informazioni di riferimento su azdata](reference-azdata.md).

## <a name="commands"></a>Comandi:
| Comando | Descrizione |
| --- | --- |
[azdata app template list](#azdata-app-template-list) | Recupera i modelli supportati.
[azdata app template pull](#azdata-app-template-pull) | Scarica i modelli supportati.
## <a name="azdata-app-template-list"></a>azdata app template list
Recupera i modelli supportati nel repository GitHub [URL] specificato.
```bash
azdata app template list [--url -u] 
                         
```
### <a name="examples"></a>Esempi
Recuperare tutti i modelli nel percorso predefinito del repository di modelli.
```bash
azdata app template list
```
Recuperare tutti i modelli in un percorso di repository diverso.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>Parametri facoltativi
#### `--url -u`
Specificare un percorso di un repository di modelli diverso. Valore predefinito: https://github.com/Microsoft/SQLBDC-AppDeploy.git
### <a name="global-arguments"></a>Argomenti globali
#### `--debug`
Aumenta il livello di dettaglio della registrazione per mostrare tutti i log di debug.
#### `--help -h`
Visualizza questo messaggio della guida ed esce.
#### `--output -o`
Formato di output.  Valori consentiti: json, jsonc, table, tsv.  Valore predefinito: json.
#### `--query -q`
Stringa di query JMESPath. Per altre informazioni ed esempi, vedere [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Aumenta il livello di dettaglio della registrazione. Usare --debug per log di debug completi.
## <a name="azdata-app-template-pull"></a>azdata app template pull
Scarica i modelli supportati nel repository GitHub [URL] specificato.
```bash
azdata app template pull [--name -n] 
                         [--url -u]  
                         
[--destination -d]
```
### <a name="examples"></a>Esempi
Scaricare tutti i modelli nel percorso predefinito del repository di modelli.
```bash
azdata app template pull
```
Scaricare tutti i modelli in un percorso di repository diverso.
```bash
azdata app template list --url https://github.com/diffrent/templates.git
```
Scaricare un singolo modello per nome.
```bash
azdata app template pull --name ssis            
```
### <a name="optional-parameters"></a>Parametri facoltativi
#### `--name -n`
Nome del modello. Per un elenco completo dei nomi di modello supportati, eseguire `azdata app template list`
#### `--url -u`
Specificare un percorso di un repository di modelli diverso. Valore predefinito: https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
Posizione in cui inserire il modello dello scheletro dell'applicazione.
`./templates`
### <a name="global-arguments"></a>Argomenti globali
#### `--debug`
Aumenta il livello di dettaglio della registrazione per mostrare tutti i log di debug.
#### `--help -h`
Visualizza questo messaggio della guida ed esce.
#### `--output -o`
Formato di output.  Valori consentiti: json, jsonc, table, tsv.  Valore predefinito: json.
#### `--query -q`
Stringa di query JMESPath. Per altre informazioni ed esempi, vedere [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Aumenta il livello di dettaglio della registrazione. Usare --debug per log di debug completi.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su altri comandi `azdata`, vedere [Informazioni di riferimento su azdata](reference-azdata.md). Per altre informazioni su come installare lo strumento `azdata`, vedere [Installare azdata per gestire i cluster Big Data di SQL Server 2019](../install/deploy-install-azdata.md).
