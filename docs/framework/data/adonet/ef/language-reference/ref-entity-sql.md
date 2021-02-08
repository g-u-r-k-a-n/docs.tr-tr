---
description: 'Daha fazla bilgi edinin: REF (Entity SQL)'
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 05f87ce8027e8e095722eb13d39f3f13d56f6faa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802066"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="e7e9d-103">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e7e9d-103">REF (Entity SQL)</span></span>

<span data-ttu-id="e7e9d-104">Bir varlık örneğine bir başvuru döndürür.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-104">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7e9d-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e7e9d-105">Syntax</span></span>  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a><span data-ttu-id="e7e9d-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="e7e9d-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="e7e9d-107">Bir varlık türünün örneğini veren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-107">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7e9d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e7e9d-108">Return Value</span></span>  

 <span data-ttu-id="e7e9d-109">Belirtilen varlık örneğine bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-109">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7e9d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7e9d-110">Remarks</span></span>  

 <span data-ttu-id="e7e9d-111">Bir varlık başvurusu, Varlık anahtarından ve bir varlık kümesi adından oluşur.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-111">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="e7e9d-112">Farklı varlık kümeleri aynı varlık türünü temel alan için, belirli bir varlık anahtarı birden fazla varlık kümesinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-112">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="e7e9d-113">Ancak, bir varlık başvurusu her zaman benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-113">However, an entity reference is always unique.</span></span> <span data-ttu-id="e7e9d-114">Giriş ifadesi kalıcı bir varlığı temsil ediyorsa, bu varlığa yönelik bir başvuru döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-114">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="e7e9d-115">Giriş ifadesi kalıcı olmayan bir varlık değilse, null bir başvuru döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-115">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="e7e9d-116">Özellik ayıklama işleci (.) bir varlığın bir özelliğine erişmek için kullanılırsa, başvuru otomatik olarak başvuru yapılır.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-116">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7e9d-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7e9d-117">Example</span></span>  

 <span data-ttu-id="e7e9d-118">Aşağıdaki Entity SQL sorgusu, bir giriş varlığı bağımsız değişkeninin başvurusunu döndürmek için REF işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-118">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="e7e9d-119">Ürün varlığının bir özelliğine erişmek için bir özellik ayıklama işlemi (.) kullandığından aynı sorgu başvurunun başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-119">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="e7e9d-120">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e7e9d-121">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="e7e9d-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e7e9d-122">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-122">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="e7e9d-123">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="e7e9d-123">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="e7e9d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7e9d-124">See also</span></span>

- [<span data-ttu-id="e7e9d-125">DEREF</span><span class="sxs-lookup"><span data-stu-id="e7e9d-125">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="e7e9d-126">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="e7e9d-126">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="e7e9d-127">ANAHTAR</span><span class="sxs-lookup"><span data-stu-id="e7e9d-127">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="e7e9d-128">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e7e9d-128">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="e7e9d-129">Tür Tanımları</span><span class="sxs-lookup"><span data-stu-id="e7e9d-129">Type Definitions</span></span>](type-definitions-entity-sql.md)
