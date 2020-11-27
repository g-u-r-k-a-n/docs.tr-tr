---
title: İleti Düzeyi Programlama ile JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 8343f7a8aa3c01557aae7df420351fa318cbb4b5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253940"
---
# <a name="serializing-in-json-with-message-level-programming"></a><span data-ttu-id="5b32c-102">İleti Düzeyi Programlama ile JSON Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5b32c-102">Serializing in Json with Message Level Programming</span></span>

<span data-ttu-id="5b32c-103">WCF, JSON biçimindeki verilerin serileştirilmesinin kullanılmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="5b32c-103">WCF supports serializing data in JSON format.</span></span> <span data-ttu-id="5b32c-104">Bu konuda, WCF 'yi kullanarak türlerinizi serileştirmek için nasıl söyleyeceğinizi açıklanmaktadır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="5b32c-104">This topic describes how to tell WCF to serialize your types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="typed-message-programming"></a><span data-ttu-id="5b32c-105">Yazılan Ileti programlama</span><span class="sxs-lookup"><span data-stu-id="5b32c-105">Typed Message Programming</span></span>  

 <span data-ttu-id="5b32c-106">, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.ServiceModel.Web.WebGetAttribute> Veya <xref:System.ServiceModel.Web.WebInvokeAttribute> bir hizmet işlemine uygulandığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b32c-106">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is used when the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute> is applied to a service operation.</span></span> <span data-ttu-id="5b32c-107">Bu özniteliklerin her ikisi de belirtmenizi sağlar `RequestFormat` `ResponseFormat` .</span><span class="sxs-lookup"><span data-stu-id="5b32c-107">Both of these attributes allow you to specify the `RequestFormat` and `ResponseFormat`.</span></span> <span data-ttu-id="5b32c-108">İstekleri ve yanıtları için JSON kullanmak.</span><span class="sxs-lookup"><span data-stu-id="5b32c-108">To use JSON for requests and responses.</span></span> <span data-ttu-id="5b32c-109">her ikisini de olarak ayarlayın `WebMessageFormat.Json` .</span><span class="sxs-lookup"><span data-stu-id="5b32c-109">set both of these to `WebMessageFormat.Json`.</span></span>  <span data-ttu-id="5b32c-110">JSON kullanmak için, <xref:System.ServiceModel.WebHttpBinding> ' yi otomatik olarak yapılandıran öğesini kullanmanız gerekir <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="5b32c-110">In order to use JSON, you must use the <xref:System.ServiceModel.WebHttpBinding>, which automatically configures the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span> <span data-ttu-id="5b32c-111">WCF serileştirme hakkında daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="5b32c-111">For more information about WCF serialization, see [Serialization and Deserialization](serialization-and-deserialization.md).</span></span> <span data-ttu-id="5b32c-112">JSON ve WCF hakkında daha fazla bilgi için bkz. [hizmet istasyonu-WCF Ile yeniden hizmet vermek Için bir giriş](/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).</span><span class="sxs-lookup"><span data-stu-id="5b32c-112">For more information about JSON and WCF, see [Service Station - An Introduction To RESTful Services With WCF](/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5b32c-113">JSON kullanımı, <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> SOAP iletişimini desteklemeyen ve kullanımını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5b32c-113">Using JSON requires use of <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> which do not support SOAP communication.</span></span> <span data-ttu-id="5b32c-114">İle iletişim kuran hizmetler, <xref:System.ServiceModel.WebHttpBinding> hizmet meta verilerinin sunulmasını desteklemez; böylece, istemci tarafı proxy oluşturmak Için Visual Studio 'nun hizmet başvurusu Ekle işlevselliğini veya Svcutil komut satırı aracını kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="5b32c-114">Services that communicate with the <xref:System.ServiceModel.WebHttpBinding> do not support exposing service metadata so you will not be able to use Visual Studio’s Add Service Reference functionality or the svcutil command-line tool to generate a client-side proxy.</span></span> <span data-ttu-id="5b32c-115">Tarafından kullanılan Hizmetleri programlı olarak nasıl çağırabilmeniz hakkında daha fazla bilgi için <xref:System.ServiceModel.WebHttpBinding> bkz. [WCF Ile Rest hizmetlerini kullanma](/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).</span><span class="sxs-lookup"><span data-stu-id="5b32c-115">For more information how you can programmatically call services that use <xref:System.ServiceModel.WebHttpBinding>, see [How to Consume REST Services with WCF](/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).</span></span>  
  
## <a name="untyped-message-programming"></a><span data-ttu-id="5b32c-116">Türsüz Ileti programlama</span><span class="sxs-lookup"><span data-stu-id="5b32c-116">Untyped Message Programming</span></span>  

 <span data-ttu-id="5b32c-117">Türsüz Ileti nesneleriyle doğrudan çalışırken, türsüz iletideki özellikleri JSON olarak seri hale getirmek için açıkça ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b32c-117">When working directly with untyped Message objects, you must explicitly set the properties on the untyped message to serialize it as JSON.</span></span> <span data-ttu-id="5b32c-118">Aşağıdaki kod parçacığında bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5b32c-118">The following code snippet shows how to do this.</span></span>  
  
```csharp
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b32c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b32c-119">See also</span></span>

- [<span data-ttu-id="5b32c-120">AJAX Tümleştirme ve JSON Desteği</span><span class="sxs-lookup"><span data-stu-id="5b32c-120">AJAX Integration and JSON Support</span></span>](ajax-integration-and-json-support.md)
- [<span data-ttu-id="5b32c-121">Bağımsız JSON Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5b32c-121">Stand-Alone JSON Serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="5b32c-122">JSON serileştirme</span><span class="sxs-lookup"><span data-stu-id="5b32c-122">JSON Serialization</span></span>](../samples/json-serialization.md)
