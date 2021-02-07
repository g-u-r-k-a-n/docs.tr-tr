---
description: 'Daha fazla bilgi edinin: dize Işlevleri (Visual Basic)'
title: Dize İşlevleri
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 1c121bc3de66caf748426b5cd04d049b30bf78bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731165"
---
# <a name="string-functions-visual-basic"></a><span data-ttu-id="12332-103">Dize İşlevleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12332-103">String Functions (Visual Basic)</span></span>

<span data-ttu-id="12332-104">Aşağıdaki tablo, <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> dizeleri aramak ve işlemek için sınıfında Visual Basic sağladığı işlevleri listeler.</span><span class="sxs-lookup"><span data-stu-id="12332-104">The following table lists the functions that Visual Basic provides in the <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> class to search and manipulate strings.</span></span> <span data-ttu-id="12332-105">Visual Basic iç işlevler olarak kabul edilebilir. diğer bir deyişle, örneklerin gösterdiği gibi, bunları bir sınıfın açık üyeleri olarak çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="12332-105">They can be regarded as Visual Basic intrinsic functions; that is, you do not have to call them as explicit members of a class, as the examples show.</span></span> <span data-ttu-id="12332-106">Ek yöntemler ve bazı durumlarda tamamlayıcı Yöntemler <xref:System.String?displayProperty=nameWithType> sınıfında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="12332-106">Additional methods, and in some cases complementary methods, are available in the <xref:System.String?displayProperty=nameWithType> class.</span></span>

