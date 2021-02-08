---
description: 'Daha fazla bilgi edinin: döngüsel Izleme'
title: Döngüsel İzleme
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 4b50420c7eb0c6ca9bc6b3354c78e7922b00f16c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778756"
---
# <a name="circular-tracing"></a><span data-ttu-id="926ea-103">Döngüsel İzleme</span><span class="sxs-lookup"><span data-stu-id="926ea-103">Circular Tracing</span></span>

<span data-ttu-id="926ea-104">Bu örnek, döngüsel arabellek İzleme dinleyicisinin uygulanmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="926ea-104">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="926ea-105">Üretim Hizmetleri için yaygın bir senaryo, uzun süreler için kullanılabilir olan ve düşük düzeyde izleme günlüğü etkin olan hizmetlerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="926ea-105">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="926ea-106">Bu hizmetler çok fazla disk alanı tüketir.</span><span class="sxs-lookup"><span data-stu-id="926ea-106">These services consume a lot of disk space.</span></span> <span data-ttu-id="926ea-107">Bir hizmette sorun giderirken, izleme günlüğündeki en son veriler bir sorunu çözmeye uygun olur.</span><span class="sxs-lookup"><span data-stu-id="926ea-107">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="926ea-108">Bu örnek, yalnızca en son izlemelerin yapılandırılabilir bir veri miktarına kadar diskte tutulduğu döngüsel bir arabellek İzleme dinleyicisi uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="926ea-108">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="926ea-109">Bu örnek [Başlarken](getting-started-sample.md) ' i temel alır ve özel bir izleme dinleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="926ea-109">This sample is based on the [Getting Started](getting-started-sample.md) and includes a custom tracing listener.</span></span>

> [!NOTE]
> <span data-ttu-id="926ea-110">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="926ea-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="926ea-111">Bu örnek, [izleme ve Ileti günlüğe kaydetme](tracing-and-message-logging.md) örneği hakkında bilgi sahibi olduğunuzu ve [Izleme ve mesaj günlüğü](tracing-and-message-logging.md) örneği için sunulan belgeleri okuduğunuzu varsayar.</span><span class="sxs-lookup"><span data-stu-id="926ea-111">This sample assumes that you are familiar with the [Tracing and Message Logging](tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](tracing-and-message-logging.md) sample.</span></span>

## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="926ea-112">Döngüsel arabellek Izleme dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="926ea-112">Circular Buffer Trace Listener</span></span>

<span data-ttu-id="926ea-113">Döngüsel arabellek Izleme dinleyicisi uygulamasının arkasındaki kavram, her bir depolama alanı için istenen toplam izleme günlüğü verilerinin yarısını oluşturan iki dosya vardır.</span><span class="sxs-lookup"><span data-stu-id="926ea-113">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="926ea-114">Dinleyici bir dosya oluşturur ve veri boyutunun yarısını alıncaya kadar bu dosyaya yazar; bu noktada ikinci bir dosyaya geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="926ea-114">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="926ea-115">Dinleyici ikinci dosya için sınıra ulaştığında, ilk dosyanın üzerine yeni izlemelerle yazar.</span><span class="sxs-lookup"><span data-stu-id="926ea-115">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>

<span data-ttu-id="926ea-116">Bu dinleyici öğesinden türetilir `XmlWriteTraceListener` ve günlüklerin [hizmet Izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)ile görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="926ea-116">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="926ea-117">Günlükleri görüntülemeye çalışırken, iki günlük dosyası her iki günlük dosyası da hizmet Izleme Görüntüleyicisi aracında aynı anda açılarak kolayca yeniden birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="926ea-117">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="926ea-118">Hizmet Izleme Görüntüleyicisi Aracı, izlemeleri doğru sırada görünecek şekilde sıralamayı otomatik olarak gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="926ea-118">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>

## <a name="configuration"></a><span data-ttu-id="926ea-119">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="926ea-119">Configuration</span></span>

<span data-ttu-id="926ea-120">Bir hizmet, bir dinleyici ve kaynak öğeleri için aşağıdaki kodu ekleyerek döngüsel arabellek Izleme dinleyicisini kullanacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="926ea-120">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="926ea-121">En büyük dosya boyutu, `maxFileSizeKB` Döngüsel İzleme dinleyicisi yapılandırmasındaki özniteliği ayarlanarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="926ea-121">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="926ea-122">Bu, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="926ea-122">This is demonstrated in the following code.</span></span>

```xml
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">
      <listeners>
        <add name="CircularTraceListener" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />
  </sharedListeners>
  <trace autoflush="true" />
</system.diagnostics>
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="926ea-123">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="926ea-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="926ea-124">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="926ea-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="926ea-125">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="926ea-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="926ea-126">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="926ea-126">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="926ea-127">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="926ea-127">The samples may already be installed on your computer.</span></span> <span data-ttu-id="926ea-128">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="926ea-128">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="926ea-129">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="926ea-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="926ea-130">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="926ea-130">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`

## <a name="see-also"></a><span data-ttu-id="926ea-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="926ea-131">See also</span></span>

- <span data-ttu-id="926ea-132">[AppFabric Izleme örnekleri](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="926ea-132">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
