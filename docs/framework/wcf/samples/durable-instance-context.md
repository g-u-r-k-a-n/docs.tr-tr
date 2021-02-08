---
description: 'Daha fazla bilgi edinin: dayanıklı örnek bağlamı'
title: Dayanıklı Örnek Bağlamı
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 6f879b2f6c592e5d8f7294405fda403e918070ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793304"
---
# <a name="durable-instance-context"></a><span data-ttu-id="fe52a-103">Dayanıklı Örnek Bağlamı</span><span class="sxs-lookup"><span data-stu-id="fe52a-103">Durable Instance Context</span></span>

<span data-ttu-id="fe52a-104">Bu örnek, dayanıklı örnek bağlamlarını etkinleştirmek için Windows Communication Foundation (WCF) çalışma zamanının nasıl özelleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-104">This sample demonstrates how to customize the Windows Communication Foundation (WCF) runtime to enable durable instance contexts.</span></span> <span data-ttu-id="fe52a-105">Bu, yedekleme deposu olarak 2005 SQL Server kullanır (Bu durumda SQL Server 2005 Express).</span><span class="sxs-lookup"><span data-stu-id="fe52a-105">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="fe52a-106">Bununla birlikte, özel depolama mekanizmalarına erişmek için de bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe52a-106">However, it also provides a way to access custom storage mechanisms.</span></span>

> [!NOTE]
> <span data-ttu-id="fe52a-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="fe52a-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="fe52a-108">Bu örnek, WCF 'nin hem kanal katmanını hem de hizmet modeli katmanını genişletmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-108">This sample involves extending both the channel layer and the service model layer of the WCF.</span></span> <span data-ttu-id="fe52a-109">Bu nedenle, uygulama ayrıntılarına geçmeden önce temel kavramları anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-109">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>

<span data-ttu-id="fe52a-110">Dayanıklı örnek bağlamları gerçek dünyada oldukça sık bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-110">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="fe52a-111">Örneğin, bir alışveriş sepeti uygulamasının, bir alışveriş sepetini aracılığıyla alışverişi bir gün içinde duraklatarak devam etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-111">A shopping cart application, for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="fe52a-112">Bu sayede, bir sonraki güne ait alışveriş sepetini ziyaret ettiğimiz zaman, özgün bağlamımız geri yüklendi.</span><span class="sxs-lookup"><span data-stu-id="fe52a-112">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="fe52a-113">, Bağlantısı kesiltiğimiz sırada alışveriş sepeti uygulamasının (sunucudaki) alışveriş sepeti örneğini korumadığını unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-113">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="fe52a-114">Bunun yerine, durumunu dayanıklı bir depolama medyasına devam ettirir ve geri yüklenen bağlam için yeni bir örnek oluştururken onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-114">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="fe52a-115">Bu nedenle, aynı bağlam için hizmet veren hizmet örneği, önceki örnekle aynı değildir (yani aynı bellek adresine sahip değildir).</span><span class="sxs-lookup"><span data-stu-id="fe52a-115">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>

<span data-ttu-id="fe52a-116">İstemci ve hizmet arasında bir bağlam KIMLIĞI değiş tokuş eden küçük bir protokol tarafından dayanıklı örnek bağlamı mümkün hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-116">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="fe52a-117">Bu bağlam KIMLIĞI istemcide oluşturulur ve hizmete iletilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-117">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="fe52a-118">Hizmet örneği oluşturulduğunda, hizmet çalışma zamanı kalıcı bir depolamadan bu bağlam KIMLIĞINE karşılık gelen kalıcı durumu yüklemeye çalışır (varsayılan olarak bir SQL Server 2005 veritabanıdır).</span><span class="sxs-lookup"><span data-stu-id="fe52a-118">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="fe52a-119">Kullanılabilir bir durum yoksa, yeni örnek varsayılan durumuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-119">If no state is available, the new instance has its default state.</span></span> <span data-ttu-id="fe52a-120">Hizmet uygulamasının, hizmet uygulamasının durumunu değiştiren işlemleri işaretlemek için özel bir öznitelik kullanır, böylece çalışma zamanı, hizmet örneğini çağırdıktan sonra kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-120">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>

<span data-ttu-id="fe52a-121">Önceki açıklama ile, iki adım hedefe ulaşmak için kolayca ayırt edilebilir:</span><span class="sxs-lookup"><span data-stu-id="fe52a-121">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>

1. <span data-ttu-id="fe52a-122">Bağlam KIMLIĞINI taşımak için tel bağlantı olan iletiyi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fe52a-122">Change the message that goes on the wire to carry the context ID.</span></span>

