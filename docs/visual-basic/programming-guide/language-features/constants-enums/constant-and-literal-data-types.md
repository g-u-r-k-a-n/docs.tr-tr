---
description: 'Daha fazla bilgi edinin: sabit ve değişmez değerli veri türleri (Visual Basic)'
title: Sabit ve Değişmez Değerli Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: e750b1e5746f935c7878e186d064060d0fa055dc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475441"
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="5a12c-103">Sabit ve Değişmez Değerli Veri Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a12c-103">Constant and Literal Data Types (Visual Basic)</span></span>

<span data-ttu-id="5a12c-104">Değişmez değer, değişkenin değeri veya "Hello" dizesi gibi bir ifadenin sonucu yerine kendisini ifade eden bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="5a12c-104">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="5a12c-105">Sabit, bir sabit değerin yerini alan anlamlı bir addır ve değer değişebilir bir değişkenin aksine, bu değeri program genelinde tutar.</span><span class="sxs-lookup"><span data-stu-id="5a12c-105">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="5a12c-106">[Option Infer](../../../language-reference/statements/option-infer-statement.md) `Off` ve [Option Strict](../../../language-reference/statements/option-strict-statement.md) olduğunda `On` , tüm sabitleri açıkça bir veri türüyle bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5a12c-106">When [Option Infer](../../../language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="5a12c-107">Aşağıdaki örnekte, veri türü `MyByte` açıkça veri türü olarak bildirilmiştir `Byte` :</span><span class="sxs-lookup"><span data-stu-id="5a12c-107">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 <span data-ttu-id="5a12c-108">`Option Infer`Veya olduğunda `On` `Option Strict` `Off` , yan tümcesiyle bir veri türü belirtmeden bir sabit bildirebilirsiniz `As` .</span><span class="sxs-lookup"><span data-stu-id="5a12c-108">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="5a12c-109">Derleyici, ifadenin türünden sabit türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="5a12c-109">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="5a12c-110">Sayısal tamsayı sabit değeri varsayılan olarak `Integer` veri türüne ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5a12c-110">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="5a12c-111">Kayan nokta numaraları için varsayılan veri türü `Double` ve anahtar sözcükler `True` ve `False` bir `Boolean` sabit belirtin.</span><span class="sxs-lookup"><span data-stu-id="5a12c-111">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="5a12c-112">Değişmez değerler ve tür zorlaması</span><span class="sxs-lookup"><span data-stu-id="5a12c-112">Literals and Type Coercion</span></span>  

 <span data-ttu-id="5a12c-113">Bazı durumlarda, bir sabit değeri belirli bir veri türüne zorlamak isteyebilirsiniz; Örneğin, tür değişkenine özellikle büyük bir integral sabit değer atama yaparken `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="5a12c-113">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="5a12c-114">Aşağıdaki örnek bir hata üretir:</span><span class="sxs-lookup"><span data-stu-id="5a12c-114">The following example produces an error:</span></span>  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="5a12c-115">Hata, sabit değerinin gösteriminden kaynaklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5a12c-115">The error results from the representation of the literal.</span></span> <span data-ttu-id="5a12c-116">`Decimal`Veri türü bu büyüklükte bir değer tutabilir, ancak değişmez değer örtülü olarak bir olarak temsil edilir, ancak `Long` .</span><span class="sxs-lookup"><span data-stu-id="5a12c-116">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="5a12c-117">Bir sabit değeri, belirli bir veri türüne iki şekilde dönüştürebilirsiniz: buna bir tür karakteri ekleyerek veya kapsayan karakterlerin içine yerleştirerek.</span><span class="sxs-lookup"><span data-stu-id="5a12c-117">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="5a12c-118">Bir tür karakteri veya kapsayan karakterler, hiçbir türden boşluk veya karakter olmadan hemen önce ve/veya sabit değer içermelidir.</span><span class="sxs-lookup"><span data-stu-id="5a12c-118">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="5a12c-119">Önceki örneğin çalışmasını sağlamak için, `D` tür karakterini değişmez değere ekleyebilirsiniz, bu, şöyle temsil edilmesine neden olur `Decimal` :</span><span class="sxs-lookup"><span data-stu-id="5a12c-119">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 <span data-ttu-id="5a12c-120">Aşağıdaki örnek, tür karakterlerinin ve kapsayan karakterlerin doğru kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5a12c-120">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 <span data-ttu-id="5a12c-121">Aşağıdaki tabloda, Visual Basic ' de bulunan karakterlerin ve tür karakterlerinin gösterildiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5a12c-121">The following table shows the enclosing characters and type characters available in Visual Basic.</span></span>  
  
|<span data-ttu-id="5a12c-122">Veri türü</span><span class="sxs-lookup"><span data-stu-id="5a12c-122">Data type</span></span>|<span data-ttu-id="5a12c-123">Kapsayan karakter</span><span class="sxs-lookup"><span data-stu-id="5a12c-123">Enclosing character</span></span>|<span data-ttu-id="5a12c-124">Eklenen tür karakteri</span><span class="sxs-lookup"><span data-stu-id="5a12c-124">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="5a12c-125">(yok)</span><span class="sxs-lookup"><span data-stu-id="5a12c-125">(none)</span></span>|<span data-ttu-id="5a12c-126">(yok)</span><span class="sxs-lookup"><span data-stu-id="5a12c-126">(none)</span></span>|  
|`Byte`|<span data-ttu-id="5a12c-127">(yok)</span><span class="sxs-lookup"><span data-stu-id="5a12c-127">(none)</span></span>|<span data-ttu-id="5a12c-128">(yok)</span><span class="sxs-lookup"><span data-stu-id="5a12c-128">(none)</span></span>|  
|`Char`|<span data-ttu-id="5a12c-129">"</span><span class="sxs-lookup"><span data-stu-id="5a12c-129">"</span></span>|<span data-ttu-id="5a12c-130">C</span><span class="sxs-lookup"><span data-stu-id="5a12c-130">C</span></span>|  
|`Date`|#|<span data-ttu-id="5a12c-131">(yok)</span><span class="sxs-lookup"><span data-stu-id="5a12c-131">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="5a12c-132">(yok)</span><span class="sxs-lookup"><span data-stu-id="5a12c-132">(none)</span></span>|<span data-ttu-id="5a12c-133">D veya @</span><span class="sxs-lookup"><span data-stu-id="5a12c-133">D or @</span></span>|  
|`Double`|<span data-ttu-id="5a12c-134">(yok)</span><span class="sxs-lookup"><span data-stu-id="5a12c-134">(none)</span></span>|<span data-ttu-id="5a12c-135">R veya #</span><span class="sxs-lookup"><span data-stu-id="5a12c-135">R or #</span></span>|  
|`Integer`|<span data-ttu-id="5a12c-136">(yok)</span><span class="sxs-lookup"><span data-stu-id="5a12c-136">(none)</span></span>|<span data-ttu-id="5a12c-137">I veya%</span><span class="sxs-lookup"><span data-stu-id="5a12c-137">I or %</span></span>|  
|`Long`|<span data-ttu-id="5a12c-138">(yok)</span><span class="sxs-lookup"><span data-stu-id="5a12c-138">(none)</span></span>|<span data-ttu-id="5a12c-139">L veya &</span><span class="sxs-lookup"><span data-stu-id="5a12c-139">L or &</span></span>|  
|`Short`|<span data-ttu-id="5a12c-140">(yok)</span><span class="sxs-lookup"><span data-stu-id="5a12c-140">(none)</span></span>|<span data-ttu-id="5a12c-141">S</span><span class="sxs-lookup"><span data-stu-id="5a12c-141">S</span></span>|  
|`Single`|<span data-ttu-id="5a12c-142">(yok)</span><span class="sxs-lookup"><span data-stu-id="5a12c-142">(none)</span></span>|<span data-ttu-id="5a12c-143">F veya!</span><span class="sxs-lookup"><span data-stu-id="5a12c-143">F or !</span></span>|  
|`String`|<span data-ttu-id="5a12c-144">"</span><span class="sxs-lookup"><span data-stu-id="5a12c-144">"</span></span>|<span data-ttu-id="5a12c-145">(yok)</span><span class="sxs-lookup"><span data-stu-id="5a12c-145">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a12c-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a12c-146">See also</span></span>

- [<span data-ttu-id="5a12c-147">Kullanıcı Tanımlı Sabitler</span><span class="sxs-lookup"><span data-stu-id="5a12c-147">User-Defined Constants</span></span>](user-defined-constants.md)
- [<span data-ttu-id="5a12c-148">Nasıl yapılır: Bir Sabit Bildirme</span><span class="sxs-lookup"><span data-stu-id="5a12c-148">How to: Declare A Constant</span></span>](how-to-declare-a-constant.md)
- [<span data-ttu-id="5a12c-149">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5a12c-149">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="5a12c-150">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="5a12c-150">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="5a12c-151">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="5a12c-151">Option Explicit Statement</span></span>](../../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="5a12c-152">Sabit Listelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5a12c-152">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="5a12c-153">Nasıl yapılır: numaralandırma bildirme</span><span class="sxs-lookup"><span data-stu-id="5a12c-153">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="5a12c-154">Sabit Listeleri ve Ad Niteliği</span><span class="sxs-lookup"><span data-stu-id="5a12c-154">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="5a12c-155">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="5a12c-155">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="5a12c-156">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="5a12c-156">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
