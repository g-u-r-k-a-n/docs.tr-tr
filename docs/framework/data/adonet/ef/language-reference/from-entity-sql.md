---
title: (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ff3e3048-0d5d-4502-ae5c-9187fcbd0514
ms.openlocfilehash: 2334a30009d6bef9544d2ca1e0ab923a7441d6f2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833825"
---
# <a name="from-entity-sql"></a><span data-ttu-id="4df5c-102">(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4df5c-102">FROM (Entity SQL)</span></span>
<span data-ttu-id="4df5c-103">[Select](select-entity-sql.md) deyimlerinde kullanılan koleksiyonu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-103">Specifies the collection used in [SELECT](select-entity-sql.md) statements.</span></span>

## <a name="syntax"></a><span data-ttu-id="4df5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4df5c-104">Syntax</span></span>

```sql
FROM expression [ ,...n ] AS C
```

## <a name="arguments"></a><span data-ttu-id="4df5c-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="4df5c-105">Arguments</span></span>

`expression` \
<span data-ttu-id="4df5c-106">`SELECT` deyiminde kaynak olarak kullanılacak bir koleksiyon veren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="4df5c-106">Any valid query expression that yields a collection to use as a source in a `SELECT` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="4df5c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4df5c-107">Remarks</span></span>

<span data-ttu-id="4df5c-108">`FROM` yan tümcesi bir veya daha fazla `FROM` yan tümce öğesinin virgülle ayrılmış listesidir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-108">A `FROM` clause is a comma-separated list of one or more `FROM` clause items.</span></span> <span data-ttu-id="4df5c-109">`FROM` yan tümcesi, bir `SELECT` deyimi için bir veya daha fazla kaynak belirtmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-109">The `FROM` clause can be used to specify one or more sources for a `SELECT` statement.</span></span> <span data-ttu-id="4df5c-110">Bir `FROM` yan tümcesinin en basit biçimi, aşağıdaki örnekte gösterildiği gibi bir koleksiyonu ve `SELECT` kaynak olarak kullanılan diğer adı tanımlayan tek bir sorgu deyimidir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-110">The simplest form of a `FROM` clause is a single query expression that identifies a collection and an alias used as the source in a `SELECT` statement, as illustrated in the following example:</span></span>

`FROM C as c`

## <a name="from-clause-items"></a><span data-ttu-id="4df5c-111">FROM yan tümce öğeleri</span><span class="sxs-lookup"><span data-stu-id="4df5c-111">FROM Clause Items</span></span>

<span data-ttu-id="4df5c-112">Her `FROM` yan tümce öğesi, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgusunda bir kaynak koleksiyonu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-112">Each `FROM` clause item refers to a source collection in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="4df5c-113">aşağıdaki `FROM` yan tümce öğelerinin sınıflarını destekler: basit `FROM` yan tümce öğeleri, `JOIN FROM` yan tümce öğeleri ve `APPLY FROM` yan tümce öğeleri.</span><span class="sxs-lookup"><span data-stu-id="4df5c-113">supports the following classes of `FROM` clause items: simple `FROM` clause items, `JOIN FROM` clause items, and `APPLY FROM` clause items.</span></span> <span data-ttu-id="4df5c-114">Bu `FROM` yan tümce öğelerinin her biri, aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-114">Each of these `FROM` clause items is described in more detail in the following sections.</span></span>

### <a name="simple-from-clause-item"></a><span data-ttu-id="4df5c-115">Basit FROM yan tümce öğesi</span><span class="sxs-lookup"><span data-stu-id="4df5c-115">Simple FROM Clause Item</span></span>

<span data-ttu-id="4df5c-116">En basit `FROM` yan tümce öğesi, bir koleksiyonu ve diğer adı tanımlayan tek bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-116">The simplest `FROM` clause item is a single expression that identifies a collection and an alias.</span></span> <span data-ttu-id="4df5c-117">İfade yalnızca bir varlık kümesi veya bir alt sorgu ya da bir koleksiyon türü olan başka bir ifade olabilir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-117">The expression can simply be an entity set, or a subquery, or any other expression that is a collection type.</span></span> <span data-ttu-id="4df5c-118">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-118">The following is an example:</span></span>

```sql
LOB.Customers as c
```

<span data-ttu-id="4df5c-119">Diğer ad belirtimi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-119">The alias specification is optional.</span></span> <span data-ttu-id="4df5c-120">Yukarıdaki from yan tümcesi öğesinin alternatif bir belirtimi şunlar olabilir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-120">An alternate specification of the above from clause item could be the following:</span></span>

```sql
LOB.Customers
```

<span data-ttu-id="4df5c-121">Diğer ad belirtilmemişse, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] koleksiyon ifadesini temel alan bir diğer ad oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-121">If no alias is specified, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias based on the collection expression.</span></span>

