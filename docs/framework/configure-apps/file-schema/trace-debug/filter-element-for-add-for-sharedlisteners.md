---
title: <sharedListeners> için <add> <filter> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: e04ecd773bd6aa7791858711edbd72128dc391ea
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088877"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="996ff-102">\<sharedListeners için \<ekleme > için Filtre > öğesi \<</span><span class="sxs-lookup"><span data-stu-id="996ff-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="996ff-103">`sharedListeners` koleksiyonundaki bir dinleyiciye bir filtre ekler.</span><span class="sxs-lookup"><span data-stu-id="996ff-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

<span data-ttu-id="996ff-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="996ff-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="996ff-105">[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="996ff-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="996ff-106">&nbsp;&nbsp;&nbsp;&nbsp;\<[**sharedListeners**](sharedlisteners-element.md) ></span><span class="sxs-lookup"><span data-stu-id="996ff-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)</span></span>\
<span data-ttu-id="996ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<add >** ](add-element-for-sharedlisteners.md)</span><span class="sxs-lookup"><span data-stu-id="996ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)</span></span>\
<span data-ttu-id="996ff-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filtresi >**</span><span class="sxs-lookup"><span data-stu-id="996ff-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="996ff-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="996ff-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="996ff-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="996ff-110">Attributes and Elements</span></span>  
 <span data-ttu-id="996ff-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="996ff-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="996ff-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="996ff-112">Attributes</span></span>  
  
|<span data-ttu-id="996ff-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="996ff-113">Attribute</span></span>|<span data-ttu-id="996ff-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="996ff-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="996ff-115">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="996ff-115">**type**</span></span>|<span data-ttu-id="996ff-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="996ff-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="996ff-117">Filtrenin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="996ff-117">Specifies the type of the filter.</span></span> <span data-ttu-id="996ff-118">Türün tam adını (<xref:System.Type.FullName%2A?displayProperty=nameWithType> özelliğinin biçiminde) kullanabilir veya derleme bilgileri de dahil olmak üzere tam nitelikli tür adını (<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> özelliğinin biçiminde) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="996ff-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="996ff-119">Tam nitelikli tür adı oluşturma hakkında bilgi için, bkz. [tam nitelikli tür adları belirtme](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="996ff-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="996ff-120">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="996ff-120">**initializeData**</span></span>|<span data-ttu-id="996ff-121">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="996ff-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="996ff-122">Belirtilen sınıf için oluşturucuya geçirilen dize.</span><span class="sxs-lookup"><span data-stu-id="996ff-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="996ff-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="996ff-123">Child Elements</span></span>  
 <span data-ttu-id="996ff-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="996ff-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="996ff-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="996ff-125">Parent Elements</span></span>  
  
|<span data-ttu-id="996ff-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="996ff-126">Element</span></span>|<span data-ttu-id="996ff-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="996ff-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="996ff-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="996ff-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="996ff-129">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="996ff-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="996ff-130">Herhangi bir kaynak veya izleme öğesinin başvurmasına yönelik bir dinleyici koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="996ff-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="996ff-131">**SharedListeners** koleksiyonuna bir dinleyici ekler.</span><span class="sxs-lookup"><span data-stu-id="996ff-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="996ff-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="996ff-132">Remarks</span></span>  
 <span data-ttu-id="996ff-133">Bir dinleyici `<sharedListeners>` öğesinin bir `<add>` öğesinde tanımlanmışsa, bu dinleyicinin filtresi, `<add>` öğesinin bir alt öğesi olan bir `<filter>` öğesinde tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="996ff-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="996ff-134">Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="996ff-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="996ff-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="996ff-135">Example</span></span>  
 <span data-ttu-id="996ff-136">Aşağıdaki örnek, `sharedListeners` koleksiyonundaki izleme dinleyicisi `console` bir filtre eklemek için `<filter>` öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="996ff-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="996ff-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="996ff-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="996ff-138">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="996ff-138">Trace and Debug Settings Schema</span></span>](index.md)
