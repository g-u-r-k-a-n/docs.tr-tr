---
title: Cloud Native için aday uygulamalar
description: Bulut Yerel yaklaşımdan hangi tür uygulamaların avantajına yarar olduğunu öğrenin
author: robvet
ms.date: 05/14/2020
ms.openlocfilehash: 8f00633a575dad12b0bc1d5adb83acac03db0659
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160950"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="40476-103">Cloud Native için aday uygulamalar</span><span class="sxs-lookup"><span data-stu-id="40476-103">Candidate apps for cloud native</span></span>

<span data-ttu-id="40476-104">Portföyünüzdeki uygulamalara bakın.</span><span class="sxs-lookup"><span data-stu-id="40476-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="40476-105">Bunlardan kaç tane bulut yerel mimari için uygun?</span><span class="sxs-lookup"><span data-stu-id="40476-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="40476-106">Bunların tümü?</span><span class="sxs-lookup"><span data-stu-id="40476-106">All of them?</span></span> <span data-ttu-id="40476-107">Belki de misiniz?</span><span class="sxs-lookup"><span data-stu-id="40476-107">Perhaps some?</span></span>

<span data-ttu-id="40476-108">Maliyet/avantaj Analizi uygulama, büyük olasılıkla bulut Yerel olması için gereken Hefty fiyat etiketini desteklememe olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="40476-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="40476-109">Cloud Native 'in maliyeti, uygulamanın iş değerini aşacak.</span><span class="sxs-lookup"><span data-stu-id="40476-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="40476-110">Bulut Native için hangi tür bir uygulama aday olabilir?</span><span class="sxs-lookup"><span data-stu-id="40476-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="40476-111">İş yeteneklerini/özelliklerini sürekli olarak gelişmesi gereken Stratejik Kurumsal Sistem</span><span class="sxs-lookup"><span data-stu-id="40476-111">Strategic enterprise system that need to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="40476-112">Yüksek bir sürüm hızı gerektiren ve yüksek güvenle bir uygulama</span><span class="sxs-lookup"><span data-stu-id="40476-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="40476-113">Tüm sistemin tam yeniden dağıtımı *olmadan* tek tek özelliklerin yayımlanması gereken bir sistem</span><span class="sxs-lookup"><span data-stu-id="40476-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="40476-114">Farklı teknoloji yığınlarında uzmanlığa sahip takımlar tarafından geliştirilen bir uygulama</span><span class="sxs-lookup"><span data-stu-id="40476-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="40476-115">Bağımsız olarak ölçeklendirilmesi gereken bileşenlere sahip bir uygulama</span><span class="sxs-lookup"><span data-stu-id="40476-115">An application with components that must scale independently</span></span>

<span data-ttu-id="40476-116">Ardından eski sistemler vardır.</span><span class="sxs-lookup"><span data-stu-id="40476-116">Then there are legacy systems.</span></span> <span data-ttu-id="40476-117">Yeni uygulamalar oluşturmak istiyoruz, ancak iş için kritik olan eski iş yüklerini modernleştirmekten genellikle sorumlu veriyoruz.</span><span class="sxs-lookup"><span data-stu-id="40476-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="40476-118">Zaman içinde, eski bir uygulama mikro hizmetlere, Kapsayıcılı ve sonunda "replatbiçimlendirilmiş" bir bulutta yerel mimariye ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="40476-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="40476-119">Eski uygulamaları modernleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="40476-119">Modernizing legacy apps</span></span>

