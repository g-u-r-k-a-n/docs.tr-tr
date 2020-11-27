---
title: CLR ETW Sağlayıcılar
description: 'Windows için iki ortak dil çalışma zamanı (CLR) olay izleme (ETW) sağlayıcısı ile ilgili ayrıntıları gözden geçirin: runtimne sağlayıcı ve runaşağı sağlayıcı.'
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
ms.openlocfilehash: f537a2e0557f1b0434d1f303d74f9cd48f157edc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283883"
---
# <a name="clr-etw-providers"></a><span data-ttu-id="399e3-103">CLR ETW Sağlayıcılar</span><span class="sxs-lookup"><span data-stu-id="399e3-103">CLR ETW Providers</span></span>

<span data-ttu-id="399e3-104">Ortak dil çalışma zamanı (CLR) iki sağlayıcıya sahiptir: çalışma zamanı sağlayıcısı ve runaşağı sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="399e3-104">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="399e3-105">Çalışma zamanı sağlayıcısı, hangi anahtar sözcüklere (olay kategorileri) etkin olarak olaylar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="399e3-105">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="399e3-106">Örneğin, anahtar sözcüğünü etkinleştirerek yükleyici olaylarını toplayabilirsiniz `LoaderKeyword` .</span><span class="sxs-lookup"><span data-stu-id="399e3-106">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="399e3-107">Windows için olay Izleme (ETW) olayları, daha sonra gerektiğinde virgülle ayrılmış değer (. csv) dosyalarında işlenmek üzere bir. etl uzantısı olan bir dosyada günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="399e3-107">Event Tracing for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="399e3-108">. Etl dosyasını. csv dosyasına dönüştürme hakkında daha fazla bilgi için bkz. [.NET Framework günlüğünü denetleme](controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="399e3-108">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="399e3-109">Çalışma zamanı sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="399e3-109">The Runtime Provider</span></span>  

 <span data-ttu-id="399e3-110">Çalışma zamanı sağlayıcısı, ana CLR ETW sağlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="399e3-110">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="399e3-111">CLR çalışma zamanı sağlayıcısı GUID 'SI e13c0d23-CCBC-4e12-931B-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="399e3-111">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="399e3-112">CLR ETW olaylarını yaygın olarak kullanılabilen araçları kullanarak günlüğe kaydetme ve görüntüleme örnekleri için bkz. [.NET Framework günlüğünü denetleme](controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="399e3-112">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](controlling-logging.md).</span></span>  
  
 <span data-ttu-id="399e3-113">Gibi anahtar sözcüklerin kullanılmasına ek olarak `LoaderKeyword` , çok sık ortaya çıkarılan olayları günlüğe kaydetmek için anahtar kelimeleri etkinleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="399e3-113">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="399e3-114">`StartEnumerationKeyword`Ve `EndEnumerationKeyword` anahtar sözcükleri bu olayları etkinleştirir ve [CLR ETW anahtar sözcükleri ve düzeylerinde](clr-etw-keywords-and-levels.md)özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="399e3-114">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="399e3-115">Özet sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="399e3-115">The Rundown Provider</span></span>  

 <span data-ttu-id="399e3-116">Özet sağlayıcının belirli özel amaçlı kullanımlar için açık olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="399e3-116">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="399e3-117">Ancak, çoğu kullanıcı için çalışma zamanı sağlayıcısı yeterli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="399e3-117">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="399e3-118">CLR özeti sağlayıcısı GUID 'SI A669021C-C450-4609-A035-5AF59AF4DF18.</span><span class="sxs-lookup"><span data-stu-id="399e3-118">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="399e3-119">Normalde, bir işlem başlatılmadan önce ETW günlüğü etkinleştirilir ve işlem çıktıktan sonra günlüğe kaydetme kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="399e3-119">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="399e3-120">Ancak, işlem yürütülürken ETW günlüğü açıksa, işlem hakkında ek bilgiler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="399e3-120">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="399e3-121">Örneğin, sembol çözümlemesi için, günlük kaydı açılmadan önce zaten yüklenmiş olan yöntemler için yöntem olaylarını günlüğe yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="399e3-121">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="399e3-122">`DCStart`Ve `DCEnd` olayları, veri toplama başlatıldığında ve durdurulduğunda işlemin durumunu yakalar.</span><span class="sxs-lookup"><span data-stu-id="399e3-122">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="399e3-123">(Durum, zaten tam zamanında (JıT) derlenmiş Yöntemler ve yüklenmiş derlemeler dahil olmak üzere yüksek düzeyde bilgi anlamına gelir.) Bu iki olay, işlemde zaten ne olduğunu hakkında bilgi sağlayabilir; Örneğin, JıT olarak derlenen Yöntemler ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="399e3-123">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="399e3-124">Yalnızca,,, veya adlarında bulunan olaylar, Özet `DC` `DCStart` `DCEnd` `DCInit` sağlayıcının altında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="399e3-124">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="399e3-125">Ayrıca, bu olaylar yalnızca Özet sağlayıcının altında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="399e3-125">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="399e3-126">Olay anahtar sözcük filtrelerine ek olarak, runaşağı sağlayıcı `StartRundownKeyword` `EndRundownKeyword` hedeflenen filtreleme sağlamak için ve anahtar kelimelerini de destekler.</span><span class="sxs-lookup"><span data-stu-id="399e3-126">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="399e3-127">Özeti Başlat</span><span class="sxs-lookup"><span data-stu-id="399e3-127">Start Rundown</span></span>  

 <span data-ttu-id="399e3-128">Bir başlangıç Özeti, runaşağı sağlayıcısı altında günlüğe kaydetme `StartRundownKeyword` anahtar sözcüğüyle etkinleştirildiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="399e3-128">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="399e3-129">Bu, etkinliğin oluşturulmasına neden olur `DCStart` ve sistemin durumunu yakalar.</span><span class="sxs-lookup"><span data-stu-id="399e3-129">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="399e3-130">Numaralandırma başlamadan önce `DCStartInit` olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="399e3-130">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="399e3-131">Numaralandırmanın sonunda, `DCStartComplete` olay, veri toplamanın normal olarak sonlandırıldığı denetleyiciye bildirmek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="399e3-131">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="399e3-132">Özeti Sonlandır</span><span class="sxs-lookup"><span data-stu-id="399e3-132">End Rundown</span></span>  

 <span data-ttu-id="399e3-133">Özet oluşturma sağlayıcısı altında günlüğe kaydetme, anahtar sözcüğüyle etkinleştirildiği zaman bir bitiş Özeti tetiklenir `EndRundownKeyword` .</span><span class="sxs-lookup"><span data-stu-id="399e3-133">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="399e3-134">Özeti Sonlandır, yürütülmeye devam eden bir işlemde profil oluşturmayı durduruyor.</span><span class="sxs-lookup"><span data-stu-id="399e3-134">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="399e3-135">`DCEnd`Olaylar, profil oluşturma durdurulduğunda sistemin durumunu yakalar.</span><span class="sxs-lookup"><span data-stu-id="399e3-135">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="399e3-136">Numaralandırma başlamadan önce `DCEndInit` olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="399e3-136">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="399e3-137">Sabit listesinin sonunda, `DCEndComplete` Bu olay, tüketiciye veri toplamanın normal şekilde sonlandırıldığını bildirmek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="399e3-137">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="399e3-138">Başlangıç özeti ve bitiş Özeti öncelikle yönetilen sembol çözümlemesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="399e3-138">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="399e3-139">Özeti Başlat, profil oluşturma oturumu başlatılmadan önce zaten JıT olarak derlenen yöntemler için adres aralığı bilgisi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="399e3-139">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="399e3-140">Özet sonu, profil oluşturma işlemi kapalı olduğunda JıT derlenen tüm yöntemler için adres aralığı bilgisi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="399e3-140">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="399e3-141">Bir profil oluşturma oturumu durdurulduğunda, Özeti Sonlandır işlemi otomatik olarak gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="399e3-141">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="399e3-142">Bunun yerine, yönetilen sembol çözünürlüğünü gerçekleştirmeye yönelik bir aracın, `EndRundownKeyword` profil oluşturma durdurulmadan hemen önce, anahtar sözcüğü etkin BIR clr özet sağlayıcısı oturumunu açıkça çağırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="399e3-142">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="399e3-143">Başlangıç Özeti veya bitiş Özeti, yönetilen sembol çözümlemesi için yöntem adres aralığı bilgilerini sağlayabilse de, `EndRundownKeyword` anahtar sözcüğü (olayları `DCEnd` sağlar) yerine anahtar sözcüğünü (olayları sağlar) kullanmanızı öneririz `StartRundownKeyword` `DCStart` .</span><span class="sxs-lookup"><span data-stu-id="399e3-143">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="399e3-144">Kullanmak, `StartRundownKeyword` profil oluşturma oturumu sırasında Özet 'in profili oluşturulan senaryoyu rahatsız eden bir şekilde oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="399e3-144">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="399e3-145">Çalışma zamanı ve Özet sağlayıcıları kullanılarak ETW veri toplama</span><span class="sxs-lookup"><span data-stu-id="399e3-145">ETW Data Collection Using Runtime and Rundown Providers</span></span>  

 <span data-ttu-id="399e3-146">Aşağıdaki örnek, CLR özet sağlayıcısının, işlemlerin profil oluşturulmuş pencerenin içinde mi yoksa dışında mı başlayıp bitmediğine bakılmaksızın, en az etkiyle yönetilen işlemlerin sembol çözümüne izin veren bir şekilde nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="399e3-146">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1. <span data-ttu-id="399e3-147">CLR Runtime sağlayıcısını kullanarak ETW günlüğünü açın:</span><span class="sxs-lookup"><span data-stu-id="399e3-147">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```console
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl
    ```  
  
     <span data-ttu-id="399e3-148">Günlük, clr1. etl dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="399e3-148">The log will be saved to the clr1.etl file.</span></span>  
  
2. <span data-ttu-id="399e3-149">İşlem yürütülmeye devam ederken profil oluşturmayı durdurmak için, olay yakalamak üzere runaşağı sağlayıcısını başlatın `DCEnd` :</span><span class="sxs-lookup"><span data-stu-id="399e3-149">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```console
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl
    ```  
  
     <span data-ttu-id="399e3-150">Bu, `DCEnd` olay koleksiyonunun bir Özet oturum başlatmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="399e3-150">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="399e3-151">Tüm olayların toplanması için 30 ila 60 saniye beklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="399e3-151">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="399e3-152">Günlük, clr1. ET2 dosyasına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="399e3-152">The log will be saved to the clr1.et2 file.</span></span>  
  
3. <span data-ttu-id="399e3-153">Tüm ETW profil oluşturmayı kapat:</span><span class="sxs-lookup"><span data-stu-id="399e3-153">Turn off all ETW profiling:</span></span>  
  
    ```console
    xperf -stop clrRundown
    xperf -stop clr  
    ```  
  
4. <span data-ttu-id="399e3-154">Tek bir günlük dosyası oluşturmak için profilleri birleştirin:</span><span class="sxs-lookup"><span data-stu-id="399e3-154">Merge the profiles to create one log file:</span></span>  
  
    ```console
    xperf -merge clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="399e3-155">Birleştirilmiş. etl dosyası çalışma zamanı ve özet sağlayıcı oturumlarından olayları içerecektir.</span><span class="sxs-lookup"><span data-stu-id="399e3-155">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="399e3-156">Bir araç, bir Kullanıcı profil oluşturmayı istemesi durumunda profil oluşturmayı hemen kapatmak yerine 2 ve 3. adımları (bir Özet oturumu başlatıp profil oluşturmayı sonlandırıp) yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="399e3-156">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="399e3-157">Bir araç, 4. adımı da yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="399e3-157">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="399e3-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="399e3-158">See also</span></span>

- [<span data-ttu-id="399e3-159">Ortak Dil Çalışma Zamanında ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="399e3-159">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
