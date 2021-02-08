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
# <a name="durable-instance-context"></a>Dayanıklı Örnek Bağlamı

Bu örnek, dayanıklı örnek bağlamlarını etkinleştirmek için Windows Communication Foundation (WCF) çalışma zamanının nasıl özelleştirileceğini gösterir. Bu, yedekleme deposu olarak 2005 SQL Server kullanır (Bu durumda SQL Server 2005 Express). Bununla birlikte, özel depolama mekanizmalarına erişmek için de bir yol sağlar.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Bu örnek, WCF 'nin hem kanal katmanını hem de hizmet modeli katmanını genişletmeyi içerir. Bu nedenle, uygulama ayrıntılarına geçmeden önce temel kavramları anlamanız gerekir.

Dayanıklı örnek bağlamları gerçek dünyada oldukça sık bulunabilir. Örneğin, bir alışveriş sepeti uygulamasının, bir alışveriş sepetini aracılığıyla alışverişi bir gün içinde duraklatarak devam etmesine olanak tanır. Bu sayede, bir sonraki güne ait alışveriş sepetini ziyaret ettiğimiz zaman, özgün bağlamımız geri yüklendi. , Bağlantısı kesiltiğimiz sırada alışveriş sepeti uygulamasının (sunucudaki) alışveriş sepeti örneğini korumadığını unutmamak önemlidir. Bunun yerine, durumunu dayanıklı bir depolama medyasına devam ettirir ve geri yüklenen bağlam için yeni bir örnek oluştururken onu kullanır. Bu nedenle, aynı bağlam için hizmet veren hizmet örneği, önceki örnekle aynı değildir (yani aynı bellek adresine sahip değildir).

İstemci ve hizmet arasında bir bağlam KIMLIĞI değiş tokuş eden küçük bir protokol tarafından dayanıklı örnek bağlamı mümkün hale getirilir. Bu bağlam KIMLIĞI istemcide oluşturulur ve hizmete iletilir. Hizmet örneği oluşturulduğunda, hizmet çalışma zamanı kalıcı bir depolamadan bu bağlam KIMLIĞINE karşılık gelen kalıcı durumu yüklemeye çalışır (varsayılan olarak bir SQL Server 2005 veritabanıdır). Kullanılabilir bir durum yoksa, yeni örnek varsayılan durumuna sahiptir. Hizmet uygulamasının, hizmet uygulamasının durumunu değiştiren işlemleri işaretlemek için özel bir öznitelik kullanır, böylece çalışma zamanı, hizmet örneğini çağırdıktan sonra kaydedebilir.

Önceki açıklama ile, iki adım hedefe ulaşmak için kolayca ayırt edilebilir:

1. Bağlam KIMLIĞINI taşımak için tel bağlantı olan iletiyi değiştirin.

2. Hizmet yerel davranışını özel örnek oluşturma mantığını uygulayacak şekilde değiştirin.

Listedeki ilk bir ileti, hattaki iletileri etkilediği için özel bir kanal olarak uygulanmalıdır ve kanal katmanına bağlanılmalıdır. İkincisi yalnızca hizmet yerel davranışını etkiler ve bu nedenle çeşitli hizmet genişletilebilirliği noktaları genişletilerek uygulanabilir. Sonraki birkaç bölümde, bu uzantıların her biri ele alınmıştır.

## <a name="durable-instancecontext-channel"></a>Dayanıklı InstanceContext kanalı

Aranacak ilk şey bir kanal katmanı uzantısıdır. Özel bir kanal yazmanın ilk adımı, kanalın iletişim yapısına karar vermidir. Yeni bir hat Protokolü tanıtılmakta olduğundan kanal, kanal yığınındaki neredeyse tüm diğer kanallarla çalışmalıdır. Bu nedenle, tüm ileti değişimi düzenlerini desteklemelidir. Ancak, kanalın temel işlevselliği, iletişim yapısıyla bağımsız olarak aynıdır. Daha belirgin bir şekilde, istemciden içerik KIMLIĞINI iletilere ve hizmetten bu bağlam KIMLIĞINI okuyup üst düzeylere geçirecek şekilde yazması gerekir. Bu nedenle, `DurableInstanceContextChannelBase` Tüm dayanıklı örnek bağlam kanalı uygulamaları için soyut temel sınıf olarak davranan bir sınıf oluşturulur. Bu sınıf, genel durum makinesi yönetim işlevlerini ve bu iki korumalı üyeyi uygulamak ve iletilere ve bu kaynaklardan bağlam bilgilerini okumak için içerir.

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

