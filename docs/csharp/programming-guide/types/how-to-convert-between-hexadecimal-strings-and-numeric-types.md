---
title: Onaltılık dizeler ve sayısal türler arasında dönüştürme-C# Programlama Kılavuzu
description: Onaltılık dizeler ve sayısal türler arasında dönüştürme yapmayı öğrenin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 35cf1af661071c70b8d68de2e47ce555be7b9fef
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025413"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="3e90c-104">Onaltılık dizeler ve sayısal türler arasında dönüştürme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3e90c-104">How to convert between hexadecimal strings and numeric types (C# Programming Guide)</span></span>

<span data-ttu-id="3e90c-105">Bu örneklerde aşağıdaki görevlerin nasıl gerçekleştirileceği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3e90c-105">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="3e90c-106">[Dizedeki](../../language-reference/builtin-types/reference-types.md)her karakterin onaltılık değerini elde edin.</span><span class="sxs-lookup"><span data-stu-id="3e90c-106">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="3e90c-107">Onaltılık dizedeki her değere karşılık gelen [char](../../language-reference/builtin-types/char.md) 'ı alın.</span><span class="sxs-lookup"><span data-stu-id="3e90c-107">Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="3e90c-108">Onaltılı bir `string` [int](../../language-reference/builtin-types/integral-numeric-types.md)'e dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="3e90c-108">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="3e90c-109">Bir onaltılık tabandaki bir `string` [float](../../language-reference/builtin-types/floating-point-numeric-types.md)öğesine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="3e90c-109">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="3e90c-110">Bir [bayt](../../language-reference/builtin-types/integral-numeric-types.md) dizisini onaltılı olarak dönüştürür `string` .</span><span class="sxs-lookup"><span data-stu-id="3e90c-110">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e90c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e90c-111">Example</span></span>  

 <span data-ttu-id="3e90c-112">Bu örnek, içindeki her bir karakterin onaltılık değerini verir `string` .</span><span class="sxs-lookup"><span data-stu-id="3e90c-112">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="3e90c-113">İlk `string` olarak, bir karakter dizisi olarak ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="3e90c-113">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="3e90c-114">Ardından <xref:System.Convert.ToInt32%28System.Char%29> , sayısal değerini elde etmek için her bir karakter üzerinde çağırır.</span><span class="sxs-lookup"><span data-stu-id="3e90c-114">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="3e90c-115">Son olarak, sayıyı içinde onaltılık gösterimi olarak biçimlendirir `string` .</span><span class="sxs-lookup"><span data-stu-id="3e90c-115">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="3e90c-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e90c-116">Example</span></span>  

 <span data-ttu-id="3e90c-117">Bu örnek `string` , onaltılı değerleri ayrıştırır ve her onaltılık değere karşılık gelen karakteri verir.</span><span class="sxs-lookup"><span data-stu-id="3e90c-117">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="3e90c-118">İlk olarak, her onaltılı değeri bir dizide bir kişi olarak almak için [Split (Char \[ \] )](xref:System.String.Split(System.Char[])) yöntemini çağırır `string` .</span><span class="sxs-lookup"><span data-stu-id="3e90c-118">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="3e90c-119">Ardından <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> , onaltılı değeri [tamsayı](../../language-reference/builtin-types/integral-numeric-types.md)olarak temsil edilen bir ondalık değere dönüştürmek için çağırır. Bu karakter koduna karşılık gelen karakteri almanın iki farklı yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e90c-119">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="3e90c-120">İlk tekniği kullanır <xref:System.Char.ConvertFromUtf32%28System.Int32%29> ve tamsayı bağımsız değişkenine karşılık gelen karakteri bir olarak döndürür `string` .</span><span class="sxs-lookup"><span data-stu-id="3e90c-120">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="3e90c-121">İkinci teknik, öğesini açıkça `int` bir [char](../../language-reference/builtin-types/char.md)öğesine yayınlar.</span><span class="sxs-lookup"><span data-stu-id="3e90c-121">The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="3e90c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e90c-122">Example</span></span>  

 <span data-ttu-id="3e90c-123">Bu örnek `string` , yöntemini çağırarak, onaltılı bir tamsayıyı bir tamsayıya dönüştürmenin başka bir yolunu gösterir <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> .</span><span class="sxs-lookup"><span data-stu-id="3e90c-123">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="3e90c-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e90c-124">Example</span></span>  

 <span data-ttu-id="3e90c-125">Aşağıdaki örnek, `string` sınıfı ve yöntemi kullanılarak bir onaltılık tabandaki bir [float](../../language-reference/builtin-types/floating-point-numeric-types.md) öğesine nasıl dönüştürüleceğini gösterir <xref:System.BitConverter?displayProperty=nameWithType> <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3e90c-125">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="3e90c-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e90c-126">Example</span></span>  

 <span data-ttu-id="3e90c-127">Aşağıdaki örnek, sınıfını kullanarak bir [bayt](../../language-reference/builtin-types/integral-numeric-types.md) dizisinin onaltılık dizeye nasıl dönüştürüleceğini gösterir <xref:System.BitConverter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3e90c-127">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="example"></a><span data-ttu-id="3e90c-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e90c-128">Example</span></span>  

 <span data-ttu-id="3e90c-129">Aşağıdaki örnekte, [](../../language-reference/builtin-types/integral-numeric-types.md) <xref:System.Convert.ToHexString%2A?displayProperty=nameWithType> .NET 5,0 ' de tanıtılan yöntemi çağırarak bir bayt dizisinin onaltılık dizeye nasıl dönüştürüleceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e90c-129">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by calling the <xref:System.Convert.ToHexString%2A?displayProperty=nameWithType> method introduced in .NET 5.0.</span></span>
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="see-also"></a><span data-ttu-id="3e90c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e90c-130">See also</span></span>

- [<span data-ttu-id="3e90c-131">Standart Sayısal Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="3e90c-131">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="3e90c-132">Türler</span><span class="sxs-lookup"><span data-stu-id="3e90c-132">Types</span></span>](./index.md)
- [<span data-ttu-id="3e90c-133">Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme</span><span class="sxs-lookup"><span data-stu-id="3e90c-133">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
