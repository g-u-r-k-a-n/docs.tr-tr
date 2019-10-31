---
title: <qualifyAssembly> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 17cfe9fc39d65f146beef5d02c701f5e3e2fbbe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115780"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="5c961-102">\<qualifyAssembly > öğesi</span><span class="sxs-lookup"><span data-stu-id="5c961-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="5c961-103">Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c961-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
<span data-ttu-id="5c961-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5c961-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5c961-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="5c961-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5c961-106">&nbsp; &nbsp; &nbsp; &nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md) </span><span class="sxs-lookup"><span data-stu-id="5c961-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="5c961-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<qualifyAssembly >**</span><span class="sxs-lookup"><span data-stu-id="5c961-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c961-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c961-108">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c961-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c961-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5c961-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c961-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c961-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5c961-111">Attributes</span></span>  
  
|<span data-ttu-id="5c961-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5c961-112">Attribute</span></span>|<span data-ttu-id="5c961-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c961-113">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="5c961-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5c961-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="5c961-115">Kodda göründüğü gibi derlemenin kısmi adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c961-115">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="5c961-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5c961-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="5c961-117">Derlemenin genel derleme önbelleğinde göründüğü haliyle tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5c961-117">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c961-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c961-118">Child Elements</span></span>  
 <span data-ttu-id="5c961-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="5c961-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c961-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c961-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5c961-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c961-121">Element</span></span>|<span data-ttu-id="5c961-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c961-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="5c961-123">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5c961-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="5c961-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5c961-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5c961-125">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="5c961-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c961-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c961-126">Remarks</span></span>  
 <span data-ttu-id="5c961-127">Kısmi derleme adlarını kullanarak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yönteminin çağrılması, ortak dil çalışma zamanının derlemeyi yalnızca uygulama temel dizininde aramasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c961-127">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="5c961-128">Tüm derleme bilgilerini (ad, sürüm, ortak anahtar belirteci ve kültür) sağlamak için uygulama yapılandırma dosyanızda **\<qualifyAssembly >** öğesini kullanın ve ortak dil çalışma zamanının, derlemeyi küresel bir şekilde aramasına neden olur bütünleştirilmiş kod önbelleği.</span><span class="sxs-lookup"><span data-stu-id="5c961-128">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="5c961-129">**FullName** özniteliği, derleme kimliğinin dört alanını içermelidir: ad, sürüm, ortak anahtar belirteci ve kültür.</span><span class="sxs-lookup"><span data-stu-id="5c961-129">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="5c961-130">**PartialName** özniteliği kısmen bir derlemeye başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c961-130">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="5c961-131">En azından derlemenin metin adını (en yaygın durum) belirtmeniz gerekir, ancak sürüm, ortak anahtar belirteci veya kültürü (ya da dört ' un herhangi bir birleşimini değil) dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c961-131">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="5c961-132">**PartialName** , çağrın içinde belirtilen ad ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c961-132">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="5c961-133">Örneğin, yapılandırma dosyanızda **partialName** özniteliği olarak `"math"` belirtemezsiniz ve kodunuzda `Assembly.Load("math, Version=3.3.3.3")` çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c961-133">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c961-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c961-134">Example</span></span>  
 <span data-ttu-id="5c961-135">Aşağıdaki örnek, `Assembly.Load("math")` çağrı `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`mantıksal olarak etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="5c961-135">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c961-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c961-136">See also</span></span>

- [<span data-ttu-id="5c961-137">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5c961-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5c961-138">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="5c961-138">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="5c961-139">[Kısmi derleme başvuruları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5c961-139">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
