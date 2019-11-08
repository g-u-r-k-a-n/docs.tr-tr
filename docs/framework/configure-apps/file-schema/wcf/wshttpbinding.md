---
title: <wsHttpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- wsHttpBinding Element
ms.assetid: 0eee8ced-ad68-427d-b95a-97260e98deed
ms.openlocfilehash: 33c1d8ed0240d737f2b5f56b889cc2f31d88d018
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735620"
---
# <a name="wshttpbinding"></a><span data-ttu-id="beab9-101">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="beab9-101">\<wsHttpBinding></span></span>
<span data-ttu-id="beab9-102">Çift yönlü olmayan hizmet sözleşmeleri için uygun olan güvenli, güvenilir, birlikte çalışabilen bir bağlama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="beab9-102">Defines a secure, reliable, interoperable binding suitable for non-duplex service contracts.</span></span> <span data-ttu-id="beab9-103">Bağlama aşağıdaki belirtimleri uygular: güvenilirlik için WS-güvenilir mesajlaşma ve ileti güvenliği ve kimlik doğrulaması için WS-Security.</span><span class="sxs-lookup"><span data-stu-id="beab9-103">The binding implements the following specifications: WS-Reliable Messaging for reliability, and WS-Security for message security and authentication.</span></span> <span data-ttu-id="beab9-104">Aktarım HTTP ve ileti kodlama metin/XML kodlanıyor.</span><span class="sxs-lookup"><span data-stu-id="beab9-104">The transport is HTTP, and message encoding is Text/XML encoding.</span></span>  
  
<span data-ttu-id="beab9-105">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="beab9-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="beab9-106">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="beab9-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="beab9-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="beab9-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="beab9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wsHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="beab9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beab9-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="beab9-109">Syntax</span></span>  
  