### <a name="join-from-clause-item"></a><span data-ttu-id="4df5c-122">Yan tümce öğesinden BIrLEŞTIr</span><span class="sxs-lookup"><span data-stu-id="4df5c-122">JOIN FROM Clause Item</span></span>

<span data-ttu-id="4df5c-123">`JOIN FROM` yan tümce öğesi iki `FROM` yan tümce öğesi arasında bir birleştirmeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4df5c-123">A `JOIN FROM` clause item represents a join between two `FROM` clause items.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="4df5c-124">çapraz birleştirmeleri, iç birleştirmeleri, sol ve sağ dış birleştirmeleri ve tam dış birleştirmeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="4df5c-124">supports cross joins, inner joins, left and right outer joins, and full outer joins.</span></span> <span data-ttu-id="4df5c-125">Tüm bu birleştirmeler Transact-SQL ' de desteklendikleri yönteme benzer şekilde desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-125">All these joins are supported similar to the way that they are supported in Transact-SQL.</span></span> <span data-ttu-id="4df5c-126">Transact-SQL ' de olduğu gibi, `JOIN` dahil olan iki `FROM` yan tümce öğesi bağımsız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-126">As in Transact-SQL, the two `FROM` clause items involved in the `JOIN` must be independent.</span></span> <span data-ttu-id="4df5c-127">Diğer bir deyişle, bağıntılı olamaz.</span><span class="sxs-lookup"><span data-stu-id="4df5c-127">That is, they cannot be correlated.</span></span> <span data-ttu-id="4df5c-128">Bu durumlar için bir `CROSS APPLY` veya `OUTER APPLY` kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-128">A `CROSS APPLY` or `OUTER APPLY` can be used for these cases.</span></span>

#### <a name="cross-joins"></a><span data-ttu-id="4df5c-129">Çapraz birleşimler</span><span class="sxs-lookup"><span data-stu-id="4df5c-129">Cross Joins</span></span>

<span data-ttu-id="4df5c-130">`CROSS JOIN` bir sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyonun Kartezyen çarpımını üretir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-130">A `CROSS JOIN` query expression produces the Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c CROSS JOIN D as d`

#### <a name="inner-joins"></a><span data-ttu-id="4df5c-131">İç Birleşimler</span><span class="sxs-lookup"><span data-stu-id="4df5c-131">Inner Joins</span></span>

<span data-ttu-id="4df5c-132">`INNER JOIN`, aşağıdaki örnekte gösterildiği gibi iki koleksiyonun kısıtlı bir Kartezyen çarpımını üretir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-132">An `INNER JOIN` produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c [INNER] JOIN D AS d ON e`

<span data-ttu-id="4df5c-133">Önceki sorgu ifadesi, sol taraftaki koleksiyonun her öğesinin bir bileşimini, `ON` koşulun doğru olduğu, sağ taraftaki koleksiyonun her öğesine karşı işler.</span><span class="sxs-lookup"><span data-stu-id="4df5c-133">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="4df5c-134">`ON` koşul belirtilmemişse, bir `INNER JOIN` `CROSS JOIN`kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-134">If no `ON` condition is specified, an `INNER JOIN` degenerates to a `CROSS JOIN`.</span></span>

