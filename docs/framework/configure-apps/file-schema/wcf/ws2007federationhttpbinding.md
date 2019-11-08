---
title: <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 0a5090166efd90efa7537f87d5fa47b8c9d078cb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735762"
---
# <a name="ws2007federationhttpbinding"></a><span data-ttu-id="d0bad-101">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d0bad-101">\<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="d0bad-102">[\<> WSFederationHttpBinding](wsfederationhttpbinding.md) ' den türetilen ve federe güvenliği destekleyen güvenli ve birlikte çalışabilen bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="d0bad-102">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) and supports federated security.</span></span>

<span data-ttu-id="d0bad-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d0bad-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d0bad-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="d0bad-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d0bad-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d0bad-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d0bad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ws2007FederationHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="d0bad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ws2007FederationHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0bad-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0bad-107">Syntax</span></span>

```xml
<ws2007FederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007FederationHttpBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0bad-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0bad-108">Attributes and Elements</span></span>

<span data-ttu-id="d0bad-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d0bad-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0bad-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d0bad-110">Attributes</span></span>

|<span data-ttu-id="d0bad-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d0bad-111">Attribute</span></span>|<span data-ttu-id="d0bad-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0bad-112">Description</span></span>|
|---------------|-----------------|
|`bypassProxyOnLocal`|<span data-ttu-id="d0bad-113">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d0bad-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="d0bad-114">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-114">The default is `false`.</span></span>|
|`closeTimeout`|<span data-ttu-id="d0bad-115">Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="d0bad-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d0bad-116">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0bad-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d0bad-117">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-117">The default is 00:01:00.</span></span>|
|`hostNameComparisonMode`|<span data-ttu-id="d0bad-118">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="d0bad-119">Bu öznitelik, ana bilgisayar adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını belirten <xref:System.ServiceModel.HostNameComparisonMode>türüdür.</span><span class="sxs-lookup"><span data-stu-id="d0bad-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="d0bad-120">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>. Bu, eşleşbir ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="d0bad-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|
|`maxBufferPoolSize`|<span data-ttu-id="d0bad-121">Bu bağlama için en büyük arabellek havuzu boyutu.</span><span class="sxs-lookup"><span data-stu-id="d0bad-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="d0bad-122">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="d0bad-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="d0bad-123">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0bad-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="d0bad-124">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0bad-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="d0bad-125">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0bad-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="d0bad-126">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="d0bad-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|
|`maxReceivedMessageSize`|<span data-ttu-id="d0bad-127">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutu.</span><span class="sxs-lookup"><span data-stu-id="d0bad-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="d0bad-128">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="d0bad-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="d0bad-129">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d0bad-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="d0bad-130">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-130">The default is 65536.</span></span>|
|`messageEncoding`|<span data-ttu-id="d0bad-131">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0bad-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="d0bad-132">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d0bad-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d0bad-133">-Metin: bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0bad-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="d0bad-134">-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d0bad-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="d0bad-135">Varsayılan değer metindir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="d0bad-136">Bu öznitelik <xref:System.ServiceModel.WSMessageEncoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|
|`name`|<span data-ttu-id="d0bad-137">Bağlamanın yapılandırma adı.</span><span class="sxs-lookup"><span data-stu-id="d0bad-137">The configuration name of the binding.</span></span> <span data-ttu-id="d0bad-138">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0bad-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d0bad-139">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-139">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d0bad-140">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="d0bad-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|
|`openTimeout`|<span data-ttu-id="d0bad-141">Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="d0bad-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d0bad-142">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0bad-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d0bad-143">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-143">The default is 00:01:00.</span></span>|
|`privacyNoticeAt`|<span data-ttu-id="d0bad-144">Gizlilik bildiriminin bulunduğu URI.</span><span class="sxs-lookup"><span data-stu-id="d0bad-144">A URI at which the privacy notice is located.</span></span>|
|`privacyNoticeVersion`|<span data-ttu-id="d0bad-145">Geçerli gizlilik bildiriminin sürümü.</span><span class="sxs-lookup"><span data-stu-id="d0bad-145">The version of the current privacy notice.</span></span>|
|`proxyAddress`|<span data-ttu-id="d0bad-146">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="d0bad-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="d0bad-147">`useDefaultWebProxy` `true`, bu ayar `null`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0bad-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="d0bad-148">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-148">The default is `null`.</span></span>|
|`receiveTimeout`|<span data-ttu-id="d0bad-149">Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="d0bad-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d0bad-150">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0bad-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d0bad-151">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-151">The default is 00:10:00.</span></span>|
|`sendTimeout`|<span data-ttu-id="d0bad-152">Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="d0bad-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d0bad-153">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d0bad-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d0bad-154">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-154">The default is 00:01:00.</span></span>|
|`textEncoding`|<span data-ttu-id="d0bad-155">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d0bad-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="d0bad-156">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d0bad-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d0bad-157">-Bigendianunıcode: Unicode Big endian kodlaması.</span><span class="sxs-lookup"><span data-stu-id="d0bad-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="d0bad-158">-UNICODE: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="d0bad-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="d0bad-159">-UTF8:8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="d0bad-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="d0bad-160">Varsayılan değer UTF8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-160">The default is UTF8.</span></span> <span data-ttu-id="d0bad-161">Bu öznitelik <xref:System.Text.Encoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|
|`transactionFlow`|<span data-ttu-id="d0bad-162">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d0bad-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="d0bad-163">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-163">The default is `false`.</span></span>|
|`useDefaultWebProxy`|<span data-ttu-id="d0bad-164">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d0bad-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="d0bad-165">Bu öznitelik `true`, proxy adresi `null` olmalıdır (ayarlı değil).</span><span class="sxs-lookup"><span data-stu-id="d0bad-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="d0bad-166">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-166">The default is `true`.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d0bad-167">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0bad-167">Child Elements</span></span>

|<span data-ttu-id="d0bad-168">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0bad-168">Element</span></span>|<span data-ttu-id="d0bad-169">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0bad-169">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0bad-170">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d0bad-170">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="d0bad-171">İleti için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0bad-171">Defines the security settings for the message.</span></span> <span data-ttu-id="d0bad-172">Bu öğe <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|
|<span data-ttu-id="d0bad-173">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d0bad-173">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="d0bad-174">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0bad-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d0bad-175">Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|
|<span data-ttu-id="d0bad-176">[Reliableoturum > \<](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d0bad-176">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="d0bad-177">Kanal uç noktaları arasında güvenilir oturumların yapılıp yapılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d0bad-178">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d0bad-178">Parent Elements</span></span>

|<span data-ttu-id="d0bad-179">Öğe</span><span class="sxs-lookup"><span data-stu-id="d0bad-179">Element</span></span>|<span data-ttu-id="d0bad-180">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0bad-180">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0bad-181">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="d0bad-181">\<bindings></span></span>](bindings.md)|<span data-ttu-id="d0bad-182">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-182">This element holds a collection of standard and custom bindings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d0bad-183">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0bad-183">Remarks</span></span>

<span data-ttu-id="d0bad-184">Federasyon, kimlik doğrulama ve yetkilendirme için birden fazla kurumda kimlik paylaşma veya etki alanına güven verme olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="d0bad-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="d0bad-185">Kimlik gösterimini bir güven etki alanından diğerine eşlemek için WS-Trust protokolünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="d0bad-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="d0bad-186">Federasyon HTTP bağlama, SOAP güvenliğini ve karma mod güvenliğini destekler, ancak aktarım güvenliğini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d0bad-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="d0bad-187">Bu bağlama ile yapılandırılan hizmetlerin HTTP aktarımını kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0bad-187">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="d0bad-188">Daha fazla bilgi için bkz. [\<wsFederationHttpBinding >](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d0bad-188">For more information, see [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>

## <a name="example"></a><span data-ttu-id="d0bad-189">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0bad-189">Example</span></span>

```xml
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="d0bad-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0bad-190">See also</span></span>

- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="d0bad-191">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d0bad-191">\<wsFederationHttpBinding></span></span>](wsfederationhttpbinding.md)
- [<span data-ttu-id="d0bad-192">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d0bad-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d0bad-193">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d0bad-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d0bad-194">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d0bad-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d0bad-195">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="d0bad-195">\<binding></span></span>](bindings.md)
