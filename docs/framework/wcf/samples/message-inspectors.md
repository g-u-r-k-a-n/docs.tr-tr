---
title: İleti Denetçileri
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 01553084aa049688cd05fa36e46fb6f67983fb21
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424146"
---
# <a name="message-inspectors"></a>İleti Denetçileri
Bu örnek, istemci ve hizmet ileti denetçilerini nasıl uygulanacağını ve yapılandırılacağını gösterir.  
  
 İleti denetçisi, hizmet modelinin istemci çalışma zamanı ve dağıtım çalışma zamanında programlama yoluyla veya yapılandırma aracılığıyla kullanılabilen ve iletileri alındıktan sonra veya gönderilmeden önce incelemenize ve değiştirebilecek bir genişletilebilirlik nesnesidir.  
  
 Bu örnek, bir dizi yapılandırılabilir XML şema belgelerine karşı gelen iletileri doğrulayan temel bir istemci ve hizmet iletisi doğrulama mekanizmasını uygular. Bu örnekte her işlem için iletileri doğrulamayacağını unutmayın. Bu, bilerek basitleştirmesi.  
  
## <a name="message-inspector"></a>İleti denetçisi  
 İstemci ileti Inspectors <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> arabirimini ve hizmet iletisi denetçilerini <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> arabirimini uygular. Uygulamalar, her iki taraf için de çalışacak bir ileti denetçisi oluşturmak için tek bir sınıfta birleştirilebilir. Bu örnek, bu tür bir Birleşik ileti denetçisi uygular. Inspector, gelen ve giden iletilerin doğrulandığı bir şema kümesi ile oluşturulur ve geliştiricinin gelen veya giden mesajların doğrulanıp onaylanmadığını ve Inspector 'ın gönderim veya istemci modunda olup olmadığını belirtmesini sağlar. Bu konunun ilerleyen kısımlarında açıklanan hata işlemesini etkiler.  
  
```csharp  
public class SchemaValidationMessageInspector : IClientMessageInspector, IDispatchMessageInspector  
{  
    XmlSchemaSet schemaSet;  
    bool validateRequest;  
    bool validateReply;  
    bool isClientSide;  
    [ThreadStatic]  
    bool isRequest;  
  
    public SchemaValidationMessageInspector(XmlSchemaSet schemaSet,  
         bool validateRequest, bool validateReply, bool isClientSide)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = validateReply;  
        this.validateRequest = validateRequest;  
        this.isClientSide = isClientSide;  
    }  
```  
  
 Herhangi bir hizmet (dağıtıcı) ileti denetçisi, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> ve <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>iki <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> yöntemini uygulamalıdır.  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, bir ileti alındığında, kanal yığını tarafından işlendiğinde ve bir hizmete atandığında, ancak seri durumdan çıkarılmadan ve bir işleme dağıtılmadan önce dağıtıcı tarafından çağrılır. Gelen ileti şifrelendiyse, ileti denetçisine ulaştığında iletinin şifresi zaten çözülür. Yöntemi, bir başvuru parametresi olarak geçirilen `request` iletisini alır, bu da iletinin gerekli olduğu şekilde incelen, değiştirilmesine veya değiştirilmesine izin verir. Dönüş değeri herhangi bir nesne olabilir ve hizmet geçerli iletiye bir yanıt döndürdüğünde <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> geçirilen bir bağıntı durumu nesnesi olarak kullanılır. Bu örnekte, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> iletinin denetlemesini (doğrulaması) özel, yerel `ValidateMessageBody` metoda devreder ve bağıntı durumu nesnesi döndürmez. Bu yöntem, hizmete hiçbir geçersiz ileti geçmemesini sağlar.  
  
