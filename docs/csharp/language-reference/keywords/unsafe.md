---
title: güvenli olmayan anahtar C# sözcük-başvuru
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: ef98809eae0329c028dfb318c4a437aae4736db1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712994"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="7bf42-102">unsafe (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7bf42-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="7bf42-103">`unsafe` anahtar sözcüğü, işaretçileri içeren tüm işlemler için gerekli olan güvenli olmayan bir bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bf42-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="7bf42-104">Daha fazla bilgi için bkz. [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="7bf42-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="7bf42-105">`unsafe` değiştiricisini bir tür veya üye bildiriminde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bf42-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="7bf42-106">Türün veya üyenin metinsel kapsamı, bu nedenle güvenli olmayan bir bağlam olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7bf42-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="7bf42-107">Örneğin, aşağıda `unsafe` değiştiriciyle belirtilen bir yöntem verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7bf42-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="7bf42-108">Güvenli olmayan bağlamın kapsamı parametre listesinden yönteminin sonuna kadar uzanır, bu nedenle işaretçiler parametre listesinde de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7bf42-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="7bf42-109">Güvenli olmayan bir blok, bu blok içinde güvenli olmayan bir kod kullanımını etkinleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bf42-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="7bf42-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7bf42-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="7bf42-111">Güvenli olmayan kod derlemek için [`-unsafe`](../compiler-options/unsafe-compiler-option.md) derleyici seçeneğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7bf42-111">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="7bf42-112">Güvenli olmayan kod, ortak dil çalışma zamanı tarafından doğrulanabilir değil.</span><span class="sxs-lookup"><span data-stu-id="7bf42-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="7bf42-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bf42-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="7bf42-114">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7bf42-114">C# language specification</span></span>

<span data-ttu-id="7bf42-115">Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [güvenli olmayan kod](~/_csharplang/spec/unsafe-code.md) .</span><span class="sxs-lookup"><span data-stu-id="7bf42-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="7bf42-116">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="7bf42-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bf42-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bf42-117">See also</span></span>

- [<span data-ttu-id="7bf42-118">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="7bf42-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7bf42-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7bf42-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7bf42-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="7bf42-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7bf42-121">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="7bf42-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="7bf42-122">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="7bf42-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="7bf42-123">Sabit Boyutlu Arabellekler</span><span class="sxs-lookup"><span data-stu-id="7bf42-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
