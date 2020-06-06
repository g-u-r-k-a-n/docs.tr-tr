---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: c43c141093c8287adb6d5a841a43ac893deefccd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139336"
---
# \<netTcpBinding>

<span data-ttu-id="6fa18-101">Makineler arası iletişim için güvenli, güvenilir ve iyileştirilmiş bir bağlama belirtir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-101">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="6fa18-102">Varsayılan olarak, ileti güvenliği ve kimlik doğrulaması, ileti teslimi için TCP ve ikili ileti kodlaması için Windows güvenliği ile bir çalışma zamanı iletişim yığını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6fa18-102">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="6fa18-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6fa18-103">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fa18-104">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="6fa18-104">Attributes and elements</span></span>

<span data-ttu-id="6fa18-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fa18-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6fa18-106">Attributes</span></span>  
  
|<span data-ttu-id="6fa18-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6fa18-107">Attribute</span></span>|<span data-ttu-id="6fa18-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fa18-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="6fa18-109"><xref:System.TimeSpan>Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6fa18-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6fa18-110">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="6fa18-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6fa18-111">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-111">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="6fa18-112">URI 'Leri ayrıştırmak için kullanılan HTTP ana bilgisayar adını karşılaştırma modunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-112">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="6fa18-113">Bu öznitelik, <xref:System.ServiceModel.HostNameComparisonMode> ana bilgisayar ADıNıN URI üzerinde eşleştirilirken hizmete erişmek için kullanılıp kullanılmadığını gösteren türüdür.</span><span class="sxs-lookup"><span data-stu-id="6fa18-113">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="6fa18-114">Varsayılan değer, <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> eşleşenlerin ana bilgisayar adını yok saymaz.</span><span class="sxs-lookup"><span data-stu-id="6fa18-114">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="6fa18-115">Dinleyicide kabul edilmesini bekleyen kanal sayısı üst sınırını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6fa18-115">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="6fa18-116">Bu sınırın üzerinde olan bağlantılar, sınırın altındaki boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-116">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="6fa18-117">`connectionTimeout`Öznitelik, bir bağlantı özel durumu oluşturmadan önce istemcinin bağlanması için bekleyeceği süreyi sınırlandırır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-117">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="6fa18-118">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="6fa18-118">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="6fa18-119">Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6fa18-119">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="6fa18-120">Varsayılan değer 512 \* 1024 bayttır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-120">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="6fa18-121">Windows Communication Foundation (WCF) birçok bölümü arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-121">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="6fa18-122">Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="6fa18-123">Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6fa18-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="6fa18-124">Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="6fa18-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="6fa18-125">İletileri bellekte depolamak için kullanılan arabelleğin bayt cinsinden en büyük boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6fa18-125">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="6fa18-126">`transferMode`Özniteliği öğesine eşitse `Buffered` , bu öznitelik `maxReceivedMessageSize` öznitelik değerine eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-126">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="6fa18-127">`transferMode`Özniteliği öğesine eşitse `Streamed` , bu öznitelik öznitelik değerinden daha fazla olamaz `maxReceivedMessageSize` ve en azından üst bilgilerin boyutu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-127">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="6fa18-128">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-128">The default is 65536.</span></span> <span data-ttu-id="6fa18-129">Daha fazla bilgi için bkz. <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="6fa18-129">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="6fa18-130">Hizmetin oluşturulacağı/kabul edeceği en fazla giden ve gelen bağlantı sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6fa18-130">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="6fa18-131">Gelen ve giden bağlantılar, bu öznitelik tarafından belirtilen ayrı bir sınıra göre sayılır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-131">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="6fa18-132">Sınırın üzerindeki gelen bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-132">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="6fa18-133">Sınırın üzerindeki giden bağlantılar, sınırın altındaki bir boşluk kullanılabilir olana kadar sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-133">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="6fa18-134">Varsayılan değer 10 ' dur.</span><span class="sxs-lookup"><span data-stu-id="6fa18-134">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="6fa18-135">Bu bağlama ile yapılandırılmış bir kanalda alınabilecek üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6fa18-135">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="6fa18-136">Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-136">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="6fa18-137">Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6fa18-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6fa18-138">Varsayılan değer 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-138">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="6fa18-139">Bağlamanın yapılandırma adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="6fa18-139">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6fa18-140">Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-140">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6fa18-141">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-141">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6fa18-142">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="6fa18-142">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="6fa18-143">Bir <xref:System.TimeSpan> Açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6fa18-143">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6fa18-144">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="6fa18-144">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6fa18-145">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-145">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="6fa18-146">Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="6fa18-146">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="6fa18-147">Bu ise `false` , her bağlama kendi özel bağlantı noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-147">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="6fa18-148">İstemciler etkilenmediğinden, bu ayar yalnızca hizmetler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-148">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="6fa18-149"><xref:System.TimeSpan>Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6fa18-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6fa18-150">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="6fa18-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6fa18-151">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="6fa18-152"><xref:System.TimeSpan>Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6fa18-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6fa18-153">Bu değer, değerinden büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="6fa18-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6fa18-154">Varsayılan değer 00:01:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-154">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="6fa18-155">Bağlamanın, akan WS-Işlemleri destekleyip desteklemediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6fa18-155">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="6fa18-156">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="6fa18-156">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="6fa18-157">Bu bağlama ile kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-157">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="6fa18-158">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="6fa18-158">Valid values are</span></span><br /><br /> <span data-ttu-id="6fa18-159">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="6fa18-159">-   OleTransactions</span></span><br /><span data-ttu-id="6fa18-160">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="6fa18-160">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="6fa18-161">Varsayılan değer OleTransactions 'dir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-161">The default is OleTransactions.</span></span> <span data-ttu-id="6fa18-162">Bu öznitelik türü <xref:System.ServiceModel.TransactionProtocol> .</span><span class="sxs-lookup"><span data-stu-id="6fa18-162">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="6fa18-163"><xref:System.ServiceModel.TransferMode>İletilerin arabelleğe alınıp alınmayacağını veya bir istek ya da yanıt olduğunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6fa18-163">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fa18-164">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6fa18-164">Child elements</span></span>  
  