```csharp  
object IDispatchMessageInspector.AfterReceiveRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel, System.ServiceModel.InstanceContext instanceContext)  
{  
    if (validateRequest)  
    {  
        // inspect the message. If a validation error occurs,  
        // the thrown fault exception bubbles up.  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>, bir yanıt istemciye geri gönderilmek üzere veya tek yönlü iletiler söz konusu olduğunda gelen ileti işlendiğinde çağrılır. Bu, uzantılarından bağımsız olarak, uzantıların simetrik olarak çağrıldığından sayımına izin verir. <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>olduğu gibi, ileti başvuru parametresi olarak geçirilir ve incelenebilir, değiştirilebilir veya değiştirilebilir. Bu örnekte gerçekleştirilen iletinin doğrulanması, `ValidMessageBody` yöntemine yeniden temsilci olarak oluşturulur, ancak doğrulama hatalarının işlenmesi bu durumda biraz farklıdır.  
  
 Hizmette bir doğrulama hatası oluşursa `ValidateMessageBody` yöntemi <xref:System.ServiceModel.FaultException>türetilmiş özel durumlar oluşturur. <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, bu özel durumlar, otomatik olarak SOAP hatalarına dönüştürülebileceği ve istemciye geçirildikleri hizmet modeli altyapısına yerleştirilebilir. <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, hizmet tarafından oluşturulan hata özel durumlarının dönüşümü ileti denetçisi çağrılmadan önce olduğundan, <xref:System.ServiceModel.FaultException> özel durumlar altyapıya yerleştirmemelidir. Bu nedenle, aşağıdaki uygulama bilinen `ReplyValidationFault` özel durumunu yakalar ve yanıt iletisini açık bir hata iletisiyle değiştirir. Bu yöntem, hizmet uygulamasının hiçbir geçersiz ileti döndürülmemesini sağlar.  
  
```csharp  
void IDispatchMessageInspector.BeforeSendReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        // Inspect the reply, catch a possible validation error   
        try  
        {  
            ValidateMessageBody(ref reply, false);  
        }  
        catch (ReplyValidationFault fault)  
        {  
            // if a validation error occurred, the message is replaced  
            // with the validation fault.  
            reply = Message.CreateMessage(reply.Version,   
                    fault.CreateMessageFault(), reply.Headers.Action);  
        }  
    }  
```  
  
 İstemci ileti denetçisi çok benzerdir. <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> uygulanması gereken iki yöntem <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> ve <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.  
  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>, ileti istemci uygulaması ya da işlem biçimlendirici tarafından oluşturulduğunda çağrılır. Dağıtıcı ileti denetçiler itibariyle, ileti yalnızca incelenebilir veya tamamen değiştirilebilir. Bu örnekte, Inspector, gönderim ileti denetçiler için de kullanılan aynı yerel `ValidateMessageBody` yardımcı yöntemine temsilci atar.  
  
 İstemci ve hizmet doğrulaması arasındaki davranış farkı (oluşturucuda belirtildiği gibi), istemci doğrulamasının bir hizmet hatası nedeniyle yerel olarak gerçekleştiğinden, Kullanıcı koduna yerleştirilen yerel özel durumları yaratmaktır. Genellikle kural, hizmet dağıtıcılarının hata oluşturması ve istemci denetçlarının özel durumlar oluşturması şeklindedir.  
  
 Bu <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> uygulama, hizmete geçersiz ileti gönderilmesini sağlar.  
  
```csharp  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 `AfterReceiveReply` uygulama, hizmetten alınan geçersiz iletilerin istemci kullanıcı koduna aktarılmamasını sağlar.  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 Bu belirli ileti denetçisinin kalp `ValidateMessageBody` yöntemidir. Çalışmasını gerçekleştirmek için, geçirilen iletinin gövde içeriği alt ağacının etrafında bir doğrulama <xref:System.Xml.XmlReader> kaydırır. Okuyucu, ileti denetçisinin tuttuğu şemalar kümesi ile doldurulur ve doğrulama geri çağırması bu yöntemin yanı sıra tanımlanan `InspectionValidationHandler` başvuran bir temsilciye ayarlanır. Doğrulama işlemini gerçekleştirmek için, ileti daha sonra okuyup bir bellek akışı ile desteklenen <xref:System.Xml.XmlDictionaryWriter>biriktirilir. İşlemde bir doğrulama hatası veya uyarı oluşursa, geri çağırma yöntemi çağrılır.  
  
 Herhangi bir hata oluşursa, özgün iletiden özellikleri ve başlıkları kopyalayan ve bir <xref:System.Xml.XmlDictionaryReader> ve değiştirme iletisine eklenen bellek akışında şimdi doğrulanan bilgi kümesini kullanan yeni bir ileti oluşturulur.  
  
