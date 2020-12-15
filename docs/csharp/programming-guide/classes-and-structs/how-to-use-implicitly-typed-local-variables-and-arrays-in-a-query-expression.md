---
title: Sorgu ifadesinde örtük olarak yazılan yerel değişkenleri ve dizileri kullanma-C# Programlama Kılavuzu
description: Derleyicinin yerel bir değişken türünü belirlemesini sağlamak Için C# dilinde örtük olarak yazılan yerel değişkenler kullanın. Anonim türleri depolamak için bunları kullanmanız gerekir.
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: bd68c913c6f0d410d97973fb28789218f88903b5
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512391"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a><span data-ttu-id="2c52b-104">Bir sorgu ifadesinde örtük olarak yazılan yerel değişkenleri ve dizileri kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2c52b-104">How to use implicitly typed local variables and arrays in a query expression (C# Programming Guide)</span></span>

<span data-ttu-id="2c52b-105">Derleyicinin yerel bir değişken türünü belirlemesini istediğinizde örtülü olarak yazılan yerel değişkenleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c52b-105">You can use implicitly typed local variables whenever you want the compiler to determine the type of a local variable.</span></span> <span data-ttu-id="2c52b-106">Genellikle sorgu ifadelerinde kullanılan anonim türleri depolamak için örtük olarak belirlenmiş yerel değişkenleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c52b-106">You must use implicitly typed local variables to store anonymous types, which are often used in query expressions.</span></span> <span data-ttu-id="2c52b-107">Aşağıdaki örneklerde, sorgularda örtük olarak belirlenmiş yerel değişkenlerin hem isteğe bağlı hem de gerekli kullanımları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2c52b-107">The following examples illustrate both optional and required uses of implicitly typed local variables in queries.</span></span>  
  
 <span data-ttu-id="2c52b-108">Örtük olarak yazılan yerel değişkenler, [var](../../language-reference/keywords/var.md) olan anahtar sözcüğü kullanılarak bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2c52b-108">Implicitly typed local variables are declared by using the [var](../../language-reference/keywords/var.md) contextual keyword.</span></span> <span data-ttu-id="2c52b-109">Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](./implicitly-typed-local-variables.md) ve [örtük olarak yazılan diziler](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="2c52b-109">For more information, see [Implicitly Typed Local Variables](./implicitly-typed-local-variables.md) and [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c52b-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c52b-110">Example</span></span>  

 <span data-ttu-id="2c52b-111">Aşağıdaki örnek, anahtar sözcüğünün gerekli olduğu ortak bir senaryoyu göstermektedir `var` : anonim türler dizisi üreten bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="2c52b-111">The following example shows a common scenario in which the `var` keyword is required: a query expression that produces a sequence of anonymous types.</span></span> <span data-ttu-id="2c52b-112">Bu senaryoda, `foreach` `var` anonim türdeki bir tür adına erişiminizin olmadığı için, hem sorgu değişkeni hem de deyimdeki yineleme değişkeni kullanılarak örtük olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c52b-112">In this scenario, both the query variable and the iteration variable in the `foreach` statement must be implicitly typed by using `var` because you do not have access to a type name for the anonymous type.</span></span> <span data-ttu-id="2c52b-113">Anonim türler hakkında daha fazla bilgi için bkz. [anonim türler](./anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="2c52b-113">For more information about anonymous types, see [Anonymous Types](./anonymous-types.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="2c52b-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c52b-114">Example</span></span>  

 <span data-ttu-id="2c52b-115">Aşağıdaki örnek, `var` anahtar sözcüğünü benzer bir durumda kullanır, ancak öğesinin kullanımı `var` isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2c52b-115">The following example uses the `var` keyword in a situation that is similar, but in which the use of `var` is optional.</span></span> <span data-ttu-id="2c52b-116">`student.LastName`Bir dize olduğundan, sorgunun yürütülmesi bir dizi dizeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2c52b-116">Because `student.LastName` is a string, execution of the query returns a sequence of strings.</span></span> <span data-ttu-id="2c52b-117">Bu nedenle, türü `queryID` yerine olarak bildirilemez `System.Collections.Generic.IEnumerable<string>` `var` .</span><span class="sxs-lookup"><span data-stu-id="2c52b-117">Therefore, the type of `queryID` could be declared as `System.Collections.Generic.IEnumerable<string>` instead of `var`.</span></span> <span data-ttu-id="2c52b-118">Anahtar sözcüğü `var` kolaylık sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c52b-118">Keyword `var` is used for convenience.</span></span> <span data-ttu-id="2c52b-119">Örnekte, deyimindeki yineleme değişkeni `foreach` açıkça bir dize olarak yazılır, ancak bunun yerine kullanılarak bildirilebilecek `var` .</span><span class="sxs-lookup"><span data-stu-id="2c52b-119">In the example, the iteration variable in the `foreach` statement is explicitly typed as a string, but it could instead be declared by using `var`.</span></span> <span data-ttu-id="2c52b-120">Yineleme değişkeninin türü anonim bir tür olmadığından, öğesinin kullanımı `var` bir seçenek değildir.</span><span class="sxs-lookup"><span data-stu-id="2c52b-120">Because the type of the iteration variable is not an anonymous type, the use of `var` is an option, not a requirement.</span></span> <span data-ttu-id="2c52b-121">Unutmayın, `var` bir tür değil, türü çıkarsanmak ve atamak için derleyicinin bir yönergesi.</span><span class="sxs-lookup"><span data-stu-id="2c52b-121">Remember, `var` itself is not a type, but an instruction to the compiler to infer and assign the type.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a><span data-ttu-id="2c52b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c52b-122">See also</span></span>

- [<span data-ttu-id="2c52b-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2c52b-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2c52b-124">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="2c52b-124">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="2c52b-125">LINQ (dil ile tümleşik sorgu)</span><span class="sxs-lookup"><span data-stu-id="2c52b-125">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="2c52b-126">l</span><span class="sxs-lookup"><span data-stu-id="2c52b-126">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="2c52b-127">C# üzerinde LINQ</span><span class="sxs-lookup"><span data-stu-id="2c52b-127">LINQ in C#</span></span>](../../linq/index.md)
