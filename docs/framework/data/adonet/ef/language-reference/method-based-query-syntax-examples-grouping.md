---
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Gruplandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: 2d84e755217878bfa248add37a752224a20d3f84
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191989"
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="5231d-102">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="5231d-102">Method-Based Query Syntax Examples: Grouping</span></span>

<span data-ttu-id="5231d-103">Bu konudaki örneklerde, yöntem `GroupBy` tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için yönteminin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5231d-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="5231d-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5231d-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5231d-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="5231d-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="5231d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="5231d-106">Example</span></span>  

 <span data-ttu-id="5231d-107">Aşağıdaki örnek, `GroupBy` `Address` posta koduna göre gruplandırılan nesneleri döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5231d-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="5231d-108">Sonuçlar anonim bir türe yansıtılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="5231d-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="5231d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5231d-109">Example</span></span>  

 <span data-ttu-id="5231d-110">Aşağıdaki örnek, `GroupBy` `Contact` kişinin son adının ilk harfine göre gruplanmış nesneleri döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5231d-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="5231d-111">Sonuçlar Ayrıca son adın ilk harfine göre sıralanır ve bir anonim türe yansıtılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5231d-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="5231d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="5231d-112">Example</span></span>  

 <span data-ttu-id="5231d-113">Aşağıdaki örnek, `GroupBy` `SalesOrderHeader` Müşteri kimliğine göre gruplanmış nesneleri döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5231d-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="5231d-114">Her müşteri için satış sayısı da döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5231d-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="5231d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5231d-115">See also</span></span>

- [<span data-ttu-id="5231d-116">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="5231d-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
