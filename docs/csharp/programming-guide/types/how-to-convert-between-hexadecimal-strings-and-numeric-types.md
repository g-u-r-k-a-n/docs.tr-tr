---
title: Hexadecimal dizeleri ve sayısal türleri arasında dönüştürmek için nasıl - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 0e1f6ad2606b367d369c1c644c947831b2aa8289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698527"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="11cf2-102">Hexadecimal dizeleri ve sayısal türleri (C# Programlama Kılavuzu) arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="11cf2-102">How to convert between hexadecimal strings and numeric types (C# Programming Guide)</span></span>
<span data-ttu-id="11cf2-103">Bu örnekler, aşağıdaki görevleri nasıl gerçekleştireceklerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="11cf2-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="11cf2-104">Bir dize her karakterin hexadecimal değerini elde [edin.](../../language-reference/builtin-types/reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="11cf2-104">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="11cf2-105">Bir hexadecimal dize her değere karşılık gelen [char](../../language-reference/builtin-types/char.md) edinin.</span><span class="sxs-lookup"><span data-stu-id="11cf2-105">Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="11cf2-106">Bir hexadecimal'ı `string` [int'e](../../language-reference/builtin-types/integral-numeric-types.md)dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="11cf2-106">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="11cf2-107">Bir hexadecimal `string` [float dönüştürün.](../../language-reference/builtin-types/floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="11cf2-107">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="11cf2-108">Bir [bayt](../../language-reference/builtin-types/integral-numeric-types.md) dizisini hexadecimal'a `string`dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="11cf2-108">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11cf2-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="11cf2-109">Example</span></span>  
 <span data-ttu-id="11cf2-110">Bu örnek, her karakterin hexadecimal değerini `string`bir .</span><span class="sxs-lookup"><span data-stu-id="11cf2-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="11cf2-111">Önce bir dizi `string` karaktere ayrışır.</span><span class="sxs-lookup"><span data-stu-id="11cf2-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="11cf2-112">Sonra her <xref:System.Convert.ToInt32%28System.Char%29> karakter kendi sayısal değerini elde etmek için çağırır.</span><span class="sxs-lookup"><span data-stu-id="11cf2-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="11cf2-113">Son olarak, sayıyı hexadecimal gösterimi `string`olarak biçimlendirmektedir.</span><span class="sxs-lookup"><span data-stu-id="11cf2-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="11cf2-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="11cf2-114">Example</span></span>  
 <span data-ttu-id="11cf2-115">Bu örnek, `string` hexadecimal değerlerden birini ayrıştırır ve her hexadecimal değere karşılık gelen karakteri çıkar.</span><span class="sxs-lookup"><span data-stu-id="11cf2-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="11cf2-116">Önce bir dizi bir birey `string` olarak her hexadecimal değeri elde etmek için Split [(Char)\[\]](xref:System.String.Split(System.Char[])) yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="11cf2-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="11cf2-117">Sonra hexadecimal değeri bir <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> [int](../../language-reference/builtin-types/integral-numeric-types.md)olarak temsil edilen ondalık değere dönüştürmek için çağırır. Bu karakter koduna karşılık gelen karakteri elde etmek için iki farklı yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="11cf2-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="11cf2-118">İlk teknik, <xref:System.Char.ConvertFromUtf32%28System.Int32%29>tamsayı bağımsız değişkenine karşılık gelen `string`karakteri döndürür.</span><span class="sxs-lookup"><span data-stu-id="11cf2-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="11cf2-119">İkinci teknik açıkça bir `int` [char](../../language-reference/builtin-types/char.md)atar.</span><span class="sxs-lookup"><span data-stu-id="11cf2-119">The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="11cf2-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="11cf2-120">Example</span></span>  
 <span data-ttu-id="11cf2-121">Bu örnek, yöntemi çağırarak bir hexadecimal'ı `string` tamsayıya dönüştürmenin <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> başka bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="11cf2-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="11cf2-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="11cf2-122">Example</span></span>  
 <span data-ttu-id="11cf2-123">Aşağıdaki örnek, [float](../../language-reference/builtin-types/floating-point-numeric-types.md) <xref:System.BitConverter?displayProperty=nameWithType> sınıfı ve <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> yöntemi kullanarak bir hexadecimal `string` float nasıl dönüştürülür gösterir.</span><span class="sxs-lookup"><span data-stu-id="11cf2-123">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="11cf2-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="11cf2-124">Example</span></span>  
 <span data-ttu-id="11cf2-125">Aşağıdaki örnek, <xref:System.BitConverter?displayProperty=nameWithType> bir [bayt](../../language-reference/builtin-types/integral-numeric-types.md) dizisini sınıfı kullanarak bir hexadecimal dizeye nasıl dönüştüreceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="11cf2-125">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="11cf2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11cf2-126">See also</span></span>

- [<span data-ttu-id="11cf2-127">Standart Sayısal Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="11cf2-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="11cf2-128">Türler</span><span class="sxs-lookup"><span data-stu-id="11cf2-128">Types</span></span>](./index.md)
- [<span data-ttu-id="11cf2-129">Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme</span><span class="sxs-lookup"><span data-stu-id="11cf2-129">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
