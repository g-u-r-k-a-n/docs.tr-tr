---
title: Standart sayısal biçim dizeleri
description: Bu makalede, standart sayısal biçim dizelerini .NET 'teki metin temsillerine biçimlendirmek için standart sayısal biçim dizeleri kullanmayı öğrenin.
ms.date: 06/10/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET]
- formatting [.NET], numbers
- standard format strings, numeric
- format strings
- numbers [.NET], formatting
- format specifiers, numeric
- standard numeric format strings
- formatting numbers [.NET]
- format specifiers, standard numeric format strings
ms.openlocfilehash: e5e1aa16d8df3d0cfce6dac00c91ca8e99e16e3d
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888977"
---
# <a name="standard-numeric-format-strings"></a>Standart sayısal biçim dizeleri

Standart sayısal biçim dizeleri, genel sayısal türleri biçimlendirmek için kullanılır. Standart bir sayısal biçim dizesi formu alır `Axx` , burada:

- `A` , *Biçim belirleyicisi* olarak adlandırılan tek bir alfabetik karakterdir. Beyaz boşluk da dahil olmak üzere birden fazla alfabetik karakter içeren herhangi bir sayısal biçim dizesi, özel bir sayısal biçim dizesi olarak yorumlanır. Daha fazla bilgi için bkz. [özel sayısal biçim dizeleri](custom-numeric-format-strings.md).

- `xx`*duyarlık belirleyicisi* olarak adlandırılan isteğe bağlı bir tamsayıdır. Precision belirleyici 0'dan 99'a kadar uzanır ve sonuç basamak sayısını etkiler. Duyarlık belirticisinin bir sayının dize temsilindeki basamak sayısını denetlediğine unutmayın. Sayının kendisini yuvarlamaz. Bir yuvarlama işlemi gerçekleştirmek için, <xref:System.Math.Ceiling%2A?displayProperty=nameWithType> <xref:System.Math.Floor%2A?displayProperty=nameWithType> veya <xref:System.Math.Round%2A?displayProperty=nameWithType> yöntemini kullanın.

  *Duyarlık belirtici* , sonuç dizesindeki kesirli basamakların sayısını denetliyorsa, sonuç dizesi sonsuz kesin sonuca en yakın bir gösterilebilir tablo sonucuna yuvarlanmış bir sayıyı yansıtır. Eşit olarak yaklaşık iki doğru gösterilebilir tablo sonucu varsa:
  - **.Net core 2,0 ' ye kadar .NET Framework ve .NET Core 'da** , çalışma zamanı, en az önemli basamakla (yani, kullanılarak) sonucu seçer <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType> .
  - **.NET Core 2,1 ve üzeri sürümlerde** , çalışma zamanı, en az önemli bir basamakla (yani, kullanılarak) sonucu seçer <xref:System.MidpointRounding.ToEven?displayProperty=nameWithType> .

  > [!NOTE]
  > Duyarlık belirtici, sonuç dizesindeki basamakların sayısını belirler. Bir sonuç dizesini başında veya sonunda boşluklarla doldurma için, [Bileşik biçimlendirme](composite-formatting.md) özelliğini kullanın ve biçim öğesinde bir *Hizalama bileşeni* tanımlayın.

Standart sayısal biçim dizeleri şunları destekler:

- `ToString`Tüm sayısal türdeki metodun bazı aşırı yüklemeleri. Örneğin, ve yöntemlerine bir sayısal biçim dizesi sağlayabilirsiniz <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> .

- [composite formatting feature](composite-formatting.md) `Write` Ve sınıflarının bazı ve `WriteLine` yöntemleri <xref:System.Console> <xref:System.IO.StreamWriter> , yöntemi ve <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> yöntemi tarafından kullanılan .net bileşik biçimlendirme özelliği. Bileşik biçim özelliği, alan genişliğini belirtmek ve bir alandaki sayıları hizalamak için birden çok veri öğesinin dize gösterimini tek bir dizeye dahil etmenize olanak tanır. Daha fazla bilgi için bkz. [Bileşik biçimlendirme](composite-formatting.md).

- C# ve Visual Basic ile Birleşik biçim dizelerine kıyasla basitleştirilmiş bir sözdizimi sağlayan [dizeleri Enterpolaştır](../../csharp/language-reference/tokens/interpolated.md) .

