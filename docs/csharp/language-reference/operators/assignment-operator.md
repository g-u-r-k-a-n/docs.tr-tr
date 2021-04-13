---
description: Atama işleçleri-C# başvurusu
title: Atama işleçleri-C# başvurusu
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 702652cc7ae05d6a2bfd419ebce55399b9403a52
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075439"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="9ca5e-103">Atama işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9ca5e-103">Assignment operators (C# reference)</span></span>

<span data-ttu-id="9ca5e-104">Atama işleci, `=` sağ işleneninin değerini bir değişkene, [özelliğe](../../programming-guide/classes-and-structs/properties.md)veya kendi sol işleneni tarafından verilen bir [Dizin Oluşturucu](../../programming-guide/indexers/index.md) öğesine atar.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-104">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="9ca5e-105">Atama ifadesinin sonucu, sol işlenene atanan değerdir.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-105">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="9ca5e-106">Sağ işlenenin türü, sol işlenenin türüyle aynı veya örtülü olarak dönüştürülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-106">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="9ca5e-107">Atama işleci, `=` doğru ilişkilendirilebilir, diğer bir deyişle, formun bir ifadesi</span><span class="sxs-lookup"><span data-stu-id="9ca5e-107">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="9ca5e-108">şöyle değerlendirilir</span><span class="sxs-lookup"><span data-stu-id="9ca5e-108">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="9ca5e-109">Aşağıdaki örnek, bir yerel değişken, bir özellik ve bir Dizin Oluşturucu öğesi olan atama işlecinin kullanımını sol işlenen olarak gösterir:</span><span class="sxs-lookup"><span data-stu-id="9ca5e-109">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](snippets/shared/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="9ca5e-110">ref atama işleci</span><span class="sxs-lookup"><span data-stu-id="9ca5e-110">ref assignment operator</span></span>

<span data-ttu-id="9ca5e-111">C# 7,3 ' den başlayarak ref atama işlecini kullanarak `= ref` bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkenini yeniden atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-111">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="9ca5e-112">Aşağıdaki örnek, ref atama işlecinin kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="9ca5e-112">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](snippets/shared/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="9ca5e-113">Ref atama operatörü durumunda, her iki işleneni de aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-113">In the case of the ref assignment operator, both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="9ca5e-114">Bileşik atama</span><span class="sxs-lookup"><span data-stu-id="9ca5e-114">Compound assignment</span></span>

<span data-ttu-id="9ca5e-115">Bir ikili işleci için `op` , formun bileşik atama ifadesi</span><span class="sxs-lookup"><span data-stu-id="9ca5e-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="9ca5e-116">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="9ca5e-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="9ca5e-117">hariç `x` yalnızca bir kez değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="9ca5e-118">Bileşik atama [Aritmetik](arithmetic-operators.md#compound-assignment), [Boole mantıksal](boolean-logical-operators.md#compound-assignment)ve [bit düzeyinde mantıksal ve kaydırma](bitwise-and-shift-operators.md#compound-assignment) işleçleri tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="9ca5e-119">Null birleştirme ataması</span><span class="sxs-lookup"><span data-stu-id="9ca5e-119">Null-coalescing assignment</span></span>

<span data-ttu-id="9ca5e-120">C# 8,0 ' den başlayarak, sağ işleneninin değerini yalnızca sol taraftaki işlenenin ' `??=` i değerlendirildiğinde sol tarafından atamak için null birleşim atama işlecini kullanabilirsiniz `null` .</span><span class="sxs-lookup"><span data-stu-id="9ca5e-120">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="9ca5e-121">Daha fazla bilgi için?? [ve?? = operatörler](null-coalescing-operator.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-121">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="9ca5e-122">Operatör overloadability</span><span class="sxs-lookup"><span data-stu-id="9ca5e-122">Operator overloadability</span></span>

<span data-ttu-id="9ca5e-123">Kullanıcı tanımlı bir tür atama işlecini [aşırı yükleyemez](operator-overloading.md) .</span><span class="sxs-lookup"><span data-stu-id="9ca5e-123">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="9ca5e-124">Ancak, Kullanıcı tanımlı bir tür, başka bir türe örtük bir dönüştürme tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-124">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="9ca5e-125">Bu şekilde, Kullanıcı tanımlı bir türün değeri bir değişkene, özelliğe veya başka bir türün Dizin Oluşturucu öğesine atanabilir.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-125">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="9ca5e-126">Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="9ca5e-126">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="9ca5e-127">Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-127">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="9ca5e-128">Ancak, Kullanıcı tanımlı bir tür ikili bir işleci aşırı yükle, varsa `op` `op=` işleç da dolaylı olarak aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-128">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9ca5e-129">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9ca5e-129">C# language specification</span></span>

<span data-ttu-id="9ca5e-130">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [atama işleçleri](~/_csharplang/spec/expressions.md#assignment-operators) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-130">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="9ca5e-131">Ref atama işleci hakkında daha fazla bilgi için `= ref` bkz. [özellik teklifi Not](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="9ca5e-131">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ca5e-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ca5e-132">See also</span></span>

- [<span data-ttu-id="9ca5e-133">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9ca5e-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9ca5e-134">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="9ca5e-134">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="9ca5e-135">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="9ca5e-135">ref keyword</span></span>](../keywords/ref.md)
