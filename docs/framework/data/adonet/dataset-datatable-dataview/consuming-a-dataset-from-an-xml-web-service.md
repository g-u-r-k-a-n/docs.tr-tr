---
title: XML Web hizmetinden veri kümesi kullanma
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: e6dc32274cc3b0d7ec9d66a837a422c87fb2468b
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416218"
---
# <a name="consume-a-dataset-from-an-xml-web-service"></a>XML Web hizmetinden veri kümesi kullanma

, <xref:System.Data.DataSet> Internet üzerinden veri aktarımını kolaylaştırmak için kısmen bağlantısız bir tasarıma göre tasarlanmıştır. Veri kümesi, **veri kümesinin** IÇERIĞINI bir XML Web hizmetinden bir istemciye ve geriye doğru akışa almak için gereken ek bir kodlama olmadan XML Web hizmetlerinden bir giriş veya çıkış olarak belirtime için "serileştirilebilir **" olur.** **Veri kümesi** örtük olarak, DiffGram biçimi KULLANıLARAK bir XML akışına dönüştürülür, ağ üzerinden gönderilir ve ardından XML akışından alma ucunda bir **veri kümesi** olarak yeniden oluşturulur. Bu, XML Web hizmetlerini kullanarak ilişkisel verileri iletmek ve döndürmek için basit ve esnek bir yöntem sunar. DiffGram biçimi hakkında daha fazla bilgi için bkz. [DiffGram](diffgrams.md).  
  
 Aşağıdaki örnek, ilişkisel verileri (değiştirilen veriler dahil) taşımak için **veri kümesini** kullanan bir XML Web hizmeti ve istemcisinin nasıl oluşturulacağını gösterir ve tüm güncelleştirmeleri özgün veri kaynağına geri çözümler.  
  
> [!NOTE]
> `DataSet` `DataTable` Girişin güvenilir OLMAMASı durumunda XML Web hizmeti çağrılarının bir parçası olarak iletilmesi veya örnekleri güvenli değildir. Daha fazla bilgi için bkz. [DataSet ve DataTable Güvenlik Kılavuzu](security-guidance.md).
> Ayrıca, bir XML Web hizmeti oluştururken her zaman güvenlik etkilerini düşünmenizi öneririz. Bir XML Web hizmetinin güvenliğini sağlama hakkında bilgi için bkz. [ASP.NET kullanılarak oluşturulan XML Web hizmetlerinin güvenliğini sağlama](/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100)).  
  
## <a name="create-an-xml-web-service"></a>XML Web hizmeti oluşturma
  
