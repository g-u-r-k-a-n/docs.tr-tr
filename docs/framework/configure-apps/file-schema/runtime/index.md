---
description: Çalışma zamanı ayarları şeması hakkında daha fazla bilgi edinin
title: Çalışma Zamanı Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- schema runtime settings
- configuration schema [.NET Framework], runtime settings
- runtime settings schema
ms.assetid: f04816ab-110d-4e28-9283-845d6d9a4a68
ms.openlocfilehash: ee9c209866eb8c505130327d78a18482f5a282e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726136"
---
# <a name="run-time-settings-schema"></a><span data-ttu-id="6f4a0-103">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="6f4a0-103">Run-time settings schema</span></span>

<span data-ttu-id="6f4a0-104">Çalışma zamanı ayarları, .NET Framework hedefleyen uygulamaları yapılandırmak için ortak dil çalışma zamanı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-104">Run-time settings are used by the common language runtime to configure applications that target the .NET Framework.</span></span>

## <a name="the-runtime-section-and-its-parent-and-child-elements"></a><span data-ttu-id="6f4a0-105">\<runtime>Bölüm ve üst ve alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6f4a0-105">The \<runtime> section and its parent and child elements</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerType>](appdomainmanagertype-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyBinding>](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<dependentAssembly>](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyIdentity>](assemblyidentity-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<bindingRedirect>](bindingredirect-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<codeBase>](codebase-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<publisherPolicy>](publisherpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<probing>](probing-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<qualifyAssembly>](qualifyassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<supportPortability>](supportportability-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<developmentMode>](developmentmode-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<etwEnable>](etwenable-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcConcurrent>](gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCCpuGroup>](gccpugroup-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCHeapCount>](gcheapcount-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCLOHThreshold>](gclohthreshold-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCNoAffinitize>](gcnoaffinitize-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcServer>](gcserver-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<generatePublisherEvidence>](generatepublisherevidence-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<loadfromRemoteSources>](loadfromremotesources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<relativeBindForResources>](relativebindforresources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<TimeSpan_LegacyFormatMode>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<useLegacyJit>](uselegacyjit-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)\
&nbsp;&nbsp;[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<memoryCache>](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<namedCaches>](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<add>](add-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clear>](clear-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<remove>](remove-element-for-namedcaches.md)

## <a name="alphabetical-list-of-runtime-elements"></a><span data-ttu-id="6f4a0-106">Öğelerin alfabetik listesi \<runtime></span><span class="sxs-lookup"><span data-stu-id="6f4a0-106">Alphabetical list of \<runtime> elements</span></span>

