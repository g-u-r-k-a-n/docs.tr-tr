---
description: 'Daha fazla bilgi edinin: <publisherPolicy> öğesi'
title: <publisherPolicy> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
ms.openlocfilehash: 35d729d5b195e010a80e7272312f14ac5802001b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802448"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="09e7b-103">\<publisherPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="09e7b-103">\<publisherPolicy> Element</span></span>

<span data-ttu-id="09e7b-104">Çalışma zamanının yayımcı ilkesi uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="09e7b-104">Specifies whether the runtime applies publisher policy.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="09e7b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="09e7b-105">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09e7b-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="09e7b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="09e7b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="09e7b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09e7b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="09e7b-108">Attributes</span></span>  
  
|<span data-ttu-id="09e7b-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="09e7b-109">Attribute</span></span>|<span data-ttu-id="09e7b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09e7b-110">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="09e7b-111">Yayımcı ilkesinin uygulanıp uygulanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="09e7b-111">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="09e7b-112">Özniteliği Uygula</span><span class="sxs-lookup"><span data-stu-id="09e7b-112">apply Attribute</span></span>  
  
|<span data-ttu-id="09e7b-113">Değer</span><span class="sxs-lookup"><span data-stu-id="09e7b-113">Value</span></span>|<span data-ttu-id="09e7b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09e7b-114">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="09e7b-115">Yayımcı ilkesini uygular.</span><span class="sxs-lookup"><span data-stu-id="09e7b-115">Applies publisher policy.</span></span> <span data-ttu-id="09e7b-116">Bu varsayılan ayardır.</span><span class="sxs-lookup"><span data-stu-id="09e7b-116">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="09e7b-117">Yayımcı ilkesi uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="09e7b-117">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09e7b-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="09e7b-118">Child Elements</span></span>  

<span data-ttu-id="09e7b-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="09e7b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09e7b-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="09e7b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="09e7b-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="09e7b-121">Element</span></span>|<span data-ttu-id="09e7b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09e7b-122">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="09e7b-123">Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="09e7b-123">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="09e7b-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="09e7b-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="09e7b-125">Her bir derleme için bağlama ilkesi ve derleme konumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="09e7b-125">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="09e7b-126">`<dependentAssembly>`Her derleme için bir öğe kullanın.</span><span class="sxs-lookup"><span data-stu-id="09e7b-126">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="09e7b-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="09e7b-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09e7b-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09e7b-128">Remarks</span></span>  

 <span data-ttu-id="09e7b-129">Bir bileşen satıcısı bir derlemenin yeni bir sürümünü yayımlarsa, satıcı bir yayımcı ilkesi içerebilir, bu nedenle eski sürümü kullanan uygulamalar artık yeni sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="09e7b-129">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="09e7b-130">Belirli bir derleme için yayımcı ilkesinin uygulanıp uygulanmayacağını belirtmek için öğesini öğesine koyun **\<publisherPolicy>** **\<dependentAssembly>** .</span><span class="sxs-lookup"><span data-stu-id="09e7b-130">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="09e7b-131">**Apply** özniteliği için varsayılan ayar **Evet**' tir.</span><span class="sxs-lookup"><span data-stu-id="09e7b-131">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="09e7b-132">**Apply** özniteliğini **Hayır** olarak ayarlamak, bir derleme için önceki tüm **Evet** ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="09e7b-132">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="09e7b-133">Uygulamanın, [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) uygulama yapılandırma dosyasındaki öğesini kullanarak yayımcı ilkesini açıkça yoksayması için izin gerekir.</span><span class="sxs-lookup"><span data-stu-id="09e7b-133">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="09e7b-134"><xref:System.Security.Permissions.SecurityPermissionFlag>' De bayrak ayarlanarak izin verilir <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="09e7b-134">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="09e7b-135">Daha fazla bilgi için bkz. [derleme bağlama yeniden yönlendirme güvenlik izni](../../assembly-binding-redirection-security-permission.md).</span><span class="sxs-lookup"><span data-stu-id="09e7b-135">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09e7b-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="09e7b-136">Example</span></span>  

 <span data-ttu-id="09e7b-137">Aşağıdaki örnek, derleme için yayımcı ilkesini devre dışı bırakır `myAssembly` .</span><span class="sxs-lookup"><span data-stu-id="09e7b-137">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09e7b-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09e7b-138">See also</span></span>

- [<span data-ttu-id="09e7b-139">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="09e7b-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="09e7b-140">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="09e7b-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="09e7b-141">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="09e7b-141">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="09e7b-142">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="09e7b-142">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