2. <span data-ttu-id="fe52a-123">Hizmet yerel davranışını özel örnek oluşturma mantığını uygulayacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fe52a-123">Change the service local behavior to implement custom instancing logic.</span></span>

<span data-ttu-id="fe52a-124">Listedeki ilk bir ileti, hattaki iletileri etkilediği için özel bir kanal olarak uygulanmalıdır ve kanal katmanına bağlanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-124">Because the first one in the list affects the messages on the wire, it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="fe52a-125">İkincisi yalnızca hizmet yerel davranışını etkiler ve bu nedenle çeşitli hizmet genişletilebilirliği noktaları genişletilerek uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-125">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="fe52a-126">Sonraki birkaç bölümde, bu uzantıların her biri ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-126">In the next few sections, each of these extensions are discussed.</span></span>

## <a name="durable-instancecontext-channel"></a><span data-ttu-id="fe52a-127">Dayanıklı InstanceContext kanalı</span><span class="sxs-lookup"><span data-stu-id="fe52a-127">Durable InstanceContext Channel</span></span>

<span data-ttu-id="fe52a-128">Aranacak ilk şey bir kanal katmanı uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-128">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="fe52a-129">Özel bir kanal yazmanın ilk adımı, kanalın iletişim yapısına karar vermidir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-129">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="fe52a-130">Yeni bir hat Protokolü tanıtılmakta olduğundan kanal, kanal yığınındaki neredeyse tüm diğer kanallarla çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-130">As a new wire protocol is being introduced, the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="fe52a-131">Bu nedenle, tüm ileti değişimi düzenlerini desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-131">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="fe52a-132">Ancak, kanalın temel işlevselliği, iletişim yapısıyla bağımsız olarak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-132">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="fe52a-133">Daha belirgin bir şekilde, istemciden içerik KIMLIĞINI iletilere ve hizmetten bu bağlam KIMLIĞINI okuyup üst düzeylere geçirecek şekilde yazması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-133">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="fe52a-134">Bu nedenle, `DurableInstanceContextChannelBase` Tüm dayanıklı örnek bağlam kanalı uygulamaları için soyut temel sınıf olarak davranan bir sınıf oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fe52a-134">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="fe52a-135">Bu sınıf, genel durum makinesi yönetim işlevlerini ve bu iki korumalı üyeyi uygulamak ve iletilere ve bu kaynaklardan bağlam bilgilerini okumak için içerir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-135">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>

```csharp
class DurableInstanceContextChannelBase
{
  //…
  protected void ApplyContext(Message message)
  {
    //…
  }
  protected string ReadContextId(Message message)
  {
    //…
  }
}
```

