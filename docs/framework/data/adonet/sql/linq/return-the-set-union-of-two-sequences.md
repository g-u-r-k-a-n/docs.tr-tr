---
title: İki Dizinin Küme Birleşimini Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 0fe32d8c3c37e99a50ca03262dc6184337b4450e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200215"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="85cc4-102">İki Dizinin Küme Birleşimini Döndürme</span><span class="sxs-lookup"><span data-stu-id="85cc4-102">Return the Set Union of Two Sequences</span></span>

<span data-ttu-id="85cc4-103"><xref:System.Linq.Queryable.Union%2A>İki sıranın set birleşimini döndürmek için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="85cc4-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85cc4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="85cc4-104">Example</span></span>  

 <span data-ttu-id="85cc4-105">Bu örnek <xref:System.Linq.Queryable.Union%2A> , ya da içinde olan tüm ülkelerin/bölgelerin bir dizisini döndürmek için kullanır `Customers` `Employees` .</span><span class="sxs-lookup"><span data-stu-id="85cc4-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries/regions in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="85cc4-106">' De, işleç multisets 'ler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Queryable.Union%2A> için çoklu kümeler için TANıMLANıR ( [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) SQL 'de yan tümcesinin sonucu etkin değildir).</span><span class="sxs-lookup"><span data-stu-id="85cc4-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) clause in SQL).</span></span>

<span data-ttu-id="85cc4-107">Daha fazla bilgi ve örnek için bkz <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType> ..</span><span class="sxs-lookup"><span data-stu-id="85cc4-107">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="85cc4-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85cc4-108">See also</span></span>

- [<span data-ttu-id="85cc4-109">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="85cc4-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="85cc4-110">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="85cc4-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
