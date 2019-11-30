---
title: 'Nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: cf20c1d27f22c0248217541763eaa617ed9493db
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569287"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="7e451-102">Nasıl yapılır: yansıma sağlayıcısını kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)</span><span class="sxs-lookup"><span data-stu-id="7e451-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
<span data-ttu-id="7e451-103">WCF Veri Hizmetleri, bu sınıfların <xref:System.Linq.IQueryable%601> arabirimini uygulayan nesneler olarak kullanıma sunulduğunu sürece rastgele sınıflara dayalı bir veri modeli tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e451-103">WCF Data Services enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="7e451-104">Daha fazla bilgi için bkz. [veri hizmetleri sağlayıcıları](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7e451-104">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e451-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e451-105">Example</span></span>  
 <span data-ttu-id="7e451-106">Aşağıdaki örnek, `Orders` ve `Items`içeren bir veri modelini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7e451-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="7e451-107">`OrderItemData` varlık kapsayıcı sınıfı, <xref:System.Linq.IQueryable%601> arabirimleri döndüren iki ortak yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="7e451-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="7e451-108">Bu arabirimler `Orders` ve `Items` varlık türlerinin varlık kümeleridir.</span><span class="sxs-lookup"><span data-stu-id="7e451-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="7e451-109">`Order` birden çok `Items`içerebilir, bu nedenle `Orders` varlık türünün `Items` nesnelerden oluşan bir koleksiyonu döndüren bir `Items` gezinti özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="7e451-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="7e451-110">`OrderItemData` varlık kapsayıcı sınıfı, `OrderItems` veri hizmetinin türetildiği <xref:System.Data.Services.DataService%601> sınıfının genel türüdür.</span><span class="sxs-lookup"><span data-stu-id="7e451-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e451-111">Bu örnek, bellek içi bir veri sağlayıcısını gösterdiği ve değişiklikler geçerli nesne örnekleri dışında kalıcı olmadığından, <xref:System.Data.Services.IUpdatable> arabirimini uygulamadan elde edilen bir avantaj yoktur.</span><span class="sxs-lookup"><span data-stu-id="7e451-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="7e451-112"><xref:System.Data.Services.IUpdatable> arabirimini uygulayan bir örnek için bkz. [nasıl yapılır: LINQ to SQL veri kaynağı kullanarak veri hizmeti oluşturma](create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="7e451-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="7e451-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e451-113">See also</span></span>

- [<span data-ttu-id="7e451-114">Nasıl yapılır: LINQ to SQL Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e451-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="7e451-115">Veri Hizmetleri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="7e451-115">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="7e451-116">Nasıl yapılır: ADO.NET Entity Framework Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e451-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
