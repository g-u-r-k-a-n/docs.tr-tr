---
title: 'Nasıl yapılır: WCF Hizmeti İşlemlerini Zaman Uyumsuz Olarak Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 400ed8e5ee8b236e9d0f843f27b7c2112ec28861
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601263"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="aeb52-102">Nasıl yapılır: WCF Hizmeti İşlemlerini Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="aeb52-102">How to: Call WCF Service Operations Asynchronously</span></span>

<span data-ttu-id="aeb52-103">Bu makalede, bir istemcinin bir hizmet işlemine zaman uyumsuz olarak nasıl erişebileceği ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aeb52-103">This article covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="aeb52-104">Bu makaledeki hizmet, `ICalculator` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="aeb52-104">The service in this article implements the `ICalculator` interface.</span></span> <span data-ttu-id="aeb52-105">İstemci, olay odaklı zaman uyumsuz çağrı modelini kullanarak bu arabirimdeki işlemleri zaman uyumsuz olarak çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="aeb52-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="aeb52-106">(Olay tabanlı zaman uyumsuz çağrı modeli hakkında daha fazla bilgi için bkz. çok [Iş parçacıklı programlama, olay tabanlı zaman uyumsuz model ile](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span><span class="sxs-lookup"><span data-stu-id="aeb52-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span></span> <span data-ttu-id="aeb52-107">Bir hizmetin bir hizmette zaman uyumsuz olarak nasıl uygulanacağını gösteren bir örnek için bkz. [nasıl yapılır: Işlem zaman uyumsuz hizmet Işlemi uygulama](../how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="aeb52-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="aeb52-108">Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla bilgi için bkz. [eşzamanlı ve zaman uyumsuz işlemler](../synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="aeb52-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aeb52-109">Kullanılarak olay odaklı zaman uyumsuz çağırma modeli desteklenmez <xref:System.ServiceModel.ChannelFactory%601> .</span><span class="sxs-lookup"><span data-stu-id="aeb52-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="aeb52-110">Kullanarak zaman uyumsuz çağrılar yapma hakkında bilgi için <xref:System.ServiceModel.ChannelFactory%601> bkz. [nasıl yapılır: bir kanal fabrikası kullanarak Işlemleri zaman uyumsuz olarak çağırma](how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="aeb52-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="aeb52-111">Yordam</span><span class="sxs-lookup"><span data-stu-id="aeb52-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="aeb52-112">WCF hizmeti işlemlerini zaman uyumsuz olarak çağırma</span><span class="sxs-lookup"><span data-stu-id="aeb52-112">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="aeb52-113">Aşağıdaki komutta gösterildiği gibi, hem hem de komut seçenekleriyle birlikte [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) aracını çalıştırın `/async` `/tcv:Version35` .</span><span class="sxs-lookup"><span data-stu-id="aeb52-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="aeb52-114">Bu, zaman uyumlu ve standart temsilci tabanlı zaman uyumsuz işlemlere ek olarak şunları içeren bir WCF istemci sınıfı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="aeb52-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    - <span data-ttu-id="aeb52-115">`operationName` > `Async` Olay tabanlı zaman uyumsuz çağırma yaklaşımıyla birlikte kullanmak için iki <işlemi.</span><span class="sxs-lookup"><span data-stu-id="aeb52-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="aeb52-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="aeb52-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - <span data-ttu-id="aeb52-117">`operationName` > `Completed` Olay tabanlı zaman uyumsuz çağırma yaklaşımıyla kullanılmak üzere <form işlem tamamlandı olayları.</span><span class="sxs-lookup"><span data-stu-id="aeb52-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="aeb52-118">Örnek:</span><span class="sxs-lookup"><span data-stu-id="aeb52-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <span data-ttu-id="aeb52-119"><xref:System.EventArgs?displayProperty=nameWithType>`operationName` > `CompletedEventArgs` olay tabanlı zaman uyumsuz çağırma yaklaşımıyla kullanılmak üzere her bir işlemin (form <) türleri.</span><span class="sxs-lookup"><span data-stu-id="aeb52-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="aeb52-120">Örnek:</span><span class="sxs-lookup"><span data-stu-id="aeb52-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. <span data-ttu-id="aeb52-121">Çağıran uygulamada, aşağıdaki örnek kodda gösterildiği gibi zaman uyumsuz işlem tamamlandığında çağrılacak bir geri arama yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="aeb52-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. <span data-ttu-id="aeb52-122">İşlem çağrılmadan önce, <xref:System.EventHandler%601?displayProperty=nameWithType> `operationName` > `EventArgs` <olayına işleyici yöntemini (önceki adımda oluşturulan) eklemek için <`operationName` > türünde yeni bir genel kullanın `Completed` .</span><span class="sxs-lookup"><span data-stu-id="aeb52-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="aeb52-123">Sonra <yöntemini çağırın `operationName` > `Async` .</span><span class="sxs-lookup"><span data-stu-id="aeb52-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="aeb52-124">Örnek:</span><span class="sxs-lookup"><span data-stu-id="aeb52-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="aeb52-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="aeb52-125">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aeb52-126">Olay tabanlı zaman uyumsuz model için, birden fazla değer döndürülürse, özellik olarak bir değer döndürülür `Result` ve diğerleri nesne üzerinde özellikler olarak döndürülür <xref:System.EventArgs> .</span><span class="sxs-lookup"><span data-stu-id="aeb52-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="aeb52-127">Bunun sonucunda, bir istemci, olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verileri içeri aktardığında ve işlem birden fazla değer döndürürse, varsayılan <xref:System.EventArgs> nesne özellik olarak bir değer döndürür `Result` ve geri kalanı <xref:System.EventArgs> nesnenin özellikleridir. İleti nesnesini özellik olarak almak `Result` ve döndürülen değerlerin bu nesnede özellikler olarak elde etmek istiyorsanız, `/messageContract` komut seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aeb52-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="aeb52-128">Bu, nesne üzerindeki özelliği olarak yanıt iletisini döndüren bir imza oluşturur `Result` <xref:System.EventArgs> .</span><span class="sxs-lookup"><span data-stu-id="aeb52-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="aeb52-129">Tüm iç dönüş değerleri, yanıt iletisi nesnesinin özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="aeb52-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="aeb52-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeb52-130">See also</span></span>

- [<span data-ttu-id="aeb52-131">Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama</span><span class="sxs-lookup"><span data-stu-id="aeb52-131">How to: Implement an Asynchronous Service Operation</span></span>](../how-to-implement-an-asynchronous-service-operation.md)