#### <a name="left-outer-joins-and-right-outer-joins"></a><span data-ttu-id="4df5c-135">Sol dış birleşimler ve sağ dış birleşimler</span><span class="sxs-lookup"><span data-stu-id="4df5c-135">Left Outer Joins and Right Outer Joins</span></span>

<span data-ttu-id="4df5c-136">`OUTER JOIN` bir sorgu ifadesi, aşağıdaki örnekte gösterildiği gibi iki koleksiyonun kısıtlı bir Kartezyen çarpımını üretir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-136">An `OUTER JOIN` query expression produces a constrained Cartesian product of the two collections, as illustrated in the following example:</span></span>

`FROM C AS c LEFT OUTER JOIN D AS d ON e`

<span data-ttu-id="4df5c-137">Önceki sorgu ifadesi, sol taraftaki koleksiyonun her öğesinin bir bileşimini, `ON` koşulun doğru olduğu, sağ taraftaki koleksiyonun her öğesine karşı işler.</span><span class="sxs-lookup"><span data-stu-id="4df5c-137">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="4df5c-138">`ON` koşulu false ise, ifade, sol taraftaki öğenin tek bir örneğini, null değeri ile sağ taraftaki öğeye karşı işler.</span><span class="sxs-lookup"><span data-stu-id="4df5c-138">If the `ON` condition is false, the expression still processes a single instance of the element on the left paired against the element on the right, with the value null.</span></span>

<span data-ttu-id="4df5c-139">`RIGHT OUTER JOIN` benzer bir şekilde ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-139">A `RIGHT OUTER JOIN` may be expressed in a similar manner.</span></span>

#### <a name="full-outer-joins"></a><span data-ttu-id="4df5c-140">Tam dış birleşimler</span><span class="sxs-lookup"><span data-stu-id="4df5c-140">Full Outer Joins</span></span>

<span data-ttu-id="4df5c-141">Açık bir `FULL OUTER JOIN`, aşağıdaki örnekte gösterildiği gibi iki koleksiyonun kısıtlı bir Kartezyen çarpımını üretir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-141">An explicit `FULL OUTER JOIN` produces a constrained Cartesian product of the two collections as illustrated in the following example:</span></span>

`FROM C AS c FULL OUTER JOIN D AS d ON e`

<span data-ttu-id="4df5c-142">Önceki sorgu ifadesi, sol taraftaki koleksiyonun her öğesinin bir bileşimini, `ON` koşulun doğru olduğu, sağ taraftaki koleksiyonun her öğesine karşı işler.</span><span class="sxs-lookup"><span data-stu-id="4df5c-142">The previous query expression processes a combination of every element of the collection on the left paired against every element of the collection on the right, where the `ON` condition is true.</span></span> <span data-ttu-id="4df5c-143">`ON` koşulu false ise, ifade, sol taraftaki öğenin bir örneğini, null değeri ile sağ taraftaki öğeye karşı işler.</span><span class="sxs-lookup"><span data-stu-id="4df5c-143">If the `ON` condition is false, the expression still processes one instance of the element on the left paired against the element on the right, with the value null.</span></span> <span data-ttu-id="4df5c-144">Ayrıca, sol taraftaki öğenin bir örneğini solda, null değeriyle birlikte işler.</span><span class="sxs-lookup"><span data-stu-id="4df5c-144">It also processes one instance of the element on the right paired against the element on the left, with the value null.</span></span>

> [!NOTE]
> <span data-ttu-id="4df5c-145">SQL-92 ile uyumluluğu korumak için Transact-SQL içinde DıŞTAKI anahtar sözcüğü isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-145">To preserve compatibility with SQL-92, in Transact-SQL the OUTER keyword is optional.</span></span> <span data-ttu-id="4df5c-146">Bu nedenle, `LEFT JOIN`, `RIGHT JOIN`ve `FULL JOIN` `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`ve `FULL OUTER JOIN`için eş anlamlılardır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-146">Therefore, `LEFT JOIN`, `RIGHT JOIN`, and `FULL JOIN` are synonyms for `LEFT OUTER JOIN`, `RIGHT OUTER JOIN`, and `FULL OUTER JOIN`.</span></span>

