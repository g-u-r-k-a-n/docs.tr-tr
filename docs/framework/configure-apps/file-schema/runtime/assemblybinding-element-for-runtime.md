---
title: <runtime> için <assemblyBinding> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154328"
---
# <a name="assemblybinding-element-for-runtime"></a><span data-ttu-id="53905-102">\<runtime> için \<assemblyBinding> Öğesi</span><span class="sxs-lookup"><span data-stu-id="53905-102">\<assemblyBinding> Element for \<runtime></span></span>
<span data-ttu-id="53905-103">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="53905-103">Contains information about assembly version redirection and the locations of assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="53905-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53905-104">Syntax</span></span>  
  
```xml  
      <assemblyBinding
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53905-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="53905-105">Attributes and Elements</span></span>  
 <span data-ttu-id="53905-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53905-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53905-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="53905-107">Attributes</span></span>  
  
|<span data-ttu-id="53905-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="53905-108">Attribute</span></span>|<span data-ttu-id="53905-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53905-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53905-110">**özniteliði**</span><span class="sxs-lookup"><span data-stu-id="53905-110">**xmlns**</span></span>|<span data-ttu-id="53905-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="53905-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="53905-112">Derleme bağlaması için gereken XML ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53905-112">Specifies the XML namespace required for assembly binding.</span></span> <span data-ttu-id="53905-113">Değer olarak "urn: schemas-microsoft-com: asm. v1" dizesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="53905-113">Use the string "urn:schemas-microsoft-com:asm.v1" as the value.</span></span>|  
|<span data-ttu-id="53905-114">**appliesTo**</span><span class="sxs-lookup"><span data-stu-id="53905-114">**appliesTo**</span></span>|<span data-ttu-id="53905-115">.NET Framework derleme yeniden yönlendirmenin uygulandığı çalışma zamanı sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="53905-115">Specifies the runtime version the .NET Framework assembly redirection applies to.</span></span> <span data-ttu-id="53905-116">Bu isteğe bağlı öznitelik, hangi sürümün uygulanacağını göstermek için .NET Framework bir sürüm numarası kullanır.</span><span class="sxs-lookup"><span data-stu-id="53905-116">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="53905-117">Hiçbir **AppliesTo** özniteliği belirtilmemişse, **\<assemblyBinding>** öğesi .NET Framework tüm sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="53905-117">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="53905-118">**AppliesTo** özniteliği .NET Framework sürüm 1,1 ' de tanıtılmıştı; .NET Framework 1,0 sürümü tarafından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="53905-118">The **appliesTo** attribute was introduced in .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="53905-119">Bu, **\<assemblyBinding>** bir **AppliesTo** özniteliği belirtilmiş olsa bile, .NET Framework sürüm 1,0 kullanılırken tüm öğelerin uygulandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="53905-119">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53905-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="53905-120">Child Elements</span></span>  
  
|<span data-ttu-id="53905-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="53905-121">Element</span></span>|<span data-ttu-id="53905-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53905-122">Description</span></span>|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|<span data-ttu-id="53905-123">Derleme için bağlama ilkesini ve derleme konumunu kapsüller.</span><span class="sxs-lookup"><span data-stu-id="53905-123">Encapsulates binding policy and assembly location for an assembly.</span></span> <span data-ttu-id="53905-124">**\<dependentAssembly>** Her derleme için bir etiket kullanın.</span><span class="sxs-lookup"><span data-stu-id="53905-124">Use one **\<dependentAssembly>** tag for each assembly.</span></span>|  
|[\<probing>](probing-element.md)|<span data-ttu-id="53905-125">Derlemeler yüklenirken ortak dil çalışma zamanı aramalarının alt dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53905-125">Specifies subdirectories the common language runtime searches when loading assemblies.</span></span>|  
|[\<publisherPolicy>](publisherpolicy-element.md)|<span data-ttu-id="53905-126">Çalışma zamanının yayımcı ilkesi uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53905-126">Specifies whether the runtime applies publisher policy.</span></span>|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|<span data-ttu-id="53905-127">Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53905-127">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53905-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="53905-128">Parent Elements</span></span>  
  
|<span data-ttu-id="53905-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="53905-129">Element</span></span>|<span data-ttu-id="53905-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53905-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="53905-131">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="53905-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="53905-132">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="53905-132">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="53905-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="53905-133">Example</span></span>  
 <span data-ttu-id="53905-134">Aşağıdaki örnek, bir derleme sürümünün diğerine nasıl yeniden yönlendirileceğini ve bir kod temeli nasıl sağlayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="53905-134">The following example shows how to redirect one assembly version to another and provide a codebase.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="53905-135">Aşağıdaki örnek, bir .NET Framework derlemesinin bağlamasını yeniden yönlendirmek için **AppliesTo** özniteliğini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="53905-135">The following example shows how to use the **appliesTo** attribute to redirect binding of a .NET Framework assembly.</span></span>  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="53905-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53905-136">See also</span></span>

- [<span data-ttu-id="53905-137">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="53905-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="53905-138">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="53905-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="53905-139">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="53905-139">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
