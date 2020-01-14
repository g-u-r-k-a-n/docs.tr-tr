---
title: F# kullanarak Azure Tablo depolama kullanmaya başlama
description: Yapılandırılmış verileri Azure Tablo depolama veya Azure Cosmos DB kullanarak bulutta depolayın.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 23f5e40e1d9b3d5a0ee27d675362930ef86e90c5
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935583"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="6f612-103">F\# kullanarak Azure Tablo depolama ve Azure Cosmos DB Tablo API'si kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="6f612-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F\#</span></span>

<span data-ttu-id="6f612-104">Azure Table Storage, bulutta yapılandırılmış NoSQL verileri depolayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="6f612-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="6f612-105">Table Storage, şemasız tasarım ile bir anahtar/öznitelik deposudur.</span><span class="sxs-lookup"><span data-stu-id="6f612-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="6f612-106">Table Storage şemasız olduğu için uygulamanızın ihtiyaçları geliştikçe verilerinizi kolayca uyarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="6f612-107">Her türlü uygulama için verilere erişim hızlı ve uygun maliyetlidir.</span><span class="sxs-lookup"><span data-stu-id="6f612-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="6f612-108">Table Storage, benzer hacimdeki veriler için geleneksel SQL’e oranla çok daha düşük maliyetlidir.</span><span class="sxs-lookup"><span data-stu-id="6f612-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="6f612-109">Web uygulamaları için kullanıcı verileri, adres defterleri, cihaz bilgileri ve hizmetiniz için gerekli olan tüm diğer meta veri türleri gibi esnek veri kümelerini depolamak üzere Table Storage’ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="6f612-110">Bir tabloda istediğiniz kadar varlık depolayabilirsiniz ve bir depolama hesabı kapasite limitini dolduracak kadar tablo içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6f612-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="6f612-111">Azure Cosmos DB, Azure Tablo depolaması için yazılmış ve şu gibi Premium yetenekler gerektiren uygulamalar için Tablo API'si sağlar:</span><span class="sxs-lookup"><span data-stu-id="6f612-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="6f612-112">Anahtar teslimi genel dağıtım.</span><span class="sxs-lookup"><span data-stu-id="6f612-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="6f612-113">Dünya çapındaki adanmış aktarım hızı.</span><span class="sxs-lookup"><span data-stu-id="6f612-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="6f612-114">99 yüzdebirlikte tek basamaklı milisaniyelik gecikme süresi.</span><span class="sxs-lookup"><span data-stu-id="6f612-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="6f612-115">Garantili yüksek kullanılabilirlik.</span><span class="sxs-lookup"><span data-stu-id="6f612-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="6f612-116">Otomatik ikincil dizin oluşturma.</span><span class="sxs-lookup"><span data-stu-id="6f612-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="6f612-117">Azure Tablo depolama için yazılmış uygulamalar herhangi bir kod değişikliği olmadan Tablo API'sini kullanarak Azure Cosmos DB'ye geçirilebilir ve üst düzey özelliklerden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6f612-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="6f612-118">Tablo API’si, .NET, Java, Python ve Node.js ile kullanılabilecek istemci SDK’larına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6f612-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="6f612-119">Daha fazla bilgi için bkz. [Azure Cosmos DB tablo API'si giriş](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="6f612-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="6f612-120">Bu öğretici hakkında</span><span class="sxs-lookup"><span data-stu-id="6f612-120">About this tutorial</span></span>

<span data-ttu-id="6f612-121">Bu öğreticide, tablo oluşturma F# ve silme ve tablo verileri ekleme, güncelleştirme, silme ve sorgulama dahil olmak üzere Azure Tablo depolamayı veya Azure Cosmos db tablo API'si kullanarak bazı yaygın görevleri yapmak için nasıl kod yazacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f612-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f612-122">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="6f612-122">Prerequisites</span></span>

<span data-ttu-id="6f612-123">Bu kılavuzu kullanmak için, önce [bir Azure depolama hesabı](/azure/storage/storage-create-storage-account) veya [Azure Cosmos DB hesabı](https://azure.microsoft.com/try/cosmosdb/)oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f612-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="6f612-124">F# Betik oluşturma ve etkileşimli başlatma F#</span><span class="sxs-lookup"><span data-stu-id="6f612-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="6f612-125">Bu makaledeki örnekler, bir F# uygulama ya da bir F# komut dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6f612-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="6f612-126">F# Betik oluşturmak için, F# geliştirme ortamınızda `.fsx` uzantılı bir dosya oluşturun (örneğin `tables.fsx`).</span><span class="sxs-lookup"><span data-stu-id="6f612-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="6f612-127">Ardından, bir `#r` yönergesi kullanarak betiğe `WindowsAzure.Storage` paketini ve başvuru `WindowsAzure.Storage.dll` yüklemek için paket veya [NuGet](https://www.nuget.org/) [gibi bir](https://fsprojects.github.io/Paket/) [Paket Yöneticisi](package-management.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f612-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="6f612-128">Microsoft. Azure ad alanını almak için `Microsoft.WindowsAzure.ConfigurationManager` yeniden yapın.</span><span class="sxs-lookup"><span data-stu-id="6f612-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="6f612-129">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="6f612-129">Add namespace declarations</span></span>

<span data-ttu-id="6f612-130">Aşağıdaki `open` bildirimlerini `tables.fsx` dosyasının üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6f612-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="6f612-131">Azure depolama Bağlantı dizenizi alın</span><span class="sxs-lookup"><span data-stu-id="6f612-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="6f612-132">Azure Storage Table Service 'e bağlanıyorsanız, bu öğretici için bağlantı dizeniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f612-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="6f612-133">Bağlantı dizenizi Azure portal kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="6f612-134">Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="6f612-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="6f612-135">Azure Cosmos DB Bağlantı dizenizi alın</span><span class="sxs-lookup"><span data-stu-id="6f612-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="6f612-136">Azure Cosmos DB 'e bağlanıyorsanız, bu öğretici için bağlantı dizeniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f612-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="6f612-137">Bağlantı dizenizi Azure portal kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="6f612-138">Azure portal, Cosmos DB hesabınızda **ayarlar** > **bağlantı dizesi**' ne gidin ve **Kopyala** düğmesine tıklayarak birincil Bağlantı dizenizi kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="6f612-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span>

<span data-ttu-id="6f612-139">Öğreticide, aşağıdaki örnekte olduğu gibi betiğe Bağlantı dizenizi girin:</span><span class="sxs-lookup"><span data-stu-id="6f612-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="6f612-140">Ancak, bu gerçek projeler için **önerilmez** .</span><span class="sxs-lookup"><span data-stu-id="6f612-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="6f612-141">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="6f612-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="6f612-142">Depolama hesabı anahtarınızı korumak için her zaman özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="6f612-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="6f612-143">Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="6f612-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="6f612-144">Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="6f612-145">Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="6f612-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="6f612-146">Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f612-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="6f612-147">Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6f612-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="6f612-148">.NET Framework `ConfigurationManager` türü gibi bir API de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="6f612-149">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="6f612-149">Parse the connection string</span></span>

<span data-ttu-id="6f612-150">Bağlantı dizesini ayrıştırmak için şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="6f612-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="6f612-151">Bu, bir `CloudStorageAccount`döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f612-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="6f612-152">Tablo hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f612-152">Create the Table service client</span></span>

<span data-ttu-id="6f612-153">`CloudTableClient` sınıfı tablo depolamadaki tabloları ve varlıkları almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f612-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="6f612-154">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6f612-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="6f612-155">Artık Table Storage’dan veri okuyan ve bu depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="6f612-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="6f612-156">Bir tablo oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f612-156">Create a table</span></span>

<span data-ttu-id="6f612-157">Bu örnek, zaten yoksa, nasıl bir tablo oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6f612-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="6f612-158">Tabloya bir varlık ekleme</span><span class="sxs-lookup"><span data-stu-id="6f612-158">Add an entity to a table</span></span>

<span data-ttu-id="6f612-159">Bir varlık `TableEntity`devralan bir türe sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f612-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="6f612-160">`TableEntity` dilediğiniz şekilde genişletebilirsiniz, ancak türü parametre-daha az bir oluşturucuya sahip *olmalıdır* .</span><span class="sxs-lookup"><span data-stu-id="6f612-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="6f612-161">Yalnızca hem `get` hem de `set` olan özellikler Azure tablonuzda depolanır.</span><span class="sxs-lookup"><span data-stu-id="6f612-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="6f612-162">Bir varlığın bölüm ve satır anahtarı, varlığı tabloda benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f612-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="6f612-163">Aynı bölüm anahtarına sahip varlıklar farklı bölüm anahtarlı varlıklara göre daha hızlı sorgulanabilir ancak farklı bölüm anahtarlarının kullanılması paralel işlemler için daha büyük ölçeklendirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f612-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="6f612-164">Aşağıda, bölüm anahtarı olarak `lastName` ve satır anahtarı olarak `firstName` kullanan bir `Customer` örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f612-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="6f612-165">Şimdi tabloya `Customer` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6f612-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="6f612-166">Bunu yapmak için tabloda yürütülen bir `TableOperation` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6f612-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="6f612-167">Bu durumda, bir `Insert` işlemi oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="6f612-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="6f612-168">Toplu işlem varlık yerleştirme</span><span class="sxs-lookup"><span data-stu-id="6f612-168">Insert a batch of entities</span></span>

<span data-ttu-id="6f612-169">Tek bir yazma işlemi kullanarak bir tabloya bir varlık toplu işi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="6f612-170">Batch işlemleri, işlemleri tek bir yürütmeye birleştirmenizi sağlar, ancak bazı kısıtlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="6f612-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="6f612-171">Aynı toplu işlemde güncelleştirme, silme ve ekleme işlemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="6f612-172">Toplu işlem, en fazla 100 varlık içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6f612-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="6f612-173">Bir toplu işlemdeki tüm varlıkların aynı bölüm anahtarı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f612-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="6f612-174">Toplu işlemde bir sorgu gerçekleştirmek mümkün olsa da, toplu işlemdeki tek işlem olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f612-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="6f612-175">İşte bir toplu işlemin iki ekleme işlemini birleştiren kod:</span><span class="sxs-lookup"><span data-stu-id="6f612-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="6f612-176">Tüm varlıkları bir bölüme alma</span><span class="sxs-lookup"><span data-stu-id="6f612-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="6f612-177">Bir bölümdeki tüm varlıklar için bir tabloyu sorgulamak üzere bir `TableQuery` nesnesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f612-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="6f612-178">Burada, "Smith" bölümünün bölüm anahtarı olduğu varlıklar için filtre uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6f612-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="6f612-179">Şimdi sonuçları yazdırmıyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="6f612-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="6f612-180">Bir bölüme bir grup varlık alma</span><span class="sxs-lookup"><span data-stu-id="6f612-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="6f612-181">Bir bölümdeki tüm varlıkları sorgulamak istemiyorsanız bölüm anahtarı filtresi ile bir satır anahtarı filtresini birleştirerek bir aralık belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="6f612-182">Burada, "Smith" bölümünde bulunan ve satır anahtarı (ad) alfabedeki "M" den önceki bir harfle başlayan tüm varlıkları almak için iki filtre kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6f612-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="6f612-183">Şimdi sonuçları yazdırmıyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="6f612-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="6f612-184">Tek bir varlık alma</span><span class="sxs-lookup"><span data-stu-id="6f612-184">Retrieve a single entity</span></span>

<span data-ttu-id="6f612-185">Tek, belirli bir varlığı almak üzere bir sorgu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="6f612-186">Burada, "Ben Smith" müşterisini belirtmek için bir `TableOperation` kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6f612-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="6f612-187">Bir koleksiyon yerine bir `Customer`geri alırsınız.</span><span class="sxs-lookup"><span data-stu-id="6f612-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="6f612-188">Bir sorgudaki bölüm anahtarını ve satır anahtarını belirtme, tablo hizmetinden tek bir varlık almanın en hızlı yoludur.</span><span class="sxs-lookup"><span data-stu-id="6f612-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="6f612-189">Şimdi sonuçları yazdırmıyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="6f612-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a><span data-ttu-id="6f612-190">Bir varlığı değiştirme</span><span class="sxs-lookup"><span data-stu-id="6f612-190">Replace an entity</span></span>

<span data-ttu-id="6f612-191">Bir varlığı güncelleştirmek için tablo hizmetinden alın, varlık nesnesini değiştirin ve ardından `Replace` işlemi kullanarak değişiklikleri tablo hizmetine geri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6f612-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="6f612-192">Bu, sunucudaki varlık alındıktan sonra değiştirilmemişse varlığın sunucu üzerinde tamamen değiştirilmesini sağlar, bu durumda işlem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="6f612-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="6f612-193">Bu hata, uygulamanızın diğer kaynaklardaki değişikliklerin yanlışlıkla üzerine yazılmasını önlemektir.</span><span class="sxs-lookup"><span data-stu-id="6f612-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="6f612-194">Bir varlığı yerleştirme veya değiştirme</span><span class="sxs-lookup"><span data-stu-id="6f612-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="6f612-195">Bazen, tabloda bir varlık olup olmadığını bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="6f612-196">Varsa, içinde depolanan geçerli değerlere artık gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="6f612-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="6f612-197">Varlığı oluşturmak için `InsertOrReplace` kullanabilir veya varsa, durumu ne olursa olsun değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="6f612-198">Giriş özellikleri alt kümesi sorgulama</span><span class="sxs-lookup"><span data-stu-id="6f612-198">Query a subset of entity properties</span></span>

<span data-ttu-id="6f612-199">Tablo sorgusu, her biri yerine bir varlıktan yalnızca birkaç özelliği alabilir.</span><span class="sxs-lookup"><span data-stu-id="6f612-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="6f612-200">Projeksiyon olarak adlandırılan bu teknik, özellikle büyük varlıklar için sorgu performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="6f612-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="6f612-201">Burada yalnızca `DynamicTableEntity` ve `EntityResolver`kullanarak e-posta adresleri döndürürler.</span><span class="sxs-lookup"><span data-stu-id="6f612-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="6f612-202">Projeksiyon yerel depolama öykünücüsünde desteklenmez, bu nedenle bu kod yalnızca Tablo hizmetinde bir hesap kullanırken çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="6f612-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="6f612-203">Sayfalarda zaman uyumsuz olarak varlıkları alma</span><span class="sxs-lookup"><span data-stu-id="6f612-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="6f612-204">Çok sayıda varlığı okuyorsanız ve bunların tümünün dönmesini beklemek yerine alındığı gibi işlemek istiyorsanız, bölümlenmiş bir sorgu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="6f612-205">Burada, büyük bir sonuç kümesinin döndürülmesini beklerken yürütmenin engellenmemesi için zaman uyumsuz iş akışı kullanarak sayfalardaki sonuçları döndürüyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="6f612-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="6f612-206">Artık bu hesaplamayı zaman uyumlu olarak yürütütemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f612-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="6f612-207">Bir varlığı silme</span><span class="sxs-lookup"><span data-stu-id="6f612-207">Delete an entity</span></span>

<span data-ttu-id="6f612-208">Bir varlığı aldıktan sonra silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="6f612-209">Bir varlığı güncelleştirmede olduğu gibi, varlık onu aldıktan sonra değiştiyse bu başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="6f612-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="6f612-210">Bir tablo silme</span><span class="sxs-lookup"><span data-stu-id="6f612-210">Delete a table</span></span>

<span data-ttu-id="6f612-211">Bir depolama hesabındaki bir tabloyu silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f612-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="6f612-212">Silinen bir tablo, silme işleminin ardından yeniden oluşturma için belirli bir süre kullanılamayacaktır.</span><span class="sxs-lookup"><span data-stu-id="6f612-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="6f612-213">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="6f612-213">Next steps</span></span>

<span data-ttu-id="6f612-214">Artık tablo depolamanın temellerini öğrendiğinize göre, daha karmaşık depolama görevleri ve Azure Cosmos DB Tablo API'si hakkında bilgi edinmek için bu bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="6f612-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="6f612-215">Azure Cosmos DB Tablo API’sine Giriş</span><span class="sxs-lookup"><span data-stu-id="6f612-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="6f612-216">.NET başvurusu için Depolama İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="6f612-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="6f612-217">Azure depolama türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="6f612-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="6f612-218">Azure Depolama Ekibi Blog’u</span><span class="sxs-lookup"><span data-stu-id="6f612-218">Azure Storage Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="6f612-219">Bağlantı Dizeleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6f612-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
