---
title: Dize Veri Türü
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: c2c6f9632646c432abb7b6da8887253e526cc994
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343906"
---
# <a name="string-data-type-visual-basic"></a>Dize Veri Türü (Visual Basic)

0 ile 65535 arasında bir değer olarak aralıktaki işaretsiz 16 bit (2 baytlık) kod noktalarının dizilerini barındırır. Her *kod noktası*veya karakter kodu, tek bir Unicode karakteri temsil eder. Dize, 0 ile yaklaşık 2.000.000.000 (2 ^ 31) Unicode karakter içerebilir.  
  
## <a name="remarks"></a>Açıklamalar  

 Dizi yönetim ek yükü olmadan birden çok karakteri tutmak için `String` veri türünü kullanın, bir dizi `Char` öğesi `Char()`.  
  
 `String` varsayılan değeri `Nothing` (null başvuru). Bunun boş dize (değer `""`) ile aynı olmadığına unutmayın.  
  
## <a name="unicode-characters"></a>Unicode karakterler  

 Unicode 'un ilk 128 kod noktası (0 – 127), standart bir ABD klavyesinde bulunan harflere ve simgelere karşılık gelir. Bu ilk 128 kod noktası, ASCII karakter kümesi tarafından tanımlananlarla aynıdır. İkinci 128 kod noktaları (128 – 255) Latin tabanlı alfabe harfleri, vurgular, para birimi sembolleri ve kesirler gibi özel karakterleri temsil eder. Unicode, çok çeşitli semboller için kalan kod noktalarını (256-65535) kullanır. Bu, dünya genelindeki metinsel karakter, Aksanlar ve matematik ve teknik sembolleri içerir.  
  
 <xref:System.Char.IsDigit%2A> ve <xref:System.Char.IsPunctuation%2A> gibi yöntemleri, bir `String` değişkenindeki tek bir karakter üzerinde, Unicode sınıflandırmasını belirleyebilmeniz için kullanabilirsiniz.  
  
## <a name="format-requirements"></a>Biçim gereksinimleri  

 `String` değişmez değerini tırnak işaretleri içine almalısınız (`" "`). Dizedeki karakterlerden biri olarak bir tırnak işareti eklemeniz gerekiyorsa, iki bitişik tırnak işareti (`""`) kullanırsınız. Aşağıdaki örnek bunu göstermektedir.  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Dizedeki bir tırnak işaretini temsil eden bitişik tırnak işaretlerinin, `String` değişmez değeri başlayıp biten tırnak işaretlerinden bağımsız olduğunu unutmayın.  
  
## <a name="string-manipulations"></a>Dize Işlemeleri  

 Bir `String` değişkenine bir dize atadıktan sonra, bu dize *sabittir*, bu da uzunluğunu veya içeriğini değiştiremeyeceğiniz anlamına gelir. Bir dizeyi dilediğiniz şekilde değiştirdiğinizde, Visual Basic yeni bir dize oluşturur ve öncekini terk ediyor. `String` değişkeni daha sonra yeni dizeyi gösterir.  
  
 Bir `String` değişkeninin içeriğini çeşitli dize işlevleri kullanarak değiştirebilirsiniz. Aşağıdaki örnekte <xref:Microsoft.VisualBasic.Strings.Left%2A> işlevi gösterilmektedir  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Başka bir bileşen tarafından oluşturulan bir dize, başında veya sonunda boşluklarla doldurulmuş olabilir. Böyle bir dize alırsanız, bu alanları kaldırmak için <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>ve <xref:Microsoft.VisualBasic.Strings.RTrim%2A> işlevlerini kullanabilirsiniz.  
  
 Dize işlemeleri hakkında daha fazla bilgi için bkz. [dizeler](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Programlama İpuçları  
  
- **Negatif sayılar.** `String` tarafından tutulan karakterlerin işaretsiz olduğunu ve negatif değerleri temsil ettiğini unutmayın. Herhangi bir durumda, sayısal değerleri tutmak için `String` kullanmamalısınız.  
  
- **Birlikte çalışma konuları.** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimleriniz varsa, diğer ortamlarda dize karakterlerinin farklı bir veri genişliğine (8 bit) sahip olduğunu unutmayın. Bu bileşene 8 bitlik karakterlerin dize bağımsız değişkenini geçirdiğinizden, yeni Visual Basic kodunuzda `String` yerine bir dizi `Byte` öğesi `Byte()`olarak bildirin.  
  
- **Tür karakterleri.** Tanımlayıcı türü karakter `$` herhangi bir tanımlayıcıya eklemek, `String` veri türüne zorlar. `String` değişmez değer türü karakteri yok. Ancak derleyici, sabit değerleri (`" "`) `String`olarak tırnak işaretleri içinde değerlendirir.  
  
- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.String?displayProperty=nameWithType> sınıfıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String?displayProperty=nameWithType>
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Char Veri Türü](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
