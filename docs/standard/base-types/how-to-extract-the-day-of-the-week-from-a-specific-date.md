---
title: 'Nasıl yapılır: Belirli bir Tarihten Haftanın Gününü Çıkarma'
description: .NET 'teki belirli bir tarih için haftanın sıralı gününü belirlemeyi öğrenin. Belirli bir tarih için yerelleştirilmiş iş günü adını görüntülemeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET], dates
- DateTime.DayOfWeek property
- DateTime.ToString method
- dates [.NET], retrieving week information
- DateTimeOffset.DayOfWeek property
- dates [.NET], day of week
- Weekday function
- day of week [.NET]
- extracting day of week
- weekday names
- WeekdayName function
- numbers [.NET], day of week
- formatting [.NET], time
- DateTimeOffset.ToString method
- full weekday names
ms.assetid: 1c9bef76-5634-46cf-b91c-9b9eb72091d7
ms.openlocfilehash: 9db11146ee9428ce22b08accacf7660137d539c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726996"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a><span data-ttu-id="cb084-104">Nasıl yapılır: Belirli bir Tarihten Haftanın Gününü Çıkarma</span><span class="sxs-lookup"><span data-stu-id="cb084-104">How to: Extract the Day of the Week from a Specific Date</span></span>

<span data-ttu-id="cb084-105">.NET, belirli bir tarih için haftanın sıralı gününü belirlemeyi ve belirli bir tarih için yerelleştirilmiş iş günü adını görüntülemeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="cb084-105">.NET makes it easy to determine the ordinal day of the week for a particular date, and to display the localized weekday name for a particular date.</span></span> <span data-ttu-id="cb084-106">Belirli bir tarihe karşılık gelen haftanın gününü gösteren numaralandırılmış bir değer <xref:System.DateTime.DayOfWeek%2A> veya <xref:System.DateTimeOffset.DayOfWeek%2A> özellikten kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cb084-106">An enumerated value that indicates the day of the week corresponding to a particular date is available from the <xref:System.DateTime.DayOfWeek%2A> or <xref:System.DateTimeOffset.DayOfWeek%2A> property.</span></span> <span data-ttu-id="cb084-107">Buna karşılık, hafta içi adının alınması, tarih ve saat değerinin yöntemi ya da yöntemi gibi bir biçimlendirme yöntemi çağırarak gerçekleştirilebilecek biçimlendirme işlemidir `ToString` <xref:System.String.Format%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cb084-107">In contrast, retrieving the weekday name is a formatting operation that can be performed by calling a formatting method, such as a date and time value's `ToString` method or the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cb084-108">Bu konuda, bu biçimlendirme işlemlerinin nasıl gerçekleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cb084-108">This topic shows how to perform these formatting operations.</span></span>  
  
## <a name="extract-a-number-indicating-the-day-of-the-week"></a><span data-ttu-id="cb084-109">Haftanın gününü belirten sayıyı Ayıkla</span><span class="sxs-lookup"><span data-stu-id="cb084-109">Extract a number indicating the day of the week</span></span>
  
1. <span data-ttu-id="cb084-110">Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="cb084-110">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="cb084-111"><xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> Haftanın gününü gösteren bir değer almak için veya özelliğini kullanın <xref:System.DayOfWeek> .</span><span class="sxs-lookup"><span data-stu-id="cb084-111">Use the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> property to retrieve a <xref:System.DayOfWeek> value that indicates the day of the week.</span></span>  
  
