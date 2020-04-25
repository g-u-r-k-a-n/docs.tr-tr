---
title: .NET 'te karakter kodlamaya giriş
description: .NET 'te karakter kodlama ve kod çözme hakkında bilgi edinin.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 086430a720e6dc7f39d459a4b99d5bbdb1cfcac3
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141300"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="c3418-103">.NET içinde karakter kodlaması</span><span class="sxs-lookup"><span data-stu-id="c3418-103">Character encoding in .NET</span></span>

<span data-ttu-id="c3418-104">Bu makalede, .NET tarafından kullanılan karakter kodlama sistemlerine giriş sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c3418-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="c3418-105">Makalesinde <xref:System.String>, <xref:System.Char> <xref:System.Text.Rune>,, ve <xref:System.Globalization.StringInfo> türlerinin Unicode, UTF-16 ve UTF-8 ile nasıl çalıştığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c3418-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="c3418-106">Bu *karakter* , *bir okuyucunun tek bir görüntüleme öğesi olarak beyin bir*genel anlamda burada kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3418-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="c3418-107">Ortak örnekler, "a", "@" simgesi ve Emoji "🐂" harftir.</span><span class="sxs-lookup"><span data-stu-id="c3418-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="c3418-108">Bazı durumlarda, [grafem kümelerindeki](#grapheme-clusters) bölümünde açıklanan bir karakter aslında birden çok bağımsız görüntüleme öğelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="c3418-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-string-and-char-types"></a><span data-ttu-id="c3418-109">Dize ve karakter türleri</span><span class="sxs-lookup"><span data-stu-id="c3418-109">The string and char types</span></span>

<span data-ttu-id="c3418-110">[String](xref:System.String) sınıfının bir örneği bazı metinleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c3418-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="c3418-111">, `string` Her biri [char](xref:System.Char) yapısının bir örneği olan 16 bit değerlerden oluşan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="c3418-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="c3418-112">[Dize. Length](xref:System.String.Length) özelliği, `char` `string` örnekteki örneklerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3418-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="c3418-113">Aşağıdaki örnek işlev, içindeki tüm `char` örneklerin onaltılı gösterimindeki değerleri yazdırır: `string`</span><span class="sxs-lookup"><span data-stu-id="c3418-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

<span data-ttu-id="c3418-114">"Hello" dizesini bu işleve geçirin ve aşağıdaki çıktıyı alın:</span><span class="sxs-lookup"><span data-stu-id="c3418-114">Pass the string "Hello" to this function, and you get the following output:</span></span>

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

<span data-ttu-id="c3418-115">Her karakter tek `char` bir değerle temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-115">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="c3418-116">Bu kalıp, dünyanın çoğu dili için geçerli bir değer içerir.</span><span class="sxs-lookup"><span data-stu-id="c3418-116">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="c3418-117">Örneğin, *nǐ hǎo* ve " *Hello*" gibi sesli iki Çince karakterin çıktısı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c3418-117">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="c3418-118">Ancak bazı dillerde ve bazı semboller ve Emoji için tek bir karakteri temsil eden iki `char` örnek sürer.</span><span class="sxs-lookup"><span data-stu-id="c3418-118">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="c3418-119">Örneğin, sözcükteki karakter ve `char` örnekleri, Ozu dilinde kullanılacak şekilde *Osage* karşılaştırın:</span><span class="sxs-lookup"><span data-stu-id="c3418-119">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

<span data-ttu-id="c3418-120">Yukarıdaki örnekte, boşluk hariç her bir karakter iki `char` örnek tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-120">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="c3418-121">Tek bir Unicode emoji Ayrıca, aşağıdaki örnekte görüldüğü `char`gibi bir Ox emoji gösterildiği gibi iki s tarafından da temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="c3418-121">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="c3418-122">Bu örnekler `string.Length`, `char` örnek sayısını gösteren değerinin, görüntülenen karakter sayısını belirtmesinin gerekli olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3418-122">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="c3418-123">Tek `char` bir örnek bir karakteri temsil etmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c3418-123">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="c3418-124">Tek `char` bir karakterle eşlenen çiftler *vekil çiftler*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c3418-124">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="c3418-125">Nasıl çalıştığını anlamak için Unicode ve UTF-16 kodlamasını anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3418-125">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="c3418-126">Unicode kod noktaları</span><span class="sxs-lookup"><span data-stu-id="c3418-126">Unicode code points</span></span>

