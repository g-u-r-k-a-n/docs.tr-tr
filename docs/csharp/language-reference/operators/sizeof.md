---
description: sizeof işleci-C# başvurusu
title: sizeof işleci-C# başvurusu
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 6685cdb4fba2460ee4a47b004aa6911ab76235a4
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497378"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="46a8d-103">sizeof işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="46a8d-103">sizeof operator (C# reference)</span></span>

<span data-ttu-id="46a8d-104">`sizeof`İşleci, verilen türdeki bir değişken tarafından bulunan bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="46a8d-104">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="46a8d-105">İşlecin bağımsız değişkeni, yönetilmeyen bir `sizeof` [türün](../builtin-types/unmanaged-types.md) veya yönetilmeyen tür olarak [Kısıtlanmış](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) bir tür parametresinin adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46a8d-105">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="46a8d-106">`sizeof`Operatör [güvenli olmayan](../keywords/unsafe.md) bir bağlam gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="46a8d-106">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="46a8d-107">Ancak, aşağıdaki tabloda sunulan ifadeler derleme zamanında karşılık gelen sabit değerlere değerlendirilir ve güvenli olmayan bir bağlam gerektirmez:</span><span class="sxs-lookup"><span data-stu-id="46a8d-107">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="46a8d-108">Expression</span><span class="sxs-lookup"><span data-stu-id="46a8d-108">Expression</span></span>|<span data-ttu-id="46a8d-109">Sabit değer</span><span class="sxs-lookup"><span data-stu-id="46a8d-109">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="46a8d-110">1</span><span class="sxs-lookup"><span data-stu-id="46a8d-110">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="46a8d-111">1</span><span class="sxs-lookup"><span data-stu-id="46a8d-111">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="46a8d-112">2</span><span class="sxs-lookup"><span data-stu-id="46a8d-112">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="46a8d-113">2</span><span class="sxs-lookup"><span data-stu-id="46a8d-113">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="46a8d-114">4</span><span class="sxs-lookup"><span data-stu-id="46a8d-114">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="46a8d-115">4</span><span class="sxs-lookup"><span data-stu-id="46a8d-115">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="46a8d-116">8</span><span class="sxs-lookup"><span data-stu-id="46a8d-116">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="46a8d-117">8</span><span class="sxs-lookup"><span data-stu-id="46a8d-117">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="46a8d-118">2</span><span class="sxs-lookup"><span data-stu-id="46a8d-118">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="46a8d-119">4</span><span class="sxs-lookup"><span data-stu-id="46a8d-119">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="46a8d-120">8</span><span class="sxs-lookup"><span data-stu-id="46a8d-120">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="46a8d-121">16</span><span class="sxs-lookup"><span data-stu-id="46a8d-121">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="46a8d-122">1</span><span class="sxs-lookup"><span data-stu-id="46a8d-122">1</span></span>|

<span data-ttu-id="46a8d-123">Ayrıca, `sizeof` işlecin işleneni bir [sabit](../builtin-types/enum.md) listesi türünün adı olduğunda güvenli olmayan bir bağlam kullanmanıza gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="46a8d-123">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="46a8d-124">Aşağıdaki örnek işlecinin kullanımını gösterir `sizeof` :</span><span class="sxs-lookup"><span data-stu-id="46a8d-124">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](snippets/shared/SizeOfOperator.cs)]

<span data-ttu-id="46a8d-125">`sizeof`İşleci, yönetilen bellekte ortak dil çalışma zamanı tarafından ayrılacak bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="46a8d-125">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="46a8d-126">[Yapı](../builtin-types/struct.md) türleri için bu değer, yukarıdaki örnekte gösterildiği gibi herhangi bir doldurma içerir.</span><span class="sxs-lookup"><span data-stu-id="46a8d-126">For [struct](../builtin-types/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="46a8d-127">İşlecinin sonucu, `sizeof` <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> *yönetilmeyen* bellekteki bir türün boyutunu döndüren yönteminin sonuçlarından farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="46a8d-127">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="46a8d-128">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="46a8d-128">C# language specification</span></span>

<span data-ttu-id="46a8d-129">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sizeof işleci](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="46a8d-129">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46a8d-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46a8d-130">See also</span></span>

- [<span data-ttu-id="46a8d-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="46a8d-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="46a8d-132">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="46a8d-132">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="46a8d-133">İşaretçi bağlantılı işleçler</span><span class="sxs-lookup"><span data-stu-id="46a8d-133">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="46a8d-134">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="46a8d-134">Pointer types</span></span>](../unsafe-code.md#pointer-types)
- [<span data-ttu-id="46a8d-135">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="46a8d-135">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="46a8d-136">.NET içindeki Genel Türler</span><span class="sxs-lookup"><span data-stu-id="46a8d-136">Generics in .NET</span></span>](../../../standard/generics/index.md)
