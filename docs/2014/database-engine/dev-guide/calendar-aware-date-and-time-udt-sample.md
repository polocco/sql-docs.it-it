---
title: Esempio di data e ora in grado di riconoscere il calendario | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: cfcf8516-0e7b-4ca4-8bd8-8b2511a50308
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c2636d417bb9956ac56885686b3512cc3c119cd7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "76929497"
---
# <a name="calendar-aware-date-and-time-udt-sample"></a>Esempio di data e ora in grado di riconoscere il calendario
  L'archiviazione di date sotto forma di stringhe può provocare confusione in quanto le date non hanno alcun significato se non si conosce il sistema di calendario utilizzato. Nell'esempio `CADatetime` vengono illustrati due tipi di dati definiti dall'utente, `CADatetime` e `CADate`, che consentono la gestione di data e ora con supporto del calendario.  
  
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
  
3.  In c:\MySample creare `CalendarAware.cs` e copiare il codice C# di esempio, riportato di seguito, nel file.  
  
4.  In c:\MySample creare il file `calendars.txt` e copiare il codice di esempio nel file.  
  
5.  In c:\MySample creare il file `calendars.ar-SA.txt` e copiare il codice seguente nel file:  
  
    -   `; the default calendar for this culture`  
  
    -   `DefaultCalendarID = 1`  
  
6.  In c:\MySample creare il file `calendars.ja.txt` e copiare il codice seguente nel file:  
  
    -   `; the default calendar for this culture`  
  
    -   `DefaultCalendarID = 3`  
  
7.  In c:\MySample creare il file `calendars.``zh-CN.txt` e copiare il codice seguente nel file:  
  
    -   `; the default calendar for this culture`  
  
    -   `DefaultCalendarID = 8`  
  
8.  In c:\MySample creare il file `build.com` e copiare il codice seguente nel file:  
  
    -   `resgen calendars.txt`  
  
    -   `resgen calendars.ar-SA.txt`  
  
    -   `resgen calendars.ja.txt`  
  
    -   `resgen calendars.zh-CN.txt`  
  
    -   `al /t:lib /culture:ar-SA /embed:calendars.ar-SA.resources /out:CADatetime.resources.ar-SA.dll`  
  
    -   `al /t:lib /culture:ja /embed:calendars.ja.resources /out:CADatetime.resources.ja.dll`  
  
    -   `al /t:lib /culture:zh-CN /embed:calendars.zh-CN.resources /out:CADatetime.resources.zh-CN.dll`  
  
    -   `al /t:lib /culture:"" /embed:calendars.resources /out:CADatetime.resources.dll`  
  
9. Compilare l'assembly satellite eseguendo la compilazione del file al prompt dei comandi.  
  
10. Compilare il codice di esempio dal prompt della riga di comando eseguendo l'istruzione seguente:  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /out:CADateTime.dll /target:library CalendarAwareDate.cs`  
  
11. Copiare il codice di installazione [!INCLUDE[tsql](../../includes/tsql-md.md)] in un file e salvarlo come `Install.sql` nella directory dell'esempio.  
  
12. Se l'esempio è installato in una directory diversa da `C:\MySample\`, modificare il file `Install.sql` come indicato, in modo che punti al percorso appropriato.  
  
13. Distribuire l'assembly e la stored procedure eseguendo  
  
    -   `sqlcmd -E -I -i install.sql`  
  
14. Copiare lo script di comandi di test [!INCLUDE[tsql](../../includes/tsql-md.md)] in un file e salvarlo come `test.sql` nella directory dell'esempio.  
  
15. Eseguire lo script di test con il comando seguente  
  
    -   `sqlcmd -E -I -i test.sql`  
  
16. Copiare lo script di pulizia [!INCLUDE[tsql](../../includes/tsql-md.md)] in un file e salvarlo come `cleanup.sql` nella directory dell'esempio.  
  
17. Eseguire lo script con il comando seguente  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a>Codice di esempio  
 Di seguito sono illustrati i listati di codice per l'esempio.  
  
 C#  
  