### <a name="apply-clause-item"></a><span data-ttu-id="4df5c-147">APPLY yan tümce öğesi</span><span class="sxs-lookup"><span data-stu-id="4df5c-147">APPLY Clause Item</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="4df5c-148">iki tür `APPLY`destekler: `CROSS APPLY` ve `OUTER APPLY`.</span><span class="sxs-lookup"><span data-stu-id="4df5c-148">supports two kinds of `APPLY`: `CROSS APPLY` and `OUTER APPLY`.</span></span>

<span data-ttu-id="4df5c-149">`CROSS APPLY`, sağ taraftaki ifade hesaplanarak oluşturulan koleksiyonun bir öğesi ile sol taraftaki koleksiyonun her bir öğesi için benzersiz bir eşleştirme üretir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-149">A `CROSS APPLY` produces a unique pairing of each element of the collection on the left with an element of the collection produced by evaluating the expression on the right.</span></span> <span data-ttu-id="4df5c-150">`CROSS APPLY`, sağdaki ifade, aşağıdaki ilişkili koleksiyon örneğinde gösterildiği gibi, sol taraftaki öğe üzerinde işlevsel olarak değişir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-150">With a `CROSS APPLY`, the expression on the right is functionally dependent on the element on the left, as illustrated in the following associated collection example:</span></span>

`SELECT c, f FROM C AS c CROSS APPLY c.Assoc AS f`

<span data-ttu-id="4df5c-151">`CROSS APPLY` davranışı, JOIN listesine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-151">The behavior of `CROSS APPLY` is similar to the join list.</span></span> <span data-ttu-id="4df5c-152">Sağdaki ifade boş bir koleksiyon olarak değerlendirilirse, `CROSS APPLY` sol taraftaki öğenin bu örneği için bir eşleşme üretmez.</span><span class="sxs-lookup"><span data-stu-id="4df5c-152">If the expression on the right evaluates to an empty collection, the `CROSS APPLY` produces no pairings for that instance of the element on the left.</span></span>

<span data-ttu-id="4df5c-153">Bir `OUTER APPLY` `CROSS APPLY`benzer, çünkü sağdaki ifade boş bir koleksiyon olarak değerlendirilse bile bir eşleştirme yine de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4df5c-153">An `OUTER APPLY` resembles a `CROSS APPLY`, except a pairing is still produced even when the expression on the right evaluates to an empty collection.</span></span> <span data-ttu-id="4df5c-154">Aşağıda bir `OUTER APPLY`örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-154">The following is an example of an `OUTER APPLY`:</span></span>

`SELECT c, f FROM C AS c OUTER APPLY c.Assoc AS f`

> [!NOTE]
> <span data-ttu-id="4df5c-155">Transact-SQL ' den farklı olarak, [!INCLUDE[esql](../../../../../../includes/esql-md.md)]açık iç içe geçme bir adım gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4df5c-155">Unlike in Transact-SQL, there is no need for an explicit unnest step in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

