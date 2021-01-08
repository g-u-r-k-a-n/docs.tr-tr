---
title: İzlenecek yollar ve teknik başlangıca genel bakış
description: Azure bulut ve Windows kapsayıcıları Ile mevcut .NET uygulamalarını modernleştirin | İzlenecek yollar ve teknik Başlarken Genel Bakış
ms.date: 12/21/2020
ms.openlocfilehash: 6bfa25e3eeeecf5a936f378df3ae548d6fa37a30
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025283"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="bc4e1-103">İzlenecek yollar ve teknik başlangıca genel bakış</span><span class="sxs-lookup"><span data-stu-id="bc4e1-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="bc4e1-104">Bu e-kitabın boyutunu sınırlamak için, ek teknik belgeler ve bir GitHub deposunda sunulan tam izlenecek yollar.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="bc4e1-105">Bu bölümde açıklanan çevrimiçi izlenecek yollar serisi, Windows kapsayıcılarına dayalı birden çok ortamın adım adım kurulumunu ve Azure 'a dağıtımını ele almaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="bc4e1-106">Aşağıdaki bölümlerde her bir izlenecek yolun ne olduğu, amaçları ve üst düzey Vizyonumuz açıklanmakta ve dahil olan görevlerin bir diyagramı sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="bc4e1-107">İzlenecek *yolları, ' de bulunan uygulama GitHub* deposu wiki ' de yer alır <https://github.com/dotnet-architecture/eShopModernizing/wiki> .</span><span class="sxs-lookup"><span data-stu-id="bc4e1-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="bc4e1-108">Teknik izlenecek yol listesi</span><span class="sxs-lookup"><span data-stu-id="bc4e1-108">Technical walkthrough list</span></span>

<span data-ttu-id="bc4e1-109">Aşağıdaki Başlarken izlenecek yollar, kapsayıcıları kullanarak kaldırıp kaydıracağınız örnek uygulamalar için tutarlı ve kapsamlı teknik rehberlik sağlar ve ardından Azure 'da birden çok dağıtım seçeneği kullanarak hareket edebilir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="bc4e1-110">Aşağıdaki izlenecek yolların her biri, GitHub 'da bulunan yeni örnek eShopLegacy ve Eshopmodernize uygulamalarını kullanır <https://github.com/dotnet-architecture/eShopModernizing> .</span><span class="sxs-lookup"><span data-stu-id="bc4e1-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="bc4e1-111">**EShop eski uygulamalar turu (temel uygulamalar modernleştirin)**</span><span class="sxs-lookup"><span data-stu-id="bc4e1-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="bc4e1-112">**Mevcut ASP.NET Web uygulamalarınızı (WebForms & MVC) Windows kapsayıcılarıyla kapsayıcıyla**</span><span class="sxs-lookup"><span data-stu-id="bc4e1-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="bc4e1-113">**Mevcut WCF hizmetlerinizi (N katmanlı uygulamalar) Windows kapsayıcılarıyla Kapsayıçleştirme**</span><span class="sxs-lookup"><span data-stu-id="bc4e1-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="bc4e1-114">**Windows kapsayıcıları tabanlı uygulamanızı Azure VM 'lerine dağıtma**</span><span class="sxs-lookup"><span data-stu-id="bc4e1-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="bc4e1-115">**Windows kapsayıcıları tabanlı uygulamalarınızı Azure Container Service 'de Kubernetes 'e dağıtma**</span><span class="sxs-lookup"><span data-stu-id="bc4e1-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="bc4e1-116">İzlenecek yol 1: eShop eski uygulamalar turu</span><span class="sxs-lookup"><span data-stu-id="bc4e1-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="bc4e1-117">Teknik izlenecek yol kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="bc4e1-117">Technical walkthrough availability</span></span>

<span data-ttu-id="bc4e1-118">Tam teknik izlenecek yol, GitHub deposu wiki ' de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="bc4e1-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="bc4e1-119">wiki gözden geçirmeleri için Eshopmodernize</span><span class="sxs-lookup"><span data-stu-id="bc4e1-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="bc4e1-120">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc4e1-120">Overview</span></span>

