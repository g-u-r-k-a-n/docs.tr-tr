---
title: <GenericParameter> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf2b06b14252f152c1eece6f9c0d317482a24b27
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039509"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="2a38d-102">\<GenericParameter > öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="2a38d-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="2a38d-103">İlkeyi genel bir türün veya yöntemin parametre türüne uygular.</span><span class="sxs-lookup"><span data-stu-id="2a38d-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a38d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a38d-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a38d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a38d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2a38d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a38d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a38d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2a38d-107">Attributes</span></span>  
  
|<span data-ttu-id="2a38d-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2a38d-108">Attribute</span></span>|<span data-ttu-id="2a38d-109">Öznitelik türü</span><span class="sxs-lookup"><span data-stu-id="2a38d-109">Attribute type</span></span>|<span data-ttu-id="2a38d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a38d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="2a38d-111">Genel</span><span class="sxs-lookup"><span data-stu-id="2a38d-111">General</span></span>|<span data-ttu-id="2a38d-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a38d-112">Required attribute.</span></span> <span data-ttu-id="2a38d-113">Genel parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="2a38d-113">The name of the generic parameter.</span></span> <span data-ttu-id="2a38d-114">Örneğin, genel temsilci <xref:System.Func%603>için, `Name` özniteliğinin değeri "TResult" olur ve çalışma zamanı ilkesini temsilcinin dönüş değerine uygular.</span><span class="sxs-lookup"><span data-stu-id="2a38d-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="2a38d-115">Yansıma</span><span class="sxs-lookup"><span data-stu-id="2a38d-115">Reflection</span></span>|<span data-ttu-id="2a38d-116">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a38d-116">Optional attribute.</span></span> <span data-ttu-id="2a38d-117">Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="2a38d-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="2a38d-118">Yansıma</span><span class="sxs-lookup"><span data-stu-id="2a38d-118">Reflection</span></span>|<span data-ttu-id="2a38d-119">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a38d-119">Optional attribute.</span></span> <span data-ttu-id="2a38d-120">Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="2a38d-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="2a38d-121">Yansıma</span><span class="sxs-lookup"><span data-stu-id="2a38d-121">Reflection</span></span>|<span data-ttu-id="2a38d-122">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a38d-122">Optional attribute.</span></span> <span data-ttu-id="2a38d-123">Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="2a38d-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="2a38d-124">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2a38d-124">Serialization</span></span>|<span data-ttu-id="2a38d-125">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a38d-125">Optional attribute.</span></span> <span data-ttu-id="2a38d-126">Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.</span><span class="sxs-lookup"><span data-stu-id="2a38d-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="2a38d-127">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2a38d-127">Serialization</span></span>|<span data-ttu-id="2a38d-128">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a38d-128">Optional attribute.</span></span> <span data-ttu-id="2a38d-129"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="2a38d-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="2a38d-130">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2a38d-130">Serialization</span></span>|<span data-ttu-id="2a38d-131">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a38d-131">Optional attribute.</span></span> <span data-ttu-id="2a38d-132"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfını kullanan JSON serileştirme için ilkeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="2a38d-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="2a38d-133">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="2a38d-133">Serialization</span></span>|<span data-ttu-id="2a38d-134">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a38d-134">Optional attribute.</span></span> <span data-ttu-id="2a38d-135"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfını kullanan XML serileştirme ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="2a38d-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="2a38d-136">Interop</span><span class="sxs-lookup"><span data-stu-id="2a38d-136">Interop</span></span>|<span data-ttu-id="2a38d-137">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a38d-137">Optional attribute.</span></span> <span data-ttu-id="2a38d-138">Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="2a38d-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="2a38d-139">Interop</span><span class="sxs-lookup"><span data-stu-id="2a38d-139">Interop</span></span>|<span data-ttu-id="2a38d-140">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a38d-140">Optional attribute.</span></span> <span data-ttu-id="2a38d-141">Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="2a38d-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="2a38d-142">Interop</span><span class="sxs-lookup"><span data-stu-id="2a38d-142">Interop</span></span>|<span data-ttu-id="2a38d-143">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a38d-143">Optional attribute.</span></span> <span data-ttu-id="2a38d-144">Değer türlerini yerel koda hazırlama ilkesini denetler.</span><span class="sxs-lookup"><span data-stu-id="2a38d-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="2a38d-145">Ad özniteliği</span><span class="sxs-lookup"><span data-stu-id="2a38d-145">Name attribute</span></span>  
  