Bu iki yöntem, bir `IContextManager` veya ileti aracılığıyla bağlam Kimliğini yazmak ve okumak için uygulamalar kullanır. ( `IContextManager` tüm bağlam yöneticileri için sözleşmeyi tanımlamak üzere kullanılan özel bir arabirimdir.) Kanal, bağlam KIMLIĞINI özel bir SOAP üstbilgisine veya bir HTTP tanımlama bilgisi başlığına dahil edebilir. Her bir bağlam Yöneticisi uygulamasının `ContextManagerBase` tüm bağlam yöneticileri için ortak işlevselliği içeren sınıftan devralır. `GetContextId`Bu sınıftaki yöntem, istemciden bağlam Kimliğini yapmak için kullanılır. Bir bağlam KIMLIĞI ilk kez oluşturulduğunda, bu yöntem, adı uzak uç nokta adresi tarafından oluşturulan bir metin dosyasına kaydeder (tipik URI 'Ler içindeki geçersiz dosya adı karakterleri @ karakterlerle değiştirilmiştir).

Daha sonra aynı uzak uç nokta için bağlam KIMLIĞI gerektiğinde, uygun bir dosyanın var olup olmadığını denetler. Varsa, bağlam KIMLIĞINI okur ve döndürür. Aksi takdirde, yeni oluşturulan bir bağlam KIMLIĞI döndürür ve bir dosyaya kaydeder. Varsayılan yapılandırmayla, bu dosyalar geçerli kullanıcının geçici dizininde bulunan ContextStore adlı bir dizine yerleştirilir. Ancak bu konum, Binding öğesi kullanılarak yapılandırılabilir.

Bağlam KIMLIĞINI taşımak için kullanılan mekanizma yapılandırılabilir. HTTP tanımlama bilgisi başlığına veya özel bir SOAP üstbilgisine yazılabilir. Özel SOAP üst bilgisi yaklaşımı, bu Protokolü HTTP olmayan protokollerle (örneğin, TCP veya adlandırılmış kanallar) kullanmayı mümkün kılar. `MessageHeaderContextManager` `HttpCookieContextManager` Bu iki seçeneği de uygulayan iki sınıf vardır.

Her ikisi de içerik KIMLIĞINI uygun şekilde iletiye yazar. Örneğin, sınıfı, `MessageHeaderContextManager` yöntemi içindeki BIR SOAP üstbilgisine yazar `WriteContext` .

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

Hem hem `ApplyContext` de `ReadContextId` `DurableInstanceContextChannelBase` sınıfındaki yöntemleri `IContextManager.ReadContext` `IContextManager.WriteContext` sırasıyla ve ' ı çağırır. Ancak, bu bağlam yöneticileri sınıf tarafından doğrudan oluşturulmaz `DurableInstanceContextChannelBase` . Bunun yerine, `ContextManagerFactory` Bu işi yapmak için sınıfını kullanır.

```csharp
IContextManager contextManager =
                ContextManagerFactory.CreateContextManager(contextType,
                this.contextStoreLocation,
                this.endpointAddress);
```

`ApplyContext`Yöntemi, gönderen kanallar tarafından çağrılır. Bağlam KIMLIĞINI giden iletilere çıkartır. `ReadContextId`Yöntemi, alan kanalları tarafından çağrılır. Bu yöntem, gelen iletilerde bağlam KIMLIĞININ kullanılabilir olmasını sağlar ve onu `Properties` sınıfının koleksiyonuna ekler `Message` . Ayrıca `CommunicationException` , bağlam kimliği okunamaması ve bu nedenle kanalın iptal edilmesine neden olur.

```csharp
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);
```

Devam etmeden önce, sınıfında koleksiyonun kullanımını anlamak önemlidir `Properties` `Message` . Genellikle, bu `Properties` koleksiyon, verileri daha düşük olan kanal katmanından üst düzeylere geçirirken kullanılır. Bu şekilde, istenen veriler, protokol ayrıntılarının ne olursa olsun, üst düzeylere tutarlı bir şekilde sağlanır. Diğer bir deyişle, kanal katmanı, bağlam KIMLIĞINI bir SOAP üstbilgisi veya HTTP tanımlama bilgisi üstbilgisi olarak gönderebilir ve alabilir. Ancak Kanal katmanı bu bilgileri koleksiyonda kullanılabilir hale yaptığından üst düzeylerin bu ayrıntıları öğrenmek için gerekli değildir `Properties` .

Artık bu `DurableInstanceContextChannelBase` sınıfla, gerekli arabirimlerin (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel destekleyen desteklenecektir, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) her on onuna sahip olmalıdır. Her kullanılabilir ileti değişimi düzenine (datagram, simpleks, dupleks ve oturumsuz çeşitleri) benzer. Bu uygulamaların her biri, daha önce açıklanan temel sınıfı ve çağrıları `ApplyContext` ve `ReadContextId` uygun şekilde devralır. Örneğin, `DurableInstanceContextOutputChannel` IOutputChannel arabirimini uygulayan- `ApplyContext` iletileri gönderen her yöntemden yöntemini çağırır.

```csharp
public void Send(Message message, TimeSpan timeout)
{
    // Apply the context information before sending the message.
    this.ApplyContext(message);
    //…
}
```

Diğer taraftan, `DurableInstanceContextInputChannel` arabirimini uygulayan- `IInputChannel` `ReadContextId` iletileri alan her yöntemde yöntemini çağırır.

```csharp
public Message Receive(TimeSpan timeout)
{
    //…
      ReadContextId(message);
      return message;
}
```

Bunun dışında, bu kanal uygulamaları kanal yığınında alttaki kanala yönelik Yöntem çağrılarını devredebilir. Ancak, oturum, bağlam KIMLIĞININ gönderildiğinden ve oturumun oluşturulmasına neden olan ilk ileti için salt okunan olduğundan emin olmak için bir temel mantığa sahiptir.

```csharp
if (isFirstMessage)
{
//…
    this.ApplyContext(message);
    isFirstMessage = false;
}
```

Daha sonra bu kanal uygulamaları, `DurableInstanceContextBindingElement` sınıf ve sınıf tarafından uygun şekılde WCF kanal çalışma zamanına eklenir `DurableInstanceContextBindingElementSection` . Bağlama öğeleri ve bağlama öğesi bölümleri hakkında daha fazla bilgi için [Httppişirce oturum](httpcookiesession.md) kanalı örnek belgelerine bakın.

## <a name="service-model-layer-extensions"></a>Hizmet modeli katmanı uzantıları

Artık bağlam KIMLIĞI kanal katmanından gezinmiş olduğuna göre, örnek oluşturmayı özelleştirmek için hizmet davranışı uygulanabilir. Bu örnekte, Depolama Yöneticisi, durumu yüklemek ve kalıcı depoya kaydetmek için kullanılır. Daha önce açıklandığı gibi, bu örnek, yedekleme deposu olarak SQL Server 2005 ' ı kullanan bir Depolama Yöneticisi sağlar. Ancak, bu uzantıya özel depolama mekanizmaları eklemek de mümkündür. Ortak bir arabirimin, tüm depolama yöneticileri tarafından uygulanması gereken şekilde bildirilmesini sağlamak.

```csharp
public interface IStorageManager
{
    object GetInstance(string contextId, Type type);
    void SaveInstance(string contextId, object state);
}
```

`SqlServerStorageManager`Sınıfı varsayılan `IStorageManager` uygulamayı içerir. `SaveInstance`Yönteminde, verilen nesne XmlSerializer kullanılarak serileştirilir ve SQL Server veritabanına kaydedilir.

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

`GetInstance`Yönteminde, serileştirilmiş veriler belirli bir bağlam kimliği için okunurdur ve öğesinden oluşturulan nesne çağırana döndürülür.

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

Bu depolama yöneticilerinin kullanıcıları doğrudan örneklendirilecek. Bunlar `StorageManagerFactory` , Depolama Yöneticisi oluşturma ayrıntılarının soyutlarından oluşan sınıfını kullanır. Bu sınıf, `GetStorageManager` belirli bir Depolama Yöneticisi türünün örneğini oluşturan bir statik üyeye sahiptir. Tür parametresi ise `null` , bu yöntem varsayılan sınıfın bir örneğini oluşturur `SqlServerStorageManager` ve döndürür. Ayrıca, arabirimi uyguladığından emin olmak için verilen türü doğrular `IStorageManager` .

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

Kalıcı depolama alanından örnekleri okumak ve yazmak için gerekli altyapı uygulanır. Artık hizmet davranışını değiştirmek için gerekli adımlar gerçekleştirilmelidir.

Bu işlemin ilk adımı olarak, geçerli InstanceContext için kanal katmanından gelen bağlam KIMLIĞINI kaydetmemiz gerekir. InstanceContext, WCF dağıtıcısı ve hizmet örneği arasında bağlantı görevi gören bir çalışma zamanı bileşenidir. Hizmet örneğine ek durum ve davranış sağlamak için kullanılabilir. Bu, sessioncommunication öğesinde bağlam KIMLIĞI yalnızca ilk iletiyle gönderildiği için önemlidir.

WCF, genişletilebilir nesne modelini kullanarak yeni bir durum ve davranış ekleyerek InstanceContext çalışma zamanı bileşenini genişletmeyi sağlar. Genişletilebilir nesne stili, mevcut çalışma zamanı sınıflarını yeni işlevlerle genişletmek ya da bir nesneye yeni durum özellikleri eklemek için WCF 'de kullanılır. Genişletilebilir nesne düzeninde üç arabirim vardır: IExtensibleObject \<T> , IExtension \<T> ve IExtensionCollection \<T> :

- IExtensibleObject \<T> arabirimi, işlevlerini özelleştiren uzantılara izin veren nesneler tarafından uygulanır.

- IExtension \<T> arabirimi T türünde sınıfların uzantıları olan nesneler tarafından uygulanır.

- IExtensionCollection \<T> arabirimi, IExtensions 'ın türlerine göre alınmasına izin veren bir IExtensions koleksiyonudur.

Bu nedenle, IExtension arabirimini uygulayan bir InstanceContextExtension sınıfı oluşturulmalıdır ve bağlam KIMLIĞINI kaydetmek için gereken durumu tanımlar. Bu sınıf Ayrıca, kullanılmakta olan depolama yöneticisini tutan durumu da sağlar. Yeni durum kaydedildikten sonra değiştirmek mümkün değildir. Bu nedenle, durum oluşturulur ve oluşturulduğu sırada örneğe kaydedilir ve yalnızca salt okunurdur özellikleri kullanılarak erişilebilir.

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

InstanceContextInitializer sınıfı, IInstanceContextInitializer arabirimini uygular ve örnek bağlam uzantısını oluşturulan InstanceContext öğesinin uzantılar koleksiyonuna ekler.

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

Daha önce açıklandığı gibi, bağlam KIMLIĞI `Properties` sınıfının koleksiyonundan okunurdur `Message` ve Extension sınıfının oluşturucusuna geçirilir. Bu, bilgilerin katmanlar arasında tutarlı bir şekilde nasıl değiş tokuş edilebilir olduğunu gösterir.

Sonraki önemli adım, hizmet örneği oluşturma sürecini geçersiz kılar. WCF, özel örnek oluşturma davranışlarını uygulamaya ve IInstanceProvider arabirimini kullanarak bunları çalışma zamanına kadar yüklemeye olanak tanır. Yeni `InstanceProvider` sınıf bu işi yapmak için uygulanır. Örnek sağlayıcıdan beklenen hizmet türü oluşturucuda kabul edildi. Daha sonra bu, yeni örnekler oluşturmak için kullanılır. `GetInstance`Uygulamada, kalıcı bir örnek bulmak için Depolama Yöneticisi 'nin bir örneği oluşturulur. Dönerse `null` , hizmet türünün yeni bir örneği oluşturulur ve çağırana döndürülür.

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

Sonraki önemli adım,, `InstanceContextExtension` `InstanceContextInitializer` ve `InstanceProvider` sınıflarını hizmet modeli çalışma zamanına yüklemektir. Davranışı yüklemek için hizmet uygulama sınıflarını işaretlemek üzere özel bir öznitelik kullanılabilir. , `DurableInstanceContextAttribute` Bu özniteliğin uygulamasını içerir ve `IServiceBehavior` tüm hizmet çalışma zamanını genişletmek için arabirimini uygular.

Bu sınıf, kullanılacak depolama Yöneticisi türünü kabul eden bir özelliğe sahiptir. Bu şekilde, uygulama, kullanıcıların kendi `IStorageManager` uygulamasını bu özniteliğin parametresi olarak belirtmesini sağlar.

`ApplyDispatchBehavior`Uygulamada, `InstanceContextMode` geçerli `ServiceBehavior` özniteliğin doğrulanması doğrulanıyor. Bu özellik Singleton olarak ayarlandıysa, dayanıklı örnek oluşturma mümkün değildir ve `InvalidOperationException` konağa bildirimde bulunan bir oluşturulur.

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

Bu, Depolama Yöneticisi örnekleri, örnek bağlam başlatıcısı ve örnek sağlayıcı, `DispatchRuntime` her bitiş noktası için oluşturulan ' de oluşturulur ve yüklenir.

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

Özet bölümünde bu örnek, özel bağlam KIMLIĞI alışverişi için özel hat protokolünü destekleyen bir kanal üretti ve ayrıca, kalıcı depolama alanından örnekleri yüklemek için varsayılan örnek oluşturma davranışının üzerine yazar.

Sol taraf, hizmet örneğini kalıcı depolamaya kaydetmek için bir yoldur. Daha önce anlatıldığı gibi, durumu bir uygulamada kaydetmek için gerekli işlevler zaten vardır `IStorageManager` . Şimdi bunu WCF çalışma zamanı ile tümleştirmelidir. Hizmet uygulama sınıfındaki yöntemler için geçerli olan başka bir öznitelik gereklidir. Bu özniteliğin, hizmet örneğinin durumunu değiştiren yöntemlere uygulanması gerekir.

`SaveStateAttribute`Sınıfı bu işlevi uygular. `IOperationBehavior`Her işlem IÇIN WCF çalışma zamanını değiştirmek için sınıfını da uygular. Bir yöntem Bu öznitelikle işaretlendiğinde, uygun durumdayken WCF çalışma zamanı `ApplyBehavior` yöntemini çağırır `DispatchOperation` . Bu yöntem uygulamasında tek bir kod satırı vardır:

```csharp
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);
```

Bu yönerge, türünün bir örneğini oluşturur `OperationInvoker` ve bu `Invoker` özelliği oluşturulan özelliğine atar `DispatchOperation` . `OperationInvoker`Sınıfı, için oluşturulan varsayılan işlem için bir sarmalayıcıdır `DispatchOperation` . Bu sınıf, `IOperationInvoker` arabirimini uygular. `Invoke`Yöntem uygulamasında gerçek Yöntem çağrısı, iç işlem uyarlaması için temsilci olarak oluşturulur. Ancak, sonuçları döndürmeden önce içindeki Depolama Yöneticisi, `InstanceContext` hizmet örneğini kaydetmek için kullanılır.

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

## <a name="using-the-extension"></a>Uzantıyı kullanma

Hem kanal katmanı hem de hizmet modeli katman uzantıları gerçekleştirilir ve bunlar artık WCF uygulamalarında kullanılabilir. Hizmetler, kanalı bir özel bağlama kullanarak kanal yığınına eklemeli ve ardından hizmet uygulama sınıflarını uygun özniteliklerle işaretmalıdır.

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

İstemci uygulamaları, özel bağlama kullanarak DurableInstanceContextChannel öğesini kanal yığınına eklememelidir. Kanalı yapılandırma dosyasında bildirimli olarak yapılandırmak için bağlama öğesi bölümünün bağlama öğesi uzantıları koleksiyonuna eklenmesi gerekir.

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

Şimdi bağlama öğesi, diğer standart bağlama öğeleri gibi özel bir bağlama ile kullanılabilir:

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

## <a name="conclusion"></a>Sonuç

Bu örnek, bir özel protokol kanalının nasıl oluşturulacağını ve hizmet davranışının etkinleştirmek için nasıl özelleştirileceğini gösterdi.

Uzantı, kullanıcıların `IStorageManager` bir yapılandırma bölümü kullanarak uygulamayı belirtmelerine izin vererek daha da iyileştirilen olabilir. Bu, hizmet kodunu yeniden derlemeden yedekleme mağazasının değiştirilmesini olanaklı kılar.

Ayrıca, örneğin durumunu kapsülleyen bir sınıfı (örneğin,) uygulamayı deneyebilirsiniz `StateBag` . Bu sınıf, her değiştiğinde durumu kalıcı hale getirmekten sorumludur. Bu şekilde özniteliği kullanmaktan kaçınabilirsiniz `SaveState` ve kalıcı çalışmayı daha doğru şekilde gerçekleştirebilirsiniz (örneğin, özniteliğe sahip bir yöntem çağrıldığında her seferinde bu durum kaydedilmeden durumu kalıcı hale getirebilirsiniz `SaveState` ).

Örneği çalıştırdığınızda aşağıdaki çıktı görüntülenir. İstemci, alışveriş sepetine iki öğe ekler ve ardından hizmet üzerinden alışveriş sepetindeki öğelerin listesini alır. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.

```console
Enter the name of the product: apples
Enter the name of the product: bananas

Shopping cart currently contains the following items.
apples
bananas
Press ENTER to shut down client
```

> [!NOTE]
> Hizmeti yeniden oluşturmak veritabanı dosyasının üzerine yazar. Örneğin birden fazla çalıştırması genelinde korunan durumu gözlemlemek için, çalıştırmaları arasında örneği yeniden derlemediğinizden emin olun.

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!NOTE]
> Bu örneği çalıştırmak için SQL Server 2005 veya SQL Express 2005 çalıştırıyor olmanız gerekir. SQL Server 2005 çalıştırıyorsanız, hizmetin bağlantı dizesinin yapılandırmasını değiştirmeniz gerekir. Çapraz makine çalışırken, yalnızca sunucu makinesinde SQL Server gereklidir.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`
