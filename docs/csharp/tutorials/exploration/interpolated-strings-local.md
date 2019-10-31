---
title: Dize ilişkilendirme- C# öğretici
description: Bu öğreticide, dize ilişkilendirme özelliğinin, C# biçimlendirilen ifade sonuçlarını daha büyük bir dizeye eklemek için nasıl kullanılacağı gösterilmektedir.
ms.date: 10/23/2018
ms.openlocfilehash: 53b9afa4c5ccdcb1f18d2947981aee6571b73134
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120113"
---
# <a name="use-string-interpolation-to-construct-formatted-strings"></a><span data-ttu-id="86af3-103">Biçimlendirilen dizeler oluşturmak için dize ilişkilendirmeyi kullanın</span><span class="sxs-lookup"><span data-stu-id="86af3-103">Use string interpolation to construct formatted strings</span></span>

<span data-ttu-id="86af3-104">Bu öğretici, tek bir sonuç dizesine C# değer eklemek için [dize ilişkilendirmeyi](../../language-reference/tokens/interpolated.md) nasıl kullanacağınızı öğretir.</span><span class="sxs-lookup"><span data-stu-id="86af3-104">This tutorial teaches you how to use C# [string interpolation](../../language-reference/tokens/interpolated.md) to insert values into a single result string.</span></span> <span data-ttu-id="86af3-105">Kod yazar C# ve bunları derleyip çalıştırmaya ilişkin sonuçları görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="86af3-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="86af3-106">Öğretici, bir dizeye değer ekleme ve bu değerleri farklı şekillerde biçimlendirme işlemlerinin nasıl yapılacağını gösteren bir dizi ders içerir.</span><span class="sxs-lookup"><span data-stu-id="86af3-106">The tutorial contains a series of lessons that show you how to insert values into a string and format those values in different ways.</span></span>

<span data-ttu-id="86af3-107">Bu öğreticide, geliştirme için kullanabileceğiniz bir makineniz olması beklenir.</span><span class="sxs-lookup"><span data-stu-id="86af3-107">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="86af3-108">[10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) .NET öğreticisi, Windows, Linux veya MacOS 'ta yerel geliştirme ortamınızı ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="86af3-108">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="86af3-109">Ayrıca, Bu öğreticinin [etkileşimli sürümünü](interpolated-strings.yml) tarayıcınızda tamamlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86af3-109">You also can complete the [interactive version](interpolated-strings.yml) of this tutorial in your browser.</span></span>

## <a name="create-an-interpolated-string"></a><span data-ttu-id="86af3-110">Enterpolasyonlu dize oluşturma</span><span class="sxs-lookup"><span data-stu-id="86af3-110">Create an interpolated string</span></span>