<span data-ttu-id="fe52a-136">Bu iki yöntem, bir `IContextManager` veya ileti aracılığıyla bağlam Kimliğini yazmak ve okumak için uygulamalar kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-136">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="fe52a-137">( `IContextManager` tüm bağlam yöneticileri için sözleşmeyi tanımlamak üzere kullanılan özel bir arabirimdir.) Kanal, bağlam KIMLIĞINI özel bir SOAP üstbilgisine veya bir HTTP tanımlama bilgisi başlığına dahil edebilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-137">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in an HTTP cookie header.</span></span> <span data-ttu-id="fe52a-138">Her bir bağlam Yöneticisi uygulamasının `ContextManagerBase` tüm bağlam yöneticileri için ortak işlevselliği içeren sınıftan devralır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-138">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="fe52a-139">`GetContextId`Bu sınıftaki yöntem, istemciden bağlam Kimliğini yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-139">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="fe52a-140">Bir bağlam KIMLIĞI ilk kez oluşturulduğunda, bu yöntem, adı uzak uç nokta adresi tarafından oluşturulan bir metin dosyasına kaydeder (tipik URI 'Ler içindeki geçersiz dosya adı karakterleri @ karakterlerle değiştirilmiştir).</span><span class="sxs-lookup"><span data-stu-id="fe52a-140">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>

<span data-ttu-id="fe52a-141">Daha sonra aynı uzak uç nokta için bağlam KIMLIĞI gerektiğinde, uygun bir dosyanın var olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="fe52a-141">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="fe52a-142">Varsa, bağlam KIMLIĞINI okur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe52a-142">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="fe52a-143">Aksi takdirde, yeni oluşturulan bir bağlam KIMLIĞI döndürür ve bir dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fe52a-143">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="fe52a-144">Varsayılan yapılandırmayla, bu dosyalar geçerli kullanıcının geçici dizininde bulunan ContextStore adlı bir dizine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-144">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user's temp directory.</span></span> <span data-ttu-id="fe52a-145">Ancak bu konum, Binding öğesi kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-145">However this location is configurable using the binding element.</span></span>

<span data-ttu-id="fe52a-146">Bağlam KIMLIĞINI taşımak için kullanılan mekanizma yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-146">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="fe52a-147">HTTP tanımlama bilgisi başlığına veya özel bir SOAP üstbilgisine yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-147">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="fe52a-148">Özel SOAP üst bilgisi yaklaşımı, bu Protokolü HTTP olmayan protokollerle (örneğin, TCP veya adlandırılmış kanallar) kullanmayı mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="fe52a-148">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="fe52a-149">`MessageHeaderContextManager` `HttpCookieContextManager` Bu iki seçeneği de uygulayan iki sınıf vardır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-149">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>

<span data-ttu-id="fe52a-150">Her ikisi de içerik KIMLIĞINI uygun şekilde iletiye yazar.</span><span class="sxs-lookup"><span data-stu-id="fe52a-150">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="fe52a-151">Örneğin, sınıfı, `MessageHeaderContextManager` yöntemi içindeki BIR SOAP üstbilgisine yazar `WriteContext` .</span><span class="sxs-lookup"><span data-stu-id="fe52a-151">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>

```csharp
public override void WriteContext(Message message)
{
  string contextId = this.GetContextId();

  MessageHeader contextHeader =
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,
      DurableInstanceContextUtility.HeaderNamespace,
      contextId,
      true);

  message.Headers.Add(contextHeader);
}
```

<span data-ttu-id="fe52a-152">Hem hem `ApplyContext` de `ReadContextId` `DurableInstanceContextChannelBase` sınıfındaki yöntemleri `IContextManager.ReadContext` `IContextManager.WriteContext` sırasıyla ve ' ı çağırır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-152">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="fe52a-153">Ancak, bu bağlam yöneticileri sınıf tarafından doğrudan oluşturulmaz `DurableInstanceContextChannelBase` .</span><span class="sxs-lookup"><span data-stu-id="fe52a-153">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="fe52a-154">Bunun yerine, `ContextManagerFactory` Bu işi yapmak için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-154">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

<span data-ttu-id="fe52a-155">`ApplyContext`Yöntemi, gönderen kanallar tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-155">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="fe52a-156">Bağlam KIMLIĞINI giden iletilere çıkartır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-156">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="fe52a-157">`ReadContextId`Yöntemi, alan kanalları tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-157">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="fe52a-158">Bu yöntem, gelen iletilerde bağlam KIMLIĞININ kullanılabilir olmasını sağlar ve onu `Properties` sınıfının koleksiyonuna ekler `Message` .</span><span class="sxs-lookup"><span data-stu-id="fe52a-158">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="fe52a-159">Ayrıca `CommunicationException` , bağlam kimliği okunamaması ve bu nedenle kanalın iptal edilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="fe52a-159">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

<span data-ttu-id="fe52a-160">Devam etmeden önce, sınıfında koleksiyonun kullanımını anlamak önemlidir `Properties` `Message` .</span><span class="sxs-lookup"><span data-stu-id="fe52a-160">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="fe52a-161">Genellikle, bu `Properties` koleksiyon, verileri daha düşük olan kanal katmanından üst düzeylere geçirirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-161">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="fe52a-162">Bu şekilde, istenen veriler, protokol ayrıntılarının ne olursa olsun, üst düzeylere tutarlı bir şekilde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-162">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="fe52a-163">Diğer bir deyişle, kanal katmanı, bağlam KIMLIĞINI bir SOAP üstbilgisi veya HTTP tanımlama bilgisi üstbilgisi olarak gönderebilir ve alabilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-163">In other words, the channel layer can send and receive the context ID either as a SOAP header or an HTTP cookie header.</span></span> <span data-ttu-id="fe52a-164">Ancak Kanal katmanı bu bilgileri koleksiyonda kullanılabilir hale yaptığından üst düzeylerin bu ayrıntıları öğrenmek için gerekli değildir `Properties` .</span><span class="sxs-lookup"><span data-stu-id="fe52a-164">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>

<span data-ttu-id="fe52a-165">Artık bu `DurableInstanceContextChannelBase` sınıfla, gerekli arabirimlerin (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel destekleyen desteklenecektir, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) her on onuna sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-165">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="fe52a-166">Her kullanılabilir ileti değişimi düzenine (datagram, simpleks, dupleks ve oturumsuz çeşitleri) benzer.</span><span class="sxs-lookup"><span data-stu-id="fe52a-166">They resemble every available message exchange pattern (datagram, simplex, duplex, and their sessionful variants).</span></span> <span data-ttu-id="fe52a-167">Bu uygulamaların her biri, daha önce açıklanan temel sınıfı ve çağrıları `ApplyContext` ve `ReadContextId` uygun şekilde devralır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-167">Each of these implementations inherits the base class previously described and calls `ApplyContext` and `ReadContextId` appropriately.</span></span> <span data-ttu-id="fe52a-168">Örneğin, `DurableInstanceContextOutputChannel` IOutputChannel arabirimini uygulayan- `ApplyContext` iletileri gönderen her yöntemden yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-168">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

<span data-ttu-id="fe52a-169">Diğer taraftan, `DurableInstanceContextInputChannel` arabirimini uygulayan- `IInputChannel` `ReadContextId` iletileri alan her yöntemde yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-169">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method, which receives the messages.</span></span>

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

<span data-ttu-id="fe52a-170">Bunun dışında, bu kanal uygulamaları kanal yığınında alttaki kanala yönelik Yöntem çağrılarını devredebilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-170">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="fe52a-171">Ancak, oturum, bağlam KIMLIĞININ gönderildiğinden ve oturumun oluşturulmasına neden olan ilk ileti için salt okunan olduğundan emin olmak için bir temel mantığa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-171">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

<span data-ttu-id="fe52a-172">Daha sonra bu kanal uygulamaları, `DurableInstanceContextBindingElement` sınıf ve sınıf tarafından uygun şekılde WCF kanal çalışma zamanına eklenir `DurableInstanceContextBindingElementSection` .</span><span class="sxs-lookup"><span data-stu-id="fe52a-172">These channel implementations are then added to the WCF channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="fe52a-173">Bağlama öğeleri ve bağlama öğesi bölümleri hakkında daha fazla bilgi için [Httppişirce oturum](httpcookiesession.md) kanalı örnek belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="fe52a-173">See the [HttpCookieSession](httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>

## <a name="service-model-layer-extensions"></a><span data-ttu-id="fe52a-174">Hizmet modeli katmanı uzantıları</span><span class="sxs-lookup"><span data-stu-id="fe52a-174">Service Model Layer Extensions</span></span>

<span data-ttu-id="fe52a-175">Artık bağlam KIMLIĞI kanal katmanından gezinmiş olduğuna göre, örnek oluşturmayı özelleştirmek için hizmet davranışı uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-175">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="fe52a-176">Bu örnekte, Depolama Yöneticisi, durumu yüklemek ve kalıcı depoya kaydetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-176">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="fe52a-177">Daha önce açıklandığı gibi, bu örnek, yedekleme deposu olarak SQL Server 2005 ' ı kullanan bir Depolama Yöneticisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe52a-177">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="fe52a-178">Ancak, bu uzantıya özel depolama mekanizmaları eklemek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="fe52a-178">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="fe52a-179">Ortak bir arabirimin, tüm depolama yöneticileri tarafından uygulanması gereken şekilde bildirilmesini sağlamak.</span><span class="sxs-lookup"><span data-stu-id="fe52a-179">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

<span data-ttu-id="fe52a-180">`SqlServerStorageManager`Sınıfı varsayılan `IStorageManager` uygulamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-180">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="fe52a-181">`SaveInstance`Yönteminde, verilen nesne XmlSerializer kullanılarak serileştirilir ve SQL Server veritabanına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-181">In its `SaveInstance` method, the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>

```csharp
XmlSerializer serializer = new XmlSerializer(state.GetType());
string data;

using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))
{
    serializer.Serialize(writer, state);
    data = writer.ToString();
}

using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";

    using (SqlCommand command = new SqlCommand(update, connection))
    {
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;

        int rows = command.ExecuteNonQuery();

        if (rows == 0)
        {
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";
            command.CommandText = insert;
            command.ExecuteNonQuery();
        }
    }
}
```

<span data-ttu-id="fe52a-182">`GetInstance`Yönteminde, serileştirilmiş veriler belirli bir bağlam kimliği için okunurdur ve öğesinden oluşturulan nesne çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fe52a-182">In the `GetInstance` method, the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>

```csharp
object data;
using (SqlConnection connection = new SqlConnection(GetConnectionString()))
{
    connection.Open();

    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";
    using (SqlCommand command = new SqlCommand(select, connection))
    {
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;
        data = command.ExecuteScalar();
    }
}

if (data != null)
{
    XmlSerializer serializer = new XmlSerializer(type);
    using (StringReader reader = new StringReader((string)data))
    {
        object instance = serializer.Deserialize(reader);
        return instance;
    }
}
```

<span data-ttu-id="fe52a-183">Bu depolama yöneticilerinin kullanıcıları doğrudan örneklendirilecek.</span><span class="sxs-lookup"><span data-stu-id="fe52a-183">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="fe52a-184">Bunlar `StorageManagerFactory` , Depolama Yöneticisi oluşturma ayrıntılarının soyutlarından oluşan sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-184">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="fe52a-185">Bu sınıf, `GetStorageManager` belirli bir Depolama Yöneticisi türünün örneğini oluşturan bir statik üyeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-185">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="fe52a-186">Tür parametresi ise `null` , bu yöntem varsayılan sınıfın bir örneğini oluşturur `SqlServerStorageManager` ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe52a-186">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="fe52a-187">Ayrıca, arabirimi uyguladığından emin olmak için verilen türü doğrular `IStorageManager` .</span><span class="sxs-lookup"><span data-stu-id="fe52a-187">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>

```csharp
public static IStorageManager GetStorageManager(Type storageManagerType)
{
IStorageManager storageManager = null;

if (storageManagerType == null)
{
    return new SqlServerStorageManager();
}
else
{
    object obj = Activator.CreateInstance(storageManagerType);

    // Throw if the specified storage manager type does not
    // implement IStorageManager.
    if (obj is IStorageManager)
    {
        storageManager = (IStorageManager)obj;
    }
    else
    {
        throw new InvalidOperationException(
                  ResourceHelper.GetString("ExInvalidStorageManager"));
    }

    return storageManager;
}
}
```

<span data-ttu-id="fe52a-188">Kalıcı depolama alanından örnekleri okumak ve yazmak için gerekli altyapı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-188">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="fe52a-189">Artık hizmet davranışını değiştirmek için gerekli adımlar gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-189">Now the necessary steps to change the service behavior have to be taken.</span></span>

<span data-ttu-id="fe52a-190">Bu işlemin ilk adımı olarak, geçerli InstanceContext için kanal katmanından gelen bağlam KIMLIĞINI kaydetmemiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-190">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="fe52a-191">InstanceContext, WCF dağıtıcısı ve hizmet örneği arasında bağlantı görevi gören bir çalışma zamanı bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-191">InstanceContext is a runtime component that acts as the link between the WCF dispatcher and the service instance.</span></span> <span data-ttu-id="fe52a-192">Hizmet örneğine ek durum ve davranış sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-192">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="fe52a-193">Bu, sessioncommunication öğesinde bağlam KIMLIĞI yalnızca ilk iletiyle gönderildiği için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-193">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>

<span data-ttu-id="fe52a-194">WCF, genişletilebilir nesne modelini kullanarak yeni bir durum ve davranış ekleyerek InstanceContext çalışma zamanı bileşenini genişletmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe52a-194">WCF allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="fe52a-195">Genişletilebilir nesne stili, mevcut çalışma zamanı sınıflarını yeni işlevlerle genişletmek ya da bir nesneye yeni durum özellikleri eklemek için WCF 'de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-195">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="fe52a-196">Genişletilebilir nesne düzeninde üç arabirim vardır: IExtensibleObject \<T> , IExtension \<T> ve IExtensionCollection \<T> :</span><span class="sxs-lookup"><span data-stu-id="fe52a-196">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>

- <span data-ttu-id="fe52a-197">IExtensibleObject \<T> arabirimi, işlevlerini özelleştiren uzantılara izin veren nesneler tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-197">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>

- <span data-ttu-id="fe52a-198">IExtension \<T> arabirimi T türünde sınıfların uzantıları olan nesneler tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-198">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>

- <span data-ttu-id="fe52a-199">IExtensionCollection \<T> arabirimi, IExtensions 'ın türlerine göre alınmasına izin veren bir IExtensions koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="fe52a-199">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>

<span data-ttu-id="fe52a-200">Bu nedenle, IExtension arabirimini uygulayan bir InstanceContextExtension sınıfı oluşturulmalıdır ve bağlam KIMLIĞINI kaydetmek için gereken durumu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fe52a-200">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="fe52a-201">Bu sınıf Ayrıca, kullanılmakta olan depolama yöneticisini tutan durumu da sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe52a-201">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="fe52a-202">Yeni durum kaydedildikten sonra değiştirmek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-202">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="fe52a-203">Bu nedenle, durum oluşturulur ve oluşturulduğu sırada örneğe kaydedilir ve yalnızca salt okunurdur özellikleri kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-203">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>

```csharp
// Constructor
public DurableInstanceContextExtension(string contextId,
            IStorageManager storageManager)
{
    this.contextId = contextId;
    this.storageManager = storageManager;
}

// Read only properties
public string ContextId
{
    get { return this.contextId; }
}

public IStorageManager StorageManager
{
    get { return this.storageManager; }
}
```

<span data-ttu-id="fe52a-204">InstanceContextInitializer sınıfı, IInstanceContextInitializer arabirimini uygular ve örnek bağlam uzantısını oluşturulan InstanceContext öğesinin uzantılar koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="fe52a-204">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>

```csharp
public void Initialize(InstanceContext instanceContext, Message message)
{
    string contextId =
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];

    DurableInstanceContextExtension extension =
                new DurableInstanceContextExtension(contextId,
                     storageManager);
    instanceContext.Extensions.Add(extension);
}
```

<span data-ttu-id="fe52a-205">Daha önce açıklandığı gibi, bağlam KIMLIĞI `Properties` sınıfının koleksiyonundan okunurdur `Message` ve Extension sınıfının oluşturucusuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-205">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="fe52a-206">Bu, bilgilerin katmanlar arasında tutarlı bir şekilde nasıl değiş tokuş edilebilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-206">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>

<span data-ttu-id="fe52a-207">Sonraki önemli adım, hizmet örneği oluşturma sürecini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="fe52a-207">The next important step is overriding the service instance creation process.</span></span> <span data-ttu-id="fe52a-208">WCF, özel örnek oluşturma davranışlarını uygulamaya ve IInstanceProvider arabirimini kullanarak bunları çalışma zamanına kadar yüklemeye olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-208">WCF allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="fe52a-209">Yeni `InstanceProvider` sınıf bu işi yapmak için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-209">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="fe52a-210">Örnek sağlayıcıdan beklenen hizmet türü oluşturucuda kabul edildi.</span><span class="sxs-lookup"><span data-stu-id="fe52a-210">The service type expected from the instance provider is accepted in the constructor.</span></span> <span data-ttu-id="fe52a-211">Daha sonra bu, yeni örnekler oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-211">Later this is used to create new instances.</span></span> <span data-ttu-id="fe52a-212">`GetInstance`Uygulamada, kalıcı bir örnek bulmak için Depolama Yöneticisi 'nin bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fe52a-212">In the `GetInstance` implementation, an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="fe52a-213">Dönerse `null` , hizmet türünün yeni bir örneği oluşturulur ve çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fe52a-213">If it returns `null`, then a new instance of the service type is instantiated and returned to the caller.</span></span>

```csharp
public object GetInstance(InstanceContext instanceContext, Message message)
{
    object instance = null;

    DurableInstanceContextExtension extension =
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();

    string contextId = extension.ContextId;
    IStorageManager storageManager = extension.StorageManager;

    instance = storageManager.GetInstance(contextId, serviceType);

    instance ??= Activator.CreateInstance(serviceType);
    return instance;
}
```

<span data-ttu-id="fe52a-214">Sonraki önemli adım,, `InstanceContextExtension` `InstanceContextInitializer` ve `InstanceProvider` sınıflarını hizmet modeli çalışma zamanına yüklemektir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-214">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer`, and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="fe52a-215">Davranışı yüklemek için hizmet uygulama sınıflarını işaretlemek üzere özel bir öznitelik kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-215">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="fe52a-216">, `DurableInstanceContextAttribute` Bu özniteliğin uygulamasını içerir ve `IServiceBehavior` tüm hizmet çalışma zamanını genişletmek için arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="fe52a-216">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>

<span data-ttu-id="fe52a-217">Bu sınıf, kullanılacak depolama Yöneticisi türünü kabul eden bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-217">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="fe52a-218">Bu şekilde, uygulama, kullanıcıların kendi `IStorageManager` uygulamasını bu özniteliğin parametresi olarak belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe52a-218">In this way, the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>

<span data-ttu-id="fe52a-219">`ApplyDispatchBehavior`Uygulamada, `InstanceContextMode` geçerli `ServiceBehavior` özniteliğin doğrulanması doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="fe52a-219">In the `ApplyDispatchBehavior` implementation, the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="fe52a-220">Bu özellik Singleton olarak ayarlandıysa, dayanıklı örnek oluşturma mümkün değildir ve `InvalidOperationException` konağa bildirimde bulunan bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fe52a-220">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>

```csharp
ServiceBehaviorAttribute serviceBehavior =
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();

if (serviceBehavior != null &&
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)
{
    throw new InvalidOperationException(
       ResourceHelper.GetString("ExSingletonInstancingNotSupported"));
}
```

<span data-ttu-id="fe52a-221">Bu, Depolama Yöneticisi örnekleri, örnek bağlam başlatıcısı ve örnek sağlayıcı, `DispatchRuntime` her bitiş noktası için oluşturulan ' de oluşturulur ve yüklenir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-221">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>

```csharp
IStorageManager storageManager =
    StorageManagerFactory.GetStorageManager(storageManagerType);

InstanceContextInitializer contextInitializer =
    new InstanceContextInitializer(storageManager);

InstanceProvider instanceProvider =
    new InstanceProvider(description.ServiceType);

foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
{
    ChannelDispatcher cd = cdb as ChannelDispatcher;

    if (cd != null)
    {
        foreach (EndpointDispatcher ed in cd.Endpoints)
        {
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);
            ed.DispatchRuntime.InstanceProvider = instanceProvider;
        }
    }
}
```

<span data-ttu-id="fe52a-222">Özet bölümünde bu örnek, özel bağlam KIMLIĞI alışverişi için özel hat protokolünü destekleyen bir kanal üretti ve ayrıca, kalıcı depolama alanından örnekleri yüklemek için varsayılan örnek oluşturma davranışının üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="fe52a-222">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>

<span data-ttu-id="fe52a-223">Sol taraf, hizmet örneğini kalıcı depolamaya kaydetmek için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="fe52a-223">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="fe52a-224">Daha önce anlatıldığı gibi, durumu bir uygulamada kaydetmek için gerekli işlevler zaten vardır `IStorageManager` .</span><span class="sxs-lookup"><span data-stu-id="fe52a-224">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="fe52a-225">Şimdi bunu WCF çalışma zamanı ile tümleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-225">We now must integrate this with the WCF runtime.</span></span> <span data-ttu-id="fe52a-226">Hizmet uygulama sınıfındaki yöntemler için geçerli olan başka bir öznitelik gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-226">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="fe52a-227">Bu özniteliğin, hizmet örneğinin durumunu değiştiren yöntemlere uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-227">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>

<span data-ttu-id="fe52a-228">`SaveStateAttribute`Sınıfı bu işlevi uygular.</span><span class="sxs-lookup"><span data-stu-id="fe52a-228">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="fe52a-229">`IOperationBehavior`Her işlem IÇIN WCF çalışma zamanını değiştirmek için sınıfını da uygular.</span><span class="sxs-lookup"><span data-stu-id="fe52a-229">It also implements `IOperationBehavior` class to modify the WCF runtime for each operation.</span></span> <span data-ttu-id="fe52a-230">Bir yöntem Bu öznitelikle işaretlendiğinde, uygun durumdayken WCF çalışma zamanı `ApplyBehavior` yöntemini çağırır `DispatchOperation` .</span><span class="sxs-lookup"><span data-stu-id="fe52a-230">When a method is marked with this attribute, the WCF runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="fe52a-231">Bu yöntem uygulamasında tek bir kod satırı vardır:</span><span class="sxs-lookup"><span data-stu-id="fe52a-231">There is a single line of code in this method implementation:</span></span>

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

<span data-ttu-id="fe52a-232">Bu yönerge, türünün bir örneğini oluşturur `OperationInvoker` ve bu `Invoker` özelliği oluşturulan özelliğine atar `DispatchOperation` .</span><span class="sxs-lookup"><span data-stu-id="fe52a-232">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="fe52a-233">`OperationInvoker`Sınıfı, için oluşturulan varsayılan işlem için bir sarmalayıcıdır `DispatchOperation` .</span><span class="sxs-lookup"><span data-stu-id="fe52a-233">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="fe52a-234">Bu sınıf, `IOperationInvoker` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="fe52a-234">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="fe52a-235">`Invoke`Yöntem uygulamasında gerçek Yöntem çağrısı, iç işlem uyarlaması için temsilci olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fe52a-235">In the `Invoke` method implementation, the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="fe52a-236">Ancak, sonuçları döndürmeden önce içindeki Depolama Yöneticisi, `InstanceContext` hizmet örneğini kaydetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-236">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>

```csharp
object result = innerOperationInvoker.Invoke(instance,
    inputs, out outputs);

// Save the instance using the storage manager saved in the
// current InstanceContext.
InstanceContextExtension extension =
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();

extension.StorageManager.SaveInstance(extension.ContextId, instance);
return result;
```

## <a name="using-the-extension"></a><span data-ttu-id="fe52a-237">Uzantıyı kullanma</span><span class="sxs-lookup"><span data-stu-id="fe52a-237">Using the Extension</span></span>

<span data-ttu-id="fe52a-238">Hem kanal katmanı hem de hizmet modeli katman uzantıları gerçekleştirilir ve bunlar artık WCF uygulamalarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-238">Both the channel layer and service model layer extensions are done and they can now be used in WCF applications.</span></span> <span data-ttu-id="fe52a-239">Hizmetler, kanalı bir özel bağlama kullanarak kanal yığınına eklemeli ve ardından hizmet uygulama sınıflarını uygun özniteliklerle işaretmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-239">Services must add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>

```csharp
[DurableInstanceContext]
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class ShoppingCart : IShoppingCart
{
//…
     [SaveState]
     public int AddItem(string item)
     {
         //…
     }
//…
 }
```

<span data-ttu-id="fe52a-240">İstemci uygulamaları, özel bağlama kullanarak DurableInstanceContextChannel öğesini kanal yığınına eklememelidir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-240">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="fe52a-241">Kanalı yapılandırma dosyasında bildirimli olarak yapılandırmak için bağlama öğesi bölümünün bağlama öğesi uzantıları koleksiyonuna eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-241">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>

```xml
<system.serviceModel>
 <extensions>
   <bindingElementExtensions>
     <add name="durableInstanceContext"
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>
   </bindingElementExtensions>
 </extensions>
</system.serviceModel>
```

<span data-ttu-id="fe52a-242">Şimdi bağlama öğesi, diğer standart bağlama öğeleri gibi özel bir bağlama ile kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="fe52a-242">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>

```xml
<bindings>
 <customBinding>
   <binding name="TextOverHttp">
     <durableInstanceContext contextType="HttpCookie"/>
     <reliableSession />
     <textMessageEncoding />
     <httpTransport />
   </binding>
 </customBinding>
</bindings>
```

## <a name="conclusion"></a><span data-ttu-id="fe52a-243">Sonuç</span><span class="sxs-lookup"><span data-stu-id="fe52a-243">Conclusion</span></span>

<span data-ttu-id="fe52a-244">Bu örnek, bir özel protokol kanalının nasıl oluşturulacağını ve hizmet davranışının etkinleştirmek için nasıl özelleştirileceğini gösterdi.</span><span class="sxs-lookup"><span data-stu-id="fe52a-244">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>

<span data-ttu-id="fe52a-245">Uzantı, kullanıcıların `IStorageManager` bir yapılandırma bölümü kullanarak uygulamayı belirtmelerine izin vererek daha da iyileştirilen olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-245">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="fe52a-246">Bu, hizmet kodunu yeniden derlemeden yedekleme mağazasının değiştirilmesini olanaklı kılar.</span><span class="sxs-lookup"><span data-stu-id="fe52a-246">This makes it possible to modify the backing store without recompiling the service code.</span></span>

<span data-ttu-id="fe52a-247">Ayrıca, örneğin durumunu kapsülleyen bir sınıfı (örneğin,) uygulamayı deneyebilirsiniz `StateBag` .</span><span class="sxs-lookup"><span data-stu-id="fe52a-247">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="fe52a-248">Bu sınıf, her değiştiğinde durumu kalıcı hale getirmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="fe52a-248">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="fe52a-249">Bu şekilde özniteliği kullanmaktan kaçınabilirsiniz `SaveState` ve kalıcı çalışmayı daha doğru şekilde gerçekleştirebilirsiniz (örneğin, özniteliğe sahip bir yöntem çağrıldığında her seferinde bu durum kaydedilmeden durumu kalıcı hale getirebilirsiniz `SaveState` ).</span><span class="sxs-lookup"><span data-stu-id="fe52a-249">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>

<span data-ttu-id="fe52a-250">Örneği çalıştırdığınızda aşağıdaki çıktı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-250">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="fe52a-251">İstemci, alışveriş sepetine iki öğe ekler ve ardından hizmet üzerinden alışveriş sepetindeki öğelerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="fe52a-251">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="fe52a-252">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fe52a-252">Press ENTER in each console window to shut down the service and client.</span></span>

```console
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> <span data-ttu-id="fe52a-253">Hizmeti yeniden oluşturmak veritabanı dosyasının üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="fe52a-253">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="fe52a-254">Örneğin birden fazla çalıştırması genelinde korunan durumu gözlemlemek için, çalıştırmaları arasında örneği yeniden derlemediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fe52a-254">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fe52a-255">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fe52a-255">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="fe52a-256">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fe52a-256">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="fe52a-257">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fe52a-257">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="fe52a-258">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fe52a-258">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="fe52a-259">Bu örneği çalıştırmak için SQL Server 2005 veya SQL Express 2005 çalıştırıyor olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-259">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="fe52a-260">SQL Server 2005 çalıştırıyorsanız, hizmetin bağlantı dizesinin yapılandırmasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-260">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="fe52a-261">Çapraz makine çalışırken, yalnızca sunucu makinesinde SQL Server gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-261">When running cross-machine, SQL Server is only required on the server machine.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fe52a-262">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe52a-262">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fe52a-263">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fe52a-263">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="fe52a-264">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fe52a-264">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fe52a-265">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fe52a-265">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`