<span data-ttu-id="bc4e1-121">Bu kılavuzda, üç örnek eski uygulamanın ilk uygulamasını inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="bc4e1-122">İlk iki örnek Web uygulaması tek parçalı bir mimariye sahiptir ve klasik ASP.NET kullanılarak oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="bc4e1-123">Bir uygulama ASP.NET 4. x MVC 'yi temel alır. ikinci uygulama, ASP.NET 4. x Web Forms temel alır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="bc4e1-124">Üçüncü uygulama, bir istemci WinForms uygulaması ve sunucu tarafı [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) hizmeti tarafından oluşturulan 3 katmanlı bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="bc4e1-125">Tüm bu uygulamalar [GitHub](https://github.com/dotnet-architecture/eShopModernizing)deposunda mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="bc4e1-126">Hedefler</span><span class="sxs-lookup"><span data-stu-id="bc4e1-126">Goals</span></span>

<span data-ttu-id="bc4e1-127">Bu izlenecek yolun ana amacı, bu uygulamaları ve bunların kod ve yapılandırmasıyla ilgili bilgi almak için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="bc4e1-128">Uygulamaları, test amacıyla SQL veritabanını kullanmadan, sahte verileri oluşturup kullanacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="bc4e1-129">Bu isteğe bağlı yapılandırma, bağımlılık ekleme işlemini ayrılmış bir şekilde temel alır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="bc4e1-130">Senaryo 1: ASP.NET Web Apps</span><span class="sxs-lookup"><span data-stu-id="bc4e1-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="bc4e1-131">Aşağıdaki şekilde, özgün eski ASP.NET Web uygulamalarının basit senaryosu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Özgün eski ASP.NET Web uygulamalarının basit mimari senaryosu](./media/image5-1.png)

<span data-ttu-id="bc4e1-133">Bir iş etki alanı perspektifinden, her iki uygulama da aynı katalog yönetimi özelliklerini sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="bc4e1-134">EShop Enterprise ekibinin üyeleri, ürün kataloğunu görüntülemek ve düzenlemek için uygulamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="bc4e1-135">Sonraki şekilde, ilk uygulama ekran görüntüleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-135">The next figure shows the initial app screenshots.</span></span>

![ASP.NET MVC ve ASP.NET Web Forms uygulamaları (mevcut/eski teknolojiler)](./media/image5-2.png)

<span data-ttu-id="bc4e1-137">ASP.NET 4. x veya önceki sürümlerindeki bağımlılıklar (MVC veya Web Forms için), kodun ASP.NET Core MVC kullanılarak tam olarak yeniden yazılması durumunda .NET Core üzerinde çalıştırılmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="bc4e1-138">Senaryo 2: WCF hizmeti ve WinForms istemci uygulaması (3 katmanlı uygulama)</span><span class="sxs-lookup"><span data-stu-id="bc4e1-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="bc4e1-139">Aşağıdaki şekilde, özgün 3 katmanlı eski uygulamanın basit senaryosu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Bir WCF hizmeti ve bir WinForms istemci uygulaması ile, eski, 3 katmanlı ilk uygulamanın basit mimari senaryosu](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="bc4e1-141">Avantajlar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-141">Benefits</span></span>

<span data-ttu-id="bc4e1-142">Bu izlenecek yolun avantajları basittir: yalnızca kod ve ilk uygulamalar hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="bc4e1-143">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-143">Next steps</span></span>

<span data-ttu-id="bc4e1-144">GitHub wiki üzerinde bu içeriği daha ayrıntılı bir şekilde gezin:</span><span class="sxs-lookup"><span data-stu-id="bc4e1-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="bc4e1-145">Temel ASP.NET MVC ve "eski" uygulamalar Web Forms turuna katılın</span><span class="sxs-lookup"><span data-stu-id="bc4e1-145">Tour on the baseline ASP.NET MVC and Web Forms "legacy" apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="bc4e1-146">Taban çizgisi WCF hizmeti ve WinForms (3 katmanlı) "eski" uygulama turu</span><span class="sxs-lookup"><span data-stu-id="bc4e1-146">Tour on the baseline WCF service and WinForms (3-Tier) "legacy" app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="bc4e1-147">İzlenecek yol 2: mevcut .NET uygulamalarınızı Windows kapsayıcılarıyla Kapsayıyleştirme</span><span class="sxs-lookup"><span data-stu-id="bc4e1-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="bc4e1-148">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc4e1-148">Overview</span></span>

