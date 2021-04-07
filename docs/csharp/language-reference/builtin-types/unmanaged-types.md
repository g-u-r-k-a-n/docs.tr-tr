---
description: "C 'deki yönetilmeyen türler hakkında bilgi edinin #"
title: Yönetilmeyen türler-C# başvurusu
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 13e8d4238a85201d46acabdf3103bdc7254ecfe8
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497404"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="fc00d-103">Yönetilmeyen türler (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fc00d-103">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="fc00d-104">Bir tür, aşağıdaki türlerden biri ise, **yönetilmeyen bir türdür** :</span><span class="sxs-lookup"><span data-stu-id="fc00d-104">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="fc00d-105">`sbyte`,,, `byte` `short` `ushort` , `int` , `uint` , `long` , `ulong` , `char` , `float` , `double` , `decimal` , veya `bool`</span><span class="sxs-lookup"><span data-stu-id="fc00d-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="fc00d-106">Herhangi bir [numaralandırma](enum.md) türü</span><span class="sxs-lookup"><span data-stu-id="fc00d-106">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="fc00d-107">Herhangi bir [işaretçi](../unsafe-code.md#pointer-types) türü</span><span class="sxs-lookup"><span data-stu-id="fc00d-107">Any [pointer](../unsafe-code.md#pointer-types) type</span></span>
- <span data-ttu-id="fc00d-108">Yalnızca yönetilmeyen türlerin ve C# 7,3 ve önceki sürümlerde bulunan alanları içeren Kullanıcı tanımlı [Yapı](struct.md) türleri, oluşturulmuş bir tür değildir (en az bir tür bağımsız değişkeni içeren bir tür)</span><span class="sxs-lookup"><span data-stu-id="fc00d-108">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="fc00d-109">C# 7,3 ' den başlayarak, bir tür parametresinin işaretçi olmayan, null atanamaz yönetilmeyen bir tür olduğunu belirtmek için [ `unmanaged` kısıtlamasını](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc00d-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="fc00d-110">C# 8,0 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, yönetilmeyen türlerin alanlarını içeren *oluşturulmuş* bir yapı türü de yönetilmdir:</span><span class="sxs-lookup"><span data-stu-id="fc00d-110">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/shared/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="fc00d-111">Genel bir yapı, yönetilmeyen ve yönetilmeyen oluşturulmuş türlerin kaynağı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc00d-111">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="fc00d-112">Yukarıdaki örnek, genel bir struct tanımlar `Coords<T>` ve yönetilmeyen oluşturulmuş türlerin örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc00d-112">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="fc00d-113">Yönetilmeyen bir tür örneği `Coords<object>` .</span><span class="sxs-lookup"><span data-stu-id="fc00d-113">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="fc00d-114">Yönetilmeyen değildir çünkü türünde alanları vardır `object` , yönetilmeyen değildir.</span><span class="sxs-lookup"><span data-stu-id="fc00d-114">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="fc00d-115">Oluşturulan *Tüm* türlerin yönetilmeyen türler olmasını istiyorsanız, `unmanaged` genel bir yapının tanımında kısıtlamayı kullanın:</span><span class="sxs-lookup"><span data-stu-id="fc00d-115">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/shared/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="fc00d-116">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="fc00d-116">C# language specification</span></span>

<span data-ttu-id="fc00d-117">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fc00d-117">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fc00d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc00d-118">See also</span></span>

- [<span data-ttu-id="fc00d-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fc00d-119">C# reference</span></span>](../index.md)
- [<span data-ttu-id="fc00d-120">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="fc00d-120">Pointer types</span></span>](../unsafe-code.md#pointer-types)
- [<span data-ttu-id="fc00d-121">Bellek ve aralıkla ilgili türler</span><span class="sxs-lookup"><span data-stu-id="fc00d-121">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="fc00d-122">sizeof işleci</span><span class="sxs-lookup"><span data-stu-id="fc00d-122">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="fc00d-123">stackalloc</span><span class="sxs-lookup"><span data-stu-id="fc00d-123">stackalloc</span></span>](../operators/stackalloc.md)