<span data-ttu-id="86af3-111">*Enterpolasyonlu*adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="86af3-111">Create a directory named *interpolated*.</span></span> <span data-ttu-id="86af3-112">Geçerli dizin yapın ve bir konsol penceresinden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="86af3-112">Make it the current directory and run the following command from a console window:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="86af3-113">Bu komut geçerli dizinde yeni bir .NET Core konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86af3-113">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="86af3-114">En sevdiğiniz düzenleyicide *program.cs* açın ve satır `Console.WriteLine("Hello World!");` aşağıdaki kodla değiştirin, burada `<name>` adınızla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="86af3-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code, where you replace `<name>` with your name:</span></span>

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```

<span data-ttu-id="86af3-115">Konsol pencerenize `dotnet run` yazarak bu kodu deneyin.</span><span class="sxs-lookup"><span data-stu-id="86af3-115">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="86af3-116">Programı çalıştırdığınızda, selamdaki adınızı içeren tek bir dize görüntüler.</span><span class="sxs-lookup"><span data-stu-id="86af3-116">When you run the program, it displays a single string that includes your name in the greeting.</span></span> <span data-ttu-id="86af3-117"><xref:System.Console.WriteLine%2A> yöntemi çağrısına dahil edilen dize, bir *enterpolasyonlu dize ifadesidir*.</span><span class="sxs-lookup"><span data-stu-id="86af3-117">The string included in the <xref:System.Console.WriteLine%2A> method call is an *interpolated string expression*.</span></span> <span data-ttu-id="86af3-118">Katıştırılmış kodu içeren bir dizeden tek bir dize ( *sonuç dizesi*olarak adlandırılır) oluşturmanıza imkan tanıyan bir şablon türüdür.</span><span class="sxs-lookup"><span data-stu-id="86af3-118">It's a kind of template that lets you construct a single string (called the *result string*) from a string that includes embedded code.</span></span> <span data-ttu-id="86af3-119">Enterpolasyonlu dizeler, bir dizeye değer eklemek veya dizeleri birleştirmek (bir araya birleştirmek) için özellikle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="86af3-119">Interpolated strings are particularly useful for inserting values into a string or concatenating (joining together) strings.</span></span>

<span data-ttu-id="86af3-120">Bu basit örnek, her bir enterpolasyonlu dizenin sahip olması gereken iki öğeyi içerir:</span><span class="sxs-lookup"><span data-stu-id="86af3-120">This simple example contains the two elements that every interpolated string must have:</span></span>

- <span data-ttu-id="86af3-121">Açılış tırnak işareti karakterinden önce `$` karakteriyle başlayan bir dize sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="86af3-121">A string literal that begins with the `$` character before its opening quotation mark character.</span></span> <span data-ttu-id="86af3-122">`$` simgesiyle tırnak işareti karakteri arasında boşluk olamaz.</span><span class="sxs-lookup"><span data-stu-id="86af3-122">There can't be any spaces between the `$` symbol and the quotation mark character.</span></span> <span data-ttu-id="86af3-123">(Bir tane eklerseniz ne olacağını görmek isterseniz, `$` karakterden sonra bir boşluk ekleyin, dosyayı kaydedin ve konsol penceresine `dotnet run` yazarak programı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="86af3-123">(If you'd like to see what happens if you include one, insert a space after the `$` character, save the file, and run the program again by typing `dotnet run` in the console window.</span></span> <span data-ttu-id="86af3-124">C# Derleyici bir hata iletisi görüntülüyor, "Error CS1056: beklenmeyen karakter ' $ '".)</span><span class="sxs-lookup"><span data-stu-id="86af3-124">The C# compiler displays an error message, "error CS1056: Unexpected character '$'".)</span></span>

- <span data-ttu-id="86af3-125">Bir veya daha fazla *ilişkilendirme ifadesi*.</span><span class="sxs-lookup"><span data-stu-id="86af3-125">One or more *interpolation expressions*.</span></span> <span data-ttu-id="86af3-126">Enterpolasyon ifadesi bir açma ve kapatma ayracı (`{` ve `}`) ile belirtilir.</span><span class="sxs-lookup"><span data-stu-id="86af3-126">An interpolation expression is indicated by an opening and closing brace (`{` and `}`).</span></span> <span data-ttu-id="86af3-127">Küme ayraçlarının içinde C# (`null` dahil) bir değer döndüren herhangi bir ifadeyi yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86af3-127">You can put any C# expression that returns a value (including `null`) inside the braces.</span></span>

<span data-ttu-id="86af3-128">Biraz daha farklı veri türleriyle daha fazla dize ilişkilendirme örneği deneyelim.</span><span class="sxs-lookup"><span data-stu-id="86af3-128">Let's try a few more string interpolation examples with some other data types.</span></span>

## <a name="include-different-data-types"></a><span data-ttu-id="86af3-129">Farklı veri türleri dahil et</span><span class="sxs-lookup"><span data-stu-id="86af3-129">Include different data types</span></span>

<span data-ttu-id="86af3-130">Önceki bölümde, bir dizeyi diğerinin içine eklemek için dize ilişkilendirmeyi kullandınız.</span><span class="sxs-lookup"><span data-stu-id="86af3-130">In the previous section, you used string interpolation to insert one string inside of another.</span></span> <span data-ttu-id="86af3-131">Enterpolasyon ifadesinin sonucu herhangi bir veri türünde olabilir, ancak.</span><span class="sxs-lookup"><span data-stu-id="86af3-131">The result of an interpolation expression can be of any data type, though.</span></span> <span data-ttu-id="86af3-132">Enterpolasyonlu bir dizedeki çeşitli veri türlerinin değerlerini ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="86af3-132">Let's include values of various data types in an interpolated string.</span></span>

<span data-ttu-id="86af3-133">Aşağıdaki örnekte, ilk olarak, <xref:System.Object.ToString?displayProperty=nameWithType> yönteminin davranışını [geçersiz kılan](../../language-reference/keywords/override.md) bir `Name` [özelliğine](../../properties.md) ve bir `ToString` [yöntemine](../../methods.md)sahip `Vegetable` bir [sınıf](../../programming-guide/classes-and-structs/classes.md) veri türü tanımladık.</span><span class="sxs-lookup"><span data-stu-id="86af3-133">In the following example, we first define a [class](../../programming-guide/classes-and-structs/classes.md) data type `Vegetable` that has a `Name` [property](../../properties.md) and a `ToString` [method](../../methods.md), which [overrides](../../language-reference/keywords/override.md) the behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="86af3-134">[`public` erişim değiştiricisi](../../language-reference/keywords/public.md) , bu yöntemi bir `Vegetable` örneğinin dize gösterimini almak için herhangi bir istemci kodu için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="86af3-134">The [`public` access modifier](../../language-reference/keywords/public.md) makes that method available to any client code to get the string representation of a `Vegetable` instance.</span></span> <span data-ttu-id="86af3-135">Örnekte `Vegetable.ToString` yöntemi `Vegetable` [oluşturucusunda](../../programming-guide/classes-and-structs/constructors.md)başlatılan `Name` özelliğinin değerini döndürür:</span><span class="sxs-lookup"><span data-stu-id="86af3-135">In the example the `Vegetable.ToString` method returns the value of the `Name` property that is initialized at the `Vegetable` [constructor](../../programming-guide/classes-and-structs/constructors.md):</span></span>

```csharp
public Vegetable(string name) => Name = name;
```

<span data-ttu-id="86af3-136">Daha sonra, [`new` işlecini](../../language-reference/operators/new-operator.md) kullanarak `item` adlı `Vegetable` sınıfının bir örneğini oluşturur ve Oluşturucu `Vegetable` için bir ad sağlar:</span><span class="sxs-lookup"><span data-stu-id="86af3-136">Then we create an instance of the `Vegetable` class named `item` by using the [`new` operator](../../language-reference/operators/new-operator.md) and providing a name for the constructor `Vegetable`:</span></span>

```csharp
var item = new Vegetable("eggplant");
```

<span data-ttu-id="86af3-137">Son olarak, `item` değişkenini Ayrıca bir <xref:System.DateTime> değeri, bir <xref:System.Decimal> değeri ve `Unit` [numaralandırma](../../programming-guide/enumeration-types.md) değeri içeren bir ara değerli dizeye dahil ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="86af3-137">Finally, we include the `item` variable into an interpolated string that also contains a <xref:System.DateTime> value, a <xref:System.Decimal> value, and a `Unit` [enumeration](../../programming-guide/enumeration-types.md) value.</span></span> <span data-ttu-id="86af3-138">Düzenleyicinizdeki tüm C# kodu aşağıdaki kodla değiştirin ve ardından çalıştırmak için `dotnet run` komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="86af3-138">Replace all of the C# code in your editor with the following code, and then use the `dotnet run` command to run it:</span></span>

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;

   public string Name { get; }

   public override string ToString() => Name;
}

public class Program
{
   public enum Unit { item, kilogram, gram, dozen };

   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```

