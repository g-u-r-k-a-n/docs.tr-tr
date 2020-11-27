---
title: Bağıntı Sorunlarını Giderme
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: 71e9cedde95791df3929b795312efd5a73fc3e93
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291095"
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="0cc1f-102">Bağıntı Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="0cc1f-102">Troubleshooting Correlation</span></span>

<span data-ttu-id="0cc1f-103">Bağıntı, iş akışı hizmeti iletilerini birbirleriyle ve doğru iş akışı örneğiyle ilişkilendirmek için kullanılır, ancak doğru yapılandırılmamışsa, iletiler alınmaz ve uygulamalar düzgün çalışmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="0cc1f-104">Bu konu, bağıntı sorunlarını gidermeye yönelik çeşitli yöntemlere genel bir bakış sağlar ve bağıntı kullandığınızda oluşabilecek bazı yaygın sorunları da listeler.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>

## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="0cc1f-105">UnknownMessageReceived olayını işleme</span><span class="sxs-lookup"><span data-stu-id="0cc1f-105">Handle the UnknownMessageReceived Event</span></span>

 <span data-ttu-id="0cc1f-106"><xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>Bu olay, mevcut bir örnekle bağıntılı olmayan iletiler de dahil olmak üzere bir hizmet tarafından bilinmeyen bir ileti alındığında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="0cc1f-107">Şirket içinde barındırılan hizmetler için bu olay ana bilgisayar uygulamasında işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-107">For self-hosted services, this event can be handled in the host application.</span></span>

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 <span data-ttu-id="0cc1f-108">Web 'de barındırılan hizmetler için bu olay bir sınıf türeterek <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> ve geçersiz kılınarak işlenebilir <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A> .</span><span class="sxs-lookup"><span data-stu-id="0cc1f-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>

```csharp
class CustomFactory : WorkflowServiceHostFactory
{
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)
    {
        // Create the WorkflowServiceHost.
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);

        // Handle the UnknownMessageReceived event.
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
        {
            Console.WriteLine("Unknown Message Received:");
            Console.WriteLine(e.Message);
        };

        return host;
    }
}
```

 <span data-ttu-id="0cc1f-109">Bu özel <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> daha sonra `svc` hizmetin dosyasında belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>

`<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>`

 <span data-ttu-id="0cc1f-110">Bu işleyici çağrıldığında, ileti <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> öğesinin özelliği kullanılarak alınabilir <xref:System.ServiceModel.UnknownMessageReceivedEventArgs> ve aşağıdaki iletiye benzecektir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
  </s:Header>
  <s:Body>
    <AddItem xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItem>
  </s:Body>