```csharp  
void ValidateMessageBody(ref System.ServiceModel.Channels.Message message, bool isRequest)  
{  
    if (!message.IsFault)  
    {  
        XmlDictionaryReaderQuotas quotas =   
                new XmlDictionaryReaderQuotas();  
        XmlReader bodyReader =   
            message.GetReaderAtBodyContents().ReadSubtree();  
        XmlReaderSettings wrapperSettings =   
                              new XmlReaderSettings();  
        wrapperSettings.CloseInput = true;  
        wrapperSettings.Schemas = schemaSet;  
        wrapperSettings.ValidationFlags =   
                                XmlSchemaValidationFlags.None;  
        wrapperSettings.ValidationType = ValidationType.Schema;  
        wrapperSettings.ValidationEventHandler += new   
           ValidationEventHandler(InspectionValidationHandler);  
        XmlReader wrappedReader = XmlReader.Create(bodyReader,   
                                            wrapperSettings);  
  
        // pull body into a memory backed writer to validate  
        this.isRequest = isRequest;  
        MemoryStream memStream = new MemoryStream();  
        XmlDictionaryWriter xdw =  
              XmlDictionaryWriter.CreateBinaryWriter(memStream);  
        xdw.WriteNode(wrappedReader, false);  
        xdw.Flush(); memStream.Position = 0;  
        XmlDictionaryReader xdr =   
        XmlDictionaryReader.CreateBinaryReader(memStream, quotas);  
  
        // reconstruct the message with the validated body  
        Message replacedMessage =   
            Message.CreateMessage(message.Version, null, xdr);  
        replacedMessage.Headers.CopyHeadersFrom(message.Headers);  
        replacedMessage.Properties.CopyProperties(message.Properties);  
        message = replacedMessage;  
    }  
}  
```  
  
 `InspectionValidationHandler` yöntemi, bir şema doğrulama hatası veya uyarı oluştuğunda doğrulama <xref:System.Xml.XmlReader> tarafından çağrılır. Aşağıdaki uygulama yalnızca hatalarla birlikte çalışarak tüm uyarıları yoksayar.  
  
 İlk bakışta ileti denetçisi ile iletiye bir doğrulama <xref:System.Xml.XmlReader> eklemek ve ileti işlendiğinde ve iletiyi arabelleğe almadan doğrulamanın gerçekleşmesini sağlamak mümkün görünebilir. Bununla birlikte, bu geri aramanın, doğrulama özel durumlarını hizmet modeli altyapısında veya geçersiz XML düğümleri algılandığı için Kullanıcı kodu olduğu anlamına gelir, ancak öngörülemeyen davranışlara neden olur. Arabelleğe alma yaklaşımı, Kullanıcı kodunu geçersiz iletilerden tamamen kalkan.  
  
 Daha önce anlatıldığı gibi işleyici tarafından oluşturulan özel durumlar, istemci ve hizmet arasında farklılık gösterir. Hizmette, özel durumlar, istemci üzerindeki özel durumlar düzenli özel istisnalardır <xref:System.ServiceModel.FaultException>türetilir.  
  
```csharp  
        void InspectionValidationHandler(object sender, ValidationEventArgs e)  
{  
    if (e.Severity == XmlSeverityType.Error)  
    {  
        // We are treating client and service side validation errors  
        // differently here. Client side errors cause exceptions  
        // and are thrown straight up to the user code. Service side  
        // validations cause faults.  
        if (isClientSide)  
        {  
            if (isRequest)  
            {  
                throw new RequestClientValidationException(e.Message);  
            }  
            else  
            {  
                throw new ReplyClientValidationException(e.Message);  
            }  
        }  
        else  
        {  
            if (isRequest)  
            {  
                // this fault is caught by the ServiceModel   
                // infrastructure and turned into a fault reply.  
                throw new RequestValidationFault(e.Message);  
             }  
             else  
             {  
                // this fault is caught and turned into a fault message  
                // in BeforeSendReply in this class  
                throw new ReplyValidationFault(e.Message);  
              }  
          }  
      }  
    }  
```  
  
## <a name="behavior"></a>Davranış  
 İleti denetçiler, istemci çalışma zamanına veya dağıtım çalışma zamanına yönelik uzantılardır. Bu tür uzantılar *davranışlar*kullanılarak yapılandırılır. Davranış, varsayılan yapılandırmayı değiştirerek veya uzantıları (ileti denetçiler gibi) ekleyerek hizmet modeli çalışma zamanının davranışını değiştiren bir sınıftır.  
  
 Aşağıdaki `SchemaValidationBehavior` sınıfı, bu örneğin ileti denetçisini istemciye veya dağıtım çalışma zamanına eklemek için kullanılan davranıştır. Uygulama, her iki durumda da temel değildir. <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> ve <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>' de ileti denetçisi oluşturulur ve ilgili çalışma zamanının <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> koleksiyonuna eklenir.  
  
