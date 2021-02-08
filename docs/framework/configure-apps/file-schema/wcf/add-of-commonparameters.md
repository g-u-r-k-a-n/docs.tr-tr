---
description: 'Hakkında daha fazla bilgi <add> edinin: <commonParameters>'
title: <add> / <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: d7a1b78ed79b7eab472460b364b90bd372ecf6bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804016"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="81130-103">\<add> / \<commonParameters></span><span class="sxs-lookup"><span data-stu-id="81130-103">\<add> of \<commonParameters></span></span>

<span data-ttu-id="81130-104">Birden çok hizmet arasında genel olarak kullanılan parametrelerin ad-değer çiftini belirtir.</span><span class="sxs-lookup"><span data-stu-id="81130-104">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="81130-105">Genellikle bu parametre, dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="81130-105">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="81130-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="81130-106">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81130-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="81130-107">Attributes and Elements</span></span>  

 <span data-ttu-id="81130-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81130-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81130-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="81130-109">Attributes</span></span>  
  
|<span data-ttu-id="81130-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="81130-110">Attribute</span></span>|<span data-ttu-id="81130-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81130-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81130-112">name</span><span class="sxs-lookup"><span data-stu-id="81130-112">name</span></span>|<span data-ttu-id="81130-113">Bir hizmet için belirtilen parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="81130-113">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="81130-114">değer</span><span class="sxs-lookup"><span data-stu-id="81130-114">value</span></span>|<span data-ttu-id="81130-115">Bir hizmet için belirtilen parametrenin değeri.</span><span class="sxs-lookup"><span data-stu-id="81130-115">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81130-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="81130-116">Child Elements</span></span>  

 <span data-ttu-id="81130-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="81130-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81130-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="81130-118">Parent Elements</span></span>  
  
|<span data-ttu-id="81130-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="81130-119">Element</span></span>|<span data-ttu-id="81130-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81130-120">Description</span></span>|  
|-------------|-----------------|  
|[\<commonParameters>](commonparameters.md)|<span data-ttu-id="81130-121">Hizmetler tarafından kullanılan ortak parametrelerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="81130-121">A collection of common parameters used by services.</span></span> <span data-ttu-id="81130-122">Bu koleksiyon, genellikle dayanıklı hizmetler tarafından paylaşılabilen veritabanı bağlantı dizesini içerir.</span><span class="sxs-lookup"><span data-stu-id="81130-122">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81130-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81130-123">Remarks</span></span>  

 <span data-ttu-id="81130-124">`<commonParameters>`Öğesi, ' yi kullanırken, birden çok hizmet arasında genel olarak kullanılan tüm parametreleri tanımlar `ConnectionString` <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> .</span><span class="sxs-lookup"><span data-stu-id="81130-124">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="81130-125">Ve gibi, kalıcılık depolarına iş toplu işleri uygulayan hizmetler için <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> , `EnableRetries` Aşağıdaki örnekte gösterildiği gibi, parametresini kullanarak işlemini yeniden denemesini sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="81130-125">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="81130-126">`EnableRetries`Parametrenin genel düzeyde ( *CommonParameters* bölümünde gösterildiği gibi) ya da tarafından desteklenen bireysel hizmetlerden `EnableRetries` ( *Hizmetler* bölümünde gösterildiği gibi) ayarlandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="81130-126">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="81130-127">Bir Windows Workflow Foundation ana bilgisayar uygulamasının bir nesnesinin davranışını denetlemek için yapılandırma dosyası kullanma hakkında daha fazla bilgi için <xref:System.Workflow.Runtime.WorkflowRuntime> bkz. [Iş akışı yapılandırma dosyaları](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="81130-127">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81130-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="81130-128">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="81130-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81130-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="81130-130">[İş akışı yapılandırma dosyaları](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="81130-130">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<commonParameters>](commonparameters.md)
