---
title: Değer türleri - C# referansı
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 406e5b8bbe0802146a65bb4b9a053e753a7827ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399583"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="bd18d-102">Değer türleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bd18d-102">Value types (C# reference)</span></span>

<span data-ttu-id="bd18d-103">*Değer türleri* ve [başvuru türleri](../keywords/reference-types.md) C# türlerinin iki ana kategorisidir.</span><span class="sxs-lookup"><span data-stu-id="bd18d-103">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="bd18d-104">Değer türünden bir değişken, türün bir örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="bd18d-104">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="bd18d-105">Bu, türünün bir örneğine başvuru içeren bir başvuru türünün değişkeninden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="bd18d-105">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="bd18d-106">Varsayılan olarak, [atama,](../operators/assignment-operator.md)bir yönteme bir argüman geçen ve bir yöntem sonucu döndürerek, değişken değerleri kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="bd18d-106">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="bd18d-107">Değer türü değişkenleri söz konusu olduğunda, karşılık gelen tür örnekleri kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="bd18d-107">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="bd18d-108">Aşağıdaki örnek, davranışı gösterir:</span><span class="sxs-lookup"><span data-stu-id="bd18d-108">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="bd18d-109">Önceki örnekte de görüldüğü gibi, değer türündeki bir değişkendeki işlemler yalnızca değişkende depolanan değer türü örneğini etkiler.</span><span class="sxs-lookup"><span data-stu-id="bd18d-109">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="bd18d-110">Bir değer türü bir başvuru türünün veri üyesini içeriyorsa, değer türü örneği kopyalandığında yalnızca başvuru türü örneğine yapılan başvuru kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="bd18d-110">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="bd18d-111">Hem kopya hem de özgün değer türü örneği aynı başvuru türü örneğine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="bd18d-111">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="bd18d-112">Aşağıdaki örnek, davranışı gösterir:</span><span class="sxs-lookup"><span data-stu-id="bd18d-112">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="bd18d-113">Kodunuzu daha az hataya yatkın ve daha sağlam hale getirmek için değişmez değer türlerini tanımlayın ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd18d-113">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="bd18d-114">Bu makalede, yalnızca gösterim amacıyla mutable değer türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd18d-114">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="bd18d-115">Değer türleri türleri</span><span class="sxs-lookup"><span data-stu-id="bd18d-115">Kinds of value types</span></span>

<span data-ttu-id="bd18d-116">Değer türü aşağıdaki iki türden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="bd18d-116">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="bd18d-117">verileri ve ilgili işlevselliği kapsayan bir [yapı türü](struct.md)</span><span class="sxs-lookup"><span data-stu-id="bd18d-117">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="bd18d-118">bir [numaralandırma türü](enum.md), adlı sabitler kümesi tarafından tanımlanan ve bir seçim veya seçenek bir arada temsil eden</span><span class="sxs-lookup"><span data-stu-id="bd18d-118">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="bd18d-119">[Nullable değer türü,](nullable-value-types.md) `T?` temel değer türünün `T` tüm değerlerini ve ek bir [null](../keywords/null.md) değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bd18d-119">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="bd18d-120">Nullable değer `null` türü olmadığı sürece, değer türünden bir değişkene atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="bd18d-120">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="bd18d-121">Yerleşik değer türleri</span><span class="sxs-lookup"><span data-stu-id="bd18d-121">Built-in value types</span></span>

<span data-ttu-id="bd18d-122">C# *basit türleri*olarak da bilinen aşağıdaki yerleşik değer türlerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="bd18d-122">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="bd18d-123">Tamsayı sayısal türler</span><span class="sxs-lookup"><span data-stu-id="bd18d-123">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="bd18d-124">Kayan nokta sayısal türleri</span><span class="sxs-lookup"><span data-stu-id="bd18d-124">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="bd18d-125">boolean değerini temsil eden [bool](bool.md)</span><span class="sxs-lookup"><span data-stu-id="bd18d-125">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="bd18d-126">unicode UTF-16 karakterini temsil eden [char](char.md)</span><span class="sxs-lookup"><span data-stu-id="bd18d-126">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="bd18d-127">Tüm basit türler yapı türleridir ve belirli ek işlemlere izin verdikleri için diğer yapı türlerinden farklıdır:</span><span class="sxs-lookup"><span data-stu-id="bd18d-127">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="bd18d-128">Basit bir tür değeri sağlamak için literals kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd18d-128">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="bd18d-129">Örneğin, `'A'` `char` türünün bir harfidir `2001` ve türünün `int`bir harfidir.</span><span class="sxs-lookup"><span data-stu-id="bd18d-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="bd18d-130">[Const](../keywords/const.md) anahtar sözcüğüyle basit türlerin sabitlerini bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd18d-130">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="bd18d-131">Diğer yapı türlerinin sabitlerinin olması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="bd18d-131">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="bd18d-132">Operandları basit türlerin tüm sabitleri olan sabit ifadeler derleme zamanında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bd18d-132">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="bd18d-133">C# 7.0 ile başlayarak, C# [değer tuples](../../tuples.md)destekler.</span><span class="sxs-lookup"><span data-stu-id="bd18d-133">Beginning with C# 7.0, C# supports [value tuples](../../tuples.md).</span></span> <span data-ttu-id="bd18d-134">Değer tuple bir değer türüdür, ancak basit bir tür değildir.</span><span class="sxs-lookup"><span data-stu-id="bd18d-134">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bd18d-135">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="bd18d-135">C# language specification</span></span>

<span data-ttu-id="bd18d-136">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="bd18d-136">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="bd18d-137">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="bd18d-137">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="bd18d-138">Basit türler</span><span class="sxs-lookup"><span data-stu-id="bd18d-138">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="bd18d-139">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="bd18d-139">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="bd18d-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd18d-140">See also</span></span>

- [<span data-ttu-id="bd18d-141">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="bd18d-141">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="bd18d-142">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="bd18d-142">Reference types</span></span>](../keywords/reference-types.md)
