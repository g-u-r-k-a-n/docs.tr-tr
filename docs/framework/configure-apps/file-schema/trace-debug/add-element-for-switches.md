---
title: <switches> için <add> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: db2de681227dfdb7420808963219b9f52381f8fe
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088955"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="35164-102">\<anahtarlar için > öğesi \<ekleyin ></span><span class="sxs-lookup"><span data-stu-id="35164-102">\<add> Element for \<switches></span></span>
<span data-ttu-id="35164-103">Bir izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="35164-103">Specifies the level where a trace switch is set.</span></span>  

<span data-ttu-id="35164-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="35164-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="35164-105">[**System. diagnostics\<** ](system-diagnostics-element.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="35164-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="35164-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<anahtarlar >** ](switches-element.md)</span><span class="sxs-lookup"><span data-stu-id="35164-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)</span></span>\
<span data-ttu-id="35164-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add >**</span><span class="sxs-lookup"><span data-stu-id="35164-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="35164-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35164-108">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35164-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="35164-109">Attributes and Elements</span></span>  
 <span data-ttu-id="35164-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="35164-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35164-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="35164-111">Attributes</span></span>  
  
|<span data-ttu-id="35164-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="35164-112">Attribute</span></span>|<span data-ttu-id="35164-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35164-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35164-114">**ada**</span><span class="sxs-lookup"><span data-stu-id="35164-114">**name**</span></span>|<span data-ttu-id="35164-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="35164-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="35164-116">Anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35164-116">Specifies the name of the switch.</span></span> <span data-ttu-id="35164-117">Bu özniteliğin değeri, Switch yapıcısına geçirilen *DisplayName* parametresine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="35164-117">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="35164-118">**value**</span><span class="sxs-lookup"><span data-stu-id="35164-118">**value**</span></span>|<span data-ttu-id="35164-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="35164-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="35164-120">Anahtar düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="35164-120">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35164-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="35164-121">Child Elements</span></span>  
 <span data-ttu-id="35164-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="35164-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35164-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="35164-123">Parent Elements</span></span>  
  
|<span data-ttu-id="35164-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="35164-124">Element</span></span>|<span data-ttu-id="35164-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35164-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="35164-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="35164-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="35164-127">İzleme anahtarlarını ve izleme anahtarlarının ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="35164-127">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="35164-128">İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="35164-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35164-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35164-129">Remarks</span></span>  
 <span data-ttu-id="35164-130">Bir izleme anahtarı düzeyini bir yapılandırma dosyasına yerleştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35164-130">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="35164-131">Anahtar bir <xref:System.Diagnostics.BooleanSwitch>, açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35164-131">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="35164-132">Anahtar bir <xref:System.Diagnostics.TraceSwitch>ise, uygulamanın çıkışları için izleme veya hata ayıklama iletilerinin türlerini belirtmek üzere buna farklı düzeyler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35164-132">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35164-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="35164-133">Example</span></span>  
 <span data-ttu-id="35164-134">Aşağıdaki örnek, `General` izleme anahtarını <xref:System.Diagnostics.TraceLevel> düzeyine ayarlamak ve `Data` Boole izleme anahtarını etkinleştirmek için **\<add >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35164-134">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35164-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35164-135">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="35164-136">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="35164-136">Trace and Debug Settings Schema</span></span>](index.md)
