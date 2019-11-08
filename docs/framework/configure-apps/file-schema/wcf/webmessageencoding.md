---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: 4aa87acaf9080959ba8b53e3ec3216314dc745b6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732587"
---
# <a name="webmessageencoding"></a><span data-ttu-id="5a38b-101">webMessageEncoding \<</span><span class="sxs-lookup"><span data-stu-id="5a38b-101">\<webMessageEncoding></span></span>
<span data-ttu-id="5a38b-102">Düz metin XML, JavaScript Nesne Gösterimi (JSON) ileti kodlamaları ve "ham" ikili içeriğin Windows Communication Foundation (WCF) bağlamasında kullanıldığı zaman okunmalarını ve yazılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5a38b-102">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
<span data-ttu-id="5a38b-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5a38b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a38b-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="5a38b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5a38b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5a38b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5a38b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5a38b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="5a38b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="5a38b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5a38b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="5a38b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a38b-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a38b-109">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a38b-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a38b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a38b-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5a38b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a38b-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5a38b-112">Attributes</span></span>  
  
|<span data-ttu-id="5a38b-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5a38b-113">Attribute</span></span>|<span data-ttu-id="5a38b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a38b-114">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="5a38b-115">Yeni okuyucu ayırmadan aynı anda okunabilecek ileti miktarı.</span><span class="sxs-lookup"><span data-stu-id="5a38b-115">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="5a38b-116">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="5a38b-117">Her iç kodlayıcıda (Text, JSON ve "RAW") her biri için varsayılan değer 64 okuyucudır.</span><span class="sxs-lookup"><span data-stu-id="5a38b-117">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="5a38b-118">Bu sayının artırılması, bellek tüketimini artırır, ancak yeni bir tane oluşturmak yerine zaten oluşturulmuş olan havuzdan okuyucuları kullanabildiğinden, Encoder 'ı gelen iletilerin ani patlayıcılarıyla uğraşmak üzere hazırlar.</span><span class="sxs-lookup"><span data-stu-id="5a38b-118">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="5a38b-119">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti miktarı.</span><span class="sxs-lookup"><span data-stu-id="5a38b-119">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="5a38b-120">Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="5a38b-121">Her iç kodlayıcıda (Text, JSON ve "RAW") her biri için varsayılan değer 16 yazıcıdır.</span><span class="sxs-lookup"><span data-stu-id="5a38b-121">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="5a38b-122">Bu sayının artırılması bellek tüketimini artırır, ancak yeni olanlar oluşturmak yerine zaten oluşturulan havuzdan yazarları kullanabilmesi nedeniyle kodlayıcıyı, giden iletilerin ani burdıklarıyla uğraşmak üzere hazırlar.</span><span class="sxs-lookup"><span data-stu-id="5a38b-122">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="5a38b-123">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-123">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="5a38b-124">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5a38b-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="5a38b-125">-Unicodefffebir kodlama: Unicode Big endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="5a38b-125">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="5a38b-126">-Utf16TextEncoding: Unicode kodlaması.</span><span class="sxs-lookup"><span data-stu-id="5a38b-126">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="5a38b-127">-Utf8TextEncoding: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="5a38b-127">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="5a38b-128">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-128">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="5a38b-129">Bu öznitelik <xref:System.Text.Encoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-129">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a38b-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a38b-130">Child Elements</span></span>  
  
|<span data-ttu-id="5a38b-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="5a38b-131">Element</span></span>|<span data-ttu-id="5a38b-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a38b-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a38b-133">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5a38b-133">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="5a38b-134">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5a38b-134">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="5a38b-135">Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-135">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a38b-136">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a38b-136">Parent Elements</span></span>  
  
|<span data-ttu-id="5a38b-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="5a38b-137">Element</span></span>|<span data-ttu-id="5a38b-138">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a38b-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a38b-139">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="5a38b-139">\<binding></span></span>](bindings.md)|<span data-ttu-id="5a38b-140">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5a38b-140">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a38b-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5a38b-141">Remarks</span></span>  
 <span data-ttu-id="5a38b-142">Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-142">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="5a38b-143">Kod çözme işlemi ters işlemdir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-143">Decoding is the reverse process.</span></span> <span data-ttu-id="5a38b-144">Bu süreçler bir karakter kodlamasının belirtimini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-144">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="5a38b-145">`webMessageEncoding` öğesi, düz metin XML ve JSON kodlamaları ve "ham" ikili verileri işlemek için bir dizi iç kodlayıcıya temsilci seçerek işe yarar.</span><span class="sxs-lookup"><span data-stu-id="5a38b-145">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="5a38b-146">Bu temsili bir bileşik ileti Kodlayıcısı tarafından yapılır.</span><span class="sxs-lookup"><span data-stu-id="5a38b-146">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="5a38b-147">Bu bağlama öğesi ve onun bileşik Kodlayıcı, `webHttpBinding` öğesi tarafından kullanılan SOAP mesajlaşma kullanmayan senaryolarda kodlamayı denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a38b-147">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="5a38b-148">Bu senaryolar "düz eski XML" (POX), temsili durum aktarımı (REST), gerçekten basit dağıtım (RSS) ve Atom dağıtımı ve zaman uyumsuz JavaScript ve XML (AJAX) içerir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-148">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="5a38b-149">Bileşik ileti Kodlayıcısı SOAP veya WS-Addressing desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5a38b-149">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="5a38b-150">Binding öğesi `writeEncoding` özniteliği kullanılarak bir yazma karakteri kodlaması ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-150">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="5a38b-151">Sağlanan <xref:System.Text.Encoding> değeri, JSON ve metin XML durumları için yazma davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-151">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="5a38b-152">Okuma sırasında, herhangi bir geçerli ileti kodlaması ve metin kodlaması anlaşılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5a38b-152">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="5a38b-153">`maxReadPoolSize` ve `maxWritePoolSize`, sırasıyla ayrılacak en fazla okuyucu ve yazıcı sayısını ayarlamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5a38b-153">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="5a38b-154">Varsayılan olarak 64 okuyucular ve 16 yazıcı ayrılır.</span><span class="sxs-lookup"><span data-stu-id="5a38b-154">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="5a38b-155">Varsayılan Karmaşıklık kısıtlamaları Ayrıca, uç nokta işleme kaynaklarını bağlamak üzere ileti karmaşıklığı kullanmayı deneyen bir hizmet reddi (DOS) saldırısı sınıfına karşı korumak için [\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) öğesi kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5a38b-155">Default complexity constraints are also set using the [\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a38b-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a38b-156">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="5a38b-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a38b-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="5a38b-158">İleti Kodlama</span><span class="sxs-lookup"><span data-stu-id="5a38b-158">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="5a38b-159">İleti Kodlayıcı Seçme</span><span class="sxs-lookup"><span data-stu-id="5a38b-159">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="5a38b-160">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5a38b-160">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5a38b-161">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="5a38b-161">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5a38b-162">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5a38b-162">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5a38b-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="5a38b-163">\<customBinding></span></span>](custombinding.md)
