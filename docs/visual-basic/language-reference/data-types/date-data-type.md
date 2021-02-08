---
description: 'Hakkında daha fazla bilgi edinin: Tarih veri türü (Visual Basic)'
title: Date Veri Türü
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: f6ea6aa99339d13824477bba99ecd211f826a3ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775025"
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="cf9bb-103">Date Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf9bb-103">Date Data Type (Visual Basic)</span></span>

<span data-ttu-id="cf9bb-104">0001 yılının 1 Ocak ayının 9999 31 Aralık 12:00:00 'a kadar (gece yarısı), 11:59:59.9999999 PM arasında değişen tarihleri temsil eden IEEE 64-bit (8 baytlık) değerleri barındırır.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-104">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="cf9bb-105">Her artış, Gregoryen takvimdeki 1 Ocak yılın başından itibaren geçen sürenin 100 nanosaniye süresini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-105">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="cf9bb-106">Maksimum değer 100, 1 Ocak 10000 yılın başından önce nanosaniye 'yi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-106">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf9bb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf9bb-107">Remarks</span></span>

<span data-ttu-id="cf9bb-108">`Date`Tarih değerlerini, zaman değerlerini veya tarih ve saat değerlerini içermesi için veri türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-108">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>

<span data-ttu-id="cf9bb-109">`Date`1 Ocak 0001 tarihinde varsayılan değer 0:00:00 ' dir (gece yarısı).</span><span class="sxs-lookup"><span data-stu-id="cf9bb-109">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>

<span data-ttu-id="cf9bb-110">Geçerli tarih ve saati <xref:Microsoft.VisualBasic.DateAndTime> sınıftan alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-110">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>

## <a name="format-requirements"></a><span data-ttu-id="cf9bb-111">Biçim gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="cf9bb-111">Format Requirements</span></span>

<span data-ttu-id="cf9bb-112">Bir `Date` sabit değeri sayı işaretleri () içine almalısınız `# #` .</span><span class="sxs-lookup"><span data-stu-id="cf9bb-112">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="cf9bb-113">Tarih değerini M/d/yyyy biçiminde belirtmeniz gerekir, örneğin `#5/31/1993#` veya yyyy-aa-gg gibi `#1993-5-31#` .</span><span class="sxs-lookup"><span data-stu-id="cf9bb-113">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="cf9bb-114">Önce yılı belirtirken eğik çizgi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-114">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="cf9bb-115">Bu gereksinim, yerel ayarınızı ve bilgisayarınızın tarih ve saat biçimi ayarlarını birbirinden bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-115">This requirement is independent of your locale and your computer's date and time format settings.</span></span>

<span data-ttu-id="cf9bb-116">Bu kısıtlamanın nedeni, kodunuzun anlamını uygulamanızın çalıştırıldığı yerel ayara bağlı olarak asla değiştirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-116">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="cf9bb-117">Bir sabit `Date` değer `#3/4/1998#` kodladığınızı ve 4 Mart 1998 ' den itibaren olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-117">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="cf9bb-118">Aa/gg/yyyy kullanan bir yerel ayarda, 3/4/1998 istediğiniz şekilde derlenir.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-118">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="cf9bb-119">Ancak uygulamanızı birçok ülkede/bölgede dağıttığınız varsayın.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-119">But suppose you deploy your application in many countries/regions.</span></span> <span data-ttu-id="cf9bb-120">Gg/aa/yyyy kullanan bir yerel ayarda, sabit kodlanmış sabit değer 3 Nisan 1998 ' e derlenir.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-120">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="cf9bb-121">Yyyy/aa/gg kullanan bir yerel ayarda, değişmez değer geçersiz (1998 Nisan, 0003) ve bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-121">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="cf9bb-122">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="cf9bb-122">Workarounds</span></span>

<span data-ttu-id="cf9bb-123">Bir `Date` sabit değeri yerel ayarınızdaki biçime veya özel bir biçime dönüştürmek için, <xref:Microsoft.VisualBasic.Strings.Format%2A> önceden tanımlanmış veya Kullanıcı tanımlı bir tarih biçimini belirterek, işleve değişmez değeri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-123">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="cf9bb-124">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-124">The following example demonstrates this.</span></span>

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

