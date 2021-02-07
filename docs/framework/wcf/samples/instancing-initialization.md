---
description: 'Daha fazla bilgi için: örnek oluşturma başlatma'
title: Başlatmayı Örneklendirme
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 056f867012667abaf046827a7c6295f83d4794f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726526"
---
# <a name="instancing-initialization"></a><span data-ttu-id="a0242-103">Başlatmayı Örneklendirme</span><span class="sxs-lookup"><span data-stu-id="a0242-103">Instancing Initialization</span></span>

<span data-ttu-id="a0242-104">Bu örnek, bir arabirimini etkinleştirerek ve devre dışı bırakarak bir nesnenin başlatılmasını özelleştiren bir arabirim tanımlayarak [Havuz oluşturma](pooling.md) örneğini genişletir `IObjectControl` .</span><span class="sxs-lookup"><span data-stu-id="a0242-104">This sample extends the [Pooling](pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="a0242-105">İstemci, nesneyi havuza döndüren ve havuza nesne döndüren yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="a0242-105">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0242-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="a0242-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="a0242-107">Genişletilebilirlik noktaları</span><span class="sxs-lookup"><span data-stu-id="a0242-107">Extensibility Points</span></span>  

 <span data-ttu-id="a0242-108">Windows Communication Foundation (WCF) uzantısı oluşturmanın ilk adımı, genişletilebilirlik noktasının kullanılmasına karar vermaktır.</span><span class="sxs-lookup"><span data-stu-id="a0242-108">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="a0242-109">WCF 'de, *EndpointDispatcher* terimi, gelen iletileri kullanıcının hizmetinde Yöntem etkinleştirmeleri içine dönüştürmeden ve dönüş değerlerini Bu yöntemden giden bir iletiye dönüştürmekten sorumlu bir çalışma zamanı bileşenine başvurur.</span><span class="sxs-lookup"><span data-stu-id="a0242-109">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="a0242-110">WCF hizmeti her uç nokta için bir EndpointDispatcher oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0242-110">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="a0242-111">EndpointDispatcher, sınıfını kullanarak uç nokta kapsamı (hizmet tarafından alınan veya gönderilen tüm iletiler için) sağlar <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> .</span><span class="sxs-lookup"><span data-stu-id="a0242-111">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="a0242-112">Bu sınıf, EndpointDispatcher davranışını denetleyen çeşitli özellikleri özelleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0242-112">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="a0242-113">Bu örnek, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> hizmet sınıfının örneklerini sağlayan nesnesine işaret eden özelliğine odaklanır.</span><span class="sxs-lookup"><span data-stu-id="a0242-113">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="a0242-114">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="a0242-114">IInstanceProvider</span></span>  

 <span data-ttu-id="a0242-115">WCF 'de, EndpointDispatcher arabirimini uygulayan bir örnek sağlayıcı kullanarak bir hizmet sınıfının örneklerini oluşturur <xref:System.ServiceModel.Dispatcher.IInstanceProvider> .</span><span class="sxs-lookup"><span data-stu-id="a0242-115">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="a0242-116">Bu arabirimin yalnızca iki yöntemi vardır:</span><span class="sxs-lookup"><span data-stu-id="a0242-116">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="a0242-117"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Bir ileti geldiğinde, dağıtıcı <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> iletiyi işlemek için hizmet sınıfının bir örneğini oluşturmak üzere yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="a0242-117"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="a0242-118">Bu yönteme yapılan çağrıların sıklığı, özelliği tarafından belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> .</span><span class="sxs-lookup"><span data-stu-id="a0242-118">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="a0242-119">Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği olarak ayarlandıysa <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType> , gelen her iletiyi işlemek için yeni bir hizmet sınıfı örneği oluşturulur, bu nedenle <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> ileti her geldiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a0242-119">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="a0242-120"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Hizmet örneği iletiyi işlemeyi tamamladığında, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="a0242-120"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="a0242-121">Yönteminde olduğu gibi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> , bu yönteme yapılan çağrıların sıklığı özelliği tarafından belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> .</span><span class="sxs-lookup"><span data-stu-id="a0242-121">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="a0242-122">Nesne havuzu</span><span class="sxs-lookup"><span data-stu-id="a0242-122">The Object Pool</span></span>  

 <span data-ttu-id="a0242-123">`ObjectPoolInstanceProvider`Sınıfı, nesne havuzu için uygulamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="a0242-123">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="a0242-124">Bu sınıf, <xref:System.ServiceModel.Dispatcher.IInstanceProvider> hizmet modeli katmanıyla etkileşimde bulunmak için arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="a0242-124">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="a0242-125">EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemi çağırdığında, yeni bir örnek oluşturmak yerine, özel uygulama bellek içi havuzda var olan bir nesneyi arar.</span><span class="sxs-lookup"><span data-stu-id="a0242-125">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="a0242-126">Kullanılabilir bir tane varsa, döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a0242-126">If one is available, it is returned.</span></span> <span data-ttu-id="a0242-127">Aksi takdirde, `ObjectPoolInstanceProvider` `ActiveObjectsCount` özelliğinin (havuzdan döndürülen nesne sayısı) en yüksek havuz boyutuna ulaştığından, bu özelliği denetler.</span><span class="sxs-lookup"><span data-stu-id="a0242-127">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="a0242-128">Aksi takdirde, yeni bir örnek oluşturulup çağırana döndürülür ve `ActiveObjectsCount` daha sonra artırılır.</span><span class="sxs-lookup"><span data-stu-id="a0242-128">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="a0242-129">Aksi takdirde, bir nesne oluşturma isteği yapılandırılmış bir süre için sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="a0242-129">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="a0242-130">İçin uygulanması `GetObjectFromThePool` Aşağıdaki örnek kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a0242-130">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```csharp
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 <span data-ttu-id="a0242-131">Özel `ReleaseInstance` uygulama, yayımlanan örneği havuza geri ekler ve `ActiveObjectsCount` değeri azaltır.</span><span class="sxs-lookup"><span data-stu-id="a0242-131">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="a0242-132">EndpointDispatcher Bu yöntemleri farklı iş parçacıklarından çağırabilir ve bu nedenle, sınıftaki sınıf düzeyi üyelerine eşitlenen erişim `ObjectPoolInstanceProvider` gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0242-132">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```csharp
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 <span data-ttu-id="a0242-133">`ReleaseInstance`Yöntemi bir *Temizleme başlatma* özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0242-133">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="a0242-134">Normalde havuz, havuzun ömrü boyunca en az sayıda nesne tutar.</span><span class="sxs-lookup"><span data-stu-id="a0242-134">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="a0242-135">Ancak, yapılandırmada belirtilen en yüksek sınıra ulaşmak için havuzda ek nesneler oluşturulmasını gerektiren aşırı kullanım süreleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="a0242-135">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="a0242-136">Sonuç olarak, havuz daha az etkin hale geldiğinde, bu fazlalık nesneler ek bir ek yük haline gelebilir.</span><span class="sxs-lookup"><span data-stu-id="a0242-136">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="a0242-137">Bu nedenle, `activeObjectsCount` bir boşta kalma süreölçeri sıfıra ulaştığında harekete geçiren ve Temizleme döngüsünü gerçekleştiren bir Zamanlayıcı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="a0242-137">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 <span data-ttu-id="a0242-138">ServiceModel katman uzantıları aşağıdaki davranışlar kullanılarak kullanıma alınır:</span><span class="sxs-lookup"><span data-stu-id="a0242-138">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="a0242-139">Hizmet davranışları: Bu, tüm hizmet çalışma zamanının özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="a0242-139">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="a0242-140">Uç nokta davranışları: Bu, EndpointDispatcher dahil olmak üzere belirli bir hizmet uç noktasının özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="a0242-140">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="a0242-141">Sözleşme davranışları: Bu, <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sırasıyla istemci veya hizmette bulunan ya da sınıfların özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="a0242-141">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="a0242-142">İşlem davranışları: Bu, <xref:System.ServiceModel.Dispatcher.ClientOperation> <xref:System.ServiceModel.Dispatcher.DispatchOperation> sırasıyla istemci veya hizmette bulunan ya da sınıfların özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="a0242-142">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="a0242-143">Bir nesne havuzu uzantısının amacı için bir uç nokta davranışı veya bir hizmet davranışı oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="a0242-143">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="a0242-144">Bu örnekte, hizmetin her uç noktasına nesne havuzu oluşturma özelliğini uygulayan bir hizmet davranışı kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a0242-144">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="a0242-145">Hizmet davranışları arabirimi uygulayarak oluşturulur <xref:System.ServiceModel.Description.IServiceBehavior> .</span><span class="sxs-lookup"><span data-stu-id="a0242-145">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="a0242-146">Özel davranışları ServiceModel olarak algılayan çeşitli yollar vardır:</span><span class="sxs-lookup"><span data-stu-id="a0242-146">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="a0242-147">Özel bir öznitelik kullanma.</span><span class="sxs-lookup"><span data-stu-id="a0242-147">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="a0242-148">Imperatively, hizmet açıklamasının davranış koleksiyonuna ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="a0242-148">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="a0242-149">Yapılandırma dosyası genişletiliyor.</span><span class="sxs-lookup"><span data-stu-id="a0242-149">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="a0242-150">Bu örnek özel bir özniteliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0242-150">This sample uses a custom attribute.</span></span> <span data-ttu-id="a0242-151">Oluşturulduğunda <xref:System.ServiceModel.ServiceHost> , hizmetin tür tanımında kullanılan öznitelikleri inceler ve kullanılabilir davranışları hizmet açıklamasının davranış koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="a0242-151">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="a0242-152"><xref:System.ServiceModel.Description.IServiceBehavior>Arabirimin üç yöntemi vardır: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` ve <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> .</span><span class="sxs-lookup"><span data-stu-id="a0242-152">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="a0242-153">Bu yöntemler, başlatıldığında WCF tarafından çağırılır <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="a0242-153">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="a0242-154"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> İlk olarak çağrılır; hizmetin tutarsızlıklar için inceleneme izin verir.</span><span class="sxs-lookup"><span data-stu-id="a0242-154"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="a0242-155"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> sonraki çağırılır; Bu yöntem yalnızca Gelişmiş senaryolarda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a0242-155"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="a0242-156"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> son olarak adlandırılır ve çalışma zamanının yapılandırılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="a0242-156"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="a0242-157">Aşağıdaki parametreler içine geçirilir <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="a0242-157">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="a0242-158">`Description`: Bu parametre hizmetin tamamı için hizmet açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0242-158">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="a0242-159">Bu, hizmetin uç noktaları, sözleşmeleri, bağlamaları ve hizmetle ilişkili diğer verilerle ilgili açıklama verilerini denetlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a0242-159">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="a0242-160">`ServiceHostBase`: Bu parametre, <xref:System.ServiceModel.ServiceHostBase> Şu anda başlatılmış olan ' i sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0242-160">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="a0242-161">Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulamada, öğesinin yeni bir örneği örneği oluşturulur `ObjectPoolInstanceProvider` ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> ' a iliştirilmiş her bir özelliğine atanır <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> <xref:System.ServiceModel.ServiceHostBase> .</span><span class="sxs-lookup"><span data-stu-id="a0242-161">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```csharp
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}
```  
  
 <span data-ttu-id="a0242-162">Bir uygulamaya ek olarak <xref:System.ServiceModel.Description.IServiceBehavior> , `ObjectPoolingAttribute` sınıfı öznitelik bağımsız değişkenlerini kullanarak nesne havuzunu özelleştirmek için çeşitli üyelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a0242-162">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="a0242-163">Bu Üyeler, `MaxSize` `MinSize` `Enabled` `CreationTimeout` .NET Enterprise Services tarafından sunulan nesne havuzu özellik kümesini eşleştirmek için, ve içerir.</span><span class="sxs-lookup"><span data-stu-id="a0242-163">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="a0242-164">Nesne havuzu oluşturma davranışı artık yeni oluşturulan özel öznitelikle hizmet uygulamasına ek olarak bir WCF hizmetine eklenebilir `ObjectPooling` .</span><span class="sxs-lookup"><span data-stu-id="a0242-164">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="a0242-165">Etkinleştirme ve devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="a0242-165">Hooking Activation and Deactivation</span></span>  

 <span data-ttu-id="a0242-166">Nesne havuzunun birincil amacı, kısa süreli nesneleri görece maliyetli oluşturma ve başlatma ile optimize etmek.</span><span class="sxs-lookup"><span data-stu-id="a0242-166">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="a0242-167">Bu nedenle, düzgün şekilde kullanılırsa uygulamaya çarpıcı bir performans artışı verebilir.</span><span class="sxs-lookup"><span data-stu-id="a0242-167">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="a0242-168">Nesne havuzdan döndürüldüğünden, Oluşturucu yalnızca bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a0242-168">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="a0242-169">Ancak bazı uygulamalar, tek bir bağlam sırasında kullanılan kaynakları başlatıp temizleyebilecekleri bir denetim düzeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a0242-169">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="a0242-170">Örneğin, bir hesaplamalar kümesi için kullanılan bir nesne, bir sonraki hesaplamayı işlemeden önce özel alanlarını sıfırlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a0242-170">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="a0242-171">Kurumsal Hizmetler, nesne geliştiricisi geçersiz kılınmasına `Activate` ve `Deactivate` temel sınıftan yöntemlere izin vererek bu tür içeriğe özgü başlatma işlemini etkinleştirdi <xref:System.EnterpriseServices.ServicedComponent> .</span><span class="sxs-lookup"><span data-stu-id="a0242-171">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="a0242-172">Nesne havuzu, `Activate` nesneyi havuzdan döndürmeden hemen önce yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="a0242-172">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="a0242-173">`Deactivate` , nesne havuza geri dönzaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a0242-173">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="a0242-174"><xref:System.EnterpriseServices.ServicedComponent>Temel sınıf Ayrıca `boolean` adlı bir özelliğe sahiptir `CanBePooled` ve bu, havuzun daha fazla havuza kaydedilip edilmeyeceğini bildirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a0242-174">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="a0242-175">Bu işlevselliği taklit etmek için örnek, belirtilen üyelere sahip ortak bir arabirim ( `IObjectControl` ) bildirir.</span><span class="sxs-lookup"><span data-stu-id="a0242-175">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="a0242-176">Bu arabirim daha sonra içeriğe özgü başlatma sağlamak üzere amaçlanan hizmet sınıfları tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a0242-176">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="a0242-177"><xref:System.ServiceModel.Dispatcher.IInstanceProvider>Uygulamanın bu gereksinimleri karşılayacak şekilde değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0242-177">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="a0242-178">Şimdi, yöntemini çağırarak bir nesne aldığınızda, `GetInstance` nesnenin ne zaman uygulayıp uygulamadığını denetlemeniz gerekir `IObjectControl.` , `Activate` yöntemi uygun şekilde çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0242-178">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="a0242-179">Havuza bir nesne döndürürken, `CanBePooled` nesne havuza geri eklenmeden önce özelliği için bir denetim gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a0242-179">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```csharp  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 <span data-ttu-id="a0242-180">Hizmet geliştiricisi bir nesnenin havuza kaydedilip edilmeyeceğini belirleyebildiğinden, havuzdaki belirli bir zamanda bulunan nesne sayısı en düşük boyutun altına gidebilir.</span><span class="sxs-lookup"><span data-stu-id="a0242-180">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="a0242-181">Bu nedenle, nesne sayısının en düşük düzeyin altında olup olmadığını ve Temizleme yordamında gerekli başlatmayı gerçekleştirip gerçekleştirmediğini denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0242-181">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```csharp  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 <span data-ttu-id="a0242-182">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a0242-182">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="a0242-183">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a0242-183">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a0242-184">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a0242-184">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a0242-185">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a0242-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a0242-186">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a0242-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a0242-187">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a0242-187">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a0242-188">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a0242-188">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a0242-189">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a0242-189">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a0242-190">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a0242-190">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a0242-191">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a0242-191">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