```  
    using System;  
    using System.Data.Sql;  
    using System.Data.SqlTypes;  
    using System.Globalization;  
    using System.Resources;  
    using System.Text;  
    using System.Reflection;  
    using System.Collections.Generic;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using System.Xml.Schema;  
    using System.IO;  
  
[assembly: System.Resources.NeutralResourcesLanguage("", System.Resources.UltimateResourceFallbackLocation.Satellite)]  
  
    /// <summary>  
    /// A date value in the specified calendar system.  
    /// </summary>  
    [Serializable]  
    [Microsoft.SqlServer.Server.SqlUserDefinedType(Microsoft.SqlServer.Server.Format.Native, IsByteOrdered = true)]  
    public struct CADate : INullable, IXmlSerializable  
    {  
        // This type uses days == 0 as the way to designate a NULL value  
  
        const string CADateSchema =  
            "<xs:schema targetNamespace=\"https://schemas.microsoft.com/sqlserver/2004/08/CADate\" " +  
                "xmlns=\"https://schemas.microsoft.com/sqlserver/2004/07/CADate\" " +  
                "elementFormDefault=\"qualified\"" +  
                "xmlns:xs=\"http://www.w3.org/2001/XMLSchema\" >" +  
                "<xs:element name=\"CADate\" >" +  
                    "<xs:complexType mixed=\"true\" >" +  
                        "<xs:attribute name=\"IsNull\" use=\"required\" type=\"xs:boolean\" />" +  
                        "<xs:attribute name=\"Year\" type=\"xs:int\"/>" +  
                        "<xs:attribute name=\"Month\" type=\"xs:int\"/>" +  
                        "<xs:attribute name=\"Day\" type=\"xs:int\"/>" +  
                        "<xs:attribute name=\"Calendar\" type=\"xs:string\"/>" +  
                    "</xs:complexType>" +  
                "</xs:element>" +  
            "</xs:schema>";  
  
        private const uint NullDay = 0;  
  
        private static readonly char[] dateChars = new char[] { 'd', 'M', 'y' };  
        private static readonly char[] allowedSinglePatternChars = new char[] { 'd', 'D', 'm', 'M', 'y', 'Y', '/', '%' };  
        private static readonly char[] allowedDoublePatternChars = new char[] { 'g', '\\' };  
  
        /// <summary>  
        ///     Each tick is 100 nanoseconds.  This conversion factor when multiplied by the number of  
        ///     days yields the number of ticks which make up that day.  Ticks are interesting as they  
        ///     can be used to construct DateTime instances in order to perform various date based computations.  
        /// </summary>  
        private const long DaysToTicksConversionFactor = 10L * 1000L * 1000L * 60L * 60L * 24L;  
  
        /// <summary>  
        /// The number of days since the calendar started (January 1, 1)  
        /// </summary>  
        private uint days;  
  
        /// <summary>  
        /// Which calendar is used for this date and time  
        /// </summary>  
        private byte calendarId;  
  
        /// <summary>  
        /// construct a CADate from the specified datetime using the default calendar.  
        /// </summary>  
        /// <param name="dt">DateTime</param>  
        public CADate(DateTime dt)  
            : this(dt, CalendarInfo.DefaultCalendarId)  
        {  
        }  
  
        /// <summary>  
        /// Construct a calendar aware date for the specified year/month/day using the default calendar  
        /// </summary>  
        /// <param name="year"></param>  
        /// <param name="month"></param>  
        /// <param name="day"></param>  
        public CADate(int year, int month, int day)  
            : this(new DateTime(year, month, day, CalendarInfo.DefaultCalendar))  
        {  
        }  
  
        /// <summary>  
        ///     Converts a DateTime instance and a calendar into a calendar aware date instance.  
        /// </summary>  
        /// <param name="dt">A specific point in time</param>  
        /// <param name="calendarId">A specific calendar system</param>  
        private CADate(DateTime dt, int calendarId)  
        {  
            this.days = (uint)(dt.Ticks / DaysToTicksConversionFactor);  
            this.calendarId = (byte)calendarId;  
        }  
  
        /// <summary>  
        /// the current CADate  
        /// </summary>  
        /// <value></value>  
        public static CADate Now  
        {  
            get  
            {  
                return new CADate(DateTime.Now);  
            }  
        }  
  
        public static string CurrentCalendarName  
        {  
            get  
            {  
                return CalendarInfo.DefaultCalendar.GetType().Name;  
            }  
        }  
  
        /// <summary>  
        /// return the null value for this type  
        /// </summary>  
        /// <value></value>  
        public static CADate Null  
        {  
            get  
            {  
                CADate caDate = new CADate();  
                caDate.days = NullDay;  
  
                return caDate;  
            }  
        }  
  
        /// <summary>  
        /// is this value null  
        /// </summary>  
        /// <value></value>  
        public bool IsNull  
        {  
            get  
            {  
                return this.days == NullDay;  
            }  
        }  
  
        public Calendar Calendar  
        {  
            get  
            {  
                return CalendarInfo.Calendars[this.calendarId];  
            }  
        }  
  
        public string CalendarName  
        {  
            get  
            {  
                return this.Calendar.GetType().Name;  
            }  
        }  
  
        // Accessors for parts of the date   
  
        public int Year  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetYear(this.DateTime);  
            }  
        }  
  
        public int Month  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetMonth(this.DateTime);  
            }  
        }  
  
        public int DayOfMonth  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetDayOfMonth(this.DateTime);  
            }  
        }  
  
        public int Day  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetDayOfYear(this.DateTime);  
            }  
        }  
  
        public uint Days  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.days;  
            }  
        }  
  
        /// <summary>  
        /// convert to datetime  
        /// </summary>  
        /// <value></value>  
        public DateTime DateTime  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return new DateTime(this.Days * DaysToTicksConversionFactor);  
            }  
        }  
  
        /// <summary>  
        /// parse the given string and return a calendar aware date.  
        /// </summary>  
        /// <param name="sqlString"></param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = false,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADate Parse(SqlString sqlString)  
        {  
            if (sqlString.IsNull)  
            {  
                return CADate.Null;  
            }  
  
            return new CADate(DateTime.Parse(sqlString.Value, DateTimeFormatInfo.CurrentInfo));  
        }  
  
        /// <summary>  
        /// Construct a CADate from the specified format, using the current culture  
        /// </summary>  
        /// <param name="data">the string to be parsed</param>  
        /// <param name="format">the format string</param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADate ParseUsingFormat(string data, string format)  
        {  
            if (data == null || format == null)  
            {  
                return CADate.Null;  
            }  
  
            return new CADate(  
                DateTime.ParseExact(  
                data,  
                FilterDateFormat(format),  
                DateTimeFormatInfo.CurrentInfo));  
        }  
  
        // The following methods are intended to be callable from tsql.  That is why they are static.  
  
        /// <summary>  
        /// Create a new CADate from a SqlDateTime  
        /// </summary>  
        /// <param name="sqlDateTime"></param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = false,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADate FromSqlDateTime(SqlDateTime sqlDateTime)  
        {  
            if (sqlDateTime.IsNull)  
            {  
                return CADate.Null;  
            }  
  
            return new CADate(sqlDateTime.Value);  
        }  
  
        /// <summary>  
        /// Creates a CADateTime from a Sql DateTime instance and a specific calendar.  
        /// </summary>  
        /// <param name="sqlDateTime">When</param>  
        /// <param name="calendarName">The short name of the desired calendar</param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = true, IsMutator = false, IsPrecise = false,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADate FromSqlDateTimeAndCalendar(SqlDateTime sqlDateTime, string calendarName)  
        {  
            return new CADate(sqlDateTime.Value, CalendarInfo.GetCalendarId(calendarName));  
        }  
  
        /// <summary>  
        /// Create a new CADate from the year/month/day  
        /// </summary>  
        /// <param name="year"></param>  
        /// <param name="month"></param>  
        /// <param name="day"></param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADate FromYearMonthDay(int year, int month, int day)  
        {  
            return new CADate(year, month, day);  
        }  
  
        public static SqlBoolean operator ==(CADate xCADate, CADate yCADate)  
        {  
            if (xCADate.IsNull || yCADate.IsNull)  
            {  
                return SqlBoolean.Null;  
            }  
  
            return xCADate.DateTime == yCADate.DateTime;  
        }  
  
        public static SqlBoolean operator !=(CADate xCADate, CADate yCADate)  
        {  
            if (xCADate.IsNull || yCADate.IsNull)  
            {  
                return SqlBoolean.Null;  
            }  
  
            return xCADate.DateTime != yCADate.DateTime;  
        }  
  
        // Conversions to other representations of the date  
  
        /// <summary>  
        /// convert the date to string  
        /// </summary>  
        /// <returns></returns>  
        public override string ToString()  
        {  
            if (this.IsNull)  
            {  
                return null;  
            }  
  
            return string.Format(  
                CultureInfo.CurrentUICulture,  
                DayMonthYearFormatString(),  
                this.DayOfMonth,  
                this.Month,  
                this.Year);  
        }  
  
        /// <summary>  
        /// Return a string representation of this date, in the Gregorian calendarId  
        /// </summary>  
        /// <returns></returns>  
        public string ToGregorianString()  
        {  
            if (this.IsNull)  
            {  
                return null;  
            }  
  
            return this.DateTime.ToString("d", DateTimeFormatInfo.CurrentInfo);  
        }  
  
        /// <summary>  
        /// Convert the date to string, using the specified format  
        /// </summary>  
        /// <param name="format">Format string</param>  
        /// <returns></returns>  
        public string ToGregorianStringUsingFormat(string format)  
        {  
            if (this.IsNull)  
            {  
                return null;  
            }  
  
            return this.DateTime.ToString(  
                FilterDateFormat(format),  
                DateTimeFormatInfo.CurrentInfo);  
        }  
  
        /// <summary>  
        /// Convert to sql datetime  
        /// </summary>  
        /// <returns></returns>  
        public SqlDateTime ToSqlDateTime()  
        {  
            return new SqlDateTime(this.DateTime);  
        }  
  
        // Manipulation of date parts  
  
        public CADate AddYears(int years)  
        {  
            return new CADate(this.Calendar.AddYears(this.DateTime, years));  
        }  
  
        public CADate AddDays(int daysToAdd)  
        {  
            return new CADate(this.Calendar.AddDays(this.DateTime, daysToAdd));  
        }  
  
        public CADate AddMonths(int months)  
        {  
            return new CADate(this.Calendar.AddMonths(this.DateTime, months));  
        }  
  
        public double DiffDays(CADate other)  
        {  
            return this.DateTime.Subtract(other.DateTime).TotalDays;  
        }  
  
        // Hashing and comparison methods  
  
        public override int GetHashCode()  
        {  
            return this.DateTime.GetHashCode();  
        }  
  
        public override bool Equals(object obj)  
        {  
            if (!(obj is DateTime))  
            {  
                return false;  
            }  
  
            DateTime dt = (DateTime)obj;  
            return this.DateTime.Equals(dt);  
        }  
  
        public XmlSchema GetSchema()  
        {  
            StringReader sr = new StringReader(CADateSchema);  
            XmlSchema schema = XmlSchema.Read(  
                sr,  
                new ValidationEventHandler(this.ValidationHandler));  
            sr.Dispose();  
  
            return schema;  
        }  
  
        public void ReadXml(XmlReader reader)  
        {  
            if (reader == null)  
            {  
                throw new ArgumentNullException("reader");  
            }  
  
            reader.MoveToContent();  
            if (reader.GetAttribute("IsNull").Equals("true"))  
            {  
                this.days = NullDay;  
            }  
            else  
            {  
                string calendarName = reader.GetAttribute("Calendar");  
                Calendar requestedCalendar   
                    = CalendarInfo.Calendars[CalendarInfo.GetCalendarId(calendarName)];  
  
                this.days = (uint)(new DateTime(  
                    int.Parse(  
                        reader.GetAttribute("Year"),  
                        CultureInfo.CurrentUICulture),  
                    int.Parse(  
                        reader.GetAttribute("Month"),   
                        CultureInfo.CurrentUICulture),  
                    int.Parse(  
                        reader.GetAttribute("Day"),   
                        CultureInfo.CurrentUICulture),  
                        requestedCalendar).Ticks / DaysToTicksConversionFactor);  
            }  
        }  
  
        public void WriteXml(XmlWriter writer)  
        {  
            if (writer == null)  
            {  
                throw new ArgumentNullException("writer");  
            }  
  
            writer.WriteStartElement(  
                "CADate",  
                "https://schemas.microsoft.com/sqlserver/2004/08/CADate");  
            writer.WriteAttributeString("IsNull", this.IsNull.ToString(CultureInfo.CurrentUICulture));  
            if (!this.IsNull)  
            {  
                writer.WriteAttributeString("Year", this.Year.ToString(CultureInfo.CurrentUICulture));  
                writer.WriteAttributeString("Month", this.Month.ToString(CultureInfo.CurrentUICulture));  
                writer.WriteAttributeString("Day", this.Day.ToString(CultureInfo.CurrentUICulture));  
                writer.WriteAttributeString("Calendar", this.Calendar.GetType().ToString());  
            }  
  
            writer.WriteEndElement();  
        }  
  
        // DateTime.ParseExact takes a "format" string which describes how to present the date and time.  
        // This method filters out any formatting characters which conflict   
        private static string FilterDateFormat(string format)  
        {  
            StringBuilder sb = new StringBuilder(format.Length);  
            for (int i = 0; i < format.Length; i++)  
            {  
                char element = format[i];  
                bool doubled = (i + 1 < format.Length)  
                    && (element.Equals(format[i + 1]) || element.Equals('\\'));  
                if (Array.IndexOf<char>(allowedSinglePatternChars, element) > -1 ||  
                    char.IsWhiteSpace(element))  
                {  
                    sb.Append(element);  
                }  
                else if (doubled && (Array.IndexOf<char>(allowedDoublePatternChars, element) > -1))  
                {  
                    sb.Append(element);  
                    sb.Append(format[++i]);  
                }  
            }  
  
            return sb.ToString();  
        }  
  
        // Returns a string suitable for use with string.Format which displays  
        // day, month, and year components in a culture appropriate way.  
        private static string DayMonthYearFormatString()  
        {  
            string cultureDatePattern = CultureInfo.CurrentCulture.DateTimeFormat.ShortDatePattern;  
            return CalendarInfo.SubstitutePositionForCharacters(dateChars, cultureDatePattern);  
        }  
  
        private void ValidationHandler(object sender, ValidationEventArgs args)  
        {  
            throw new ApplicationException(args.Message);  
        }  
    }  
    public static class CalendarInfo  
    {  
        public const byte MaxCalendarId = 0xff;  
        private readonly static char[] stringFormatChars; // = new char[] { 't' };  
        private static readonly Calendar defaultCalendar; // = new GregorianCalendar();  
        private static readonly int defaultCalendarId;  
        private static readonly Calendar[] calendars;  
  
        /// <summary>  
        /// Initialize the calendar array, one for each possible calendar  
        /// </summary>  
        static CalendarInfo()  
        {  
            stringFormatChars = new char[] { 't' };  
  
            ResourceManager rm = new ResourceManager("calendars", Assembly.GetExecutingAssembly());  
  
            int numCalendars = int.Parse(rm.GetString("NumCalendars"), CultureInfo.CurrentUICulture);  
            if (numCalendars > MaxCalendarId)  
            {  
                throw new ArgumentOutOfRangeException("Does not support more than 255 calendars");  
            }  
  
            calendars = new Calendar[numCalendars];  
            for (int i = 0; i < numCalendars; i++)  
            {  
                string typeName = rm.GetString(i.ToString(CultureInfo.CurrentUICulture));  
                calendars[i] = (Calendar)Activator.CreateInstance(Type.GetType(typeName, true));  
            }  
  
            defaultCalendarId = int.Parse(rm.GetString("DefaultCalendarID"), CultureInfo.CurrentUICulture);  
            defaultCalendar = calendars[defaultCalendarId];  
        }  
  
        public static Calendar DefaultCalendar  
        {  
            get  
            {  
                return CalendarInfo.defaultCalendar;  
            }  
        }  
  
        public static int DefaultCalendarId  
        {  
            get  
            {  
                return CalendarInfo.defaultCalendarId;  
            }  
        }  
  
        public static Calendar[] Calendars  
        {  
            get  
            {  
                return CalendarInfo.calendars;  
            }  
        }  
  
        public static int GetCalendarId(string calendarName)  
        {  
            for (int i = 0; i < calendars.Length; i++)  
            {  
                if (calendars[i].GetType().Name == calendarName)  
                {  
                    return i;  
                }  
            }  
  
            throw new ArgumentException("Unknown calendar: " + calendarName);  
        }  
  
        // Returns a string suitable for use with string.Format which displays  
        // either date or datetime components in a culture appropriate way.  
        public static string SubstitutePositionForCharacters(Char[] characters, string pattern)  
        {  
            StringBuilder sb = new StringBuilder();  
            char lastChar = ' ';  
            for (int i = 0; i < pattern.Length; i++)  
            {  
                char c = pattern[i];  
                int position = Array.IndexOf<char>(characters, c);  
                if (position != -1)  
                {  
                    if (lastChar != c)  
                    {  
                        sb.Append('{');  
                        sb.Append(position);  
  
                        // If this isn't a string format char, it is a numeric format char.  
                        // In that case we need to get the correct number of digits from  
                        // the pattern.  
                        if (Array.IndexOf<char>(stringFormatChars, c) == -1)  
                        {  
                            // Decimal number with the appropriate minimum number of digits  
                            sb.AppendFormat(":d{0:d}", CountRun(c, pattern, i));  
                        }  
  
                        sb.Append('}');  
                    }  
                }  
                else  
                {  
                    sb.Append(c);  
                }  
  
                lastChar = c;  
            }  
  
            return sb.ToString();  
        }  
  
        // Given that you have found character c in a pattern, count how many instances of that  
        // character occur at that position before another character or the end of the string is reached.  
  
        public static int CountRun(char chr, string pattern, int start)  
        {  
            if (pattern == null)  
            {  
                throw new ArgumentNullException("pattern");  
            }  
  
            int result = 1;  
            for (int i = start + 1; i < pattern.Length; i++)  
            {  
                if (pattern[i] == chr)  
                {  
                    result += 1;  
                }  
                else  
                {  
                    break;  
                }  
            }  
  
            return result;  
        }  
    }  
    /// <summary>  
    /// A datetime value in the specified calendar system.  
    /// </summary>  
    [Serializable]  
    [Microsoft.SqlServer.Server.SqlUserDefinedType(Microsoft.SqlServer.Server.Format.Native, IsByteOrdered = true, ValidationMethodName = "IsValid")]  
    public struct CADateTime : INullable, IXmlSerializable  
    {  
        const string CADateTimeSchema =  
            "<xs:schema targetNamespace=\"https://schemas.microsoft.com/sqlserver/2004/08/CADateTime\" " +  
                "xmlns=\"https://schemas.microsoft.com/sqlserver/2004/07/CADate\" " +  
                "elementFormDefault=\"qualified\"" +  
                "xmlns:xs=\"http://www.w3.org/2001/XMLSchema\" >" +  
                "<xs:element name=\"CADate\" >" +  
                    "<xs:complexType mixed=\"true\" >" +  
                        "<xs:attribute name=\"IsNull\" use=\"required\" type=\"xs:boolean\" />" +  
                        "<xs:attribute name=\"Year\" type=\"xs:int\"/>" +  
                        "<xs:attribute name=\"Month\" type=\"xs:int\"/>" +  
                        "<xs:attribute name=\"Day\" type=\"xs:int\"/>" +  
                        "<xs:attribute name=\"Hour\" type=\"xs:int\">" +  
                        "<xs:attribute name=\"Minute\" type=\"xs:int\">" +  
                        "<xs:attribute name=\"Second\" type=\"xs:int\">" +  
                        "<xs:attribute name=\"Calendar\" type=\"xs:string\"/>" +  
                    "</xs:complexType>" +  
                "</xs:element>" +  
            "</xs:schema>";  
  
        static readonly char[] datetimeChars = new char[] { 'd', 'M', 'y', 'h', 'H', 'm', 's', 't' };  
  
        // This type uses ticks == 0 as the way to designate a NULL value  
        private const long NullTicks = 0;  
  
        /// <summary>  
        /// What date and time this is as ticks from midnight January 1, 1  
        /// </summary>  
        private long dtTicks;  
  
        /// <summary>  
        /// Which calendar is used for this date and time  
        /// </summary>  
        private byte calendarId;  
  
        /// <summary>  
        /// Construct a CADateTime from the specified datetime using the default calendar.  
        /// </summary>  
        /// <param name="dt">DateTime</param>  
        public CADateTime(DateTime dt)  
            : this(dt, CalendarInfo.DefaultCalendarId)  
        {  
        }  
  
        /// <summary>  
        /// Construct a calendar aware datetime for the specified year/month/day using the default calendar  
        /// </summary>  
        /// <param name="year"></param>  
        /// <param name="month"></param>  
        /// <param name="day"></param>  
        public CADateTime(int year, int month, int day)  
            : this(new DateTime(year, month, day, CalendarInfo.DefaultCalendar))  
        {  
        }  
  
        /// <summary>  
        ///     Converts a DateTime instance and a calendar into a calendar aware datetime instance.  
        /// </summary>  
        /// <param name="dt">A specific point in time</param>  
        /// <param name="calendarId">A specific calendar system</param>  
        private CADateTime(DateTime dt, int calendarId)  
        {  
            this.dtTicks = dt.Ticks;  
            this.calendarId = (byte)calendarId;  
        }  
  
        /// <summary>  
        /// return the null value for this type  
        /// </summary>  
        /// <value></value>  
        public static CADateTime Null  
        {  
            get  
            {  
                CADateTime dt = new CADateTime();  
                dt.dtTicks = NullTicks;  
  
                return dt;  
            }  
        }  
  
        /// <summary>  
        /// the current CADateTime  
        /// </summary>  
        /// <value></value>  
        public static CADateTime Now  
        {  
            get  
            {  
                return new CADateTime(DateTime.Now);  
            }  
        }  
  
        public static string CurrentCalendarName  
        {  
            get  
            {  
                return CalendarInfo.DefaultCalendar.GetType().Name;  
            }  
        }  
  
        /// <summary>  
        /// is this value null  
        /// </summary>  
        /// <value></value>  
        public bool IsNull  
        {  
            get  
            {  
                return this.Ticks == NullTicks;  
            }  
        }  
  
        public int Year  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetYear(this.DateTime);  
            }  
        }  
  
        public int Month  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetMonth(this.DateTime);  
            }  
        }  
  
        public int DayOfMonth  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetDayOfMonth(this.DateTime);  
            }  
        }  
  
        public int Day  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetDayOfYear(this.DateTime);  
            }  
        }  
  
        public int Hour  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetHour(this.DateTime);  
            }  
        }  
  
        public int Minute  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetMinute(this.DateTime);  
            }  
        }  
  
        public int Second  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetSecond(this.DateTime);  
            }  
        }  
  
        /// <summary>  
        /// Milliseconds  
        /// </summary>  
        /// <value></value>  
        public double Milliseconds  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.Calendar.GetMilliseconds(this.DateTime);  
            }  
        }  
  
        public long Ticks  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get  
            {  
                return this.dtTicks;  
            }  
        }  
  
        /// <summary>  
        /// convert to datetime  
        /// </summary>  
        /// <value></value>  
        public DateTime DateTime  
        {  
            [Microsoft.SqlServer.Server.SqlMethod(IsDeterministic = true, IsPrecise = true)]  
            get { return new DateTime(this.dtTicks); }  
        }  
  
        public Calendar Calendar  
        {  
            get  
            {  
                return CalendarInfo.Calendars[this.calendarId];  
            }  
        }  
  
        public string CalendarName  
        {  
            get  
            {  
                return this.Calendar.GetType().Name;  
            }  
        }  
  
        /// <summary>  
        /// parse the given string and return a calendar aware datetime.  
        /// </summary>  
        /// <param name="sqlString"></param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADateTime Parse(SqlString sqlString)  
        {  
            if (sqlString.IsNull)  
            {  
                return CADateTime.Null;  
            }  
  
            return new CADateTime(  
                DateTime.Parse(  
                    sqlString.Value,  
                    DateTimeFormatInfo.CurrentInfo));  
        }  
  
        /// <summary>  
        /// Construct a CADateTime from the specified format, using the current culture  
        /// </summary>  
        /// <param name="data">the string to be parsed</param>  
        /// <param name="format">the format string</param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADateTime ParseUsingFormat(string data, string format)  
        {  
            if (data == null || format == null)  
            {  
                return CADateTime.Null;  
            }  
  
            return new CADateTime(DateTime.ParseExact(data, format, DateTimeFormatInfo.CurrentInfo));  
        }  
  
        /// <summary>  
        /// Create a new CADateTime from a SqlDateTime  
        /// </summary>  
        /// <param name="sqlDateTime"></param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADateTime FromSqlDateTime(SqlDateTime sqlDateTime)  
        {  
            if (sqlDateTime.IsNull)  
            {  
                return CADateTime.Null;  
            }  
  
            return new CADateTime(sqlDateTime.Value);  
        }  
  
        /// <summary>  
        /// Creates a CADateTime from a Sql DateTime instance and a specific calendar.  
        /// </summary>  
        /// <param name="sqlDateTime">When</param>  
        /// <param name="calendarName">The short name of the desired calendar</param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = true, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADateTime FromSqlDateTimeAndCalendar(SqlDateTime sqlDateTime, string calendarName)  
        {  
            return new CADateTime(sqlDateTime.Value, CalendarInfo.GetCalendarId(calendarName));  
        }  
  
        /// <summary>  
        /// Create a new CADateTime from the year/month/day  
        /// </summary>  
        /// <param name="year"></param>  
        /// <param name="month"></param>  
        /// <param name="day"></param>  
        /// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlMethod(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.None, IsDeterministic = false, IsMutator = false, IsPrecise = true,  
        SystemDataAccess = Microsoft.SqlServer.Server.SystemDataAccessKind.None)]  
        public static CADateTime FromYearMonthDay(int year, int month, int day)  
        {  
            return new CADateTime(year, month, day);  
        }  
  
        public static SqlBoolean operator ==(CADateTime xCADateTime, CADateTime yCADateTime)  
        {  
            if (xCADateTime.IsNull || yCADateTime.IsNull)  
            {  
                return SqlBoolean.Null;  
            }  
  
            return xCADateTime.DateTime == yCADateTime.DateTime;  
        }  
  
        public static SqlBoolean operator !=(CADateTime xCADateTime, CADateTime yCADateTime)  
        {  
            if (xCADateTime.IsNull || yCADateTime.IsNull)  
            {  
                return SqlBoolean.Null;  
            }  
  
            return xCADateTime.DateTime != yCADateTime.DateTime;  
        }  
  
        /// <summary>  
        /// convert the datetime to string  
        /// </summary>  
        /// <returns></returns>  
        public override string ToString()  
        {  
            if (this.IsNull)  
            {  
                return null;  
            }  
  
            bool afternoon = this.Hour >= 12;  
            int twelveHour = this.Hour;  
            if (twelveHour == 0)  
            {  
                twelveHour = 12;  
            }  
            else if (twelveHour > 12)  
            {  
                twelveHour = twelveHour - 12;  
            }  
  
            return string.Format(  
                CultureInfo.CurrentCulture,  
                DateTimeFormatString(),  
                this.DayOfMonth,  
                this.Month,  
                this.Year,  
                twelveHour,  
                this.Hour,  
                this.Minute,  
                this.Second,  
                afternoon  
                    ? CultureInfo.CurrentCulture.DateTimeFormat.PMDesignator  
                    : CultureInfo.CurrentCulture.DateTimeFormat.AMDesignator);  
        }  
  
        /// <summary>  
        /// convert the datetime to string, using the specified format  
        /// </summary>  
        /// <param name="format">Format string</param>  
        /// <returns></returns>  
        public string ToGregorianStringUsingFormat(string format)  
        {  
            if (this.IsNull)  
            {  
                return null;  
            }  
  
            return this.DateTime.ToString(format, DateTimeFormatInfo.CurrentInfo);  
        }  
  
        /// <summary>  
        /// Return a string representation of this DateTime, in the Gregorian calendarId  
        /// </summary>  
        /// <returns></returns>  
        public string ToGregorianString()  
        {  
            if (this.IsNull)  
            {  
                return null;  
            }  
  
            return this.DateTime.ToString(DateTimeFormatInfo.CurrentInfo);  
        }  
  
        public bool IsValid()  
        {  
            return this.dtTicks >= 0;  
        }  
  
        /// <summary>  
        /// convert to sql datetime  
        /// </summary>  
        /// <returns></returns>  
        public SqlDateTime ToSqlDateTime()  
        {  
            return new SqlDateTime(this.DateTime);  
        }  
  
        public CADateTime AddYears(int years)  
        {  
            return new CADateTime(this.Calendar.AddYears(this.DateTime, years));  
        }  
  
        public CADateTime AddDays(int days)  
        {  
            return new CADateTime(this.Calendar.AddDays(this.DateTime, days));  
        }  
  
        public CADateTime AddMonths(int months)  
        {  
            return new CADateTime(this.Calendar.AddMonths(this.DateTime, months));  
        }  
  
        public CADateTime AddHours(int hours)  
        {  
            return new CADateTime(this.Calendar.AddHours(this.DateTime, hours));  
        }  
  
        public CADateTime AddMinutes(int minutes)  
        {  
            return new CADateTime(this.Calendar.AddMinutes(this.DateTime, minutes));  
        }  
  
        public CADateTime AddSeconds(int seconds)  
        {  
            return new CADateTime(this.Calendar.AddSeconds(this.DateTime, seconds));  
        }  
  
        public CADateTime AddMilliseconds(double millis)  
        {  
            return new CADateTime(this.Calendar.AddMilliseconds(this.DateTime, millis));  
        }  
  
        public double DiffDays(CADateTime other)  
        {  
            return this.DateTime.Subtract(other.DateTime).TotalDays;  
        }  
  
        public double DiffHours(CADateTime other)  
        {  
            return this.DateTime.Subtract(other.DateTime).TotalHours;  
        }  
  
        public double DiffMinutes(CADateTime other)  
        {  
            return this.DateTime.Subtract(other.DateTime).TotalMinutes;  
        }  
  
        public double DiffSeconds(CADateTime other)  
        {  
            return this.DateTime.Subtract(other.DateTime).TotalSeconds;  
        }  
  
        public double DiffMilliseconds(CADateTime other)  
        {  
            return this.DateTime.Subtract(other.DateTime).TotalMilliseconds;  
        }  
  
        // Hash and comparison operators  
  
        public override int GetHashCode()  
        {  
            return this.DateTime.GetHashCode();  
        }  
  
        public override bool Equals(object obj)  
        {  
            if (!(obj is DateTime))  
            {  
                return false;  
            }  
  
            DateTime dt = (DateTime)obj;  
            return this.DateTime.Equals(dt);  
        }  
  
        public XmlSchema GetSchema()  
        {  
            StringReader sr = new StringReader(CADateTimeSchema);  
            XmlSchema schema = XmlSchema.Read(  
                sr,  
                new ValidationEventHandler(this.ValidationHandler));  
            sr.Dispose();  
  
            return schema;  
        }  
  
        public void ReadXml(XmlReader reader)  
        {  
            if (reader == null)  
            {  
                throw new ArgumentNullException("reader");  
            }  
  
            reader.MoveToContent();  
            if (reader.GetAttribute("IsNull").Equals("true"))  
            {  
                this.dtTicks = CADateTime.NullTicks;  
            }  
            else  
            {  
                string calendarName = reader.GetAttribute("Calendar");  
                Calendar requestedCalendar  
                    = CalendarInfo.Calendars[CalendarInfo.GetCalendarId(calendarName)];  
  
                this.dtTicks = (uint)new DateTime(  
                    int.Parse(reader.GetAttribute("Year"), CultureInfo.CurrentCulture),  
                    int.Parse(reader.GetAttribute("Month"), CultureInfo.CurrentCulture),  
                    int.Parse(reader.GetAttribute("Day"), CultureInfo.CurrentCulture),  
                    int.Parse(reader.GetAttribute("Hour"), CultureInfo.CurrentCulture),  
                    int.Parse(reader.GetAttribute("Minute"), CultureInfo.CurrentCulture),  
                    int.Parse(reader.GetAttribute("Second"), CultureInfo.CurrentCulture),  
                    requestedCalendar).Ticks;  
            }  
        }  
  
        public void WriteXml(XmlWriter writer)  
        {  
            if (writer == null)  
            {  
                throw new ArgumentNullException("writer");  
            }  
  
            writer.WriteStartElement("CADate", "https://schemas.microsoft.com/sqlserver/2004/08/CADate");  
            writer.WriteAttributeString("IsNull", this.IsNull.ToString());  
  
            if (!this.IsNull)  
            {  
                writer.WriteAttributeString("Year", this.Year.ToString(CultureInfo.CurrentUICulture));  
                writer.WriteAttributeString("Month", this.Month.ToString(CultureInfo.CurrentUICulture));  
                writer.WriteAttributeString("Day", this.Day.ToString(CultureInfo.CurrentUICulture));  
                writer.WriteAttributeString("Calendar", Calendar.GetType().ToString());  
            }  
  
            writer.WriteEndElement();  
        }  
  
        // Returns a string suitable for use with string.Format which displays  
        // day, month, and year components in a culture appropriate way.  
        private static string DateTimeFormatString()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.Append(CultureInfo.CurrentCulture.DateTimeFormat.ShortDatePattern);  
            sb.Append(" ");  
            sb.Append(CultureInfo.CurrentCulture.DateTimeFormat.LongTimePattern);  
            string cultureDatePattern = sb.ToString();  
  
            return CalendarInfo.SubstitutePositionForCharacters(datetimeChars, cultureDatePattern);  
        }  
  
        private void ValidationHandler(object sender, ValidationEventArgs args)  
        {  
            throw new ApplicationException(args.Message);  
        }  
    }  
  
```  
  
 Di seguito è illustrato il file `calendars.txt` necessario per la definizione dei calendari.  
  
