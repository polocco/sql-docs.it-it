---
title: Pulizia assembly non utilizzata | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: e03c2b6f-8f39-4382-9cf3-7f766a1bd929
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3edb481894bdf9c4b9ff6228abb27c51b1affc75
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933226"
---
# <a name="unused-assembly-cleanup"></a>Pulizia degli assembly inutilizzati
  L'esempio `AssemblyCleanup` contiene una stored procedure .NET, che consente di eseguire la pulizia degli assembly inutilizzati nel database corrente tramite l'esecuzione di query sui cataloghi di metadati. L'unico parametro, `visible_assemblies`, viene utilizzato per specificare se gli assembly visibili inutilizzati devono essere o meno eliminati. Per impostazione predefinita un valore "false" indica che solo gli assembly invisibili inutilizzati vengono eliminati; in caso contrario vengono eliminati tutti gli assembly inutilizzati. Il set di assembly inutilizzati è formato dagli assembly che non dispongono di alcun punto di ingresso definito (routine/tipi e aggregazioni) e a cui nessun assembly utilizzato fa riferimento direttamente o indirettamente.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per creare ed eseguire questo progetto, è necessario installare il software seguente:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express è disponibile gratuitamente nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sito Web [di documentazione ed esempi di](https://www.microsoft.com/sql-server/sql-server-editions-express)Express  
  
