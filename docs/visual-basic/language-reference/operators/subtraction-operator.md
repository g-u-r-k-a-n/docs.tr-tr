---
title: '- Operatör'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 6539beb5cf8078281357445e2391fac189208087
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406360"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="71f32-102">- İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71f32-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="71f32-103">İki sayısal ifade arasındaki farkı ya da sayısal bir ifadenin negatif değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="71f32-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f32-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71f32-104">Syntax</span></span>  
  
```vb  
expression1 – expression2
```
  
<span data-ttu-id="71f32-105">veya</span><span class="sxs-lookup"><span data-stu-id="71f32-105">or</span></span>

```vb  
–expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="71f32-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="71f32-106">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="71f32-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="71f32-107">Required.</span></span> <span data-ttu-id="71f32-108">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="71f32-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="71f32-109">`–`İşleç negatif bir değer hesaplanmadığı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="71f32-109">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="71f32-110">Herhangi bir sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="71f32-110">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="71f32-111">Sonuç</span><span class="sxs-lookup"><span data-stu-id="71f32-111">Result</span></span>  
 <span data-ttu-id="71f32-112">Sonuç, `expression1` ile veya arasında bir değer arasındaki farktır `expression2` `expression1` .</span><span class="sxs-lookup"><span data-stu-id="71f32-112">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="71f32-113">Sonuç veri türü ve veri türleri için uygun bir sayısal türdür `expression1` `expression2` .</span><span class="sxs-lookup"><span data-stu-id="71f32-113">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="71f32-114">[Işleç sonuçlarının veri türlerinde](data-types-of-operator-results.md)"tamsayı aritmetiği" tablolarına bakın.</span><span class="sxs-lookup"><span data-stu-id="71f32-114">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="71f32-115">Desteklenen türler</span><span class="sxs-lookup"><span data-stu-id="71f32-115">Supported Types</span></span>  
 <span data-ttu-id="71f32-116">Tüm sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="71f32-116">All numeric types.</span></span> <span data-ttu-id="71f32-117">Bu, imzasız ve kayan nokta türlerini içerir `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="71f32-117">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71f32-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71f32-118">Remarks</span></span>  
 <span data-ttu-id="71f32-119">Daha önce gösterilen sözdiziminde gösterilen ilk kullanımlarda `–` işleç, iki sayısal ifade arasındaki fark için *ikili* aritmetik çıkarma işleçidir.</span><span class="sxs-lookup"><span data-stu-id="71f32-119">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="71f32-120">Daha önce gösterilen sözdiziminde gösterilen ikinci kullanımda `–` işleci, bir ifadenin negatif değeri için *birli* olumsuzlama işleçidir.</span><span class="sxs-lookup"><span data-stu-id="71f32-120">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="71f32-121">Bu anlamda olumsuzlama, negatif ise sonucun pozitif olması için işaretini tersine döndürdükten oluşur `expression1` `expression1` .</span><span class="sxs-lookup"><span data-stu-id="71f32-121">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="71f32-122">Her iki ifade de [Nothing](../nothing.md)olarak değerlendirilirse, `–` işleç onu sıfır olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="71f32-122">If either expression evaluates to [Nothing](../nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71f32-123">`–`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="71f32-123">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="71f32-124">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="71f32-124">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="71f32-125">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="71f32-125">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="71f32-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="71f32-126">Example</span></span>  
 <span data-ttu-id="71f32-127">Aşağıdaki örnek, `–` iki sayı arasındaki farkı hesaplamak ve döndürmek için işlecini ve sonra bir sayıyı bir sayı olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="71f32-127">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="71f32-128">Bu deyimlerin yürütülmesi sonrasında `binaryResult` 124,45 ve `unaryResult` içerir – 334,90 içerir.</span><span class="sxs-lookup"><span data-stu-id="71f32-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f32-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71f32-129">See also</span></span>

- [<span data-ttu-id="71f32-130">-= İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71f32-130">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="71f32-131">Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="71f32-131">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="71f32-132">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="71f32-132">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="71f32-133">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="71f32-133">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="71f32-134">Visual Basic'de Aritmetik İşleçler</span><span class="sxs-lookup"><span data-stu-id="71f32-134">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