1. XML Web hizmetini oluşturun.  
  
     Örnekte, verileri döndüren bir XML Web hizmeti oluşturulur ve bu durumda **Northwind** veritabanındaki müşterilerin bir listesi bulunur ve XML Web hizmeti 'nin özgün veri kaynağına geri çözümlenen veriler için güncelleştirmeler Içeren bir **veri kümesi** alır.  
  
     XML Web hizmeti, güncelleştirmeleri veri kaynağına geri çözümlemek üzere müşteriler ve **UpdateCustomers**listesini döndürmek için iki yöntem sunar: **GetCustomers**. XML Web hizmeti, Web sunucusunda DataSetSample. asmx adlı bir dosyada depolanır. Aşağıdaki kod, DataSetSample. asmx içeriğini özetler.  
  
    ```vb  
    <% @ WebService Language = "vb" Class = "Sample" %>  
    Imports System  
    Imports System.Data  
    Imports System.Data.SqlClient  
    Imports System.Web.Services  
  
    <WebService(Namespace:="http://microsoft.com/webservices/")> _  
    Public Class Sample  
  
    Public connection As SqlConnection = New SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind")  
  
      <WebMethod( Description := "Returns Northwind Customers", EnableSession := False )> _  
      Public Function GetCustomers() As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
          "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
        Dim custDS As DataSet = New DataSet()  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
        adapter.Fill(custDS, "Customers")  
  
        Return custDS  
      End Function  
  
      <WebMethod( Description := "Updates Northwind Customers", EnableSession := False )> _  
      Public Function UpdateCustomers(custDS As DataSet) As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter()  
  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Customers (CustomerID, CompanyName) " & _  
          "Values(@CustomerID, @CompanyName)", connection)  
        adapter.InsertCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.InsertCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Customers Set CustomerID = @CustomerID, " & _  
          "CompanyName = @CompanyName WHERE CustomerID = " & _  
          @OldCustomerID", connection)  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        Dim parameter As SqlParameter = _  
          adapter.UpdateCommand.Parameters.Add( _  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Customers WHERE CustomerID = @CustomerID", _  
          connection)  
        parameter = adapter.DeleteCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.Update(custDS, "Customers")  
  
        Return custDS  
      End Function  
    End Class  
    ```  
  
    ```csharp  
    <% @ WebService Language = "C#" Class = "Sample" %>  
    using System;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Web.Services;  
  
    [WebService(Namespace="http://microsoft.com/webservices/")]  
    public class Sample  
    {  
      public SqlConnection connection = new SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind");  
  
      [WebMethod( Description = "Returns Northwind Customers", EnableSession = false )]  
      public DataSet GetCustomers()  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter(  
          "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
        DataSet custDS = new DataSet();  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
        adapter.Fill(custDS, "Customers");  
  
        return custDS;  
      }  
  
      [WebMethod( Description = "Updates Northwind Customers",  
        EnableSession = false )]  
      public DataSet UpdateCustomers(DataSet custDS)  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        adapter.InsertCommand = new SqlCommand(  
          "INSERT INTO Customers (CustomerID, CompanyName) " +  
          "Values(@CustomerID, @CompanyName)", connection);  
        adapter.InsertCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.InsertCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
  
        adapter.UpdateCommand = new SqlCommand(  
          "UPDATE Customers Set CustomerID = @CustomerID, " +  
          "CompanyName = @CompanyName WHERE CustomerID = " +  
          "@OldCustomerID", connection);  
        adapter.UpdateCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.UpdateCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
        SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.DeleteCommand = new SqlCommand(  
        "DELETE FROM Customers WHERE CustomerID = @CustomerID",  
         connection);  
        parameter = adapter.DeleteCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.Update(custDS, "Customers");  
  
        return custDS;  
      }  
    }  
    ```  
  
     Tipik bir senaryoda, iyimser eşzamanlılık ihlallerini yakalamak için **UpdateCustomers** yöntemi yazılır. Kolaylık olması için örnek bunu içermez. İyimser eşzamanlılık hakkında daha fazla bilgi için bkz. [Iyimser eşzamanlılık](../optimistic-concurrency.md).  
  
