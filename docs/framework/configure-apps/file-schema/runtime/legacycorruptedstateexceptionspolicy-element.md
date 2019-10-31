---
title: <legacyCorruptedStateExceptionsPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: d1d29a37999a01f3e370897a1052f4f94435a218
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116452"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="71f1c-102">\<Legacybozulmuş Tedstateexceptionspolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="71f1c-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="71f1c-103">Ortak dil çalışma zamanının yönetilen kodun erişim ihlallerini ve diğer bozuk durum özel durumlarını yakalayıp belirlemesine izin verip içermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="71f1c-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
<span data-ttu-id="71f1c-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="71f1c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="71f1c-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="71f1c-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="71f1c-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Legacybozulmuş Tedstateexceptionspolicy >**</span><span class="sxs-lookup"><span data-stu-id="71f1c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f1c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71f1c-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71f1c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="71f1c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="71f1c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71f1c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71f1c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="71f1c-110">Attributes</span></span>  
  
|<span data-ttu-id="71f1c-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="71f1c-111">Attribute</span></span>|<span data-ttu-id="71f1c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71f1c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="71f1c-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="71f1c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="71f1c-114">Uygulamanın erişim ihlalleri gibi bozulmaları durum özel durum başarısızlıklarını yakalayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="71f1c-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="71f1c-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="71f1c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="71f1c-116">Değer</span><span class="sxs-lookup"><span data-stu-id="71f1c-116">Value</span></span>|<span data-ttu-id="71f1c-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71f1c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="71f1c-118">Uygulama, erişim ihlalleri gibi bozulmayan durum özel durum başarısızlıklarını yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="71f1c-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="71f1c-119">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="71f1c-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="71f1c-120">Uygulama, erişim ihlalleri gibi bozulmaları durum özel durum başarısızlıklarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="71f1c-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71f1c-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="71f1c-121">Child Elements</span></span>  
 <span data-ttu-id="71f1c-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="71f1c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71f1c-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="71f1c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="71f1c-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="71f1c-124">Element</span></span>|<span data-ttu-id="71f1c-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71f1c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="71f1c-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="71f1c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="71f1c-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="71f1c-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71f1c-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71f1c-128">Remarks</span></span>  
 <span data-ttu-id="71f1c-129">.NET Framework sürüm 3,5 ve önceki sürümlerde, ortak dil çalışma zamanının bozuk işlem durumları tarafından oluşturulan özel durumları yakalayabileceği yönetilen koda izin verilir.</span><span class="sxs-lookup"><span data-stu-id="71f1c-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="71f1c-130">Erişim ihlali, bu tür bir özel durum örneğidir.</span><span class="sxs-lookup"><span data-stu-id="71f1c-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="71f1c-131">.NET Framework 4 ' te başlayarak, yönetilen kod artık `catch` bloklardaki bu tür özel durumları yakalamayacaktır.</span><span class="sxs-lookup"><span data-stu-id="71f1c-131">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="71f1c-132">Ancak, bu değişikliği geçersiz kılabilir ve bozulmuş durum istisnalarını iki şekilde işleme devam edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="71f1c-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="71f1c-133">`<legacyCorruptedStateExceptionsPolicy>` öğenin `enabled` özniteliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="71f1c-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="71f1c-134">Bu yapılandırma ayarı, processwide uygulanır ve tüm yöntemleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="71f1c-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="71f1c-135">veya</span><span class="sxs-lookup"><span data-stu-id="71f1c-135">-or-</span></span>  
  
- <span data-ttu-id="71f1c-136"><xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> özniteliğini, özel durumları `catch` bloğunu içeren yönteme uygulayın.</span><span class="sxs-lookup"><span data-stu-id="71f1c-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="71f1c-137">Bu yapılandırma öğesi yalnızca .NET Framework 4 ve üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71f1c-137">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71f1c-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="71f1c-138">Example</span></span>  
 <span data-ttu-id="71f1c-139">Aşağıdaki örnek, uygulamanın .NET Framework 4 ' den önceki davranışa ne şekilde dönmesi gerektiğini belirtir ve tüm bozulmalı durum özel durum başarısızlıklarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="71f1c-139">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="71f1c-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71f1c-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="71f1c-141">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="71f1c-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="71f1c-142">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="71f1c-142">Configuration File Schema</span></span>](../index.md)