```csharp  
public class SchemaValidationBehavior : IEndpointBehavior  
{  
    XmlSchemaSet schemaSet;   
    bool validateRequest;   
    bool validateReply;  
  
    public SchemaValidationBehavior(XmlSchemaSet schemaSet, bool   
                           inspectRequest, bool inspectReply)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = inspectReply;  
        this.validateRequest = inspectRequest;  
    }  
    #region IEndpointBehavior Members  
  
    public void AddBindingParameters(ServiceEndpoint endpoint,   
       System.ServiceModel.Channels.BindingParameterCollection   
                                            bindingParameters)  
    {  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint,   
            System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
    {  
        SchemaValidationMessageInspector inspector =   
           new SchemaValidationMessageInspector(schemaSet,   
                      validateRequest, validateReply, true);  
            clientRuntime.MessageInspectors.Add(inspector);  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint,   
         System.ServiceModel.Dispatcher.EndpointDispatcher   
                                          endpointDispatcher)  
    {  
        SchemaValidationMessageInspector inspector =   
           new SchemaValidationMessageInspector(schemaSet,   
                        validateRequest, validateReply, false);  
   endpointDispatcher.DispatchRuntime.MessageInspectors.Add(inspector);  
    }  
  
   public void Validate(ServiceEndpoint endpoint)  
   {  
   }  
  
    #endregion  
}  
```  
  
> [!NOTE]
> Bu belirli davranış bir öznitelik olarak Double değildir ve bu nedenle bir hizmet türünün anlaşma türüne bildirimli olarak eklenemez. Şema koleksiyonu bir öznitelik bildiriminde yüklenemeyeceği ve bu öznitelikteki ek bir yapılandırma konumuna (örneğin, uygulama ayarlarına) başvuran bir yapılandırma öğesi oluşturulması nedeniyle, bu bir tasarım tarafından yapılan karardır. , hizmet modeli yapılandırmasının geri kalanı ile tutarlı değil. Bu nedenle, bu davranış yalnızca kod üzerinden ve bir hizmet modeli yapılandırma uzantısı aracılığıyla imperatively eklenebilir.  
  
## <a name="adding-the-message-inspector-through-configuration"></a>Yapılandırma yoluyla Ileti denetçisi ekleme  
 Uygulama yapılandırma dosyasındaki bir uç noktada özel bir davranışı yapılandırmak için, hizmet modeli, ımplemenonun <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>türetilen bir sınıf tarafından temsil edilen bir yapılandırma *uzantısı öğesi* oluşturmasını gerektirir. Bu uzantı, bu bölümde açıklanan aşağıdaki uzantı için gösterildiği gibi, uzantılar için hizmet modelinin yapılandırma bölümüne eklenmelidir.  
  
```xml  
<system.serviceModel>  
…  
   <extensions>  
      <behaviorExtensions>  
        <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
      </behaviorExtensions>  
    </extensions>  
…  
</system.serviceModel>  
```  
  
 Uzantılar, en yaygın seçim olan veya makine yapılandırma dosyasında bulunan uygulama veya ASP.NET yapılandırma dosyasına eklenebilir.  
  
 Uzantı bir yapılandırma kapsamına eklendiğinde, davranış aşağıdaki kodda gösterildiği gibi bir davranış yapılandırmasına eklenebilir. Davranış yapılandırması, gerektiğinde birden çok uç noktaya uygulanabilen yeniden kullanılabilir öğelerdir. Burada yapılandırılacak belirli davranış <xref:System.ServiceModel.Description.IEndpointBehavior>uyguladığından, yalnızca yapılandırma dosyasında ilgili yapılandırma bölümünde geçerli olur.  
  
```xml  
<system.serviceModel>  
   <behaviors>  
      …  
     <endpointBehaviors>  
        <behavior name="HelloServiceEndpointBehavior">  
          <schemaValidator validateRequest="True" validateReply="True">  
            <schemas>  
              <add location="messages.xsd" />    
            </schemas>  
          </schemaValidator>  
        </behavior>  
      </endpointBehaviors>  
      …  
    </behaviors>  
</system.serviceModel>  
```  
  
 İleti denetçisini yapılandıran `<schemaValidator>` öğesi `SchemaValidationBehaviorExtensionElement` sınıfı tarafından desteklenir. Sınıfı, `ValidateRequest` ve `ValidateReply`adlı iki Boole ortak özelliği kullanıma sunar. Bunların her ikisi de bir <xref:System.Configuration.ConfigurationPropertyAttribute>işaretlenir. Bu öznitelik, önceki XML yapılandırma öğesinde görünebileceğiniz kod özellikleri ve XML öznitelikleri arasındaki bağlantıyı oluşturur. Ayrıca sınıfı, Ayrıca, <xref:System.Configuration.ConfigurationCollectionAttribute> birlikte işaretlenmiş ve bu örneğin bir parçası olan `SchemaCollection`tür olan ve bu örnek için bu belgede atlanan bir özellik `Schemas` sahiptir. Bu özellik koleksiyon ve koleksiyon öğesi sınıfıyla birlikte `SchemaConfigElement` önceki yapılandırma parçacığındaki `<schemas>` öğesini yedekler ve doğrulama kümesine bir şema koleksiyonu eklenmesine izin verir.  
  
 Geçersiz kılınan `CreateBehavior` yöntemi, çalışma zamanı bir istemci veya uç nokta oluşturduğunda yapılandırma verilerini değerlendirirken, yapılandırma verilerini bir davranış nesnesine dönüştürür.  
  
