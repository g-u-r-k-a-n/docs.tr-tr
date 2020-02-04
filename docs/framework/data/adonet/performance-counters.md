---
title: Performans Sayaçları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: 985951180a5c8ee09460b7fe4bf3213b986c3bb6
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980073"
---
# <a name="performance-counters-in-adonet"></a>ADO.NET 'de performans sayaçları
ADO.NET 2,0, hem <xref:System.Data.SqlClient> hem de <xref:System.Data.OracleClient>için destek içeren performans sayaçları için genişletilmiş destek getirmiştir. Önceki ADO.NET sürümlerinde bulunan <xref:System.Data.SqlClient> performans sayaçları kullanımdan kaldırılmıştır ve bu konuda açıklanan yeni performans sayaçlarıyla değiştirilmiştir. Uygulamanızın durumunu ve kullandığı bağlantı kaynaklarını izlemek için ADO.NET performans sayaçlarını kullanabilirsiniz. Performans sayaçları, Windows performans Izleyicisi kullanılarak izlenebilir veya <xref:System.Diagnostics> ad alanındaki <xref:System.Diagnostics.PerformanceCounter> sınıfı kullanılarak programlı bir şekilde erişilebilir.  
  
## <a name="available-performance-counters"></a>Kullanılabilir performans sayaçları  
 Şu anda <xref:System.Data.SqlClient> ve <xref:System.Data.OracleClient> için aşağıdaki tabloda açıklandığı gibi 14 farklı performans sayacı mevcuttur. Bireysel sayaçların adlarının Microsoft .NET çerçevesinin bölgesel sürümlerinde yerelleştirilmemiş olduğunu unutmayın.  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|Bir veritabanı sunucusuna yapılan saniye başına bağlantı sayısı.|  