> [!NOTE]
> <span data-ttu-id="4df5c-156">`CROSS` ve `OUTER APPLY` işleçleri SQL Server 2005 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="4df5c-156">`CROSS` and `OUTER APPLY` operators were introduced in SQL Server 2005.</span></span> <span data-ttu-id="4df5c-157">Bazı durumlarda sorgu işlem hattı, `CROSS APPLY` ve/veya `OUTER APPLY` işleçlerini içeren Transact-SQL üretebilir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-157">In some cases, the query pipeline might produce Transact-SQL that contains `CROSS APPLY` and/or `OUTER APPLY` operators.</span></span> <span data-ttu-id="4df5c-158">SQL Server 2005 ' den önceki SQL Server sürümleri de dahil olmak üzere bazı arka uç sağlayıcılar bu işleçleri desteklemediğinden, bu arka uç sağlayıcılarında bu sorgular yürütülemez.</span><span class="sxs-lookup"><span data-stu-id="4df5c-158">Because some backend providers, including versions of SQL Server earlier than SQL Server 2005, do not support these operators, such queries cannot be executed on these backend providers.</span></span>
>
> <span data-ttu-id="4df5c-159">Çıktı sorgusunda `CROSS APPLY` ve/veya `OUTER APPLY` işleçlerinin varlığına neden olabilecek bazı tipik senaryolar şunlardır: sayfalama ile bağıntılı bir alt sorgu; Bağıntılı bir alt sorgu üzerinden veya gezinti tarafından oluşturulan bir koleksiyon üzerinden AnyElement; Öğe seçiciyi kabul eden gruplandırma yöntemlerini kullanan LINQ sorguları; `CROSS APPLY` veya `OUTER APPLY` açıkça belirtildiği bir sorgu; `REF` yapısı üzerinde `DEREF` yapısına sahip bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="4df5c-159">Some typical scenarios that might lead to the presence of `CROSS APPLY` and/or `OUTER APPLY` operators in the output query are the following: a correlated subquery with paging; AnyElement over a correlated subquery or over a collection produced by navigation; LINQ queries that use grouping methods that accept an element selector; a query in which a `CROSS APPLY` or an `OUTER APPLY` are explicitly specified; a query that has a `DEREF` construct over a `REF` construct.</span></span>

## <a name="multiple-collections-in-the-from-clause"></a><span data-ttu-id="4df5c-160">FROM yan tümcesinde birden çok koleksiyon</span><span class="sxs-lookup"><span data-stu-id="4df5c-160">Multiple Collections in the FROM Clause</span></span>

<span data-ttu-id="4df5c-161">`FROM` yan tümcesi, virgülle ayrılmış birden fazla koleksiyon içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-161">The `FROM` clause can contain more than one collection separated by commas.</span></span> <span data-ttu-id="4df5c-162">Bu durumlarda, koleksiyonların birlikte birleştirilme varsayılır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-162">In these cases, the collections are assumed to be joined together.</span></span> <span data-ttu-id="4df5c-163">Bunları n yönlü bir çapraz JOIN olarak düşünün.</span><span class="sxs-lookup"><span data-stu-id="4df5c-163">Think of these as an n-way CROSS JOIN.</span></span>

<span data-ttu-id="4df5c-164">Aşağıdaki örnekte, `C` ve `D` bağımsız koleksiyonlardır, ancak `c.Names` `C`bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-164">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`.</span></span>

```sql
FROM C AS c, D AS d, c.Names AS e
```

<span data-ttu-id="4df5c-165">Önceki örnek, aşağıdaki örneğe mantıksal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-165">The previous example is logically equivalent to the following example:</span></span>

`FROM (C AS c JOIN D AS d) CROSS APPLY c.Names AS e`

## <a name="left-correlation"></a><span data-ttu-id="4df5c-166">Sol bağıntı</span><span class="sxs-lookup"><span data-stu-id="4df5c-166">Left Correlation</span></span>
 <span data-ttu-id="4df5c-167">`FROM` yan tümcesindeki öğeler, önceki yan tümcelerde belirtilen öğelere başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-167">Items in the `FROM` clause can refer to items specified in earlier clauses.</span></span> <span data-ttu-id="4df5c-168">Aşağıdaki örnekte, `C` ve `D` bağımsız koleksiyonlardır, ancak `c.Names` `C`bağımlıdır:</span><span class="sxs-lookup"><span data-stu-id="4df5c-168">In the following example, `C` and `D` are independent collections, but `c.Names` is dependent on `C`:</span></span>

```sql
from C as c, D as d, c.Names as e
```

<span data-ttu-id="4df5c-169">Bu, mantıksal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-169">This is logically equivalent to:</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

## <a name="semantics"></a><span data-ttu-id="4df5c-170">İçeriyor</span><span class="sxs-lookup"><span data-stu-id="4df5c-170">Semantics</span></span>

