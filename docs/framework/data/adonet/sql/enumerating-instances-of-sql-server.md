---
title: SQL Server örnekleri numaralandırılıyor
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: c59db5869ed848071611cdbf985b45dc59790d69
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979995"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="0cfca-102">SQL Server (ADO.NET) Numaralandırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="0cfca-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
<span data-ttu-id="0cfca-103">SQL Server, uygulamaların geçerli ağ içinde SQL Server örneklerini bulmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="0cfca-103">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="0cfca-104"><xref:System.Data.Sql.SqlDataSourceEnumerator> sınıfı, bu bilgileri uygulama geliştiricisi için gösterir ve tüm görünür sunucularla ilgili bilgileri içeren bir <xref:System.Data.DataTable> sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cfca-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="0cfca-105">Döndürülen bu tablo, bir Kullanıcı yeni bir bağlantı oluşturmayı denediğinde sağlanan listeyle eşleşen ve **bağlantı özellikleri** iletişim kutusundaki tüm kullanılabilir sunucuları içeren açılan listeyi genişleten ağ üzerinde bulunan sunucu örneklerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0cfca-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="0cfca-106">Görüntülenen sonuçlar her zaman tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="0cfca-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cfca-107">Çoğu Windows hizmetinde olduğu gibi, SQL Browser hizmetini en az olası ayrıcalıklarla çalıştırmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="0cfca-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="0cfca-108">SQL Browser hizmeti hakkında daha fazla bilgi ve davranışını yönetme hakkında daha fazla bilgi için bkz. SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="0cfca-108">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="0cfca-109">Numaralandırıcı örneği alma</span><span class="sxs-lookup"><span data-stu-id="0cfca-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="0cfca-110">Kullanılabilir SQL Server örnekleri hakkında bilgi içeren tabloyu almak için, önce paylaşılan/statik <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> özelliğini kullanarak bir Numaralandırıcı almanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="0cfca-110">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="0cfca-111">Statik örneği aldıktan sonra, kullanılabilir sunucular hakkında bilgi içeren bir <xref:System.Data.DataTable> döndüren <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> yöntemini çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0cfca-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="0cfca-112">Yöntem çağrısından döndürülen tablo, hepsi `string` değerler içeren aşağıdaki sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="0cfca-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="0cfca-113">Sütun</span><span class="sxs-lookup"><span data-stu-id="0cfca-113">Column</span></span>|<span data-ttu-id="0cfca-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0cfca-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0cfca-115">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="0cfca-115">**ServerName**</span></span>|<span data-ttu-id="0cfca-116">Sunucusunun adı.</span><span class="sxs-lookup"><span data-stu-id="0cfca-116">Name of the server.</span></span>|  
|<span data-ttu-id="0cfca-117">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="0cfca-117">**InstanceName**</span></span>|<span data-ttu-id="0cfca-118">Sunucu örneğinin adı.</span><span class="sxs-lookup"><span data-stu-id="0cfca-118">Name of the server instance.</span></span> <span data-ttu-id="0cfca-119">Sunucu varsayılan örnek olarak çalışıyorsa boştur.</span><span class="sxs-lookup"><span data-stu-id="0cfca-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="0cfca-120">**Ikümeli**</span><span class="sxs-lookup"><span data-stu-id="0cfca-120">**IsClustered**</span></span>|<span data-ttu-id="0cfca-121">Sunucunun bir kümenin parçası olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cfca-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="0cfca-122">**Sürüm**</span><span class="sxs-lookup"><span data-stu-id="0cfca-122">**Version**</span></span>|<span data-ttu-id="0cfca-123">Sunucu sürümü.</span><span class="sxs-lookup"><span data-stu-id="0cfca-123">Version of the server.</span></span> <span data-ttu-id="0cfca-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0cfca-124">For example:</span></span><br /><br /> <span data-ttu-id="0cfca-125">-9.00. x (SQL Server 2005)</span><span class="sxs-lookup"><span data-stu-id="0cfca-125">-   9.00.x (SQL Server 2005)</span></span><br /><span data-ttu-id="0cfca-126">-   10.0.xx (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="0cfca-126">-   10.0.xx (SQL Server 2008)</span></span><br /><span data-ttu-id="0cfca-127">-10.50 olan. x (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="0cfca-127">-   10.50.x (SQL Server 2008 R2)</span></span><br /><span data-ttu-id="0cfca-128">-11.0. xx (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="0cfca-128">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="0cfca-129">Listeleme sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="0cfca-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="0cfca-130">Kullanılabilir sunucuların tümü listelenmeyebilir veya listede bulunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0cfca-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="0cfca-131">Liste zaman aşımları ve ağ trafiği gibi etkenlere bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="0cfca-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="0cfca-132">Bu, listenin birbirini izleyen iki çağrıda farklı olmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0cfca-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="0cfca-133">Yalnızca aynı ağdaki sunucular listelenir.</span><span class="sxs-lookup"><span data-stu-id="0cfca-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="0cfca-134">Yayın paketleri genellikle, listelenen bir sunucuyu görmediğiniz, ancak çağrılar arasında kararlı hale geçememenizin neden olduğu yönlendiricilerde geçiş yapamaz.</span><span class="sxs-lookup"><span data-stu-id="0cfca-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="0cfca-135">Listelenen sunucular `IsClustered` ve sürümü gibi ek bilgilere sahip olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="0cfca-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="0cfca-136">Bu, listenin nasıl alındıklarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0cfca-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="0cfca-137">SQL Server Browser hizmeti aracılığıyla listelenen sunucular, Windows altyapısı aracılığıyla bulunanlardan daha fazla ayrıntı alacak ve yalnızca adı listelecektir.</span><span class="sxs-lookup"><span data-stu-id="0cfca-137">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cfca-138">Sunucu numaralandırması yalnızca tam güvende çalışırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cfca-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="0cfca-139">Kısmen güvenilen bir ortamda çalışan derlemeler, <xref:System.Data.SqlClient.SqlClientPermission> kodu erişim güvenliği (CAS) iznine sahip olsalar bile kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="0cfca-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="0cfca-140">SQL Server, SQL Browser adlı bir dış Windows hizmeti kullanılarak <xref:System.Data.Sql.SqlDataSourceEnumerator> ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cfca-140">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="0cfca-141">Bu hizmet varsayılan olarak etkindir, ancak yöneticiler bunu kapatabilir veya devre dışı bırakabilir ve sunucu örneği bu sınıfta görünmez hale gelir.</span><span class="sxs-lookup"><span data-stu-id="0cfca-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cfca-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cfca-142">Example</span></span>  
 <span data-ttu-id="0cfca-143">Aşağıdaki konsol uygulaması, tüm görünür SQL Server örnekleri hakkındaki bilgileri alır ve konsol penceresinde bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0cfca-143">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0cfca-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cfca-144">See also</span></span>

- [<span data-ttu-id="0cfca-145">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0cfca-145">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="0cfca-146">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0cfca-146">ADO.NET Overview</span></span>](../ado-net-overview.md)