```xml  
<wsHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</wsHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="beab9-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="beab9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="beab9-111">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="beab9-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="beab9-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="beab9-112">Attributes</span></span>  
  
|<span data-ttu-id="beab9-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="beab9-113">Attribute</span></span>|<span data-ttu-id="beab9-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="beab9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="beab9-115">allowCookies</span><span class="sxs-lookup"><span data-stu-id="beab9-115">allowCookies</span></span>|<span data-ttu-id="beab9-116">İstemcinin tanımlama bilgilerini kabul edip etmediğini ve gelecekteki isteklere yayıp yaymadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="beab9-116">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="beab9-117">Varsayılan olarak yanlıştır.</span><span class="sxs-lookup"><span data-stu-id="beab9-117">The default is false.</span></span><br /><br /> <span data-ttu-id="beab9-118">Tanımlama bilgilerini kullanan ASMX Web hizmetleriyle etkileşim kurarken bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="beab9-118">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="beab9-119">Bu şekilde, sunucudan döndürülen tanımlama bilgilerinin, bu hizmet için gelecekteki tüm istemci isteklerine otomatik olarak kopyalandığından emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="beab9-119">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|<span data-ttu-id="beab9-120">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="beab9-120">bypassProxyOnLocal</span></span>|<span data-ttu-id="beab9-121">Yerel adresler için proxy sunucusunun atlanıp atlanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="beab9-121">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="beab9-122">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="beab9-122">The default is `false`.</span></span>|  
|<span data-ttu-id="beab9-123">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="beab9-123">closeTimeout</span></span>|<span data-ttu-id="beab9-124">Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="beab9-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="beab9-125">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="beab9-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="beab9-126">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="beab9-126">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="beab9-127">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="beab9-127">hostnameComparisonMode</span></span>|<span data-ttu-id="beab9-128">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="beab9-128">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="beab9-129">Bu öznitelik, ana bilgisayar adının URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını belirten <xref:System.ServiceModel.HostNameComparisonMode>türüdür.</span><span class="sxs-lookup"><span data-stu-id="beab9-129">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="beab9-130">Varsayılan değer <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>. Bu, eşleşbir ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="beab9-130">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="beab9-131">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="beab9-131">maxBufferPoolSize</span></span>|<span data-ttu-id="beab9-132">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="beab9-132">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="beab9-133">Varsayılan değer 524.288 bayttır (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="beab9-133">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="beab9-134">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="beab9-134">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="beab9-135">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="beab9-135">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="beab9-136">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="beab9-136">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="beab9-137">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="beab9-137">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="beab9-138">Değerini</span><span class="sxs-lookup"><span data-stu-id="beab9-138">maxReceivedMessageSize</span></span>|<span data-ttu-id="beab9-139">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="beab9-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="beab9-140">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="beab9-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="beab9-141">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="beab9-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="beab9-142">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="beab9-142">The default is 65536.</span></span>|  
|<span data-ttu-id="beab9-143">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="beab9-143">messageEncoding</span></span>|<span data-ttu-id="beab9-144">İletiyi kodlamak için kullanılan kodlayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="beab9-144">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="beab9-145">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="beab9-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="beab9-146">-Metin: bir metin mesajı Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="beab9-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="beab9-147">-MTOM: Ileti Iletimi kuruluş mekanizması 1,0 (MTOM) Kodlayıcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="beab9-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><span data-ttu-id="beab9-148">-Varsayılan metindir.</span><span class="sxs-lookup"><span data-stu-id="beab9-148">-   The default is Text.</span></span><br /><br /> <span data-ttu-id="beab9-149">Bu öznitelik <xref:System.ServiceModel.WSMessageEncoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="beab9-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="beab9-150">name</span><span class="sxs-lookup"><span data-stu-id="beab9-150">name</span></span>|<span data-ttu-id="beab9-151">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="beab9-151">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="beab9-152">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="beab9-152">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="beab9-153">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="beab9-153">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="beab9-154">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="beab9-154">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="beab9-155">openTimeout</span><span class="sxs-lookup"><span data-stu-id="beab9-155">openTimeout</span></span>|<span data-ttu-id="beab9-156">Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="beab9-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="beab9-157">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="beab9-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="beab9-158">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="beab9-158">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="beab9-159">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="beab9-159">proxyAddress</span></span>|<span data-ttu-id="beab9-160">HTTP proxy adresini belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="beab9-160">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="beab9-161">`useSystemWebProxy` `true`, bu ayar `null`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="beab9-161">If `useSystemWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="beab9-162">Varsayılan, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="beab9-162">The default is `null`.</span></span>|  
|<span data-ttu-id="beab9-163">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="beab9-163">receiveTimeout</span></span>|<span data-ttu-id="beab9-164">Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="beab9-164">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="beab9-165">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="beab9-165">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="beab9-166">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="beab9-166">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="beab9-167">Binding üstündeki SendTimeout</span><span class="sxs-lookup"><span data-stu-id="beab9-167">sendTimeout</span></span>|<span data-ttu-id="beab9-168">Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri.</span><span class="sxs-lookup"><span data-stu-id="beab9-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="beab9-169">Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="beab9-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="beab9-170">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="beab9-170">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="beab9-171">Kodkodu kodlama</span><span class="sxs-lookup"><span data-stu-id="beab9-171">textEncoding</span></span>|<span data-ttu-id="beab9-172">Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="beab9-172">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="beab9-173">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="beab9-173">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="beab9-174">-Unicodefffebir kodlama: Unicode Bigenyen kodlaması.</span><span class="sxs-lookup"><span data-stu-id="beab9-174">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="beab9-175">-Utf16TextEncoding: 16 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="beab9-175">-   Utf16TextEncoding: 16-bit encoding.</span></span><br /><span data-ttu-id="beab9-176">-Utf8TextEncoding: 8 bit kodlama.</span><span class="sxs-lookup"><span data-stu-id="beab9-176">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="beab9-177">Varsayılan değer Utf8TextEncoding ' dir.</span><span class="sxs-lookup"><span data-stu-id="beab9-177">The default is Utf8TextEncoding.</span></span><br /><br /> <span data-ttu-id="beab9-178">Bu öznitelik <xref:System.Text.Encoding>türündedir.</span><span class="sxs-lookup"><span data-stu-id="beab9-178">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|<span data-ttu-id="beab9-179">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="beab9-179">transactionFlow</span></span>|<span data-ttu-id="beab9-180">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="beab9-180">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="beab9-181">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="beab9-181">The default is `false`.</span></span>|  
|<span data-ttu-id="beab9-182">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="beab9-182">useDefaultWebProxy</span></span>|<span data-ttu-id="beab9-183">Sistemin otomatik olarak yapılandırılmış HTTP proxy 'sinin kullanılıp kullanılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="beab9-183">A Boolean value that specifies whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="beab9-184">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="beab9-184">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="beab9-185">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="beab9-185">Child Elements</span></span>  
  
