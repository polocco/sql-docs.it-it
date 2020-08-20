---
description: Ordinamento dei dati per le trasformazioni Unione e Merge Join
title: Ordinare i dati per le trasformazioni Unione e Merge Join | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- sort attributes [Integration Services]
- output columns [Integration Services]
ms.assetid: 22ce3f5d-8a88-4423-92c2-60a8f82cd4fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5a9d622868c934065a47b6bb3c02b49b4de36371
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88495698"
---
# <a name="sort-data-for-the-merge-and-merge-join-transformations"></a>Ordinamento dei dati per le trasformazioni Unione e Merge Join

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  In [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]le trasformazioni Unione e Merge Join richiedono dati di input ordinati. I dati di input devono essere ordinati fisicamente ed è necessario impostare le opzioni di ordinamento sugli output e sulle colonne di output nell'origine o nella trasformazione a monte. Se le opzioni di ordinamento indicano che i dati sono ordinati, mentre in realtà non lo sono, l'operazione di Unione o Merge join restituisce risultati imprevisti.  
  
## <a name="sorting-the-data"></a>Ordinamento dei dati  
 È possibile ordinare i dati mediante uno dei seguenti metodi:  
  
-   Utilizzare nell'origine una clausola ORDER BY nell'istruzione utilizzata per caricare i dati.  
  
-   Inserire nel flusso di dati una trasformazione Ordinamento prima della trasformazione Unione o Merge join.  
  
 Se i dati sono di tipo stringa, le trasformazioni Unione e Merge join presuppongono che i valori stringa siano stati ordinati mediante le regole di confronto di Windows. Per fornire i valori stringa alle trasformazioni Unione e Merge join ordinate mediante le regole di confronto di Windows, utilizzare la procedura seguente:  
  
#### <a name="to-provide-string-values-that-are-sorted-by-using-windows-collation"></a>Per fornire valori stringa ordinati tramite regole di confronto di Windows  
  
-   Utilizzare una trasformazione Ordinamento per ordinare i dati.  
  
     La trasformazione Ordinamento utilizza le regole di confronto di Windows per ordinare i valori stringa.  
  
     -oppure-  
  
-   Usare l'operatore CAST Transact-SQL per eseguire innanzitutto il cast dei valori **varchar** in valori **nvarchar** e quindi usare la clausola ORDER BY Transact-SQL per ordinare i dati.  
  
    > [!IMPORTANT]  
    >  Non è possibile utilizzare solo la clausola ORDER BY perché tale clausola utilizza le regole di confronto di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per ordinare i valori stringa. L'uso delle regole di confronto di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] può restituire un ordinamento diverso rispetto alle regole di confronto di Windows, con risultati imprevisti nella trasformazione Unione o Merge join.  
  
## <a name="setting-sort-options-on-the-data"></a>Impostazione delle opzioni di ordinamento nei dati  
 È necessario impostare due importanti proprietà di ordinamento per l'origine o per la trasformazione a monte che fornisce i dati alle trasformazioni Unione e Merge join:  
  
-   La proprietà **IsSorted** dell'output che indica se i dati sono stati ordinati. Questa proprietà deve essere impostata su **True**.  
  
    > [!IMPORTANT]  
    >  L'impostazione del valore della proprietà **IsSorted** su **True** non determina l'ordinamento dei dati. Questa proprietà fornisce solo un hint ai componenti a valle in relazione all'ordinamento precedente dei dati.  
  
-   La proprietà **SortKeyPosition** delle colonne di output che indica se una colonna è ordinata, l'ordinamento della colonna e la sequenza di ordinamento di più colonne. Questa proprietà deve essere impostata per ogni colonna di dati ordinati.  
  
 Se si utilizza una trasformazione Ordinamento per ordinare i dati, entrambe le proprietà vengono impostate come richiesto dalla trasformazione Unione o Merge join, ovvero, la trasformazione Ordinamento imposta la proprietà **IsSorted** dell'output su **True**e le proprietà **SortKeyPosition** delle colonne di output.  
  
 Tuttavia, se non si utilizza una trasformazione Ordinamento per ordinare i dati, è necessario impostare manualmente queste proprietà di ordinamento nell'origine o nella trasformazione a monte. Per impostare manualmente le proprietà di ordinamento nell'origine o nella trasformazione a monte, utilizzare la procedura seguente.  
  
#### <a name="to-manually-set-sort-attributes-on-a-source-or-transformation-component"></a>Per impostare manualmente gli attributi di ordinamento in un componente dell'origine o della trasformazione  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Nella scheda **Flusso di dati** individuare l'origine o la trasformazione a monte appropriata o trascinarla dalla **Casella degli strumenti** nell'area di progettazione.  
  
4.  Fare clic sul componente con il pulsante destro del mouse e scegliere **Visualizza editor avanzato**.  
  
5.  Fare clic sulla scheda **Proprietà input e output** .  
  
6.  Fare clic su **Output \<component name>** e impostare la proprietà **IsSorted** su **True**.  
  
    > [!NOTE]  
    >  Se si imposta manualmente la proprietà **IsSorted** dell'output su **True** e se i dati non sono ordinati, quando si esegue il pacchetto alcuni dati potrebbero risultare mancanti o danneggiati nella trasformazione Unione o Merge Join.  
  
7.  Espandere **Colonne di output**.  
  
8.  Fare clic sulla colonna che si vuole indicare come ordinata e impostarne la proprietà **SortKeyPosition** su un valore intero diverso da zero attenendosi alle linee guida seguenti:  
  
    -   Il valore intero deve rappresentare una sequenza numerica che inizia con 1 e che ha incrementi di 1.  
  
    -   Un valore intero positivo indica un ordinamento crescente.  
  
    -   Un valore intero negativo indica un ordinamento decrescente. Se impostato su un numero negativo, il valore assoluto del numero determina la posizione della colonna nella sequenza di ordinamento.  
  
    -   Il valore predefinito 0 indica che la colonna non è ordinata. Lasciare il valore 0 per colonne di output che non vengono incluse nell'ordinamento.  
  
     Come esempio per l'impostazione della proprietà **SortKeyPosition** , considerare l'istruzione Transact-SQL seguente che carica i dati in un'origine:  
  
     `SELECT * FROM MyTable ORDER BY ColumnA, ColumnB DESC, ColumnC`  
  
     Per questa istruzione, impostare la proprietà **SortKeyPosition** per ogni colonna come indicato di seguito:  
  
    -   Impostare la proprietà **SortKeyPosition** di ColumnA su 1. In questo modo viene indicato che ColumnA è la prima colonna da ordinare e che l'ordinamento deve essere crescente.  
  
    -   Impostare la proprietà **SortKeyPosition** di ColumnB su -2. In questo modo viene indicato che ColumnB è la seconda colonna da ordinare e che l'ordinamento deve essere decrescente.  
  
    -   Impostare la proprietà **SortKeyPosition** di ColumnC su 3. In questo modo viene indicato che ColumnC è la terza colonna da ordinare e che l'ordinamento deve essere crescente.  
  
9. Ripetere il passaggio 8 per ogni colonna ordinata.  
  
10. Fare clic su **OK**.  
  
11. Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Trasformazione Unione](../../../integration-services/data-flow/transformations/merge-transformation.md)   
 [Trasformazione Merge join](../../../integration-services/data-flow/transformations/merge-join-transformation.md)   
 [Trasformazioni di Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Percorsi in Integration Services](../../../integration-services/data-flow/integration-services-paths.md)   
 [Attività Flusso di dati](../../../integration-services/control-flow/data-flow-task.md)  
  
  
