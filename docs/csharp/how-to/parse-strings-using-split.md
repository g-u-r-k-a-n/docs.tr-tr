---
title: String. Split kullanarak dizeleri bölme (C# Kılavuzu)
description: Split yöntemi, bir sınırlayıcı kümesinden bölünen dizelerin dizisini döndürür. Bu, bir dizeden alt dizeler ayıklamanın kolay bir yoludur.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 5361a3c60905edd19b180c5ddb14064a85f64337
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400506"
---
# <a name="how-to-separate-strings-using-stringsplit-in-c"></a><span data-ttu-id="a08b3-104">C 'de dize. Split kullanarak dizeleri ayırma\#</span><span class="sxs-lookup"><span data-stu-id="a08b3-104">How to separate strings using String.Split in C\#</span></span>

<span data-ttu-id="a08b3-105"><xref:System.String.Split%2A?displayProperty=nameWithType>Yöntemi, giriş dizesini bir veya daha fazla sınırlayıcı temelinde bölerek bir alt dizeler dizisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a08b3-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="a08b3-106">Bu yöntem genellikle sözcük sınırlarındaki bir dizeyi ayırmanın en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="a08b3-106">This method is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="a08b3-107">Ayrıca, diğer belirli karakter veya dizelerde dizeleri ayırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a08b3-107">It's also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="a08b3-108">Aşağıdaki kod, ortak bir tümceciği her sözcük için bir dizeler dizisine böler.</span><span class="sxs-lookup"><span data-stu-id="a08b3-108">The following code splits a common phrase into an array of strings for each word.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

<span data-ttu-id="a08b3-109">Bir ayırıcı karakterinin her örneği döndürülen dizide bir değer üretir.</span><span class="sxs-lookup"><span data-stu-id="a08b3-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="a08b3-110">Ardışık Ayırıcı karakterler boş dizeyi döndürülen dizide bir değer olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a08b3-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span> <span data-ttu-id="a08b3-111">Bir ayırıcı olarak boşluk karakterini kullanan aşağıdaki örnekte boş bir dizenin nasıl oluşturulduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a08b3-111">You can see how an empty string is created in the following example, which uses the space character as a separator.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

<span data-ttu-id="a08b3-112">Bu davranış, tablo verilerini temsil eden, virgülle ayrılmış değerler (CSV) dosyaları gibi biçimlerin daha kolay olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a08b3-112">This behavior makes it easier for formats like comma-separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="a08b3-113">Ardışık virgüller boş bir sütunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a08b3-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="a08b3-114"><xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType>Döndürülen dizide boş dizeleri hariç tutmak için isteğe bağlı bir parametre geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a08b3-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="a08b3-115">Döndürülen koleksiyonun daha karmaşık işlenmesi için, [LINQ](../programming-guide/concepts/linq/index.md) kullanarak sonuç sırasını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a08b3-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="a08b3-116"><xref:System.String.Split%2A?displayProperty=nameWithType> birden çok ayırıcı karakter kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a08b3-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="a08b3-117">Aşağıdaki örnek, bir dizide geçirilen karakter ayrımı olarak boşluk, virgül, nokta, iki nokta üst üste ve sekmeleri kullanır <xref:System.String.Split%2A> .</span><span class="sxs-lookup"><span data-stu-id="a08b3-117">The following example uses spaces, commas, periods, colons, and tabs as separating characters, which are passed to <xref:System.String.Split%2A> in an array .</span></span>
<span data-ttu-id="a08b3-118">Kodun alt kısmındaki döngü döndürülen dizideki her bir sözcüğü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a08b3-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

<span data-ttu-id="a08b3-119">Herhangi bir ayırıcıdaki ardışık örnekler, çıkış dizisinde boş dize üretir:</span><span class="sxs-lookup"><span data-stu-id="a08b3-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<span data-ttu-id="a08b3-120"><xref:System.String.Split%2A?displayProperty=nameWithType> bir dizi dizeyi alabilir (tek karakterler yerine hedef dizeyi ayrıştırmak için ayırıcı olarak davranan karakter dizileri).</span><span class="sxs-lookup"><span data-stu-id="a08b3-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a><span data-ttu-id="a08b3-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a08b3-121">See also</span></span>

- [<span data-ttu-id="a08b3-122">Dizeden öğeleri ayıklama</span><span class="sxs-lookup"><span data-stu-id="a08b3-122">Extract elements from a string</span></span>](../../standard/base-types/divide-up-strings.md)
- [<span data-ttu-id="a08b3-123">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a08b3-123">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="a08b3-124">Dizeler</span><span class="sxs-lookup"><span data-stu-id="a08b3-124">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="a08b3-125">.NET normal ifadeleri</span><span class="sxs-lookup"><span data-stu-id="a08b3-125">.NET regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