<span data-ttu-id="cf9bb-125">Alternatif olarak, <xref:System.DateTime> bir tarih ve saat değerini birleştirmek için yapının aşırı yüklenmiş oluşturucularından birini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-125">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="cf9bb-126">Aşağıdaki örnek, öğleden sonra 31 Mayıs 12:14 1993 ' i temsil eden bir değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-126">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a><span data-ttu-id="cf9bb-127">Saat biçimi</span><span class="sxs-lookup"><span data-stu-id="cf9bb-127">Hour Format</span></span>

<span data-ttu-id="cf9bb-128">Saat değerini 12 saat veya 24 saat biçiminde belirtebilirsiniz, örneğin `#1:15:30 PM#` veya `#13:15:30#` .</span><span class="sxs-lookup"><span data-stu-id="cf9bb-128">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="cf9bb-129">Ancak, dakikalar veya saniyeler belirtmezseniz, har veya PM belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-129">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>

## <a name="date-and-time-defaults"></a><span data-ttu-id="cf9bb-130">Tarih ve saat Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="cf9bb-130">Date and Time Defaults</span></span>

<span data-ttu-id="cf9bb-131">Tarih/saat değişmez değerinde bir tarih eklemezseniz, Visual Basic değerin tarih bölümünü 1 Ocak 0001 olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-131">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="cf9bb-132">Tarih/saat değişmez değerinde bir saat eklemezseniz, Visual Basic değerin saat bölümünü günün başına, yani gece yarısı (0:00:00) olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-132">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>

## <a name="type-conversions"></a><span data-ttu-id="cf9bb-133">Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="cf9bb-133">Type Conversions</span></span>

<span data-ttu-id="cf9bb-134">Bir `Date` değeri `String` türüne dönüştürürseniz Visual Basic, tarihi çalışma zamanı yerel ayarı tarafından belirtilen kısa tarih biçimine göre işler ve saati çalışma zamanı yerel ayarı tarafından belirtilen saat biçimine (12 saat veya 24 saat) göre işler.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-134">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="cf9bb-135">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="cf9bb-135">Programming Tips</span></span>

- <span data-ttu-id="cf9bb-136">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="cf9bb-136">**Interop Considerations.**</span></span> <span data-ttu-id="cf9bb-137">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimleriniz varsa, diğer ortamlardaki tarih/saat türlerinin Visual Basic türüyle uyumlu olmadığını aklınızda bulundurun `Date` .</span><span class="sxs-lookup"><span data-stu-id="cf9bb-137">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="cf9bb-138">Böyle bir bileşene bir tarih/saat bağımsız değişkeni geçirdiğinizden, bunu `Double` yeni Visual Basic kodunuzda değil olarak bildirin `Date` ve dönüştürme yöntemlerini <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> ve kullanın <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cf9bb-138">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="cf9bb-139">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="cf9bb-139">**Type Characters.**</span></span> <span data-ttu-id="cf9bb-140">`Date` değişmez değer türü karakteri veya tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-140">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="cf9bb-141">Ancak derleyici, sayıları sayı işaretleri () içinde olarak değerlendirir `# #` `Date` .</span><span class="sxs-lookup"><span data-stu-id="cf9bb-141">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>

- <span data-ttu-id="cf9bb-142">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="cf9bb-142">**Framework Type.**</span></span> <span data-ttu-id="cf9bb-143">.NET Framework karşılık gelen tür <xref:System.DateTime?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-143">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="cf9bb-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf9bb-144">Example</span></span>

<span data-ttu-id="cf9bb-145">Veri türünün bir değişkeni veya sabiti `Date` hem tarih hem de saati tutar.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-145">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="cf9bb-146">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-146">The following example illustrates this.</span></span>

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a><span data-ttu-id="cf9bb-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf9bb-147">See also</span></span>

- <xref:System.DateTime?displayProperty=nameWithType>
- [<span data-ttu-id="cf9bb-148">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="cf9bb-148">Data Types</span></span>](index.md)
- [<span data-ttu-id="cf9bb-149">Standart Tarih ve saat biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="cf9bb-149">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [<span data-ttu-id="cf9bb-150">Özel tarih ve saat biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="cf9bb-150">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [<span data-ttu-id="cf9bb-151">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cf9bb-151">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="cf9bb-152">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="cf9bb-152">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="cf9bb-153">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="cf9bb-153">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