|<span data-ttu-id="12332-107">.NET Framework yöntemi</span><span class="sxs-lookup"><span data-stu-id="12332-107">.NET Framework method</span></span>|<span data-ttu-id="12332-108">Description</span><span class="sxs-lookup"><span data-stu-id="12332-108">Description</span></span>|
|---------------------------|-----------------|
|<span data-ttu-id="12332-109"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="12332-109"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>|<span data-ttu-id="12332-110">`Integer`Bir karaktere karşılık gelen karakter kodunu temsil eden bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-110">Returns an `Integer` value representing the character code corresponding to a character.</span></span>|
|<span data-ttu-id="12332-111"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="12332-111"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>|<span data-ttu-id="12332-112">Belirtilen karakter koduyla ilişkili karakteri döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-112">Returns the character associated with the specified character code.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|<span data-ttu-id="12332-113">Belirtilen filtre ölçütlerine göre bir dizinin alt kümesini içeren sıfır tabanlı bir dizi döndürür `String` .</span><span class="sxs-lookup"><span data-stu-id="12332-113">Returns a zero-based array containing a subset of a `String` array based on specified filter criteria.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|<span data-ttu-id="12332-114">Biçim ifadesinde bulunan yönergelere göre biçimlendirilen bir dize döndürür `String` .</span><span class="sxs-lookup"><span data-stu-id="12332-114">Returns a string formatted according to instructions contained in a format `String` expression.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|<span data-ttu-id="12332-115">Sistem denetim masasında tanımlanan para birimi simgesini kullanarak para birimi değeri olarak biçimlendirilen bir ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-115">Returns an expression formatted as a currency value using the currency symbol defined in the system control panel.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|<span data-ttu-id="12332-116">Tarih/saat değerini gösteren bir dize ifadesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-116">Returns a string expression representing a date/time value.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|<span data-ttu-id="12332-117">Sayı olarak biçimlendirilen bir ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-117">Returns an expression formatted as a number.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|<span data-ttu-id="12332-118">% Karakteriyle bir yüzde (yani, 100 ile çarpılmış) olarak biçimlendirilen bir ifade döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-118">Returns an expression formatted as a percentage (that is, multiplied by 100) with a trailing % character.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|<span data-ttu-id="12332-119">Bir dizenin diğeri içindeki ilk örneğinin başlangıç konumunu belirten bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-119">Returns an integer specifying the start position of the first occurrence of one string within another.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|<span data-ttu-id="12332-120">Dizenin sağ tarafından başlayarak bir dizenin diğeri içindeki ilk oluşumunun konumunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-120">Returns the position of the first occurrence of one string within another, starting from the right side of the string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|<span data-ttu-id="12332-121">Bir dizide bulunan bir dizi alt dizenin birleştirilmesiyle oluşturulan bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-121">Returns a string created by joining a number of substrings contained in an array.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|<span data-ttu-id="12332-122">Küçük harfe dönüştürülmüş bir dize veya karakter döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-122">Returns a string or character converted to lowercase.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|<span data-ttu-id="12332-123">Dizenin sol tarafından belirtilen sayıda karakter içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-123">Returns a string containing a specified number of characters from the left side of a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|<span data-ttu-id="12332-124">Dizedeki karakter sayısını içeren bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-124">Returns an integer that contains the number of characters in a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|<span data-ttu-id="12332-125">Belirtilen uzunluğa ayarlanmış belirtilen dizeyi içeren sola hizalanmış bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-125">Returns a left-aligned string containing the specified string adjusted to the specified length.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|<span data-ttu-id="12332-126">Belirtilen dizenin başında boşluk olmayan bir kopyasını içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-126">Returns a string containing a copy of a specified string with no leading spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|<span data-ttu-id="12332-127">Bir dizeden belirtilen sayıda karakter içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-127">Returns a string containing a specified number of characters from a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|<span data-ttu-id="12332-128">Belirtilen bir alt dizenin belirtilen sayıda başka bir alt dizeyle değiştirildiği bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-128">Returns a string in which a specified substring has been replaced with another substring a specified number of times.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|<span data-ttu-id="12332-129">Dizenin sağ tarafından belirtilen sayıda karakter içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-129">Returns a string containing a specified number of characters from the right side of a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|<span data-ttu-id="12332-130">Belirtilen uzunluğa ayarlanmış belirtilen dizeyi içeren sağa hizalanmış bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-130">Returns a right-aligned string containing the specified string adjusted to the specified length.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|<span data-ttu-id="12332-131">Belirtilen dizenin sonunda boşluk olmayan bir kopyasını içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-131">Returns a string containing a copy of a specified string with no trailing spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|<span data-ttu-id="12332-132">Belirtilen sayıda boşluktan oluşan bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-132">Returns a string consisting of the specified number of spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|<span data-ttu-id="12332-133">Belirtilen sayıda alt dize içeren sıfır tabanlı, tek boyutlu bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-133">Returns a zero-based, one-dimensional array containing a specified number of substrings.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|<span data-ttu-id="12332-134">Dize karşılaştırmasının sonucuna bağlı olarak-1, 0 veya 1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-134">Returns -1, 0, or 1, based on the result of a string comparison.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|<span data-ttu-id="12332-135">Belirtilen şekilde dönüştürülmüş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-135">Returns a string converted as specified.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|<span data-ttu-id="12332-136">Belirtilen karakterin belirtilen sayıda yinelenmesinden oluşan bir dize veya nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-136">Returns a string or object consisting of the specified character repeated the specified number of times.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|<span data-ttu-id="12332-137">Belirtilen dizenin karakter sırasının tersine döndürüldüğü bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-137">Returns a string in which the character order of a specified string is reversed.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|<span data-ttu-id="12332-138">Belirtilen dizenin başında veya sonunda boşluk olmayan bir kopyasını içeren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-138">Returns a string containing a copy of a specified string with no leading or trailing spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|<span data-ttu-id="12332-139">Belirtilen dizeyi büyük harfe dönüştürülmüş olarak içeren bir dize veya karakter döndürür.</span><span class="sxs-lookup"><span data-stu-id="12332-139">Returns a string or character containing the specified string converted to uppercase.</span></span>|

<span data-ttu-id="12332-140">Dizelerin, sisteminizin yerel [](../statements/option-compare-statement.md) ayarında ( `Text` ) veya karakterlerin iç ikili gösterimlerine () göre belirlenen büyük/küçük harf duyarsız metin sıralama düzeni kullanılarak karşılaştırıldığını ayarlamak için Option Compare ifadesini kullanabilirsiniz `Binary` .</span><span class="sxs-lookup"><span data-stu-id="12332-140">You can use the [Option Compare](../statements/option-compare-statement.md) statement to set whether strings are compared using a case-insensitive text sort order determined by your system's locale (`Text`) or by the internal binary representations of the characters (`Binary`).</span></span> <span data-ttu-id="12332-141">Varsayılan metin karşılaştırma yöntemi `Binary` .</span><span class="sxs-lookup"><span data-stu-id="12332-141">The default text comparison method is `Binary`.</span></span>

## <a name="example-ucase"></a><span data-ttu-id="12332-142">Örnek: UCase</span><span class="sxs-lookup"><span data-stu-id="12332-142">Example: UCase</span></span>

<span data-ttu-id="12332-143">Bu örnek, `UCase` bir dizenin büyük bir sürümünü döndürmek için işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="12332-143">This example uses the `UCase` function to return an uppercase version of a string.</span></span>
[!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]

