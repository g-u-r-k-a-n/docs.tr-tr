---
title: Yönetilen İş Parçacığı Oluşturma
description: Temel bilgiler, en iyi uygulamalar, iş parçacığı nesneleri & özellikler, başvuru sayfaları & daha fazlasını kapsayan, .NET 'teki yönetilen iş parçacığı hakkındaki makalelerin bağlantılarını inceleyin.
ms.date: 03/30/2017
helpviewer_keywords:
- threading [.NET], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: 28ba05c345d22b14512d280f3855934d727b3142
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728452"
---
# <a name="managed-threading"></a><span data-ttu-id="ce34d-103">Yönetilen iş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="ce34d-103">Managed threading</span></span>

<span data-ttu-id="ce34d-104">Tek bir işlemciye veya birkaç kullanıcıya sahip bilgisayarlar için geliştirme olsanız da, uygulama şu anda başka bir iş yapıyor olsa bile, uygulamanızın kullanıcıyla en iyi yanıt verme etkileşimini sağlamasını istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce34d-104">Whether you're developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="ce34d-105">Birden çok iş parçacığının kullanılması, uygulamanızı kullanıcıya yanıt vermenin en güçlü yöntemlerinden biridir ve aynı zamanda Kullanıcı olayları sırasında veya hatta içinde işlemciyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ce34d-105">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="ce34d-106">Bu bölümde iş parçacığı temel kavramları tanıtılırken, yönetilen iş parçacığı kavramlarıyla ve yönetilen iş parçacığı kullanımıyla odaklanır.</span><span class="sxs-lookup"><span data-stu-id="ce34d-106">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce34d-107">.NET Framework 4 ' ten itibaren, çok iş parçacıklı programlama, <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları, [paralel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), ad alanındaki eşzamanlı koleksiyon sınıfları <xref:System.Collections.Concurrent?displayProperty=nameWithType> ve iş parçacıkları yerine görev kavramını temel alan bir programlama modeli ile büyük ölçüde basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ce34d-107">Starting with .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="ce34d-108">Daha fazla bilgi için bkz. [paralel programlama](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce34d-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce34d-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ce34d-109">In This Section</span></span>  

 [<span data-ttu-id="ce34d-110">Yönetilen İş Parçacığı Oluşturma Temelleri</span><span class="sxs-lookup"><span data-stu-id="ce34d-110">Managed Threading Basics</span></span>](managed-threading-basics.md)  
 <span data-ttu-id="ce34d-111">Yönetilen iş parçacığına genel bir bakış sağlar ve birden çok iş parçacığının ne zaman kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce34d-111">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="ce34d-112">Iş parçacıkları ve Iş parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="ce34d-112">Using Threads and Threading</span></span>](using-threads-and-threading.md)  
 <span data-ttu-id="ce34d-113">İş parçacıklarını oluşturmayı, başlatmayı, duraklatmayı, sürdürmeyi ve iptal etmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce34d-113">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="ce34d-114">Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ce34d-114">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="ce34d-115">Eşitleme düzeylerini, kilitlenmeleri ve yarış durumlarını ve diğer iş parçacığı sorunlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce34d-115">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="ce34d-116">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="ce34d-116">Threading Objects and Features</span></span>](threading-objects-and-features.md)  
 <span data-ttu-id="ce34d-117">İş parçacıklarının etkinliklerini ve farklı iş parçacıklarında erişilen nesnelerin verilerini eşleştirmek için kullanabileceğiniz yönetilen sınıfları açıklar ve iş parçacığı havuzu iş parçacıkları için bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce34d-117">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ce34d-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ce34d-118">Reference</span></span>  

 <xref:System.Threading>  
 <span data-ttu-id="ce34d-119">Yönetilen iş parçacıklarını kullanma ve eşitleme için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="ce34d-119">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="ce34d-120">Birden çok iş parçacığı ile kullanım için güvenli olan koleksiyon sınıflarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ce34d-120">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="ce34d-121">Eşzamanlı işleme görevlerinin oluşturulması ve zamanlanması için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="ce34d-121">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ce34d-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ce34d-122">Related Sections</span></span>  

 [<span data-ttu-id="ce34d-123">Uygulama Etki Alanları</span><span class="sxs-lookup"><span data-stu-id="ce34d-123">Application Domains</span></span>](../../framework/app-domains/application-domains.md)  
 <span data-ttu-id="ce34d-124">Uygulama etki alanlarına ve bunların ortak dil altyapısı tarafından kullanımına ilişkin bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce34d-124">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="ce34d-125">Zaman uyumsuz dosya g/ç</span><span class="sxs-lookup"><span data-stu-id="ce34d-125">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)  
 <span data-ttu-id="ce34d-126">Zaman uyumsuz I/O'nun performans avantajlarını ve temek işleyişini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce34d-126">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="ce34d-127">Görev Tabanlı Zaman Uyumsuz Desen (TAP)</span><span class="sxs-lookup"><span data-stu-id="ce34d-127">Task-based Asynchronous Pattern (TAP)</span></span>](../asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="ce34d-128">.NET 'te zaman uyumsuz programlama için önerilen modele genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce34d-128">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="ce34d-129">Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="ce34d-129">Calling Synchronous Methods Asynchronously</span></span>](../asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="ce34d-130">Temsilcilerin yerleşik özellikleri kullanılarak iş parçacığı havuzu iş parçacıklarında yöntemlerin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce34d-130">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="ce34d-131">Paralel programlama</span><span class="sxs-lookup"><span data-stu-id="ce34d-131">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="ce34d-132">Uygulamalarda birden çok iş parçacığının kullanımını kolaylaştıran paralel programlama kitaplıklarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce34d-132">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="ce34d-133">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="ce34d-133">Parallel LINQ (PLINQ)</span></span>](../parallel-programming/introduction-to-plinq.md)  
 <span data-ttu-id="ce34d-134">Birden çok işlemcinin avantajlarından yararlanmak için sorguları paralel olarak çalıştırmaya yönelik bir sistem açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce34d-134">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
