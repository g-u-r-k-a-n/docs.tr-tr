---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Bölümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
ms.openlocfilehash: 548701f375b550e3a533a012bf34dc686ed42ac1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203611"
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="cb13f-102">Sorgu İfadesi Söz Dizimi Örnekleri: Bölümleme</span><span class="sxs-lookup"><span data-stu-id="cb13f-102">Query Expression Syntax Examples: Partitioning</span></span>

<span data-ttu-id="cb13f-103">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Skip%2A> <xref:System.Linq.Enumerable.Take%2A> sorgu ifadesi sözdizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cb13f-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="cb13f-104">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="cb13f-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="cb13f-105">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="cb13f-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="cb13f-106">Atla</span><span class="sxs-lookup"><span data-stu-id="cb13f-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="cb13f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb13f-107">Example</span></span>  

 <span data-ttu-id="cb13f-108">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Skip%2A> Seattle 'daki ilk iki adres hariç tümünü almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cb13f-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="cb13f-109">Take</span><span class="sxs-lookup"><span data-stu-id="cb13f-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="cb13f-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb13f-110">Example</span></span>  

 <span data-ttu-id="cb13f-111">Aşağıdaki örnek, <xref:System.Linq.Enumerable.Take%2A> Seattle 'daki ilk üç adresi almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cb13f-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="cb13f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb13f-112">See also</span></span>

- [<span data-ttu-id="cb13f-113">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="cb13f-113">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
