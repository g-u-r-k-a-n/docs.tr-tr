---
title: .NET Core Kılavuzu
description: .NET Core, Windows, Linux ve Mac uygulamaları oluşturmaya yönelik modüler ve yüksek performanslı bir uygulamasıdır. Başlamak için .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: b2622dba53d64c9dcf58e852d57de117fe79eb2e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837018"
---
# <a name="net-core-guide"></a><span data-ttu-id="57b31-104">.NET Core Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="57b31-104">.NET Core Guide</span></span>

<span data-ttu-id="57b31-105">[.NET Core](about.md) , [GitHub](https://github.com/dotnet/core)'da Microsoft ve .net Community tarafından sürdürülen [Açık kaynaklı](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), genel amaçlı bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="57b31-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="57b31-106">Platformlar arası bir platformdur (Windows, macOS ve Linux 'u destekleme) ve cihaz, bulut ve IoT uygulamaları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57b31-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="57b31-107">.NET Core hakkında özellikler, desteklenen diller ve çerçeveler ve anahtar API 'Leri dahil olmak üzere .NET Core hakkında daha fazla bilgi için bkz. [.NET Core hakkında](about.md) .</span><span class="sxs-lookup"><span data-stu-id="57b31-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="57b31-108">[.NET Core öğreticilerine](tutorials/index.md) göz atın ve basit bir .NET Core uygulaması oluşturma hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="57b31-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="57b31-109">İlk uygulamanızı çalışır duruma getirmek için yalnızca birkaç dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="57b31-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="57b31-110">Tarayıcınızda .NET Core 'u denemek istiyorsanız çevrimiçi öğreticideki [numaralara C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) bakın.</span><span class="sxs-lookup"><span data-stu-id="57b31-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="57b31-111">.NET Core indirin</span><span class="sxs-lookup"><span data-stu-id="57b31-111">Download .NET Core</span></span>

<span data-ttu-id="57b31-112">Windows, macOS veya Linux makinenizde .NET Core 'u denemek için [.NET Core SDK](https://www.microsoft.com/net/download) indirin.</span><span class="sxs-lookup"><span data-stu-id="57b31-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="57b31-113">Docker Kapsayıcıları kullanmayı tercih ediyorsanız, [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/)' ı ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="57b31-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="57b31-114">Başka bir .NET Core sürümü arıyorsanız, tüm .NET Core sürümleri [.NET Core İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core) ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="57b31-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="57b31-115">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="57b31-115">.NET Core 3.1</span></span>

<span data-ttu-id="57b31-116">En son sürüm .NET Core 3,1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="57b31-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="57b31-117">.NET Core 3,0 üzerinde küçük iyileştirmeler içerir.</span><span class="sxs-lookup"><span data-stu-id="57b31-117">Which includes minor improvements over .NET Core 3.0.</span></span> <span data-ttu-id="57b31-118">Ancak .NET Core 3,1, uzun süreli desteklenen bir sürümdür.</span><span class="sxs-lookup"><span data-stu-id="57b31-118">However, .NET Core 3.1 is a long-term supported release.</span></span> <span data-ttu-id="57b31-119">.NET Core 3,1 sürümü hakkında daha fazla bilgi için bkz. [.net core 3,1 ' deki](./whats-new/dotnet-core-3-1.md)yenilikler.</span><span class="sxs-lookup"><span data-stu-id="57b31-119">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="57b31-120">İlk uygulamanızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="57b31-120">Create your first application</span></span>

<span data-ttu-id="57b31-121">.NET Core SDK yükledikten sonra bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="57b31-121">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="57b31-122">Bir C# uygulama oluşturmak ve çalıştırmak için aşağıdaki `dotnet` komutlarını yazın:</span><span class="sxs-lookup"><span data-stu-id="57b31-122">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="57b31-123">Aşağıdaki çıkışı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="57b31-123">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="57b31-124">Destek</span><span class="sxs-lookup"><span data-stu-id="57b31-124">Support</span></span>

<span data-ttu-id="57b31-125">.NET Core, [Microsoft](https://dotnet.microsoft.com/platform/support/policy), Windows, MacOS ve Linux 'ta desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="57b31-125">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="57b31-126">Genellikle ayda bir yılda birkaç kez güvenlik ve kalite için güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="57b31-126">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="57b31-127">.NET Core ikili dağıtımları, Azure 'da Microsoft tarafından korunan sunucularda oluşturulup test edilir ve tıpkı tüm Microsoft ürünleri gibi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="57b31-127">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="57b31-128">[Red Hat](http://redhatloves.net/) Red Hat Enterprise Linux (RHEL) üzerinde .NET Core 'u destekler.</span><span class="sxs-lookup"><span data-stu-id="57b31-128">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="57b31-129">Red hat, kaynaktan .NET Core 'u oluşturur ve [Red Hat yazılım koleksiyonlarında](https://developers.redhat.com/products/softwarecollections/overview/)kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="57b31-129">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="57b31-130">Red Hat ve Microsoft, .NET Core 'un RHEL üzerinde iyi çalıştığından emin olmak için işbirliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="57b31-130">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
