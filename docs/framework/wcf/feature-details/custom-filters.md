---
description: 'Daha fazla bilgi edinin: özel filtreler'
title: Özel Filtreler
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 95a419823cf69575f951c0984e2136f9e7afca56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704985"
---
# <a name="custom-filters"></a><span data-ttu-id="5636b-103">Özel Filtreler</span><span class="sxs-lookup"><span data-stu-id="5636b-103">Custom Filters</span></span>

<span data-ttu-id="5636b-104">Özel filtreler, sistem tarafından sağlanmış ileti filtreleri kullanılarak gerçekleştiresağlanmayan eşleşen mantığı tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5636b-104">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="5636b-105">Örneğin, belirli bir ileti öğesini karma hale getirmek için bir özel filtre oluşturabilir ve sonra filtrenin true veya false olarak döndürülüp döndürülmeyeceğini tespit etmek için değeri incelemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="5636b-105">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="5636b-106">Uygulama</span><span class="sxs-lookup"><span data-stu-id="5636b-106">Implementation</span></span>  

 <span data-ttu-id="5636b-107">Özel filtre <xref:System.ServiceModel.Dispatcher.MessageFilter> soyut temel sınıfın bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="5636b-107">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="5636b-108">Özel filtrenizi uygularken, Oluşturucu isteğe bağlı olarak tek bir dize parametresini kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="5636b-108">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="5636b-109">Bu parametre, filtre uygulamak için filtrenin çalışma zamanında ihtiyacı olan herhangi bir değer veya yapılandırma sağlamak üzere MessageFilter oluşturucusuna geçirilen yapılandırma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5636b-109">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="5636b-110">Örneğin, bu, filtrenin değerlendirilen ileti içinde aradığı bir değer sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5636b-110">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="5636b-111">Aşağıdaki örnek, bir dize parametresini kabul eden özel bir ileti filtresinin temel bir uygulamasını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="5636b-111">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="5636b-112">Gerçek bir uygulamada, eşleşme yöntemi (ler), bu ileti filtresinin **true** veya **false** döndürmesi gerekip gerekmediğini belirleyecek şekilde iletiyi inceleyecek mantığı içerir.</span><span class="sxs-lookup"><span data-stu-id="5636b-112">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="5636b-113">Performans</span><span class="sxs-lookup"><span data-stu-id="5636b-113">Performance</span></span>  

 <span data-ttu-id="5636b-114">Özel bir filtre uygularken, filtrenin bir ileti değerlendirmesini tamamlaması için gereken en uzun süreyi dikkate almanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5636b-114">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="5636b-115">Bir ileti bir eşleşme bulunamadığı için birden çok filtreye karşı değerlendirilebileceğinizden, tüm filtreler hesaplanmadan önce istemci isteğinin zaman aşımına memesini sağlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5636b-115">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="5636b-116">Bu nedenle, özel bir filtrenin filtre ölçütleriyle eşleşip eşleşmediğini anlamak için yalnızca bir iletinin içeriğini veya özniteliklerini değerlendirmek için gereken kodu içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5636b-116">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="5636b-117">Genel olarak, bir özel filtre uygularken aşağıdakilerden kaçınmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="5636b-117">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="5636b-118">Verileri diske veya bir veritabanına kaydetme gibi GÇ.</span><span class="sxs-lookup"><span data-stu-id="5636b-118">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="5636b-119">Belgedeki birden çok kayıt üzerinde döngü gibi gereksiz işleme.</span><span class="sxs-lookup"><span data-stu-id="5636b-119">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="5636b-120">Paylaşılan kaynaklar üzerinde bir kilit elde etmek veya bir veritabanında arama gerçekleştirmek için gereken çağrılar gibi engelleyici işlemler.</span><span class="sxs-lookup"><span data-stu-id="5636b-120">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="5636b-121">Bir üretim ortamında özel bir filtre kullanmadan önce, filtrenin bir iletiyi değerlendirmek için aldığı ortalama süreyi öğrenmek için performans testlerini çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="5636b-121">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="5636b-122">Filtre tablosunda kullanılan diğer filtrelerin ortalama işlem süresi ile birleştirildiğinde, bu, istemci uygulaması tarafından belirtilmesi gereken en büyük zaman aşımı değerini doğru bir şekilde belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5636b-122">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="5636b-123">Kullanım</span><span class="sxs-lookup"><span data-stu-id="5636b-123">Usage</span></span>  

 <span data-ttu-id="5636b-124">Özel filtrenizi yönlendirme hizmetiyle kullanabilmeniz için, "Custom" türünde yeni bir filtre girişi belirterek filtre tablosuna eklemeniz gerekir, ileti filtresinin tam tür adı ve derlemenizin adı.</span><span class="sxs-lookup"><span data-stu-id="5636b-124">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="5636b-125">Diğer MessageFilters gibi, özel filtreniz yapıcısına geçirilecek olan filterData dizesini de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5636b-125">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="5636b-126">Aşağıdaki örneklerde, yönlendirme hizmeti ile özel bir filtrenin kullanılması gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5636b-126">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"
            customType="CustomAssembly.MyMessageFilter,
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