|<span data-ttu-id="beab9-186">Öğe</span><span class="sxs-lookup"><span data-stu-id="beab9-186">Element</span></span>|<span data-ttu-id="beab9-187">Açıklama</span><span class="sxs-lookup"><span data-stu-id="beab9-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="beab9-188">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="beab9-188">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="beab9-189">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="beab9-189">Defines the security settings for the binding.</span></span> <span data-ttu-id="beab9-190">Bu öğe <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="beab9-190">This element is of type <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.</span></span>|  
|<span data-ttu-id="beab9-191">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="beab9-191">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="beab9-192">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="beab9-192">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="beab9-193">Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.</span><span class="sxs-lookup"><span data-stu-id="beab9-193">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="beab9-194">[Reliableoturum > \<](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="beab9-194">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="beab9-195">Kanal uç noktaları arasında güvenilir oturumların kurulu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="beab9-195">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="beab9-196">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="beab9-196">Parent Elements</span></span>  
  
|<span data-ttu-id="beab9-197">Öğe</span><span class="sxs-lookup"><span data-stu-id="beab9-197">Element</span></span>|<span data-ttu-id="beab9-198">Açıklama</span><span class="sxs-lookup"><span data-stu-id="beab9-198">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="beab9-199">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="beab9-199">\<bindings></span></span>](bindings.md)|<span data-ttu-id="beab9-200">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="beab9-200">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="beab9-201">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="beab9-201">Remarks</span></span>  
 <span data-ttu-id="beab9-202">`WSHttpBinding`, `BasicHttpBinding` benzer ancak daha fazla Web hizmeti özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="beab9-202">The `WSHttpBinding` is similar to the `BasicHttpBinding` but provides more Web service features.</span></span> <span data-ttu-id="beab9-203">HTTP aktarımını kullanır ve, BasicHttpBinding gibi ileti güvenliği sağlar, ancak varsayılan olarak etkinleştirilmiş veya tek bir denetim ayarıyla kullanılabilen işlemler, güvenilir mesajlaşma ve WS-Addressing işlemleri de sağlar.</span><span class="sxs-lookup"><span data-stu-id="beab9-203">It uses the HTTP transport and provides message security, as does BasicHttpBinding, but it also provides transactions, reliable messaging, and WS-Addressing, either enabled by default or available through a single control setting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="beab9-204">Örnek</span><span class="sxs-lookup"><span data-stu-id="beab9-204">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <wsHttpBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://foo/bar"
                 textEncoding="utf-16"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="Transport">
            <transport clientCredentialType="Digest"
                       proxyCredentialType="None"
                       realm="someRealm" />
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     defaultProtectionLevel="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="beab9-205">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="beab9-205">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement>
- [<span data-ttu-id="beab9-206">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="beab9-206">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="beab9-207">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="beab9-207">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="beab9-208">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="beab9-208">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="beab9-209">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="beab9-209">\<binding></span></span>](bindings.md)