</s:Envelope>
```

 <span data-ttu-id="0cc1f-111">İşleyiciye dağıtılan iletilerin İnceleme, <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> iletinin neden iş akışı hizmeti örneğiyle bağıntılı olduğuna ilişkin ipuçları verebilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="0cc1f-112">Iş akışının Ilerlemesini Izlemek için Izleme kullanma</span><span class="sxs-lookup"><span data-stu-id="0cc1f-112">Use Tracking to Monitor the Progress of the Workflow</span></span>

 <span data-ttu-id="0cc1f-113">İzleme, bir iş akışının ilerlemesini izlemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="0cc1f-114">Varsayılan olarak, izleme kayıtları iş akışı yaşam döngüsü olayları, etkinlik yaşam döngüsü olayları, hata yayma ve yer işareti sürdürme için yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="0cc1f-115">Ayrıca, özel izleme kayıtları özel etkinlikler tarafından dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="0cc1f-116">Bağıntı sorunlarını giderirken, etkinlik izleme kayıtları, yer işareti sürdürme kayıtları ve hata yayma kayıtları en yararlı seçenektir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="0cc1f-117">Etkinlik izleme kayıtları, iş akışının geçerli ilerlemesini belirlemek için kullanılabilir ve şu anda ileti için bekleyen mesajlaşma etkinliğini belirlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="0cc1f-118">Yer işareti sürdürme kayıtları, iş akışı tarafından bir iletinin alındığını ve hata yayma kayıtları iş akışındaki hataların bir kaydını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="0cc1f-119">İzlemeyi etkinleştirmek için, <xref:System.Activities.Tracking.TrackingParticipant> içinde istediğiniz ' ı belirtin <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="0cc1f-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="0cc1f-120">Aşağıdaki örnekte, `ConsoleTrackingParticipant` ( [özel izleme](../../windows-workflow-foundation/samples/custom-tracking.md) örneğinden) varsayılan izleme profili kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 <span data-ttu-id="0cc1f-121">Consoletrackingkatılımcı gibi bir izleme katılımcısı, bir konsol penceresi olan şirket içinde barındırılan iş akışı hizmetleri için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="0cc1f-122">Web 'de barındırılan bir hizmet için izleme bilgilerini sürekli bir depoya kaydeden bir izleme katılımcısı, yerleşik <xref:System.Activities.Tracking.EtwTrackingParticipant> veya bilgileri bir dosyaya kaydeden özel bir izleme katılımcısı gibi kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file.</span></span>

 <span data-ttu-id="0cc1f-123">Web 'de barındırılan bir iş akışı hizmeti için izlemeyi izleme ve yapılandırma hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../../windows-workflow-foundation/workflow-tracking-and-tracing.md), [Iş akışı için izlemeyi yapılandırma](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)ve [&#91;WF örnekleri&#93;](../../windows-workflow-foundation/samples/tracking.md) örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-123">For more information about tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../windows-workflow-foundation/samples/tracking.md) samples.</span></span>

## <a name="use-wcf-tracing"></a><span data-ttu-id="0cc1f-124">WCF Izlemeyi kullan</span><span class="sxs-lookup"><span data-stu-id="0cc1f-124">Use WCF Tracing</span></span>

 <span data-ttu-id="0cc1f-125">WCF izleme, bir iş akışı hizmetine veya bir iş akışı hizmetinden ileti akışını izlemeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="0cc1f-126">Bu izleme bilgileri, özellikle içerik tabanlı bağıntı için, bağıntı sorunlarını giderirken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="0cc1f-127">İzlemeyi etkinleştirmek için, `system.diagnostics` `web.config` iş akışı hizmeti Web 'de barındırılıyorsa veya `app.config` iş akışı hizmeti kendiliğinden barındırılıyorsa dosyayı dosyanın bölümünde, istenen izleme dinleyicilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="0cc1f-128">İletilerin içeriğini izleme dosyasına eklemek için `true` `logEntireMessage` `messageLogging` bölümündeki öğesinde için öğesini belirtin `diagnostics` `system.serviceModel` .</span><span class="sxs-lookup"><span data-stu-id="0cc1f-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="0cc1f-129">Aşağıdaki örnekte, iletilerin içeriği de dahil olmak üzere izleme bilgileri, adlı bir dosyaya yazılacak şekilde yapılandırılmıştır `service.svclog` .</span><span class="sxs-lookup"><span data-stu-id="0cc1f-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
      <source name="System.ServiceModel.MessageLogging">
        <listeners>
          <add name="corr"/>
        </listeners>
      </source>
    </sources>

    <sharedListeners>
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">
      </add>
    </sharedListeners>
  </system.diagnostics>

  <system.serviceModel>
    <diagnostics>
      <messageLogging logEntireMessage="true" logMalformedMessages="false"
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">
      </messageLogging>
    </diagnostics>
  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="0cc1f-130">' De bulunan izleme bilgilerini görüntülemek için `service.svclog` , [hizmet Izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="0cc1f-131">Bu özellikle, ileti içeriğini görüntüleyebildiğinden ve tam olarak neyin geçtiğini ve <xref:System.ServiceModel.CorrelationQuery> içerik tabanlı bağıntı için ile eşleşip eşleşmediğini görmenizi sağladığından, içerik tabanlı bağıntı sorunları giderirken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> <span data-ttu-id="0cc1f-132">WCF izleme hakkında daha fazla bilgi için bkz. [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md), [Izlemeyi yapılandırma](../diagnostics/tracing/configuring-tracing.md)ve [uygulamanızda sorun giderme için izleme kullanma](../diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="0cc1f-132">For more information about WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="0cc1f-133">Ortak bağlam değişim bağıntı sorunları</span><span class="sxs-lookup"><span data-stu-id="0cc1f-133">Common Context Exchange Correlation Issues</span></span>

 <span data-ttu-id="0cc1f-134">Belirli bağıntı türleri, bağıntı doğru şekilde çalışması için belirli bir bağlama türünün kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="0cc1f-135">Örnek olarak, gibi iki yönlü bir bağlama gerektiren istek-yanıt bağıntısını ve gibi <xref:System.ServiceModel.BasicHttpBinding> bağlam tabanlı bağlama gerektiren bağlam değişim bağıntısını içerir <xref:System.ServiceModel.BasicHttpContextBinding> .</span><span class="sxs-lookup"><span data-stu-id="0cc1f-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="0cc1f-136">Çoğu bağlama iki yönlü işlemleri destekler. bu nedenle, istek-yanıt bağıntısı için yaygın bir sorun değildir, ancak, ve dahil olmak üzere yalnızca el ile bağlam tabanlı bağlamalar <xref:System.ServiceModel.BasicHttpContextBinding> vardır <xref:System.ServiceModel.WSHttpContextBinding> <xref:System.ServiceModel.NetTcpContextBinding> .</span><span class="sxs-lookup"><span data-stu-id="0cc1f-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="0cc1f-137">Bu bağlamalardan biri kullanılmazsa, bir iş akışı hizmetine yapılan ilk çağrı başarılı olur, ancak sonraki çağrılar aşağıdaki gibi başarısız olur <xref:System.ServiceModel.FaultException> .</span><span class="sxs-lookup"><span data-stu-id="0cc1f-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>

```output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 <span data-ttu-id="0cc1f-138">Bağlam bağıntısı için kullanılan bağlam bilgileri, <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Receive> iki yönlü bir işlem kullanılırken bağlam bağıntısını Başlatan etkinliğe veya işlem tek yönlü ise çağıran tarafından belirtilebilecek şekilde döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="0cc1f-139">Bağlam, çağıran tarafından gönderilmezse veya iş akışı hizmeti tarafından döndürülürse, <xref:System.ServiceModel.FaultException> sonraki bir işlem çağrıldığında daha önce açıklanan daha önce de açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>

## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="0cc1f-140">Ortak Request-Reply bağıntı sorunları</span><span class="sxs-lookup"><span data-stu-id="0cc1f-140">Common Request-Reply Correlation Issues</span></span>

 <span data-ttu-id="0cc1f-141">İstek-Yanıt Bağıntısı, bir <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> iş akışı hizmetinde iki yönlü bir işlem ve <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> başka bir Web hizmetinde iki yönlü bir işlem çağıran bir çifte bir çifte birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-141">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="0cc1f-142">Bir WCF hizmetinde iki yönlü bir işlem çağrılırken, hizmet geleneksel bir kesinlik temelli kod tabanlı WCF hizmeti olabilir veya bir iş akışı hizmeti olabilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-142">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based WCF service or it can be a workflow service.</span></span> <span data-ttu-id="0cc1f-143">İstek-yanıt bağıntısını kullanmak için iki yönlü bağlama kullanılmalıdır, örneğin <xref:System.ServiceModel.BasicHttpBinding> , ve işlemler iki yönlü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-143">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>

 <span data-ttu-id="0cc1f-144">İş akışı hizmetinin paralel veya çakışan ya da çiftler halinde iki yönlü işlemleri varsa, <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> tarafından sunulan örtük bağıntı tanıtıcısı yönetimi, <xref:System.ServiceModel.Activities.WorkflowServiceHost> özellikle yüksek stres senaryolarında yeterli olmayabilir ve iletiler doğru şekilde yönlendirilmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-144">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="0cc1f-145">Bu sorunun oluşmasını önlemek için, <xref:System.ServiceModel.Activities.CorrelationHandle> istek-yanıt bağıntısını kullanırken her zaman açıkça bir belirtmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-145">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="0cc1f-146">İş akışı tasarımcısında **araç kutusunun** Mesajlaşma bölümünde **SendAndReceiveReply** ve **ReceiveAndSendReply** şablonları kullanılırken, <xref:System.ServiceModel.Activities.CorrelationHandle> Varsayılan olarak açıkça yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-146">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="0cc1f-147">Kodu kullanarak bir iş akışı oluştururken, <xref:System.ServiceModel.Activities.CorrelationHandle> <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> çiftteki ilk etkinliğin içinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-147">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="0cc1f-148">Aşağıdaki örnekte, bir <xref:System.ServiceModel.Activities.Receive> etkinlik öğesinde belirtilen açık ile yapılandırılır <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .</span><span class="sxs-lookup"><span data-stu-id="0cc1f-148">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>

