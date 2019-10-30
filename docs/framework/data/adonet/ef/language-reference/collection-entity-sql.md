---
title: KOLEKSIYON (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 5a1af1aab8a084b19e48fbdbb159d7ddd8a8dd7c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039903"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="14373-102">KOLEKSIYON (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="14373-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="14373-103">KOLEKSIYON anahtar sözcüğü yalnızca bir satır içi işlevin tanımında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="14373-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="14373-104">Koleksiyon işlevleri, bir değer koleksiyonunda çalışan ve skaler bir çıktı üreten işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="14373-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14373-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14373-105">Syntax</span></span>  
  
```csharp  
COLLECTION(type_definition)
```  
  
## <a name="arguments"></a><span data-ttu-id="14373-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="14373-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="14373-107">Desteklenen türlerin, satırların veya başvuruların koleksiyonunu döndüren bir ifade.</span><span class="sxs-lookup"><span data-stu-id="14373-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14373-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14373-108">Remarks</span></span>  
 <span data-ttu-id="14373-109">KOLEKSIYON anahtar sözcüğü hakkında daha fazla bilgi için bkz. [tür tanımları](type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="14373-109">For more information about the COLLECTION keyword, see [Type Definitions](type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="14373-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="14373-110">Example</span></span>  
 <span data-ttu-id="14373-111">Aşağıdaki örnek, bir satır içi sorgu işlevi için bir bağımsız değişken olarak bir ondalık toplamayı bildirmek üzere COLLECTION anahtar sözcüğünün nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="14373-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="14373-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14373-112">See also</span></span>

- [<span data-ttu-id="14373-113">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="14373-113">Entity SQL Reference</span></span>](entity-sql-reference.md)