<span data-ttu-id="bc4e1-149">MVC, Web Forms veya WCF tabanlı uygulamalar, üretim, geliştirme ve test ortamları gibi mevcut .NET uygulamalarının dağıtımını geliştirmek için Windows kapsayıcıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="bc4e1-150">Hedefler</span><span class="sxs-lookup"><span data-stu-id="bc4e1-150">Goals</span></span>

<span data-ttu-id="bc4e1-151">Bu izlenecek yolun amacı, mevcut bir .NET Framework uygulamasını kapsayıdırma için size çeşitli seçenekler göstermektir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="bc4e1-152">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bc4e1-152">You can:</span></span>

- <span data-ttu-id="bc4e1-153">[Visual studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (visual Studio 2017 veya üzeri sürümler) kullanarak uygulamanızı kapsayıkatın.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="bc4e1-154">El ile bir [Dockerfile](https://docs.docker.com/engine/reference/builder/)ekleyerek ve sonra [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)kullanarak uygulamanızı kapsayıcın.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="bc4e1-155">[Img2Docker](https://github.com/docker/communitytools-image2docker-win) aracını kullanarak (Docker 'daki açık kaynaklı bir araç) uygulamanızı kapsayıkatın.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="bc4e1-156">Bu izlenecek yol, Docker yaklaşımına yönelik Visual Studio 2017 araçlarına odaklanır, ancak diğer iki yaklaşım Dockerfiles kullanımına benzer şekilde oldukça benzerdir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="bc4e1-157">Senaryo 1: Kapsayıcılı ASP.NET Web uygulamaları</span><span class="sxs-lookup"><span data-stu-id="bc4e1-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="bc4e1-158">Aşağıdaki şekilde Kapsayıcılı, eski Web Apps uygulamalarına yönelik senaryo gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Geliştirme ortamında Kapsayıcılı ASP.NET uygulamalarının Basitleştirilmiş mimari diyagramı](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="bc4e1-160">Senaryo 2: Kapsayıcılı WCF hizmeti</span><span class="sxs-lookup"><span data-stu-id="bc4e1-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="bc4e1-161">Aşağıdaki şekilde kapsayıcılı bir WCF hizmeti olan 3 katmanlı bir uygulamanın senaryosu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Bir geliştirme ortamında Kapsayıcılı WCF hizmetinin Basitleştirilmiş mimari diyagramı](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="bc4e1-163">Avantajlar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-163">Benefits</span></span>

<span data-ttu-id="bc4e1-164">Tek parçalı uygulamanızı bir kapsayıcıda çalıştırmanın avantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="bc4e1-165">İlk olarak, uygulama için bir görüntü oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-165">First, you create an image for the application.</span></span> <span data-ttu-id="bc4e1-166">Bu noktadan itibaren, her dağıtım aynı ortamda çalışır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="bc4e1-167">Her kapsayıcı aynı işletim sistemi sürümünü kullanır, aynı bağımlılıklar sürümü yüklü, aynı .NET Framework sürümünü kullanır ve aynı işlem kullanılarak oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="bc4e1-168">Temel olarak, bir Docker görüntüsü kullanarak uygulamanızın bağımlılıklarını kontrol edersiniz.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="bc4e1-169">Kapsayıcılar, kapsayıcıları dağıtırken uygulamayla birlikte seyahat ediyor.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="bc4e1-170">Ek bir avantaj, geliştiricilerin uygulamayı Windows kapsayıcıları tarafından sunulan tutarlı bir ortamda çalıştırabildiği bir avantajdır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="bc4e1-171">Yalnızca belirli sürümlerle görüntülenen sorunlar, hazırlama veya üretim ortamında kullanıma sunulacak şekilde hemen bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="bc4e1-172">Geliştirme ortamlarının üyeleri tarafından kullanılan geliştirme ortamlarındaki farklar, uygulamalar kapsayıcılar içinde çalıştırıldığında daha az önemlidir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="bc4e1-173">Kapsayıcılı uygulamalar için de eğri ölçeği genişletme eğrisi vardır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="bc4e1-174">Kapsayıcılı uygulamalar, makine başına normal uygulama dağıtımlarıyla karşılaştırıldığında bir VM 'de veya fiziksel makinede daha fazla uygulama ve hizmet örneği (kapsayıcılara göre) sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="bc4e1-175">Bu yaklaşım, özellikle Kubernetes gibi düzenleyiciler kullandığınızda daha yüksek yoğunluklu ve daha az gereken kaynağa çevrilir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-175">This approach translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="bc4e1-176">Kapsayıcılama, ideal durumlarda uygulama kodunda herhangi bir değişiklik yapılmasını gerektirmez (C \# ).</span><span class="sxs-lookup"><span data-stu-id="bc4e1-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="bc4e1-177">Çoğu senaryoda yalnızca Docker dağıtım meta verileri dosyalarına (Dockerfiles ve Docker Compose dosyaları) ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="bc4e1-178">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-178">Next steps</span></span>

<span data-ttu-id="bc4e1-179">GitHub wiki üzerinde bu içeriği daha ayrıntılı bir şekilde gezin:</span><span class="sxs-lookup"><span data-stu-id="bc4e1-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="bc4e1-180">Windows kapsayıcıları ve Docker ile .NET Framework Web uygulamalarını kapsayıcıyla</span><span class="sxs-lookup"><span data-stu-id="bc4e1-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="bc4e1-181">WCF hizmetine Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="bc4e1-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="bc4e1-182">İzlenecek yol 3: Windows kapsayıcıları tabanlı uygulamanızı Azure VM 'lerine dağıtma</span><span class="sxs-lookup"><span data-stu-id="bc4e1-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="bc4e1-183">Teknik izlenecek yol kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="bc4e1-183">Technical walkthrough availability</span></span>

<span data-ttu-id="bc4e1-184">Tam teknik izlenecek yol, GitHub deposu wiki ' de kullanılabilir: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="bc4e1-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="bc4e1-185">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc4e1-185">Overview</span></span>

<span data-ttu-id="bc4e1-186">Azure 'da bir Windows Server 2016 sanal makinesi (VM) üzerindeki bir Docker konağına dağıtım, geliştirme/test/hazırlık ortamlarını hızla ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="bc4e1-187">Ayrıca, Sınayıcılar veya iş kullanıcılarının uygulamayı doğrulaması için ortak bir yer sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="bc4e1-188">VM 'Ler ayrıca geçerli bir hizmet olarak altyapı (IaaS) üretim ortamları olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="bc4e1-189">Hedefler</span><span class="sxs-lookup"><span data-stu-id="bc4e1-189">Goals</span></span>

<span data-ttu-id="bc4e1-190">Bu izlenecek yolun amacı, Windows Server 2016 veya sonraki sürümlerini temel alan Azure VM 'lerine Windows kapsayıcıları dağıtırken size sahip olduğunuz birden çok alternatifi göstermektir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="bc4e1-191">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-191">Scenarios</span></span>

<span data-ttu-id="bc4e1-192">Bu izlenecek yolda çeşitli senaryolar ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="bc4e1-193">Senaryo A: Azure VM 'ye Docker altyapısı bağlantısı aracılığıyla bir geliştirme PC 'den dağıtma</span><span class="sxs-lookup"><span data-stu-id="bc4e1-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Bir Azure sanal makinesine Docker altyapısı bağlantısı aracılığıyla bir geliştirme BILGISAYARDAN dağıtma](./media/image5-4.png)

<span data-ttu-id="bc4e1-195">**Şekil 5-4.**</span><span class="sxs-lookup"><span data-stu-id="bc4e1-195">**Figure 5-4.**</span></span> <span data-ttu-id="bc4e1-196">Bir Azure sanal makinesine Docker altyapısı bağlantısı aracılığıyla bir geliştirme BILGISAYARDAN dağıtma</span><span class="sxs-lookup"><span data-stu-id="bc4e1-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="bc4e1-197">Senaryo B: bir Docker kayıt defteri aracılığıyla bir Azure VM 'ye dağıtma</span><span class="sxs-lookup"><span data-stu-id="bc4e1-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Docker kayıt defteri aracılığıyla bir Azure VM 'ye dağıtma](./media/image5-5.png)

<span data-ttu-id="bc4e1-199">**Şekil 5-5.**</span><span class="sxs-lookup"><span data-stu-id="bc4e1-199">**Figure 5-5.**</span></span> <span data-ttu-id="bc4e1-200">Docker kayıt defteri aracılığıyla bir Azure VM 'ye dağıtma</span><span class="sxs-lookup"><span data-stu-id="bc4e1-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="bc4e1-201">Senaryo C: Azure DevOps Services içindeki CI/CD işlem hatlarından bir Azure VM 'sine dağıtım</span><span class="sxs-lookup"><span data-stu-id="bc4e1-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Azure DevOps Services ' deki CI/CD işlem hatlarından bir Azure VM 'sine dağıtım](./media/image5-6.png)

<span data-ttu-id="bc4e1-203">**Şekil 5-6.**</span><span class="sxs-lookup"><span data-stu-id="bc4e1-203">**Figure 5-6.**</span></span> <span data-ttu-id="bc4e1-204">Azure DevOps Services ' deki CI/CD işlem hatlarından bir Azure VM 'sine dağıtım</span><span class="sxs-lookup"><span data-stu-id="bc4e1-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="bc4e1-205">Windows kapsayıcıları için Azure VM 'Leri</span><span class="sxs-lookup"><span data-stu-id="bc4e1-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="bc4e1-206">Windows kapsayıcıları için Azure VM 'Leri, hem Docker Engine 'in ayarlandığı Windows Server 2016, Windows 10 veya sonraki sürümleri temel alır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="bc4e1-207">Çoğu durumda, Azure VM 'lerinde Windows Server 2016 kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="bc4e1-208">Azure Şu anda **kapsayıcılarla Windows Server 2016** ADLı bir VM sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="bc4e1-209">Windows Server Core veya Windows nano Server ile yeni Windows Server kapsayıcısı özelliğini denemek için bu VM 'yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="bc4e1-210">Kapsayıcı işletim sistemi görüntüleri yüklenir ve ardından sanal makine Docker ile kullanıma hazırdır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="bc4e1-211">Avantajlar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-211">Benefits</span></span>

<span data-ttu-id="bc4e1-212">Windows kapsayıcıları, şirket içi Windows Server 2016 VM 'lerine dağıtılabilse de, Azure 'a dağıtırken, kullanıma hazırlama öncesi Windows Server kapsayıcısı VM 'Leri ile kullanmaya başlamak için daha kolay bir yol alırsınız.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="bc4e1-213">Ayrıca, Test edicilerin erişebileceği ve Azure sanal makine ölçek kümeleri aracılığıyla otomatik ölçeklenebilirlik sağlayan ortak bir çevrimiçi konum alırsınız.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-213">You also get a common online location that's accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="bc4e1-214">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-214">Next steps</span></span>

<span data-ttu-id="bc4e1-215">GitHub wiki üzerinde bu içeriği daha ayrıntılı bir şekilde gezin:</span><span class="sxs-lookup"><span data-stu-id="bc4e1-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="bc4e1-216">Adım 4: Windows kapsayıcıları tabanlı uygulamalarınızı Azure Container Instances (ACI) uygulamasına dağıtma</span><span class="sxs-lookup"><span data-stu-id="bc4e1-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="bc4e1-217">Teknik izlenecek yol kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="bc4e1-217">Technical walkthrough availability</span></span>

<span data-ttu-id="bc4e1-218">Tam teknik izlenecek yol, GitHub deposu wiki ' de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="bc4e1-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="bc4e1-219">[Uygulamaları ACI 'ye dağıtma (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="bc4e1-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="bc4e1-220">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc4e1-220">Overview</span></span>

<span data-ttu-id="bc4e1-221">[Azure Container Instances (ACI)](/azure/container-instances/) , kapsayıcılar geliştirme/test/hazırlama ortamının tek tek örneklerini dağıtabileceğiniz en hızlı yoldur.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-221">[Azure Container Instances (ACI)](/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="bc4e1-222">Hedefler</span><span class="sxs-lookup"><span data-stu-id="bc4e1-222">Goals</span></span>

<span data-ttu-id="bc4e1-223">Bu izlenecek yol, Windows kapsayıcılarını Azure Container Instances (ACI) ile dağıtırken ve ACI 'de Eshopmodernize uygulamaları nasıl dağıtabileceğiniz ana senaryoları gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="bc4e1-224">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-224">Scenarios</span></span>

<span data-ttu-id="bc4e1-225">Uygulamaların yalnızca birini veya tümünü (MVC uygulaması, WebForms uygulaması veya WCF hizmeti) dağıtmak gibi, Eshopmodernize uygulamalarını dağıtmaya yönelik Çeşitlemeler bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="bc4e1-226">Aşağıda gösterilen aşağıdaki senaryoda, ASP.NET MVC uygulamasını ve her ikisi de bir kapsayıcı olarak dağıtılan SQL Server kapsayıcısını ACI 'ye (Azure Container Instances) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-226">In the following scenario shown below, you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Geliştirme ortamından acı 'ye dağıtma](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="bc4e1-228">Avantajlar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-228">Benefits</span></span>

<span data-ttu-id="bc4e1-229">Azure Container Instances, sanal makine sağlamak veya daha yüksek düzey bir hizmet benimsemek zorunda kalmadan Azure’da Docker kapsayıcıları oluşturmayı ve yönetmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="bc4e1-230">ACI ile, bir Windows kapsayıcısını doğrudan Azure 'da dağıtabilir ve saniyeler içinde tam etki alanı adı (FQDN) ile internet 'te kullanıma sunabilirsiniz (Windows kapsayıcı görüntünüzü Docker Hub veya Azure Container Registry gibi bir Docker kayıt defterine hazırlayın).</span><span class="sxs-lookup"><span data-stu-id="bc4e1-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="bc4e1-231">Dikkat edilmesi gerekenler</span><span class="sxs-lookup"><span data-stu-id="bc4e1-231">Considerations</span></span>

<span data-ttu-id="bc4e1-232">Windows kapsayıcılarını tam .NET Framework/ASP.NET veya SQL Server ile Azure Container Instances (ACI) ile dağıtmak, Docker görüntüsünün her seferinde ve SQL Container Image 'ın boyutlarını (Docker kayıt defteri 'nden çekildiğinden), düzenli bir Docker ana bilgisayarına (Windows kapsayıcıları ile Windows Server 2016 gibi) dağıtım kadar hızlı değildir. (15,1 GB) ve ASP.NET kapsayıcı görüntüsü (13,9 GB) önemli ölçüde büyüktür, ancak Azure 'da (AKS) bulunan Kubernetes gibi bir düzenleyicinin tamamını değil, kendi Docker ana bilgisayarınızı (Azure 'daki Windows kapsayıcıları sanal makinesi ile kalıcı olarak çevrimiçi Windows Server 2016) kullanmaktan çok daha ucuz. öte yandan, üretim dağıtımları için harika bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="bc4e1-233">Ana sonuç olarak, Azure Container Instances kullanımı geliştirme/test senaryoları ve CI/CD işlem hatları için çok etkileyici bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-233">As the main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

### <a name="next-steps"></a><span data-ttu-id="bc4e1-234">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-234">Next steps</span></span>

<span data-ttu-id="bc4e1-235">GitHub wiki üzerinde bu içeriği daha ayrıntılı bir şekilde gezin:</span><span class="sxs-lookup"><span data-stu-id="bc4e1-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="bc4e1-236">İzlenecek yol 5: Windows kapsayıcıları tabanlı uygulamalarınızı Azure Container Service Kubernetes 'e dağıtma</span><span class="sxs-lookup"><span data-stu-id="bc4e1-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="bc4e1-237">Teknik izlenecek yol kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="bc4e1-237">Technical walkthrough availability</span></span>

<span data-ttu-id="bc4e1-238">Tam teknik izlenecek yol, GitHub deposu wiki ' de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="bc4e1-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="bc4e1-239">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc4e1-239">Overview</span></span>

<span data-ttu-id="bc4e1-240">Windows kapsayıcılarına dayalı bir uygulamanın, IaaS VM 'lerinden daha da fazla hareket eden platformları kullanması hızla gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="bc4e1-241">Bu yaklaşım, kolayca yüksek ölçeklenebilirlik ve daha iyi otomatik ölçeklenebilirlik elde etmek ve otomatikleştirilmiş dağıtımlar ve sürüm oluşturma konusunda önemli bir geliştirme sağlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-241">This approach is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="bc4e1-242">[Azure Container Services](https://azure.microsoft.com/services/container-service/)'de bulunan Orchestrator [Kubernetes](https://kubernetes.io/)'i kullanarak bu hedeflere ulaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="bc4e1-243">Hedefler</span><span class="sxs-lookup"><span data-stu-id="bc4e1-243">Goals</span></span>

<span data-ttu-id="bc4e1-244">Bu izlenecek yol, Azure Container Service ' de bir Windows kapsayıcı tabanlı uygulamayı Kubernetes 'e dağıtmayı öğrenmektir ( *K8s* olarak da bilinir).</span><span class="sxs-lookup"><span data-stu-id="bc4e1-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="bc4e1-245">Sıfırdan Kubernetes 'e dağıtım iki adımlı bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="bc4e1-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="bc4e1-246">Azure Container Service için bir Kubernetes kümesi dağıtın.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="bc4e1-247">Uygulamayı ve ilgili kaynakları Kubernetes kümesine dağıtın.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="bc4e1-248">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="bc4e1-249">Senaryo A: bir geliştirme ortamından bir Kubernetes kümesine doğrudan dağıtım</span><span class="sxs-lookup"><span data-stu-id="bc4e1-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Geliştirme ortamından bir Kubernetes kümesine doğrudan dağıtım](./media/image5-7.png)

<span data-ttu-id="bc4e1-251">**Şekil 5-7.**</span><span class="sxs-lookup"><span data-stu-id="bc4e1-251">**Figure 5-7.**</span></span> <span data-ttu-id="bc4e1-252">Geliştirme ortamından bir Kubernetes kümesine doğrudan dağıtım</span><span class="sxs-lookup"><span data-stu-id="bc4e1-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="bc4e1-253">Senaryo B: Azure DevOps Services içindeki CI/CD işlem hatlarından bir Kubernetes kümesine dağıtım</span><span class="sxs-lookup"><span data-stu-id="bc4e1-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Azure DevOps Services ' deki CI/CD işlem hatlarından bir Kubernetes kümesine dağıtın](./media/image5-8.png)

<span data-ttu-id="bc4e1-255">**Şekil 5-8.**</span><span class="sxs-lookup"><span data-stu-id="bc4e1-255">**Figure 5-8.**</span></span> <span data-ttu-id="bc4e1-256">Azure DevOps Services ' deki CI/CD işlem hatlarından bir Kubernetes kümesine dağıtın</span><span class="sxs-lookup"><span data-stu-id="bc4e1-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="bc4e1-257">Avantajlar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-257">Benefits</span></span>

<span data-ttu-id="bc4e1-258">Kubernetes içindeki bir kümeye dağıtmanın birçok avantajı vardır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="bc4e1-259">En büyük avantaj, kullanmak istediğiniz kapsayıcı örneği sayısına (mevcut düğümlerde iç ölçeklenebilirlik) göre ve kümedeki düğüm veya VM sayısına (kümenin genel ölçeklenebilirliği) göre, uygulamayı ölçeklendirebilmeniz için üretime hazır bir ortam elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="bc4e1-260">Azure Container Service, popüler açık kaynaklı araçları ve teknolojileri özel olarak Azure için iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="bc4e1-261">Kapsayıcılar ve uygulama yapılandırmanız için taşınabilirlik sağlayan açık bir çözüm alırsınız.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="bc4e1-262">Boyut, ana bilgisayar sayısı ve Orchestrator Araçları-kapsayıcı hizmeti, diğer her şeyi de gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="bc4e1-263">Kubernetes sayesinde, geliştiriciler fiziksel ve sanal makineler hakkında düşünmekten ilerlemeye devam edebilir ve diğer kullanıcıların yanı sıra aşağıdaki özellikleri kolaylaştıran kapsayıcı merkezli bir altyapı planlıyor:</span><span class="sxs-lookup"><span data-stu-id="bc4e1-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="bc4e1-264">Birden çok kapsayıcıyı temel alan uygulamalar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="bc4e1-265">Kapsayıcı örnekleri ve yatay otomatik ölçeklendirmeyi çoğaltma</span><span class="sxs-lookup"><span data-stu-id="bc4e1-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="bc4e1-266">Adlandırma ve bulma (örneğin, iç DNS)</span><span class="sxs-lookup"><span data-stu-id="bc4e1-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="bc4e1-267">Yük Dengelemesi</span><span class="sxs-lookup"><span data-stu-id="bc4e1-267">Balancing loads</span></span>

- <span data-ttu-id="bc4e1-268">Güncelleştirmeler alınıyor</span><span class="sxs-lookup"><span data-stu-id="bc4e1-268">Rolling updates</span></span>

- <span data-ttu-id="bc4e1-269">Gizli dizileri dağıtma</span><span class="sxs-lookup"><span data-stu-id="bc4e1-269">Distributing secrets</span></span>

- <span data-ttu-id="bc4e1-270">Uygulama durumu denetimleri</span><span class="sxs-lookup"><span data-stu-id="bc4e1-270">Application health checks</span></span>

### <a name="next-steps"></a><span data-ttu-id="bc4e1-271">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-271">Next steps</span></span>

<span data-ttu-id="bc4e1-272">GitHub wiki üzerinde bu içeriği daha ayrıntılı bir şekilde gezin: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="bc4e1-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="bc4e1-273">İzlenecek yol 6: Windows kapsayıcıları tabanlı uygulamalarınızı kapsayıcılar için Azure App Service dağıtma</span><span class="sxs-lookup"><span data-stu-id="bc4e1-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="bc4e1-274">Teknik izlenecek yol kullanılabilirliği</span><span class="sxs-lookup"><span data-stu-id="bc4e1-274">Technical walkthrough availability</span></span>

<span data-ttu-id="bc4e1-275">Tam teknik izlenecek yol, GitHub deposu wiki ' de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="bc4e1-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="bc4e1-276">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc4e1-276">Overview</span></span>

<span data-ttu-id="bc4e1-277">Windows kapsayıcıları kullanılarak basit kapsayıcılı bir uygulama, kapsayıcılar için Azure App Service kolayca dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="bc4e1-278">Bu yaklaşım, çoğu Windows kapsayıcı tabanlı uygulama için önerilen yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-278">This approach is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="bc4e1-279">Hedefler</span><span class="sxs-lookup"><span data-stu-id="bc4e1-279">Goals</span></span>

<span data-ttu-id="bc4e1-280">Bu izlenecek yol, bir kayıt defterinden (Docker Hub veya Azure Container Registry) kapsayıcılar için Azure App Service Windows kapsayıcı tabanlı bir uygulamanın nasıl dağıtılacağını öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="bc4e1-281">Senaryo</span><span class="sxs-lookup"><span data-stu-id="bc4e1-281">Scenario</span></span>

![Kapsayıcılar için Windows kapsayıcı tabanlı uygulamayı Azure App Service dağıtma](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="bc4e1-283">Avantajlar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-283">Benefits</span></span>

<span data-ttu-id="bc4e1-284">Kapsayıcılar için Azure App Service dağıtım, Azure App Service PaaS avantajları ile eşleştirilmiş kapsayıcıların avantajlarını sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="bc4e1-285">App Service kolayca dikey ve yatay olarak ölçeklendirilebilir ve değişen talepleri karşılamak üzere otomatik olarak ölçeklendirilebilen şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="bc4e1-286">Güncelleştirmeler sıfır kapalı kalma süresiyle gerçekleştirilebilir ve bir kayıt defterinden sürekli dağıtım yapılandırması da kolayca yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="bc4e1-286">Updates can be performed with zero downtime and the configuration of continuous deployment from a registry is easily configured as well.</span></span>

### <a name="next-steps"></a><span data-ttu-id="bc4e1-287">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="bc4e1-287">Next steps</span></span>

<span data-ttu-id="bc4e1-288">GitHub wiki üzerinde bu içeriği daha ayrıntılı bir şekilde gezin: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="bc4e1-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="bc4e1-289">[Önceki](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md) 
>  [Sonraki](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="bc4e1-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
