---
description: 'Hakkında daha fazla bilgi edinin: SQL Server örnekleri numaralandırma (ADO.NET)'
title: SQL Server örnekleri numaralandırılıyor
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: dd52142a06d5c7203eb8a2a14d0e6fc48f1e2a27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672315"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>SQL Server (ADO.NET) Numaralandırma Örnekleri

SQL Server, uygulamaların geçerli ağ içinde SQL Server örneklerini bulmasına izin verir. <xref:System.Data.Sql.SqlDataSourceEnumerator>Sınıfı, bu bilgileri uygulama geliştiricisi için gösterir ve <xref:System.Data.DataTable> tüm görünür sunucularla ilgili bir bilgi sağlar. Döndürülen bu tablo, bir Kullanıcı yeni bir bağlantı oluşturmayı denediğinde sağlanan listeyle eşleşen ve **bağlantı özellikleri** iletişim kutusundaki tüm kullanılabilir sunucuları içeren açılan listeyi genişleten ağ üzerinde bulunan sunucu örneklerinin bir listesini içerir. Görüntülenen sonuçlar her zaman tamamlanmaz.  
  
> [!NOTE]
> Çoğu Windows hizmetinde olduğu gibi, SQL Browser hizmetini en az olası ayrıcalıklarla çalıştırmak en iyisidir. SQL Browser hizmeti hakkında daha fazla bilgi ve davranışını yönetme hakkında daha fazla bilgi için bkz. SQL Server Books Online.  
  
## <a name="retrieving-an-enumerator-instance"></a>Numaralandırıcı örneği alma  

 Kullanılabilir SQL Server örnekleri hakkında bilgi içeren tabloyu almak için, önce paylaşılan/statik özelliğini kullanarak bir Numaralandırıcı almalısınız <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> :  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Statik örneği aldıktan sonra, <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> <xref:System.Data.DataTable> kullanılabilir sunucular hakkında içeren bir bilgi döndüren yöntemini çağırabilirsiniz:  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 Yöntem çağrısından döndürülen tablo, hepsi değer içeren şu sütunları içerir `string` :  
  
|Sütun|Açıklama|  
|------------|-----------------|  
|**aboneliğinde ve**|Sunucunun adı.|  
|**InstanceName**|Sunucu örneğinin adı. Sunucu varsayılan örnek olarak çalışıyorsa boştur.|  
|**Ikümeli**|Sunucunun bir kümenin parçası olup olmadığını gösterir.|  
|**Sürüm**|Sunucu sürümü. Örneğin:<br /><br /> -9.00. x (SQL Server 2005)<br />-10.0. xx (SQL Server 2008)<br />-10.50 olan. x (SQL Server 2008 R2)<br />-11.0. xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Listeleme sınırlamaları  

 Kullanılabilir sunucuların tümü listelenmeyebilir veya listede bulunmayabilir. Liste zaman aşımları ve ağ trafiği gibi etkenlere bağlı olarak farklılık gösterebilir. Bu, listenin birbirini izleyen iki çağrıda farklı olmasına neden olabilir. Yalnızca aynı ağdaki sunucular listelenir. Yayın paketleri genellikle, listelenen bir sunucuyu görmediğiniz, ancak çağrılar arasında kararlı hale geçememenizin neden olduğu yönlendiricilerde geçiş yapamaz.  
  
 Listelenen sunucular ve sürümü gibi ek bilgilere sahip olabilir veya olmayabilir `IsClustered` . Bu, listenin nasıl alındıklarına bağlıdır. SQL Server Browser hizmeti aracılığıyla listelenen sunucular, Windows altyapısı aracılığıyla bulunanlardan daha fazla ayrıntı alacak ve yalnızca adı listelecektir.  
  
> [!NOTE]
> Sunucu numaralandırması yalnızca tam güvende çalışırken kullanılabilir. Kısmen güvenilen bir ortamda çalışan derlemeler, <xref:System.Data.SqlClient.SqlClientPermission> kod erişimi güvenliği (CAS) iznine sahip olsalar bile kullanamaz.  
  
 SQL Server, <xref:System.Data.Sql.SqlDataSourceEnumerator> SQL Browser adlı bir dış Windows hizmetinin kullanımıyla ilgili bilgiler sağlar. Bu hizmet varsayılan olarak etkindir, ancak yöneticiler bunu kapatabilir veya devre dışı bırakabilir ve sunucu örneği bu sınıfta görünmez hale gelir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki konsol uygulaması, tüm görünür SQL Server örnekleri hakkındaki bilgileri alır ve konsol penceresinde bilgileri görüntüler.  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server ve ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
