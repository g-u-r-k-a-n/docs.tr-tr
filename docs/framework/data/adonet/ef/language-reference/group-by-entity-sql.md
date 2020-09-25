---
title: Gruplandırma ölçütü (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 281d5d2df389f0952f0552747fa12b67b14d470c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204495"
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="7f14c-102">Gruplandırma ölçütü (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7f14c-102">GROUP BY (Entity SQL)</span></span>

<span data-ttu-id="7f14c-103">Sorgu ([Select](select-entity-sql.md)) ifadesi tarafından döndürülen nesnelerin yerleştirileceği grupları belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f14c-103">Specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f14c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7f14c-104">Syntax</span></span>  
  
```sql  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7f14c-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="7f14c-105">Arguments</span></span>  

 `aliasedExpression`  
 <span data-ttu-id="7f14c-106">Gruplandırmada uygulanan geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="7f14c-106">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="7f14c-107">`expression` FROM yan tümcesi tarafından döndürülen bir özelliğe başvuran bir özellik veya toplama olmayan bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f14c-107">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="7f14c-108">GROUP BY yan tümcesindeki her bir ifade, eşitlik için karşılaştırılabileceğiniz bir tür olarak değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7f14c-108">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="7f14c-109">Bu türler genellikle sayılar, dizeler ve tarihler gibi skaler temel öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="7f14c-109">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="7f14c-110">Bir koleksiyona göre gruplandırma yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="7f14c-110">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f14c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f14c-111">Remarks</span></span>  

 <span data-ttu-id="7f14c-112">Toplama işlevleri SELECT yan tümcesine dahil edilip \<select list> , group by her grup için bir Özet değeri hesaplar.</span><span class="sxs-lookup"><span data-stu-id="7f14c-112">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="7f14c-113">GROUP BY belirtildiğinde, select listesindeki toplama olmayan bir ifadedeki her bir özellik adı, gruplama ölçütü listesine dahil edilmelidir, ya da GROUP BY ifadesi Select List ifadesiyle tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7f14c-113">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f14c-114">ORDER BY yan tümcesi belirtilmemişse GROUP BY yan tümcesinin döndürdüğü gruplar belirli bir sırada değildir.</span><span class="sxs-lookup"><span data-stu-id="7f14c-114">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="7f14c-115">Verilerin belirli bir sıralamasını belirtmek için ORDER BY yan tümcesini her zaman kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="7f14c-115">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="7f14c-116">GROUP BY yan tümcesi belirtildiğinde, açıkça veya örtük olarak (örneğin, sorgudaki HAVING yan tümcesi tarafından), geçerli kapsam gizlidir ve yeni bir kapsam ortaya çıkartılır.</span><span class="sxs-lookup"><span data-stu-id="7f14c-116">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="7f14c-117">SELECT yan tümcesi, HAVING yan tümcesi ve ORDER BY yan tümcesi artık FROM yan tümcesinde belirtilen öğe adlarına başvuramayacak.</span><span class="sxs-lookup"><span data-stu-id="7f14c-117">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="7f14c-118">Yalnızca gruplandırma ifadelerine başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f14c-118">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="7f14c-119">Bunu yapmak için, her gruplama ifadesine yeni adlar (diğer adlar) atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f14c-119">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="7f14c-120">Gruplandırma ifadesi için bir diğer ad belirtilmemişse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Aşağıdaki örnekte gösterildiği gibi diğer ad oluşturma kurallarını kullanarak bir tane oluşturmayı dener.</span><span class="sxs-lookup"><span data-stu-id="7f14c-120">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="7f14c-121">GROUP BY yan tümcesindeki ifadeler, aynı GROUP BY yan tümcesinde daha önce tanımlanan adlara başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="7f14c-121">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="7f14c-122">Adları gruplandırma konusuna ek olarak, SELECT yan tümcesinde, HAVING yan tümcesinde ve ORDER BY yan tümcesinde toplamaları de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f14c-122">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="7f14c-123">Bir toplama, grubun her öğesi için değerlendirilen bir ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="7f14c-123">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="7f14c-124">Toplam işleci, tüm bu ifadelerin değerlerini azaltır (genellikle, ancak her zaman tek bir değere değildir).</span><span class="sxs-lookup"><span data-stu-id="7f14c-124">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="7f14c-125">Toplama ifadesi, üst kapsamda görünen özgün öğe adlarına veya GROUP BY yan tümcesinin kendisi tarafından tanıtılan yeni adlara başvuru yapabilir.</span><span class="sxs-lookup"><span data-stu-id="7f14c-125">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="7f14c-126">Toplamaların SELECT yan tümcesinde, HAVING yan tümcesinde ve ORDER BY yan tümcesinde görünmesine karşın, bu değerler, aşağıdaki örnekte gösterildiği gibi gruplama ifadeleri ile aynı kapsam altında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7f14c-126">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="7f14c-127">Bu sorgu, ürüne göre bölünmüş, sipariş edilen tüm ürünlerin maliyetinin bir raporunu oluşturmak için GROUP BY yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f14c-127">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="7f14c-128">`name`Gruplandırma ifadesinin parçası olarak ürüne adı verir ve ardından seçim listesinde bu ada başvurur.</span><span class="sxs-lookup"><span data-stu-id="7f14c-128">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="7f14c-129">Ayrıca, `sum` Select listesindeki toplamı, dahili olarak sipariş satırının fiyatına ve miktarına da belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f14c-129">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="7f14c-130">Her bir GROUP BY anahtar ifadesine giriş kapsamına en az bir başvuru olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="7f14c-130">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```sql  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="7f14c-131">GROUP BY kullanımına ilişkin bir örnek için bkz. [HAVING](having-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="7f14c-131">For an example of using GROUP BY, see [HAVING](having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f14c-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f14c-132">Example</span></span>  

 <span data-ttu-id="7f14c-133">Aşağıdaki Entity SQL sorgusu, nesneleri bir sorgu tarafından döndürülen grupları belirtmek için GROUP BY işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f14c-133">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="7f14c-134">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="7f14c-134">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7f14c-135">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="7f14c-135">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7f14c-136">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="7f14c-136">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="7f14c-137">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="7f14c-137">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GROUPBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="7f14c-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f14c-138">See also</span></span>

- [<span data-ttu-id="7f14c-139">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7f14c-139">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="7f14c-140">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="7f14c-140">Query Expressions</span></span>](query-expressions-entity-sql.md)
