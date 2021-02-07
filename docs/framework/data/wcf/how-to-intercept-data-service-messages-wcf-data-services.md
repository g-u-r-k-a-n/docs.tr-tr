---
description: ': Nasıl yapılır: veri hizmeti Iletilerini kesme (WCF Veri Hizmetleri) hakkında daha fazla bilgi edinin'
title: 'Nasıl yapılır: veri hizmeti Iletilerini kesme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: 6768fa9f0c7ca9a5a6ed6faa318675f2c2c51543
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765288"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a><span data-ttu-id="5d97c-103">Nasıl yapılır: veri hizmeti Iletilerini kesme (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="5d97c-103">How to: Intercept Data Service Messages (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="5d97c-104">WCF Veri Hizmetleri, bir işleme özel mantık ekleyebilmeniz için istek iletilerini ele alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d97c-104">With WCF Data Services, you can intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="5d97c-105">Bir iletiyi ele almak için veri hizmetinde özel olarak öznitelikli yöntemleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5d97c-105">To intercept a message, you use specially attributed methods in the data service.</span></span> <span data-ttu-id="5d97c-106">Daha fazla bilgi için bkz. [yakalayıcılar](interceptors-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="5d97c-106">For more information, see [Interceptors](interceptors-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="5d97c-107">Bu konudaki örnek, Northwind örnek veri hizmetini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d97c-107">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="5d97c-108">Bu hizmet, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5d97c-108">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a><span data-ttu-id="5d97c-109">Siparişler varlık kümesi için bir sorgu yakalayıcısı tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="5d97c-109">To define a query interceptor for the Orders entity set</span></span>  
  
1. <span data-ttu-id="5d97c-110">Northwind Data Service projesinde, Northwind. svc dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="5d97c-110">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2. <span data-ttu-id="5d97c-111">Sınıfına ait kod sayfasında `Northwind` , aşağıdaki `using` ifadeyi ekleyin ( `Imports` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5d97c-111">In the code page for the `Northwind` class, add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. <span data-ttu-id="5d97c-112">`Northwind`Sınıfında, aşağıdaki gibi adlı bir hizmet işlemi yöntemi tanımlayın `OnQueryOrders` :</span><span class="sxs-lookup"><span data-stu-id="5d97c-112">In the `Northwind` class, define a service operation method named `OnQueryOrders` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a><span data-ttu-id="5d97c-113">Ürünler varlık kümesi için bir değişiklik yakalayıcısı tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="5d97c-113">To define a change interceptor for the Products entity set</span></span>  
  
1. <span data-ttu-id="5d97c-114">Northwind Data Service projesinde, Northwind. svc dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="5d97c-114">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2. <span data-ttu-id="5d97c-115">`Northwind`Sınıfında, aşağıdaki gibi adlı bir hizmet işlemi yöntemi tanımlayın `OnChangeProducts` :</span><span class="sxs-lookup"><span data-stu-id="5d97c-115">In the `Northwind` class, define a service operation method named `OnChangeProducts` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a><span data-ttu-id="5d97c-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d97c-116">Example</span></span>  

 <span data-ttu-id="5d97c-117">Bu örnek, `Orders` bir lambda ifadesi döndüren varlık kümesi için bir sorgu yakalayıcısı yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5d97c-117">This example defines a query interceptor method for the `Orders` entity set that returns a lambda expression.</span></span> <span data-ttu-id="5d97c-118">Bu ifade, `Orders` `Customers` belirli bir kişi adına sahip olan ilişkili öğesine bağlı olarak filtre uygulayan bir temsilci içerir.</span><span class="sxs-lookup"><span data-stu-id="5d97c-118">This expression contains a delegate that filters the requested `Orders` based on related `Customers` that have a specific contact name.</span></span> <span data-ttu-id="5d97c-119">Ad, istekte bulunan kullanıcıya göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5d97c-119">The name is in turn determined based on the requesting user.</span></span> <span data-ttu-id="5d97c-120">Bu örnekte, veri hizmetinin WCF kullanan bir ASP.NET Web uygulaması içinde barındırıldığı ve kimlik doğrulamasının etkinleştirildiği varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5d97c-120">This example assumes that the data service is hosted within an ASP.NET Web application that uses WCF, and that authentication is enabled.</span></span> <span data-ttu-id="5d97c-121"><xref:System.Web.HttpContext>Sınıfı, geçerli isteğin ilkesini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d97c-121">The <xref:System.Web.HttpContext> class is used to retrieve the principle of the current request.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a><span data-ttu-id="5d97c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d97c-122">Example</span></span>  

 <span data-ttu-id="5d97c-123">Bu örnek, varlık kümesi için bir değişiklik yakalayıcısı yöntemi tanımlar `Products` .</span><span class="sxs-lookup"><span data-stu-id="5d97c-123">This example defines a change interceptor method for the `Products` entity set.</span></span> <span data-ttu-id="5d97c-124">Bu yöntem bir veya işlemi için hizmete girişi doğrular <xref:System.Data.Services.UpdateOperations.Add> <xref:System.Data.Services.UpdateOperations.Change> ve üretimi durdurulmuş bir ürüne yapılan bir değişiklik yapılırsa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d97c-124">This method validates input to the service for an <xref:System.Data.Services.UpdateOperations.Add> or <xref:System.Data.Services.UpdateOperations.Change> operation and raises an exception if a change is being made to a discontinued product.</span></span> <span data-ttu-id="5d97c-125">Ayrıca, ürünlerin desteklenmeyen bir işlem olarak silinmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="5d97c-125">It also blocks the deletion of products as an unsupported operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a><span data-ttu-id="5d97c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d97c-126">See also</span></span>

- [<span data-ttu-id="5d97c-127">Nasıl yapılır: Hizmet İşlemi Tanımlama</span><span class="sxs-lookup"><span data-stu-id="5d97c-127">How to: Define a Service Operation</span></span>](how-to-define-a-service-operation-wcf-data-services.md)
- [<span data-ttu-id="5d97c-128">WCF Veri Hizmetlerini Tanımlama</span><span class="sxs-lookup"><span data-stu-id="5d97c-128">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
