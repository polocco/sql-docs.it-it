---
description: Gestione delle password (MySQLToSQL)
title: Gestione delle password (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 07/06/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Password management, importing or exporting encrypted password
- Password management, securing password
ms.assetid: 4ffbc587-ea3f-49ad-bc42-a654f672325e
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 50238d3cbcd65077ad724d41c907221d5d8be998
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/13/2020
ms.locfileid: "91988527"
---
# <a name="managing-passwords-mysqltosql"></a>Gestione delle password (MySQLToSQL)
Questo articolo descrive come proteggere le password del database e la procedura per importarli o esportarli tra server.
  
## <a name="securing-password"></a>Sicurezza della password  
SSMA consente di proteggere la password di un database.  
  
Per implementare una connessione protetta, attenersi alla procedura seguente:  
  
Specificare una password valida utilizzando uno dei tre metodi seguenti:  
  
1.  **Testo non crittografato:** Digitare la password del database nell'attributo value del nodo ' password '. Si trova nel nodo definizione server della sezione server del file di script o di connessione al server.  
  
    Le password in testo non crittografato non sono sicure. Pertanto, nell'output della console verrà visualizzato il seguente messaggio di avviso: *"server &lt; -ID &gt; password è disponibile in formato testo non protetto, l'applicazione console SSMA fornisce un'opzione per proteggere la password tramite crittografia. per ulteriori informazioni, vedere l'opzione-SecurePassword nel file della Guida di SSMA."*  
  
    **Password crittografate:** La password specificata, in questo caso, viene archiviata in formato crittografato nel computer locale in ProtectedStorage. SSMA.  
  
    -   **Protezione delle password**  
  
        -   Eseguire `SSMAforMySQLConsole.exe` con `-securepassword` e aggiungere switch alla riga di comando passando la connessione al server o il file di script contenente il nodo password nella sezione relativa alla definizione del server.  
  
        -   Al prompt, all'utente viene richiesto di immettere la password del database e di confermarla.  
  
            Gli ID di definizione del server e le password crittografate corrispondenti vengono archiviati in un file nel computer locale  
            
            **Esempio 1:**
            
            1. Specificare la password
            
            2. `C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ VariableValueFileSample.xml"`
            
            3. Immettere la password per server_id ' XXX_1': xxxxxxx
            
            4. Immettere nuovamente la password per server_id ' XXX_1': xxxxxxx
            
            **Esempio 2:**
            
            1. `C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for MySQL\Sample Console Scripts\ VariableValueFileSample.xml" -o`
            
            2. Immettere la password per server_id ' source_1': xxxxxxx
            
            3. Immettere nuovamente la password per server_id ' source_1': xxxxxxx
            
            4. Immettere la password per server_id ' target_1': xxxxxxx
            
            5. Immettere nuovamente la password per server_id ' destinazione _1': xxxxxxx
            
    -   **Rimozione delle password crittografate**  
  
        Eseguire `SSMAforMySQLConsole.exe` con l' `-securepassword` opzione e `-remove` nella riga di comando passando gli ID server per rimuovere le password crittografate dal file di archiviazione protetto presente nel computer locale.  
  
        Esempio:  

        ```console
        C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -remove all
        C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -remove "source_1,target_1"  
        ```
  
    -   **Elenco di ID server le cui password sono crittografate**  
  
        Eseguire `SSMAforMySQLConsole.exe` con `-securepassword` e `-list` passare alla riga di comando per elencare tutti gli ID server le cui password sono state crittografate.  
  
        Esempio:  
        
        ```console
        C:\SSMA\SSMAforMySQLConsole.EXE -securepassword -list  
        ```
  
    > [!NOTE]  
    > 1.  La password in testo non crittografato indicato nel file di connessione dello script o del server ha la precedenza sulla password crittografata in un file protetto.  
    > 2.  Se nella sezione server del file di connessione del server o del file di script non è presente alcuna password o se non è stata protetta nel computer locale, nella console viene richiesto di immettere la password.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Esportazione o importazione di password crittografate  
L'applicazione console SSMA consente di esportare le password di database crittografate presenti in un file nel computer locale in un file protetto e viceversa. Consente di rendere le password crittografate indipendenti dal computer.

La funzionalità di esportazione consente di leggere l'ID e la password del server dall'archiviazione protetta locale e di salvare le informazioni in un file crittografato. All'utente viene richiesto di immettere la password per il file protetto. Verificare che la password immessa sia di 8 caratteri o superiore. Questo file protetto è portabile tra computer diversi.

La funzionalità di importazione legge le informazioni relative all'ID server e alla password dal file protetto. All'utente viene richiesto di immettere la password per il file protetto e di accodare le informazioni all'archivio locale protetto.  
  
### <a name="export-example"></a>Esempio di esportazione:  

1. Esporta password

2. Immettere la password per la protezione del file esportato

3. C:\SSMA\SSMAforMySQLConsole.EXE-SecurePassword-Esporta tutti i file "machine1passwords. file"

4. Immettere la password per la protezione del file esportato: xxxxxxxx

5. Confermare la password: xxxxxxxx

6. C:\SSMA\SSMAforMySQLConsole.EXE-p-e "MySQLDB_1_1, Sql_1" "machine2passwords. file"

7. Immettere la password per la protezione del file esportato: xxxxxxxx

8. Confermare la password: xxxxxxxx  
  
### <a name="import-example"></a>Esempio di importazione:  

1. Importare una password crittografata

2. Immettere la password per la protezione del file importato

3. C:\SSMA\SSMAforMySQLConsole.EXE-SecurePassword-importare tutti i file "machine1passwords. file"

4. Immettere la password per importare i server dal file crittografato: xxxxxxxx

5. Confermare la password: xxxxxxxx

6. C:\SSMA\SSMAforMySQLConsole.EXE-p-i "MySQLDB_1, Sql_1" "machine2passwords. file"

7. Immettere la password per importare i server dal file crittografato: xxxxxxxx

8. Confermare la password: xxxxxxxx  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione della console SSMA (MySQL)](./executing-the-ssma-console-mysqltosql.md)  