<span data-ttu-id="4df5c-171">Mantıksal olarak, `FROM` yan tümcesindeki koleksiyonlar, bir `n`yönlü çapraz birleştirmenin parçası olduğu varsayılır (1 yönlü çapraz birleşimin olması dışında).</span><span class="sxs-lookup"><span data-stu-id="4df5c-171">Logically, the collections in the `FROM` clause are assumed to be part of an `n`-way cross join (except in the case of a 1-way cross join).</span></span> <span data-ttu-id="4df5c-172">`FROM` yan tümcesindeki diğer adlar soldan sağa işlenir ve daha sonra başvurmak üzere geçerli kapsama eklenir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-172">Aliases in the `FROM` clause are processed left to right, and are added to the current scope for later reference.</span></span> <span data-ttu-id="4df5c-173">`FROM` yan tümcesi, birden çok satır kümesi üreten varsayılır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-173">The `FROM` clause is assumed to produce a multiset of rows.</span></span> <span data-ttu-id="4df5c-174">Bu koleksiyon öğesinden tek bir öğeyi temsil eden `FROM` yan tümcesindeki her öğe için bir alan olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-174">There will be one field for each item in the `FROM` clause that represents a single element from that collection item.</span></span>

<span data-ttu-id="4df5c-175">`FROM` yan tümcesi, c, d ve e alanlarının `C`, `D`ve `c.Names`öğe türünde olduğu kabul edildiği satır türünde satırları (c, d, e) mantıksal olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4df5c-175">The `FROM` clause logically produces a multiset of rows of type Row(c, d, e) where fields c, d, and e are assumed to be of the element type of `C`, `D`, and `c.Names`.</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="4df5c-176">kapsamdaki her bir basit `FROM` yan tümce öğesi için bir diğer ad tanıtır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-176">introduces an alias for each simple `FROM` clause item in scope.</span></span> <span data-ttu-id="4df5c-177">Örneğin, aşağıdaki FROM yan tümcesi kod parçacığında, kapsamında tanıtılan adlar c, d ve e 'dir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-177">For example, in the following FROM clause snippet, The names introduced into scope are c, d, and e.</span></span>

```sql
from (C as c join D as d) cross apply c.Names as e
```

<span data-ttu-id="4df5c-178">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] (Transact-SQL ' den farklı olarak), `FROM` yan tümcesi yalnızca kapsamdaki diğer adları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="4df5c-178">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (unlike Transact-SQL), the `FROM` clause only introduces the aliases into scope.</span></span> <span data-ttu-id="4df5c-179">Bu koleksiyonların sütunlarına (Özellikler) yapılan tüm başvurular diğer adla nitelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="4df5c-179">Any references to columns (properties) of these collections must be qualified with the alias.</span></span>

## <a name="pulling-up-keys-from-nested-queries"></a><span data-ttu-id="4df5c-180">Iç Içe sorgulardan anahtarları çekme</span><span class="sxs-lookup"><span data-stu-id="4df5c-180">Pulling Up Keys from Nested Queries</span></span>

<span data-ttu-id="4df5c-181">İç içe bir sorgudan anahtar çekmesini gerektiren bazı sorgu türleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4df5c-181">Certain types of queries that require pulling up keys from a nested query are not supported.</span></span> <span data-ttu-id="4df5c-182">Örneğin, aşağıdaki sorgu geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-182">For example, the following query is valid:</span></span>

```sql
select c.Orders from Customers as c
```

<span data-ttu-id="4df5c-183">Ancak, iç içe sorgu herhangi bir anahtara sahip olmadığından aşağıdaki sorgu geçerli değildir:</span><span class="sxs-lookup"><span data-stu-id="4df5c-183">However, the following query is not valid, because the nested query does not have any keys:</span></span>

```sql
select {1} from {2, 3}
```

## <a name="see-also"></a><span data-ttu-id="4df5c-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4df5c-184">See also</span></span>

- [<span data-ttu-id="4df5c-185">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4df5c-185">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="4df5c-186">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="4df5c-186">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="4df5c-187">Null Değer Atanabilir Yapılandırılmış Türler</span><span class="sxs-lookup"><span data-stu-id="4df5c-187">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