```  
; the list of calendars  
; the key is the calendar ID, the value is the assembly-qualified name of the type  
NumCalendars = 9  
  
; Note, new calendars _MUST_ be added to the end of this list  
0 = System.Globalization.GregorianCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
  
; Saudi Hijri, the business calendar for use in Saudi Arabia  
1 = System.Globalization.UmAlQuraCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
  
; HijriCalendar   
2 = System.Globalization.HijriCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
  
; other calendars  
3 = System.Globalization.JapaneseCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
4 = System.Globalization.JulianCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
5 = System.Globalization.KoreanCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
6 = System.Globalization.TaiwanCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
7 = System.Globalization.ThaiBuddhistCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
8 = System.Globalization.ChineseLunisolarCalendar, mscorlib, Version=2.0.3600.0, Culte=neutral, PublicKeyToken=b77a5c561934e089  
  
; the default calendar for this culture  
DefaultCalendarID = 0  
  
```  
  
 Di seguito è illustrato lo script di installazione [!INCLUDE[tsql](../../includes/tsql-md.md)] (`Install.sql`) che consente la distribuzione degli assembly e la creazione delle funzioni di conversione nel database, nonché la preparazione di una tabella di dati di esempio.  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[ufn_CADateFromSqlDateTimeAndCalendar]') AND type in (N'FN', N'IF', N'TF', N'FS', N'FT'))  
