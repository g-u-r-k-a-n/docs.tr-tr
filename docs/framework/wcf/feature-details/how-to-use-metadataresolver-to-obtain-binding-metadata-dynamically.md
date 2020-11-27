---
title: 'Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: fc64e11271c6901a8d4598c0efa563a06a92decf
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280721"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="b2e95-102">Nasıl yapılır: Bağlama Meta Verilerini Dinamik Olarak Almak için MetadataResolver Kullanma</span><span class="sxs-lookup"><span data-stu-id="b2e95-102">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>

<span data-ttu-id="b2e95-103">Bu konuda, <xref:System.ServiceModel.Description.MetadataResolver> sınıfının bağlama meta verilerini dinamik olarak almak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b2e95-103">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="b2e95-104">Bağlama meta verilerini dinamik olarak almak için</span><span class="sxs-lookup"><span data-stu-id="b2e95-104">To dynamically obtain binding metadata</span></span>  
  
1. <span data-ttu-id="b2e95-105"><xref:System.ServiceModel.EndpointAddress>Meta veri uç noktası adresiyle bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b2e95-105">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```csharp
    EndpointAddress metaAddress  
      = new EndpointAddress(new Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. <span data-ttu-id="b2e95-106"><xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>Hizmet türü ve meta veri uç noktası adresinde geçen çağrı.</span><span class="sxs-lookup"><span data-stu-id="b2e95-106">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="b2e95-107">Bu, belirtilen sözleşmeyi uygulayan bitiş noktaları koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2e95-107">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="b2e95-108">Meta verilerden yalnızca bağlama bilgileri içeri aktarılır; sözleşme bilgileri içeri aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="b2e95-108">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="b2e95-109">Bunun yerine sağlanan sözleşme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b2e95-109">The supplied contract is used instead.</span></span>  
  
    ```csharp  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. <span data-ttu-id="b2e95-110">Daha sonra, ihtiyacınız olan bağlama bilgilerini ayıklamak için hizmet uç noktaları koleksiyonunu yineleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2e95-110">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="b2e95-111">Aşağıdaki kod uç noktalar üzerinden yinelenir, geçerli uç noktayla ilişkili bağlama ve adreste geçen bir hizmet istemci nesnesi oluşturur ve sonra hizmette bir yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b2e95-111">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
    ```csharp  
    foreach (ServiceEndpoint point in endpoints)  
    {  
       if (point != null)  
       {  
          // Create a new wcfClient using retrieved endpoints.  
          using (wcfClient = new SampleServiceClient(point.Binding, point.Address))  
          {  
             Console.WriteLine(  
               wcfClient.SampleMethod("Client used the "  
               + point.Address.ToString() + " address."));  
          }  
      }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b2e95-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2e95-112">See also</span></span>

- [<span data-ttu-id="b2e95-113">Meta veri</span><span class="sxs-lookup"><span data-stu-id="b2e95-113">Metadata</span></span>](metadata.md)
