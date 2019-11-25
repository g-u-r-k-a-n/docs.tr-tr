---
title: Zaman Uyumlu ve Zaman Uyumsuz İşlemler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: 39a7db3fb7dc3651f2cf6c850e7ebb5525e24963
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281626"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="73ac9-102">Zaman Uyumlu ve Zaman Uyumsuz İşlemler</span><span class="sxs-lookup"><span data-stu-id="73ac9-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="73ac9-103">Bu konuda, zaman uyumsuz hizmet işlemlerini uygulama ve çağırma ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73ac9-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="73ac9-104">Birçok uygulama yöntemi zaman uyumsuz olarak çağırır, çünkü Yöntem çağrısı çalıştırılırken uygulamanın faydalı iş yapmaya devam etmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="73ac9-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="73ac9-105">Windows Communication Foundation (WCF) Hizmetleri ve istemcileri, uygulamanın iki farklı düzeyinde zaman uyumsuz işlem çağrılarına katılabilir ve bu da, WCF uygulamalarının etkileşime karşı dengeli hale getirme hızını en üst düzeye çıkarmak için daha fazla esneklik sağlar .</span><span class="sxs-lookup"><span data-stu-id="73ac9-105">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="73ac9-106">Zaman uyumsuz Işlem türleri</span><span class="sxs-lookup"><span data-stu-id="73ac9-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="73ac9-107">WCF 'deki tüm hizmet sözleşmeleri, parametre türleri ve dönüş değerleri ne olduğuna bakılmaksızın, istemci ve hizmet arasında belirli bir ileti değişim modelini belirtmek için WCF özniteliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="73ac9-107">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="73ac9-108">WCF gelen ve giden iletileri otomatik olarak uygun hizmet işlemine yönlendirir veya istemci kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="73ac9-108">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="73ac9-109">İstemci yalnızca belirli bir işlem için ileti değişim modelini belirten hizmet sözleşmesine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="73ac9-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="73ac9-110">Temel alınan ileti değişim modeli gözlemlendiği sürece, istemciler geliştiriciyi istedikleri programlama modeline sunabilir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="73ac9-111">Bu nedenle, çok sayıda, belirtilen ileti deseninin gözlemlendiği sürece işlemleri herhangi bir şekilde uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="73ac9-112">Hizmet sözleşmesinin hizmet veya istemci uygulamasından bağımsız olması, WCF uygulamalarında aşağıdaki zaman uyumsuz yürütme biçimlerini sunar:</span><span class="sxs-lookup"><span data-stu-id="73ac9-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
- <span data-ttu-id="73ac9-113">İstemciler zaman uyumsuz olarak istek/yanıt işlemlerini zaman uyumsuz bir ileti değişimi kullanarak çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="73ac9-114">Hizmetler, zaman uyumsuz bir ileti alışverişi kullanarak istek/yanıt işlemini zaman uyumsuz olarak uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="73ac9-115">İleti alışverişi, istemci veya hizmet uygulanmadığına bakılmaksızın tek yönlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="73ac9-116">Önerilen zaman uyumsuz senaryolar</span><span class="sxs-lookup"><span data-stu-id="73ac9-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="73ac9-117">İşlem hizmeti kullanımı, g/ç işi gibi bir engelleme çağrısı yapıyorsa, bir hizmet işlemi uygulamasında zaman uyumsuz bir yaklaşım kullanın.</span><span class="sxs-lookup"><span data-stu-id="73ac9-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="73ac9-118">Zaman uyumsuz bir işlem uygulamasında olduğunuzda, zaman uyumsuz çağrı yolunu mümkün olduğunca uzatmak için zaman uyumsuz işlemleri ve yöntemleri çağırmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="73ac9-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="73ac9-119">Örneğin, `BeginOperationOne()`içinden bir `BeginOperationTwo()` çağırın.</span><span class="sxs-lookup"><span data-stu-id="73ac9-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
- <span data-ttu-id="73ac9-120">Bir istemcide zaman uyumsuz bir yaklaşım kullanın veya aşağıdaki durumlarda uygulama çağırma:</span><span class="sxs-lookup"><span data-stu-id="73ac9-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
- <span data-ttu-id="73ac9-121">İşlemleri bir orta katmanlı uygulamadan çağırdıysanız.</span><span class="sxs-lookup"><span data-stu-id="73ac9-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="73ac9-122">(Bu senaryolar hakkında daha fazla bilgi için bkz. [Orta katman Istemci uygulamaları](./feature-details/middle-tier-client-applications.md).)</span><span class="sxs-lookup"><span data-stu-id="73ac9-122">(For more information about such scenarios, see [Middle-Tier Client Applications](./feature-details/middle-tier-client-applications.md).)</span></span>  
  
