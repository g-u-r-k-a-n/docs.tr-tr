---
description: 'Daha fazla bilgi edinin: GROUPPARTITION (Entity SQL)'
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 18fdb655f62f54d59c03c0a34f6f77c5ca26729e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696912"
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="dab95-103">GROUPPARTITION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dab95-103">GROUPPARTITION (Entity SQL)</span></span>

<span data-ttu-id="dab95-104">Toplamanın ilgili olduğu geçerli grup bölümünün yansıtıldıkları bağımsız değişken değerlerinin bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="dab95-104">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="dab95-105">`GroupPartition`Toplama, grup tabanlı bir kümedir ve koleksiyon tabanlı bir form içermez.</span><span class="sxs-lookup"><span data-stu-id="dab95-105">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab95-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="dab95-106">Syntax</span></span>  
  
```sql  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="dab95-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="dab95-107">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="dab95-108">Herhangi bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ifade.</span><span class="sxs-lookup"><span data-stu-id="dab95-108">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dab95-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dab95-109">Remarks</span></span>  

 <span data-ttu-id="dab95-110">Aşağıdaki sorgu ürünlerin bir listesini ve her bir ürün için sipariş satırı miktarları koleksiyonunu üretir:</span><span class="sxs-lookup"><span data-stu-id="dab95-110">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="dab95-111">Aşağıdaki iki sorgu anlamsal olarak eşittir:</span><span class="sxs-lookup"><span data-stu-id="dab95-111">The following two queries are semantically equal:</span></span>  
  
```sql  
SELECT p, Sum(GroupPartition(ol.Quantity)) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
SELET p, Sum(ol.Quantity) FROM LOB.OrderLines AS ol
  group by ol.Product as p  
```  
  
 <span data-ttu-id="dab95-112">`GROUPPARTITION`İşleci, Kullanıcı tanımlı toplama işlevleriyle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dab95-112">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
<span data-ttu-id="dab95-113">`GROUPPARTITION` , gruplandırılmış giriş kümesine yönelik bir başvuruyu tutan özel bir toplam işleçtir.</span><span class="sxs-lookup"><span data-stu-id="dab95-113">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="dab95-114">Bu başvuru, GROUP BY Scope içinde olan sorguda herhangi bir yerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dab95-114">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="dab95-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="dab95-115">For example:</span></span>
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="dab95-116">Düzenli `GROUP BY` olarak, gruplandırmanın sonuçları gizlidir.</span><span class="sxs-lookup"><span data-stu-id="dab95-116">With a regular `GROUP BY`, the results of the grouping are hidden.</span></span> <span data-ttu-id="dab95-117">Sonuçları yalnızca bir toplama işlevinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dab95-117">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="dab95-118">Gruplandırmanın sonuçlarını görmek için gruplandırma sonuçlarını ve giriş kümesini bir alt sorgu kullanarak ilişkilendirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dab95-118">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="dab95-119">Aşağıdaki iki sorgu eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="dab95-119">The following two queries are equivalent:</span></span>  
  
```sql  
SELET p, (SELECT q FROM GroupPartition(ol.Quantity) AS q) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
SELECT p, (SELECT ol.Quantity AS q FROM LOB.OrderLines AS ol2 WHERE ol2.Product = p) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="dab95-120">Bu örnekte görüldüğü gibi, GROUPPARTITION toplama operatörü, gruplandırma işleminden sonra giriş kümesine bir başvuru almayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="dab95-120">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="dab95-121">GROUPPARTITION işleci, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] parametresini kullandığınızda işleç girişinde herhangi bir ifadeyi belirtebilir `expression` .</span><span class="sxs-lookup"><span data-stu-id="dab95-121">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="dab95-122">Örneğin, grup bölümüne aşağıdaki giriş ifadelerinin tümü geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="dab95-122">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```sql  
SELECT groupkey, GroupPartition(b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(1) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(a + b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition({a + b}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition({42}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition(b > a) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="dab95-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="dab95-123">Example</span></span>  

 <span data-ttu-id="dab95-124">Aşağıdaki örnek, GROUP BY yan tümcesi ile GROUPPARTITION yan tümcesinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="dab95-124">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="dab95-125">GROUP BY yan tümcesi `SalesOrderHeader` varlıkları kendilerine göre gruplandırır `Contact` .</span><span class="sxs-lookup"><span data-stu-id="dab95-125">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="dab95-126">GROUPPARTITION yan tümcesi daha sonra `TotalDue` her bir grup için özelliği projeler, bu da ondalık bir toplama sonucu oluşur.</span><span class="sxs-lookup"><span data-stu-id="dab95-126">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#Collection_GroupPartition](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#collection_grouppartition)]
