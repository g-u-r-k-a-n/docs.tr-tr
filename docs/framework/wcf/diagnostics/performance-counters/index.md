---
description: 'Daha fazla bilgi edinin: WCF performans sayaçları'
title: WCF Performans Sayaçları
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: c6572ece289fb550dd4974a8f8e957f7d3ef51b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655350"
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="e19dd-103">WCF Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="e19dd-103">WCF Performance Counters</span></span>

<span data-ttu-id="e19dd-104">Windows Communication Foundation (WCF), uygulamanızın performansını ölçgetirmenize yardımcı olacak büyük bir performans sayacı kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-104">Windows Communication Foundation (WCF) includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="e19dd-105">Performans sayaçlarını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e19dd-105">Enabling Performance Counters</span></span>  

 <span data-ttu-id="e19dd-106">WCF hizmetinin app.config yapılandırma dosyası aracılığıyla bir WCF hizmeti için performans sayaçlarını aşağıdaki şekilde etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e19dd-106">You can enable performance counters for a WCF service through the app.config configuration file of the WCF service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e19dd-107">`performanceCounters`Özniteliği, belirli bir performans sayacı türünü etkinleştirecek şekilde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-107">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="e19dd-108">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="e19dd-108">Valid values are</span></span>  
  
- <span data-ttu-id="e19dd-109">All: tüm kategori sayaçları (ServiceModelService, ServiceModelEndpoint ve ServiceModelOperation) etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-109">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
- <span data-ttu-id="e19dd-110">ServiceOnly: yalnızca ServiceModelService kategori sayaçları etkindir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-110">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="e19dd-111">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="e19dd-111">This is the default value.</span></span>  
  
- <span data-ttu-id="e19dd-112">Kapalı: ServiceModel \* performans sayaçları devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e19dd-112">Off: ServiceModel\* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="e19dd-113">Tüm WCF uygulamaları için performans sayaçlarını etkinleştirmek istiyorsanız, yapılandırma ayarlarını Machine.config dosyasına yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e19dd-113">If you want to enable performance counters for all WCF applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="e19dd-114">Makinenizde performans sayaçları için yeterli bellek yapılandırma hakkında daha fazla bilgi için lütfen aşağıdaki **performans sayaçları Için bellek boyutunu artırma** bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e19dd-114">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="e19dd-115">Özel işlem invokers gibi WCF genişletilebilirlik noktalarını kullanırsanız, kendi performans Sayaçlarınızı da yaymalısınız.</span><span class="sxs-lookup"><span data-stu-id="e19dd-115">If you use WCF extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="e19dd-116">Bunun nedeni, bir genişletilebilirlik noktası uyguladığınızda WCF 'nin varsayılan yoldaki standart performans sayacı verilerini artık yaymayabilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-116">This is because if you implement an extensibility point, WCF may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="e19dd-117">El ile performans sayacı desteğini uygulamadıysanız, beklediğinizi performans sayacı verilerini göremeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e19dd-117">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="e19dd-118">Ayrıca kodunuzda performans sayaçlarını aşağıdaki şekilde etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e19dd-118">You can also enable performance counters in your code as follows,</span></span>  
  
