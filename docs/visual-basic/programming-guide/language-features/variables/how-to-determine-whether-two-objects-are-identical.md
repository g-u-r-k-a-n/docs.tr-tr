---
title: 'Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 5deebd4ffc5b277c94f5ae36c00fd6e5010a1551
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348605"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="fbeb1-102">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Belirleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbeb1-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="fbeb1-103">Visual Basic, işaretçilerin aynısı varsa, iki değişken başvurusu özdeş kabul edilir, yani her iki değişken de bellekteki aynı sınıf örneğini işaret ediyor.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="fbeb1-104">Örneğin, Windows Forms bir uygulamada, geçerli örneğin (`Me`) `Form2`gibi belirli bir örnekle aynı olup olmadığını belirlemede bir karşılaştırma yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="fbeb1-105">Visual Basic işaretçileri karşılaştırmak için iki işleç sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="fbeb1-106">İf [işleci](../../../../visual-basic/language-reference/operators/is-operator.md) , nesneler aynıysa `True` döndürür ve [ınot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md) yoksa `True` döndürür.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="fbeb1-107">Iki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="fbeb1-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="fbeb1-108">İki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="fbeb1-108">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="fbeb1-109">İki nesneyi test etmek için bir `Boolean` ifadesi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="fbeb1-110">Test ifadenizde, iki nesne işlenen olarak `Is` işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="fbeb1-111">`Is`, nesneler aynı sınıf örneğine işaret ettikten sonra `True` döndürür.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="fbeb1-112">Iki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="fbeb1-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="fbeb1-113">Bazen iki nesne özdeş değilse bir eylem gerçekleştirmek istiyor ve bu, örneğin `If Not obj1 Is obj2``Not` ve `Is`birleştirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="fbeb1-114">Böyle bir durumda `IsNot` işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="fbeb1-115">İki nesnenin aynı olup olmadığını belirleme</span><span class="sxs-lookup"><span data-stu-id="fbeb1-115">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="fbeb1-116">İki nesneyi test etmek için bir `Boolean` ifadesi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="fbeb1-117">Test ifadenizde, iki nesne işlenen olarak `IsNot` işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="fbeb1-118">nesneler aynı sınıf örneğini işaret etmez `IsNot` `True` döndürür.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbeb1-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbeb1-119">Example</span></span>  
 <span data-ttu-id="fbeb1-120">Aşağıdaki örnek, aynı sınıf örneğine işaret edip ettikleri görmek için `Object` değişkenlerinin çiftlerini sınar.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="fbeb1-121">Yukarıdaki örnek aşağıdaki çıktıyı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="fbeb1-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbeb1-122">See also</span></span>

- [<span data-ttu-id="fbeb1-123">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="fbeb1-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="fbeb1-124">Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="fbeb1-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="fbeb1-125">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="fbeb1-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="fbeb1-126">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="fbeb1-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="fbeb1-127">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="fbeb1-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="fbeb1-128">Nasıl yapılır: İki Nesnenin İlgili Olup Olmadığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="fbeb1-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="fbeb1-129">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="fbeb1-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
