---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: afe0479d9cbf6d754b309c18e23d3a479870177c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739076"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="a9fa4-101">binaryMessageEncoding \<</span><span class="sxs-lookup"><span data-stu-id="a9fa4-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="a9fa4-102">Tel Windows Communication Foundation (WCF) iletilerini kodlayan bir ikili ileti Kodlayıcısı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
<span data-ttu-id="a9fa4-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a9fa4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a9fa4-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="a9fa4-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a9fa4-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="a9fa4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="a9fa4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="a9fa4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="a9fa4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="a9fa4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="a9fa4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<binaryMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="a9fa4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9fa4-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9fa4-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9fa4-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9fa4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a9fa4-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9fa4-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a9fa4-112">Attributes</span></span>  
  
|<span data-ttu-id="a9fa4-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a9fa4-113">Attribute</span></span>|<span data-ttu-id="a9fa4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9fa4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a9fa4-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="a9fa4-115">maxReadPoolSize</span></span>|<span data-ttu-id="a9fa4-116">Yeni okuyucular ayırmadan aynı anda okunabilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="a9fa4-117">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a9fa4-118">Varsayılan değer 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-118">The default is 64.</span></span>|  
|<span data-ttu-id="a9fa4-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="a9fa4-119">maxSessionSize</span></span>|<span data-ttu-id="a9fa4-120">Kodlama için kullanılan arabelleğin bayt cinsinden boyutunu ayarlayan pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="a9fa4-121">Daha büyük bir arabellek, çalışma kümesinin boyutunun masrafına göre kodlama hızını artırır.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="a9fa4-122">Varsayılan değer 2048 ' dir.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-122">The default is 2048.</span></span>|  
|<span data-ttu-id="a9fa4-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="a9fa4-123">maxWritePoolSize</span></span>|<span data-ttu-id="a9fa4-124">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="a9fa4-125">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="a9fa4-126">Varsayılan değer 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-126">The default is 16.</span></span>|  
|<span data-ttu-id="a9fa4-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="a9fa4-127">messageVersion</span></span>|<span data-ttu-id="a9fa4-128">Kullanılan veya beklenen SOAP iletisini ve WS-Addressing sürümlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9fa4-129">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9fa4-129">Child Elements</span></span>  
  
|<span data-ttu-id="a9fa4-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9fa4-130">Element</span></span>|<span data-ttu-id="a9fa4-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9fa4-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9fa4-132">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9fa4-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="a9fa4-133">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a9fa4-134">Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9fa4-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a9fa4-135">Parent Elements</span></span>  
  
|<span data-ttu-id="a9fa4-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="a9fa4-136">Element</span></span>|<span data-ttu-id="a9fa4-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9fa4-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9fa4-138">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="a9fa4-138">\<binding></span></span>](bindings.md)|<span data-ttu-id="a9fa4-139">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9fa4-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9fa4-140">Remarks</span></span>  
 <span data-ttu-id="a9fa4-141">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="a9fa4-142">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-142">Decoding is the reverse process.</span></span> <span data-ttu-id="a9fa4-143">Windows Communication Foundation (WCF), SOAP iletileri için üç tür kodlama içerir: metin, Ikili ve Ileti Iletimi Iyileştirme mekanizması (MTOM).</span><span class="sxs-lookup"><span data-stu-id="a9fa4-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="a9fa4-144">`binaryMessageEncoding` öğesi, XML için .NET Ikili biçimini belirtir ve karakter kodlamasını ve kullanılacak SOAP ve WS-Addressing sürümünü belirtmek için seçeneklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="a9fa4-145">İkili ileti Kodlayıcısı, Windows Communication Foundation (WCF) iletilerini kablo üzerinde ikili olarak kodlar.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="a9fa4-146">Bu kodlama, iletilerin çok hızlı aktarılmasına neden olsa da, WS-\* standartlarına dayalı olarak birlikte çalışabilirlik kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9fa4-147">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9fa4-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="a9fa4-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9fa4-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="a9fa4-149">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="a9fa4-149">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="a9fa4-150">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="a9fa4-150">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="a9fa4-151">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a9fa4-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a9fa4-152">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="a9fa4-152">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a9fa4-153">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a9fa4-153">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a9fa4-154">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a9fa4-154">\<customBinding></span></span>](custombinding.md)