<span data-ttu-id="c3418-127">Unicode, çeşitli platformlarda ve çeşitli diller ve betiklerle kullanım için uluslararası bir kodlama standardıdır.</span><span class="sxs-lookup"><span data-stu-id="c3418-127">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="c3418-128">Unicode standart 1.100.000 ' den fazla [kod noktasını](https://www.unicode.org/glossary/#code_point)tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c3418-128">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="c3418-129">Kod noktası, 0 ile `U+10FFFF` (ondalık 1.114.111) arasında değişebilir bir tamsayı değeridir.</span><span class="sxs-lookup"><span data-stu-id="c3418-129">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="c3418-130">Bazı kod noktaları harflere, simgelere veya emoji 'ye atanır.</span><span class="sxs-lookup"><span data-stu-id="c3418-130">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="c3418-131">Diğer bir deyişle, yeni bir satıra ilerlemek gibi metin veya karakterlerin nasıl görüntülendiğini denetleyen eylemlere atanır.</span><span class="sxs-lookup"><span data-stu-id="c3418-131">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="c3418-132">Birçok kod noktası henüz atanmadı.</span><span class="sxs-lookup"><span data-stu-id="c3418-132">Many code points are not yet assigned.</span></span>

<span data-ttu-id="c3418-133">Aşağıda göründükleri Unicode grafiklerine yönelik bağlantılarla birlikte kod noktası atamalarından oluşan bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c3418-133">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="c3418-134">Ondalık</span><span class="sxs-lookup"><span data-stu-id="c3418-134">Decimal</span></span>|<span data-ttu-id="c3418-135">Onaltılık</span><span class="sxs-lookup"><span data-stu-id="c3418-135">Hex</span></span>       |<span data-ttu-id="c3418-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3418-136">Example</span></span>|<span data-ttu-id="c3418-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3418-137">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="c3418-138">10</span><span class="sxs-lookup"><span data-stu-id="c3418-138">10</span></span>     | `U+000A` |<span data-ttu-id="c3418-139">Yok</span><span class="sxs-lookup"><span data-stu-id="c3418-139">N/A</span></span>| [<span data-ttu-id="c3418-140">SATıR BESLEME</span><span class="sxs-lookup"><span data-stu-id="c3418-140">LINE FEED</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="c3418-141">65</span><span class="sxs-lookup"><span data-stu-id="c3418-141">65</span></span>     | `U+0061` | <span data-ttu-id="c3418-142">a</span><span class="sxs-lookup"><span data-stu-id="c3418-142">a</span></span> | [<span data-ttu-id="c3418-143">LATIN KÜÇÜK HARF A</span><span class="sxs-lookup"><span data-stu-id="c3418-143">LATIN SMALL LETTER A</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="c3418-144">562</span><span class="sxs-lookup"><span data-stu-id="c3418-144">562</span></span>    | `U+0232` | <span data-ttu-id="c3418-145">Ȳ</span><span class="sxs-lookup"><span data-stu-id="c3418-145">Ȳ</span></span> | [<span data-ttu-id="c3418-146">LATIN BÜYÜK HARF Y WITH MACRON</span><span class="sxs-lookup"><span data-stu-id="c3418-146">LATIN CAPITAL LETTER Y WITH MACRON</span></span>](https://www.unicode.org/charts/PDF/U0180.pdf) |
|<span data-ttu-id="c3418-147">68.675</span><span class="sxs-lookup"><span data-stu-id="c3418-147">68,675</span></span> | `U+10C43`| <span data-ttu-id="c3418-148">𐱃</span><span class="sxs-lookup"><span data-stu-id="c3418-148">𐱃</span></span> | [<span data-ttu-id="c3418-149">ESKI TÜRKIC LETTER ORKHON</span><span class="sxs-lookup"><span data-stu-id="c3418-149">OLD TURKIC LETTER ORKHON AT</span></span>](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|<span data-ttu-id="c3418-150">127.801</span><span class="sxs-lookup"><span data-stu-id="c3418-150">127,801</span></span>| `U+1F339`| <span data-ttu-id="c3418-151">🌹</span><span class="sxs-lookup"><span data-stu-id="c3418-151">🌹</span></span> | [<span data-ttu-id="c3418-152">GÜL emoji</span><span class="sxs-lookup"><span data-stu-id="c3418-152">ROSE emoji</span></span>](https://www.unicode.org/charts/PDF/U1F300.pdf) |

<span data-ttu-id="c3418-153">Kod noktaları, sözdizimi `U+xxxx`kullanılarak geleneksel adlandırılır; burada `xxxx` onaltılık kodlanmış tamsayı değeridir.</span><span class="sxs-lookup"><span data-stu-id="c3418-153">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="c3418-154">Kod noktalarının tam aralığı içinde iki alt Aralık vardır:</span><span class="sxs-lookup"><span data-stu-id="c3418-154">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="c3418-155">`U+0000..U+FFFF`Aralıktaki **temel çok dıllı düzlem (BMP)** .</span><span class="sxs-lookup"><span data-stu-id="c3418-155">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="c3418-156">Bu 16 bit Aralık, dünyanın yazma sistemlerinin çoğunluğunu kapsayacak kadar 65.536 kod noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3418-156">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="c3418-157">Aralıktaki `U+10000..U+10FFFF` **tamamlayıcı kod noktaları** .</span><span class="sxs-lookup"><span data-stu-id="c3418-157">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="c3418-158">Bu 21 bitlik Aralık, daha az bilinen diller ve emojıs gibi diğer amaçlar için kullanılabilen bir milyon ek kod noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3418-158">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="c3418-159">Aşağıdaki diyagramda, BMP ve ek kod noktaları arasındaki ilişki gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c3418-159">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP ve ek kod noktaları":::

## <a name="utf-16-code-units"></a><span data-ttu-id="c3418-161">UTF-16 kod birimleri</span><span class="sxs-lookup"><span data-stu-id="c3418-161">UTF-16 code units</span></span>

<span data-ttu-id="c3418-162">16 bit Unicode dönüştürme biçimi ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)), Unicode kod noktalarını temsil etmek için 16 bit *kod birimi* kullanan bir karakter kodlama sistemidir.</span><span class="sxs-lookup"><span data-stu-id="c3418-162">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="c3418-163">.NET, içindeki metni kodlamak için UTF-16 kullanır `string`.</span><span class="sxs-lookup"><span data-stu-id="c3418-163">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="c3418-164">`char` Örnek, 16 bit kod birimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c3418-164">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="c3418-165">Tek bir 16 bit kod birimi, temel çok dilli düzlemin 16 bit aralığında herhangi bir kod noktasını temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-165">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="c3418-166">Ancak, tamamlayıcı aralıktaki bir kod noktası için iki `char` örnek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c3418-166">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="c3418-167">Vekil çiftleri</span><span class="sxs-lookup"><span data-stu-id="c3418-167">Surrogate pairs</span></span>

