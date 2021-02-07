---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: kod içinde hizmet bağlama belirtme'
title: 'Nasıl yapılır: Kodda Hizmet Bağlama Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 744919fee4ec28d7df4581ac1d608d1fa9e99a29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755947"
---
# <a name="how-to-specify-a-service-binding-in-code"></a><span data-ttu-id="32545-103">Nasıl yapılır: Kodda Hizmet Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="32545-103">How to: Specify a Service Binding in Code</span></span>

<span data-ttu-id="32545-104">Bu örnekte, bir `ICalculator` anlaşma Hesaplayıcı hizmeti için tanımlanmıştır, hizmet `CalculatorService` sınıfında uygulanır ve ardından uç noktası kodda tanımlanır ve burada hizmetin sınıfını kullanması gerektiği belirtilir <xref:System.ServiceModel.BasicHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="32545-104">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="32545-105">Genellikle, bağlama ve adres bilgilerini, kod içinde imperatively yerine bildirimli olarak yapılandırmaya göre belirlemek en iyi uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="32545-105">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="32545-106">Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir.</span><span class="sxs-lookup"><span data-stu-id="32545-106">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="32545-107">Daha genel olarak, bağlama ve adresleme bilgilerini koddan tutmanın, uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="32545-107">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="32545-108">Bu hizmetin kod yerine yapılandırma öğelerini kullanarak nasıl yapılandırılacağı hakkında bir açıklama için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="32545-108">For a description of how to configure this service using configuration elements instead of code, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a><span data-ttu-id="32545-109">Hizmet için BasicHttpBinding 'in kullanılacağı kodu belirtmek için</span><span class="sxs-lookup"><span data-stu-id="32545-109">To specify in code to use the BasicHttpBinding for the service</span></span>  
  
1. <span data-ttu-id="32545-110">Hizmet türü için bir hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="32545-110">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="32545-111">Hizmet sözleşmesini bir hizmet sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="32545-111">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="32545-112">Barındırma uygulamasında, hizmet için temel adresi ve hizmetle birlikte kullanılacak bağlamayı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="32545-112">In the hosting application, create the base address for the service and the binding to use with the service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="32545-113">Hizmet için konak oluşturun, uç noktayı ekleyin ve ardından Konağı açın.</span><span class="sxs-lookup"><span data-stu-id="32545-113">Create the host for the service, add the endpoint, and then open the host.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="32545-114">Bağlama özelliklerinin varsayılan değerlerini değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="32545-114">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="32545-115">Sınıfının varsayılan özellik değerlerinden birini değiştirmek için <xref:System.ServiceModel.BasicHttpBinding> , Konağı oluşturmadan önce bağlamasındaki özellik değerini yeni değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="32545-115">To modify one of the default property values of the <xref:System.ServiceModel.BasicHttpBinding> class, set the property value on the binding to the new value before creating the host.</span></span> <span data-ttu-id="32545-116">Örneğin, varsayılan açık ve kapalı zaman aşımı değerlerini 1 dakika ila 2 dakika olarak değiştirmek için aşağıdakileri kullanın.</span><span class="sxs-lookup"><span data-stu-id="32545-116">For example, to change the default open and close timeout values of 1 minute to 2 minutes, use the following.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="32545-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32545-117">See also</span></span>

- [<span data-ttu-id="32545-118">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="32545-118">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="32545-119">Bir Uç Noktası Adresi Belirtme</span><span class="sxs-lookup"><span data-stu-id="32545-119">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
