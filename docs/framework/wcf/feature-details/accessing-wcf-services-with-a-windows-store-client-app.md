---
title: WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: ff6638936f476bd8fe75a065d3e61e96790cb7f4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597702"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="56f08-102">WCF Hizmetlerine Windows Mağazası İstemci Uygulaması ile Erişme</span><span class="sxs-lookup"><span data-stu-id="56f08-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="56f08-103">Windows 8, Windows Mağazası uygulamaları adlı yeni bir uygulama türü sunar.</span><span class="sxs-lookup"><span data-stu-id="56f08-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="56f08-104">Bu uygulamalar dokunmatik ekran arabirimi etrafında tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="56f08-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="56f08-105">.NET Framework 4,5, Windows Mağazası uygulamalarının WCF hizmetlerini çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="56f08-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="56f08-106">Windows Mağazası uygulamalarında WCF desteği</span><span class="sxs-lookup"><span data-stu-id="56f08-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="56f08-107">WCF işlevselliğinin bir alt kümesi bir Windows Mağazası uygulaması içinden edinilebilir, daha fazla ayrıntı için aşağıdaki bölümlere bakın.</span><span class="sxs-lookup"><span data-stu-id="56f08-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="56f08-108">WCF tarafından sunulmayan yerine WinRT dağıtım API 'Lerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="56f08-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="56f08-109">Daha fazla bilgi için bkz. [WinRT dağıtım API 'si](xref:Windows.Web.Syndication)</span><span class="sxs-lookup"><span data-stu-id="56f08-109">For more information see, [WinRT Syndication API](xref:Windows.Web.Syndication)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="56f08-110">Bir Windows Çalışma Zamanı bileşenine Web hizmeti başvurusu eklemek için Hizmet Başvurusu Ekle kullanmak desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="56f08-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="56f08-111">Desteklenen bağlamalar</span><span class="sxs-lookup"><span data-stu-id="56f08-111">Supported Bindings</span></span>  
 <span data-ttu-id="56f08-112">Windows Mağazası uygulamalarında aşağıdaki WCF bağlamaları desteklenir:</span><span class="sxs-lookup"><span data-stu-id="56f08-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="56f08-113">Windows Mağazası uygulamalarında aşağıdaki bağlama öğeleri desteklenir</span><span class="sxs-lookup"><span data-stu-id="56f08-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="56f08-114">Hem metin hem de Ikili kodlamalar desteklenir.</span><span class="sxs-lookup"><span data-stu-id="56f08-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="56f08-115">Tüm WCF aktarım modları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="56f08-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="56f08-116">Daha fazla bilgi için bkz. [akış Ileti aktarımı](streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="56f08-116">For more information see, [Streaming Message Transfer](streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="56f08-117">Hizmet Başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="56f08-117">Add Service Reference</span></span>  
 <span data-ttu-id="56f08-118">Bir Windows Mağazası uygulamasından bir WCF hizmetini çağırmak için, Visual Studio 2012 Hizmet Başvurusu Ekle özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="56f08-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="56f08-119">Windows Mağazası uygulamasında yapıldığında Hizmet Başvurusu Ekle işlevselliğinde birkaç değişiklik olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="56f08-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="56f08-120">İlk olarak hiçbir yapılandırma dosyası oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="56f08-120">First no configuration file is generated.</span></span> <span data-ttu-id="56f08-121">Windows Mağazası uygulamaları yapılandırma dosyalarını kullanmaz, bu nedenle kodda yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="56f08-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="56f08-122">Bu yapılandırma kodu, Hizmet Başvurusu Ekle tarafından oluşturulan References.cs dosyasında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="56f08-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="56f08-123">Bu dosyayı görmek için Çözüm Gezgini 'nde "tüm dosyaları göster" seçeneğini belirlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="56f08-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="56f08-124">Dosya, hizmet başvurularının altında bulunur ve ardından proje içindeki. svcmap düğümlerine başvuracaktır.</span><span class="sxs-lookup"><span data-stu-id="56f08-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="56f08-125">Bir Windows Mağazası uygulaması içindeki WCF Hizmetleri için oluşturulan tüm işlemler, görev tabanlı zaman uyumsuz model kullanılarak zaman uyumsuz olacaktır.</span><span class="sxs-lookup"><span data-stu-id="56f08-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="56f08-126">Daha fazla bilgi için bkz. [zaman uyumsuz görevler-görevlerle zaman uyumsuz programlamayı kolaylaştırın](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span><span class="sxs-lookup"><span data-stu-id="56f08-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span></span>  
  
 <span data-ttu-id="56f08-127">Yapılandırma artık kodda oluşturulduğundan, hizmet başvurusunun her güncelleştirildiği her seferinde Reference.cs dosyasında yapılan tüm değişikliklerin üzerine yazılacak.</span><span class="sxs-lookup"><span data-stu-id="56f08-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="56f08-128">Bu durumu gidermek için yapılandırma kodu, istemci proxy sınıfınız içinde uygulayabileceğiniz kısmi bir yöntemde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="56f08-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="56f08-129">Kısmi Yöntem şu şekilde bildirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="56f08-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="56f08-130">Daha sonra bu kısmi yöntemi uygulayabilir ve istemci proxy sınıfınızın bağlama veya uç noktasını aşağıdaki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="56f08-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a><span data-ttu-id="56f08-131">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="56f08-131">Serialization</span></span>  
 <span data-ttu-id="56f08-132">Windows Mağazası uygulamalarında aşağıdaki serileştiriciler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="56f08-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="56f08-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="56f08-133">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="56f08-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="56f08-134">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="56f08-135">Çağrılamıyor</span><span class="sxs-lookup"><span data-stu-id="56f08-135">XmlSerializer</span></span>  
  
> [!WARNING]
> <span data-ttu-id="56f08-136">XmlDictionaryWriter. Write (DateTime) şimdi DateTime nesnesini bir dize olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="56f08-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="56f08-137">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="56f08-137">Security</span></span>  

<span data-ttu-id="56f08-138">Windows Mağazası uygulamalarında aşağıdaki güvenlik modları desteklenir:</span><span class="sxs-lookup"><span data-stu-id="56f08-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="56f08-139">Aşağıdaki istemci kimlik bilgisi türleri Windows Mağazası uygulamalarında desteklenir:</span><span class="sxs-lookup"><span data-stu-id="56f08-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="56f08-140">Yok</span><span class="sxs-lookup"><span data-stu-id="56f08-140">None</span></span>  
  
2. <span data-ttu-id="56f08-141">Temel</span><span class="sxs-lookup"><span data-stu-id="56f08-141">Basic</span></span>  
  
3. <span data-ttu-id="56f08-142">Bilgisi</span><span class="sxs-lookup"><span data-stu-id="56f08-142">Digest</span></span>  
  
4. <span data-ttu-id="56f08-143">Anlaşma</span><span class="sxs-lookup"><span data-stu-id="56f08-143">Negotiate</span></span>  
  
5. <span data-ttu-id="56f08-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="56f08-144">NTLM</span></span>  
  
6. <span data-ttu-id="56f08-145">Windows</span><span class="sxs-lookup"><span data-stu-id="56f08-145">Windows</span></span>  
  
7. <span data-ttu-id="56f08-146">Kullanıcı adı (Ileti güvenliği)</span><span class="sxs-lookup"><span data-stu-id="56f08-146">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="56f08-147">Windows (taşıma güvenliği)</span><span class="sxs-lookup"><span data-stu-id="56f08-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="56f08-148">Windows Mağazası uygulamalarının varsayılan Windows kimlik bilgilerini erişmesi ve gönderebilmesi için, bu işlevselliği Package. AppManifest dosyası içinde etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="56f08-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="56f08-149">Bu dosyayı açın ve yetenekler sekmesini seçin ve "varsayılan Windows kimlik bilgileri" ni seçin.</span><span class="sxs-lookup"><span data-stu-id="56f08-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="56f08-150">Bu, uygulamanın etki alanı kimlik bilgileri gerektiren intranet kaynaklarına bağlanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="56f08-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="56f08-151">Windows Mağazası uygulamalarının çapraz makine çağrıları yapması için, "Ev/Iş ağı" adlı başka bir özelliği etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="56f08-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="56f08-152">Bu ayar ayrıca Yetenekler sekmesi altındaki Package. AppManifest dosyasında bulunur. Ev/Iş ağı onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="56f08-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="56f08-153">Bu, uygulamanıza giriş ve çalışma gibi kullanıcının güvenilen yerlerinin ağlarına gelen ve giden erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="56f08-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="56f08-154">Gelen kritik bağlantı noktaları her zaman engellenir.</span><span class="sxs-lookup"><span data-stu-id="56f08-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="56f08-155">Internet 'teki hizmetlere erişim için Internet (Istemci) özelliğini de etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="56f08-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="56f08-156">Çeşitli</span><span class="sxs-lookup"><span data-stu-id="56f08-156">Misc</span></span>  
 <span data-ttu-id="56f08-157">Aşağıdaki sınıfların kullanımı Windows Mağazası uygulamaları için desteklenir:</span><span class="sxs-lookup"><span data-stu-id="56f08-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="56f08-158">Hizmet sözleşmelerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="56f08-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="56f08-159">Yalnızca görev tabanlı zaman uyumsuz model kullanarak zaman uyumsuz hizmet işlemlerini tanımlamayı öneririz.</span><span class="sxs-lookup"><span data-stu-id="56f08-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="56f08-160">Bu, bir hizmet işlemi çağrılırken Windows Mağazası uygulamalarının yanıt vermeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="56f08-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="56f08-161">Zaman uyumlu bir işlem tanımlarsanız hiçbir özel durum oluşturulmaz, ancak yalnızca zaman uyumsuz işlemler tanımlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="56f08-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="56f08-162">Windows Mağazası uygulamalarından WCF Hizmetleri çağırma</span><span class="sxs-lookup"><span data-stu-id="56f08-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="56f08-163">Oluşturulan proxy sınıfında GetBindingForEndpoint yöntemindeki kodda tüm yapılandırma yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56f08-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="56f08-164">Bir hizmet işleminin çağrılması, aşağıdaki kod parçacığında gösterildiği gibi herhangi bir görev tabanlı zaman uyumsuz yöntemi çağırma ile aynı şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="56f08-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 <span data-ttu-id="56f08-165">Zaman uyumsuz çağrıyı yapan yöntemde async anahtar sözcüğünün kullanımını ve zaman uyumsuz yöntemi çağırırken await anahtar sözcüğünü kullanmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="56f08-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f08-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56f08-166">See also</span></span>

- [<span data-ttu-id="56f08-167">Windows Mağazası uygulamaları blogu 'nda WCF</span><span class="sxs-lookup"><span data-stu-id="56f08-167">WCF in Windows Store Apps Blog</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/wcf-in-windows-8-metro-styled-apps-absolutely-supported)
- [<span data-ttu-id="56f08-168">WCF Windows Mağazası Istemcileri ve güvenliği</span><span class="sxs-lookup"><span data-stu-id="56f08-168">WCF Windows Store Clients and Security</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-adding-security)
- [<span data-ttu-id="56f08-169">Windows Mağazası uygulamaları ve çapraz makine çağrıları</span><span class="sxs-lookup"><span data-stu-id="56f08-169">Windows Store Apps and Cross Machine Calls</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="56f08-170">Azure 'da dağıtılan bir WCF hizmetini bir Windows Mağazası uygulamasından çağırma</span><span class="sxs-lookup"><span data-stu-id="56f08-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="56f08-171">WCF Güvenliğini Programlama</span><span class="sxs-lookup"><span data-stu-id="56f08-171">Programming WCF Security</span></span>](programming-wcf-security.md)
- [<span data-ttu-id="56f08-172">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="56f08-172">Bindings</span></span>](../bindings.md)