<span data-ttu-id="86af3-139">Enterpolasyonlu dizedeki enterpolasyon ifadesinin `item`, sonuç dizesinde "eggbitki" metni olarak çözümlendiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="86af3-139">Note that the interpolation expression `item` in the interpolated string resolves to the text "eggplant" in the result string.</span></span> <span data-ttu-id="86af3-140">Yani, ifade sonucunun türü bir dize olmadığında, sonuç aşağıdaki şekilde bir dizeye çözülür:</span><span class="sxs-lookup"><span data-stu-id="86af3-140">That's because, when the type of the expression result is not a string, the result is resolved to a string in the following way:</span></span>

- <span data-ttu-id="86af3-141">Enterpolasyon ifadesi `null` olarak değerlendirilirse, boş bir dize ("" veya <xref:System.String.Empty?displayProperty=nameWithType>) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86af3-141">If the interpolation expression evaluates to `null`, an empty string ("", or <xref:System.String.Empty?displayProperty=nameWithType>) is used.</span></span>

- <span data-ttu-id="86af3-142">Enterpolasyon ifadesi `null` olarak değerlendirilmiyorsa, genellikle sonuç türünün `ToString` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="86af3-142">If the interpolation expression doesn't evaluate to `null`, typically the `ToString` method of the result type is called.</span></span> <span data-ttu-id="86af3-143">`Vegetable.ToString` yönteminin uygulamasını güncelleştirerek bunu test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86af3-143">You can test this by updating the implementation of the `Vegetable.ToString` method.</span></span> <span data-ttu-id="86af3-144">Her tür bu yöntemin bir uygulaması olduğundan `ToString` yöntemini uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="86af3-144">You might not even need to implement the `ToString` method since every type has some implementation of this method.</span></span> <span data-ttu-id="86af3-145">Bunu test etmek için örnekteki `Vegetable.ToString` yönteminin tanımını (bunu yapmak için, bir açıklama simgesi koyun `//`, önüne ekleyin).</span><span class="sxs-lookup"><span data-stu-id="86af3-145">To test this, comment out the definition of the `Vegetable.ToString` method in the example (to do that, put a comment symbol, `//`, in front of it).</span></span> <span data-ttu-id="86af3-146">Çıktıda, "eggbitki" dizesi, <xref:System.Object.ToString?displayProperty=nameWithType> yönteminin varsayılan davranışı olan tam nitelikli tür adı (Bu örnekteki "Vegetable") ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="86af3-146">In the output, the string "eggplant" is replaced by the fully qualified type name ("Vegetable" in this example), which is the default behavior of the <xref:System.Object.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="86af3-147">Bir numaralandırma değeri için `ToString` yönteminin varsayılan davranışı değerin dize gösterimini döndürmektir.</span><span class="sxs-lookup"><span data-stu-id="86af3-147">The default behavior of the `ToString` method for an enumeration value is to return the string representation of the value.</span></span>