<span data-ttu-id="c3418-168">2 16 bitlik değerlerin tek 21 bitlik bir değere çevrilmesi, ' den `U+D800` (Decimal 55.296-57.343), dahil olmak üzere `U+DFFF` , *vekil kod noktaları*adlı özel bir Aralık tarafından kolaylaştırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="c3418-168">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="c3418-169">Aşağıdaki diyagramda, BMP ve vekil kod noktaları arasındaki ilişki gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c3418-169">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP ve vekil kod noktaları":::

<span data-ttu-id="c3418-171">Yüksek bir *yedek* kod noktası (`U+D800..U+DBFF`) hemen sonrasında *düşük bir yedek* kod noktası (`U+DC00..U+DFFF`) olduğunda, Çift, aşağıdaki formül kullanılarak bir ek kod noktası olarak yorumlanır:</span><span class="sxs-lookup"><span data-stu-id="c3418-171">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="c3418-172">Ondalık gösterimi kullanan aynı formül aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c3418-172">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="c3418-173">*Üst* yedek kod noktası, *düşük* bir vekil kod noktasına göre daha yüksek bir sayı değerine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="c3418-173">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="c3418-174">Yüksek yedek kod noktası, tam 21 bit kod noktası aralığının daha yüksek sıralı 11 bitini hesaplamak için kullanıldığından, "yüksek" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c3418-174">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="c3418-175">Düşük yedek kod noktası, alt sıra 10 bitlerini hesaplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3418-175">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="c3418-176">Örneğin, yedek çiftine `0xD83C` `0xDF39` karşılık gelen gerçek kod noktası aşağıdaki şekilde hesaplanır:</span><span class="sxs-lookup"><span data-stu-id="c3418-176">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="c3418-177">Ondalık gösterimi kullanılarak aynı hesaplama aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c3418-177">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="c3418-178">Yukarıdaki örnek, daha önce `"\ud83c\udf39"` bahsedilen `U+1F339 ROSE ('🌹')` kod noktasının UTF-16 kodlaması olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3418-178">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="c3418-179">Unicode skaler değerleri</span><span class="sxs-lookup"><span data-stu-id="c3418-179">Unicode scalar values</span></span>

