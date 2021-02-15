---
description: 'Daha fazla bilgi edinin: enterpolasyonlu dizeler (Visual Basic Başvurusu)'
title: Enterpolasyonlu dizeler
ms.date: 10/31/2017
ms.openlocfilehash: c054401070079bdf85181619ef43c246feea5e18
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429669"
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="b40f1-103">Enterpolasyonlu dizeler (Visual Basic Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b40f1-103">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="b40f1-104">Dizeleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b40f1-104">Used to construct strings.</span></span>  <span data-ttu-id="b40f1-105">Bir ara değerli dize, *enterpolasyonlu ifadeler* içeren bir şablon dizesi gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="b40f1-105">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="b40f1-106">Bir enterpolasyonlu dize, içerdiği ilişkili ifadelerin dize gösterimleriyle yerini alan bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="b40f1-106">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="b40f1-107">Bu özellik Visual Basic 14 ve sonraki sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b40f1-107">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="b40f1-108">Enterpolasyonlu bir dizenin bağımsız değişkenleri bir [bileşik biçim dizesinden](../../../../standard/base-types/composite-formatting.md#composite-format-string)daha kolay anlaşılır.</span><span class="sxs-lookup"><span data-stu-id="b40f1-108">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="b40f1-109">Örneğin, enterpolasyonlu dize</span><span class="sxs-lookup"><span data-stu-id="b40f1-109">For example, the interpolated string</span></span>

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

<span data-ttu-id="b40f1-110">' {name} ' ve ' {hours: hh} ' adlı iki enterpolasyonlu ifade içeriyor.</span><span class="sxs-lookup"><span data-stu-id="b40f1-110">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="b40f1-111">Eşdeğer bileşik biçim dizesi:</span><span class="sxs-lookup"><span data-stu-id="b40f1-111">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours)
```

<span data-ttu-id="b40f1-112">Enterpolasyonlu bir dizenin yapısı:</span><span class="sxs-lookup"><span data-stu-id="b40f1-112">The structure of an interpolated string is:</span></span>

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

<span data-ttu-id="b40f1-113">burada:</span><span class="sxs-lookup"><span data-stu-id="b40f1-113">where:</span></span>

- <span data-ttu-id="b40f1-114">*alan genişliği* , alandaki karakter sayısını gösteren işaretli bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="b40f1-114">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="b40f1-115">Pozitif ise, alan sağa hizalanır; negatif ise, sola hizalı.</span><span class="sxs-lookup"><span data-stu-id="b40f1-115">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span>

- <span data-ttu-id="b40f1-116">*Biçim-dize* , biçimlendirilen nesne türüne uygun bir biçim dizesidir.</span><span class="sxs-lookup"><span data-stu-id="b40f1-116">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="b40f1-117">Örneğin, bir değer için <xref:System.DateTime> , "d" veya "d" gibi [Standart Tarih ve saat biçimi dizesi](../../../../standard/base-types/standard-date-and-time-format-strings.md) olabilir.</span><span class="sxs-lookup"><span data-stu-id="b40f1-117">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](../../../../standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b40f1-118">`$`Ve arasında `"` dize Başlatan boşluk olamaz.</span><span class="sxs-lookup"><span data-stu-id="b40f1-118">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="b40f1-119">Bunun yapılması bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b40f1-119">Doing so causes a compiler error.</span></span>

<span data-ttu-id="b40f1-120">Bir dize sabit değeri kullanabileceğiniz her yerde enterpolasyonlu bir dize kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b40f1-120">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="b40f1-121">Enterpolasyonlu dize, enterpolasyonlu dize her çalıştırıldığında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b40f1-121">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="b40f1-122">Bu, enterpolasyonlu bir dizenin tanımını ve değerlendirmesini ayırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b40f1-122">This allows you to separate the definition and evaluation of an interpolated string.</span></span>

<span data-ttu-id="b40f1-123">Bir küme ayracı ("{" veya "}"), enterpolasyonlu bir dizeye eklemek için, iki küme ayracı kullanın, "{{" veya "}}".</span><span class="sxs-lookup"><span data-stu-id="b40f1-123">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="b40f1-124">Daha fazla bilgi için örtük dönüşümler bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b40f1-124">See the Implicit Conversions section for more details.</span></span>

