---
description: 'Hakkında daha fazla bilgi edinin: Method-Based sorgu söz dizimi örnekleri: filtreleme'
title: 'Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e40e314c-eb30-4f44-a054-41e511e35832
ms.openlocfilehash: c9d051712ea1e7a0db8e4fd66f4b8891ceeee488
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673537"
---
# <a name="method-based-query-syntax-examples-filtering"></a><span data-ttu-id="37bc9-103">Metot Tabanlı Sorgu Söz Dizimi Örnekleri: Filtreleme</span><span class="sxs-lookup"><span data-stu-id="37bc9-103">Method-Based Query Syntax Examples: Filtering</span></span>

<span data-ttu-id="37bc9-104">Bu konudaki örneklerde, `Where` ve `Where…Contains` yöntemlerinin Yöntem tabanlı sorgu söz dizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="37bc9-104">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="37bc9-105">Note, burada...`Contains`</span><span class="sxs-lookup"><span data-stu-id="37bc9-105">Note, Where…`Contains`</span></span> <span data-ttu-id="37bc9-106">, [derlenmiş bir sorgunun](compiled-queries-linq-to-entities.md)parçası olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="37bc9-106">cannot be used as a part of a [compiled query](compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="37bc9-107">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="37bc9-107">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="37bc9-108">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="37bc9-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="37bc9-109">Konum</span><span class="sxs-lookup"><span data-stu-id="37bc9-109">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="37bc9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="37bc9-110">Example</span></span>  

 <span data-ttu-id="37bc9-111">Aşağıdaki örnek tüm çevrimiçi siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="37bc9-111">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1_mq)]
 [!code-vb[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1_mq)]  
  
### <a name="example"></a><span data-ttu-id="37bc9-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="37bc9-112">Example</span></span>  

 <span data-ttu-id="37bc9-113">Aşağıdaki örnek, sipariş miktarının 2 ' den büyük ve 6 ' dan küçük olduğu siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="37bc9-113">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2_mq)]
 [!code-vb[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2_mq)]  
  
### <a name="example"></a><span data-ttu-id="37bc9-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="37bc9-114">Example</span></span>  

 <span data-ttu-id="37bc9-115">Aşağıdaki örnek, tüm kırmızı renkli ürünleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="37bc9-115">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3_mq)]
 [!code-vb[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3_mq)]  
  
### <a name="example"></a><span data-ttu-id="37bc9-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="37bc9-116">Example</span></span>  

 <span data-ttu-id="37bc9-117">Aşağıdaki örnek, `Where` 1 aralık 2003 ' den sonra yapılan siparişleri bulmak için yöntemini kullanır ve ardından `order.SalesOrderDetail` her bir siparişin ayrıntılarını almak için gezinti özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="37bc9-117">The following example uses the `Where` method to find orders that were made after December 1, 2003 and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty_mq)]
 [!code-vb[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty_mq)]  
  
## <a name="wherecontains"></a><span data-ttu-id="37bc9-118">Where... Vardır</span><span class="sxs-lookup"><span data-stu-id="37bc9-118">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="37bc9-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="37bc9-119">Example</span></span>  

 <span data-ttu-id="37bc9-120">Aşağıdaki örnek `Where…Contains` dizideki bir değerle eşleşen tüm ürünleri bulmak için yan tümcesinin bir parçası olarak bir diziyi kullanır `ProductModelID` .</span><span class="sxs-lookup"><span data-stu-id="37bc9-120">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#3)]
 [!code-vb[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#3)]  
  
> [!NOTE]
> <span data-ttu-id="37bc9-121">Bir yan tümcedeki koşulun bir parçası olarak, bir, `Where…Contains` <xref:System.Array> <xref:System.Collections.Generic.List%601> veya arabirimini uygulayan herhangi bir türün koleksiyonunu kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="37bc9-121">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="37bc9-122">Ayrıca, bir LINQ to Entities sorgusu içinde bir koleksiyonu bildirebilir ve başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="37bc9-122">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="37bc9-123">Daha fazla bilgi için bkz. sonraki örnek.</span><span class="sxs-lookup"><span data-stu-id="37bc9-123">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="37bc9-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="37bc9-124">Example</span></span>  

 <span data-ttu-id="37bc9-125">Aşağıdaki örnek, diziler içindeki bir `Where…Contains` değerle eşleşen bir veya içeren tüm ürünleri bulmak için bir yan tümcedeki dizileri bildirir ve başlatır `ProductModelID` `Size` .</span><span class="sxs-lookup"><span data-stu-id="37bc9-125">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or a `Size` that matches a value in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#4)]
 [!code-vb[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="37bc9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37bc9-126">See also</span></span>

- [<span data-ttu-id="37bc9-127">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="37bc9-127">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