<span data-ttu-id="86af3-148">Bu örnekteki çıktıda, tarih çok kesin (eggbitki fiyatı her saniye değişmez) ve fiyat değeri bir para birimi göstermez.</span><span class="sxs-lookup"><span data-stu-id="86af3-148">In the output from this example, the date is too precise (the price of eggplant doesn't change every second), and the price value doesn't indicate a unit of currency.</span></span> <span data-ttu-id="86af3-149">Sonraki bölümde, ifade sonuçlarının dize temsillerini biçimini denetleyerek bu sorunları nasıl düzelteceğinizi öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="86af3-149">In the next section, you'll learn how to fix those issues by controlling the format of string representations of the expression results.</span></span>

## <a name="control-the-formatting-of-interpolation-expressions"></a><span data-ttu-id="86af3-150">Enterpolasyon ifadelerinin biçimlendirmesini denetleme</span><span class="sxs-lookup"><span data-stu-id="86af3-150">Control the formatting of interpolation expressions</span></span>

<span data-ttu-id="86af3-151">Önceki bölümde, sonuç dizesine hatalı biçimli iki dize eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="86af3-151">In the previous section, two poorly formatted strings were inserted into the result string.</span></span> <span data-ttu-id="86af3-152">Bunlardan biri, yalnızca tarihin uygun olduğu tarih ve saat değeridir.</span><span class="sxs-lookup"><span data-stu-id="86af3-152">One was a date and time value for which only the date was appropriate.</span></span> <span data-ttu-id="86af3-153">İkincisi, para birimi birimini göstermediğiniz bir fiyattır.</span><span class="sxs-lookup"><span data-stu-id="86af3-153">The second was a price that didn't indicate its unit of currency.</span></span> <span data-ttu-id="86af3-154">Her iki sorunun de kolay bir şekilde ele alınır.</span><span class="sxs-lookup"><span data-stu-id="86af3-154">Both issues are easy to address.</span></span> <span data-ttu-id="86af3-155">Dize ilişkilendirme, belirli türlerin biçimlendirilmesini denetleyen *Biçim dizelerini* belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="86af3-155">String interpolation lets you specify *format strings* that control the formatting of particular types.</span></span> <span data-ttu-id="86af3-156">Aşağıdaki satırda gösterildiği gibi, tarih ve fiyat ifadelerinin biçim dizelerini dahil etmek için önceki örnekteki `Console.WriteLine` çağrısını değiştirin:</span><span class="sxs-lookup"><span data-stu-id="86af3-156">Modify the call to `Console.WriteLine` from the previous example to include the format strings for the date and price expressions as shown in the following line:</span></span>

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```

<span data-ttu-id="86af3-157">Bir biçim dizesini, iki nokta üst üste (":") ve biçim dizesiyle birlikte enterpolasyon ifadesini izleyerek belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86af3-157">You specify a format string by following the interpolation expression with a colon (":") and the format string.</span></span> <span data-ttu-id="86af3-158">"d", kısa tarih biçimini temsil eden [Standart bir tarih ve saat biçim dizesidir](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) .</span><span class="sxs-lookup"><span data-stu-id="86af3-158">"d" is a [standard date and time format string](../../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier) that represents the short date format.</span></span> <span data-ttu-id="86af3-159">"C2", ondalık ayırıcıdan sonraki iki basamakla para birimi değeri olarak bir sayıyı temsil eden [Standart bir sayısal biçim dizesidir](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) .</span><span class="sxs-lookup"><span data-stu-id="86af3-159">"C2" is a  [standard numeric format string](../../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier) that represents a number as a currency value with two digits after the decimal point.</span></span>

<span data-ttu-id="86af3-160">.NET kitaplıklarında bulunan birçok tür, önceden tanımlanmış bir biçim dizeleri kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="86af3-160">A number of types in the .NET libraries support a predefined set of format strings.</span></span> <span data-ttu-id="86af3-161">Bunlar, tüm sayısal türleri ve Tarih ve saat türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="86af3-161">These include all the numeric types and the date and time types.</span></span> <span data-ttu-id="86af3-162">Biçim dizelerini destekleyen türlerin tüm listesi için bkz. [.net makalesindeki biçimlendirme türleri](../../../standard/base-types/formatting-types.md) ' nde [Biçim dizeleri ve .NET sınıf kitaplığı türleri](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) .</span><span class="sxs-lookup"><span data-stu-id="86af3-162">For a complete list of types that support format strings, see [Format Strings and .NET Class Library Types](../../../standard/base-types/formatting-types.md#format-strings-and-net-types) in the [Formatting Types in .NET](../../../standard/base-types/formatting-types.md) article.</span></span>

<span data-ttu-id="86af3-163">Metin düzenleyicinizdeki biçim dizelerini değiştirmeyi deneyin ve her değişiklik yaptığınızda, değişikliklerin tarih ve saat ve sayısal değer biçimlendirmesini nasıl etkilediğini görmek için programı yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="86af3-163">Try modifying the format strings in your text editor and, each time you make a change, rerun the program to see how the changes affect the formatting of the date and time and the numeric value.</span></span> <span data-ttu-id="86af3-164">`{date:d}` içindeki "d" öğesini "t" olarak değiştirin (kısa saat biçimini göstermek için), "y" (yılı ve ayı göstermek için) ve "yyyy" (yılı dört basamaklı bir sayı olarak göstermek için).</span><span class="sxs-lookup"><span data-stu-id="86af3-164">Change the "d" in `{date:d}` to "t" (to display the short time format), "y" (to display the year and month), and "yyyy" (to display the year as a four-digit number).</span></span> <span data-ttu-id="86af3-165">`{price:C2}` içindeki "C2" öğesini "e" (üstel gösterim için) ve "F3" (ondalık ayırıcıdan sonra üç basamaklı bir sayısal değer için) olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="86af3-165">Change the "C2" in `{price:C2}` to "e" (for exponential notation) and "F3" (for a numeric value with three digits after the decimal point).</span></span>

<span data-ttu-id="86af3-166">Biçimlendirmeyi denetlemenin yanı sıra, sonuç dizesinde bulunan biçimlendirilmiş dizelerin alan genişliğini ve hizalamasını da denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86af3-166">In addition to controlling formatting, you can also control the field width and alignment of the formatted strings that are included in the result string.</span></span> <span data-ttu-id="86af3-167">Sonraki bölümde bunu nasıl yapacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="86af3-167">In the next section, you'll learn how to do this.</span></span>

## <a name="control-the-field-width-and-alignment-of-interpolation-expressions"></a><span data-ttu-id="86af3-168">Enterpolasyon ifadelerinin alan genişliğini ve hizalamasını denetleme</span><span class="sxs-lookup"><span data-stu-id="86af3-168">Control the field width and alignment of interpolation expressions</span></span>

<span data-ttu-id="86af3-169">Genellikle, bir enterpolasyon ifadesinin sonucu dize olarak biçimlendirildiğinde, bu dize öndeki veya sondaki boşluklar olmadan bir sonuç dizesine dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="86af3-169">Ordinarily, when the result of an interpolation expression is formatted to string, that string is included in a result string without leading or trailing spaces.</span></span> <span data-ttu-id="86af3-170">Özellikle bir veri kümesiyle çalışırken, alan genişliğini denetleyebilmekte ve metin hizalaması daha okunabilir bir çıktı oluşturulmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="86af3-170">Particularly when you work with a set of data, being able to control a field width and text alignment helps to produce a more readable output.</span></span> <span data-ttu-id="86af3-171">Bunu görmek için, metin düzenleyicinizdeki tüm kodu aşağıdaki kodla değiştirin ve ardından `dotnet run` yazarak programı yürütün:</span><span class="sxs-lookup"><span data-stu-id="86af3-171">To see this, replace all the code in your text editor with the following code, then type `dotnet run` to execute the program:</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>()
      {
          ["Doyle, Arthur Conan"] = "Hound of the Baskervilles, The",
          ["London, Jack"] = "Call of the Wild, The",
          ["Shakespeare, William"] = "Tempest, The"
      };

      Console.WriteLine("Author and Title List");
      Console.WriteLine();
      Console.WriteLine($"|{"Author",-25}|{"Title",30}|");
      foreach (var title in titles)
         Console.WriteLine($"|{title.Key,-25}|{title.Value,30}|");
   }
}
```

<span data-ttu-id="86af3-172">Yazarların adları sola hizalanır ve yazdığı başlıklar sağa hizalanır.</span><span class="sxs-lookup"><span data-stu-id="86af3-172">The names of authors are left-aligned, and the titles they wrote are right-aligned.</span></span> <span data-ttu-id="86af3-173">Bir ilişkilendirme ifadesinden sonra bir virgül (",") ekleyerek ve *en az* alan genişliğini belirterek hizalamayı belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="86af3-173">You specify the alignment by adding a comma (",") after an interpolation expression and designating the *minimum* field width.</span></span> <span data-ttu-id="86af3-174">Belirtilen değer pozitif bir sayıysa, alan sağa hizalanır.</span><span class="sxs-lookup"><span data-stu-id="86af3-174">If the specified value is a positive number, the field is right-aligned.</span></span> <span data-ttu-id="86af3-175">Negatif bir sayı ise, alan sola hizalanır.</span><span class="sxs-lookup"><span data-stu-id="86af3-175">If it is a negative number, the field is left-aligned.</span></span>

<span data-ttu-id="86af3-176">`{"Author",-25}` ve `{title.Key,-25}` koddan negatif işaretlerini kaldırmayı deneyin ve aşağıdaki kod olduğu gibi örneği yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="86af3-176">Try removing the negative signs from the `{"Author",-25}` and `{title.Key,-25}` code and run the example again, as the following code does:</span></span>

```csharp
Console.WriteLine($"|{"Author",25}|{"Title",30}|");
foreach (var title in titles)
   Console.WriteLine($"|{title.Key,25}|{title.Value,30}|");
```

<span data-ttu-id="86af3-177">Bu kez, yazar bilgileri sağa hizalanır.</span><span class="sxs-lookup"><span data-stu-id="86af3-177">This time, the author information is right-aligned.</span></span>

<span data-ttu-id="86af3-178">Tek bir ilişkilendirme ifadesi için bir hizalama belirleyicisi ve biçim dizesi birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86af3-178">You can combine an alignment specifier and a format string for a single interpolation expression.</span></span> <span data-ttu-id="86af3-179">Bunu yapmak için önce hizalamayı, ardından iki nokta üst üste ve biçim dizesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="86af3-179">To do that, specify the alignment first, followed by a colon and the format string.</span></span> <span data-ttu-id="86af3-180">`Main` yöntemi içindeki tüm kodu, tanımlı alan genişlikleri olan üç biçimli dizeyi görüntüleyen aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="86af3-180">Replace all of the code inside the `Main` method with the following code, which displays three formatted strings with defined field widths.</span></span> <span data-ttu-id="86af3-181">Ardından `dotnet run` komutunu girerek programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="86af3-181">Then run the program by entering the `dotnet run` command.</span></span>

```csharp
Console.WriteLine($"[{DateTime.Now,-20:d}] Hour [{DateTime.Now,-10:HH}] [{1063.342,15:N2}] feet");
```

<span data-ttu-id="86af3-182">Çıktı aşağıdakine benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="86af3-182">The output looks something like the following:</span></span>

```console
[04/14/2018          ] Hour [16        ] [       1,063.34] feet
```

<span data-ttu-id="86af3-183">Dize ilişkilendirme öğreticisini tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="86af3-183">You've completed the string interpolation tutorial.</span></span>

<span data-ttu-id="86af3-184">Daha fazla bilgi için bkz. [dize ilişkilendirme](../../language-reference/tokens/interpolated.md) konusu ve öğreticide [dize ilişkilendirme C# ](../../tutorials/string-interpolation.md) .</span><span class="sxs-lookup"><span data-stu-id="86af3-184">For more information, see the [String interpolation](../../language-reference/tokens/interpolated.md) topic and the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>