-   Database AdventureWorks, disponibile nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sito Web [per sviluppatori di](https://go.microsoft.com/fwlink/?linkid=62796)  
  
-   .NET Framework SDK 2.0 o versione successiva oppure Microsoft Visual Studio 2005 o versione successiva. .NET Framework SDK è disponibile gratuitamente.  
  
-   È necessario inoltre che siano soddisfatte le condizioni seguenti:  
  
-   Per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usata deve essere abilitata l'integrazione con CLR.  
  
-   Per abilitare l'integrazione con CLR, effettuare le operazioni seguenti:  
  
    #### <a name="enabling-clr-integration"></a>Abilitazione dell'integrazione con CLR  
  
    -   Eseguire i comandi [!INCLUDE[tsql](../../includes/tsql-md.md)] seguenti:  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  Per abilitare CLR, è necessario disporre dell'autorizzazione `ALTER SETTINGS` a livello di server, che viene assegnata implicitamente ai membri dei ruoli predefiniti del server `sysadmin` e `serveradmin`.  
  
-   Il database AdventureWorks deve essere installato nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in uso.  
  
-   Se non si è un amministratore per l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza di in uso, è necessario disporre di un amministratore per concedere l'autorizzazione **CreateAssembly** per completare l'installazione.  
  
## <a name="building-the-sample"></a>Compilazione dell'esempio  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a>Creare ed eseguire l'esempio tramite le istruzioni seguenti:  
  
1.  Aprire un prompt dei comandi di .NET Framework o Visual Studio.  
  
2.  Se necessario, creare una directory per l'esempio. Per questo esempio verrà utilizzata la directory C:\MySample.  
  
3.  In c:\MySample creare `AssemblyCleanup.vb` (per l'esempio Visual Basic) o `AssemblyCleanup.cs` (per l'esempio C#) e copiare nel file il codice di esempio appropriato, Visual Basic o C#, riportato di seguito.  
  
4.  Compilare il codice di esempio dal prompt della riga di comando eseguendo una delle istruzioni seguenti, a seconda del linguaggio scelto.  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Transactions.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /target:library AssemblyCleanup.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /target:library AssemblyCleanup.cs`  
  
5.  Copiare il codice di installazione [!INCLUDE[tsql](../../includes/tsql-md.md)] in un file e salvarlo come `Install.sql` nella directory dell'esempio.  
  
6.  Se l'esempio è installato in una directory diversa da `C:\MySample\`, modificare il file `Install.sql` come indicato, in modo che punti al percorso appropriato.  
  
7.  Distribuire l'assembly e la stored procedure eseguendo  
  
    -   `sqlcmd -E -I -i install.sql`  
  
8.  Copiare lo script di comandi di test [!INCLUDE[tsql](../../includes/tsql-md.md)] in un file e salvarlo come `test.sql` nella directory dell'esempio.  
  
9. Eseguire lo script di test con il comando seguente  
  
    -   `sqlcmd -E -I -i test.sql`  
  
10. Copiare lo script di pulizia [!INCLUDE[tsql](../../includes/tsql-md.md)] in un file e salvarlo come `cleanup.sql` nella directory dell'esempio.  
  
11. Eseguire lo script con il comando seguente  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a>Codice di esempio  
 Di seguito sono illustrati i listati di codice per l'esempio.  
  
 C#  
  
```  
using System;  
using System.Text;  
using System.Diagnostics;  
using System.Data.SqlClient;  
using System.Collections.Generic;  
using System.Globalization;  
using Microsoft.SqlServer.Server;  
  
    /// <summary>  
    /// Defines a CLR user defined function CleanupUnusedAssemblies that drops   
    /// all the invisible assemblies with no references.  
    /// </summary>  
    public sealed class AssemblyCleanup  
    {  
        private SqlTransaction transaction;  
  
        internal class AssemblySet  
        {  
            private Dictionary<int, object> m_dictionary;  
  
            /// <summary>  
            /// Initialize internal structures  
            /// </summary>  
            /// <returns></returns>  
            public AssemblySet()  
            {  
                m_dictionary = new Dictionary<int, object>();  
            }  
  
            /// <summary>  
            /// Adds an assembly id into the current AssemblySet if it is not   
            /// already part of it.  
            /// </summary>  
            /// <returns></returns>  
            public void Add(int assemblyId)  
            {  
                if (!m_dictionary.ContainsKey(assemblyId))  
                {  
                    m_dictionary.Add(assemblyId, null);  
                }  
            }  
  
            /// <summary>  
            /// Number of assembly ids stored in this instance  
            /// </summary>  
            /// <returns></returns>  
            public int Count  
            {  
                get  
                {  
                    return m_dictionary.Count;  
                }  
            }  
  
            /// <summary>  
            /// Returns the comma-separated list of assembly ids contained in this instance  
            /// </summary>  
            /// <returns>string value that represents a comma-separated list   
            /// of assembly ids</returns>  
            public string ToCommaSeparatedList()  
            {  
                StringBuilder sb = new StringBuilder();  
  
                if (m_dictionary.Count > 0)  
                {  
                    foreach (KeyValuePair<int, object> kv in m_dictionary)  
                    {  
                        sb.Append(kv.Key);  
                        sb.Append(",");  
                    }  
  
                    sb.Length--; // remove the trailing comma  
                }  
  
                return sb.ToString();  
            }  
        }  
  
        /// <summary>  
        /// Initializes an instance of AssemblyCleanup with a SqlTransaction  
        /// </summary>  
        /// <returns></returns>  
        private AssemblyCleanup(SqlTransaction transaction)  
        {  
            this.transaction = transaction;  
        }  
  
        /// <summary>  
        /// Helper function that creates a SqlCommand object as part of the current   
        /// transaction  
        /// </summary>  
        /// <returns></returns>  
        private SqlCommand CreateCommandInTransaction()  
        {  
            SqlCommand cmd = this.transaction.Connection.CreateCommand();  
  
            cmd.Transaction = this.transaction;  
  
            return cmd;  
        }  
  
        /// <summary>  
        /// Helper function that constructs an AssemblySet instance using the   
        /// first column of the resultset resulting from the query that was passed in.  
        /// </summary>  
        /// <param name="query"></param>  
        /// <returns></returns>  
        private AssemblySet GetAssemblySetFromQuery(string query)  
        {  
            SqlCommand cmd = CreateCommandInTransaction();  
  
            AssemblySet set = new AssemblySet();  
  
            cmd.CommandText = query;  
            using (SqlDataReader rd = cmd.ExecuteReader())  
            {  
                while (rd.Read())  
                {  
                    set.Add(rd.GetInt32(0));  
                }  
            }  
  
            return set;  
        }  
  
        /// <summary>  
        /// Constructs a DROP ASSEMBLY T-SQL statement using the AssemblySet   
        /// passed in as a parameter.  
        /// </summary>  
        /// <param name="set"></param>  
        /// <returns></returns>  
        private void DropAssemblies(AssemblySet unusedAssemblySet)  
        {  
            if (unusedAssemblySet.Count > 0)  
            {  
                StringBuilder assemblyNamesToDrop = new StringBuilder();  
  
                // Gather the list of assembly names we will drop later  
                SqlCommand cmd = CreateCommandInTransaction();  
  
                cmd.CommandText = String.Format(CultureInfo.InvariantCulture,  
                    "SELECT name FROM sys.assemblies WHERE assembly_id IN ({0});",  
                    unusedAssemblySet.ToCommaSeparatedList());  
                using (SqlDataReader rd = cmd.ExecuteReader())  
                {  
                    while (rd.Read())  
                    {  
                        assemblyNamesToDrop.Append("[");  
                        assemblyNamesToDrop.Append(rd.GetString(0));  
                        assemblyNamesToDrop.Append("],");  
                    }  
                }  
  
                // Remove trailing comma  
                assemblyNamesToDrop.Length--;  
  
                // Drop all assemblies at the same time  
                cmd.CommandText = String.Format(CultureInfo.InvariantCulture,  
                    "DROP ASSEMBLY {0}", assemblyNamesToDrop.ToString());  
                cmd.ExecuteNonQuery();  
            }  
        }  
  
        /// <summary>  
        /// Serves as the stored procedure entry point and drives the process   
        /// of expanding the "assemblies in use" set, negating it, and   
        /// dropping the results  
        /// </summary>  
        /// <param name="visibleAssemblies">If set to true, will also drop   
        /// unused visible assemblies. Otherwise, will only drop unused invisible   
        /// assemblies.</param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlProcedure()]  
        public static void CleanupUnusedAssemblies(bool visibleAssemblies)  
        {  
            bool succeeded = false;  
            SqlConnection conn;  
            SqlTransaction transaction;  
            string sqlStatement;  
            AssemblySet assembliesToDrop;  
            AssemblyCleanup assemblyCleanup;  
  
            conn = new SqlConnection("context connection=true");  
            conn.Open();  
            transaction = conn.BeginTransaction();  
  
            try  
            {  
                // Create a set of assemblies in use by looking at   
                // the metadata of the current database  
                sqlStatement =  
                    "DECLARE @UsedAssembly TABLE (AssemblyID int NOT NULL); " +  
                    "DECLARE @RowCount int; " +  
                    "INSERT INTO @UsedAssembly " +  
                    "SELECT DISTINCT([assembly_id]) " +  
                    "FROM sys.assembly_modules " +  
                    "UNION " +  
                    "SELECT [assembly_id] " +  
                    "FROM sys.assembly_types; " +  
                    "SET @RowCount = @@ROWCOUNT; " +  
                    "WHILE @RowCount > 0 " +  
                    "BEGIN " +  
                    "INSERT INTO @UsedAssembly " +  
                    "SELECT [referenced_assembly_id] " +  
                    "FROM sys.assembly_references ar " +  
                    "INNER JOIN @UsedAssembly ua " +  
                    "ON ar.[assembly_id] = ua.AssemblyID " +  
                    "WHERE NOT EXISTS (SELECT * FROM @UsedAssembly WHERE AssemblyID = [referenced_assembly_id]) " +  
                    "SET @RowCount = @@ROWCOUNT; " +  
                    "END;";  
  
                if (visibleAssemblies)  
                {  
                    sqlStatement +=  
                        "SELECT assembly_id " +  
                        "FROM sys.assemblies " +  
                        "WHERE assembly_id NOT IN (SELECT AssemblyID FROM @UsedAssembly);";  
                }  
                else  
                {  
                    sqlStatement +=  
                        "SELECT assembly_id " +  
                        "FROM sys.assemblies " +  
                        "WHERE assembly_id NOT IN (SELECT AssemblyID FROM @UsedAssembly) " +  
                        "    AND is_visible = 0;";  
                }  
  
                // This marks the beginning of the transaction  
                assemblyCleanup = new AssemblyCleanup(transaction);  
  
                // Assemblies that are currently in use  
                assembliesToDrop  
                    = assemblyCleanup.GetAssemblySetFromQuery(sqlStatement);  
  
                assemblyCleanup.DropAssemblies(assembliesToDrop);  
  
                // Mark as succeeded  
                succeeded = true;  
            }  
            finally  
            {  
                // We must guarantee that we explicitly call either Commit()   
                // or Rollback() before we return.  
                if (succeeded)  
                {  
                    transaction.Commit();  
                }  
                else  
                {  
                    transaction.Rollback();  
                }  
                conn.Dispose();  
            }  
        }  
    }  
  
```  
  
 Visual Basic  
  
```  
Imports Microsoft.SqlServer.Server  
Imports Microsoft.VisualBasic  
Imports System  
Imports System.Collections  
Imports System.Collections.Generic  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Diagnostics  
Imports System.Globalization  
Imports System.Text  
Imports System.Transactions  
Public NotInheritable Class AssemblyCleanup  
    Private transaction As SqlTransaction  
  
    Friend Class AssemblySet  
        Private m_dictionary As Dictionary(Of Integer, Object)  
  
        ''' <summary>  
        ''' Initialize internal structures  
        ''' </summary>  
        ''' <returns></returns>  
        Public Sub New()  
            m_dictionary = New Dictionary(Of Integer, Object)  
        End Sub  
  
        ''' <summary>  
        ''' Adds an assembly id into the current AssemblySet if it is not already part of it.  
        ''' </summary>  
        ''' <returns></returns>  
        Public Sub Add(ByVal assemblyId As Integer)  
            If Not m_dictionary.ContainsKey(assemblyId) Then  
                m_dictionary.Add(assemblyId, Nothing)  
            End If  
        End Sub  
  
        ''' <summary>  
        ''' Number of assembly ids stored in this instance  
        ''' </summary>  
        ''' <returns></returns>  
        Public ReadOnly Property Count() As Integer  
            Get  
                Return m_dictionary.Count  
            End Get  
        End Property  
  
        ''' <summary>  
        ''' Returns the comma-separated list of assembly ids contained in this instance  
        ''' </summary>  
        ''' <returns>string value that represents a comma-separated list of assembly ids</returns>  
        Public Function ToCommaSeparatedList() As String  
            Dim sb As New StringBuilder()  
  
            If m_dictionary.Count > 0 Then  
                For Each kv As KeyValuePair(Of Integer, Object) In m_dictionary  
                    If (True) Then  
                        sb.Append(kv.Key)  
                        sb.Append(",")  
                    End If  
                Next  
  
                sb.Length -= 1 ' remove the trailing comma  
            End If  
  
            Return sb.ToString()  
  
        End Function  
    End Class  
  
    ''' <summary>  
    ''' Initializes an instance of AssemblyCleanup with a SqlTransaction  
    ''' </summary>  
    ''' <returns></returns>  
    Private Sub New(ByVal trans As SqlTransaction)  
        Me.transaction = trans  
    End Sub  
  
    ''' <summary>  
    ''' Helper function that creates a SqlCommand object as part of the   
    ''' current transaction  
    ''' </summary>  
    ''' <returns></returns>  
    Private Function CreateCommandInTransaction() As SqlCommand  
        Dim cmd As SqlCommand = transaction.Connection.CreateCommand()  
  
        cmd.Transaction = Me.transaction  
  
        Return cmd  
    End Function  
  
    ''' <summary>  
    ''' Helper function that constructs an AssemblySet instance using the   
    ''' first column of the resultset resulting from the query that was passed in.  
    ''' </summary>  
    ''' <param name="query"></param>  
    ''' <returns></returns>  
    Private Function GetAssemblySetFromQuery(ByVal query As String) As AssemblySet  
        Dim cmd As SqlCommand = CreateCommandInTransaction()  
        Dim [set] As New AssemblySet()  
  
        cmd.CommandText = query  
        Dim rd As SqlDataReader = cmd.ExecuteReader()  
        Try  
            While rd.Read()  
                [set].Add(rd.GetInt32(0))  
            End While  
        Finally  
            rd.Dispose()  
        End Try  
  
        Return [set]  
    End Function  
  
    ''' <summary>  
    ''' Constructs a DROP ASSEMBLY T-SQL statement using the AssemblySet   
    ''' passed in as a parameter.  
    ''' </summary>  
    ''' <param name="set"></param>  
    ''' <returns></returns>  
    Private Sub DropAssemblies(ByVal unusedAssemblySet As AssemblySet)  
        If unusedAssemblySet.Count > 0 Then  
            Dim assemblyNamesToDrop As New StringBuilder()  
  
            ' Gather the list of assembly names we will drop later  
            Dim cmd As SqlCommand = CreateCommandInTransaction()  
  
            cmd.CommandText = String.Format(CultureInfo.InvariantCulture, _  
                "SELECT name FROM sys.assemblies WHERE assembly_id IN ({0});", _  
                unusedAssemblySet.ToCommaSeparatedList())  
            Dim rd As SqlDataReader = cmd.ExecuteReader()  
            Try  
                While rd.Read()  
                    assemblyNamesToDrop.Append("[")  
                    assemblyNamesToDrop.Append(rd.GetString(0))  
                    assemblyNamesToDrop.Append("],")  
                End While  
            Finally  
                rd.Dispose()  
            End Try  
  
            ' Remove trailing comma  
            assemblyNamesToDrop.Length -= 1  
  
            ' Drop all assemblies at the same time  
            cmd.CommandText = String.Format(CultureInfo.InvariantCulture, _  
                "DROP ASSEMBLY {0}", assemblyNamesToDrop.ToString())  
            cmd.ExecuteNonQuery()  
        End If  
    End Sub  
  
    ''' <summary>  
    ''' Serves as the stored procedure entry point and drives the process of   
    ''' expanding the "assemblies in use" set, negating it, and dropping   
    ''' the results.  
    ''' </summary>  
    ''' <param name="visibleAssemblies">If set to true, will also drop unused   
    ''' visible assemblies. Otherwise, will only drop unused invisible assemblies.</param>  
    ''' <returns></returns>  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub CleanupUnusedAssemblies(ByVal visibleAssemblies As Boolean)  
  
        Dim succeeded As Boolean = False  
        Dim conn As SqlConnection  
        Dim transaction As SqlTransaction  
        Dim sqlStatement As String  
        Dim assembliesToDrop As AssemblySet  
        Dim assemblyCleanup As AssemblyCleanup  
  
        conn = New SqlConnection("context connection=true")  
        conn.Open()  
        transaction = conn.BeginTransaction()  
  
        Try  
            ' Create a set of assemblies in use by looking at   
            ' the metadata of the current database  
            sqlStatement = "DECLARE @UsedAssembly TABLE (AssemblyID int NOT NULL); " & _  
                "DECLARE @RowCount int; " & _  
                "INSERT INTO @UsedAssembly " & _  
                "SELECT DISTINCT([assembly_id]) " & _  
                "FROM sys.assembly_modules " & _  
                "UNION " & _  
                "SELECT [assembly_id] " & _  
                "FROM sys.assembly_types; " & _  
                "SET @RowCount = @@ROWCOUNT; " & _  
                "WHILE @RowCount > 0 " & _  
                "BEGIN " & _  
                "INSERT INTO @UsedAssembly " & _  
                "SELECT [referenced_assembly_id] " & _  
                "FROM sys.assembly_references ar " & _  
                "INNER JOIN @UsedAssembly ua " & _  
                "ON ar.[assembly_id] = ua.AssemblyID " & _  
                "WHERE NOT EXISTS (SELECT * FROM @UsedAssembly WHERE AssemblyID = [referenced_assembly_id]) " & _  
                "SET @RowCount = @@ROWCOUNT; " & _  
                "END;"  
  
            If visibleAssemblies Then  
                sqlStatement += "SELECT assembly_id " & _  
                    "FROM sys.assemblies " & _  
                    "WHERE assembly_id NOT IN (SELECT AssemblyID FROM @UsedAssembly);"  
            Else  
                sqlStatement += "SELECT assembly_id " & _  
                    "FROM sys.assemblies " & _  
                    "WHERE assembly_id NOT IN (SELECT AssemblyID FROM @UsedAssembly) " & _  
                    "    AND is_visible = 0;"  
            End If  
  
            ' This marks the beginning of the transaction  
            assemblyCleanup = New AssemblyCleanup(transaction)  
  
            ' Assemblies that are currently in use  
            assembliesToDrop _  
                = assemblyCleanup.GetAssemblySetFromQuery(sqlStatement)  
  
            assemblyCleanup.DropAssemblies(assembliesToDrop)  
  
            ' Mark as succeeded  
            succeeded = True  
        Finally  
            ' We must guarantee that we explicitly call either Commit()   
            ' or Rollback() before we return.  
            If succeeded Then  
                transaction.Commit()  
            Else  
                transaction.Rollback()  
            End If  
            conn.Dispose()  
        End Try  
    End Sub  
End Class  
```  
  
 Di seguito è illustrato lo script di installazione [!INCLUDE[tsql](../../includes/tsql-md.md)] (`Install.sql`) che consente la distribuzione dell'assembly e la creazione della stored procedure nel database.  
  
```  
USE AdventureWorks;  
GO  
IF EXISTS (SELECT * FROM sys.objects WHERE name = N'CleanupUnusedAssemblies')  
DROP PROCEDURE CleanupUnusedAssemblies;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE name = N'AssemblyCleanupUtils')   
DROP ASSEMBLY AssemblyCleanupUtils;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
Set @SamplesPath = 'C:\MySample\'  
  
CREATE ASSEMBLY AssemblyCleanupUtils   
FROM @SamplesPath + 'AssemblyCleanup.dll'   
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE CleanupUnusedAssemblies (  
@visible_assemblies bit  
) AS  
EXTERNAL NAME [AssemblyCleanupUtils].[AssemblyCleanup].CleanupUnusedAssemblies;  
GO  
```  
  
 Di seguito è illustrato lo script `test.sql` che consente di testare l'esempio eseguendo la stored procedure.  
  
```  
USE AdventureWorks;  
GO  
  
PRINT 'Before cleanup...'  
SELECT [name] FROM sys.assemblies;  
GO  
  
-- pass in false, which means the cleanup will only include invisible assemblies  
EXEC dbo.CleanupUnusedAssemblies false;  
GO  
  
PRINT 'After cleanup'  
SELECT [name] FROM sys.assemblies;  
```  
  
 Il codice [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente consente di rimuovere l'assembly e la stored procedure dal database.  
  
```  
USE AdventureWorks;  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE name = N'CleanupUnusedAssemblies')  
DROP PROCEDURE CleanupUnusedAssemblies;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE name = N'AssemblyCleanupUtils')   
DROP ASSEMBLY AssemblyCleanupUtils;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Scenari di utilizzo ed esempi per l'integrazione con CLR &#40;Common Language Runtime&#41;](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
