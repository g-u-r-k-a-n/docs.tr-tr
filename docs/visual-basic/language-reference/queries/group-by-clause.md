---
title: Group By Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: 87080254ad5d237a593f0c35e7c3fdaef3a8ad59
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350469"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="68fad-102">Group By Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68fad-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="68fad-103">Bir sorgu sonucunun öğelerini gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="68fad-103">Groups the elements of a query result.</span></span> <span data-ttu-id="68fad-104">, Her gruba toplam işlevleri uygulamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="68fad-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="68fad-105">Gruplandırma işlemi bir veya daha fazla anahtara göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="68fad-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68fad-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68fad-106">Syntax</span></span>  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="68fad-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="68fad-107">Parts</span></span>  
  
- <span data-ttu-id="68fad-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="68fad-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="68fad-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="68fad-109">Optional.</span></span> <span data-ttu-id="68fad-110">Gruplanmış sonuca dahil edilecek alanları açıkça tanımlayan sorgu değişkeninin veya değişkenlerinin bir veya daha fazla alanı.</span><span class="sxs-lookup"><span data-stu-id="68fad-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="68fad-111">Hiçbir alan belirtilmemişse, sorgu değişkeni veya değişkenlerinin tüm alanları gruplanmış sonuca dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="68fad-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="68fad-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="68fad-112">Required.</span></span> <span data-ttu-id="68fad-113">Öğe gruplarını belirlemekte kullanılacak anahtarı tanımlayan bir ifade.</span><span class="sxs-lookup"><span data-stu-id="68fad-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="68fad-114">Bileşik bir anahtar belirtmek için birden fazla anahtar belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68fad-114">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="68fad-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="68fad-115">Optional.</span></span> <span data-ttu-id="68fad-116">Bileşik anahtar oluşturmak için `keyExp1` birlikte birleştirilmiş bir veya daha fazla ek anahtar.</span><span class="sxs-lookup"><span data-stu-id="68fad-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="68fad-117">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="68fad-117">Required.</span></span> <span data-ttu-id="68fad-118">Grupların nasıl toplanacağına ilişkin bir veya daha fazla ifade.</span><span class="sxs-lookup"><span data-stu-id="68fad-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="68fad-119">Gruplanmış sonuçların üye adını belirlemek için, aşağıdaki biçimlerden birinde olabilecek `Group` anahtar sözcüğünü kullanın:</span><span class="sxs-lookup"><span data-stu-id="68fad-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```vb  
    Into Group  
    ```  
  
     <span data-ttu-id="68fad-120">veya</span><span class="sxs-lookup"><span data-stu-id="68fad-120">-or-</span></span>  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="68fad-121">Gruba uygulanacak toplama işlevlerini de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68fad-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68fad-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68fad-122">Remarks</span></span>  
 <span data-ttu-id="68fad-123">Bir sorgunun sonuçlarını gruplara bölmek için `Group By` yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68fad-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="68fad-124">Gruplandırma bir anahtara veya birden çok anahtardan oluşan bileşik anahtara göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="68fad-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="68fad-125">Eşleşen anahtar değerleriyle ilişkili öğeler aynı gruba dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="68fad-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="68fad-126">Gruba başvurmak için kullanılan üye adını belirlemek için `Into` yan tümcesinin `aggregateList` parametresini ve `Group` anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="68fad-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="68fad-127">Gruplanmış öğelerin değerlerini hesaplamak için `Into` yan tümcesine toplama işlevleri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68fad-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="68fad-128">Standart toplama işlevlerinin bir listesi için bkz. [Aggregate yan tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="68fad-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68fad-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="68fad-129">Example</span></span>  
 <span data-ttu-id="68fad-130">Aşağıdaki kod örneği, konumlarına (ülke/bölge) göre müşterilerin bir listesini gruplandırır ve her bir gruptaki müşterilerin sayısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="68fad-130">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span></span> <span data-ttu-id="68fad-131">Sonuçlar ülke/bölge adına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="68fad-131">The results are ordered by country/region name.</span></span> <span data-ttu-id="68fad-132">Gruplanmış sonuçlar şehir adına göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="68fad-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="68fad-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68fad-133">See also</span></span>

- [<span data-ttu-id="68fad-134">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="68fad-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="68fad-135">Sorgular</span><span class="sxs-lookup"><span data-stu-id="68fad-135">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="68fad-136">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="68fad-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="68fad-137">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="68fad-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="68fad-138">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="68fad-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="68fad-139">Aggregate Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="68fad-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="68fad-140">Group Join Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="68fad-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