2. Bir XML Web hizmeti proxy 'si oluşturun.  
  
     XML Web hizmeti istemcilerinin, sunulan yöntemleri kullanabilmesi için bir SOAP proxy 'si gerekir. Bu proxy 'yi sizin için Visual Studio 'Nun oluşturmasını sağlayabilirsiniz. Visual Studio içinden mevcut bir Web hizmetine bir Web başvurusu ayarlayarak, bu adımda açıklanan tüm davranışlar saydam bir şekilde gerçekleşir. Proxy sınıfını kendiniz oluşturmak istiyorsanız bu tartışmaya devam edin. Ancak çoğu durumda, istemci uygulaması için proxy sınıfı oluşturmak üzere Visual Studio kullanılması yeterlidir.  
  
     Bir proxy, Web Hizmetleri Açıklama Dili Aracı kullanılarak oluşturulabilir. Örneğin, XML Web hizmeti URL 'de açığa çıkarılacaksanız `http://myserver/data/DataSetSample.asmx` , **Webdata. dssample** ad alanı ile Visual Basic .net proxy oluşturmak için aşağıdaki gibi bir komut oluşturun ve bunu Sample. vb dosyasında depolayın.  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     Sample.cs dosyasında bir C# proxy oluşturmak için aşağıdaki komutu verin.  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     Proxy daha sonra bir kitaplık olarak derlenebilir ve XML Web hizmeti istemcisine aktarılabilir. Örnek. vb 'de depolanan Visual Basic .NET proxy kodunu sample.dll olarak derlemek için aşağıdaki komutu verin.  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     Sample.cs içinde depolanan C# proxy kodunu sample.dll olarak derlemek için aşağıdaki komutu verin.  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. Bir XML Web hizmeti istemcisi oluşturun.  
  
     Sizin için Visual Studio 'nun Web hizmeti proxy sınıfını oluşturmasını istiyorsanız, yalnızca istemci projesini oluşturun ve Çözüm Gezgini penceresinde projeye sağ tıklayıp **Add**  >  **hizmet başvurusu**Ekle ' yi seçin. **Hizmet başvurusu Ekle** Iletişim kutusunda **Gelişmiş**' i seçin ve ardından **Web başvurusu Ekle**' yi seçin. Kullanılabilir Web Hizmetleri listesinden Web hizmeti ' ni seçin (Web hizmeti geçerli çözüm içinde veya geçerli bilgisayarda yoksa Web hizmeti uç noktasının adresini sağlamak gerekebilir). XML Web hizmeti proxy 'sini kendiniz oluşturursanız (önceki adımda açıklandığı gibi), istemci kodunuza içeri aktarabilir ve XML Web hizmeti yöntemlerini kullanabilirsiniz.

     Aşağıdaki örnek kod, ara kitaplığı içeri aktarır, müşterilerin listesini almak için **GetCustomers** çağırır, yeni bir müşteri ekliyor ve sonra **UpdateCustomers**güncelleştirmeleriyle birlikte bir **veri kümesi** döndürüyor.  
  
     Örnek **DataSet. GetChanges** tarafından döndürülen **veri kümesini** **UpdateCustomers** 'e geçirir çünkü yalnızca değiştirilen satırların **UpdateCustomers**'a geçirilmesi gerekir. **UpdateCustomers** , çözümlenen değişiklikleri ve tüm satır hata bilgilerini güncelleştirmeden birleştirmek için, daha sonra mevcut **veri kümesiyle** **birleştirebilen** çözümlenmiş **veri kümesini**döndürür. Aşağıdaki kod, Web başvurusu oluşturmak için Visual Studio kullandığınızı ve **Web başvurusu Ekle** Iletişim kutusunda dssample için Web başvurusunu yeniden adlandırdığınızı varsayar.  
  
    ```vb  
    Imports System  
    Imports System.Data  
  
    Public Class Client  
  
      Public Shared Sub Main()  
        Dim proxySample As New DsSample.Sample ()  ' Proxy object.  
        Dim customersDataSet As DataSet = proxySample.GetCustomers()  
        Dim customersTable As DataTable = _  
          customersDataSet.Tables("Customers")  
  
        Dim rowAs DataRow = customersTable.NewRow()  
        row("CustomerID") = "ABCDE"  
        row("CompanyName") = "New Company Name"  
        customersTable.Rows.Add(row)  
  
        Dim updateDataSet As DataSet = _  
          proxySample.UpdateCustomers(customersDataSet.GetChanges())  
  
        customersDataSet.Merge(updateDataSet)  
        customersDataSet.AcceptChanges()  
      End Sub  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using System.Data;  
  
    public class Client  
    {  
      public static void Main()  
      {  
        Sample proxySample = new DsSample.Sample();  // Proxy object.  
        DataSet customersDataSet = proxySample.GetCustomers();  
        DataTable customersTable = customersDataSet.Tables["Customers"];  
  
        DataRow row = customersTable.NewRow();  
        row["CustomerID"] = "ABCDE";  
        row["CompanyName"] = "New Company Name";  
        customersTable.Rows.Add(row);  
  
        DataSet updateDataSet = new DataSet();  
  
        updateDataSet =
          proxySample.UpdateCustomers(customersDataSet.GetChanges());  
  
        customersDataSet.Merge(updateDataSet);  
        customersDataSet.AcceptChanges();  
      }  
    }  
    ```  
  
     Proxy sınıfını kendiniz oluşturmaya karar verirseniz, aşağıdaki ek adımları uygulamanız gerekir. Örneği derlemek için, oluşturulan ara sunucu kitaplığını (sample.dll) ve ilgili .NET kitaplıklarını sağlayın. Örneğin, Client. vb dosyasında depolanan örnek Visual Basic .NET sürümünü derlemek için aşağıdaki komutu verin.  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     Örneğin, client.cs dosyasında depolanan örnek C# sürümünü derlemek için aşağıdaki komutu verin.  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](../index.md)
- [DataSets, DataTables ve DataViews](index.md)
- [DataTables](datatables.md)
- [DataAdapter’dan bir DataSet Doldurma](../populating-a-dataset-from-a-dataadapter.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../updating-data-sources-with-dataadapters.md)
- [DataAdapter Parametreleri](../dataadapter-parameters.md)
- [Web Hizmetleri Açıklama Dili Aracı (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
