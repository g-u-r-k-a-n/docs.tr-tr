---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 3360ad4ca7306a8cc1b7d6948204f825ff9a93c6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203624"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="124de-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="124de-102">ISNULL (Entity SQL)</span></span>

<span data-ttu-id="124de-103">Sorgu ifadesinin null olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="124de-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="124de-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="124de-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="124de-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="124de-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="124de-106">Herhangi bir geçerli sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="124de-106">Any valid query expression.</span></span> <span data-ttu-id="124de-107">Koleksiyon, koleksiyon üyeleri veya koleksiyon türü özellikleri olan bir kayıt türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="124de-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="124de-108">NOT</span><span class="sxs-lookup"><span data-stu-id="124de-108">NOT</span></span>  
 <span data-ttu-id="124de-109">EDM 'yi geçersiz kılar. Boolean sonucu NULL.</span><span class="sxs-lookup"><span data-stu-id="124de-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="124de-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="124de-110">Return Value</span></span>  

 <span data-ttu-id="124de-111">`true` Eğer `expression` null döndürürse, tersi durumda `false` .</span><span class="sxs-lookup"><span data-stu-id="124de-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="124de-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="124de-112">Remarks</span></span>  

 <span data-ttu-id="124de-113">`IS NULL`Dış birleştirmenin öğesinin null olup olmadığını anlamak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="124de-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="124de-114">`IS NULL`Üyenin gerçek bir değere sahip olup olmadığını anlamak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="124de-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="124de-115">Aşağıdaki tabloda `IS NULL` bazı desenlerin üzerinde davranış gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="124de-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="124de-116">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="124de-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="124de-117">Desen</span><span class="sxs-lookup"><span data-stu-id="124de-117">Pattern</span></span>|<span data-ttu-id="124de-118">Davranış</span><span class="sxs-lookup"><span data-stu-id="124de-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="124de-119">NULL NULL</span><span class="sxs-lookup"><span data-stu-id="124de-119">null IS NULL</span></span>|<span data-ttu-id="124de-120">`true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="124de-120">Returns `true`.</span></span>|  
|<span data-ttu-id="124de-121">DAVRAN (EntityType olarak null) NULL</span><span class="sxs-lookup"><span data-stu-id="124de-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="124de-122">`true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="124de-122">Returns `true`.</span></span>|  
|<span data-ttu-id="124de-123">DAVRAN (ComplexType olarak null) NULL</span><span class="sxs-lookup"><span data-stu-id="124de-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="124de-124">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="124de-124">Throws an error.</span></span>|  
|<span data-ttu-id="124de-125">DEĞERLENDIRIN (RowType olarak null) NULL</span><span class="sxs-lookup"><span data-stu-id="124de-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="124de-126">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="124de-126">Throws an error.</span></span>|  
|<span data-ttu-id="124de-127">EntityType NULL</span><span class="sxs-lookup"><span data-stu-id="124de-127">EntityType IS NULL</span></span>|<span data-ttu-id="124de-128">`true`Veya döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="124de-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="124de-129">ComplexType NULL</span><span class="sxs-lookup"><span data-stu-id="124de-129">ComplexType IS NULL</span></span>|<span data-ttu-id="124de-130">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="124de-130">Throws an error.</span></span>|  
|<span data-ttu-id="124de-131">RowType NULL</span><span class="sxs-lookup"><span data-stu-id="124de-131">RowType IS NULL</span></span>|<span data-ttu-id="124de-132">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="124de-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="124de-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="124de-133">Example</span></span>  

 <span data-ttu-id="124de-134">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir sorgu ifadesinin null olmadığını anlamak IÇIN null olmayan bir işleç kullanır.</span><span class="sxs-lookup"><span data-stu-id="124de-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="124de-135">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="124de-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="124de-136">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="124de-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="124de-137">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="124de-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="124de-138">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="124de-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="124de-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="124de-139">See also</span></span>

- [<span data-ttu-id="124de-140">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="124de-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