DROP FUNCTION [dbo].[ufn_CADateFromSqlDateTimeAndCalendar];  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[ufn_CADateTimeFromSqlDateTimeAndCalendar]') AND type in (N'FN', N'IF', N'TF', N'FS', N'FT'))  
DROP FUNCTION [dbo].[ufn_CADateTimeFromSqlDateTimeAndCalendar];  
GO  
  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = OBJECT_ID(N'[Sales].[SalesSummary]') AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
DROP TABLE [Sales].[SalesSummary];  
GO  
  
IF EXISTS (SELECT * FROM sys.types WHERE [name] = N'CADateTime')   
DROP TYPE CADateTime;  
GO  
  
IF EXISTS (SELECT * FROM sys.types WHERE [name] = N'CADate')   
DROP TYPE CADate;  
GO  
  
-- If the assembly we want to add already exists, drop it.  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime')  
DROP ASSEMBLY CADateTime;  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.neutral')  
DROP ASSEMBLY [CADateTime.resources.neutral];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.ar-SA')  
DROP ASSEMBLY [CADateTime.resources.ar-SA];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.ja')  
DROP ASSEMBLY [CADateTime.resources.ja];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.zh-CN')  
DROP ASSEMBLY [CADateTime.resources.zh-CN];  
GO  
  