```csharp  
public class SchemaValidationBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public SchemaValidationBehaviorExtensionElement()  
    {  
    }  
  
    public override Type BehaviorType   
    {   
        get  
        {  
            return typeof(SchemaValidationBehavior);  
        }   
    }  
  
    protected override object CreateBehavior()  
    {  
        XmlSchemaSet schemaSet = new XmlSchemaSet();  
        foreach (SchemaConfigElement schemaCfg in this.Schemas)  
        {  
            Uri baseSchema = new   
                Uri(AppDomain.CurrentDomain.BaseDirectory);  
            string location = new   
                Uri(baseSchema,schemaCfg.Location).ToString();  
            XmlSchema schema =   
                XmlSchema.Read(new XmlTextReader(location), null);  
            schemaSet.Add(schema);  
        }  
     return new   
     SchemaValidationBehavior(schemaSet,ValidateRequest,ValidateReply);  
    }  
  
[ConfigurationProperty("validateRequest",DefaultValue=false,IsRequired=false)]  
public bool ValidateRequest  
{  
    get { return (bool)base["validateRequest"]; }  
    set { base["validateRequest"] = value; }  
}  
  
[ConfigurationProperty("validateReply", DefaultValue = false, IsRequired = false)]  
        public bool ValidateReply  
        {  
            get { return (bool)base["validateReply"]; }  
            set { base["validateReply"] = value; }  
        }  
  
     //Declare the Schema collection property.  
     //Note: the "IsDefaultCollection = false" instructs   
     //.NET Framework to build a nested section of   
     //the kind <Schema> ...</Schema>.  
    [ConfigurationProperty("schemas", IsDefaultCollection = true)]  
    [ConfigurationCollection(typeof(SchemasCollection),  
        AddItemName = "add",  
        ClearItemsName = "clear",  
        RemoveItemName = "remove")]  
    public SchemasCollection Schemas  
    {  
        get  
        {  
            SchemasCollection SchemasCollection =  
            (SchemasCollection)base["schemas"];  
            return SchemasCollection;  
        }  
    }  
}  
```  
  
## <a name="adding-message-inspectors-imperatively"></a>Ileti Inspectors Imperatively ekleme  
 Öznitelikleri (daha önce, bu örnekte, daha önce alıntı yapılan nedenler için desteklenmez) ve yapılandırma dışında, davranışları, zorunlu kod kullanarak istemci ve hizmet çalışma zamanına oldukça kolay bir şekilde eklenebilir. Bu örnekte, istemci uygulamasında istemci ileti denetçisini test etmek için bu yapılır. `GenericClient` sınıfı, uç nokta yapılandırmasını Kullanıcı koduna sunan <xref:System.ServiceModel.ClientBase%601>türetilir. İstemci örtük olarak açılmadan önce, aşağıdaki kodda gösterildiği gibi davranışları ekleyerek uç nokta yapılandırması değiştirilebilir. Hizmetin davranışını eklemek burada gösterilen istemci tekniğinden büyük ölçüde eşdeğerdir ve hizmet ana bilgisayarı açılmadan önce gerçekleştirilmesi gerekir.  
  
```csharp  
try  
{  
    Console.WriteLine("*** Call 'Hello' with generic client, with client behavior");  
    GenericClient client = new GenericClient();  
  
    // Configure client programmatically, adding behavior  
    XmlSchema schema = XmlSchema.Read(new StreamReader("messages.xsd"),   
                                                          null);  
    XmlSchemaSet schemaSet = new XmlSchemaSet();  
    schemaSet.Add(schema);  
    client.Endpoint.Behaviors.Add(new   
                SchemaValidationBehavior(schemaSet, true, true));  
  
    Console.WriteLine("--- Sending valid client request:");  
    GenericCallValid(client, helloAction);  
    Console.WriteLine("--- Sending invalid client request:");  
    GenericCallInvalid(client, helloAction);  
  
    client.Close();  
}  
catch (Exception e)  
{  
    DumpException(e);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
