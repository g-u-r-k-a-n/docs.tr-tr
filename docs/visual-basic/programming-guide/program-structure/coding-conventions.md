---
title: Kodlama Kuralları
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: eae283c757ddeb1290c15d82a41c8028a8941e63
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91059164"
---
# <a name="visual-basic-coding-conventions"></a>Visual Basic Kodlama Kuralları

Microsoft, bu konudaki yönergeleri izleyen örnekler ve belgeler geliştirir. Aynı kodlama kurallarını izlerseniz, aşağıdaki avantajları elde edebilirsiniz:  
  
- Kodunuzun tutarlı bir görünümü olur, böylece okuyucular düzene göre değil içeriğe daha iyi odaklanabilir.  
  
- Okuyucular, önceki deneyimle ilgili varsayımlar yapabildiğinden kodunuzu daha hızlı bir şekilde öğrenirler.  
  
- Kodu daha kolay kopyalayabilir, değiştirebilir ve bakımını yapabilirsiniz.  
  
- Kodunuzun, Visual Basic için "en iyi uygulamaları" gösterdiği sağlanmasına yardımcı olursunuz.  
  
## <a name="naming-conventions"></a>Adlandırma Kuralları  
  
- Adlandırma yönergeleri hakkında daha fazla bilgi için bkz. [Adlandırma yönergeleri](../../../standard/design-guidelines/naming-guidelines.md) konusu.  
  
- Değişken adının bir parçası olarak "My" veya "My" kullanmayın. Bu uygulama, nesneleriyle karışıklık oluşturur `My` .  
  
- Otomatik olarak oluşturulan koddaki nesnelerin adlarını, kurallara uyacak şekilde değiştirmeniz gerekmez.  
  
## <a name="layout-conventions"></a>Düzeni Kuralları  
  
- Sekmeleri boşluk olarak ekleyin ve dört boşluklu girintilerle akıllı girintileme kullanın.  
  
