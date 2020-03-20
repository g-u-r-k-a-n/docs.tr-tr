---
title: Akış Gerçekleştirme Örneği
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 7a887fa1eceac4d8ee323f03fd5bc536bb1dc579
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143973"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="dca76-102">Akış Gerçekleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="dca76-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="dca76-103">Bu örnek, çok sayıda öğe içeren sendikasyon akışlarının nasıl yönetilenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dca76-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="dca76-104">Sunucuda, örnek, öğe ağ akışına yazılmadan hemen önceye kadar besleme içindeki tek tek <xref:System.ServiceModel.Syndication.SyndicationItem> nesnelerin oluşturulmasını nasıl geciktirleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dca76-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="dca76-105">İstemci de örnek, okunan özet akışının hiçbir zaman belleğe tam olarak arabelleğe alınmaması için ağ akışındaki tek tek öğeleri okumak için özel bir sendikasyon akışı nın nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dca76-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="dca76-106">Sendikasyon API'sının akış yeteneğini en iyi şekilde göstermek için, bu örnek, sunucunun sonsuz sayıda öğe içeren bir akışı ortaya çıkardığı olası olmayan bir senaryo kullanır.</span><span class="sxs-lookup"><span data-stu-id="dca76-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="dca76-107">Bu durumda, istemcinin akıştan belirli sayıda öğe okuduğunu belirleyene kadar sunucu özet akışına yeni öğeler üretmeye devam eder (varsayılan olarak, 10).</span><span class="sxs-lookup"><span data-stu-id="dca76-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="dca76-108">Basitlik için, istemci ve sunucu aynı işlemde uygulanır ve istemcinin kaç öğe ürettiğini izlemek için paylaşılan `ItemCounter` bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="dca76-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="dca76-109">Tür, `ItemCounter` yalnızca örnek senaryonun temiz bir şekilde sonlandırılmasına izin vermek amacıyla vardır ve gösterilen desenin temel öğesi değildir.</span><span class="sxs-lookup"><span data-stu-id="dca76-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="dca76-110">Gösteri, Visual C# yineleyicilerini `yield return` (anahtar kelime yapısı kullanarak) kullanır.</span><span class="sxs-lookup"><span data-stu-id="dca76-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="dca76-111">Yineleyiciler hakkında daha fazla bilgi için MSDN'deki "Yineleyicileri Kullanma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="dca76-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="dca76-112">Hizmet</span><span class="sxs-lookup"><span data-stu-id="dca76-112">Service</span></span>  
 <span data-ttu-id="dca76-113">Hizmet, aşağıdaki kodda gösterildiği gibi, tek bir işlemden oluşan temel <xref:System.ServiceModel.Web.WebGetAttribute> bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="dca76-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="dca76-114">Hizmet, aşağıdaki kodda gösterildiği `ItemGenerator` gibi bir yineleyici kullanarak <xref:System.ServiceModel.Syndication.SyndicationItem> olası sonsuz bir örnek akışı oluşturmak için bir sınıf kullanarak bu sözleşmeyi uygular.</span><span class="sxs-lookup"><span data-stu-id="dca76-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```csharp
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="dca76-115">Hizmet uygulaması özet akışı oluşturduğunda, `ItemGenerator.GenerateItems()` arabelleğe alan madde koleksiyonu yerine çıktı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dca76-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```csharp
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
```  
  
 <span data-ttu-id="dca76-116">Sonuç olarak, öğe akışı hiçbir zaman tam olarak belleğe arabelleğe almaz.</span><span class="sxs-lookup"><span data-stu-id="dca76-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="dca76-117">Yöntemin `yield return` `ItemGenerator.GenerateItems()` içindeki deyime bir kesme noktası ayarlayarak ve hizmet `StreamedFeed()` yöntemin sonucunu döndürdikten sonra bu kesme noktasına ilk kez rastlandığını belirterek bu davranışı gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dca76-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="dca76-118">İstemci</span><span class="sxs-lookup"><span data-stu-id="dca76-118">Client</span></span>  
 <span data-ttu-id="dca76-119">Bu örnekteki istemci, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> bunları belleğe arabelleğe almak yerine akıştaki tek tek öğelerin somutlaştırılmasını geciktiren özel bir uygulama kullanır.</span><span class="sxs-lookup"><span data-stu-id="dca76-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="dca76-120">Özel `StreamedAtom10FeedFormatter` örnek aşağıdaki gibi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dca76-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="dca76-121">Normalde, özet akışı <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> içeriğinin tamamı ağdan okunup belleğe arabelleğe alınana kadar bir çağrı geri dönmez.</span><span class="sxs-lookup"><span data-stu-id="dca76-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="dca76-122">Ancak, `StreamedAtom10FeedFormatter` nesne aşağıdaki <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> kodda gösterildiği gibi arabelleğe alan bir koleksiyon yerine bir yineleyici döndürmek için geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="dca76-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```csharp  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
```  
  
 <span data-ttu-id="dca76-123">Sonuç olarak, sonuçları `ReadItems()` geçiş istemci uygulaması kullanmaya hazır olana kadar her öğe ağdan okunmaz.</span><span class="sxs-lookup"><span data-stu-id="dca76-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="dca76-124">Bu davranışı, içindeki deyime `yield return` bir kesme noktası `StreamedAtom10FeedFormatter.DelayReadItems()` ayarlayarak ve bu kesme noktasının `ReadFrom()` çağrı tamamlandıktan sonra ilk kez karşılaşılan olduğunu fark ederek bu davranışı gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dca76-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="dca76-125">Aşağıdaki yönergeler, örneğin nasıl oluşturup çalıştırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dca76-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="dca76-126">Sunucu, istemci 10 öğe okuduktan sonra öğe oluşturmayı durdursa da, çıktının istemcinin önemli ölçüde 10'dan fazla öğe okuduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dca76-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="dca76-127">Bunun nedeni, örnek tarafından kullanılan ağ bağlamanın verileri dört kilobaytlık (KB) segmentlerde iletmesidir.</span><span class="sxs-lookup"><span data-stu-id="dca76-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="dca76-128">Bu nedenle, istemci bir öğeyi bile okuma fırsatı nasahip olmadan önce 4KB madde verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="dca76-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="dca76-129">Bu normal davranıştır (akışlı HTTP verilerini makul boyutlu segmentlerde göndermek performansı artırır).</span><span class="sxs-lookup"><span data-stu-id="dca76-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dca76-130">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="dca76-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="dca76-131">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="dca76-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="dca76-132">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="dca76-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="dca76-133">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="dca76-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dca76-134">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="dca76-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="dca76-135">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="dca76-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dca76-136">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="dca76-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dca76-137">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="dca76-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="dca76-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dca76-138">See also</span></span>

- [<span data-ttu-id="dca76-139">Bağımsız Tanılama Akışı</span><span class="sxs-lookup"><span data-stu-id="dca76-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