-- Add the assembly which contains the CLR methods we want to invoke on the server.  
DECLARE @SamplesPath nvarchar(1024);  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
Set @SamplesPath= N'C:\MySample\'  
  
CREATE ASSEMBLY CADateTime  
FROM @SamplesPath + 'CADateTime.dll'  
WITH permission_set = safe;  
  
CREATE ASSEMBLY [CADateTime.resources.neutral]    
FROM @SamplesPath + 'CADateTime.resources.dll'  
WITH permission_set = safe;  
  
CREATE ASSEMBLY [CADateTime.resources.ar-SA]    
FROM @SamplesPath + 'CADateTime.resources.ar-SA.dll'  
WITH permission_set = safe;  
  
CREATE ASSEMBLY [CADateTime.resources.ja]    
FROM @SamplesPath + 'CADateTime.resources.ja.dll'  
WITH permission_set = safe;  
  
CREATE ASSEMBLY [CADateTime.resources.zh-CN]    
FROM @SamplesPath + 'CADateTime.resources.zh-CN.dll'  
WITH permission_set = safe;  
GO  
  
CREATE TYPE CADateTime EXTERNAL NAME CADateTime.[CADateTime];  
GO  
  
CREATE TYPE CADate EXTERNAL NAME CADateTime.[CADate];  
GO  
  