## <a name="example-ltrim"></a><span data-ttu-id="12332-144">Örnek: LTrim</span><span class="sxs-lookup"><span data-stu-id="12332-144">Example: LTrim</span></span>

<span data-ttu-id="12332-145">Bu örnek, `LTrim` `RTrim` bir dize değişkeninden sondaki boşlukları park etmek için öndeki boşlukları ve işlevi eklemek için işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="12332-145">This example uses the `LTrim` function to strip leading spaces and the `RTrim` function to strip trailing spaces from a string variable.</span></span> <span data-ttu-id="12332-146">`Trim`Her iki boşluk türünü de atmak için işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="12332-146">It uses the `Trim` function to strip both types of spaces.</span></span>

[!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]

## <a name="example-mid"></a><span data-ttu-id="12332-147">Örnek: PARÇAAL</span><span class="sxs-lookup"><span data-stu-id="12332-147">Example: Mid</span></span>

<span data-ttu-id="12332-148">Bu örnek, `Mid` bir dizeden belirtilen sayıda karakteri döndürmek için işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="12332-148">This example uses the `Mid` function to return a specified number of characters from a string.</span></span>

[!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]

## <a name="example-len"></a><span data-ttu-id="12332-149">Örnek: Len</span><span class="sxs-lookup"><span data-stu-id="12332-149">Example: Len</span></span>

<span data-ttu-id="12332-150">Bu örnek `Len` , bir dizedeki karakter sayısını döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="12332-150">This example uses `Len` to return the number of characters in a string.</span></span>

[!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]

## <a name="example-instr"></a><span data-ttu-id="12332-151">Örnek: InStr</span><span class="sxs-lookup"><span data-stu-id="12332-151">Example: InStr</span></span>

<span data-ttu-id="12332-152">Bu örnek, bir `InStr` dizenin diğeri içindeki ilk oluşumunun konumunu döndürmek için işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="12332-152">This example uses the `InStr` function to return the position of the first occurrence of one string within another.</span></span>

[!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]

## <a name="example-format"></a><span data-ttu-id="12332-153">Örnek: biçim</span><span class="sxs-lookup"><span data-stu-id="12332-153">Example: Format</span></span>

<span data-ttu-id="12332-154">Bu örnek, `Format` her iki `String` biçimi ve Kullanıcı tanımlı biçimleri kullanarak değerleri biçimlendirmek için işlevinin çeşitli kullanımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="12332-154">This example shows various uses of the `Format` function to format values using both `String` formats and user-defined formats.</span></span> <span data-ttu-id="12332-155">Tarih ayırıcısı ( `/` ), zaman ayırıcısı ( `:` ) ve ı/PM göstergeleri ( `t` ve `tt` ) için, sisteminiz tarafından görünen gerçek biçimli çıktı, kodun kullandığı yerel ayar ayarlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="12332-155">For the date separator (`/`), time separator (`:`), and the AM/PM indicators (`t` and `tt`), the actual formatted output displayed by your system depends on the locale settings the code is using.</span></span> <span data-ttu-id="12332-156">Geliştirme ortamında saat ve tarihler görüntülendiğinde, kod yerel ayarının kısa saat biçimi ve kısa tarih biçimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12332-156">When times and dates are displayed in the development environment, the short time format and short date format of the code locale are used.</span></span>

> [!NOTE]
> <span data-ttu-id="12332-157">24 saatlik bir saat kullanan yerel ayarlarda, ı/PM göstergeleri ( `t` ve `tt` ) hiçbir şey görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="12332-157">For locales that use a 24-hour clock, the AM/PM indicators (`t` and `tt`) display nothing.</span></span>

[!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]

## <a name="see-also"></a><span data-ttu-id="12332-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12332-158">See also</span></span>

- [<span data-ttu-id="12332-159">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="12332-159">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="12332-160">Visual Basic Çalışma Süresi Kitaplık Üyeleri</span><span class="sxs-lookup"><span data-stu-id="12332-160">Visual Basic Runtime Library Members</span></span>](../runtime-library-members.md)
- [<span data-ttu-id="12332-161">Dize Düzenleme Özeti</span><span class="sxs-lookup"><span data-stu-id="12332-161">String Manipulation Summary</span></span>](../keywords/string-manipulation-summary.md)
- [<span data-ttu-id="12332-162">System. String sınıf yöntemleri</span><span class="sxs-lookup"><span data-stu-id="12332-162">System.String class methods</span></span>](xref:System.String#methods)