|<span data-ttu-id="2a38d-146">Değer</span><span class="sxs-lookup"><span data-stu-id="2a38d-146">Value</span></span>|<span data-ttu-id="2a38d-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a38d-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a38d-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="2a38d-148">*generic_parameter_name*</span></span>|<span data-ttu-id="2a38d-149">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2a38d-149">Required attribute.</span></span> <span data-ttu-id="2a38d-150">Genel tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="2a38d-150">The name of the generic type parameter.</span></span> <span data-ttu-id="2a38d-151">Örneğin, genel temsilci <xref:System.Func%603>için, "TResult" *generic_parameter_name* değeri, temsilcinin dönüş değerine çalışma zamanı ilkesi uygular.</span><span class="sxs-lookup"><span data-stu-id="2a38d-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="2a38d-152">Diğer tüm öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2a38d-152">All other attributes</span></span>  
  
|<span data-ttu-id="2a38d-153">Değer</span><span class="sxs-lookup"><span data-stu-id="2a38d-153">Value</span></span>|<span data-ttu-id="2a38d-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a38d-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a38d-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="2a38d-155">*policy_setting*</span></span>|<span data-ttu-id="2a38d-156">Bu ilke türüne uygulanacak ayar.</span><span class="sxs-lookup"><span data-stu-id="2a38d-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="2a38d-157">Olası değerler şunlardır `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`ve `Required All`.</span><span class="sxs-lookup"><span data-stu-id="2a38d-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="2a38d-158">Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="2a38d-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a38d-159">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a38d-159">Child Elements</span></span>  
 <span data-ttu-id="2a38d-160">Yok.</span><span class="sxs-lookup"><span data-stu-id="2a38d-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a38d-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2a38d-161">Parent Elements</span></span>  
  
|<span data-ttu-id="2a38d-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="2a38d-162">Element</span></span>|<span data-ttu-id="2a38d-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a38d-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a38d-164">\<yöntemi ></span><span class="sxs-lookup"><span data-stu-id="2a38d-164">\<Method></span></span>](method-element-net-native.md)|<span data-ttu-id="2a38d-165">Çalışma zamanı yansıtma ilkesini bir oluşturucuya veya yöntemine uygular.</span><span class="sxs-lookup"><span data-stu-id="2a38d-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="2a38d-166">\<türü ></span><span class="sxs-lookup"><span data-stu-id="2a38d-166">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="2a38d-167">Çalışma zamanı yansıma ilkesini sınıf veya yapı gibi belirli bir türe uygular.</span><span class="sxs-lookup"><span data-stu-id="2a38d-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a38d-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a38d-168">Remarks</span></span>  
 <span data-ttu-id="2a38d-169">`<GenericParameter>` öğesi [\<yöntemi >](method-element-net-native.md) ya da [\<Type >](type-element-net-native.md) öğesinin bir alt öğesidir ve ilkeyi genel tür veya yöntem imzasında adıyla belirtilen belirli bir genel tür parametresine uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2a38d-169">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="2a38d-170">`<GenericParameter>` öğesi, serileştiriciler ile birlikte kullanıldığında en yararlı seçenektir.</span><span class="sxs-lookup"><span data-stu-id="2a38d-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="2a38d-171">Aşağıdaki örnek, NewtonSoft JSON serileştiricinin [JsonConvert. DeserializeObject\<t > (dize)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) yöntem aşırı yüklerini çağırarak `T` türüne ilke uygulamak için `<GenericParameter>` öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a38d-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a38d-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a38d-172">See also</span></span>

- [<span data-ttu-id="2a38d-173">\<yöntemi > öğesi</span><span class="sxs-lookup"><span data-stu-id="2a38d-173">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="2a38d-174">\<türü > öğesi</span><span class="sxs-lookup"><span data-stu-id="2a38d-174">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="2a38d-175">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2a38d-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="2a38d-176">Çalışma Zamanı Yönerge İlkesi Ayarları</span><span class="sxs-lookup"><span data-stu-id="2a38d-176">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="2a38d-177">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="2a38d-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
