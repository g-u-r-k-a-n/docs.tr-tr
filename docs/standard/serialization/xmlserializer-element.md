---
title: <xmlSerializer> Öğesi
description: <xmlSerializer>Öğesi XmlSerializer 'ın ilerleme durumunun gerçekleştirilip yapılmadığını belirtir.
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 68037959893ec307a896ea86d21e40a9d7aa824c
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380028"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="98a1a-103">\<xmlSerializer> öğesi</span><span class="sxs-lookup"><span data-stu-id="98a1a-103">\<xmlSerializer> Element</span></span>
<span data-ttu-id="98a1a-104">Belirtir ilerleme durumunu ek bir denetim olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> yapılır.</span><span class="sxs-lookup"><span data-stu-id="98a1a-104">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="98a1a-105">\<yapılandırma></span><span class="sxs-lookup"><span data-stu-id="98a1a-105">\<configuration></span></span>  
<span data-ttu-id="98a1a-106">\<System. xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="98a1a-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a1a-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98a1a-107">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98a1a-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="98a1a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="98a1a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="98a1a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98a1a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="98a1a-110">Attributes</span></span>  
  
|<span data-ttu-id="98a1a-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="98a1a-111">Attribute</span></span>|<span data-ttu-id="98a1a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a1a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98a1a-113">**Checkdeserializeavanslar**</span><span class="sxs-lookup"><span data-stu-id="98a1a-113">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="98a1a-114">Belirtir olup olmadığını ilerleme durumunu <xref:System.Xml.Serialization.XmlSerializer> denetlenir.</span><span class="sxs-lookup"><span data-stu-id="98a1a-114">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="98a1a-115">Özniteliği "true" veya "false" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="98a1a-115">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="98a1a-116">Varsayılan değer "true" dır.</span><span class="sxs-lookup"><span data-stu-id="98a1a-116">The default is "true".</span></span>|  
|<span data-ttu-id="98a1a-117">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="98a1a-117">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="98a1a-118">Belirtir olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> C# kod bir dosyaya yazmak ve sonra da bir derlemeye derlemek tarafından derlemeleri oluşturan eski serileştirme oluşturma kullanır.</span><span class="sxs-lookup"><span data-stu-id="98a1a-118">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="98a1a-119">Varsayılan değer **false**'dur.</span><span class="sxs-lookup"><span data-stu-id="98a1a-119">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98a1a-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="98a1a-120">Child Elements</span></span>  
 <span data-ttu-id="98a1a-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="98a1a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98a1a-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="98a1a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="98a1a-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="98a1a-123">Element</span></span>|<span data-ttu-id="98a1a-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a1a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98a1a-125">\<System. xml. Serialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="98a1a-125">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="98a1a-126">İçin yapılandırma ayarlarını içeren <xref:System.Xml.Serialization.XmlSerializer> ve <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="98a1a-126">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98a1a-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98a1a-127">Remarks</span></span>  
 <span data-ttu-id="98a1a-128">Varsayılan olarak, <xref:System.Xml.Serialization.XmlSerializer> Güvenilmeyen verilerin serisi kaldırılırken olası hizmet reddi saldırılarına karşı ek bir güvenlik katmanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="98a1a-128">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="98a1a-129">Bunu seri durumundan çıkarma sırasında sonsuz döngü algılamak deneyerek yapar.</span><span class="sxs-lookup"><span data-stu-id="98a1a-129">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="98a1a-130">Böyle bir koşul algılanırsa, şu iletiyle bir özel durum oluşturulur: "Iç hata: seri kaldırma, temel alınan akışın üzerinde ilerleyemedi."</span><span class="sxs-lookup"><span data-stu-id="98a1a-130">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="98a1a-131">Bu iletiyi alan değil gerekmeyen gösteren bir saldırı hizmet reddi devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="98a1a-131">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="98a1a-132">Bazı ender durumlarda, yanlış Pozitif sonsuz döngü algılama mekanizması oluşturur ve yasal gelen ileti için özel durum.</span><span class="sxs-lookup"><span data-stu-id="98a1a-132">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="98a1a-133">Özel uygulamanızda bu ek koruma katmanı tarafından meşru iletiler reddedilmekte olduğunu fark ederseniz **Checkdeserializeavanslar** özniteliğini "false" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="98a1a-133">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="98a1a-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="98a1a-134">Example</span></span>  
 <span data-ttu-id="98a1a-135">Aşağıdaki kod örneği **Checkdeserializeavanslar** özniteliğini "false" olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98a1a-135">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="98a1a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98a1a-136">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="98a1a-137">\<System. xml. Serialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="98a1a-137">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="98a1a-138">XML ve SOAP serileştirme</span><span class="sxs-lookup"><span data-stu-id="98a1a-138">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
