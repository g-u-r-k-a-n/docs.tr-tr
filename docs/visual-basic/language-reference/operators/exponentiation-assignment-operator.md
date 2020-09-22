---
title: ^= İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: a956ffdaa3456ed09443f25c3383b6aab52fb5bf
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867056"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="ad91b-102">^= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad91b-102">^= Operator (Visual Basic)</span></span>

<span data-ttu-id="ad91b-103">Bir değişkenin veya özelliğin değerini bir ifadenin gücüne yükseltir ve sonucu değişkene veya özelliğe geri atar.</span><span class="sxs-lookup"><span data-stu-id="ad91b-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad91b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad91b-104">Syntax</span></span>  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ad91b-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ad91b-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="ad91b-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ad91b-106">Required.</span></span> <span data-ttu-id="ad91b-107">Herhangi bir sayısal değişken veya özellik.</span><span class="sxs-lookup"><span data-stu-id="ad91b-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="ad91b-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ad91b-108">Required.</span></span> <span data-ttu-id="ad91b-109">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="ad91b-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad91b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad91b-110">Remarks</span></span>  

 <span data-ttu-id="ad91b-111">İşlecinin sol tarafındaki öğesi `^=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad91b-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="ad91b-112">Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="ad91b-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="ad91b-113">`^=`İşleci ilk olarak, değişkenin veya özelliğin değerini (işlecin sol tarafında) ifadenin değerinin (işlecin sağ tarafında) kuvvetine yükseltir..</span><span class="sxs-lookup"><span data-stu-id="ad91b-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="ad91b-114">İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe geri atar.</span><span class="sxs-lookup"><span data-stu-id="ad91b-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="ad91b-115">Visual Basic her zaman [Double veri türünde](../data-types/double-data-type.md)üs gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ad91b-115">Visual Basic always performs exponentiation in the [Double Data Type](../data-types/double-data-type.md).</span></span> <span data-ttu-id="ad91b-116">Farklı türdeki işlenenler öğesine dönüştürülür `Double` ve sonuç her zaman olur `Double` .</span><span class="sxs-lookup"><span data-stu-id="ad91b-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="ad91b-117">Değeri `expression` kesirli, negatif veya her ikisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad91b-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ad91b-118">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="ad91b-118">Overloading</span></span>  

 <span data-ttu-id="ad91b-119">[^ İşleci](exponentiation-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ad91b-119">The [^ Operator](exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ad91b-120">İşleci aşırı yüklemek `^` işlecin davranışını etkiler `^=` .</span><span class="sxs-lookup"><span data-stu-id="ad91b-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="ad91b-121">Kodunuzun `^=` bir sınıf veya yapı üzerinde kullanması durumunda `^` , yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ad91b-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ad91b-122">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ad91b-122">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad91b-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad91b-123">Example</span></span>  

 <span data-ttu-id="ad91b-124">Aşağıdaki örnek, `^=` bir `Integer` değişkenin değerini ikinci bir değişkenin gücüne yükseltmek ve sonucu ilk değişkene atamak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ad91b-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="ad91b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad91b-125">See also</span></span>

- [<span data-ttu-id="ad91b-126">^ İşleci</span><span class="sxs-lookup"><span data-stu-id="ad91b-126">^ Operator</span></span>](exponentiation-operator.md)
- [<span data-ttu-id="ad91b-127">Atama Işleçleri</span><span class="sxs-lookup"><span data-stu-id="ad91b-127">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="ad91b-128">Aritmetik Işleçler</span><span class="sxs-lookup"><span data-stu-id="ad91b-128">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="ad91b-129">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="ad91b-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="ad91b-130">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="ad91b-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="ad91b-131">Deyimler</span><span class="sxs-lookup"><span data-stu-id="ad91b-131">Statements</span></span>](../../programming-guide/language-features/statements.md)