```csharp
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();

Receive StartOrder = new Receive
{
    CanCreateInstance = true,
    ServiceContractName = OrderContractName,
    OperationName = "StartOrder",
    CorrelationInitializers =
    {
        new RequestReplyCorrelationInitializer
        {
            CorrelationHandle = RRHandle
        }
    }
};

SendReply ReplyToStartOrder = new SendReply
{
    Request = StartOrder,
    Content = ... // Contains the return value, if any.
};

// Construct a workflow using StartOrder and ReplyToStartOrder.
```

 <span data-ttu-id="0cc1f-149"><xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> Çift veya <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> çift arasında Kalıcılık kullanılmasına izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-149">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="0cc1f-150">Her iki etkinlik de tamamlanana kadar devam eden kalıcı olmayan bir bölge oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-150">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="0cc1f-151">Gecikme etkinliği gibi bir etkinlik bu kalıcı olmayan bir bölgede yer alıyorsa ve iş akışının boşta olmasına neden oluyorsa, ana bilgisayar boşta kaldığında iş akışlarını kalıcı hale getirmek üzere yapılandırılmış olsa bile, iş akışı devam etmez.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-151">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="0cc1f-152">Kalıcı etkinlik gibi bir etkinlik, kalıcı olmayan bir bölgede açık bir şekilde kalıcı hale getirmeye çalışırsa, önemli bir özel durum oluşturulur, iş akışı iptal edilir ve <xref:System.ServiceModel.FaultException> çağrı yapana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-152">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="0cc1f-153">Önemli özel durum iletisi "System. InvalidOperationException: Persist etkinlikleri kalıcı olmayan bloklar içinde yer alamaz.".</span><span class="sxs-lookup"><span data-stu-id="0cc1f-153">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="0cc1f-154">Bu özel durum çağırana döndürülmüyor, ancak izleme etkinse gözlemlenebilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-154">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="0cc1f-155"><xref:System.ServiceModel.FaultException>Arayan için döndürülen ileti ", WorkflowInstance ' 5836145b-7dav2-49d0-a052-a49162adeab6 ' tamamlandığı için işlem gerçekleştirilemedi.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-155">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>

 <span data-ttu-id="0cc1f-156">İstek-yanıt bağıntısı hakkında daha fazla bilgi için bkz. [istek-yanıt](request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="0cc1f-156">For more information about request-reply correlation, see [Request-Reply](request-reply-correlation.md).</span></span>

## <a name="common-content-correlation-issues"></a><span data-ttu-id="0cc1f-157">Ortak Içerik bağıntı sorunları</span><span class="sxs-lookup"><span data-stu-id="0cc1f-157">Common Content Correlation Issues</span></span>

 <span data-ttu-id="0cc1f-158">İçerik tabanlı bağıntı, bir iş akışı hizmeti birden çok ileti aldığında ve değiştirilen iletilerde bir veri parçası istenen örneği tanımlarsa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-158">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="0cc1f-159">İçerik tabanlı bağıntı, iletileri doğru iş akışı örneğine yönlendirmek için bir müşteri numarası veya sipariş KIMLIĞI gibi iletideki bu verileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-159">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="0cc1f-160">Bu bölümde, içerik tabanlı bağıntı kullanılırken oluşabilecek bazı yaygın sorunlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-160">This section describes several common issues that may occur when using content-based correlation.</span></span>

### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="0cc1f-161">Tanımlayıcı verilerin benzersiz olduğundan emin olun</span><span class="sxs-lookup"><span data-stu-id="0cc1f-161">Ensure the Identifying Data Is Unique</span></span>

 <span data-ttu-id="0cc1f-162">Örneği tanımlamak için kullanılan veriler bir bağıntı anahtarına karma hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-162">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="0cc1f-163">Bağıntı için kullanılan verilerin benzersiz olduğundan emin olmak için dikkatli olunmalıdır, aksi takdirde karma anahtardaki çakışmaların oluşması ve iletilerin hatalı yönlendirilmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-163">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="0cc1f-164">Örneğin, aynı ada sahip birden fazla müşteri olabileceğinden, yalnızca müşteri adı temelinde bir bağıntı çakışmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-164">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="0cc1f-165">İki nokta (:) ileti sorgusunun anahtar ve değerini daha sonra karma hale getirilen dizeyi oluşturacak şekilde sınırlandırmak için zaten kullanıldığından, iletiyi ilişkilendirmek için kullanılan verilerin bir parçası olarak kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-165">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="0cc1f-166">Kalıcılık kullanılıyorsa, geçerli tanımlama verilerinin önceden kalıcı bir örnek tarafından kullanılmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-166">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="0cc1f-167">Kalıcılığı geçici olarak devre dışı bırakmak bu sorunu belirlemenize yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-167">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="0cc1f-168">WCF izleme, hesaplanan bağıntı anahtarını görüntülemek için kullanılabilir ve bu tür bir sorunu ayıklamak için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-168">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>

### <a name="race-conditions"></a><span data-ttu-id="0cc1f-169">Yarış durumları</span><span class="sxs-lookup"><span data-stu-id="0cc1f-169">Race Conditions</span></span>

 <span data-ttu-id="0cc1f-170">Bir ileti alma ile bağıntıdan başlatılan bağıntı arasında küçük bir boşluk vardır ve bu süre, izleme iletilerinin yok sayılacak olur.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-170">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="0cc1f-171">Bir iş akışı hizmeti, istemciden tek yönlü bir işlem üzerinden geçirilen verileri kullanarak içerik tabanlı bağıntıyı başlatır ve arayan anında izleme iletileri gönderdiğinde, bu iletiler bu Aralık sırasında yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-171">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="0cc1f-172">Bu, bağıntıyı başlatmak için iki yönlü bir işlem kullanılarak veya kullanılarak kaçınılabilir <xref:System.ServiceModel.Activities.TransactedReceiveScope> .</span><span class="sxs-lookup"><span data-stu-id="0cc1f-172">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>

### <a name="correlation-query-issues"></a><span data-ttu-id="0cc1f-173">Bağıntı sorgusu sorunları</span><span class="sxs-lookup"><span data-stu-id="0cc1f-173">Correlation Query Issues</span></span>

 <span data-ttu-id="0cc1f-174">Bağıntı sorguları, iletiyi ilişkilendirmek için hangi verilerin kullanıldığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-174">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="0cc1f-175">Bu veriler bir XPath sorgusu kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-175">This data is specified by using an XPath query.</span></span> <span data-ttu-id="0cc1f-176">Her şey doğru gibi görünse de bir hizmete gönderilen iletiler dağıtılmazsa, sorun gidermeye yönelik bir strateji, bir XPath sorgusu yerine ileti verilerinin değeriyle eşleşen bir sabit değer belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-176">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="0cc1f-177">Bir sabit değer belirtmek için `string` işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-177">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="0cc1f-178">Aşağıdaki örnekte, <xref:System.ServiceModel.MessageQuerySet> , için değişmez değer değerini kullanacak şekilde yapılandırılmıştır `11445` `OrderId` ve XPath sorgusu açıklama olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-178">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>

```csharp
MessageQuerySet = new MessageQuerySet
{
    {
        "OrderId",
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")
        new XPathMessageQuery("string('11445')")
    }
}
```

 <span data-ttu-id="0cc1f-179">Bir XPath sorgusu, hiçbir bağıntı verisi alınmadıysa yanlış yapılandırılmışsa şu iletiyle bir hata döndürülür: "bir bağıntı sorgusu boş bir sonuç kümesi verdi.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-179">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="0cc1f-180">Lütfen uç nokta için bağıntı sorgularının doğru yapılandırıldığından emin olun. "</span><span class="sxs-lookup"><span data-stu-id="0cc1f-180">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="0cc1f-181">Bu sorunu gidermeye yönelik bir hızlı yol, XPath sorgusunun önceki bölümde açıklanan şekilde değişmez değer değeriyle değiştirilmesini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-181">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="0cc1f-182">Bu sorun, **bağıntı başlatıcıları** veya **CorrelatesOn tanımı** Ekle iletişim kutularında XPath sorgu oluşturucuyu kullanırsanız ve iş akışı hizmetiniz ileti sözleşmeleri kullanıyorsa oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-182">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="0cc1f-183">Aşağıdaki örnekte, bir ileti sözleşmesi sınıfı tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-183">In the following example, a message contract class is defined.</span></span>

```csharp
[MessageContract]
public class AddItemMessage
{
    [MessageHeader]
    public string CartId;

    [MessageBodyMember]
    public string Item;
}
```

 <span data-ttu-id="0cc1f-184">Bu ileti sözleşmesi <xref:System.ServiceModel.Activities.Receive> bir iş akışındaki etkinlik tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-184">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="0cc1f-185">`CartId`İleti üstbilgisinde ileti doğru örnekle ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-185">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="0cc1f-186">Öğesini alan XPath sorgusu, `CartId` iş akışı tasarımcısında bağıntı iletişim kutuları kullanılarak oluşturulduysa, şu yanlış XPath sorgusu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-186">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 <span data-ttu-id="0cc1f-187">Bu XPath sorgusu, <xref:System.ServiceModel.Activities.Receive> etkinlik veriler için parametreler kullanıyorsa, ancak bir ileti sözleşmesi kullandığı için doğru olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-187">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="0cc1f-188">Aşağıdaki XPath sorgusu, üst bilgisinden alınacak doğru XPath sorgusudur `CartId` .</span><span class="sxs-lookup"><span data-stu-id="0cc1f-188">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>

```
sm:header()/tempuri:CartId
```

<span data-ttu-id="0cc1f-189">Bu, iletinin gövdesini inceleyerek onaylanır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-189">This can be confirmed by examining the body of the message.</span></span>

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header>
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>
  </s:Header>
  <s:Body>
    <AddItemMessage xmlns="http://tempuri.org/">
      <Item>Books</Item>
    </AddItemMessage>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="0cc1f-190">Aşağıdaki örnekte, <xref:System.ServiceModel.Activities.Receive> `AddItem` verileri almak için önceki ileti sözleşmesini kullanan bir işlem için yapılandırılmış bir etkinlik gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-190">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="0cc1f-191">XPath sorgusu doğru bir şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0cc1f-191">The XPath query is correctly configured.</span></span>

```xaml
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">
  <Receive.CorrelatesOn>
    <XPathMessageQuery x:Key="key1">
      <XPathMessageQuery.Namespaces>
        <ssx:XPathMessageContextMarkup>
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>
        </ssx:XPathMessageContextMarkup>
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>
  </Receive.CorrelatesOn>
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>
  </ReceiveMessageContent>
</Receive>
```
