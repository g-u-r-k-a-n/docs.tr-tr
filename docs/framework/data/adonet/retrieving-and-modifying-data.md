---
title: Verileri alma ve değiştirme
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 65c373ecff004e219527754bf2e9cc56837dc305
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980060"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="066f3-102">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="066f3-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="066f3-103">Herhangi bir veritabanı uygulamasının birincil işlevi bir veri kaynağına bağlanıyor ve içerdiği verileri alıyor.</span><span class="sxs-lookup"><span data-stu-id="066f3-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="066f3-104">ADO.NET veri sağlayıcıları bir uygulama ile veri kaynağı arasında bir köprü olarak görev yapar ve ayrıca, bir **DataReader** veya **DataAdapter**kullanarak veri alma ve komutları yürütmenize olanak tanır. .NET Framework</span><span class="sxs-lookup"><span data-stu-id="066f3-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="066f3-105">Herhangi bir veritabanı uygulamasının anahtar işlevi, veritabanında depolanan verileri güncelleştirebilme olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="066f3-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="066f3-106">ADO.NET ' de, verileri güncelleştirme, **DataAdapter** ve <xref:System.Data.DataSet>ile **komut** nesnelerinin kullanımı ile ilgilidir. Ayrıca işlem kullanmayı da gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="066f3-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="066f3-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="066f3-107">In This Section</span></span>  
 [<span data-ttu-id="066f3-108">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="066f3-108">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)  
 <span data-ttu-id="066f3-109">Bir veri kaynağına nasıl bağlantı kurulacağını ve bağlantı olaylarıyla nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="066f3-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="066f3-110">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="066f3-110">Connection Strings</span></span>](connection-strings.md)  
 <span data-ttu-id="066f3-111">Bağlantı dizesi anahtar sözcükleri, güvenlik bilgileri ve bunları depolama ve alma gibi bağlantı dizelerini kullanmanın çeşitli yönlerini açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="066f3-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="066f3-112">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="066f3-112">Connection Pooling</span></span>](connection-pooling.md)  
 <span data-ttu-id="066f3-113">.NET Framework veri sağlayıcıları için bağlantı havuzunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="066f3-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="066f3-114">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="066f3-114">Commands and Parameters</span></span>](commands-and-parameters.md)  
 <span data-ttu-id="066f3-115">Komutların ve komut oluşturucuların nasıl oluşturulacağını, parametrelerin nasıl yapılandırılacağını ve verilerin alınması ve değiştirilmesi için komutların nasıl yürütüleceğini açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="066f3-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="066f3-116">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="066f3-116">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)  
 <span data-ttu-id="066f3-117">DataReaders, DataAdapter, Parameters, DataAdapter olaylarını işleme ve Batch işlemleri gerçekleştirme konularını açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="066f3-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="066f3-118">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="066f3-118">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)  
 <span data-ttu-id="066f3-119">Yerel işlemlerin nasıl gerçekleştirileceğini, dağıtılmış işlemlerin ve iyimser eşzamanlılık ile nasıl çalıştığını açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="066f3-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="066f3-120">Kimliği veya Otomatik Sayı Değerlerini Alma</span><span class="sxs-lookup"><span data-stu-id="066f3-120">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="066f3-121">Bir SQL Server tablosundaki bir **kimlik** sütunu için veya bir Microsoft Access tablosundaki bir **OtomatikSayı** alanı için oluşturulan değerleri bir tabloda bulunan satır sütunuyla eşlemek için bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="066f3-121">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="066f3-122">Kimlik değerlerini bir `DataTable`birleştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="066f3-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="066f3-123">İkili Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="066f3-123">Retrieving Binary Data</span></span>](retrieving-binary-data.md)  
 <span data-ttu-id="066f3-124">`CommandBehavior`kullanarak ikili verilerin veya büyük veri yapılarının nasıl alınacağını açıklar.`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="066f3-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="066f3-125">`DataReader`varsayılan davranışını değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="066f3-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="066f3-126">Saklı Yordamlarla Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="066f3-126">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="066f3-127">Yeni bir kimlik değeri döndüren bir veritabanına satır eklemek için saklı yordam giriş parametrelerinin ve çıkış parametrelerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="066f3-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="066f3-128">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="066f3-128">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)  
 <span data-ttu-id="066f3-129">Kullanılabilir veritabanlarının veya katalogların, tabloların ve görünümlerin bir veritabanında, tablolar için var olan kısıtlamaların ve bir veri kaynağından alınan diğer şema bilgilerinin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="066f3-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="066f3-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="066f3-130">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="066f3-131">Sağlayıcı fabrikası modelini açıklar ve `System.Data.Common` ad alanındaki temel sınıfların nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="066f3-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="066f3-132">ADO.NET’te Veri İzleme</span><span class="sxs-lookup"><span data-stu-id="066f3-132">Data Tracing in ADO.NET</span></span>](data-tracing.md)  
 <span data-ttu-id="066f3-133">ADO.NET 'in yerleşik veri izleme işlevselliği nasıl sağladığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="066f3-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="066f3-134">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="066f3-134">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="066f3-135">`SqlClient` ve `OracleClient`için kullanılabilen performans sayaçlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="066f3-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="066f3-136">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="066f3-136">Asynchronous Programming</span></span>](asynchronous-programming.md)  
 <span data-ttu-id="066f3-137">Zaman uyumsuz programlama için ADO.NET desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="066f3-137">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="066f3-138">SqlClient Akış Desteği</span><span class="sxs-lookup"><span data-stu-id="066f3-138">SqlClient Streaming Support</span></span>](sqlclient-streaming-support.md)  
 <span data-ttu-id="066f3-139">Verilerin belleğe tam olarak yüklenmesini gerektirmeden SQL Server veri akışı yapan uygulamaların nasıl yazılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="066f3-139">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="066f3-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="066f3-140">See also</span></span>

- [<span data-ttu-id="066f3-141">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="066f3-141">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="066f3-142">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="066f3-142">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="066f3-143">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="066f3-143">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- [<span data-ttu-id="066f3-144">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="066f3-144">SQL Server and ADO.NET</span></span>](./sql/index.md)
- [<span data-ttu-id="066f3-145">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="066f3-145">ADO.NET Overview</span></span>](ado-net-overview.md)