3. <span data-ttu-id="cb084-112">Gerekirse, (C# ' de) cast veya değeri (Visual Basic olarak) <xref:System.DayOfWeek> bir tamsayıya dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="cb084-112">If necessary, cast (in C#) or convert (in Visual Basic) the <xref:System.DayOfWeek> value to an integer.</span></span>  
  
 <span data-ttu-id="cb084-113">Aşağıdaki örnek, belirli bir tarihin haftanın gününü temsil eden bir tamsayı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cb084-113">The following example displays an integer that represents the day of the week of a specific date.</span></span>  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
## <a name="extract-the-abbreviated-weekday-name"></a><span data-ttu-id="cb084-114">Kısaltılmış iş günü adını Ayıkla</span><span class="sxs-lookup"><span data-stu-id="cb084-114">Extract the abbreviated weekday name</span></span>
  
1. <span data-ttu-id="cb084-115">Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="cb084-115">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="cb084-116">Geçerli kültürün kısaltılmış iş günü adını veya belirli bir kültürü ayıklayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cb084-116">You can extract the abbreviated weekday name of the current culture or of a specific culture:</span></span>  
  
    1. <span data-ttu-id="cb084-117">Geçerli kültür için kısaltılmış iş günü adını ayıklamak için, tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> örnek yöntemini çağırın ve "ddd" dizesini parametre olarak geçirin `format` .</span><span class="sxs-lookup"><span data-stu-id="cb084-117">To extract the abbreviated weekday name for the current culture, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instance method, and pass the string "ddd" as the `format` parameter.</span></span> <span data-ttu-id="cb084-118">Aşağıdaki örnek yöntemine yapılan çağrıyı gösterir <xref:System.DateTime.ToString%28System.String%29> .</span><span class="sxs-lookup"><span data-stu-id="cb084-118">The following example illustrates the call to the <xref:System.DateTime.ToString%28System.String%29> method.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. <span data-ttu-id="cb084-119">Belirli bir kültür için kısaltılmış iş günü adını ayıklamak için tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> örnek yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="cb084-119">To extract the abbreviated weekday name for a specific culture, call the date and time value's <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="cb084-120">"Ddd" dizesini parametre olarak geçirin `format` .</span><span class="sxs-lookup"><span data-stu-id="cb084-120">Pass the string "ddd" as the `format` parameter.</span></span> <span data-ttu-id="cb084-121"><xref:System.Globalization.CultureInfo> <xref:System.Globalization.DateTimeFormatInfo> Hafta içi adı parametre olarak almak istediğiniz kültürü temsil eden bir veya bir nesnesi geçirin `provider` .</span><span class="sxs-lookup"><span data-stu-id="cb084-121">Pass either a <xref:System.Globalization.CultureInfo> or a <xref:System.Globalization.DateTimeFormatInfo> object that represents the culture whose weekday name you want to retrieve as the `provider` parameter.</span></span> <span data-ttu-id="cb084-122">Aşağıdaki kod, <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> <xref:System.Globalization.CultureInfo> FR-fr kültürünü temsil eden bir nesnesi kullanarak yöntemine yapılan çağrıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb084-122">The following code illustrates a call to the <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> method using a <xref:System.Globalization.CultureInfo> object that represents the fr-FR culture.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
## <a name="extract-the-full-weekday-name"></a><span data-ttu-id="cb084-123">Tam hafta içi adı Ayıkla</span><span class="sxs-lookup"><span data-stu-id="cb084-123">Extract the full weekday name</span></span>
  
1. <span data-ttu-id="cb084-124">Eğer bir tarihin dize gösterimiyle çalışıyorsanız, statik <xref:System.DateTime> veya <xref:System.DateTimeOffset> yöntemini kullanarak bunu bir <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya bir <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> değerine dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="cb084-124">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="cb084-125">Geçerli kültürün veya belirli bir kültürün tam iş günü adını ayıklayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cb084-125">You can extract the full weekday name of the current culture or of a specific culture:</span></span>  
  
    1. <span data-ttu-id="cb084-126">Geçerli kültürün hafta içi adını ayıklamak için, tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> örnek yöntemini çağırın ve "gggg" dizesini parametre olarak geçirin `format` .</span><span class="sxs-lookup"><span data-stu-id="cb084-126">To extract the weekday name for the current culture, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instance method, and pass the string "dddd" as the `format` parameter.</span></span> <span data-ttu-id="cb084-127">Aşağıdaki örnek yöntemine yapılan çağrıyı gösterir <xref:System.DateTime.ToString%28System.String%29> .</span><span class="sxs-lookup"><span data-stu-id="cb084-127">The following example illustrates the call to the <xref:System.DateTime.ToString%28System.String%29> method.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. <span data-ttu-id="cb084-128">Belirli bir kültürün hafta içi adını ayıklamak için tarih ve saat değerinin <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> veya <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> örnek yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="cb084-128">To extract the weekday name for a specific culture, call the date and time value's <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="cb084-129">"Gggg" dizesini parametre olarak geçirin `format` .</span><span class="sxs-lookup"><span data-stu-id="cb084-129">Pass the string "dddd" as the `format` parameter.</span></span> <span data-ttu-id="cb084-130"><xref:System.Globalization.CultureInfo> <xref:System.Globalization.DateTimeFormatInfo> Hafta içi adı parametre olarak almak istediğiniz kültürü temsil eden bir veya bir nesnesi geçirin `provider` .</span><span class="sxs-lookup"><span data-stu-id="cb084-130">Pass either a <xref:System.Globalization.CultureInfo> or a <xref:System.Globalization.DateTimeFormatInfo> object that represents the culture whose weekday name you want to retrieve as the `provider` parameter.</span></span> <span data-ttu-id="cb084-131">Aşağıdaki kod, <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> <xref:System.Globalization.CultureInfo> ES-es kültürünü temsil eden bir nesnesini kullanarak yöntemine yapılan çağrıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb084-131">The following code illustrates a call to the <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> method using a <xref:System.Globalization.CultureInfo> object that represents the es-ES culture.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="cb084-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb084-132">Example</span></span>  

 <span data-ttu-id="cb084-133">Örnek, <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> ve özelliklerinin yanı sıra, <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> belirli bir tarih için haftanın gününü, kısaltılmış iş günü adını ve tam gün adını temsil eden sayıyı almak için ve yöntemlerine ve yöntemlere yönelik çağrıları gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb084-133">The example illustrates calls to the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> properties and the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> methods to retrieve the number that represents the day of the week, the abbreviated weekday name, and the full weekday name for a particular date.</span></span>  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 <span data-ttu-id="cb084-134">Bireysel diller .NET tarafından sunulan işlevselliği çoğaltan veya tamamlayan işlevselliği sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="cb084-134">Individual languages may provide functionality that duplicates or supplements the functionality provided by .NET.</span></span> <span data-ttu-id="cb084-135">Örneğin, Visual Basic iki işlevi de içerir:</span><span class="sxs-lookup"><span data-stu-id="cb084-135">For example, Visual Basic includes two such functions:</span></span>  
  
- <span data-ttu-id="cb084-136">`Weekday`, belirli bir tarihin haftanın gününü gösteren bir sayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb084-136">`Weekday`, which returns a number that indicates the day of the week of a particular date.</span></span> <span data-ttu-id="cb084-137">Haftanın ilk gününün sıra değerini bir kabul eder, ancak <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> özellik onu sıfır olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="cb084-137">It considers the ordinal value of the first day of the week to be one, whereas the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> property considers it to be zero.</span></span>  
  
- <span data-ttu-id="cb084-138">`WeekdayName`Bu, geçerli kültürün belirli bir iş günü numarasına karşılık gelen haftanın adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="cb084-138">`WeekdayName`, which returns the name of the week in the current culture that corresponds to a particular weekday number.</span></span>  
  
 <span data-ttu-id="cb084-139">Aşağıdaki örnek, Visual Basic `Weekday` ve işlevlerinin kullanımını gösterir `WeekdayName` .</span><span class="sxs-lookup"><span data-stu-id="cb084-139">The following example illustrates the use of the Visual Basic `Weekday` and `WeekdayName` functions.</span></span>  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 <span data-ttu-id="cb084-140"><xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType>Belirli bir tarihin hafta içi adını almak için özelliği tarafından döndürülen değeri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb084-140">You can also use the value returned by the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> property to retrieve the weekday name of a particular date.</span></span> <span data-ttu-id="cb084-141">Bu, yalnızca <xref:System.Enum.ToString%2A> <xref:System.DayOfWeek> özelliği tarafından döndürülen değer üzerinde yöntemine bir çağrı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cb084-141">This requires only a call to the <xref:System.Enum.ToString%2A> method on the <xref:System.DayOfWeek> value returned by the property.</span></span> <span data-ttu-id="cb084-142">Ancak, bu teknik, aşağıdaki örnekte gösterildiği gibi geçerli kültür için yerelleştirilmiş bir iş günü adı üretmez.</span><span class="sxs-lookup"><span data-stu-id="cb084-142">However, this technique does not produce a localized weekday name for the current culture, as the following example illustrates.</span></span>  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]

## <a name="see-also"></a><span data-ttu-id="cb084-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb084-143">See also</span></span>

- [<span data-ttu-id="cb084-144">Standart Tarih ve saat biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="cb084-144">Standard Date and Time Format Strings</span></span>](standard-date-and-time-format-strings.md)
- [<span data-ttu-id="cb084-145">Özel tarih ve saat biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="cb084-145">Custom Date and Time Format Strings</span></span>](custom-date-and-time-format-strings.md)
