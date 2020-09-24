---
title: '! BAŞLATıLMADı (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 0eb9be9ed4cbce45a51d15eea68e9fb1a26f0107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191846"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="90fbd-103">!</span><span class="sxs-lookup"><span data-stu-id="90fbd-103">!</span></span> <span data-ttu-id="90fbd-104">BAŞLATıLMADı (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="90fbd-104">(NOT) (Entity SQL)</span></span>

<span data-ttu-id="90fbd-105">Bir ifadeyi geçersiz kılar `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="90fbd-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90fbd-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="90fbd-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a><span data-ttu-id="90fbd-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="90fbd-107">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="90fbd-108">Boolean döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="90fbd-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90fbd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90fbd-109">Remarks</span></span>  

 <span data-ttu-id="90fbd-110">Ünlem işareti (!), NOT işleci ile aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="90fbd-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90fbd-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="90fbd-111">Example</span></span>  

 <span data-ttu-id="90fbd-112">Aşağıdaki Entity SQL sorgusu, bir ifadeyi geçersiz hale getirir için NOT işlecini kullanır `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="90fbd-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="90fbd-113">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="90fbd-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="90fbd-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="90fbd-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="90fbd-115">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="90fbd-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="90fbd-116">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="90fbd-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="90fbd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90fbd-117">See also</span></span>

- [<span data-ttu-id="90fbd-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="90fbd-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