```csharp
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a><span data-ttu-id="e19dd-119">Performans verilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e19dd-119">Viewing Performance Data</span></span>  

 <span data-ttu-id="e19dd-120">Performans sayaçları tarafından yakalanan verileri görüntülemek için, Windows ile birlikte gelen performans Izleyicisini (Perfmon.exe) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e19dd-120">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="e19dd-121">**Başlat**' a gidip **Çalıştır** ' a tıklayıp iletişim kutusuna yazarak bu aracı başlatabilirsiniz `perfmon.exe` .</span><span class="sxs-lookup"><span data-stu-id="e19dd-121">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e19dd-122">Son iletiler bitiş noktası dağıtıcısı tarafından işlenmeden önce performans sayacı örnekleri serbest bırakılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-122">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="e19dd-123">Bu, performans verilerinin birkaç ileti için yakalanmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-123">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="e19dd-124">Performans sayaçları için bellek boyutunu artırma</span><span class="sxs-lookup"><span data-stu-id="e19dd-124">Increasing Memory Size for Performance Counters</span></span>  

 <span data-ttu-id="e19dd-125">WCF, performans sayacı kategorileri için ayrı paylaşılan bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="e19dd-125">WCF uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="e19dd-126">Varsayılan olarak, ayrı paylaşılan bellek, genel performans sayacı belleğinin boyutu için bir çeyreğe ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e19dd-126">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="e19dd-127">Varsayılan genel performans sayacı belleği 524.288 bayttır.</span><span class="sxs-lookup"><span data-stu-id="e19dd-127">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="e19dd-128">Bu nedenle, üç WCF performans sayacı kategorisinin her biri yaklaşık 128KB varsayılan boyutu vardır.</span><span class="sxs-lookup"><span data-stu-id="e19dd-128">Therefore, the three WCF performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="e19dd-129">Bir makinedeki WCF uygulamalarının çalışma zamanı özelliklerine bağlı olarak, performans sayacı belleği tükenebilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-129">Depending upon the runtime characteristics of the WCF applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="e19dd-130">Bu durumda, WCF uygulama olay günlüğüne bir hata yazar.</span><span class="sxs-lookup"><span data-stu-id="e19dd-130">When this happens, WCF writes an error to the application event log.</span></span> <span data-ttu-id="e19dd-131">Hatanın içeriği bir performans sayacının yüklenmediğini ve girişin "System. InvalidOperationException: özel sayaçlar dosya görünümü bellek dışında" özel durum içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-131">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="e19dd-132">İzleme hata düzeyinde etkinleştirilirse, bu hata da izleniyor.</span><span class="sxs-lookup"><span data-stu-id="e19dd-132">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="e19dd-133">Performans sayacı belleği tükenirse, WCF uygulamalarınızı performans sayaçlarıyla çalıştırmaya devam etmek performans düşüşüne neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-133">If performance counter memory is exhausted, continuing to run your WCF applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="e19dd-134">Makinenin yöneticisiyseniz, her zaman var olan en fazla performans sayacı sayısını destekleyecek şekilde yeterli bellek ayırabilecek şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-134">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="e19dd-135">Kayıt defterindeki WCF kategorilerinin performans sayacı bellek miktarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e19dd-135">You can change the amount of performance counter memory for WCF categories in the registry.</span></span> <span data-ttu-id="e19dd-136">Bunu yapmak için, aşağıdaki üç konuma adlı yeni bir DWORD değeri eklemeniz `FileMappingSize` ve bayt cinsinden istenen değere ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-136">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="e19dd-137">Bu değişikliklerin yürürlüğe alınması için makinenizi yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="e19dd-137">Reboot your machine so that these changes are taken into effect.</span></span>  
  
- <span data-ttu-id="e19dd-138">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0 \ performans</span><span class="sxs-lookup"><span data-stu-id="e19dd-138">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
- <span data-ttu-id="e19dd-139">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0 \ performans</span><span class="sxs-lookup"><span data-stu-id="e19dd-139">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
- <span data-ttu-id="e19dd-140">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0 \ performans</span><span class="sxs-lookup"><span data-stu-id="e19dd-140">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="e19dd-141">Çok sayıda nesne (örneğin, ServiceHost) atıldığında ancak çöp toplanmayı beklerken, `PrivateBytes` performans sayacı alışılmadık bir yüksek sayıyı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e19dd-141">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="e19dd-142">Bu sorunu çözmek için uygulamaya özel Sayaçlarınızı ekleyebilir ya da `performanceCounters` yalnızca hizmet düzeyi sayaçlarını etkinleştirmek için özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e19dd-142">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="e19dd-143">Performans sayacı türleri</span><span class="sxs-lookup"><span data-stu-id="e19dd-143">Types of Performance Counters</span></span>  

 <span data-ttu-id="e19dd-144">Performans sayaçları üç farklı düzeye sahiptir: hizmet, uç nokta ve Işlem.</span><span class="sxs-lookup"><span data-stu-id="e19dd-144">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="e19dd-145">Bir performans sayacı örneğinin adını almak için WMI ' y i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e19dd-145">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="e19dd-146">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="e19dd-146">For example,</span></span>  
  
- <span data-ttu-id="e19dd-147">Hizmet sayacı örnek adı, WMI [hizmeti](../wmi/service.md) örneğinin "CounterInstanceName" özelliği aracılığıyla alınabilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-147">Service counter instance name can be obtained through WMI [Service](../wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
- <span data-ttu-id="e19dd-148">Uç nokta sayacı örneği adı, WMI [uç noktası](../wmi/endpoint.md) örneğinin "CounterInstanceName" özelliği aracılığıyla alınabilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-148">Endpoint counter instance name can be obtained through WMI [Endpoint](../wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
- <span data-ttu-id="e19dd-149">İşlem sayacı örnek adı, WMI [uç noktası](../wmi/endpoint.md) örneğinin "GetOperationCounterInstanceName" yöntemiyle elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-149">Operation counter instance name can be obtained through WMI [Endpoint](../wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="e19dd-150">WMI hakkında daha fazla bilgi için bkz. [Tanılama için Windows Yönetim araçları kullanma](../wmi/index.md).</span><span class="sxs-lookup"><span data-stu-id="e19dd-150">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="e19dd-151">Hizmet performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="e19dd-151">Service performance counters</span></span>  

 <span data-ttu-id="e19dd-152">Hizmet performans sayaçları, hizmet davranışını bir bütün olarak ölçer ve tüm hizmetin performansını tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-152">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="e19dd-153">Performans `ServiceModelService 4.0.0.0` İzleyicisi ile görüntülenirken Performans nesnesi altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-153">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="e19dd-154">Örnekler aşağıdaki model kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="e19dd-154">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
 <span data-ttu-id="e19dd-155">Bir hizmet kapsamındaki sayaç, bir uç nokta koleksiyonundaki sayaçdan toplanır.</span><span class="sxs-lookup"><span data-stu-id="e19dd-155">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="e19dd-156">Yeni bir InstanceContext oluşturulduğunda hizmet örneği oluşturma için performans sayaçları artırılır.</span><span class="sxs-lookup"><span data-stu-id="e19dd-156">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="e19dd-157">Etkinleştirme dışı bir ileti (var olan bir hizmetle) aldığınızda ya da bir oturumdan bir örneğe bağlanıp oturumu sonlandırdığınızda ve sonra başka bir oturumdan yeniden bağlandığınızda bile yeni bir InstanceContext oluşturulduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e19dd-157">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="e19dd-158">Uç nokta performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="e19dd-158">Endpoint performance counters</span></span>  

 <span data-ttu-id="e19dd-159">Uç nokta performans sayaçları, bir uç noktanın iletileri nasıl kabul ettiğini yansıtan verileri gözden etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e19dd-159">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="e19dd-160">Performans `ServiceModelEndpoint 4.0.0.0` İzleyicisi kullanılarak görüntüleme sırasında performans nesnesi altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-160">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="e19dd-161">Örnekler aşağıdaki model kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="e19dd-161">The instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName)@(endpoint listener address)`
  
 <span data-ttu-id="e19dd-162">Veriler tek tek işlemler için toplanmaya benzerdir, ancak yalnızca uç nokta boyunca toplanır.</span><span class="sxs-lookup"><span data-stu-id="e19dd-162">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="e19dd-163">Bir uç nokta kapsamındaki sayaç, bir işlem koleksiyonundaki sayaçlardan toplanır.</span><span class="sxs-lookup"><span data-stu-id="e19dd-163">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e19dd-164">İki uç noktanın aynı sözleşme adları ve adresleri varsa, bunlar aynı sayaç örneğiyle eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-164">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="e19dd-165">İşlem performansı sayaçları</span><span class="sxs-lookup"><span data-stu-id="e19dd-165">Operation performance counters</span></span>  

 <span data-ttu-id="e19dd-166">Performans `ServiceModelOperation 4.0.0.0` İzleyicisi ile görüntülenirken Performans nesnesi altında işlem performansı sayaçları bulunur.</span><span class="sxs-lookup"><span data-stu-id="e19dd-166">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="e19dd-167">Her işlemin tek bir örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="e19dd-167">Each operation has an individual instance.</span></span> <span data-ttu-id="e19dd-168">Diğer bir deyişle, belirli bir sözleşmede 10 işlem varsa, bu sözleşmeyle ilişkili 10 işlem sayacı örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="e19dd-168">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="e19dd-169">Nesne örnekleri aşağıdaki model kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="e19dd-169">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="e19dd-170">Bu sayaç, çağrının nasıl kullanıldığını ve işlemin ne kadar iyi çalıştığını ölçmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e19dd-170">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="e19dd-171">Sayaçlar birden çok kapsamda görünür olduğunda, daha yüksek bir kapsamdan toplanan veriler, daha düşük kapsamlardan alınan verilerle toplanır.</span><span class="sxs-lookup"><span data-stu-id="e19dd-171">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="e19dd-172">Örneğin, `Calls` bir uç nokta içindeki tüm işlem çağrılarının toplamını temsil eder; `Calls` bir hizmette, hizmet içindeki tüm uç noktalara yapılan çağrıların toplamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e19dd-172">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e19dd-173">Bir sözleşmede yinelenen işlem adları varsa, her iki işlem için yalnızca bir sayaç örneği alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e19dd-173">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="e19dd-174">WCF performans sayaçlarını programlama</span><span class="sxs-lookup"><span data-stu-id="e19dd-174">Programming the WCF Performance Counters</span></span>  

