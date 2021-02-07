---
description: 'Daha fazla bilgi edinin: Visual Basic operatör önceliği'
title: İşleç Önceliği
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: 7aa4677549328d450834f3a1ecb047d405893f69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665295"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="84750-103">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="84750-103">Operator Precedence in Visual Basic</span></span>

<span data-ttu-id="84750-104">Bir ifadede birkaç işlem gerçekleştiğinde, her parça, *işleç önceliği* olarak adlandırılan önceden belirlenmiş bir sırada değerlendirilir ve çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="84750-104">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>

## <a name="precedence-rules"></a><span data-ttu-id="84750-105">Öncelik kuralları</span><span class="sxs-lookup"><span data-stu-id="84750-105">Precedence Rules</span></span>

 <span data-ttu-id="84750-106">İfadeler birden fazla kategoriden işleçler içerdiğinde, bunlar aşağıdaki kurallara göre değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="84750-106">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>

- <span data-ttu-id="84750-107">Aritmetik ve birleştirme işleçleri aşağıdaki bölümde açıklanan öncelik sırasına sahiptir ve tümü karşılaştırma, mantıksal ve bit düzeyinde operatörlerden daha önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="84750-107">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>

- <span data-ttu-id="84750-108">Tüm karşılaştırma işleçleri eşit önceliğe sahiptir ve tümü mantıksal ve bit düzeyinde operatörlerden daha önceliklidir, ancak aritmetik ve birleştirme işleçlerinden daha düşük önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="84750-108">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>

- <span data-ttu-id="84750-109">Mantıksal ve bit düzeyinde işleçler aşağıdaki bölümde açıklanan öncelik sırasına sahiptir ve tümünün aritmetik, birleştirme ve karşılaştırma işleçlerinden daha düşük önceliği vardır.</span><span class="sxs-lookup"><span data-stu-id="84750-109">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>

- <span data-ttu-id="84750-110">Eşit önceliğe sahip işleçler, ifadede göründükleri sırada soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="84750-110">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>

## <a name="precedence-order"></a><span data-ttu-id="84750-111">Öncelik sırası</span><span class="sxs-lookup"><span data-stu-id="84750-111">Precedence Order</span></span>

 <span data-ttu-id="84750-112">İşleçler aşağıdaki öncelik sırasına göre değerlendirilir:</span><span class="sxs-lookup"><span data-stu-id="84750-112">Operators are evaluated in the following order of precedence:</span></span>

### <a name="await-operator"></a><span data-ttu-id="84750-113">Await İşleci</span><span class="sxs-lookup"><span data-stu-id="84750-113">Await Operator</span></span>

 <span data-ttu-id="84750-114">Await</span><span class="sxs-lookup"><span data-stu-id="84750-114">Await</span></span>

### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="84750-115">Aritmetik ve birleştirme Işleçleri</span><span class="sxs-lookup"><span data-stu-id="84750-115">Arithmetic and Concatenation Operators</span></span>

 <span data-ttu-id="84750-116">Üs ( `^` )</span><span class="sxs-lookup"><span data-stu-id="84750-116">Exponentiation (`^`)</span></span>

 <span data-ttu-id="84750-117">Birli kimlik ve olumsuzlama ( `+` , `–` )</span><span class="sxs-lookup"><span data-stu-id="84750-117">Unary identity and negation (`+`, `–`)</span></span>

 <span data-ttu-id="84750-118">Çarpma ve kayan nokta bölmesi ( `*` , `/` )</span><span class="sxs-lookup"><span data-stu-id="84750-118">Multiplication and floating-point division (`*`, `/`)</span></span>

 <span data-ttu-id="84750-119">Tamsayı bölümü ( `\` )</span><span class="sxs-lookup"><span data-stu-id="84750-119">Integer division (`\`)</span></span>

 <span data-ttu-id="84750-120">Modüler aritmetik ( `Mod` )</span><span class="sxs-lookup"><span data-stu-id="84750-120">Modular arithmetic (`Mod`)</span></span>

 <span data-ttu-id="84750-121">Toplama ve çıkarma ( `+` , `–` )</span><span class="sxs-lookup"><span data-stu-id="84750-121">Addition and subtraction (`+`, `–`)</span></span>

 <span data-ttu-id="84750-122">Dize birleştirme ( `&` )</span><span class="sxs-lookup"><span data-stu-id="84750-122">String concatenation (`&`)</span></span>

 <span data-ttu-id="84750-123">Aritmetik bit kaydırma ( `<<` , `>>` )</span><span class="sxs-lookup"><span data-stu-id="84750-123">Arithmetic bit shift (`<<`, `>>`)</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="84750-124">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="84750-124">Comparison Operators</span></span>

 <span data-ttu-id="84750-125">Tüm karşılaştırma işleçleri ( `=` , `<>` , `<` , `<=` , `>` , `>=` , `Is` , `IsNot` , `Like` , `TypeOf` ... `Is` )</span><span class="sxs-lookup"><span data-stu-id="84750-125">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>

### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="84750-126">Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="84750-126">Logical and Bitwise Operators</span></span>

 <span data-ttu-id="84750-127">Değilleme ( `Not` )</span><span class="sxs-lookup"><span data-stu-id="84750-127">Negation (`Not`)</span></span>

 <span data-ttu-id="84750-128">Birlikte ( `And` , `AndAlso` )</span><span class="sxs-lookup"><span data-stu-id="84750-128">Conjunction (`And`, `AndAlso`)</span></span>

 <span data-ttu-id="84750-129">Kapsamlı ayırıcı ( `Or` , `OrElse` )</span><span class="sxs-lookup"><span data-stu-id="84750-129">Inclusive disjunction (`Or`, `OrElse`)</span></span>

 <span data-ttu-id="84750-130">Dışlamalı ayırıcı ( `Xor` )</span><span class="sxs-lookup"><span data-stu-id="84750-130">Exclusive disjunction (`Xor`)</span></span>

### <a name="comments"></a><span data-ttu-id="84750-131">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="84750-131">Comments</span></span>

 <span data-ttu-id="84750-132">`=`İşleci atama işleci değil yalnızca eşitlik karşılaştırma işleçtir.</span><span class="sxs-lookup"><span data-stu-id="84750-132">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="84750-133">Dize birleştirme işleci ( `&` ) bir aritmetik işleç değil, ancak önceliğe göre Aritmetik işleçlerle gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="84750-133">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>

 <span data-ttu-id="84750-134">`Is`Ve `IsNot` işleçleri nesne başvurusu karşılaştırma işleçleridir.</span><span class="sxs-lookup"><span data-stu-id="84750-134">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="84750-135">İki nesnenin değerlerini karşılaştırmazlar; yalnızca iki nesne değişkeninin aynı nesne örneğine başvurmadığını belirlemesini denetler.</span><span class="sxs-lookup"><span data-stu-id="84750-135">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>

## <a name="associativity"></a><span data-ttu-id="84750-136">İlişkilendirilebilirlik</span><span class="sxs-lookup"><span data-stu-id="84750-136">Associativity</span></span>

 <span data-ttu-id="84750-137">Eşit önceliğe sahip işleçler bir ifadede birlikte görüntülendiğinde, örneğin çarpma ve bölme gibi, derleyici, her işlemi soldan sağa karşılaştığı şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="84750-137">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="84750-138">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="84750-138">The following example illustrates this.</span></span>

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 <span data-ttu-id="84750-139">İlk ifade, Bölüm 96/8 ' i (12 ' de sonuç olarak) değerlendirir ve sonra Bölüm 12/4 ' dir ve bu da üç ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="84750-139">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="84750-140">Derleyici işlemleri soldan sağa değerlendirdiği için `n1` , bu sıra için açıkça belirtildiği zaman değerlendirme aynı olur `n2` .</span><span class="sxs-lookup"><span data-stu-id="84750-140">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="84750-141">Her ikisi de `n1` üç ile oluşur `n2` .</span><span class="sxs-lookup"><span data-stu-id="84750-141">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="84750-142">Bunun aksine `n3` 48 sonucu vardır, çünkü parantezler derleyicinin önce 8/4 ' i değerlendirmesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="84750-142">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>

 <span data-ttu-id="84750-143">Bu davranış nedeniyle, operatörlerin Visual Basic olarak *sola ilişkilendirilebilir* olduğu söylenir.</span><span class="sxs-lookup"><span data-stu-id="84750-143">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>

## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="84750-144">Öncelik ve birleşim özelliklerini geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="84750-144">Overriding Precedence and Associativity</span></span>

 <span data-ttu-id="84750-145">Bir ifadenin bazı bölümlerinin diğerlerinden önce değerlendirilmesini zorlamak için parantezleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84750-145">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="84750-146">Bu, hem öncelik sırasını hem de sola ilişkilendirilebilirliği geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="84750-146">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="84750-147">Visual Basic, dış öğelerden önce parantez içine alınmış işlemleri her zaman gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="84750-147">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="84750-148">Bununla birlikte, parantez içinde parantez kullanmadığınız müddetçe, parantez içinde normal öncelik ve ilişkilendirilebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="84750-148">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="84750-149">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="84750-149">The following example illustrates this.</span></span>

```vb
Dim a, b, c, d, e, f, g As Double
a = 8.0
b = 3.0
c = 4.0
d = 2.0
e = 1.0
f = a - b + c / d * e
' The preceding line sets f to 7.0. Because of natural operator
' precedence and associativity, it is exactly equivalent to the
' following line.
f = (a - b) + ((c / d) * e)
' The following line overrides the natural operator precedence
' and left associativity.
g = (a - (b + c)) / (d * e)
' The preceding line sets g to 0.5.
```

## <a name="see-also"></a><span data-ttu-id="84750-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84750-150">See also</span></span>

- [<span data-ttu-id="84750-151">= İşleci</span><span class="sxs-lookup"><span data-stu-id="84750-151">= Operator</span></span>](assignment-operator.md)
- [<span data-ttu-id="84750-152">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="84750-152">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="84750-153">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="84750-153">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="84750-154">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="84750-154">Like Operator</span></span>](like-operator.md)
- [<span data-ttu-id="84750-155">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="84750-155">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="84750-156">Await Işleci</span><span class="sxs-lookup"><span data-stu-id="84750-156">Await Operator</span></span>](await-operator.md)
- [<span data-ttu-id="84750-157">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="84750-157">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="84750-158">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="84750-158">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