<span data-ttu-id="c3418-180">[Unicode skaler değeri](https://www.unicode.org/glossary/#unicode_scalar_value) , yedek kod noktalarından başka tüm kod noktalarına başvurur.</span><span class="sxs-lookup"><span data-stu-id="c3418-180">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="c3418-181">Diğer bir deyişle, skaler bir değer bir karakter atanmış veya gelecekte bir karakter atanabilir olan herhangi bir kod noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="c3418-181">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="c3418-182">Burada "karakter", metin veya karakterlerin nasıl görüntülendiğini denetleyen eylemler gibi şeyler içeren bir kod noktasına atanabilecek her şeyi ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c3418-182">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="c3418-183">Aşağıdaki diyagramda skaler değer kod noktaları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c3418-183">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Skaler değerler":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a><span data-ttu-id="c3418-185">Skalar Rune değer olarak tür</span><span class="sxs-lookup"><span data-stu-id="c3418-185">The Rune type as a scalar value</span></span>

<span data-ttu-id="c3418-186">.NET Core 3,0 ile başlayarak, <xref:System.Text.Rune?displayProperty=fullName> tür bir Unicode skaler değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c3418-186">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="c3418-187">**`Rune`.NET Core 2. x veya .NET Framework 4. x sürümünde kullanılamaz.**</span><span class="sxs-lookup"><span data-stu-id="c3418-187">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="c3418-188">`Rune` Oluşturucular, sonuçta elde edilen örneğin geçerli bir Unicode skaler değeri olduğunu doğrular, aksi takdirde bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3418-188">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="c3418-189">Aşağıdaki örnek, giriş geçerli skaler değerleri temsil `Rune` ettiğinden örnekleri başarıyla örnekleyen kodu gösterir:</span><span class="sxs-lookup"><span data-stu-id="c3418-189">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

<span data-ttu-id="c3418-190">Aşağıdaki örnek, bir özel durum oluşturur çünkü kod noktası vekil aralıkta ve bir yedek çiftinin parçası değil:</span><span class="sxs-lookup"><span data-stu-id="c3418-190">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

<span data-ttu-id="c3418-191">Aşağıdaki örnek bir özel durum oluşturur çünkü kod noktası, tamamlayıcı aralığın ötesinde:</span><span class="sxs-lookup"><span data-stu-id="c3418-191">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Rune<span data-ttu-id="c3418-192">Kullanım örneği: harf durumunu değiştirme</span><span class="sxs-lookup"><span data-stu-id="c3418-192"> usage example: changing letter case</span></span>

<span data-ttu-id="c3418-193">Bir ' a `char` sahip olan ve bir vekil çiftten `char` ise, skaler bir değer olan bir kod noktasıyla ÇALıŞTıĞıNı varsayan bir API.</span><span class="sxs-lookup"><span data-stu-id="c3418-193">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="c3418-194">Örneğin, her <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> char birinde ' de çağıran aşağıdaki yöntemi göz önünde bulundurun string:</span><span class="sxs-lookup"><span data-stu-id="c3418-194">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

<span data-ttu-id="c3418-195">`input` string Küçük harfli Deseret harfini `er` içeriyorsa (`𐑉`), bu kod bunu büyük harfe (`𐐡`) dönüştürmez.</span><span class="sxs-lookup"><span data-stu-id="c3418-195">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="c3418-196">Kod, `char.ToUpperInvariant` `U+D801` her yedek kod noktasında ayrı olarak çağırır `U+DC49`.</span><span class="sxs-lookup"><span data-stu-id="c3418-196">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="c3418-197">Ancak `U+D801` kendi kendine küçük harf olarak tanımlamak için yeterli bilgi yok, bu nedenle `char.ToUpperInvariant` tek başına çıkar.</span><span class="sxs-lookup"><span data-stu-id="c3418-197">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="c3418-198">Aynı şekilde işler `U+DC49` .</span><span class="sxs-lookup"><span data-stu-id="c3418-198">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="c3418-199">Sonuç, içindeki `input` string küçük harfli ' 𐑉 ' ' 𐑉 ' değerine dönüştürülmez.</span><span class="sxs-lookup"><span data-stu-id="c3418-199">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="c3418-200">Doğru bir string şekilde büyük harfe dönüştürmek için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="c3418-200">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="c3418-201">Giriş <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> string üzerinde, yineleme `char`yerine çağırın`char`.</span><span class="sxs-lookup"><span data-stu-id="c3418-201">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="c3418-202">`string.ToUpperInvariant` Yöntemi her bir yedek çiftinin her iki bölümüne erişebilir, bu nedenle tüm Unicode kod noktalarını doğru bir şekilde işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-202">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="c3418-203">Aşağıdaki örnekte gösterildiği gibi, UNICODE skaler `Rune` değerlerini `char` örnekler yerine örnekler olarak yineleyin.</span><span class="sxs-lookup"><span data-stu-id="c3418-203">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="c3418-204">`Rune` Örnek geçerli bir Unicode skaler değeri olduğundan, skaler bir değer üzerinde çalışmasını bekleyen API 'lere geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-204">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="c3418-205">Örneğin, aşağıdaki örnekte <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> gösterildiği gibi çağırmak doğru sonuçlar verir:</span><span class="sxs-lookup"><span data-stu-id="c3418-205">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a><span data-ttu-id="c3418-206">Diğer Rune API 'ler</span><span class="sxs-lookup"><span data-stu-id="c3418-206">Other Rune APIs</span></span>

<span data-ttu-id="c3418-207">`Rune` Tür, `char` API 'lerin çoğunun analoglarından sunar.</span><span class="sxs-lookup"><span data-stu-id="c3418-207">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="c3418-208">Örneğin, aşağıdaki yöntemler `char` tür üzerinde statik API 'leri yansıtır:</span><span class="sxs-lookup"><span data-stu-id="c3418-208">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="c3418-209">Bir `Rune` örnekten ham skaler değer almak için <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3418-209">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="c3418-210">Bir `Rune` örneği bir dizi `char`için geri dönüştürmek için veya <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3418-210">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c3418-211">Herhangi bir Unicode skaler değeri tek `char` veya bir vekil çifti tarafından gösterilebilir olduğundan, herhangi bir `Rune` örnek en fazla 2 `char` örnek tarafından temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-211">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="c3418-212">Bir <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> `Rune` örneği göstermek için kaç `char` örnek gerektiğini görmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3418-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="c3418-213">.Net `Rune` türü hakkında daha fazla bilgi için bkz. [ `Rune` API başvurusu](xref:System.Text.Rune).</span><span class="sxs-lookup"><span data-stu-id="c3418-213">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="c3418-214">Grapheme kümeleri</span><span class="sxs-lookup"><span data-stu-id="c3418-214">Grapheme clusters</span></span>

<span data-ttu-id="c3418-215">Tek bir karakter, birden çok kod noktasının birleşiminden kaynaklanabilir. bu nedenle, genellikle "character" yerine kullanılan daha açıklayıcı bir terim [grafem](https://www.unicode.org/glossary/#grapheme_cluster)kümesidir.</span><span class="sxs-lookup"><span data-stu-id="c3418-215">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="c3418-216">.NET 'teki denk terim [metin öğesidir](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="c3418-216">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="c3418-217">"A `string` ", "á" örneklerini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c3418-217">Consider the `string` instances "a", "á".</span></span> <span data-ttu-id="c3418-218">"á" ve "`👩🏽‍🚒`".</span><span class="sxs-lookup"><span data-stu-id="c3418-218">"á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="c3418-219">İşletim sisteminiz, Unicode standardı tarafından belirtildiği gibi bunları işlediğinde, bu `string` örneklerin her biri tek bir metin öğesi veya grafem kümesi olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="c3418-219">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="c3418-220">Ancak son ikisi birden fazla skaler değer kod noktasıyla temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-220">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="c3418-221">" string A", bir skaler değerle temsil edilir ve bir `char` örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="c3418-221">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="c3418-222">" string Á", bir skaler değerle temsil edilir ve bir `char` örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="c3418-222">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* <span data-ttu-id="c3418-223">string "Á", "á" ile aynı görünür, ancak iki skaler değerle temsil edilir ve iki `char` örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="c3418-223">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="c3418-224">Son olarak, string "`👩🏽‍🚒`" dört skaler değer ile temsil edilir ve yedi `char` örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="c3418-224">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="c3418-225">`U+1F469 WOMAN`(tamamlayıcı Aralık, yedek çifti gerektirir)</span><span class="sxs-lookup"><span data-stu-id="c3418-225">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="c3418-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(tamamlayıcı Aralık, yedek çifti gerektirir)</span><span class="sxs-lookup"><span data-stu-id="c3418-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="c3418-227">`U+1F692 FIRE ENGINE`(tamamlayıcı Aralık, yedek çifti gerektirir)</span><span class="sxs-lookup"><span data-stu-id="c3418-227">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="c3418-228">Önceki örneklerde, örneğin, vurgulu vurgu değiştiricisi veya kaplama tonu değiştiricisi gibi-kod noktası ekranda tek başına bir öğe olarak görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="c3418-228">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="c3418-229">Bunun yerine, daha önce gelen bir metin öğesinin görünümünü değiştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3418-229">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="c3418-230">Bu örnekler, tek bir "karakter" veya "grapheme kümesi" olarak düşündüğimizi oluşturmak için birden çok skalar değer alıp verebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3418-230">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="c3418-231">Bir a `string`'nın grafem kümelerini numaralandırmak için aşağıdaki örnekte gösterildiği <xref:System.Globalization.StringInfo> gibi sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3418-231">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="c3418-232">Swift hakkında bilginiz varsa, .NET `StringInfo` türü [Swift 'ın `character` tipine](https://developer.apple.com/documentation/swift/character)benzer.</span><span class="sxs-lookup"><span data-stu-id="c3418-232">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a><span data-ttu-id="c3418-233">Örnek: Count char, Rune, ve metin öğesi örnekleri</span><span class="sxs-lookup"><span data-stu-id="c3418-233">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="c3418-234">.NET API 'lerinde, bir grafem kümesine *metin öğesi*denir.</span><span class="sxs-lookup"><span data-stu-id="c3418-234">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="c3418-235">Aşağıdaki yöntem, `char` `Rune`, ve içindeki metin öğesi örnekleri arasındaki farkları göstermektedir `string`:</span><span class="sxs-lookup"><span data-stu-id="c3418-235">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

<span data-ttu-id="c3418-236">Bu kodu .NET Framework veya .NET Core 3,1 veya önceki sürümlerde çalıştırırsanız, emoji için metin öğesi sayısı gösterilir `4`.</span><span class="sxs-lookup"><span data-stu-id="c3418-236">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="c3418-237">Bunun nedeni, .NET 5 ' te düzeltilen `StringInfo` sınıftaki bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="c3418-237">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-opno-locstring-instances"></a><span data-ttu-id="c3418-238">Örnek: örnekleri string bölme</span><span class="sxs-lookup"><span data-stu-id="c3418-238">Example: splitting string instances</span></span>

<span data-ttu-id="c3418-239">Örnekleri bölrken `string` , vekil çiftleri ve grafem kümelerini bölmemeye özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="c3418-239">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="c3418-240">Aşağıdaki hatalı kod örneğini göz önünde bulundurun. Bu, her 10 karakterden oluşan satır sonlarını bir stringaraya eklemeyi amaçlar:</span><span class="sxs-lookup"><span data-stu-id="c3418-240">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

<span data-ttu-id="c3418-241">Bu kod örnekleri numaralandırdığından `char` , Straddle bir 10`char` sınır olarak gerçekleşen bir yedek çift bölünecektir ve aralarında bir yeni satır eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-241">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="c3418-242">Bu ekleme veri bozulması sunarak, vekil kod noktaları yalnızca çiftler olarak anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="c3418-242">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="c3418-243">Örnekler yerine `Rune` `char` örnekleri (skaler değerler) numaralandırdıysanız veri bozulması olasılığı ortadan kalkar.</span><span class="sxs-lookup"><span data-stu-id="c3418-243">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="c3418-244">Bir dizi `Rune` örnek, 10`char` sınırını izleyen bir grafem kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3418-244">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="c3418-245">Grafem kümesi ayarlandıysa, doğru yorumlanamaz.</span><span class="sxs-lookup"><span data-stu-id="c3418-245">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="c3418-246">Aşağıdaki örnekte olduğu gibi, grafem kümelerini veya metin öğelerini sayarak daha iyi bir yaklaşım vardır string :</span><span class="sxs-lookup"><span data-stu-id="c3418-246">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

<span data-ttu-id="c3418-247">Ancak daha önce belirtildiği gibi, .NET 5 dışındaki .NET uygulamalarında, `StringInfo` sınıfı bazı grafem kümelerini yanlış işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-247">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="c3418-248">UTF-8 ve UTF-32</span><span class="sxs-lookup"><span data-stu-id="c3418-248">UTF-8 and UTF-32</span></span>

<span data-ttu-id="c3418-249">Önceki bölümlerde, .NET 'in örnekleri kodlamak `string` için KULLANDıĞı, UTF-16 ' a odaklanan bölümler vardır.</span><span class="sxs-lookup"><span data-stu-id="c3418-249">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="c3418-250">Unicode- [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) ve [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)için başka kodlama sistemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="c3418-250">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="c3418-251">Bu kodlamalar sırasıyla 8 bit kod birimleri ve 32 bit kod birimleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="c3418-251">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="c3418-252">UTF-16 gibi, UTF-8, bazı Unicode skaler değerleri temsil etmek için birden çok kod birimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c3418-252">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="c3418-253">UTF-32, tek bir 32 bit kod biriminde herhangi bir skaler değeri temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-253">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="c3418-254">Bu üç Unicode kodlama sisteminin her birinde aynı Unicode kod noktasının nasıl temsil edileceğini gösteren bazı örnekler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c3418-254">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

<span data-ttu-id="c3418-255">Daha önce belirtildiği gibi, bir [vekil çiftin](#surrogate-pairs) tek bir UTF-16 kod birimi kendi kendine daha az anlamlı olur.</span><span class="sxs-lookup"><span data-stu-id="c3418-255">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="c3418-256">Aynı şekilde, tek bir UTF-8 kod birimi, skalar bir değeri hesaplamak için kullanılan iki, üç veya dört dizilirse, kendisini anlamlı hale gelir.</span><span class="sxs-lookup"><span data-stu-id="c3418-256">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="c3418-257">Endian</span><span class="sxs-lookup"><span data-stu-id="c3418-257">Endianness</span></span>

<span data-ttu-id="c3418-258">.NET ' te, UTF-16 kod birimleri string , 16 bit tamsayılar (`char` örnekler) dizisi olarak bitişik bellekte depolanır.</span><span class="sxs-lookup"><span data-stu-id="c3418-258">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="c3418-259">Bağımsız kod birimlerinin bitleri geçerli mimarinin [bitimcisine](https://en.wikipedia.org/wiki/Endianness) göre düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="c3418-259">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="c3418-260">Küçük endian mimarisinde, UTF-16 kod string noktalarından `[ D801 DCCC ]` oluşan bir tanesi bayt `[ 0x01, 0xD8, 0xCC, 0xDC ]`olarak bellekte düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="c3418-260">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="c3418-261">Aynı büyüklükte bir mimaride, bayt string `[ 0xD8, 0x01, 0xDC, 0xCC ]`olarak bellekte aynı şekilde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="c3418-261">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="c3418-262">Birbirleriyle iletişim kuran bilgisayar sistemleri, kablo ile kesişen verilerin gösterimini kabul etmelidir.</span><span class="sxs-lookup"><span data-stu-id="c3418-262">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="c3418-263">Çoğu ağ protokolü, metin aktarırken bir standart olarak UTF-8 kullanır, kısmen de az endian bir makineyle iletişim kuran büyük endian makinesinden kaynaklanan sorunlardan kaçınmaktır.</span><span class="sxs-lookup"><span data-stu-id="c3418-263">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="c3418-264">UTF string -8 kod noktalarından `[ F0 90 93 8C ]` oluşan bir işlem, her zaman bitime yönteminden bağımsız olarak `[ 0xF0, 0x90, 0x93, 0x8C ]` bayt olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-264">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="c3418-265">Metin aktarmak için UTF-8 ' i kullanmak için, .NET uygulamaları genellikle aşağıdaki örnek gibi bir kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="c3418-265">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="c3418-266">Önceki örnekte, [. UTF8. GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) YÖNTEMI, UTF-16 `string` ' ı bir dizi Unicode skaler değere geri çözer, ardından bu skaler değerleri UTF-8 ' e yeniden kodlar ve sonuç sırasını bir `byte` diziye koyar.</span><span class="sxs-lookup"><span data-stu-id="c3418-266">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="c3418-267">[Encoding. UTF8. GetString](xref:System.Text.UTF8Encoding.GetString%2A) yöntemi, bir UTF-8 `byte` dizisini UTF-16 `string`' a dönüştürerek ters dönüştürmeyi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c3418-267">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="c3418-268">UTF-8 internet 'te ortak olduğundan, ham baytları kablolu olarak okumak ve verileri UTF-8 gibi değerlendirmek mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-268">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="c3418-269">Ancak, gerçekten doğru biçimlendirildiğini doğrulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c3418-269">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="c3418-270">Kötü amaçlı bir istemci, hizmetinize hatalı biçimlendirilmiş UTF-8 gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-270">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="c3418-271">Doğru biçimlendirilmiş gibi bu veriler üzerinde işlem yaparsanız, uygulamanızda hatalara veya güvenlik delikleri oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-271">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="c3418-272">UTF-8 verilerini doğrulamak için, gibi `Encoding.UTF8.GetString`bir yöntemi kullanabilirsiniz. Bu, gelen verileri bir `string`öğesine dönüştürürken doğrulama işlemi gerçekleştirecek.</span><span class="sxs-lookup"><span data-stu-id="c3418-272">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="c3418-273">İyi biçimlendirilmiş kodlama</span><span class="sxs-lookup"><span data-stu-id="c3418-273">Well-formed encoding</span></span>

<span data-ttu-id="c3418-274">İyi biçimlendirilmiş bir Unicode kodlaması, belirsiz bir string şekilde çözülemeyen ve bir Unicode skaler değerler dizisine hatasız bir şekilde kodu oluşturulan kod birimleridir.</span><span class="sxs-lookup"><span data-stu-id="c3418-274">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="c3418-275">İyi biçimlendirilmiş veriler UTF-8, UTF-16 ve UTF-32 arasında serbestçe dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-275">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="c3418-276">Bir kodlama sırasının doğru biçimlendirilmiş olup olmadığı ve bir makinenin mimarisinin BİTİLMESİ ile ilgisi olmadığı hakkında soru.</span><span class="sxs-lookup"><span data-stu-id="c3418-276">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="c3418-277">Hatalı biçimlendirilmiş bir UTF-8 sırası, büyük endian ve az endian makinelerde aynı şekilde hatalı biçimlendirilmiş bir dizelerdir.</span><span class="sxs-lookup"><span data-stu-id="c3418-277">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="c3418-278">Hatalı biçimlendirilmiş kodlamalar örnekleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c3418-278">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="c3418-279">UTF-8 ' de, izleyen `[ 6C C2 61 ]` sıra hatalı biçimlendirilmiş `C2` `61`.</span><span class="sxs-lookup"><span data-stu-id="c3418-279">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="c3418-280">UTF-16 ' da, dizi `[ DC00 DD00 ]` ( string `"\udc00\udd00"`veya C# ' ta) hatalı biçimlendirilmiş olduğundan düşük vekil `DC00` başka bir düşük yedek `DD00`tarafından izlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="c3418-280">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="c3418-281">UTF-32 ' de, dizi `[ 0011ABCD ]` , Unicode skaler değerler aralığının `0011ABCD` dışında olduğundan, sıra hatalı biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="c3418-281">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="c3418-282">.NET sürümünde `string` örnekler neredeyse her zaman ıyı biçimlendirilmiş UTF-16 verileri içerir, ancak bu garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="c3418-282">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="c3418-283">Aşağıdaki örneklerde, `string` örneklerde hatalı biçimlendirilmiş UTF-16 verileri oluşturan geçerli C# kodu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c3418-283">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="c3418-284">Hatalı biçimlendirilmiş değişmez değer:</span><span class="sxs-lookup"><span data-stu-id="c3418-284">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="c3418-285">Bir vekil çifti ayıran alt dize:</span><span class="sxs-lookup"><span data-stu-id="c3418-285">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="c3418-286">Hiçbir şekilde [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) hatalı oluşturulmuş `string` örnekler döndürmeyen API 'ler.</span><span class="sxs-lookup"><span data-stu-id="c3418-286">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="c3418-287">`Encoding.GetString`ve `Encoding.GetBytes` yöntemleri, girişte hatalı biçimlendirilmiş dizileri tespit edin ve çıkış oluştururken karakter değiştirme işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c3418-287">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="c3418-288">Örneğin, girişte ASCII [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) olmayan bir bayt görürseniz (U + 0000.. U + 007F aralığı dışında), döndürülen `string` örneğe bir '? ' ekler.</span><span class="sxs-lookup"><span data-stu-id="c3418-288">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="c3418-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)Hatalı biçimlendirilmiş UTF-8 dizilerini döndürülen `U+FFFD REPLACEMENT CHARACTER ('�')` `string` örnekteki ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c3418-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="c3418-290">Daha fazla bilgi için bkz. [Unicode standart](https://www.unicode.org/versions/latest/), Bölüm 5,22 ve 3,9.</span><span class="sxs-lookup"><span data-stu-id="c3418-290">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="c3418-291">Yerleşik `Encoding` sınıflar, hatalı biçimlendirilmiş diziler görüldüğünde karakter değişimi gerçekleştirmek yerine bir özel durum oluşturmak için de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c3418-291">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="c3418-292">Bu yaklaşım, genellikle karakter değiştirme 'nin kabul edilebilir olabileceği güvenliğe duyarlı uygulamalarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c3418-292">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="c3418-293">Yerleşik `Encoding` sınıfların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.net 'te karakter kodlama sınıfları kullanma](character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="c3418-293">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3418-294">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3418-294">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="c3418-295">Genelleştirme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="c3418-295">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
