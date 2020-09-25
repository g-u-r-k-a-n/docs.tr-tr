---
title: 'Nasıl yapılır: Model ve Eşleme Dosyalarını Gömülü Kaynak Yapma'
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 8496dcad5422d1a45af52e58325efd360768da34
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198294"
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="e5cfd-102">Nasıl yapılır: Model ve Eşleme Dosyalarını Gömülü Kaynak Yapma</span><span class="sxs-lookup"><span data-stu-id="e5cfd-102">How to: Make Model and Mapping Files Embedded Resources</span></span>

<span data-ttu-id="e5cfd-103">Entity Framework, bir uygulamanın katıştırılmış kaynakları olarak model ve eşleme dosyalarını dağıtmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5cfd-103">The Entity Framework enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="e5cfd-104">Katıştırılmış model ve eşleme dosyaları olan derlemenin, varlık bağlantısıyla aynı uygulama etki alanında yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5cfd-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="e5cfd-105">Daha fazla bilgi için bkz. [bağlantı dizeleri](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="e5cfd-105">For more information, see [Connection Strings](connection-strings.md).</span></span> <span data-ttu-id="e5cfd-106">Varsayılan olarak, Varlık Veri Modeli araçları modeli ve eşleme dosyalarını gömer.</span><span class="sxs-lookup"><span data-stu-id="e5cfd-106">By default, the Entity Data Model tools embed the model and mapping files.</span></span> <span data-ttu-id="e5cfd-107">Model ve eşleme dosyalarını el ile tanımladığınızda, dosyaların bir Entity Framework uygulamayla birlikte gömülü kaynaklar olarak dağıtıldığından emin olmak için bu yordamı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5cfd-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an Entity Framework application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5cfd-108">Katıştırılmış kaynakları korumak için, model ve eşleme dosyaları her değiştirildiğinde bu yordamı yinelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5cfd-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="e5cfd-109">Model ve eşleme dosyalarını eklemek için</span><span class="sxs-lookup"><span data-stu-id="e5cfd-109">To embed model and mapping files</span></span>  
  
1. <span data-ttu-id="e5cfd-110">**Çözüm Gezgini**, kavramsal (. csdl) dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="e5cfd-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2. <span data-ttu-id="e5cfd-111">**Özellikler** bölmesinde, **derleme eylemini** **katıştırılmış kaynak**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e5cfd-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3. <span data-ttu-id="e5cfd-112">Depolama (. ssdl) dosyası ve eşleme (. MSL) dosyası için 1 ve 2. adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="e5cfd-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4. <span data-ttu-id="e5cfd-113">**Çözüm Gezgini**, App.config dosyasına çift tıklayın ve ardından `Metadata` `connectionString` özniteliğinde parametresini aşağıdaki biçimlerden birine göre değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e5cfd-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    - <span data-ttu-id="e5cfd-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="e5cfd-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    - <span data-ttu-id="e5cfd-115">`Metadata=` `res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="e5cfd-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    - `Metadata=res://*;`  
  
     <span data-ttu-id="e5cfd-116">Daha fazla bilgi için bkz. [bağlantı dizeleri](connection-strings.md).</span><span class="sxs-lookup"><span data-stu-id="e5cfd-116">For more information, see [Connection Strings](connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5cfd-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5cfd-117">Example</span></span>  

 <span data-ttu-id="e5cfd-118">Aşağıdaki bağlantı dizesi, [AdventureWorks Sales modeli](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)için gömülü modele ve eşleme dosyalarına başvurur.</span><span class="sxs-lookup"><span data-stu-id="e5cfd-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="e5cfd-119">Bu bağlantı dizesi projenin App.config dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="e5cfd-119">This connection string is stored in the project's App.config file.</span></span>  

## <a name="see-also"></a><span data-ttu-id="e5cfd-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5cfd-120">See also</span></span>

- [<span data-ttu-id="e5cfd-121">Modelleme ve Eşleme</span><span class="sxs-lookup"><span data-stu-id="e5cfd-121">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- [<span data-ttu-id="e5cfd-122">Nasıl yapılır: Bağlantı Dizesi Tanımlama</span><span class="sxs-lookup"><span data-stu-id="e5cfd-122">How to: Define the Connection String</span></span>](how-to-define-the-connection-string.md)
- [<span data-ttu-id="e5cfd-123">Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5cfd-123">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)
- <span data-ttu-id="e5cfd-124">[ADO.NET Varlık Veri Modeli araçları](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e5cfd-124">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