CREATE FUNCTION [dbo].[ufn_CADateFromSqlDateTimeAndCalendar]  
(  
    @D datetime,  
    @CalendarName nvarchar(128)  
)   
RETURNS CADate   
AS EXTERNAL NAME CADateTime.[CADate].FromSqlDateTimeAndCalendar;  
GO  
  
CREATE FUNCTION [dbo].[ufn_CADateTimeFromSqlDateTimeAndCalendar]  
(  
    @D datetime,  
    @CalendarName nvarchar(128)  
)   
RETURNS CADateTime  
AS EXTERNAL NAME CADateTime.[CADateTime].FromSqlDateTimeAndCalendar;  
GO  
  
SELECT SalesOrderID, [dbo].[ufn_CADateTimeFromSqlDateTimeAndCalendar](OrderDate, 'GregorianCalendar') AS OrderDate, TotalDue   
INTO [Sales].[SalesSummary]  
FROM [Sales].[SalesOrderHeader];  
GO  
  
ALTER TABLE [Sales].[SalesSummary] WITH CHECK ADD   
    CONSTRAINT [PK_SalesSummary_SalesOrderID] PRIMARY KEY CLUSTERED   
    (  
        [SalesOrderID]  
    );  
GO  
  
ALTER TABLE [Sales].[SalesSummary] ADD DayOfYear AS [OrderDate].[Day] PERSISTED;  
GO  
  