|`HardDisconnectsPerSecond`|Bir veritabanı sunucusuna yapılan saniye başına bağlantı kesilen bağlantı sayısı.|  
|`NumberOfActiveConnectionPoolGroups`|Etkin olan benzersiz bağlantı havuzu grupları sayısı. Bu sayaç, AppDomain 'de bulunan benzersiz bağlantı dizeleri sayısına göre denetlenir.|  
|`NumberOfActiveConnectionPools`|Bağlantı havuzlarının toplam sayısı.|  
|`NumberOfActiveConnections`|Şu anda kullanımda olan etkin bağlantı sayısı. **Note:**  Bu performans sayacı varsayılan olarak etkinleştirilmemiştir. Bu performans sayacını etkinleştirmek için bkz. [Varsayılan olarak devre dışı sayaçları etkinleştirme](#ActivatingOffByDefault).|  
|`NumberOfFreeConnections`|Bağlantı havuzlarında kullanılabilecek bağlantı sayısı. **Note:**  Bu performans sayacı varsayılan olarak etkinleştirilmemiştir. Bu performans sayacını etkinleştirmek için bkz. [Varsayılan olarak devre dışı sayaçları etkinleştirme](#ActivatingOffByDefault).|  
|`NumberOfInactiveConnectionPoolGroups`|Ayıklama için işaretlenen benzersiz bağlantı havuzu grupları sayısı. Bu sayaç, AppDomain 'de bulunan benzersiz bağlantı dizeleri sayısına göre denetlenir.|  
|`NumberOfInactiveConnectionPools`|En son etkinliği olmayan ve aktiften çıkarılmayı bekleyen etkin olmayan bağlantı havuzu sayısı.|  
|`NumberOfNonPooledConnections`|Havuza alınmamış etkin bağlantı sayısı.|  
|`NumberOfPooledConnections`|Bağlantı havuzu altyapısı tarafından yönetilmekte olan etkin bağlantı sayısı.|  
|`NumberOfReclaimedConnections`|`Close` veya `Dispose` uygulama tarafından çağrılmayan çöp toplama aracılığıyla geri kazanılan bağlantı sayısı. Bağlantı kesilmesi performansını açıkça kapatma veya atma.|  
|`NumberOfStasisConnections`|Şu anda bir eylemin tamamlanmasını bekleyen ve bu nedenle uygulamanız tarafından kullanılamayan bağlantı sayısı.|  
|`SoftConnectsPerSecond`|Bağlantı havuzundan çekilen etkin bağlantı sayısı. **Note:**  Bu performans sayacı varsayılan olarak etkinleştirilmemiştir. Bu performans sayacını etkinleştirmek için bkz. [Varsayılan olarak devre dışı sayaçları etkinleştirme](#ActivatingOffByDefault).|  
|`SoftDisconnectsPerSecond`|Bağlantı havuzuna döndürülen etkin bağlantı sayısı. **Note:**  Bu performans sayacı varsayılan olarak etkinleştirilmemiştir. Bu performans sayacını etkinleştirmek için bkz. [Varsayılan olarak devre dışı sayaçları etkinleştirme](#ActivatingOffByDefault).|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>Bağlantı havuzu grupları ve bağlantı havuzları  
 Windows kimlik doğrulaması (tümleşik güvenlik) kullanırken hem `NumberOfActiveConnectionPoolGroups` hem de `NumberOfActiveConnectionPools` performans sayaçlarını izlemeniz gerekir. Bunun nedeni, bağlantı havuzu gruplarının benzersiz bağlantı dizeleriyle eşlenme nedenidir. Tümleşik güvenlik kullanıldığında, bağlantı havuzları bağlantı dizelerine eşlenir ve ayrıca ayrı Windows kimlikleri için ayrı havuzlar oluşturur. Örneğin, Fred ve Julie, her ikisi de aynı AppDomain içinde `"Data Source=MySqlServer;Integrated Security=true"`, bağlantı dizesi için bir bağlantı havuzu grubu oluşturulur ve biri Fred ve Julie için olmak üzere iki ek havuz oluşturulur. John ve Martha aynı SQL Server oturum açma `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`sahip bir bağlantı dizesi kullanıyorsa, **Lowprıkullanıcı** kimliği için yalnızca tek bir havuz oluşturulur.  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a>Varsayılan olarak devre dışı sayaçları etkinleştirme  
 `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`ve `SoftConnectsPerSecond` performans sayaçları varsayılan olarak kapalıdır. Aşağıdaki bilgileri etkinleştirmek için uygulamanın yapılandırma dosyasına ekleyin:  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a>Performans sayacı değerlerini alma  
 Aşağıdaki konsol uygulaması, uygulamanızda performans sayacı değerlerinin nasıl alınacağını gösterir. Tüm ADO.NET performans sayaçlarıyla ilgili bilgilerin döndürülmesi için bağlantıların açık ve etkin olması gerekir.  
  
> [!NOTE]
> Bu örnek, SQL Server eklenen örnek **AdventureWorks** veritabanını kullanır. Örnek kodda sağlanan bağlantı dizeleri, veritabanının bir örnek adı SqlExpress olan yerel bilgisayarda yüklü ve kullanılabilir olduğunu ve bağlantı dizelerinde sağlananlarla eşleşen SQL Server oturum açma işlemleri oluşturduğunuzu varsayar. Sunucunuz yalnızca Windows kimlik doğrulamasına izin veren varsayılan güvenlik ayarları kullanılarak yapılandırılmışsa SQL Server oturum açma işlemlerini etkinleştirmeniz gerekebilir. Bağlantı dizelerini ortamınıza uyacak şekilde değiştirin.  
  
### <a name="example"></a>Örnek  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System.Data.SqlClient  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Class Program  
  
    Private PerfCounters(9) As PerformanceCounter  
    Private connection As SqlConnection = New SqlConnection  
  
    Public Shared Sub Main()  
        Dim prog As Program = New Program  
        ' Open a connection and create the performance counters.   
        prog.connection.ConnectionString = _  
           GetIntegratedSecurityConnectionString()  
        prog.SetUpPerformanceCounters()  
        Console.WriteLine("Available Performance Counters:")  
  
        ' Create the connections and display the results.  
        prog.CreateConnections()  
        Console.WriteLine("Press Enter to finish.")  
        Console.ReadLine()  
    End Sub  
  
    Private Sub CreateConnections()  
        ' List the Performance counters.  
        WritePerformanceCounters()  
  
        ' Create 4 connections and display counter information.  
        Dim connection1 As SqlConnection = New SqlConnection( _  
           GetIntegratedSecurityConnectionString)  
        connection1.Open()  
        Console.WriteLine("Opened the 1st Connection:")  
        WritePerformanceCounters()  
  
        Dim connection2 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionStringDifferent)  
        connection2.Open()  
        Console.WriteLine("Opened the 2nd Connection:")  
        WritePerformanceCounters()  
  
        Console.WriteLine("Opened the 3rd Connection:")  
        Dim connection3 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection3.Open()  
        WritePerformanceCounters()  
  
        Dim connection4 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection4.Open()  
        Console.WriteLine("Opened the 4th Connection:")  
        WritePerformanceCounters()  
  
        connection1.Close()  
        Console.WriteLine("Closed the 1st Connection:")  
        WritePerformanceCounters()  
  
        connection2.Close()  
        Console.WriteLine("Closed the 2nd Connection:")  
        WritePerformanceCounters()  
  
        connection3.Close()  
        Console.WriteLine("Closed the 3rd Connection:")  
        WritePerformanceCounters()  
  
        connection4.Close()  
        Console.WriteLine("Closed the 4th Connection:")  
        WritePerformanceCounters()  
    End Sub  
  
    Private Enum ADO_Net_Performance_Counters  
        NumberOfActiveConnectionPools  
        NumberOfReclaimedConnections  
        HardConnectsPerSecond  
        HardDisconnectsPerSecond  
        NumberOfActiveConnectionPoolGroups  
        NumberOfInactiveConnectionPoolGroups  
        NumberOfInactiveConnectionPools  
        NumberOfNonPooledConnections  
        NumberOfPooledConnections  
        NumberOfStasisConnections  
        ' The following performance counters are more expensive to track.  
        ' Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        '     SoftConnectsPerSecond  
        '     SoftDisconnectsPerSecond  
        '     NumberOfActiveConnections  
        '     NumberOfFreeConnections  
    End Enum  
  
    Private Sub SetUpPerformanceCounters()  
        connection.Close()  
        Me.PerfCounters(9) = New PerformanceCounter()  
  
        Dim instanceName As String = GetInstanceName()  
        Dim apc As Type = GetType(ADO_Net_Performance_Counters)  
        Dim i As Integer = 0  
        Dim s As String = ""  
        For Each s In [Enum].GetNames(apc)  
            Me.PerfCounters(i) = New PerformanceCounter()  
            Me.PerfCounters(i).CategoryName = ".NET Data Provider for SqlServer"  
            Me.PerfCounters(i).CounterName = s  
            Me.PerfCounters(i).InstanceName = instanceName  
            i = (i + 1)  
        Next  
    End Sub  
  
    Private Declare Function GetCurrentProcessId Lib "kernel32.dll" () As Integer  
  
    Private Function GetInstanceName() As String  
        'This works for Winforms apps.   
        Dim instanceName As String = _  
           System.Reflection.Assembly.GetEntryAssembly.GetName.Name  
  
        ' Must replace special characters like (, ), #, /, \\   
        Dim instanceName2 As String = _  
           AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
           .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        'For ASP.NET applications your instanceName will be your CurrentDomain's   
        'FriendlyName. Replace the line above that sets the instanceName with this:   
        'instanceName = AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
        '    .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        Dim pid As String = GetCurrentProcessId.ToString  
        instanceName = (instanceName + ("[" & (pid & "]")))  
        Console.WriteLine("Instance Name: {0}", instanceName)  
        Console.WriteLine("---------------------------")  
        Return instanceName  
    End Function  
  
    Private Sub WritePerformanceCounters()  
        Console.WriteLine("---------------------------")  
        For Each p As PerformanceCounter In Me.PerfCounters  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue)  
        Next  
        Console.WriteLine("---------------------------")  
    End Sub  
  
    Private Shared Function GetIntegratedSecurityConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrieve it from a configuration file.   
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrieve it from a configuration file.   
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrieve it from a configuration file.   
        Return ("Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" & _  
          "User Id=LowPriv;Password=Data!05;")  
    End Function  
End Class  
```  

```csharp  
using System;  
using System.Data.SqlClient;  
using System.Diagnostics;  
using System.Runtime.InteropServices;  
  
class Program  
{  
    PerformanceCounter[] PerfCounters = new PerformanceCounter[10];  
    SqlConnection connection = new SqlConnection();  
  
    static void Main()  
    {  
        Program prog = new Program();  
        // Open a connection and create the performance counters.  
        prog.connection.ConnectionString =  
           GetIntegratedSecurityConnectionString();  
        prog.SetUpPerformanceCounters();  
        Console.WriteLine("Available Performance Counters:");  
  
        // Create the connections and display the results.  
        prog.CreateConnections();  
        Console.WriteLine("Press Enter to finish.");  
        Console.ReadLine();  
    }  
  
    private void CreateConnections()  
    {  
        // List the Performance counters.  
        WritePerformanceCounters();  
  
        // Create 4 connections and display counter information.  
        SqlConnection connection1 = new SqlConnection(  
              GetIntegratedSecurityConnectionString());  
        connection1.Open();  
        Console.WriteLine("Opened the 1st Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection2 = new SqlConnection(  
              GetSqlConnectionStringDifferent());  
        connection2.Open();  
        Console.WriteLine("Opened the 2nd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection3 = new SqlConnection(  
              GetSqlConnectionString());  
        connection3.Open();  
        Console.WriteLine("Opened the 3rd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection4 = new SqlConnection(  
              GetSqlConnectionString());  
        connection4.Open();  
        Console.WriteLine("Opened the 4th Connection:");  
        WritePerformanceCounters();  
  
        connection1.Close();  
        Console.WriteLine("Closed the 1st Connection:");  
        WritePerformanceCounters();  
  
        connection2.Close();  
        Console.WriteLine("Closed the 2nd Connection:");  
        WritePerformanceCounters();  
  
        connection3.Close();  
        Console.WriteLine("Closed the 3rd Connection:");  
        WritePerformanceCounters();  
  
        connection4.Close();  
        Console.WriteLine("Closed the 4th Connection:");  
        WritePerformanceCounters();  
    }  
  
    private enum ADO_Net_Performance_Counters  
    {  
        NumberOfActiveConnectionPools,  
        NumberOfReclaimedConnections,  
        HardConnectsPerSecond,  
        HardDisconnectsPerSecond,  
        NumberOfActiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPools,  
        NumberOfNonPooledConnections,  
        NumberOfPooledConnections,  
        NumberOfStasisConnections  
        // The following performance counters are more expensive to track.  
        // Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        //     SoftConnectsPerSecond  
        //     SoftDisconnectsPerSecond  
        //     NumberOfActiveConnections  
        //     NumberOfFreeConnections  
    }  
  
    private void SetUpPerformanceCounters()  
    {  
        connection.Close();  
        this.PerfCounters = new PerformanceCounter[10];  
        string instanceName = GetInstanceName();  
        Type apc = typeof(ADO_Net_Performance_Counters);  
        int i = 0;  
        foreach (string s in Enum.GetNames(apc))  
        {  
            this.PerfCounters[i] = new PerformanceCounter();  
            this.PerfCounters[i].CategoryName = ".NET Data Provider for SqlServer";  
            this.PerfCounters[i].CounterName = s;  
            this.PerfCounters[i].InstanceName = instanceName;  
            i++;  
        }  
    }  
  
    [DllImport("kernel32.dll", SetLastError = true)]  
    static extern int GetCurrentProcessId();  
  
    private string GetInstanceName()  
    {  
        //This works for Winforms apps.  
        string instanceName =  
            System.Reflection.Assembly.GetEntryAssembly().GetName().Name;  
  
        // Must replace special characters like (, ), #, /, \\  
        string instanceName2 =  
            AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(', '[')  
            .Replace(')', ']').Replace('#', '_').Replace('/', '_').Replace('\\', '_');  
  
        // For ASP.NET applications your instanceName will be your CurrentDomain's   
        // FriendlyName. Replace the line above that sets the instanceName with this:  
        // instanceName = AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(','[')  
        // .Replace(')',']').Replace('#','_').Replace('/','_').Replace('\\','_');  
  
        string pid = GetCurrentProcessId().ToString();  
        instanceName = instanceName + "[" + pid + "]";  
        Console.WriteLine("Instance Name: {0}", instanceName);  
        Console.WriteLine("---------------------------");  
        return instanceName;  
    }  
  
    private void WritePerformanceCounters()  
    {  
        Console.WriteLine("---------------------------");  
        foreach (PerformanceCounter p in this.PerfCounters)  
        {  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue());  
        }  
        Console.WriteLine("---------------------------");  
    }  
  
    private static string GetIntegratedSecurityConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
          "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Kaynağına Bağlanma](connecting-to-a-data-source.md)
- [OLE DB, ODBC ve Oracle Bağlantı Havuzu](ole-db-odbc-and-oracle-connection-pooling.md)
- [ASP.NET için performans sayaçları](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))
- [Çalışma Zamanı Profili Oluşturma](../../debug-trace-profile/runtime-profiling.md)
- [Performans eşiklerini Izlemeye giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