- Kod düzenleyicisinde kodunuzu yeniden biçimlendirmek için **kodun düzgün listesini (yeniden biçimlendirme)** kullanın. Daha fazla bilgi için bkz. [Seçenekler, metin düzenleyici, temel (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
- Her satırda yalnızca bir ifade kullanın. Visual Basic çizgi ayırıcı karakterini kullanmayın (:).  
  
- "_" Açık satır devamlılığı, dilin izin verdiği her yerde örtük satır devamlılığı kullanımına karşı kullanmaktan kaçının.  
  
- Her satırda yalnızca bir bildirim kullanın.  
  
- **Kodun düzgün listelenmesi (yeniden biçimlendirilmesi)** devam satırlarını otomatik olarak biçimlendirmezse, devamlılık satırlarını bir sekme durağı olarak el ile girintileyin. Ancak, her zaman bir listedeki öğeleri sola hizalayın.  
  
    ```vb  
    a As Integer,  
    b As Integer  
    ```  
  
- Yöntem ve özellik tanımları arasına en az bir boş satır ekleyin.  
  
## <a name="commenting-conventions"></a>Yorum Oluşturma Kuralları  
  
- Açıklamaları bir kod satırının sonu yerine ayrı bir satıra koyun.  
  
- Açıklama metnini büyük harfle başlatın ve açıklama metnini noktayla bitirin.  
  
- Açıklama sınırlayıcısı (') ve açıklama metni arasına bir boşluk ekleyin.  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- Açıklamaları, biçimli yıldız blokları ile çevrelemeyin.  
  
## <a name="program-structure"></a>Program Yapısı  
  
- `Main`Yöntemini kullandığınızda, yeni konsol uygulamaları için varsayılan yapıyı kullanın ve `My` komut satırı bağımsız değişkenleri için kullanın.  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a>Dil Kuralları  
  
### <a name="string-data-type"></a>Dize Veri Türü  
  
- Aşağıdaki kodda gösterildiği gibi, kısa dizeleri birleştirmek için [dize ilişkilendirmeyi](../language-features/strings/interpolated-strings.md) kullanın.
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- Döngülerde dizeler eklemek için <xref:System.Text.StringBuilder> nesnesini kullanın.  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Olay Işleyicilerinde gevşek temsilciler  

 Bağımsız değişkenleri (Object ve EventArgs) olay işleyicileriyle açıkça nitelemeyin. Bir olaya iletilen olay bağımsız değişkenlerini kullanmıyorsanız (örneğin, gönderen nesne, EventArgs olarak e), gevşek temsilciler kullanın ve kodunuzda olay bağımsız değişkenlerini bırakın:  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a>İmzasız Veri Türü  
  
- `Integer`Gerekli olduğu durumlar dışında, imzasız türler yerine kullanın.  
  
### <a name="arrays"></a>Diziler  
  
- Bildirim satırında dizileri başlattığınızda kısa sözdizimini kullanın. Örneğin, aşağıdaki sözdizimini kullanın.  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     Aşağıdaki sözdizimini kullanmayın.  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- Dizi göstergesini değişkene değil, türüne koyun. Örneğin, aşağıdaki sözdizimini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     Aşağıdaki sözdizimini kullanmayın:  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- Temel veri türleri dizilerini bildirdiğinizde ve başlattığınızda {} sözdizimini kullanın. Örneğin, aşağıdaki sözdizimini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     Aşağıdaki sözdizimini kullanmayın:  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a>WITH anahtar sözcüğünü kullanma  

 Bir nesneye bir dizi çağrı yaptığınızda, `With` anahtar sözcüğünü kullanmayı düşünün:  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>TRY... öğesini kullanın Özel durum Işleme kullandığınızda deyimleri yakalama ve kullanma  

 Kullanmayın `On Error Goto` .  
  
### <a name="use-the-isnot-keyword"></a>Inot anahtar sözcüğünü kullanma  

 `IsNot`Yerine anahtar sözcüğünü kullanın `Not...Is Nothing` .  
  
### <a name="new-keyword"></a>Yeni anahtar sözcük  
  
- Kısa örnek oluşturma kullanın. Örneğin, aşağıdaki sözdizimini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     Yukarıdaki satır buna eşdeğerdir:  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- Parametresiz Oluşturucu yerine yeni nesneler için nesne başlatıcıları kullanın:  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a>Olay İşleme  
  
- `Handles`Yerine kullanın `AddHandler` :  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- `AddressOf`Öğesini kullanın ve temsilciyi açıkça örneğini oluşturun:  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- Bir olay tanımladığınızda, kısa sözdizimini kullanın ve derleyicinin temsilciyi tanımlamasına izin verin:  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- `Nothing`Yöntemi çağırmadan önce bir olayın (null) olup olmadığını doğrulama `RaiseEvent` . `RaiseEvent``Nothing`olayı oluşturmadan önce olup olmadığını denetler.  
  
### <a name="using-shared-members"></a>Paylaşılan üyeleri kullanma  

 `Shared`Bir örnek değişkeninden değil sınıf adını kullanarak üyeleri çağırın.  
  
### <a name="use-xml-literals"></a>XML değişmez değerlerini kullan  

 XML sabit değerleri, XML ile çalışırken karşılaşabileceğiniz en yaygın görevleri basitleştirir (örneğin, Load, Query ve Transform). XML ile geliştirme yaparken şu yönergeleri izleyin:  
  
- XML API 'Lerini doğrudan çağırmak yerine XML belgelerini ve parçalarını oluşturmak için XML değişmez değerlerini kullanın.  
  
- XML değişmez değerleri için performans iyileştirmelerinden faydalanmak için dosya veya proje düzeyinde XML ad alanlarını içeri aktarın.  
  
- XML belgesindeki öğelere ve özniteliklere erişmek için XML eksen özelliklerini kullanın.  
  
- Yöntem gibi API çağrılarını kullanmak yerine mevcut değerlerden XML oluşturmak ve değerleri dahil etmek için gömülü ifadeleri kullanın `Add` :  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a>LINQ Sorguları  
  
- Sorgu değişkenleri için anlamlı adlar kullanın:  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- Anonim türlerin özellik adlarının, Pascal büyük harfleri kullanarak doğru şekilde büyük harfli olduğundan emin olmak için bir sorgudaki öğelerin adlarını sağlayın:  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- Sonuç içindeki Özellik adları belirsiz olduğunda özellikleri yeniden adlandırın. Örneğin, sorgunuz bir müşteri adı ve bir sipariş KIMLIĞI döndürürse, bunları ve sonuç olarak bırakmak yerine yeniden adlandırın `Name` `ID` :  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- Sorgu değişkenleri ve Aralık değişkenleri bildiriminde tür çıkarımı kullanın:  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- Sorgu yan tümcelerini deyimin altına Hizala `From` :  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- `Where`Daha sonra sorgu yan tümcelerinin filtrelenmiş veri kümesinde çalışması için diğer sorgu yan tümcelerinden önce yan tümceleri kullanın:  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- `Join` `Where` Bir JOIN işlemini örtük olarak tanımlamak için yan tümcesini kullanmak yerine bir JOIN işlemini açıkça tanımlamak için yan tümcesini kullanın:  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../standard/security/secure-coding-guidelines.md)
