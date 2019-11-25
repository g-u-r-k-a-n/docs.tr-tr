---
title: Office programlama- C# programlama kılavuzunda adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: d7efd13f26912f8cd944bcbc5568e9bbca92c3a0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970500"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma (C# Programlama Kılavuzu)

Adlandırılmış bağımsız değişkenler ve isteğe bağlı bağımsız değişkenler C# , 4 ' te tanıtılan ve C# programlamada kolaylık, esneklik ve okunabilirliği geliştirir. Ayrıca, bu özellikler Microsoft Office Automation API 'Leri gibi COM arabirimlerine erişimi büyük ölçüde kolaylaştırır.

Aşağıdaki örnekte, [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) yönteminin sütun ve satır sayısı, biçimlendirme, kenarlık, yazı tipi ve renkler gibi bir tablonun özelliklerini temsil eden on altı parametresi vardır. Tüm on altı parametresi isteğe bağlıdır, çünkü çoğu zaman belirli değerleri belirtmek istemezsiniz. Ancak, adlandırılmış ve isteğe bağlı bağımsız değişkenler olmadan her bir parametre için bir değer veya yer tutucu değeri sağlanmalıdır. Adlandırılmış ve isteğe bağlı bağımsız değişkenlerle, yalnızca projeniz için gerekli olan parametrelerin değerlerini belirtirsiniz.

Bu yordamları gerçekleştirmek için bilgisayarınızda Microsoft Office Word yüklü olmalıdır.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Yeni bir konsol uygulaması oluşturmak için

1. Visual Studio 'Yu başlatın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

3. **Şablonlar kategorileri** bölmesinde, **görsel C#** ' i genişletin ve ardından **Windows**' a tıklayın.

4. **.NET Framework 4** ' ün **hedef çerçeve** kutusunda göründüğünden emin olmak için **Şablonlar** bölmesinin üst kısmına bakın.

5. **Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.

6. **Ad** alanına projeniz için bir ad yazın.

7. **Tamam**'a tıklayın.

     Yeni proje **Çözüm Gezgini**görüntülenir.

## <a name="to-add-a-reference"></a>Başvuru eklemek için

1. **Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın. **Başvuru Ekle** iletişim kutusu görüntülenir.

2. **.Net** sayfasında, **bileşen adı** listesinde **Microsoft. Office. Interop. Word** öğesini seçin.

3. **Tamam**'a tıklayın.

## <a name="to-add-necessary-using-directives"></a>Gerekli yönergeleri kullanarak ekleme

1. **Çözüm Gezgini**, *program.cs* dosyasına sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.

2. Aşağıdaki `using` yönergelerini kod dosyasının en üstüne ekleyin:

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a>Bir Word belgesinde metin göstermek için

1. *Program.cs*içindeki `Program` sınıfında, bir Word uygulaması ve Word belgesi oluşturmak için aşağıdaki yöntemi ekleyin. [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) yönteminde dört isteğe bağlı parametre vardır. Bu örnek, varsayılan değerlerini kullanır. Bu nedenle, çağırma ifadesinde herhangi bir bağımsız değişken gerekmez.

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. İçinde metnin nerede görüntüleneceğini ve hangi metnin görüntüleneceğini tanımlamak için yönteminin sonuna aşağıdaki kodu ekleyin:

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a>Uygulamayı çalıştırmak için

1. Aşağıdaki ifadeyi Main öğesine ekleyin:

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. Projeyi çalıştırmak için <kbd>CTRL</kbd>+<kbd>F5</kbd> tuşuna basın. Belirtilen metni içeren bir Word belgesi görüntülenir.

## <a name="to-change-the-text-to-a-table"></a>Metni bir tabloya dönüştürmek için
  
1. Metni bir tabloya kapsamak için `ConvertToTable` yöntemini kullanın. Yönteminde on altı isteğe bağlı parametre vardır. IntelliSense, aşağıdaki çizimde gösterildiği gibi isteğe bağlı parametreleri köşeli ayraç içine alır.

     ![ConvertToTable yöntemi için parametrelerin listesi](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     Adlandırılmış ve isteğe bağlı bağımsız değişkenler yalnızca değiştirmek istediğiniz parametrelerin değerlerini belirtmenizi sağlar. Basit bir tablo oluşturmak için `DisplayInWord` yönteminin sonuna aşağıdaki kodu ekleyin. Bağımsız değişkeni, `range` içindeki metin dizesindeki virgüllerin tablonun hücrelerini ayırabelirtir.

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     Önceki sürümlerinde C#, aşağıdaki kodda gösterildiği gibi, `ConvertToTable` çağrısı her parametre için bir başvuru bağımsız değişkeni gerektirir:
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. Projeyi çalıştırmak için <kbd>CTRL</kbd>+<kbd>F5</kbd> tuşuna basın.

## <a name="to-experiment-with-other-parameters"></a>Diğer parametrelerle denemek için

1. Tabloyu tek bir sütuna ve üç satıra sahip olacak şekilde değiştirmek için `DisplayInWord` son satırını aşağıdaki deyimle değiştirin ve ardından <kbd>CTRL</kbd>+<kbd>F5</kbd>yazın.  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. Tablo için önceden tanımlanmış bir biçim belirtmek üzere `DisplayInWord` son satırını aşağıdaki deyimle değiştirin ve ardından <kbd>CTRL</kbd>+<kbd>F5</kbd>yazın. Biçim, [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) sabitlerinden herhangi biri olabilir.

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a>Örnek

Aşağıdaki kod tam örneği içerir:

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a>Ayrıca bkz.

- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](./named-and-optional-arguments.md)
