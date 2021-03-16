---
title: XML belge açıklamaları-C# Programlama Kılavuzu
description: XML belge açıklamaları hakkında bilgi edinin. Özel Açıklama alanlarına XML öğeleri ekleyerek, kodunuz için belge oluşturabilirsiniz.
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: d784ec58096e44cf010edd279f682555df58a8ef
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478391"
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="17946-104">XML belgeleri Yorumları (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="17946-104">XML documentation comments (C# programming guide)</span></span>

<span data-ttu-id="17946-105">C# ' de, örneğin, yorumların başvurduğu kod bloğundan hemen önce, kaynak kodundaki özel Açıklama alanlarına (üç eğik çizgi ile gösterilir) XML öğeleri ekleyerek kodunuz için belge oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17946-105">In C#, you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example.</span></span>

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

<span data-ttu-id="17946-106">Belgelerce [**Tationfile**](../../language-reference/compiler-options/output.md#documentationfile) seçeneğiyle derlerken, derleyici kaynak KODUNDAKI tüm XML etiketlerini arar ve bir XML belge dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17946-106">When you compile with the [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="17946-107">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17946-107">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="17946-108">XML öğelerine başvurmak için (örneğin, işleviniz bir XML belge açıklamasında açıklama eklemek istediğiniz belirli XML öğelerini işler), standart tırnak işareti mekanizmasını ( `<` ve `>` ) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17946-108">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="17946-109">Kod başvurusu () öğelerinde genel tanımlayıcılara başvurmak için `cref` , kaçış karakterlerini (örneğin, `cref="List&lt;T&gt;"` ) veya küme ayracı ( `cref="List{T}"` ) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17946-109">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="17946-110">Özel bir durum olarak, derleyici, genel tanımlayıcılara başvururken belge açıklamasının yazar için daha az sıkıcı olması için, derleyici tireleri açılı ayraçlar olarak ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="17946-110">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>

> [!NOTE]
> <span data-ttu-id="17946-111">XML belge açıklamaları meta veri değildir; oluşturulan derlemeye dahil edilmezler ve bu nedenle yansıtma üzerinden erişilemezler.</span><span class="sxs-lookup"><span data-stu-id="17946-111">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="17946-112">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="17946-112">In this section</span></span>

- [<span data-ttu-id="17946-113">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="17946-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)

- [<span data-ttu-id="17946-114">XML dosyasını işleme</span><span class="sxs-lookup"><span data-stu-id="17946-114">Processing the XML file</span></span>](./processing-the-xml-file.md)

- [<span data-ttu-id="17946-115">Belge etiketleri için sınırlayıcılar</span><span class="sxs-lookup"><span data-stu-id="17946-115">Delimiters for documentation tags</span></span>](./delimiters-for-documentation-tags.md)

- [<span data-ttu-id="17946-116">XML belge özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="17946-116">How to use the XML documentation features</span></span>](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a><span data-ttu-id="17946-117">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="17946-117">Related sections</span></span>

<span data-ttu-id="17946-118">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="17946-118">For more information, see:</span></span>

- [<span data-ttu-id="17946-119">**Belgetationfile** (Işlem belgeleri açıklamaları)</span><span class="sxs-lookup"><span data-stu-id="17946-119">**DocumentationFile** (Process Documentation Comments)</span></span>](../../language-reference/compiler-options/output.md#documentationfile)

## <a name="c-language-specification"></a><span data-ttu-id="17946-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="17946-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="17946-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17946-121">See also</span></span>

- [<span data-ttu-id="17946-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="17946-122">C# Programming Guide</span></span>](../index.md)