|<span data-ttu-id="6fa18-165">Öğe</span><span class="sxs-lookup"><span data-stu-id="6fa18-165">Element</span></span>|<span data-ttu-id="6fa18-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fa18-166">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="6fa18-167">Bağlama için güvenlik ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6fa18-167">Defines the security settings for the binding.</span></span> <span data-ttu-id="6fa18-168">Bu öğe türündedir <xref:System.ServiceModel.Configuration.NetTcpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="6fa18-168">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="6fa18-169">Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6fa18-169">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="6fa18-170">Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="6fa18-170">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="6fa18-171">Kanal uç noktaları arasında güvenilir oturumların kurulu olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-171">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6fa18-172">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6fa18-172">Parent elements</span></span>  
  
|<span data-ttu-id="6fa18-173">Öğe</span><span class="sxs-lookup"><span data-stu-id="6fa18-173">Element</span></span>|<span data-ttu-id="6fa18-174">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fa18-174">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="6fa18-175">Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-175">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fa18-176">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6fa18-176">Remarks</span></span>

<span data-ttu-id="6fa18-177">Bu bağlama, aktarım güvenliği, ileti teslimi için TCP ve ikili ileti kodlaması kullanan, varsayılan olarak bir çalışma zamanı iletişim yığını üretir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-177">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="6fa18-178">Bu bağlama, bir Intranet üzerinden iletişim kurmak için uygun bir Windows Communication Foundation (WCF) sistem tarafından sağlanmış seçenektir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-178">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="6fa18-179">İçin varsayılan yapılandırma `netTcpBinding` , tarafından sağlanmış yapılandırmadan daha hızlıdır `wsHttpBinding` , ancak yalnızca WCF iletişimi amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-179">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="6fa18-180">Güvenlik davranışı, isteğe bağlı özniteliği kullanılarak yapılandırılabilir `securityMode` .</span><span class="sxs-lookup"><span data-stu-id="6fa18-180">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="6fa18-181">WS-ReliableMessaging kullanımı, isteğe bağlı özniteliği kullanılarak yapılandırılabilir `reliableSessionEnabled` .</span><span class="sxs-lookup"><span data-stu-id="6fa18-181">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="6fa18-182">Ancak güvenilir mesajlaşma varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-182">But reliable messaging is off by default.</span></span> <span data-ttu-id="6fa18-183">Daha genel olarak, ve gibi HTTP sistem tarafından sağlanmış bağlamalar `wsHttpBinding` , `basicHttpBinding` Varsayılan olarak ' ı açmak üzere yapılandırılmıştır, ancak `netTcpBinding` Örneğin, WS-\* belirtimlerinden biri için, destek almak için kabul etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-183">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="6fa18-184">Bu, TCP varsayılan yapılandırmasının, HTTP bağlamaları için varsayılan olarak yapılandırılanlardan farklı uç noktalar arasında ileti alışverişi yaparken daha hızlı olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-184">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fa18-185">Örnek</span><span class="sxs-lookup"><span data-stu-id="6fa18-185">Example</span></span>

<span data-ttu-id="6fa18-186">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-186">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="6fa18-187">Bağlama türü, `binding` öğesinin özniteliğinde belirtilir `<endpoint>` .</span><span class="sxs-lookup"><span data-stu-id="6fa18-187">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="6fa18-188">NetTcpBinding bağlamasını yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bir bağlama yapılandırması tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6fa18-188">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="6fa18-189">Uç noktanın bağlama yapılandırmasına bir özniteliğiyle başvurması gerekir `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="6fa18-189">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="6fa18-190">Aşağıdaki örnekte, bir bağlama yapılandırması tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6fa18-190">In the following example, a binding configuration is defined.</span></span>  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="6fa18-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fa18-191">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="6fa18-192">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6fa18-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6fa18-193">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6fa18-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6fa18-194">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6fa18-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