CREATE INDEX IX_Sales_SalesSummary ON [Sales].[SalesSummary] (DayOfYear);  
GO  
```  
  
 Di seguito è illustrato lo script `test.sql` che consente di testare l'esempio eseguendo le funzioni in calendari diversi.  
  
```  
USE AdventureWorks  
GO  
  
SELECT CADateTime::CurrentCalendarName;  
  
-- Simple usage, create a new value from a string and print it out  
-- We're using ISO 8601 format dates as input, which are YYYY-MM-DD  
DECLARE @h CADateTime;  
SET @h = '1976-01-02';  
SELECT CAST(@h as nvarchar(128)), @h.CalendarName;  
GO  
  
-- print it out in "full format"  
DECLARE @h CADateTime;  
SET @h = '1976-01-02';  
SELECT @h.ToGregorianStringUsingFormat('F');  
GO  
  
-- print it out in a custom format  
DECLARE @h CADateTime;  
SET @h = '1976-01-02';  
SELECT @h.ToGregorianStringUsingFormat('MMM dd yyyy');  
GO  
  
-- convert it to arabic (for testing purposes)  
DECLARE @h CADateTime;  
SET @h = CADateTime::Parse('1976-01-02');  
SELECT @h.ToString(), @h.ToGregorianStringUsingFormat('F');  
GO  
  
-- convert sql datetime to CAD and back  
DECLARE @h CADateTime;  
SET @h = CADateTime::FromSqlDateTime(GetDate());  
SELECT @h.ToString(), @h.ToSqlDateTime();  
GO  
  
-- get the current CAD, in two ways  
SELECT   CADateTime::Now.ToString(),   
    CADateTime::FromSqlDateTime(GetDate()).ToString();  