<span data-ttu-id="40476-120">[Azure bulut ve Windows kapsayıcıları ile](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) ücretsiz Microsoft e-book modernleştirin mevcut .NET uygulamaları, şirket içi iş yüklerini buluta geçirmeye yönelik yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="40476-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="40476-121">Şekil 1-10, eski uygulamaların modernleştirilmesi için tek, tek boyutlu uygun bir strateji olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="40476-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![Eski iş yüklerini geçirme stratejileri](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="40476-123">**Şekil 1-10**.</span><span class="sxs-lookup"><span data-stu-id="40476-123">**Figure 1-10**.</span></span> <span data-ttu-id="40476-124">Eski iş yüklerini geçirme stratejileri</span><span class="sxs-lookup"><span data-stu-id="40476-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="40476-125">Kritik olmayan tek parçalı uygulamalar hızlı bir kaldırma ve kaydırma ([bulut altyapıya](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)yönelik) geçiş işleminden büyük ölçüde avantaj sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="40476-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) migration.</span></span> <span data-ttu-id="40476-126">Burada, şirket içi iş yükü, hiçbir değişiklik yapılmadan bulut tabanlı bir VM 'de yeniden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="40476-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="40476-127">Bu yaklaşım [IaaS (hizmet olarak altyapı) modeli](https://azure.microsoft.com/overview/what-is-iaas/)kullanır.</span><span class="sxs-lookup"><span data-stu-id="40476-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="40476-128">Azure, böyle bir taşımanın daha kolay olması için [Azure geçişi](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)ve [Azure veritabanı geçiş hizmeti](https://azure.microsoft.com/campaigns/database-migration/) gibi çeşitli araçlar içerir.</span><span class="sxs-lookup"><span data-stu-id="40476-128">Azure includes several tools such as [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) to make such a move easier.</span></span> <span data-ttu-id="40476-129">Bu strateji bazı maliyet tasarrufu sağlayabilir, ancak bu gibi uygulamalar genellikle kilit açma ve bulut bilgi işlemin avantajlarından faydalanmayı sanallaştırmıştır.</span><span class="sxs-lookup"><span data-stu-id="40476-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="40476-130">İş açısından kritik öneme sahip tek parçalı uygulamalar, gelişmiş bir kaldırma ve kaydırma (*buluta iyileştirilmiş*) geçişinden faydalanır.</span><span class="sxs-lookup"><span data-stu-id="40476-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="40476-131">Bu yaklaşım, uygulamanın çekirdek mimarisini değiştirmeden anahtar bulut hizmetlerini etkinleştiren dağıtım iyileştirmelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="40476-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="40476-132">Örneğin [, uygulamayı](/virtualization/windowscontainers/about/) kapsayıcınıza ve bu kitabın ilerleyen kısımlarında açıklanan [Azure Kubernetes Hizmetleri](https://azure.microsoft.com/services/kubernetes-service/)gibi bir kapsayıcı Orchestrator 'a dağıtırsınız.</span><span class="sxs-lookup"><span data-stu-id="40476-132">For example, you might [containerize](/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="40476-133">Bulutta, uygulama veritabanları, ileti kuyrukları, izleme ve dağıtılmış önbelleğe alma gibi diğer bulut hizmetlerini tüketebilir.</span><span class="sxs-lookup"><span data-stu-id="40476-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="40476-134">Son olarak, Stratejik Kurumsal işlevleri gerçekleştiren tek parçalı uygulamalar, bu kitabın konusu olan bir *bulutta yerel* yaklaşımdan en iyi şekilde faydalanabilir.</span><span class="sxs-lookup"><span data-stu-id="40476-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="40476-135">Bu yaklaşım, çeviklik ve hız sağlar.</span><span class="sxs-lookup"><span data-stu-id="40476-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="40476-136">Ancak, kod yeniden oluşturma, yeniden mimari işleme ve kodu yeniden yazma maliyetlerine gelir.</span><span class="sxs-lookup"><span data-stu-id="40476-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="40476-137">Siz ve takımınız, buluta özgü bir yaklaşıma uygun olduğunu düşünüyorsanız, bu kararı kuruluşunuzla kararlaşmanızı behooves.</span><span class="sxs-lookup"><span data-stu-id="40476-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="40476-138">Bulutta yerel yaklaşımın hangi iş sorununa göre çözülecektir?</span><span class="sxs-lookup"><span data-stu-id="40476-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="40476-139">İş ihtiyaçları nasıl hizalanır?</span><span class="sxs-lookup"><span data-stu-id="40476-139">How would it align with business needs?</span></span>

- <span data-ttu-id="40476-140">Artırılmış güvenle özelliklerin hızlı sürümleri mı?</span><span class="sxs-lookup"><span data-stu-id="40476-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="40476-141">Hassas ölçeklenebilirlik-kaynakların daha verimli kullanımı</span><span class="sxs-lookup"><span data-stu-id="40476-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="40476-142">Geliştirilmiş sistem dayanıklılığı?</span><span class="sxs-lookup"><span data-stu-id="40476-142">Improved system resiliency?</span></span>

- <span data-ttu-id="40476-143">Sistem performansı iyileştirildi mi?</span><span class="sxs-lookup"><span data-stu-id="40476-143">Improved system performance?</span></span>

- <span data-ttu-id="40476-144">İşlemlere daha fazla görünürlük mı?</span><span class="sxs-lookup"><span data-stu-id="40476-144">More visibility into operations?</span></span>

- <span data-ttu-id="40476-145">İş için en iyi araca ulaşmak üzere geliştirme platformları ve veri depoları Blend?</span><span class="sxs-lookup"><span data-stu-id="40476-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="40476-146">Gelecekteki uygulama yatırımı</span><span class="sxs-lookup"><span data-stu-id="40476-146">Future-proof application investment?</span></span>

<span data-ttu-id="40476-147">Doğru geçiş stratejisi, kuruluşunuzun önceliklerine ve hedeflediğiniz sistemlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="40476-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="40476-148">Çoğu için, tek parçalı bir uygulamayı en iyi duruma getirmeyi veya N katmanlı bir uygulamaya kaba hizmetler eklemeyi daha fazla maliyetli olabilir.</span><span class="sxs-lookup"><span data-stu-id="40476-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="40476-149">Bu gibi durumlarda, Azure App Service tarafından sunulan bulut PaaS yeteneklerini de tamamen kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40476-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="40476-150">Özet</span><span class="sxs-lookup"><span data-stu-id="40476-150">Summary</span></span>

<span data-ttu-id="40476-151">Bu bölümde, bulutta yerel bilgi işlem tanıtıldık.</span><span class="sxs-lookup"><span data-stu-id="40476-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="40476-152">Bulut Yerel uygulamasını hedefleyen anahtar özellikleri ile birlikte bir tanım sağladık.</span><span class="sxs-lookup"><span data-stu-id="40476-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="40476-153">Bu yatırım ve çabayı göz ardı edebilir uygulama türlerine baktık.</span><span class="sxs-lookup"><span data-stu-id="40476-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="40476-154">Bu konuda daha ayrıntılı bilgi edinmek için artık Cloud Native 'e çok daha ayrıntılı bir bakış sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="40476-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="40476-155">Başvurular</span><span class="sxs-lookup"><span data-stu-id="40476-155">References</span></span>

- [<span data-ttu-id="40476-156">Bulut Yerel Bilgi Işlem altyapısı</span><span class="sxs-lookup"><span data-stu-id="40476-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="40476-157">.NET mikro hizmetleri: Kapsayıcılı .NET uygulamaları için mimari</span><span class="sxs-lookup"><span data-stu-id="40476-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="40476-158">Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin</span><span class="sxs-lookup"><span data-stu-id="40476-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="40476-159">Bir Davis 'e göre bulutta yerel desenler</span><span class="sxs-lookup"><span data-stu-id="40476-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="40476-160">On Iki öğeli uygulamanın ötesinde</span><span class="sxs-lookup"><span data-stu-id="40476-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="40476-161">Kod olarak altyapı nedir?</span><span class="sxs-lookup"><span data-stu-id="40476-161">What is Infrastructure as Code</span></span>](/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="40476-162">Uıber mühendisin mikro dağıtımı: her gün güvenle dağıtım</span><span class="sxs-lookup"><span data-stu-id="40476-162">Uber Engineering's Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="40476-163">Netflix kodu dağıtır</span><span class="sxs-lookup"><span data-stu-id="40476-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="40476-164">WeChat mikro hizmetlerini ölçeklendirmeye yönelik aşırı yükleme denetimi</span><span class="sxs-lookup"><span data-stu-id="40476-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
><span data-ttu-id="40476-165">[Önceki](definition.md) 
> [Sonraki](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="40476-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>
