---
description: 'Daha fazla bilgi edinin: <applicationPool> öğesi (Web ayarları)'
title: <applicationPool> Öğesi (Web Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: e70b804fbad506f98d5356828843208e5ef9e515
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682000"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="fc49a-103">\<applicationPool> Öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="fc49a-103">\<applicationPool> Element (Web Settings)</span></span>

<span data-ttu-id="fc49a-104">Bir ASP.NET uygulaması IIS 7,0 veya sonraki bir sürümde tümleşik modda çalışırken, işlem genelinde davranışı yönetmek için ASP.NET tarafından kullanılan yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc49a-104">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc49a-105">Bu öğe ve özellik yalnızca ASP.NET uygulamanız IIS 7,0 veya sonraki sürümlerde barındırılıyorsa çalışmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="fc49a-105">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**  
  
## <a name="syntax"></a><span data-ttu-id="fc49a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fc49a-106">Syntax</span></span>  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc49a-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc49a-107">Attributes and Elements</span></span>  

<span data-ttu-id="fc49a-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc49a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc49a-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fc49a-109">Attributes</span></span>  
  
|<span data-ttu-id="fc49a-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fc49a-110">Attribute</span></span>|<span data-ttu-id="fc49a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc49a-111">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="fc49a-112">CPU başına kaç tane eş zamanlı istek ASP.NET izin verdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc49a-112">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="fc49a-113">Her CPU için bir uygulama havuzu için kaç tane eş zamanlı iş parçacığının çalıştığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc49a-113">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="fc49a-114">Bu, isteklere hizmeti sağlamak için CPU başına kullanılabilecek yönetilen iş parçacıklarının sayısını sınırlayabilmeniz için ASP.NET eşzamanlılık denetiminin alternatif bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc49a-114">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="fc49a-115">Varsayılan olarak, bu ayar 0 ' dır, yani CLR iş parçacığı havuzu oluşturulabilen iş parçacığı sayısını da sınırladığından, bu ayar, ASP.NET CPU başına oluşturulabilen iş parçacığı sayısını sınırlamaz.</span><span class="sxs-lookup"><span data-stu-id="fc49a-115">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="fc49a-116">Tek bir işlemde ASP.NET için sıraya alınabilen en fazla istek sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fc49a-116">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="fc49a-117">İki veya daha fazla ASP.NET uygulaması tek bir uygulama havuzunda çalıştığında, uygulama havuzundaki herhangi bir uygulamaya yapılan toplam istek kümesi bu ayara tabidir.</span><span class="sxs-lookup"><span data-stu-id="fc49a-117">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc49a-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc49a-118">Child Elements</span></span>  

 <span data-ttu-id="fc49a-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="fc49a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc49a-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc49a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fc49a-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="fc49a-121">Element</span></span>|<span data-ttu-id="fc49a-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc49a-122">Description</span></span>|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|<span data-ttu-id="fc49a-123">ASP.NET 'in bir konak uygulamasıyla nasıl etkileşime girdiği hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fc49a-123">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc49a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc49a-124">Remarks</span></span>  

<span data-ttu-id="fc49a-125">IIS 7,0 veya sonraki bir sürümü tümleşik modda çalıştırdığınızda, bu öğe birleşimi, uygulamanın bir IIS uygulama havuzunda barındırıldığı zaman iş parçacıklarını ve sıra isteklerini nasıl yönettiğini ASP.NET yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fc49a-125">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="fc49a-126">IIS 6 veya IIS 7,0 'yi Klasik modda veya ISAPI modunda çalıştırırsanız, bu ayarlar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="fc49a-126">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
<span data-ttu-id="fc49a-127">`applicationPool`Ayarlar .NET Framework belirli bir sürümünde çalışan tüm uygulama havuzları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fc49a-127">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="fc49a-128">Ayarlar bir aspnet.config dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="fc49a-128">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="fc49a-129">.NET Framework 2,0 ve 4,0 sürümleri için bu dosyanın bir sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="fc49a-129">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="fc49a-130">(.NET Framework 3,0 sürümleri ve 3,5 sürümü aspnet.config dosyayı sürüm 2,0 ile paylaşır.)</span><span class="sxs-lookup"><span data-stu-id="fc49a-130">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc49a-131">IIS 7,0 'yi Windows 7 üzerinde çalıştırırsanız, her uygulama havuzu için ayrı bir aspnet.config dosyası yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc49a-131">If you run IIS 7.0 on Windows 7, you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="fc49a-132">Bu, her uygulama havuzu için iş parçacıklarının performansını uyarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc49a-132">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
<span data-ttu-id="fc49a-133">Bu `maxConcurrentRequestsPerCPU` ayar için, "5000 .NET Framework" varsayılan ayarı, ASP.NET tarafından denetlenen istek azaltmasını etkin bir şekilde devre dışı bırakır, ancak CPU başına 5000 veya daha fazla istek olmadığı müddetçe.</span><span class="sxs-lookup"><span data-stu-id="fc49a-133">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="fc49a-134">Varsayılan ayar, CLR iş parçacığı havuzuna CPU başına otomatik olarak yönetilecek şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="fc49a-134">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="fc49a-135">Zaman uyumsuz istek işlemenin çok fazla kullanımını veya ağ g/ç 'de engellenen çok uzun süreli istekleri olan uygulamalar, .NET Framework 4 ' te artan varsayılan sınırdan faydalanır.</span><span class="sxs-lookup"><span data-stu-id="fc49a-135">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="fc49a-136">Sıfıra ayarlandığında, `maxConcurrentRequestsPerCPU` ASP.net isteklerini işlemek için yönetilen iş parçacıklarının kullanımını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="fc49a-136">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="fc49a-137">Bir uygulama bir IIS uygulama havuzunda çalıştığında, istekler IIS g/ç iş parçacığında kalır ve bu nedenle eşzamanlılık IIS iş parçacığı ayarları tarafından kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="fc49a-137">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
<span data-ttu-id="fc49a-138">`requestQueueLimit`Ayar, `requestQueueLimit` ASP.NET uygulamaları için Web.config dosyalarında ayarlanan [processModel](/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) öğesinin özniteliğiyle aynı şekilde çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="fc49a-138">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="fc49a-139">Ancak, `requestQueueLimit` bir aspnet.config dosyadaki ayar, `requestQueueLimit` Web.config bir dosyadaki ayarı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="fc49a-139">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="fc49a-140">Diğer bir deyişle, her iki öznitelik de ayarlanırsa (varsayılan olarak, bu true ise) `requestQueueLimit` aspnet.config dosyadaki ayar önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="fc49a-140">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc49a-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc49a-141">Example</span></span>  

<span data-ttu-id="fc49a-142">Aşağıdaki örnekte, aşağıdaki durumlarda aspnet.config dosyasında ASP.NET işlem genelinde davranışın nasıl yapılandırılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="fc49a-142">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="fc49a-143">Uygulama bir IIS 7,0 uygulama havuzunda barındırılır.</span><span class="sxs-lookup"><span data-stu-id="fc49a-143">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="fc49a-144">IIS 7,0, tümleşik modda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="fc49a-144">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="fc49a-145">Uygulama .NET Framework 3,5 SP1 veya sonraki bir sürümünü kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="fc49a-145">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
<span data-ttu-id="fc49a-146">Örnekteki değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="fc49a-146">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="fc49a-147">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="fc49a-147">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fc49a-148">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="fc49a-148">Namespace</span></span>||  
|<span data-ttu-id="fc49a-149">Şema adı</span><span class="sxs-lookup"><span data-stu-id="fc49a-149">Schema Name</span></span>||  
|<span data-ttu-id="fc49a-150">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="fc49a-150">Validation File</span></span>||  
|<span data-ttu-id="fc49a-151">Boş olabilir</span><span class="sxs-lookup"><span data-stu-id="fc49a-151">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="fc49a-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc49a-152">See also</span></span>

- [<span data-ttu-id="fc49a-153">\<system.web> Öğesi (Web ayarları)</span><span class="sxs-lookup"><span data-stu-id="fc49a-153">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)