GO  
  
-- do some arithmetic  
DECLARE @h CADateTime, @d datetime;  
SET @h = CADateTime::Now; -- get the current hijri datetime  
SET @h = @h.AddDays(10); -- add ten days to it  
SET @d = GetDate(); -- current sql date  
SET @d = DateAdd(day, 10, @d); -- add ten days to the sql datetime  
-- print 'em both, should be the same  
SELECT @h.ToSqlDateTime(), @d;  
GO  
  
-- what about datepart  
DECLARE @h CADateTime;  
SET @h = CADateTime::Now; -- get the current datetime  
SELECT @h.Year as year, @h.Month as month, @h.Day as dayofyear, @h.DayOfMonth as dom;  
GO  
  
-- print the same date in four different calendars  
SELECT   
    CADateTime::FromSqlDateTimeAndCalendar(GetDate(), 'UmAlQuraCalendar').ToString() as Umq,  
    CADateTime::FromSqlDateTimeAndCalendar(GetDate(), 'GregorianCalendar').ToString() as Gregorian,  
    CADateTime::FromSqlDateTimeAndCalendar(GetDate(), 'JapaneseCalendar').ToString() as Japanese,  
    CADateTime::FromSqlDateTimeAndCalendar(GetDate(), 'ChineseLunisolarCalendar').ToString() as ChineseLunisolar;  
GO  
  
SELECT CADate::CurrentCalendarName;  
  
-- simple usage, create a new value from a string and print it out  
DECLARE @h CADate;  
SET @h = '1976-01-02';  
SELECT CAST(@h as nvarchar(128)), @h.CalendarName;  
GO  
  
-- print it out in "date format"  
DECLARE @h CADate;  
SET @h = '1976-01-02';  
SELECT @h.ToGregorianStringUsingFormat('d');  
GO  
  
-- print it out in a custom format  
DECLARE @h CADate;  
SET @h = '1976-01-02';  
SELECT @h.ToGregorianStringUsingFormat('MMM dd yyyy');  
GO  
  
-- convert it to arabic (for testing purposes)  
DECLARE @h CADate;  
SET @h = CADate::Parse('1976-01-02');  
SELECT @h.ToString(), @h.ToGregorianStringUsingFormat('d');  
GO  
  
-- convert sql datetime to CAD and back  
DECLARE @h CADate;  
SET @h = CADate::FromSqlDateTime(GetDate());  
SELECT @h.ToString(), @h.ToSqlDateTime();  
GO  
  
-- get the current CAD, in two ways  
SELECT   CADate::Now.ToString(),   
    CADate::FromSqlDateTime(GetDate()).ToString();  
GO  
  
-- do some arithmetic  
DECLARE @h CADate, @d datetime;  
SET @h = CADate::Now; -- get the current hijri datetime  
SET @h = @h.AddDays(10); -- add ten days to it  
SET @d = GetDate(); -- current sql date  
SET @d = DateAdd(day, 10, @d); -- add ten days to the sql datetime  
-- print 'em both, should be the same  
SELECT @h.ToSqlDateTime(), @d;  
GO  
  
-- what about datepart  
DECLARE @h CADate;  
SET @h = CADate::Now; -- get the current datetime  
SELECT @h.Year as year, @h.Month as month, @h.Day as dayofyear, @h.DayOfMonth as dom;  
GO  
  
-- print the same date in four different calendars  
SELECT   
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'UmAlQuraCalendar').ToString() as Umq,  
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'GregorianCalendar').ToString() as Gregorian,  
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'JapaneseCalendar').ToString() as Japanese,  
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'ChineseLunisolarCalendar').ToString() as ChineseLunisolar;  
GO  
  
-- Show the total sales figures for particular days of the year over a 90 day   
-- range starting with day 90.  
SELECT DayOfYear, SUM(TotalDue)  
FROM [Sales].[SalesSummary]  
WHERE DayOfYear >= 90 AND DayOfYear < 180  
GROUP BY DayOfYear  
ORDER BY DayOfYear;  
GO  
  
-- Show the first day of the year where there is sales between day 90 and day 180.  
SELECT TOP 1 DayOfYear   
FROM [Sales].[SalesSummary]  
WHERE DayOfYear >= 90 AND DayOfYear < 180   
ORDER BY DayOfYear ASC  
GO  
  
SET LANGUAGE French  
GO  
  
-- print the same date in four different calendars using the French culture  
SELECT   
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'UmAlQuraCalendar').ToString() as Umq,  
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'GregorianCalendar').ToString() as Gregorian,  
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'JapaneseCalendar').ToString() as Japanese,  
    CADate::FromSqlDateTimeAndCalendar(GetDate(), 'ChineseLunisolarCalendar').ToString() as ChineseLunisolar;  
GO  
  
SET LANGUAGE us_english  
GO  
```  
  
 Il codice [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente consente di rimuovere gli assembly, le funzioni e la tabella dal database.  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[ufn_CADateFromSqlDateTimeAndCalendar]') AND type in (N'FN', N'IF', N'TF', N'FS', N'FT'))  
DROP FUNCTION [dbo].[ufn_CADateFromSqlDateTimeAndCalendar];  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[ufn_CADateTimeFromSqlDateTimeAndCalendar]') AND type in (N'FN', N'IF', N'TF', N'FS', N'FT'))  
DROP FUNCTION [dbo].[ufn_CADateTimeFromSqlDateTimeAndCalendar];  
GO  
  
IF EXISTS (SELECT * FROM dbo.sysobjects WHERE id = OBJECT_ID(N'[Sales].[SalesSummary]') AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
DROP TABLE [Sales].[SalesSummary];  
GO  
  
IF EXISTS (SELECT * FROM sys.types WHERE [name] = N'CADateTime')   
DROP TYPE CADateTime;  
GO  
  
IF EXISTS (SELECT * FROM sys.types WHERE [name] = N'CADate')   
DROP TYPE CADate;  
GO  
  
-- If the assembly we want to add already exists, drop it.  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime')  
DROP ASSEMBLY CADateTime;  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.neutral')  
DROP ASSEMBLY [CADateTime.resources.neutral];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.ar-SA')  
DROP ASSEMBLY [CADateTime.resources.ar-SA];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.ja')  
DROP ASSEMBLY [CADateTime.resources.ja];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies WHERE [name] = N'CADateTime.resources.zh-CN')  
DROP ASSEMBLY [CADateTime.resources.zh-CN];  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Scenari di utilizzo ed esempi per l'integrazione con CLR &#40;Common Language Runtime&#41;](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