|<span data-ttu-id="6f4a0-107">Öğe</span><span class="sxs-lookup"><span data-stu-id="6f4a0-107">Element</span></span>|<span data-ttu-id="6f4a0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f4a0-108">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="6f4a0-109">`namedCaches`Bir bellek önbelleği için koleksiyona adlandırılmış bir önbellek ekler.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-109">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|<span data-ttu-id="6f4a0-110">Kimliğe bürünme işlemi ne olursa olsun, Windows kimliğinin her zaman zaman uyumsuz noktalarda akacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-110">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|<span data-ttu-id="6f4a0-111"><xref:System.AppContext>Yeni işlevlere yönelik bir geri alma mekanizması sağlamak için sınıfı tarafından kullanılan bir veya daha fazla anahtarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-111">Defines one or more switches used by the <xref:System.AppContext> class to provide an opt-out mechanism for new functionality.</span></span>|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|<span data-ttu-id="6f4a0-112">İşlemdeki varsayılan uygulama etki alanı için uygulama etki alanı yöneticisini sağlayan derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-112">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|<span data-ttu-id="6f4a0-113">Varsayılan uygulama etki alanı için uygulama etki alanı yöneticisi olarak hizmet veren türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-113">Specifies the type that serves as the application domain manager for the default application domain.</span></span>|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|<span data-ttu-id="6f4a0-114">Çalışma zamanına, işlemin ömrü boyunca işlemdeki tüm uygulama etki alanlarında istatistikler toplamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-114">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|<span data-ttu-id="6f4a0-115">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-115">Contains information about assembly version redirection and the locations of assemblies.</span></span>|
|[\<assemblyIdentity>](assemblyidentity-element-for-runtime.md)|<span data-ttu-id="6f4a0-116">Bir derlemeyle ilgili tanımlama bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-116">Contains identifying information about an assembly.</span></span>|
|[\<bindingRedirect>](bindingredirect-element.md)|<span data-ttu-id="6f4a0-117">Bir derleme sürümünü diğerine yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-117">Redirects one assembly version to another.</span></span>|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|<span data-ttu-id="6f4a0-118">Güvenilen derlemeler için tanımlayıcı ad doğrulamasının atlanıp atlanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-118">Specifies whether strong name verification for trusted assemblies should be bypassed.</span></span>|
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="6f4a0-119">`namedCaches`Bir bellek önbelleğinin koleksiyonunu temizler.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-119">Clears the `namedCaches` collection for a memory cache.</span></span>|
|[\<codeBase>](codebase-element.md)|<span data-ttu-id="6f4a0-120">Çalışma zamanının bir derlemeyi bulabilecekleri yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-120">Specifies where the runtime can find an assembly.</span></span>|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|<span data-ttu-id="6f4a0-121">Çalışma zamanının, dize karşılaştırmaları gerçekleştirirken eski sıralama davranışını kullanması gerektiğini belirtir</span><span class="sxs-lookup"><span data-stu-id="6f4a0-121">Specifies that the runtime should use legacy sorting behavior when performing string comparisons</span></span>|
|[\<dependentAssembly>](dependentassembly-element.md)|<span data-ttu-id="6f4a0-122">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-122">Encapsulates binding policy and assembly location for each assembly.</span></span>|
|[\<developmentMode>](developmentmode-element.md)|<span data-ttu-id="6f4a0-123">Çalışma zamanının DEVPATH ortam değişkeni tarafından belirtilen dizinlerde derlemeleri arayıp aramayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-123">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|<span data-ttu-id="6f4a0-124">.NET Framework 2,0 ' de varsayılan davranış olan bağlama hatalarının önbelleğe alınmasının devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-124">Specifies whether the caching of binding failures, which is the default behavior in the .NET Framework 2.0, is disabled.</span></span>|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|<span data-ttu-id="6f4a0-125">Bir iş parçacığı başlatıldığında tam iş parçacığı yığınının uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-125">Specifies whether the full thread stack is committed when a thread starts.</span></span>|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|<span data-ttu-id="6f4a0-126">Çalışma zamanı konağının bir uygulama etki alanı için yapılandırma ayarlarını geçersiz kılmasına izin vermek üzere varsayılan davranışın devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-126">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|<span data-ttu-id="6f4a0-127">Tarih ve saat ayrıştırma yöntemlerinin, yalnızca bir gün, ay, saat ve i/PM göstergesini içeren Tarih dizelerini ayrıştırmak için ayarlanmış bir kural kümesi kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-127">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|<span data-ttu-id="6f4a0-128">Şifreleme algoritmalarının Federal bilgi Işleme standartları (FIPS) ile uyumlu olması gereken bir bilgisayar yapılandırma gereksinimini zorlayamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-128">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>|
|[\<etwEnable>](etwenable-element.md)|<span data-ttu-id="6f4a0-129">Ortak dil çalışma zamanı olayları için Windows için olay izlemenin (ETW) etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-129">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|<span data-ttu-id="6f4a0-130">PerfCounter.dll, performans sayacı verilerinin kategoriye özgü paylaşılan bellekten mı yoksa genel bellekten mi yükleneceğini öğrenmek için, .NET Framework sürüm 1,1 uygulamasında CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-130">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|<span data-ttu-id="6f4a0-131">64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-131">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>|
|[\<gcConcurrent>](gcconcurrent-element.md)|<span data-ttu-id="6f4a0-132">Çalışma zamanının çöp toplamayı eşzamanlı olarak çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-132">Specifies whether the runtime runs garbage collection concurrently.</span></span>|
|[\<GCCpuGroup>](gccpugroup-element.md)|<span data-ttu-id="6f4a0-133">Çöp toplamanın birden çok CPU grubunu destekleyip desteklemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-133">Specifies whether garbage collection supports multiple CPU groups.</span></span>|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|<span data-ttu-id="6f4a0-134">GC yığınlarını ve bireysel işlemcileri arasındaki benzeşimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-134">Defines the affinity between GC heaps and individual processors.</span></span>|
|[\<GCHeapCount>](gcheapcount-element.md)|<span data-ttu-id="6f4a0-135">Sunucu atık toplama için kullanılacak Heap/iş parçacığı sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-135">Specifies the number of heaps/threads to use for server garbage collection.</span></span>  |
|[\<GCLOHThreshold>](gclohthreshold-element.md)|<span data-ttu-id="6f4a0-136">Nesnelerin büyük nesne yığınında (LOH) geçmesine neden olan eşik boyutunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-136">Specifies the threshold size that causes objects to go on the large object heap (LOH).</span></span>|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|<span data-ttu-id="6f4a0-137">Sunucu GC iş parçacıklarının CPU 'Lara yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-137">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>|
|[\<gcServer>](gcserver-element.md)|<span data-ttu-id="6f4a0-138">Ortak dil çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-138">Specifies whether the common language runtime runs server garbage collection.</span></span>|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|<span data-ttu-id="6f4a0-139">Çalışma zamanının kod erişim güvenliği (CAS) Yayımcı ilkesini kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-139">Specifies whether the runtime uses code access security (CAS) publisher policy.</span></span>|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|<span data-ttu-id="6f4a0-140">Çalışma zamanının yönetilen kodun erişim ihlallerini ve diğer bozuk durum özel durumlarını yakalayıp belirlemesine izin verip içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-140">Specifies whether the runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|<span data-ttu-id="6f4a0-141">Geçerli iş parçacığında yürütme bağlamı için akış ayarlarından bağımsız olarak, Windows kimliğinin zaman uyumsuz noktalarda akış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-141">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|<span data-ttu-id="6f4a0-142">Uzak kaynaklardaki derlemelerin tam güven olarak yüklenip yüklenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-142">Specifies whether assemblies from remote sources are loaded as full trust.</span></span>|
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="6f4a0-143">Sınıfına dayalı bir önbelleği yapılandırmak için kullanılan bir öğesi tanımlar <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="6f4a0-143">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="6f4a0-144">Örnek için yapılandırma ayarlarının bir koleksiyonunu içerir `namedCache` .</span><span class="sxs-lookup"><span data-stu-id="6f4a0-144">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|<span data-ttu-id="6f4a0-145">Çalışma zamanının eski kod erişim güvenliği (CAS) ilkesi kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-145">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|<span data-ttu-id="6f4a0-146">Çalışma zamanının, yönetilen ve yönetilmeyen kod arasındaki yavaş geçişlerin maliyetinde, çalışma zamanında hatalı platform çağırma bildirimlerini otomatik olarak düzeltilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-146">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|<span data-ttu-id="6f4a0-147">Çalışma zamanının, yöntemin karma kodlarını hesaplamak için sabit miktarda bellek kullanıp kullanmadığını belirtir <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6f4a0-147">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>|
|[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)|<span data-ttu-id="6f4a0-148">Çalışma zamanının, uygulama etki alanı sınırları arasında uzaktan iletişim yerine COM birlikte çalışabilirliğine sahip olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-148">Specifies that the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|
|[\<probing>](probing-element.md)|<span data-ttu-id="6f4a0-149">Derlemeler yüklenirken çalışma zamanının aradığı alt dizinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-149">Specifies subdirectories that the runtime searches when loading assemblies.</span></span>|
|[\<publisherPolicy>](publisherpolicy-element.md)|<span data-ttu-id="6f4a0-150">Çalışma zamanının yayımcı ilkesi uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-150">Specifies whether the runtime applies publisher policy.</span></span>|
|[\<qualifyAssembly>](qualifyassembly-element.md)|<span data-ttu-id="6f4a0-151">Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-151">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|
|[\<relativeBindForResources>](relativebindforresources-element.md)|<span data-ttu-id="6f4a0-152">Uydu derlemeleri için araştırmayı iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-152">Optimizes the probe for satellite assemblies.</span></span>|
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="6f4a0-153">`namedCaches`Bir bellek önbelleği için koleksiyondan adlandırılmış bir önbellek girdisini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-153">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|
|[\<runtime>](runtime-element.md)|<span data-ttu-id="6f4a0-154">Derleme bağlaması ve çöp toplamanın davranışı hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-154">Contains information about assembly binding and the behavior of garbage collection.</span></span>|
|[\<shadowCopyTimeStampVerification>](shadowcopyverifybytimestamp-element.md)|<span data-ttu-id="6f4a0-155">Gölge kopyalamanın .NET Framework 4 ' te tanıtılan varsayılan başlangıç davranışını kullanıp kullanmadığını veya .NET Framework önceki sürümlerinin başlangıç davranışına geri dönmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-155">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>|
|[\<supportPortability>](supportportability-element.md)|<span data-ttu-id="6f4a0-156">Bir uygulamanın, uygulama taşınabilirlik amaçları doğrultusunda derlemeleri eşdeğer olarak ele alan varsayılan davranışı devre dışı bırakarak, .NET Framework iki farklı uygulamasındaki aynı derlemeye başvurabildiklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-156">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="6f4a0-157">Varsayılan bellek içi nesne önbelleğinde yapılandırma bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-157">Provides configuration information for the default in-memory object cache.</span></span>|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|<span data-ttu-id="6f4a0-158">Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-158">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|<span data-ttu-id="6f4a0-159">İşlenmemiş görev özel durumlarının çalışan bir işlemi sonlandırmayı gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-159">Specifies whether unhandled task exceptions should terminate a running process.</span></span>|
|[\<TimeSpan_LegacyFormatMode>](runtime-element.md)|<span data-ttu-id="6f4a0-160">Çalışma zamanının değerler için eski biçimlendirmeyi kullanıp kullanmadığını belirtir <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="6f4a0-160">Specifies whether the runtime uses legacy formatting for <xref:System.TimeSpan> values.</span></span>|
|[\<useLegacyJit>](uselegacyjit-element.md)|<span data-ttu-id="6f4a0-161">Ortak dil çalışma zamanının, Just-In-Time derlemesi için eski 64-bit JıT derleyicisini kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-161">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|<span data-ttu-id="6f4a0-162">Çalışma zamanının, her uygulama etki alanı temelinde dizeler için karma kodları hesaplayıp hesaplamadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-162">Specifies whether the runtime calculates hash codes for strings on a per application domain basis.</span></span>|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|<span data-ttu-id="6f4a0-163">Çalışma zamanının, varsayılan yığın boyutu yerine dahili olarak kullandığı belirli iş parçacıklarını oluştururken açık yığın boyutlarını kullanmasını ister.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-163">Requests that the runtime use explicit stack sizes when it creates certain threads that it uses internally, instead of the default stack size.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6f4a0-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f4a0-164">See also</span></span>

- [<span data-ttu-id="6f4a0-165">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="6f4a0-165">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6f4a0-166">Eşzamanlı atık toplamayı devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="6f4a0-166">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="6f4a0-167">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="6f4a0-167">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