<span data-ttu-id="b40f1-125">Enterpolasyonlu dize, ara değer ("), iki nokta üst üste (:) veya virgül (,) gibi, enterpolasyonlu bir dizede özel anlamı olan başka karakterler içeriyorsa, sabit metin halinde gerçekleştiklerinde kaçışlar veya enterpolasyonlu bir ifadeye dahil edilen bir ifadeye dahil edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b40f1-125">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="b40f1-126">Aşağıdaki örnek, sonuç dizesine dahil etmek için tırnak işaretleri çıkar:</span><span class="sxs-lookup"><span data-stu-id="b40f1-126">The following example escapes quotation marks to include them in the result string:</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a><span data-ttu-id="b40f1-127">Örtük dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="b40f1-127">Implicit Conversions</span></span>

<span data-ttu-id="b40f1-128">Enterpolasyonlu bir dizeden üç örtük tür dönüştürmesi vardır:</span><span class="sxs-lookup"><span data-stu-id="b40f1-128">There are three implicit type conversions from an interpolated string:</span></span>

1. <span data-ttu-id="b40f1-129">Enterpolasyonlu bir dizenin öğesine dönüştürülmesi <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="b40f1-129">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="b40f1-130">Aşağıdaki örnek, enterpolasyonlu dize ifadeleri dize gösterimleriyle değiştirilmiş olan bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="b40f1-130">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="b40f1-131">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b40f1-131">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   <span data-ttu-id="b40f1-132">Bu, bir dize yorumlamasının nihai sonucudur.</span><span class="sxs-lookup"><span data-stu-id="b40f1-132">This is the final result of a string interpretation.</span></span> <span data-ttu-id="b40f1-133">Çift küme ayracı ("{{" ve "}}") tüm oluşumları tek bir küme ayracına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="b40f1-133">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span>

2. <span data-ttu-id="b40f1-134"><xref:System.IFormattable>Tek bir örnekten kültüre özgü içerikle birden çok sonuç dizesi oluşturmanıza izin veren bir değişkene, enterpolasyonlu bir dizenin dönüştürülmesi <xref:System.IFormattable> .</span><span class="sxs-lookup"><span data-stu-id="b40f1-134">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="b40f1-135">Bu, bireysel kültürler için doğru sayısal ve tarih biçimleri gibi şeyleri dahil etmek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="b40f1-135">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="b40f1-136">Çift küme ayracı ("{{" ve "}}") tüm oluşumları, yöntemi açıkça veya örtük olarak çağırarak, dizeyi biçimlendirene kadar çift küme ayraçları olarak kalır <xref:System.Object.ToString> .</span><span class="sxs-lookup"><span data-stu-id="b40f1-136">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="b40f1-137">İçerilen tüm enterpolasyon ifadeleri {0} ,, vb. olarak dönüştürülür {1} .</span><span class="sxs-lookup"><span data-stu-id="b40f1-137">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   <span data-ttu-id="b40f1-138">Aşağıdaki örnek, öğeleri ve <xref:System.IFormattable> enterpolasyonlu bir dizeden oluşturulan bir değişkenin alan ve özellik değerlerini göstermek için yansıma kullanır.</span><span class="sxs-lookup"><span data-stu-id="b40f1-138">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="b40f1-139">Ayrıca, <xref:System.IFormattable> değişkenini <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemine geçirir.</span><span class="sxs-lookup"><span data-stu-id="b40f1-139">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   <span data-ttu-id="b40f1-140">Enterpolasyonlu dize yalnızca yansıma kullanılarak incelenebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b40f1-140">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="b40f1-141">Bir dize biçimlendirme yöntemine (örneğin,) geçirilirse <xref:System.Console.WriteLine(System.String)> , biçim öğeleri çözümlenir ve sonuç dizesi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b40f1-141">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span>

3. <span data-ttu-id="b40f1-142">Enterpolasyonlu bir dizenin <xref:System.FormattableString> bileşik biçim dizesini temsil eden bir değişkene dönüştürülmesi.</span><span class="sxs-lookup"><span data-stu-id="b40f1-142">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="b40f1-143">Bileşik biçim dizesini ve bunun sonuç dizesi olarak nasıl işlediğini incelemek, örneğin bir sorgu oluşturuyorsanız ekleme saldırısından korunmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b40f1-143">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="b40f1-144"><xref:System.FormattableString>Ayrıca şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="b40f1-144">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="b40f1-145"><xref:System.FormattableString.ToString>İçin sonuç dizesi üreten bir aşırı yükleme <xref:System.Globalization.CultureInfo.CurrentCulture> .</span><span class="sxs-lookup"><span data-stu-id="b40f1-145">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>

      - <span data-ttu-id="b40f1-146"><xref:System.FormattableString.Invariant%2A>İçin bir dize üreten bir yöntem <xref:System.Globalization.CultureInfo.InvariantCulture> .</span><span class="sxs-lookup"><span data-stu-id="b40f1-146">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>

      - <span data-ttu-id="b40f1-147"><xref:System.FormattableString.ToString(System.IFormatProvider)>Belirtilen kültür için sonuç dizesi üreten bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="b40f1-147">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="b40f1-148">Çift küme ayracı ("{{" ve "}}") tüm oluşumları, biçimlendirene kadar çift küme ayraçları olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="b40f1-148">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="b40f1-149">İçerilen tüm enterpolasyon ifadeleri {0} ,, vb. olarak dönüştürülür {1} .</span><span class="sxs-lookup"><span data-stu-id="b40f1-149">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a><span data-ttu-id="b40f1-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b40f1-150">See also</span></span>

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [<span data-ttu-id="b40f1-151">Visual Basic dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="b40f1-151">Visual Basic Language Reference</span></span>](index.md)
