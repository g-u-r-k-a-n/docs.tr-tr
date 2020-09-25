---
title: 'Yöntem tabanlı sorgu söz dizimi örnekleri: sıralama (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: 635b7f6e498e27ef8ca2e133df639f1010184a93
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197878"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="ae373-102">Yöntem tabanlı sorgu söz dizimi örnekleri: sıralama (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="ae373-102">Method-Based Query Syntax Examples: Ordering (LINQ to DataSet)</span></span>

<span data-ttu-id="ae373-103">Bu konudaki örneklerde <xref:System.Linq.Enumerable.OrderBy%2A> ,,  <xref:System.Linq.Enumerable.Reverse%2A> ve <xref:System.Linq.Enumerable.ThenBy%2A> yöntemlerinin sorgu <xref:System.Data.DataSet> söz dizimini kullanarak sonuçları sıralamak için, ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ae373-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>,  <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenBy%2A> methods to query a <xref:System.Data.DataSet> and order the results using the method query syntax.</span></span>  
  
 <span data-ttu-id="ae373-104">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ae373-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="ae373-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ae373-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ae373-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="ae373-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="ae373-107">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ae373-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="ae373-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="ae373-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="ae373-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae373-109">Example</span></span>  

 <span data-ttu-id="ae373-110">Bu örnek, <xref:System.Linq.Enumerable.OrderBy%2A> son adları büyük/küçük harfe duyarsız bir sıralama yapmak için özel bir karşılaştırıcı ile yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae373-110">This example uses the <xref:System.Linq.Enumerable.OrderBy%2A> method with a custom comparer to do a case-insensitive sort of last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a><span data-ttu-id="ae373-111">Reverse</span><span class="sxs-lookup"><span data-stu-id="ae373-111">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="ae373-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae373-112">Example</span></span>  

 <span data-ttu-id="ae373-113">Bu örnek, <xref:System.Linq.Enumerable.Reverse%2A> `OrderDate` 20 Şubat 2002 ' den önceki bir siparişlerin listesini oluşturmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae373-113">This example uses the <xref:System.Linq.Enumerable.Reverse%2A> method to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a><span data-ttu-id="ae373-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="ae373-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="ae373-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae373-115">Example</span></span>  

 <span data-ttu-id="ae373-116">Bu örnekte <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.ThenBy%2A> , ilk olarak liste fiyatına göre sıralama yapmak için özel bir karşılaştırıcı ile Yöntemler ve ardından ürün adları büyük/küçük harf duyarsız azalan sıralaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="ae373-116">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.ThenBy%2A> methods with a custom comparer to first sort by list price, and then perform a case-insensitive descending sort of the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="ae373-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae373-117">See also</span></span>

- [<span data-ttu-id="ae373-118">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="ae373-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="ae373-119">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="ae373-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="ae373-120">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="ae373-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="ae373-121">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae373-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