- <span data-ttu-id="73ac9-123">İşlemleri bir ASP.NET sayfasında çağırdıysanız zaman uyumsuz sayfalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="73ac9-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
- <span data-ttu-id="73ac9-124">Windows Forms veya Windows Presentation Foundation (WPF) gibi tek iş parçacıklı herhangi bir uygulamadan işlem çağırdıysanız.</span><span class="sxs-lookup"><span data-stu-id="73ac9-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="73ac9-125">Olay tabanlı zaman uyumsuz çağrı modelini kullanırken, sonuç olayı kullanıcı arabirimi iş parçacığında tetiklenir ve birden çok iş parçacığını kendiniz işleyebilmeniz gerekmeden uygulamaya yanıt verme işlemi yapılır.</span><span class="sxs-lookup"><span data-stu-id="73ac9-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
- <span data-ttu-id="73ac9-126">Genel olarak, zaman uyumlu ve zaman uyumsuz çağrı arasında seçim yaptıysanız, zaman uyumsuz çağrıyı seçin.</span><span class="sxs-lookup"><span data-stu-id="73ac9-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="73ac9-127">Zaman uyumsuz bir hizmet Işlemi uygulama</span><span class="sxs-lookup"><span data-stu-id="73ac9-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="73ac9-128">Zaman uyumsuz işlemler, aşağıdaki üç yöntemden biri kullanılarak uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="73ac9-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1. <span data-ttu-id="73ac9-129">Görev tabanlı zaman uyumsuz model</span><span class="sxs-lookup"><span data-stu-id="73ac9-129">The task-based asynchronous pattern</span></span>  
  
2. <span data-ttu-id="73ac9-130">Olay tabanlı zaman uyumsuz model</span><span class="sxs-lookup"><span data-stu-id="73ac9-130">The event-based asynchronous pattern</span></span>  
  
3. <span data-ttu-id="73ac9-131">IAsyncResult zaman uyumsuz model</span><span class="sxs-lookup"><span data-stu-id="73ac9-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="73ac9-132">Görev tabanlı zaman uyumsuz model</span><span class="sxs-lookup"><span data-stu-id="73ac9-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="73ac9-133">Görev tabanlı zaman uyumsuz model, zaman uyumsuz işlemleri uygulamak için tercih edilen bir yoldur çünkü en kolay ve en basit yoldur.</span><span class="sxs-lookup"><span data-stu-id="73ac9-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="73ac9-134">Bu yöntemi kullanmak için yalnızca hizmet işleminizi uygulayın ve\<T > görevin bir dönüş türünü belirtin; burada T mantıksal işlem tarafından döndürülen türdür.</span><span class="sxs-lookup"><span data-stu-id="73ac9-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="73ac9-135">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="73ac9-135">For example:</span></span>  
  
