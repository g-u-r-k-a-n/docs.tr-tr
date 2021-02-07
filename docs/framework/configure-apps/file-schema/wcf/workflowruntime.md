---
description: 'Hakkında daha fazla bilgi edinin: <workflowRuntime>'
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 9c234073bbbbfc8f1b5bb1579ff1dfa54a744ec1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682233"
---
# \<workflowRuntime>

<span data-ttu-id="5b2b1-102"><xref:System.Workflow.Runtime.WorkflowRuntime>İş akışı tabanlı Windows Communication Foundation (WCF) hizmetlerini barındırmak için bir örneğinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
## <a name="syntax"></a><span data-ttu-id="5b2b1-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b2b1-103">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b2b1-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b2b1-104">Attributes and Elements</span></span>  

 <span data-ttu-id="5b2b1-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b2b1-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5b2b1-106">Attributes</span></span>  
  
|<span data-ttu-id="5b2b1-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5b2b1-107">Attribute</span></span>|<span data-ttu-id="5b2b1-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b2b1-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5b2b1-109">CachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="5b2b1-109">cachedInstanceExpiration</span></span>|<span data-ttu-id="5b2b1-110"><xref:System.TimeSpan>Bir iş akışı örneğinin, zorla kaldırılmadan veya durdurulmadan önce boşta durumunda kalabileceği en uzun süreyi belirten isteğe bağlı bir değer.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-110">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="5b2b1-111">WorkflowRuntime, `PersistenceService` UnloadOnIdle işlemini gerçekleştirirse, bu öznitelik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-111">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="5b2b1-112">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="5b2b1-112">enablePerformanceCounters</span></span>|<span data-ttu-id="5b2b1-113">Performans sayaçlarının etkin olup olmadığını belirten isteğe bağlı bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-113">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="5b2b1-114">Performans sayaçları, iş akışı ile ilgili çeşitli istatistikler hakkında bilgi sağlar, ancak iş akışı çalışma zamanı altyapısı başladığında ve iş akışı örnekleri çalışırken performans cezasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-114">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="5b2b1-115">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-115">The default value is `true`.</span></span>|  
|<span data-ttu-id="5b2b1-116">name</span><span class="sxs-lookup"><span data-stu-id="5b2b1-116">name</span></span>|<span data-ttu-id="5b2b1-117">İş akışı çalışma zamanı altyapısının adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-117">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="5b2b1-118">Bu ad, bu çalışma zamanını sistemde çalışmakta olabilecek diğer çalışma zamanları (örneğin, performans sayaçları) ayırt etmek için çıktıda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-118">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="5b2b1-119">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-119">The default is an empty string.</span></span>|  
|<span data-ttu-id="5b2b1-120">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="5b2b1-120">validateOnCreate</span></span>|<span data-ttu-id="5b2b1-121">WorkflowServiceHost açıldığında iş akışı tanımı doğrulamasının gerçekleşmeyeceğini belirten isteğe bağlı bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-121">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="5b2b1-122">Bu öznitelik olarak ayarlandığında `true` , iş akışı doğrulama her `WorkflowServiceHost.Open` çağrıldığında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-122">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="5b2b1-123">Doğrulama hataları bulunursa bir <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-123">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="5b2b1-124">Bu özellik olarak ayarlandığında `false` , Iş akışı tanımı doğrulaması gerçekleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-124">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="5b2b1-125">Bu özellik için varsayılan değer `true` .</span><span class="sxs-lookup"><span data-stu-id="5b2b1-125">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b2b1-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b2b1-126">Child Elements</span></span>  
  
|<span data-ttu-id="5b2b1-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="5b2b1-127">Element</span></span>|<span data-ttu-id="5b2b1-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b2b1-128">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b2b1-129">commonParameters</span><span class="sxs-lookup"><span data-stu-id="5b2b1-129">commonParameters</span></span>|<span data-ttu-id="5b2b1-130">Hizmetler tarafından kullanılan ortak parametrelerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-130">A collection of common parameters used by services.</span></span> <span data-ttu-id="5b2b1-131">Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-131">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="5b2b1-132">services</span><span class="sxs-lookup"><span data-stu-id="5b2b1-132">services</span></span>|<span data-ttu-id="5b2b1-133">Altyapıya eklenecek hizmetlerden oluşan bir koleksiyon <xref:System.Workflow.Runtime.WorkflowRuntime> .</span><span class="sxs-lookup"><span data-stu-id="5b2b1-133">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="5b2b1-134">Öğeler türündedir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="5b2b1-134">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="5b2b1-135">Koleksiyonda belirtilen hizmetler, iş akışı çalışma zamanı altyapısı tarafından başlatılır ve uygun Oluşturucu çağrıldığında bu hizmetin hizmetlerine eklenir <xref:System.Workflow.Runtime.WorkflowRuntime> .</span><span class="sxs-lookup"><span data-stu-id="5b2b1-135">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="5b2b1-136">Bu nedenle, koleksiyonda belirtilen hizmetler oluşturucuların imzaları hakkındaki belirli kurallara uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-136">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="5b2b1-137">Daha fazla bilgi edinmek için bkz. <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-137">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b2b1-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5b2b1-138">Parent Elements</span></span>  
  
|<span data-ttu-id="5b2b1-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="5b2b1-139">Element</span></span>|<span data-ttu-id="5b2b1-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b2b1-140">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="5b2b1-141">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-141">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b2b1-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5b2b1-142">Remarks</span></span>  

 <span data-ttu-id="5b2b1-143">Bir Windows Workflow Foundation ana bilgisayar uygulamasının bir nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için <xref:System.Workflow.Runtime.WorkflowRuntime> bkz. [Iş akışı yapılandırma dosyaları](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5b2b1-143">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b2b1-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="5b2b1-144">Example</span></span>  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="5b2b1-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b2b1-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="5b2b1-146">[İş akışı yapılandırma dosyaları](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5b2b1-146">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
