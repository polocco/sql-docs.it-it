
<!--
### Code examples for Azure cloud differ slightly from on-premises
  Or.....
### Code examples can differ for Azure SQL Database
-->

Alcuni esempi di codice Transact-SQL scritti per SQL Server locale richiedono qualche piccola modifica per funzionare nel servizio database SQL di Azure nel cloud. Una categoria di questi esempi di codice prevede viste di sistema i cui prefissi dei nomi differiscono leggermente tra i due sistemi di database:

- **server\_** &nbsp; - &nbsp; _prefisso per locale_
- **database\_** &nbsp; - &nbsp; _prefisso per il database SQL di Azure_

Come riferimento visivo, la tabella seguente elenca e confronta due subset delle viste di sistema. Per brevità, i subset sono limitati ai nomi di vista che contengono anche la stringa `_event`. I nomi dei subset hanno prefissi diversi perché derivano dai due diversi sistemi di database.

| Nome dalla versione 2017 locale | Nome dal servizio cloud |
| :------------------------- | :---------------------- |
| server_event_notifications<br />server_event_session_actions<br />server_event_session_events<br />server_event_session_fields<br />server_event_session_targets<br />server_event_sessions<br />server_events<br />server_trigger_events | database_event_session_actions<br />database_event_session_events<br />database_event_session_fields<br />database_event_session_targets<br />database_event_sessions |
| &nbsp; | &nbsp; |

I due elenchi nella tabella precedente sono aggiornati al giugno 2019. Il contenuto della tabella, tuttavia, può essere obsoleto, perché non viene aggiornato in questo articolo. Per ottenere elenchi accurati, eseguire l'istruzione T-SQL SELECT seguente. Eseguire l'istruzione SELECT due volte, una volta per ciascun sistema di database.

```sql
SELECT name
    FROM sys.all_objects
    WHERE
        (name LIKE 'database\_%' { ESCAPE '\' } OR
         name LIKE 'server\_%' { ESCAPE '\' })
        AND name LIKE '%\_event%' { ESCAPE '\' }
        AND type = 'V'
    ORDER BY name;
```

<!--
The creation of this docs/includes/ file was prompted by Issue 2211 (https://github.com/MicrosoftDocs/sql-docs/issues/2211).
Initial PR was PR 10427 (https://github.com/MicrosoftDocs/sql-docs-pr/pull/10427).
The complaint was that a specific T-SQL code block failed on Azure SQL Database.

GeneMi  ,  2019/05/28
-->