```csharp  
public class SampleService:ISampleService   
{   
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)   
   {   
      return Task<string>.Factory.StartNew(() =>   
      {   
         return msg;   
      });   
   }  
   // ...  
}  
```  
  
 <span data-ttu-id="73ac9-136">SampleMethodTaskAsync işlemi, mantıksal işlem bir dize döndürdüğünden\<dize > döndürür.</span><span class="sxs-lookup"><span data-stu-id="73ac9-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="73ac9-137">Görev tabanlı zaman uyumsuz model hakkında daha fazla bilgi için, bkz. [görev tabanlı zaman uyumsuz model](https://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="73ac9-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="73ac9-138">Görev tabanlı zaman uyumsuz model kullanılırken, işlemin tamamlanması beklenirken bir özel durum oluşursa bir T:System.AggregateException oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="73ac9-139">Bu özel durum istemci veya hizmetlerde oluşabilir</span><span class="sxs-lookup"><span data-stu-id="73ac9-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="73ac9-140">Olay tabanlı zaman uyumsuz model</span><span class="sxs-lookup"><span data-stu-id="73ac9-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="73ac9-141">Olay tabanlı zaman uyumsuz deseninin desteklendiği bir hizmetin MethodNameAsync adlı bir veya daha fazla işlemi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="73ac9-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="73ac9-142">Bu yöntemler, geçerli iş parçacığında aynı işlemi gerçekleştiren zaman uyumlu sürümleri yansıtabilir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="73ac9-143">Sınıfta Ayrıca bir MethodNameCompleted olayı olabilir ve bir MethodNameAsyncCancel (ya da yalnızca bir algıladığında Lasync) yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="73ac9-144">İşlemi çağırmak isteyen bir istemci, işlem tamamlandığında çağrılacak bir olay işleyicisi tanımlar,</span><span class="sxs-lookup"><span data-stu-id="73ac9-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="73ac9-145">Aşağıdaki kod parçacığında, olay tabanlı zaman uyumsuz model kullanılarak zaman uyumsuz işlemlerin nasıl bildirildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 <span data-ttu-id="73ac9-146">Olay tabanlı zaman uyumsuz model hakkında daha fazla bilgi için bkz. [olay tabanlı zaman uyumsuz model](https://go.microsoft.com/fwlink/?LinkId=232515).</span><span class="sxs-lookup"><span data-stu-id="73ac9-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232515).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="73ac9-147">IAsyncResult zaman uyumsuz model</span><span class="sxs-lookup"><span data-stu-id="73ac9-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="73ac9-148">Bir hizmet işlemi .NET Framework zaman uyumsuz programlama modelini kullanarak zaman uyumsuz bir biçimde uygulanabilir ve `<Begin>` yöntemi <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliği `true`olarak işaretleniyor.</span><span class="sxs-lookup"><span data-stu-id="73ac9-148">A service operation can be implemented in an asynchronous fashion using the .NET Framework asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="73ac9-149">Bu durumda, zaman uyumsuz işlem eşzamanlı bir işlemle aynı biçimde meta verilerde kullanıma sunulur: istek iletisi ve bağıntılı yanıt iletisi ile tek bir işlem olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="73ac9-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="73ac9-150">İstemci programlama modellerinin bir seçimi vardır.</span><span class="sxs-lookup"><span data-stu-id="73ac9-150">Client programming models then have a choice.</span></span> <span data-ttu-id="73ac9-151">Bu model, zaman uyumlu bir işlem olarak veya zaman uyumsuz bir işlem olarak temsil edebilirler, bu nedenle hizmetin bir istek çağrıldığı zaman yanıt iletisi değişimi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="73ac9-152">Genel olarak, sistemlerin zaman uyumsuz doğası ile iş parçacıkları üzerinde bir bağımlılık almanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="73ac9-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="73ac9-153">İşlem gönderme işleminin çeşitli aşamalarına veri geçirmenin en güvenilir yolu, uzantıları kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="73ac9-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="73ac9-154">Bir örnek için bkz. [nasıl yapılır: zaman uyumsuz bir hizmet Işlemi uygulama](how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="73ac9-154">For an example, see [How to: Implement an Asynchronous Service Operation](how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="73ac9-155">İstemci uygulamasında nasıl çağrdığına bakılmaksızın zaman uyumsuz olarak yürütülen `X` bir sözleşme işlemi tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="73ac9-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
- <span data-ttu-id="73ac9-156">`BeginOperation` ve `EndOperation`düzenlerini kullanarak iki yöntem tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="73ac9-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
- <span data-ttu-id="73ac9-157">`BeginOperation` yöntemi, işlem için `in` ve `ref` parametrelerini içerir ve bir <xref:System.IAsyncResult> türü döndürür.</span><span class="sxs-lookup"><span data-stu-id="73ac9-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
- <span data-ttu-id="73ac9-158">`EndOperation` yöntemi, `out` ve `ref` parametrelerinin yanı sıra <xref:System.IAsyncResult> bir parametre içerir ve işlemler dönüş türünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="73ac9-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="73ac9-159">Örneğin, aşağıdaki yöntemine bakın.</span><span class="sxs-lookup"><span data-stu-id="73ac9-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="73ac9-160">Zaman uyumsuz bir işlem oluşturmak için iki yöntem şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="73ac9-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]
IAsyncResult BeginDoWork(string data,
                         ref string inout,
                         AsyncCallback callback,
                         object state);
int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>
Function BeginDoWork(ByVal data As String, _
                     ByRef inout As String, _
                     ByVal callback As AsyncCallback, _
                     ByVal state As Object) As IAsyncResult
Function EndDoWork(ByRef inout As String, ByRef outonly As String, ByVal result As IAsyncResult) As Integer  
```  
  
> [!NOTE]
> <span data-ttu-id="73ac9-161"><xref:System.ServiceModel.OperationContractAttribute> özniteliği yalnızca `BeginDoWork` yöntemine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="73ac9-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="73ac9-162">Elde edilen sözleşmede `DoWork`adlı bir WSDL işlemi vardır.</span><span class="sxs-lookup"><span data-stu-id="73ac9-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="73ac9-163">İstemci tarafı zaman uyumsuz çağırmaları</span><span class="sxs-lookup"><span data-stu-id="73ac9-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="73ac9-164">WCF istemci uygulaması, daha önce açıklanan üç zaman uyumsuz çağrı modelini kullanabilir</span><span class="sxs-lookup"><span data-stu-id="73ac9-164">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="73ac9-165">Görev tabanlı modeli kullanırken, aşağıdaki kod parçacığında gösterildiği gibi await anahtar sözcüğünü kullanarak işlemi çağırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="73ac9-166">Olay tabanlı zaman uyumsuz düzenin kullanılması yalnızca yanıtın bildirimini almak için bir olay işleyicisinin eklenmesini gerektirir ve sonuçta elde edilen olay kullanıcı arabirimi iş parçacığında otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="73ac9-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="73ac9-167">Bu yaklaşımı kullanmak için, aşağıdaki örnekte olduğu gibi, **/Async** ve **/tcv: Version35** komut seçeneklerini [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)ile birlikte belirtin.</span><span class="sxs-lookup"><span data-stu-id="73ac9-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="73ac9-168">Bu tamamlandığında, Svcutil. exe, çağıran uygulamanın, yanıtı almak ve uygun eylemi gerçekleştirmek için bir olay işleyicisi uygulayıp atamasını sağlayan olay altyapısına sahip bir WCF istemci sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73ac9-168">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="73ac9-169">Tüm bir örnek için bkz. [nasıl yapılır: hizmet Işlemlerini zaman uyumsuz olarak çağırma](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="73ac9-169">For a complete example, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="73ac9-170">Ancak, olay tabanlı zaman uyumsuz model yalnızca .NET Framework 3,5 ' de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-170">The event-based asynchronous model, however, is only available in .NET Framework 3.5.</span></span> <span data-ttu-id="73ac9-171">Ayrıca, bir <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>kullanılarak WCF istemci kanalı oluşturulduğunda .NET Framework 3,5 ' de de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="73ac9-171">In addition, it is not supported even in .NET Framework 3.5 when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73ac9-172">WCF istemci kanalı nesneleri ile işlemlerinizi zaman uyumsuz olarak çağırmak için <xref:System.IAsyncResult?displayProperty=nameWithType> nesneleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-172">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="73ac9-173">Bu yaklaşımı kullanmak için, aşağıdaki örnekte olduğu gibi [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)ile **/Async** komut seçeneğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="73ac9-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 <span data-ttu-id="73ac9-174">Bu, her bir işlemin, <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliği `true` ve karşılık gelen bir `<End>` yöntemi olarak ayarlandığı `<Begin>` yöntemi olarak modellendiği bir hizmet sözleşmesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73ac9-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="73ac9-175"><xref:System.ServiceModel.ChannelFactory%601>kullanan bir örnek için bkz. [nasıl yapılır: bir kanal fabrikası kullanarak Işlemleri zaman uyumsuz olarak çağırma](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="73ac9-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="73ac9-176">Her iki durumda da, bir uygulamanın zaman uyumsuz olarak yerel bir zaman uyumlu yöntemi çağırmak için aynı şekli kullanabilmesi gibi, uygulamalar zaman uyumsuz olarak bir işlemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="73ac9-177">İşlemin nasıl uygulandığı, istemci için önemli değildir; Yanıt iletisi geldiğinde, içeriği istemcinin zaman uyumsuz <`End`> yöntemine gönderilir ve istemci bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="73ac9-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="73ac9-178">Tek yönlü Ileti değişimi desenleri</span><span class="sxs-lookup"><span data-stu-id="73ac9-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="73ac9-179">Ayrıca, tek yönlü işlemlerin (<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> `true` ilişkili yanıt olmayan işlemler) istemci ya da hizmet tarafından diğer taraftan bağımsız olarak gönderilebileceği zaman uyumsuz ileti değişim düzenlerini de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73ac9-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="73ac9-180">(Bu, çift yönlü ileti değişim modelini tek yönlü iletilerle kullanır.) Bu durumda, hizmet sözleşmesi, her iki tarafın da uygun olmayan zaman uyumsuz çağrılar veya uygulamalar olarak uygulayabilirler tek yönlü bir ileti değişimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="73ac9-181">Genellikle, sözleşme tek yönlü bir ileti alışverişi olduğunda, bir ileti gönderildiğinde uygulama bir yanıt beklemez ve diğer işleri yapmaya devam edebileceğinden uygulamalar büyük ölçüde zaman uyumsuz olabilir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="73ac9-182">Olay tabanlı zaman uyumsuz Istemciler ve Ileti sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="73ac9-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="73ac9-183">Olay tabanlı zaman uyumsuz model için, birden fazla değer döndürülürse, bir değer `Result` özellik olarak döndürülür ve diğerleri <xref:System.EventArgs> nesnesi üzerinde özellikler olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="73ac9-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="73ac9-184">Bunun sonucunda, bir istemci, olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verileri içeri aktardığında ve işlem birden fazla değer döndürürse, varsayılan <xref:System.EventArgs> nesnesi bir değeri `Result` özelliği olarak döndürür ve geri kalan <xref:System.EventArgs> nesnesinin özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="73ac9-185">İleti nesnesini `Result` özelliği olarak almak ve döndürülen değerlerin bu nesnede özellikler olarak elde etmek istiyorsanız, **/MessageContract** komut seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="73ac9-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="73ac9-186">Bu, <xref:System.EventArgs> nesnesinde `Result` özelliği olarak yanıt iletisini döndüren bir imza oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73ac9-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="73ac9-187">Tüm iç dönüş değerleri, yanıt iletisi nesnesinin özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="73ac9-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ac9-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73ac9-188">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