> [!TIP]
> Sayısal veya tarih ve saat değerlerine biçim dizeleri uygulamanızı sağlayan ve sonuç dizesini görüntüleyen bir .NET Core Windows Forms uygulaması olan **biçimlendirme yardımcı programını** indirebilirsiniz. Kaynak kodu [C#](/samples/dotnet/samples/windowsforms-formatting-utility-cs) ve [Visual Basic](/samples/dotnet/samples/windowsforms-formatting-utility-vb)için kullanılabilir.

<a name="table"></a> Aşağıdaki tabloda standart sayısal biçim belirticileri açıklanmakta ve her biçim belirticisi tarafından üretilen örnek çıktı görüntülenir. Standart sayısal biçim dizeleri kullanma hakkında ek bilgi için [Notlar](#NotesStandardFormatting) bölümüne ve kullanımlarının kapsamlı bir gösterimi için [örnek](#example) bölümüne bakın.

|Biçim belirteci|Ad|Açıklama|Örnekler|
|----------------------|----------|-----------------|--------------|
|"C" ya da "c"|Para birimi|Sonuç: Bir para birimi değeri.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık belirticisi: tarafından tanımlanır <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> .<br /><br /> Daha fazla bilgi: [para birimi ("C") Biçim belirleyicisi](#CFormatString).|123,456 ("C", en-US)-> \\ $123,46<br /><br /> 123,456 ("C", fr-FR)-> 123, 46 &euro;<br /><br /> 123,456 ("C", ja-JP)-> ¥123<br /><br /> -123,456 ("C3", en-US)-> ( \\ $123,456)<br /><br /> -123,456 ("C3", fr-FR)->-123.456 &euro;<br /><br /> -123,456 ("C3", ja-JP)->-¥123,456|
|"D" veya "d"|Ondalık|Sonuç: İsteğe bağlı eksi işaretli tamsayı basamaklar.<br /><br /> Desteklenen: sadece integral türleri.<br /><br /> Duyarlık belirtici: Minimum basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: En az gereken basamak sayısı.<br /><br /> Daha fazla bilgi: [ondalık ("D") Biçim belirleyicisi](#DFormatString).|1234 ("D")-> 1234<br /><br /> -1234 ("D6")->-001234|
|"E" ya da "e"|Üstsel (bilimsel)|Sonuç: Üstel simgeleme.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: 6.<br /><br /> Daha fazla bilgi: [üstel ("E") Biçim belirleyicisi](#EFormatString).|1052,0329112756 ("E", en-US)-> 052033e E + 003<br /><br /> 1052,0329112756 ("e", fr-FR)-> 1, 052033e + 003<br /><br /> -1052,0329112756 ("E2", en-US)->-1,05 e + 003<br /><br /> -1052,0329112756 ("E2", fr-FR)->-1, 05E + 003|
|"F" ya da "f"|Sabit nokta|Sonuç: İsteğe bağlı eksi işaretli tamsayı ve ondalık basamaklar.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık belirticisi: tarafından tanımlanır <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> .<br /><br /> Daha fazla bilgi: [Fixed-Point ("F") Biçim belirleyicisi](#FFormatString).|1234,567 ("F", en-US)-> 1234,57<br /><br /> 1234,567 ("F", de-DE)-> 1234, 57<br /><br /> 1234 ("F1", en-US)-> 1234,0<br /><br /> 1234 ("F1", de-DE)-> 1234, 0<br /><br /> -1234,56 ("F4", en-US)->-1234,5600<br /><br /> -1234,56 ("F4", de-DE)->-1234, 1234,5600|
|"G" ya da "g"|Genel|Sonuç: sabit noktalı veya bilimsel gösterimin daha küçük olması.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: Anlamlı basamak sayısı.<br /><br /> Varsayılan duyarlık belirtici: Sayısal türe bağlıdır.<br /><br /> Daha fazla bilgi: [Genel ("G") Biçim belirleyicisi](#GFormatString).|-123,456 ("G", en-US)->-123,456<br /><br /> -123,456 ("G", SV-i)->-123.456<br /><br /> 123,4546 ("G4", en-US)-> 123,5<br /><br /> 123,4546 ("G4", SV-i)-> 123, 5<br /><br /> - -1 234567890e e-25 ("G", en-US)->- -1 23456789e E-25<br /><br /> - -1 234567890e e-25 ("G", SV-o)->-1, 23456789E-25|
|"N" ya da "n"|Sayı|Sonuç: Integral ve ondalık basamaklar, grup ayırıcılar ve isteğe bağlı eksi işaretli ondalık ayırıcı.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: İstenen ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık belirticisi: tarafından tanımlanır <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> .<br /><br /> Daha fazla bilgi: [sayısal ("N") Biçim belirleyicisi](#NFormatString).|1234,567 ("N", en-US)-> 1.234,57<br /><br /> 1234,567 ("N", ru-RU)-> 1 234, 57<br /><br /> 1234 ("N1", en-US)-> 1.234,0<br /><br /> 1234 ("N1", ru-RU)-> 1 234, 0<br /><br /> -1234,56 ("N3", en-US)->-1.234,560<br /><br /> -1234,56 ("N3", ru-RU)->-1 234.560|
|"P" ya da "p"|Yüzde|Sonuç: Sayı 100 ile çarpılır ve yüzde simgesi ile görüntülenir.<br /><br /> Destekleyen: Tüm sayısal türler.<br /><br /> Duyarlık belirtici: İstenen ondalık basamak sayısı.<br /><br /> Varsayılan duyarlık belirticisi: tarafından tanımlanır  <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType> .<br /><br /> Daha fazla bilgi: [yüzde ("P") Biçim belirleyicisi](#PFormatString).|1 ("P", en-US)->% 100,00<br /><br /> 1 ("P", fr-FR)-> 100, 00%<br /><br /> -0,39678 ("P1", en-US)->-39,7%<br /><br /> -0,39678 ("P1", fr-FR)->-39, %7|
|"R" ya da "r"|Gidiş|Sonuç: Aynı numaraya gidiş dönüş yapabilen bir dize.<br /><br /> Destekleyen: <xref:System.Single> , <xref:System.Double> , ve <xref:System.Numerics.BigInteger> .<br /><br /> Note: <xref:System.Numerics.BigInteger> yalnızca tür Için önerilir. <xref:System.Double>Türler için "G17" kullanın; türler için <xref:System.Single> "G9" kullanın. <br> Duyarlık belirtici: Yoksayıldı.<br /><br /> Daha fazla bilgi: [gidiş dönüş ("R") Biçim belirleyicisi](#RFormatString).|123456789,12345678 ("R")-> 123456789,12345678<br /><br /> -1234567890,12345678 ("R")->-1234567890,1234567|
|"X" ya da "x"|Onaltılık|Sonuç: Bir onaltılık dize.<br /><br /> Desteklenen: sadece integral türleri.<br /><br /> Duyarlık belirtici: Sonuç dizesindeki basamak sayısı.<br /><br /> Daha fazla bilgi: [onaltılı ("X") Biçim belirleyicisi](#XFormatString).|255 ("X")-> FF<br /><br /> -1 ("x")-> FF<br /><br /> 255 ("x4")-> 00FF<br /><br /> -1 ("X4")-> 00FF|
|Başka bir tek karakter|Bilinmeyen tanımlayıcı|Sonuç: çalışma zamanında bir oluşturur <xref:System.FormatException> .||

<a name="Using"></a>

## <a name="using-standard-numeric-format-strings"></a>Standart Sayısal Biçim Dizeleri Kullanma

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Standart bir sayısal biçimli dize, şu iki yoldan biriyle sayısal bir değerin biçimlendirmesini tanımlamak için kullanılabilir:

- Parametresi olan yönteminin aşırı yüküne geçirilebilir `ToString` `format` . Aşağıdaki örnek, sayısal bir değeri geçerli kültürde (Bu durumda en-US kültürü) bir para birimi dizesi olarak biçimlendirir.

  [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
  [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]

- `formatString`, Ve gibi yöntemlerle kullanılan bir biçim öğesinde bağımsız değişken olarak sağlanabilir <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [Bileşik biçimlendirme](composite-formatting.md). Aşağıdaki örnek, bir dizeye bir para birimi değeri eklemek için bir biçim öğesi kullanmaktadır.

  [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
  [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]

  İsteğe bağlı olarak, `alignment` sayısal alanın genişliğini ve değerinin sağ veya sola hizalı olup olmadığını belirtmek için bir bağımsız değişken sağlayabilirsiniz. Aşağıdaki örnek bir 28 karakter alanındaki bir para birimi değerini sola hizalar ve bir para birimi değerini 14 karakterli bir alanda sağa hizalar.

  [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
  [!code-csharp-interactive[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
  [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]

- `formatString`Enterpolasyonlu bir dizenin enterpolasyonlu ifade öğesinde bağımsız değişken olarak sağlanabilir. Daha fazla bilgi için, Visual Basic başvurusunun C# başvurusu veya [enterpolasyonlu dizeler](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) konusunun [dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md) konusuna bakın.

Aşağıdaki bölümlerde her standart sayısal biçim dizesi hakkında ayrıntılı bilgi sağlanmaktadır.

<a name="CFormatString"></a>

## <a name="the-currency-c-format-specifier"></a>Para Birimi ("C") Biçim Belirleyicisi

"C" (ya da para birimi) biçim belirticisi, bir sayıyı para birimi tutarını gösteren bir dizeye dönüştürür. Duyarlık belirtici, sonuç dizesindeki istenen ondalık basamak sayısını gösterir. Duyarlık belirticisi atlanırsa, varsayılan duyarlık özelliği tarafından tanımlanır <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> .

Biçimlendirilecek değer, belirtilen veya varsayılan ondalık basamak sayısından fazlasına sahipse, sonuç dizesinde kesirli değer yuvarlanır. Belirtilen ondalık basamak sayısının sağındaki değer 5 veya daha büyükse, sonuç dizesindeki son basamak, sıfırdan uzağa yuvarlanır.

Sonuç dizesi geçerli nesnenin biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> . Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> döndürülen dizenin biçimlendirmesini denetleyen özellikler listelenmiştir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|Pozitif değerler için para birimi sembolünün yerleşimini tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|Negatif değerler için para birimi sembolünün yerleşimini tanımlar ve eksi işaretinin parantezle mi yoksa özelliği ile mi temsil edileceğini belirtir <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> .|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Parantezlerin kullanılmadığını gösteriyorsa, kullanılan negatif işareti tanımlar <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> .|
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|Para birimi sembolünü tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|Para birimi değerindeki varsayılan ondalık basamak sayısını tanımlar. B değeri hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|Tamsayı ve ondalık basamakları ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|Tam sayı gruplarını ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|Bir grup içinde görüntülenen tamsayı basamak sayısını tanımlar.|

Aşağıdaki örnek <xref:System.Double> para birimi biçim belirticisiyle bir değeri biçimlendirir:

[!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
[!code-csharp[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
[!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]

[Tabloya dön](#table)

<a name="DFormatString"></a>

## <a name="the-decimal-d-format-specifier"></a>Ondalık ("D") Biçim Belirleyicisi

"D" (veya ondalık) biçim belirticisi, sayıyı, sayı negatifse eksi işaretiyle önekli bir ondalık basamaklı (0-9) bir dizeye dönüştürür. Bu biçim yalnızca tam sayı türleri için desteklenir.

Duyarlık belirtici, sonuç dizesindeki istenen minimum basamak sayısını gösterir. Gerekirse, duyarlık belirtici tarafından verilen basamak sayısını üretmek için sayının sol tarafı sıfırlarla doldurulur Bir duyarlık belirtici belirtilmezse varsayılan, başta sıfır bulunmadan tamsayıyı temsil etmek için gerekli minimum değerdir.

Sonuç dizesi geçerli nesnenin biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> . Aşağıdaki tabloda gösterildiği gibi tek bir özellik, sonuç dizesinin biçimlendirmesini etkiler.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|

Aşağıdaki örnek, bir <xref:System.Int32> değeri ondalık biçim belirleyicisi ile biçimlendirir.

[!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
[!code-csharp-interactive[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
[!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]

[Tabloya dön](#table)

<a name="EFormatString"></a>

## <a name="the-exponential-e-format-specifier"></a>Üstel ("E") Biçim Belirleyicisi

Üstel ("E") biçim belirteci bir sayıyı "-d.ddd...E + ggg" veya "-d.ddd...e+ddd" biçiminde bir dizeye dönüştürür; burada her "d" bir basamağı (0-9) gösterir. Sayı negatifse, dize eksi işaretiyle başlar. Ondalık işaretinden önce her zaman tam bir basamak gelir.

Duyarlık belirtici, ondalık noktasından sonraki istenen basamak sayısını gösterir. Duyarlık belirtici atlanırsa, ondalık işaretinden sonra varsayılan olarak altı basamak kullanılır.

Biçim belirticisinin durumu üsse "E" veya "e" önekinin getirilip getirilmeyeceğini gösterir. Üs her zaman bir artı veya eksi işareti ile en az üç basamaktan oluşur. Üs bu minimum şartı karşılamak için gerekirse sıfırlarla doldurulur.

Sonuç dizesi geçerli nesnenin biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> . Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> döndürülen dizenin biçimlendirmesini denetleyen özellikler listelenmiştir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının hem katsayı hem de üs için negatif olduğunu belirten dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamağını, katsayıdaki ondalık basamaklardan ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Bir üssün pozitif olduğunu belirten dizeyi tanımlar.|

Aşağıdaki örnek, bir <xref:System.Double> değeri üstel biçim belirleyicisi ile biçimlendirir:

[!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
[!code-csharp[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
[!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]

[Tabloya dön](#table)

<a name="FFormatString"></a>

## <a name="the-fixed-point-f-format-specifier"></a>Sabit Nokta ("F") Biçim Belirleyicisi

Sabit nokta ("F") Biçim belirleyicisi bir sayıyı "-ddd. ddd..." biçiminde bir dizeye dönüştürür Burada her "d" bir basamağı (0-9) gösterir. Sayı negatifse, dize eksi işaretiyle başlar.

Duyarlık belirtici, istenen ondalık basamak sayısını gösterir. Duyarlık belirticisi atlanırsa, geçerli <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> özelliği sayısal duyarlık sağlar.

Sonuç dizesi geçerli nesnenin biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> . Aşağıdaki tabloda, <xref:System.Globalization.NumberFormatInfo> sonuç dizesinin biçimlendirmesini denetleyen nesnenin özellikleri listelenmektedir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamaklarını ondalık basamaklardan ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Varsayılan ondalık basamak sayısını tanımlar. B değeri hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|

Aşağıdaki örnek bir <xref:System.Double> ve <xref:System.Int32> değerini sabit noktalı Biçim belirleyicisi ile biçimlendirir:

[!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
[!code-csharp[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
[!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]

[Tabloya dön](#table)

<a name="GFormatString"></a>

## <a name="the-general-g-format-specifier"></a>Genel ("G") Biçim Belirleyicisi

Genel ("G") Biçim Belirleyicisi, sayının türüne ve bir duyarlık belirticisinin var olup olmadığına bağlı olarak, sayıyı sabit noktalı veya bilimsel gösterimden daha küçük bir değere dönüştürür. Duyarlık belirtici, sonuç dizesindeki görünebilir maksimum anlamlı basamak sayısını tanımlar. Duyarlık belirtici atlanırsa veya sıfır olursa, sayının türü, aşağıdaki tabloda gösterildiği gibi varsayılan duyarlığı belirler.

|Sayısal tür|Varsayılan duyarlık|
|------------------|-----------------------|
|<xref:System.Byte> veya <xref:System.SByte>|3 basamak|
|<xref:System.Int16> veya <xref:System.UInt16>|5 basamak|
|<xref:System.Int32> veya <xref:System.UInt32>|10 basamak|
|<xref:System.Int64>|19 basamak|
|<xref:System.UInt64>|20 basamak|
|<xref:System.Numerics.BigInteger>|Sınırsız ( ["R"](#RFormatString)ile aynı)|
|<xref:System.Single>|7 basamak|
|<xref:System.Double>|15 basamak|
|<xref:System.Decimal>|29 basamak|

Sayı bilimsel gösterimde ifade edildiğinde elde edilen üs -5'ten büyükse ve duyarlık belirticiden küçükse sabit noktalı gösterim kullanılır; aksi takdirde bilimsel gösterim kullanılır. Sonuç gerekirse bir ondalık noktası içerir ve ondalık noktadan sonra gelen sıfırlar atlanır. Duyarlık belirtici varsa ve sonuçtaki anlamlı basamak sayısı, belirtilen duyarlığı aşarsa, sondaki fazlalık basamaklar yuvarlama tarafından kaldırılır.

Ancak, sayı bir ise <xref:System.Decimal> ve duyarlık belirtici atlanırsa, sabit noktalı gösterim her zaman kullanılır ve sondaki sıfırlar korunur.

Bilimsel gösterim kullanılırsa, biçim belirtici "G" olduğunda sonuçtaki üssün başına "E", biçim belirtici "g" olduğunda "e" eklenir. Üs, en az iki basamak içerir. Bu, üs değerinde en az üç basamak içeren üssel biçim belirleyici tarafından üretilen bilimsel gösterim biçiminden farklıdır.

Bir <xref:System.Double> değerle kullanıldığında, "G17" Biçim belirticisinin özgün <xref:System.Double> değerin başarılı bir şekilde gidiş dönüşmesini sağlar. Bunun nedeni, en <xref:System.Double> fazla 17 anlamlı basamak sağlayan BIR ıeee 754-2008 uyumlu çift duyarlıklı ( `binary64` ) kayan noktalı sayıdır. "R" [Biçim belirleyicisi](#RFormatString)yerine kullanılmasını öneririz, çünkü bazı durumlarda "r", çift duyarlıklı kayan nokta değerlerini başarıyla geri dönmez. Aşağıdaki örnekte böyle bir durum gösterilmektedir.

[!code-csharp-interactive[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs#GeneralFormatSpecifier)]
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]

Bir <xref:System.Single> değerle kullanıldığında, "G9" Biçim belirleyicisi orijinal <xref:System.Single> değerin başarılı bir şekilde gidiş dönüşmesini sağlar. Bunun nedeni, <xref:System.Single> en fazla dokuz önemli basamak sağlayan BIR ıeee 754-2008 uyumlu tek duyarlıklı ( `binary32` ) bir kayan noktalı sayıdır. Performans nedenleriyle, ["R" Biçim belirleyicisi](#RFormatString)yerine kullanılmasını öneririz.

Sonuç dizesi geçerli nesnenin biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> . Aşağıdaki tabloda, <xref:System.Globalization.NumberFormatInfo> sonuç dizesinin biçimlendirmesini denetleyen özellikler listelenmiştir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamaklarını ondalık basamaklardan ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Bir üssün pozitif olduğunu belirten dizeyi tanımlar.|

Aşağıdaki örnek, kayan nokta değerlerini genel biçim belirticisi ile biçimlendirir:

[!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
[!code-csharp[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
[!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]

[Tabloya dön](#table)

<a name="NFormatString"></a>

## <a name="the-numeric-n-format-specifier"></a>Sayısal ("N") Biçim Belirleyicisi

Sayısal ("N") biçim belirteci bir sayıyı "-d,ddd,ddd.ddd…" biçiminde bir dizeye dönüştürür; burada "-" gerekirse negatif bir sayı simgesini, "d" bir basamağı (0-9) gösterir, "," bir grup ayırıcıyı gösterir ve "." bir ondalık simgesini gösterir. Duyarlık belirtici, ondalık noktasından sonraki istenen basamak sayısını gösterir. Duyarlık belirticisi atlanırsa, ondalık basamak sayısı geçerli özellik tarafından tanımlanır <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> .

Sonuç dizesi geçerli nesnenin biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> . Aşağıdaki tabloda, <xref:System.Globalization.NumberFormatInfo> sonuç dizesinin biçimlendirmesini denetleyen özellikler listelenmiştir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|Negatif değerlerin biçimini tanımlar ve eksi işaretinin parantezle mi yoksa özelliği ile mi temsil edileceğini belirtir <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> .|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|Grup ayırıcıları arasında görüntülenen tam sayı basamak sayısını tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|Tam sayı gruplarını ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı ve ondalık basamakları ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|Varsayılan ondalık basamak sayısını tanımlar. B değeri bir hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|

Aşağıdaki örnek, belirtilen kayan nokta değerlerini sayı Biçim belirleyicisi ile biçimlendirir:

[!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
[!code-csharp[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
[!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]

[Tabloya dön](#table)

<a name="PFormatString"></a>

## <a name="the-percent-p-format-specifier"></a>Yüzde ("p") Biçim Belirleyicisi

Yüzde ("P") biçim belirticisi sayıyı 100 ile çarpar ve yüzde temsil eden bir dizeye dönüştürür. Duyarlık belirtici, istenen ondalık basamak sayısını gösterir. Duyarlık belirticisi atlanırsa, geçerli özelliği tarafından sağlanan varsayılan sayısal duyarlık <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> kullanılır.

Aşağıdaki tabloda <xref:System.Globalization.NumberFormatInfo> döndürülen dizenin biçimlendirmesini denetleyen özellikler listelenmiştir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.PercentPositivePattern%2A>|Pozitif değerler için yüzde sembolünün yerleşimini tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.PercentNegativePattern%2A>|Negatif değerler için yüzde sembolünün ve eksi sembolünün yerleşimini tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A>|Yüzde sembolünü tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A>|Yüzde değerindeki varsayılan ondalık basamak sayısını tanımlar. B değeri hassasiyet belirleyici kullanılarak geçersiz kılınabilir.|
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalSeparator%2A>|Tamsayı ve ondalık basamakları ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSeparator%2A>|Tam sayı gruplarını ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSizes%2A>|Bir grup içinde görüntülenen tamsayı basamak sayısını tanımlar.|

Aşağıdaki örnek, kayan nokta değerlerini yüzde Biçim belirleyicisi ile biçimlendirir:

[!code-cpp[Formatting.Numeric.Standard#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#7)]
[!code-csharp[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
[!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]

[Tabloya dön](#table)

<a name="RFormatString"></a>

## <a name="the-round-trip-r-format-specifier"></a>Gidiş Dönüş ("R") Biçim Belirleyicisi

Gidiş dönüş ("R") Biçim Belirleyicisi, bir dizeye dönüştürülen sayısal bir değerin aynı sayısal değere ayrıştırılmasını sağlamaya çalışır. Bu biçim yalnızca <xref:System.Single> ,, <xref:System.Double> ve türleri için desteklenir <xref:System.Numerics.BigInteger> .

<xref:System.Double>Değerler için, bazı durumlarda "R" Biçim belirleyicisi özgün değeri başarıyla geri dönmez. Hem hem <xref:System.Double> de <xref:System.Single> değerleri için de nispeten düşük performans sağlar. Bunun yerine, değerler için ["G17"](#GFormatString) biçim belirticisini <xref:System.Double> ve ["G9"](#GFormatString) biçim belirticisini başarıyla gidiş dönüş değerlerini kullanmanızı öneririz <xref:System.Single> .

Bir <xref:System.Numerics.BigInteger> değer bu tanımlayıcı kullanılarak biçimlendirilirken, dize temsili değerindeki tüm önemli rakamları içerir <xref:System.Numerics.BigInteger> .

Bir duyarlık belirtici ekleyebilirsiniz, ancak bu yoksayılır. Bu belirleyici kullanırken gidiş dönüşlere duyarlılık üzerinde öncelik verilir.
Sonuç dizesi geçerli nesnenin biçimlendirme bilgileri tarafından etkilenir <xref:System.Globalization.NumberFormatInfo> . Aşağıdaki tabloda, <xref:System.Globalization.NumberFormatInfo> sonuç dizesinin biçimlendirmesini denetleyen özellikler listelenmiştir.

|NumberFormatInfo özellikleri|Açıklama|
|-------------------------------|-----------------|
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|Bir sayının negatif olduğunu belirten dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|Tamsayı basamaklarını ondalık basamaklardan ayıran dizeyi tanımlar.|
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|Bir üssün pozitif olduğunu belirten dizeyi tanımlar.|

Aşağıdaki örnek, bir <xref:System.Numerics.BigInteger> değeri gidiş dönüş Biçim belirleyicisi ile biçimlendirir.

[!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
[!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
[!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]

> [!IMPORTANT]
> Bazı durumlarda, <xref:System.Double> "R" standart sayısal biçim dizesiyle biçimlendirilen değerler, veya anahtarları kullanılarak derlenirse `/platform:x64` `/platform:anycpu` ve 64 bitlik sistemlerde çalıştırıldığında, başarılı bir şekilde gidiş dönüş değildir. Daha fazla bilgi için aşağıdaki paragrafa bakın.

<xref:System.Double>"R" standart sayısal biçim dizesiyle biçimlendirilen değer sorununa geçici bir çözüm bulmak için, veya anahtarlar kullanılarak derlenirse `/platform:x64` `/platform:anycpu` ve 64 bitlik sistemlerde çalıştırırsanız, değerleri başarıyla yuvarlamaz. <xref:System.Double> "G17" standart sayısal biçim dizesini kullanarak değerleri biçimlendirebilirsiniz. Aşağıdaki örnek, başarılı bir şekilde gidiş dönüş olmayan bir değerle "R" biçim dizesini <xref:System.Double> ve ayrıca özgün değeri başarıyla yuvarlamak için "G17" biçim dizesini kullanır:

[!code-csharp[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#RoundTrip)]
[!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]

[Tabloya dön](#table)

<a name="XFormatString"></a>

## <a name="the-hexadecimal-x-format-specifier"></a>Onaltılı ("X") Biçim Belirleyicisi

("X") onaltılı biçim belirticisi bir sayıyı onaltı basamaklı bir dizeye dönüştürür. Biçim belirticisinin durumu, 9'dan büyük onaltılık basamak için büyük veya küçük harf kullanılıp kullanılmayacağını belirtir. Örneğin, "ABCDEF" üretmek için "X" ve "abcdef" üretmek için "x" kullanın. Bu biçim yalnızca tam sayı türleri için desteklenir.

Duyarlık belirtici, sonuç dizesindeki istenen minimum basamak sayısını gösterir. Gerekirse, duyarlık belirtici tarafından verilen basamak sayısını üretmek için sayının sol tarafı sıfırlarla doldurulur

Sonuç dizesi geçerli nesnenin biçimlendirme bilgisi tarafından etkilenmemektedir <xref:System.Globalization.NumberFormatInfo> .

Aşağıdaki örnek <xref:System.Int32> değerleri onaltılık biçim belirleyicisi ile biçimlendirir.

[!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
[!code-csharp-interactive[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
[!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]

[Tabloya dön](#table)

<a name="NotesStandardFormatting"></a>

## <a name="notes"></a>Notlar

### <a name="control-panel-settings"></a>Denetim Masası Ayarları

Denetim Masası 'ndaki **bölge ve dil seçenekleri** öğesindeki ayarlar, bir biçimlendirme işlemi tarafından üretilen sonuç dizesini etkiler. Bu ayarlar <xref:System.Globalization.NumberFormatInfo> , biçimlendirmeyi yönetmek için kullanılan değerleri sağlayan geçerli iş parçacığı kültürüyle ilişkili nesneyi başlatmak için kullanılır. Farklı ayarları kullanan bilgisayarlar farklı sonuç dizeleri üretir.

Ayrıca, <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29> Oluşturucu <xref:System.Globalization.CultureInfo> geçerli sistem kültürüyle aynı kültürü temsil eden yeni bir nesne oluşturmak için kullanılıyorsa, Denetim Masası 'ndaki **bölge ve dil seçenekleri** öğesi tarafından belirlenen tüm özelleştirmeler yeni <xref:System.Globalization.CultureInfo> nesneye uygulanır. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29>Oluşturucuyu, <xref:System.Globalization.CultureInfo> sistemin özelleştirmelerini yansıtmayan bir nesne oluşturmak için kullanabilirsiniz.

### <a name="numberformatinfo-properties"></a>NumberFormatInfo Özellikleri

Biçimlendirme, geçerli <xref:System.Globalization.NumberFormatInfo> iş parçacığı kültürü tarafından örtük olarak veya <xref:System.IFormatProvider> Biçimlendirmeyi çağıran yöntemin parametresi tarafından açıkça sunulan geçerli nesnenin özelliklerinden etkilenir. <xref:System.Globalization.NumberFormatInfo> <xref:System.Globalization.CultureInfo> Bu parametre için bir veya nesnesi belirtin.

> [!NOTE]
> Sayısal değerleri biçimlendirmede kullanılan desenleri veya dizeleri özelleştirme hakkında bilgi için, bkz <xref:System.Globalization.NumberFormatInfo> . sınıf konusu.

### <a name="integral-and-floating-point-numeric-types"></a>Tam Sayı ve Kayan Nokta Sayısal Türleri

Bazı standart sayısal biçim belirticilerinin açıklamaları, ayrılmaz veya kayan nokta sayısal türlere başvurur. İntegral sayısal türleri,,,,, <xref:System.Byte> <xref:System.SByte> ,, <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.UInt16> <xref:System.UInt32> <xref:System.UInt64> ve <xref:System.Numerics.BigInteger> . Kayan nokta sayısal türleri <xref:System.Decimal> , <xref:System.Single> , ve <xref:System.Double> .

### <a name="floating-point-infinities-and-nan"></a>Kayan Nokta Sonsuz ve NaN

Biçim dizesi ne olursa olsun, bir <xref:System.Single> veya <xref:System.Double> kayan nokta türünün değeri pozitif sonsuzluk, negatif sonsuzluk veya sayı değil (NaN), biçimlendirilen dize <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A> geçerli geçerli <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A> <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> nesne tarafından belirtilen ilgili, veya özelliğin değeridir <xref:System.Globalization.NumberFormatInfo> .

## <a name="example"></a>Örnek

[!INCLUDE[interactive-note](~/includes/csharp-interactive-partial-note.md)]

Aşağıdaki örnek, bir tamsayı ve kayan nokta sayısal değerini ing-ABD kültürü ve tüm standart sayısal biçim tanımlayıcılarını kullanarak biçimlendirir. Bu örnek iki özel sayısal türü ( <xref:System.Double> ve <xref:System.Int32> ) kullanır, ancak diğer sayısal temel türlerden ( <xref:System.Byte> ,,,,, <xref:System.SByte> <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> <xref:System.UInt16> , <xref:System.UInt32> ,, <xref:System.UInt64> , <xref:System.Numerics.BigInteger> <xref:System.Decimal> <xref:System.Single> ,,,,, ve) herhangi biri için benzer sonuçlar verir.

[!code-csharp[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#FinalExample)]
[!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Globalization.NumberFormatInfo>
- [Özel sayısal biçim dizeleri](custom-numeric-format-strings.md)
- [Biçimlendirme Türleri](formatting-types.md)
- [Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma](how-to-pad-a-number-with-leading-zeros.md)
- [Bileşik biçimlendirme](composite-formatting.md)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programı (C#)](/samples/dotnet/samples/windowsforms-formatting-utility-cs)
- [Örnek: .NET Core WinForms biçimlendirme yardımcı programı (Visual Basic)](/samples/dotnet/samples/windowsforms-formatting-utility-vb)
