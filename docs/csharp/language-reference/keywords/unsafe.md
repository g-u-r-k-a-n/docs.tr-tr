---
description: güvenli olmayan anahtar sözcük-C# başvurusu
title: güvenli olmayan anahtar sözcük-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 5be895621966dd10b2b1b0f53ebf0f3c688f1ef0
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480659"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="1f035-103">unsafe (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1f035-103">unsafe (C# Reference)</span></span>

<span data-ttu-id="1f035-104">`unsafe`Anahtar sözcüğü, işaretçileri içeren tüm işlemler için gerekli olan güvenli olmayan bir bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f035-104">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="1f035-105">Daha fazla bilgi için bkz. [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f035-105">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="1f035-106">`unsafe`Değiştirici bir tür veya üye bildiriminde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f035-106">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="1f035-107">Türün veya üyenin metinsel kapsamı, bu nedenle güvenli olmayan bir bağlam olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1f035-107">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="1f035-108">Örneğin, değiştirici ile belirtilen bir yöntemi aşağıda verilmiştir `unsafe` :</span><span class="sxs-lookup"><span data-stu-id="1f035-108">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="1f035-109">Güvenli olmayan bağlamın kapsamı parametre listesinden yönteminin sonuna kadar uzanır, bu nedenle işaretçiler parametre listesinde de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1f035-109">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="1f035-110">Güvenli olmayan bir blok, bu blok içinde güvenli olmayan bir kod kullanımını etkinleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f035-110">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="1f035-111">Örnek:</span><span class="sxs-lookup"><span data-stu-id="1f035-111">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="1f035-112">Güvenli olmayan kod derlemek için [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks) derleyici seçeneğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f035-112">To compile unsafe code, you must specify the [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks) compiler option.</span></span> <span data-ttu-id="1f035-113">Güvenli olmayan kod, ortak dil çalışma zamanı tarafından doğrulanabilir değil.</span><span class="sxs-lookup"><span data-stu-id="1f035-113">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="1f035-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f035-114">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="1f035-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1f035-115">C# language specification</span></span>

<span data-ttu-id="1f035-116">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [güvenli olmayan kod](~/_csharplang/spec/unsafe-code.md) .</span><span class="sxs-lookup"><span data-stu-id="1f035-116">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="1f035-117">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="1f035-117">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f035-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f035-118">See also</span></span>

- [<span data-ttu-id="1f035-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1f035-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1f035-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1f035-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1f035-121">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1f035-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1f035-122">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="1f035-122">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="1f035-123">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="1f035-123">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="1f035-124">Sabit boyutlu arabellekler</span><span class="sxs-lookup"><span data-stu-id="1f035-124">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