<span data-ttu-id="e19dd-175">WCF performans sayaçlarına programlı bir şekilde erişebilmeniz için SDK yükleme klasörüne birkaç dosya yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e19dd-175">Several files are installed in the SDK install folder so that you can access the WCF performance counters programmatically.</span></span> <span data-ttu-id="e19dd-176">Bu dosyalar aşağıdaki gibi listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="e19dd-176">These files are listed as follows:</span></span>
  
- <span data-ttu-id="e19dd-177">*\_ServiceModelEndpointPerfCounters. VRG*</span><span class="sxs-lookup"><span data-stu-id="e19dd-177">*\_ServiceModelEndpointPerfCounters.vrg*</span></span>
- <span data-ttu-id="e19dd-178">*\_ServiceModelOperationPerfCounters. VRG*</span><span class="sxs-lookup"><span data-stu-id="e19dd-178">*\_ServiceModelOperationPerfCounters.vrg*</span></span>
- <span data-ttu-id="e19dd-179">*\_ServiceModelServicePerfCounters. VRG*</span><span class="sxs-lookup"><span data-stu-id="e19dd-179">*\_ServiceModelServicePerfCounters.vrg*</span></span>  
- <span data-ttu-id="e19dd-180">*\_SMSvcHostPerfCounters. VRG*</span><span class="sxs-lookup"><span data-stu-id="e19dd-180">*\_SMSvcHostPerfCounters.vrg*</span></span>
- <span data-ttu-id="e19dd-181">*\_Transactionköprüperfcounters. VRG*</span><span class="sxs-lookup"><span data-stu-id="e19dd-181">*\_TransactionBridgePerfCounters.vrg*</span></span>
  
<span data-ttu-id="e19dd-182">Sayaçlara programlı olarak erişme hakkında daha fazla bilgi için bkz. [performans sayacı programlama mimarisi](/previous-versions/visualstudio/visual-studio-2008/5f9bkxzf(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e19dd-182">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](/previous-versions/visualstudio/visual-studio-2008/5f9bkxzf(v=vs.90)).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e19dd-183">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e19dd-183">See also</span></span>

- [<span data-ttu-id="e19dd-184">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="e19dd-184">Administration and Diagnostics</span></span>](../index.md)
