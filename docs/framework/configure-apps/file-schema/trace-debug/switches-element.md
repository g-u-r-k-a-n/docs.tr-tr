---
title: <switches> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: 15cc9680d7a20341eb5d1d1df302c1e034e70e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153236"
---
# <a name="switches-element"></a><span data-ttu-id="97c36-102">\<anahtarları> Eleman</span><span class="sxs-lookup"><span data-stu-id="97c36-102">\<switches> Element</span></span>
<span data-ttu-id="97c36-103">İzleme anahtarları ve izleme anahtarlarının ayarlandığı düzeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="97c36-103">Contains trace switches and the level where the trace switches are set.</span></span>  

<span data-ttu-id="97c36-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="97c36-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="97c36-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="97c36-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="97c36-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<anahtarları>**</span><span class="sxs-lookup"><span data-stu-id="97c36-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>

## <a name="syntax"></a><span data-ttu-id="97c36-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97c36-107">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97c36-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="97c36-108">Attributes and Elements</span></span>  
 <span data-ttu-id="97c36-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="97c36-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97c36-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="97c36-110">Attributes</span></span>  
 <span data-ttu-id="97c36-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="97c36-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="97c36-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="97c36-112">Child Elements</span></span>  
  
|<span data-ttu-id="97c36-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="97c36-113">Element</span></span>|<span data-ttu-id="97c36-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97c36-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97c36-115">\<>ekleyin</span><span class="sxs-lookup"><span data-stu-id="97c36-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="97c36-116">İzleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="97c36-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97c36-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="97c36-117">Parent Elements</span></span>  
  
|<span data-ttu-id="97c36-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="97c36-118">Element</span></span>|<span data-ttu-id="97c36-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97c36-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="97c36-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="97c36-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="97c36-121">İletileri toplayan, depolayan ve yönlendiren izleme dinleyicilerini ve izleme anahtarının ayarlandığı düzeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="97c36-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97c36-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97c36-122">Remarks</span></span>  
 <span data-ttu-id="97c36-123">Bir yapılandırma dosyasına koyarak izleme anahtarıdüzeyini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97c36-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="97c36-124">Anahtar bir <xref:System.Diagnostics.BooleanSwitch>ise, açıp kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97c36-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="97c36-125">Anahtar bir <xref:System.Diagnostics.TraceSwitch>ise, uygulama çıktılarının izleme veya hata ayıklama iletilerinin türlerini belirtmek için bu düzeylere farklı düzeyler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97c36-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97c36-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="97c36-126">Example</span></span>  
 <span data-ttu-id="97c36-127">Aşağıdaki örnekte, izleme anahtarını `General` <xref:System.Diagnostics.TraceLevel> düzeye ayarlamak ve Boolean izleme `Data` anahtarını \*\* \<\*\* etkinleştirmek için anahtar>öğesinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="97c36-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97c36-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97c36-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="97c36-129">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="97c36-129">Trace and Debug Settings Schema</span></span>](index.md)
