---
title: .NET 'teki dizeleri karşılaştırmak için en iyi yöntemler
description: .NET uygulamalarında dizelerin etkin bir şekilde nasıl karşılaştırılacağını öğrenin.
ms.date: 05/01/2019
ms.topic: conceptual
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET],searching
- best practices,string comparison and sorting
- strings [.NET],best practices
- strings [.NET],basic string operations
- sorting strings
- strings [.NET],sorting
- string comparison [.NET],best practices
- string sorting
- comparing strings
- strings [.NET],comparing
ms.assetid: b9f0bf53-e2de-4116-8ce9-d4f91a1df4f7
ms.openlocfilehash: 7e495edbf3cdfe5886a2dfbf06eee04d4f6a7567
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98693117"
---
# <a name="best-practices-for-comparing-strings-in-net"></a>.NET 'teki dizeleri karşılaştırmak için en iyi yöntemler

.NET, yerelleştirilmiş ve genelleştirilmiş uygulamaları geliştirmeye yönelik kapsamlı destek sağlar ve dizeleri sıralama ve görüntüleme gibi genel işlemleri gerçekleştirirken geçerli kültür ya da belirli bir kültürün kurallarını uygulamayı kolaylaştırır. Ancak dizeleri sıralamak veya karşılaştırmak her zaman kültüre duyarlı bir işlem değildir. Örneğin, bir uygulama tarafından dahili olarak kullanılan dizelerin genellikle tüm kültürlerde aynı şekilde işlenmeleri gerekir. XML etiketleri, HTML etiketleri, kullanıcı adları, dosya yolları ve sistem nesnelerinin adları gibi kültürden bağımsız dize verileri kültüre duyarlıymış gibi yorumlanırsa, uygulama kodu küçük hatalar, zayıf performans ve bazı durumlarda güvenlik sorunlarıyla karşılaşabilir.

Bu makale, .NET 'teki dize sıralama, karşılaştırma ve büyük/küçük harf yöntemlerini inceler, uygun bir dize işleme yöntemi seçmeye yönelik öneriler sunar ve dize işleme yöntemleriyle ilgili ek bilgiler sağlar.

## <a name="recommendations-for-string-usage"></a>Dize kullanımı için öneriler

.NET ile geliştirme yaptığınızda, dizeleri karşılaştırdığınızda bu basit önerileri takip edin:

- Dize işlemleri için dize karşılaştırma kurallarını açıkça belirten aşırı yüklemeleri kullanın. Genellikle bu, <xref:System.StringComparison> türünde bir parametreye sahip olan bir yöntem aşırı yüklemesini çağırmayı içerir.
- Güvenli varsayılan olarak kültürden bağımsız dize karşılaştırmalarınız için <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> veya <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> kullanın.
- Daha iyi performans için <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> veya <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> ile karşılaştırma kullanın.
- Kullanıcıya çıktı görüntülerken <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> öğesini temel alan dize işlemlerini kullanın.
- Karşılaştırma dilsel olarak alakasız iken (örneğin simgesel olduğunda), <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> öğesini temel alan dize işlemleri yerine dilsel olmayan <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> veya <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> değerlerini kullanın.
- Karşılaştırma için dizelerinizi normalleştirirken <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> yöntemi yerine <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> yöntemini kullanın.
- İki dizenin eşit olup olmadığını test etmek için <xref:System.String.Equals%2A?displayProperty=nameWithType> yönteminin bir aşırı yüklemesini kullanın.
- Eşit olup olmadıklarını kontrol etmek için değil, dizeleri sıralamak için <xref:System.String.Compare%2A?displayProperty=nameWithType> ve <xref:System.String.CompareTo%2A?displayProperty=nameWithType> yöntemlerini kullanın.
- Sayılar ve tarihler gibi dize olmayan verileri bir kullanıcı arabiriminde görüntülemek için kültüre duyarlı biçimlendirme kullanın. Dize olmayan verileri dize biçiminde kalıcı hale getirmek için [sabit kültür](xref:System.Globalization.CultureInfo.InvariantCulture) ile biçimlendirme kullanın.

Dizeleri karşılaştırdığınızda aşağıdaki uygulamalardan kaçının:

- Dize işlemleri için dize karşılaştırma kurallarını açıkça veya dolaylı olarak belirtmeyen aşırı yüklemeleri kullanmayın.
- Çoğu durumda <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> öğesini temel alan dize işlemlerini kullanmayın. Dilsel olarak anlamlı ancak kültüre duyarlı olmayan verileri kalıcı hale getirmeniz, az sayıdaki istisnalardan biridir.
- İki dizenin eşit olup olmadığını belirlerken sıfır dönüş değerini test etmek için <xref:System.String.Compare%2A?displayProperty=nameWithType> veya <xref:System.String.CompareTo%2A> yöntemlerinin bir aşırı yüklemesini kullanmayın.

## <a name="specifying-string-comparisons-explicitly"></a>Açık dize karşılaştırmaları belirtme

.NET 'teki dize düzenleme yöntemlerinin çoğu aşırı yüklenmiştir. Genellikle bir veya daha fazla aşırı yükleme varsayılan ayarları kabul ederken diğerleri varsayılanları kabul etmez ve bunun yerine dizelerin tam olarak nasıl karşılaştırılacağını veya değiştirileceğini tanımlar. Varsayılan değerleri kullanmayan yöntemlerin çoğu, dize karşılaştırma kurallarını kültür ve büyük/küçük harfe göre açıkça belirten bir numaralandırma olan <xref:System.StringComparison> türü bir parametre içerir. Aşağıdaki tablo, <xref:System.StringComparison> numaralandırma üyelerini açıklar.

|StringComparison üyesi|Description|
|-----------------------------|-----------------|
|<xref:System.StringComparison.CurrentCulture>|Geçerli kültürü kullanarak büyük/küçük harfe duyarlı bir karşılaştırma gerçekleştirir.|
|<xref:System.StringComparison.CurrentCultureIgnoreCase>|Geçerli kültürü kullanarak büyük/küçük harfe duyarsız bir karşılaştırma gerçekleştirir.|
|<xref:System.StringComparison.InvariantCulture>|Sabit kültürü kullanarak büyük/küçük harfe duyarlı bir karşılaştırma gerçekleştirir.|
|<xref:System.StringComparison.InvariantCultureIgnoreCase>|Sabit kültürü kullanarak büyük/küçük harfe duyarsız bir karşılaştırma gerçekleştirir.|
|<xref:System.StringComparison.Ordinal>|Sıralı bir karşılaştırma gerçekleştirir.|
|<xref:System.StringComparison.OrdinalIgnoreCase>|Büyük/küçük harfe duyarlı olmayan sıralı bir karşılaştırma gerçekleştirir.|

Örneğin, bir karakteri veya bir dizeyi eşleştiren bir <xref:System.String.IndexOf%2A> nenesindeki alt dizine ait dizeyi döndüren <xref:System.String> yönteminin dokuz aşırı yüklemesi vardır:

- Varsayılan olarak dizedeki bir karakter için sıralı bir arama (büyük/küçük harfe duyarlı ve kültüre duyarsız) gerçekleştiren <xref:System.String.IndexOf%28System.Char%29>, <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%29> ve <xref:System.String.IndexOf%28System.Char%2CSystem.Int32%2CSystem.Int32%29>.
- Dizedeki bir alt dize için varsayılan olarak büyük/küçük harfe ve kültüre duyarlı bir arama gerçekleştiren <xref:System.String.IndexOf%28System.String%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%29> ve <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%29>.
- Karşılaştırma biçiminin belirlenmesini sağlayan <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29> türü bir parametreyi içeren <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.StringComparison%29>, <xref:System.String.IndexOf%28System.String%2CSystem.Int32%2CSystem.Int32%2CSystem.StringComparison%29> ve <xref:System.StringComparison>.

Aşağıdaki nedenlerden dolayı varsayılan değerleri kullanmayan bir aşırı yükleme seçmenizi öneririz:

- Varsayılan parametreleri olan bazı aşırı yüklemeler (dize örneğinde bir <xref:System.Char> arayanlar) sıralı bir karşılaştırma gerçekleştirirken diğerleri (dize örneğinde bir dize arayanlar), kültüre duyarlıdır. Hangi yöntemin hangi varsayılan değeri kullandığını hatırlamak zordur ve aşırı yüklemeler kolayca karıştırılabilir.
- Yöntem çağrıları için varsayılan değerleri kullanan kodun amacı açık değildir. Varsayılan değerleri kullanan aşağıdaki örnekte, geliştiricinin iki dizenin karşılaştırmasını sıralı mı yoksa dilsel mi yapmayı amaçladığını yoksa `protocol` ve "http" arasındaki bir büyük/küçük harf farkının eşitlik testinin `false` dönmesine neden olup olmayacağını bilmek zordur.

     [!code-csharp[Conceptual.Strings.BestPractices#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#1)]
     [!code-vb[Conceptual.Strings.BestPractices#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#1)]

Genelde, kodun amacını belirsiz yaptığından varsayılan değerleri kullanmayan bir yöntemi çağırmanızı öneririz. Bu sayede kod daha okunabilir olur ve hata ayıklaması ve bakımı daha kolay hale gelir. Aşağıdaki örnek, önceki örnekle ilgili oluşturulan soruları ele alır. Sıralı karşılaştırmanın kullanıldığını ve büyük/küçük harfteki farkların yok sayıldığını belirtir.

[!code-csharp[Conceptual.Strings.BestPractices#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/explicitargs1.cs#2)]
[!code-vb[Conceptual.Strings.BestPractices#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/explicitargs1.vb#2)]

## <a name="the-details-of-string-comparison"></a>Dize karşılaştırmasının ayrıntıları

Dize karşılaştırma, özellikle sıralama ve eşitlik testi gibi, dizeyle ilgili pek çok işlemin temelidir. Dizeler belirli bir düzende sıralanır: Eğer dizelerin sıralı bir listesinde "my" dizesi "string" dizesinden önce görünüyorsa, "my" dizesi "string" dizesi ile karşılaştırıldığında daha küçük veya eşit olmalıdır. Ek olarak, karşılaştırma dolaylı olarak eşitliği tanımlar. Karşılaştırma işlemi, eşit olarak gördüğü dizeler için sıfır döndürür. İki dizenin de diğerinden daha az olmaması iyi bir yorumdur. Dizeleri içeren en anlamlı işlemler, şu yordamların birini veya her ikisini içerir: başka bir dize ile karşılaştırma ve iyi tanımlanmış bir sıralama işlemini yürütme.

> [!NOTE]
> [Sıralama ağırlığı tablolarını](https://www.microsoft.com/download/details.aspx?id=10921), Windows işletim sistemleri için sıralama ve karşılaştırma işlemlerinde kullanılan karakter ağırlıklarını ve [varsayılan Unicode harmanlama öğesi tablosu](https://www.unicode.org/Public/UCA/latest/allkeys.txt), Linux ve MacOS için sıralama ağırlığı tablosunun en son sürümünü içeren bir metin dosyası kümesi indirebilirsiniz. Linux ve macOS üzerindeki sıralama ağırlığı tablosunun belirli sürümü sistemde yüklü olan [Unicode kitaplıklarının Uluslararası bileşenlerinin](http://site.icu-project.org/) sürümüne bağlıdır. ICU sürümleri ve uygulamadıkları Unicode sürümleri hakkında bilgi için, bkz. [ICU indirme](http://site.icu-project.org/download).

Ancak, iki dizeyi eşitlik veya sıralama düzeni için değerlendirmek tek bir doğru sonuç vermez; sonuç, dizeleri karşılaştırmakta kullanılan ölçütlere bağlıdır. Özellikle, sıralı olan veya geçerli kültürün büyük/küçük harf ve sıralama kurallarına dayalı dize karşılaştırmaları veya [sabit kültür](xref:System.Globalization.CultureInfo.InvariantCulture) (İngilizce dili temel alan yerel ayar belirsiz kültür) farklı sonuçlar üretebilir.

Ayrıca, .NET 'in farklı sürümlerini kullanan veya farklı işletim sistemlerinde ya da işletim sistemi sürümlerindeki .NET kullanan dize karşılaştırmaları farklı sonuçlar döndürebilir. Daha fazla bilgi için bkz. [dizeler ve Unicode standart](xref:System.String#Unicode).

### <a name="string-comparisons-that-use-the-current-culture"></a>Geçerli kültürü kullanan dize karşılaştırmaları

Ölçütlerden biri, dizeleri karşılaştırırken geçerli kültüre ait kuralların kullanılmasını içerir. Geçerli kültürü temel alan karşılaştırmalar iş parçacığının geçerli kültürünü veya yerel ayarlarını kullanır. Kültür Kullanıcı tarafından ayarlanmamışsa, Denetim Masası 'ndaki **Bölgesel Seçenekler** penceresinde varsayılan ayar olarak ayarlanır. Veriler dilsel olduğunda ve kültüre duyarlı kullanıcı etkileşimini yansıttığında her zaman geçerli kültürü temel alan karşılaştırmalar kullanmalısınız.

Ancak, kültür değiştiğinde .NET 'teki karşılaştırma ve büyük/küçük harf davranışı değişir. Bu, bir uygulama geliştirildiği bilgisayardakinden farklı bir kültüre sahip olan başka bir bilgisayarda yürütüldüğünde veya uygulamayı yürüten iş parçacığı kültürünü değiştirdiğinde gerçekleşir. Bu davranış kasıtlıdır, ancak çoğu geliştirici için belirgin değildir. Aşağıdaki örnek, sıralama düzeninin A.B.D. İngilizce ("en-US") ve İsveççe ("sv-SE") kültürleri arasındaki farkını gösterir. "Ångström", "Windows" ve "Visual Studio" sözcüklerinin sıralanmış dize dizilerindeki farklı konumlarda göründüğünü unutmayın.

[!code-csharp[Conceptual.Strings.BestPractices#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison1.cs#3)]
[!code-vb[Conceptual.Strings.BestPractices#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison1.vb#3)]

Geçerli kültürü kullanan ve büyük/küçük harfe duyarlı olmayan karşılaştırmalar, kültüre duyarlı karşılaştırmalarla aynıdır, ancak iş parçacığının geçerli kültürü tarafından belirtilen büyük/küçük harfi göz ardı eder. Bu davranış kendisini sıralama düzenlerinde de gösterebilir.

Geçerli kültürün semantiklerini kullanan karşılaştırmalar aşağıdaki yöntemler için varsayılan değerdir:

- Bir <xref:System.String.Compare%2A?displayProperty=nameWithType> parametresi içermeyen <xref:System.StringComparison> aşırı yüklemeleri.
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType> aşırı yüklemeleri.
- Varsayılan <xref:System.String.StartsWith%28System.String%29?displayProperty=nameWithType> yöntemi ve bir <xref:System.String.StartsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>`null` parametresi olan <xref:System.Globalization.CultureInfo> yöntemi.
- Varsayılan <xref:System.String.EndsWith%28System.String%29?displayProperty=nameWithType> yöntemi ve bir <xref:System.String.EndsWith%28System.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>`null` parametresi olan <xref:System.Globalization.CultureInfo> yöntemi.
- Arama parametresi olarak bir <xref:System.String.IndexOf%2A?displayProperty=nameWithType>'i kabul eden ve bir <xref:System.String> parametresi olmayan <xref:System.StringComparison> aşırı yüklemeleri.
- Arama parametresi olarak bir <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>'i kabul eden ve bir <xref:System.String> parametresi olmayan <xref:System.StringComparison> aşırı yüklemeleri.

Her durumda, metodun çağrı amacını belli etmek için <xref:System.StringComparison> parametresi olan bir aşırı yüklemeyi çağırmanızı öneririz.

Dilsel olmayan veriler dilsel olarak yorumlandığında veya belirli bir kültürdeki dize verileri başka bir kültürün kuralları kullanılarak yorumlandığında küçük ve küçük olmayan hatalar oluşabilir. Kurallı örnek, Türkçe-I sorunudur.

A.B.D. İngilizce dahil olmak üzere neredeyse tüm Latin alfabelerinde, "i" karakteri (\u0069) "I" karakterinin (\u0049) küçük harfli halidir. Bu büyük/küçük harf kuralı bunun gibi bir kültürde programlama yapan birisi için hızla varsayılan hale gelir. Ancak, Türkçe ("tr-TR") alfabesi, "i" karakterinin büyük harfli hali olan "Noktalı I" karakteri, yani "İ" (\u0130) içerir. Türkçe ayrıca büyük harfi "I" olan "noktasız i", yani "ı" (\u0131) karakterini içerir. Bu davranış Azerbaycan dili ("az") kültüründe de bulunur.

Bu nedenle, "i" harfini büyük harfe dönüştürmek veya "I" harfini küçük harfe dönüştürmek hakkındaki varsayımlar her kültürde geçerli değildir. Eğer dize karşılaştırma yordamları için varsayılan aşırı yüklemeleri kullanırsanız, bunlar kültürler arasındaki farktan etkilenir. Eğer karşılaştırılacak veriler dilsel değilse, aşağıdaki "file" ve "FILE" dizelerinin büyük/küçük harfe duyarlı olmayan karşılaştırması örneğinin gösterdiği üzere varsayılan aşırı yüklemeleri kullanmak, istenmeyen sonuçlara neden olabilir.

[!code-csharp[Conceptual.Strings.BestPractices#11](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#11)]
[!code-vb[Conceptual.Strings.BestPractices#11](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#11)]

Bu karşılaştırma, eğer kültür güvenliğe duyarlı yerlerde farkında olunmadan kullanılıyorsa aşağıdaki örnekteki gibi önemli sorunlara neden olabilir. `IsFileURI("file:")` gibi bir yöntem çağrısı, eğer geçerli kültür A.B.D. İngilizce ise `true`'i döndürürken, geçerli kültür Türkçe ise `false`'i döndürür. Bu nedenle, Türkçe sistemlerde "FILE:" ile başlayan büyük/küçük harfe duyarsız URI değerlerine olan erişimi engelleyen güvenlik önlemleri aşılabilir.

[!code-csharp[Conceptual.Strings.BestPractices#12](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#12)]
[!code-vb[Conceptual.Strings.BestPractices#12](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#12)]

Bu durumda, "dosya:" dilsel olmayan ve kültüre duyarsız bir tanımlayıcı olarak yorumlanmak üzere olduğu için, kod aşağıdaki örnekte gösterildiği gibi yazılmalıdır:

[!code-csharp[Conceptual.Strings.BestPractices#13](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/turkish1.cs#13)]
[!code-vb[Conceptual.Strings.BestPractices#13](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/turkish1.vb#13)]

### <a name="ordinal-string-operations"></a>Sıralı dize işlemleri

Bir yöntem çağrısında <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> veya <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> değerini belirtmek, doğal dillerin özelliklerinin göz ardı edildiği dilsel olmayan bir karşılaştırmayı belirtir. Bu <xref:System.StringComparison> değerleriyle çağırılan yöntemler, temel dize işlemi kararlarında kültür tarafından parametre haline getirilen büyük/küçük harf veya eşitlik tabloları yerine basit bayt karşılaştırmalarını temel alır. Çoğu durumda, bu yaklaşım dizelerin istenen şekilde yorumlanmasının yanı sıra kodun daha hızlı ve daha güvenilir olmasını sağlar.

Sıralı karşılaştırmalar, her dizeye ait her baytın dilsel yorumlama olmadan karşılaştırıldığı dize karşılaştırmalarıdır; örneğin, "windows" ile "Windows" eşleşmez. Bu aslında C çalışma zamanı `strcmp` işlevine yapılan bir çağrıdır. Bağlam, dizelerin tam olarak karşılaşmasını gerektirdiğinde veya koruyucu bir eşleştirme ilkesine sahip olduğunda bu karşılaştırmayı kullanın. Ek olarak, sıralı karşılaştırma, sonuç oluştururken dilsel kurallar uygulamadığından en hızlı karşılaştırma işlemidir.

.NET 'teki dizeler, gömülü null karakterleri içerebilir. Sıralı ve kültüre duyarlı karşılaştırmalar (sabit kültür kullanan karşılaştırmalar dahil) arasındaki en belirgin farklardan biri bir dizedeki gömülü null karakterlerin işlenmesiyle ilgilidir. Bu karakterler, kültüre duyarlı karşılaştırmalar (sabit kültür kullanan karşılaştırmalar dahil) yapmak için <xref:System.String.Compare%2A?displayProperty=nameWithType> ve <xref:System.String.Equals%2A?displayProperty=nameWithType> yöntemlerini kullandığınızda yok sayılır. Sonuç olarak, kültüre duyarlı karşılaştırmalarda, gömülü null karakterleri içeren dizeler, bunları içermeyen dizelerle eşit kabul edilebilir.

> [!IMPORTANT]
> Dize karşılaştırma yöntemleri gömülü null karakterleri yok saysa da, <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.EndsWith%2A?displayProperty=nameWithType>, <xref:System.String.IndexOf%2A?displayProperty=nameWithType>, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> ve <xref:System.String.StartsWith%2A?displayProperty=nameWithType> gibi dize arama yöntemleri bu karakterleri yok saymaz.

Aşağıdaki örnek, "A" ve "a" arasında birden fazla katıştırılmış null karakter içeren benzer bir dizeyle "AA" dizesinin kültüre duyarlı bir karşılaştırmasını gerçekleştirir ve iki dizenin nasıl eşit kabul edileceğini gösterir:

[!code-csharp[Conceptual.Strings.BestPractices#19](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls1.cs#19)]
 [!code-vb[Conceptual.Strings.BestPractices#19](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls1.vb#19)]

Ancak, aşağıdaki örnekte gösterildiği gibi, sıralı karşılaştırma kullandığınızda dizeler eşit kabul edilmez:

[!code-csharp[Conceptual.Strings.BestPractices#20](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/embeddednulls2.cs#20)]
[!code-vb[Conceptual.Strings.BestPractices#20](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/embeddednulls2.vb#20)]

Büyük/küçük harfe duyarsız sıralı karşılaştırmalar bundan sonraki en koruyucu yaklaşımdır. Bu karşılaştırmalar, çoğu büyük/küçük harfi yok sayar; örneğin, "windows" ile "Windows" eşleşir. ASCII karakterleri ile çalışırken bu ilke <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> ile eşdeğerdir, ancak tek farkı genel ASCII büyük/küçük harflerini yok saymasıdır. Bu nedenle, [A, Z] (\u0041-\u005A) içindeki herhangi bir karakter [a,z] (\u0061-\007A) içindeki karşılık gelen karakterle eşleşir. ASCII aralığı dışındaki büyük/küçük harf kuralları sabit kültürün tablolarını kullanır. Bu nedenle, aşağıdaki karşılaştırma:

[!code-csharp[Conceptual.Strings.BestPractices#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#4)]
[!code-vb[Conceptual.Strings.BestPractices#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#4)]

bu karşılaştırmaya eşdeğerdir (ancak daha hızlıdır):

[!code-csharp[Conceptual.Strings.BestPractices#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison2.cs#5)]
[!code-vb[Conceptual.Strings.BestPractices#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison2.vb#5)]

Bu karşılaştırmalar yine de çok hızlıdır.

<xref:System.StringComparison.Ordinal?displayProperty=nameWithType> ve <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType>'in her ikisi de doğrudan ikili değerleri kullanır ve eşleştirme için idealdir. Karşılaştırma ayarlarınızdan emin olmadığınızda, bu iki değerden birini kullanın. Ancak, bayt bayt karşılaştırma yaptıkları için bunlar, bir dilsel sıralama düzeninde (bir İngilizce sözlüğü gibi) değil, ikili sıralama düzeninde sıralarlar. Sonuçlar kullanıcılara görüntülenirse çoğu bağlamda tuhaf görünebilir.

Sıralı semantikler, bir <xref:System.String.Equals%2A?displayProperty=nameWithType> bağımsız değişkeni içermeyen <xref:System.StringComparison> aşırı yüklemeleri için (eşitlik işleci dahil) varsayılandır. Her durumda <xref:System.StringComparison> parametresi olan bir aşırı yüklemeyi çağırmanızı öneririz.

### <a name="string-operations-that-use-the-invariant-culture"></a>Sabit kültür kullanan dize işlemleri

Sabit kültürle yapılan karşılaştırmalar, statik <xref:System.Globalization.CultureInfo.CompareInfo%2A> özelliği tarafından döndürülen <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliğini kullanır. Bu davranış tüm sistemlerde aynıdır; aralığı dışındaki karakterleri eşdeğer sabit karakter olarak düşündüğü karakterlere çevirir. Bu ilke, kültürler arası tek bir dize davranışı bulundurmak için kullanışlı olabilir, ancak genellikle beklenmeyen sonuçlar sağlar.

Sabit kültürle yapılan büyük/küçük harfe duyarsız karşılaştırmalar, karşılaştırma bilgisi için statik <xref:System.Globalization.CultureInfo.CompareInfo%2A> özelliğinden döndürülen statik <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliğini kullanır. Bu çevrilen karakterler arasındaki tüm büyük/küçük harf farkları yok sayılır.

<xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> ve <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> kullanan karşılaştırmalar ASCII dizelerinde de aynı şekilde çalışır. Ancak <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType>, bir bayt kümesi olarak yorumlanması gereken dizeler için uygun olmayabilecek dilsel kararlar alır. `CultureInfo.InvariantCulture.CompareInfo` nesnesi <xref:System.String.Compare%2A> yönteminin belirli karakter kümelerini eşdeğer olarak yorumlamasını sağlar. Örneğin, aşağıdaki eşitlik sabit kültürde geçerlidir:

InvariantCulture: a + ̊ = å

LATIN KÜÇÜK HARF A karakteri "a" (\u0061), ÜSTTEKİ BİRLEŞEN DAİRE karakterinin "+ " ̊" (\u030a) yanında olduğunda, ÜSTÜNDE DAİRE OLAN LATIN KÜÇÜK A HARFİ karakteri "å" (\u00e5) olarak yorumlanır. Aşağıdaki örnekte gösterildiği gibi bu davranış, sıralı karşılaştırmadan farklıdır.

[!code-csharp[Conceptual.Strings.BestPractices#15](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/comparison3.cs#15)]
[!code-vb[Conceptual.Strings.BestPractices#15](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/comparison3.vb#15)]

Dosya adlarını, tanımlama bilgilerini veya "å" gibi bir birleşimin görünebileceği başka herhangi bir şeyi yorumlarken, sıralı karşılaştırmalar yine de en saydam ve sığdırma davranışını sunmaktadır.

Buna karşılık, sabit kültürün karşılaştırma için kullanışlı olan çok az özelliği vardır. Karşılaştırmayı dilsel olarak yaptığı için tam simgesel eşitliğin sağlanacağından emin olamaz, ancak herhangi bir kültürdeki görüntüleme için tercih edilmez. Karşılaştırma için <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> kullanmanın birkaç nedeninden biri, kültürler arası aynı görüntülenmesi için sıralanan verilerin kalıcı hale getirilmesidir. Örneğin bir uygulamanın yanında, görüntülenecek bir sıralı tanımlayıcılar listesi içeren büyük bir veri dosyası varsa bu listeye ekleme yapmak sabit stil sıralama ile eklemeyi gerektirir.

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Yöntem çağrlarınız için StringComparison üyesi seçme

Aşağıdaki tabloda anlam dizesi bağlamından bir numaralandırma üyesine yönelik eşleme özetlenmektedir <xref:System.StringComparison> :

|Veriler|Davranış|İlgili System.StringComparison<br /><br /> değer|
|----------|--------------|-----------------------------------------------------|
|Büyük/küçük harfe duyarlı dahili tanımlayıcılar.<br /><br /> XML ve HTTP gibi standartlardaki büyük/küçük harfe duyarlı tanımlayıcılar.<br /><br /> Güvenlikle ilgili büyük/küçük harfe duyarlı ayarlar.|Baytların tam olarak eşleştiği dilsel olmayan bir tanımlayıcı.|<xref:System.StringComparison.Ordinal>|
|Büyük/küçük harfe duyarsız iç tanımlayıcılar.<br /><br /> XML ve HTTP gibi standartlardaki büyük/küçük harfe duyarsız tanımlayıcılar.<br /><br /> Dosya yolları.<br /><br /> Kayıt defteri anahtarları ve değerleri.<br /><br /> Ortam değişkenleri.<br /><br /> Kaynak tanımlayıcıları (örneğin, işleyici adları).<br /><br /> Güvenlikle ilgili büyük/küçük harfe duyarsız ayarlar.|Büyük/küçük harfin alakasız olduğu dilsel olmayan bir tanımlayıcı; özellikle çoğu Windows sistem hizmetinde depolanan veriler.|<xref:System.StringComparison.OrdinalIgnoreCase>|
|Kalıcı olan bazı dilsel veriler.<br /><br /> Sabit bir sıralama düzeni gerektiren dilsel verinin görüntülenmesi.|Dilsel olan ancak kültüre duyarlı olmayan veri.|<xref:System.StringComparison.InvariantCulture><br /><br /> -veya-<br /><br /> <xref:System.StringComparison.InvariantCultureIgnoreCase>|
|Kullanıcıya görüntülenen veri.<br /><br /> Çoğu kullanıcı girişi.|Yerel dilsel özellikleri gerektiren veriler.|<xref:System.StringComparison.CurrentCulture><br /><br /> -veya-<br /><br /> <xref:System.StringComparison.CurrentCultureIgnoreCase>|

## <a name="common-string-comparison-methods-in-net"></a>.NET 'teki ortak dize karşılaştırma yöntemleri

Aşağıdaki bölümlerde, en yaygın olarak dize karşılaştırmaları için kullanılan yöntemler açıklanır.

### <a name="stringcompare"></a>String.Compare

Varsayılan yorum: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Dize yorumlamak için en önemli işlem olarak bu yöntem çağrılarının tüm örnekleri, dizelerin geçerli kültüre göre mi yoksa geçerli kültürden bağımsız (simgesel) olarak mı yorumlanacağını belirlemek için incelenmelidir. Genellikle ikincisidir ve yerine bir <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> karşılaştırması kullanılmalıdır.

<xref:System.Globalization.CompareInfo?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> sınıfı, aynı zamanda <xref:System.Globalization.CompareInfo.Compare%2A> bayrak sabit listesini kullanarak çok sayıda eşleştirme seçeneği (sıralı, boşluğu göz ardı ederek, kana türünü göz ardı ederek vb.) sunan bir <xref:System.Globalization.CompareOptions> yöntemi de içerir.

### <a name="stringcompareto"></a>String.CompareTo

Varsayılan yorum: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Bu yöntem şu anda bir <xref:System.StringComparison> türü belirten bir aşırı yüklemeye sahip değildir. Bu yöntemi, önerilen <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> biçimine dönüştürmek genellikle mümkündür.

<xref:System.IComparable> ve <xref:System.IComparable%601> arabirimlerini uygulayan türler bu yöntemi uygular. Bir <xref:System.StringComparison> parametresi seçeneğini sunmadığı için, türleri uygulamak genellikle kullanıcının oluşturucuda bir <xref:System.StringComparer> belirtmesine olanak sağlar. Aşağıdaki örnek, sınıf oluşturucusu bir `FileName` parametresi içeren bir <xref:System.StringComparer> sınıfını tanımlar. Bu <xref:System.StringComparer> nesnesi daha sonra `FileName.CompareTo` yönteminde kullanılır.

[!code-csharp[Conceptual.Strings.BestPractices#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/api1.cs#6)]
[!code-vb[Conceptual.Strings.BestPractices#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/api1.vb#6)]

### <a name="stringequals"></a>String.Equals

Varsayılan yorum: <xref:System.StringComparison.Ordinal?displayProperty=nameWithType>.

<xref:System.String> sınıfı, statik veya örnek <xref:System.String.Equals%2A> yöntemi aşırı yüklemelerini çağırarak veya statik eşitlik işlecini kullanarak eşitliği test etmenizi sağlar. Aşırı yüklemeler ve işleç, varsayılan olarak sıralı karşılaştırma kullanır. Ancak, sıralı karşılaştırma yapmak isteseniz bile <xref:System.StringComparison> türünü açıkça belirten bir aşırı yükleme çağırmanızı öneririz, çünkü bu, belirli bir dize yorumu için kodda arama yapmanızı kolaylaştırır.

### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper ve String.ToLower

Varsayılan yorum: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Ve yöntemlerini kullanırken dikkatli olun <xref:System.String.ToUpper?displayProperty=nameWithType> <xref:System.String.ToLower?displayProperty=nameWithType> , çünkü bir dizeyi büyük veya küçük harfe zorlamak, genellikle dizeleri büyük/küçük harf olarak karşılaştırmak için küçük bir normalleştirme olarak kullanılır. Bu durumda, büyük/küçük harfe duyarsız bir karşılaştırma kullanmayı düşünün.

Aynı zamanda <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> ve <xref:System.String.ToLowerInvariant%2A?displayProperty=nameWithType> yöntemleri de mevcuttur. <xref:System.String.ToUpperInvariant%2A>, büyük/küçük harfi normalleştirmek için standart yöntemdir. <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> kullanılarak yapılan karşılaştırmalar, davranışsal olarak iki çağrının birleşimidir: her iki dize bağımsız değişkeninde <xref:System.String.ToUpperInvariant%2A>'i çağırmak ve <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> kullanarak bir karşılaştırma yapmak.

Aşırı yüklemeler aynı zamanda, yöntemde kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesini geçirerek belirli bir kültürde büyük harfe ve küçük harfe dönüştürme için de kullanılabilir.

### <a name="chartoupper-and-chartolower"></a>Char.ToUpper ve Char.ToLower

Varsayılan yorum: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

<xref:System.Char.ToUpper(System.Char)?displayProperty=nameWithType>Ve <xref:System.Char.ToLower(System.Char)?displayProperty=nameWithType> yöntemleri, <xref:System.String.ToUpper?displayProperty=nameWithType> <xref:System.String.ToLower?displayProperty=nameWithType> önceki bölümde açıklanan ve yöntemlerine benzer şekilde çalışır.

### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith ve String.EndsWith

Varsayılan yorum: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Varsayılan olarak, bu yöntemlerin ikisi de kültüre duyarlı bir karşılaştırma yapar.

### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf ve String.LastIndexOf

Varsayılan yorum: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Bu yöntemlere ait varsayılan aşırı yüklemelerin karşılaştırmaları yapma şekillerinde bir tutarsızlık vardır. Bir <xref:System.String.IndexOf%2A?displayProperty=nameWithType> parametresi içeren tüm <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> ve <xref:System.Char> yöntemleri sıralı karşılaştırma yapar, ancak bir <xref:System.String.IndexOf%2A?displayProperty=nameWithType> parametresi içeren varsayılan <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> ve <xref:System.String> yöntemleri kültüre duyarlı bir karşılaştırma yapar.

Eğer <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> veya <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> yöntemini çağırıp geçerli örnekte konumlandırılacak bir dizeye geçirirseniz, <xref:System.StringComparison> türünü açıkça belirten bir aşırı yüklemeyi çağırmanızı öneririz. Bir <xref:System.Char> bağımsız değişkenini içeren aşırı yüklemeler bir <xref:System.StringComparison> türü belirtmenizi sağlar.

## <a name="methods-that-perform-string-comparison-indirectly"></a>Dolaylı olarak dize karşılaştırması gerçekleştiren Yöntemler

Merkezi işlem olarak dize karşılaştırmasına sahip olan dize olmayan bazı yöntemler <xref:System.StringComparer> türünü kullanır. <xref:System.StringComparer> sınıfı, <xref:System.StringComparer> yöntemleri aşağıdaki türde dize karşılaştırması yapan <xref:System.StringComparer.Compare%2A?displayProperty=nameWithType> örneklerini döndüren altı statik özelliği içerir:

- Geçerli kültürü kullanarak kültüre duyarlı dize karşılaştırmaları. Bu <xref:System.StringComparer> nesnesi, <xref:System.StringComparer.CurrentCulture%2A?displayProperty=nameWithType> özelliği tarafından döndürülür.
- Geçerli kültürü kullanarak büyük/küçük harfe duyarsız karşılaştırmalar. Bu <xref:System.StringComparer> nesnesi, <xref:System.StringComparer.CurrentCultureIgnoreCase%2A?displayProperty=nameWithType> özelliği tarafından döndürülür.
- Sabit kültürün sözcük karşılaştırma kurallarını kullanarak kültüre duyarsız karşılaştırmalar. Bu <xref:System.StringComparer> nesnesi, <xref:System.StringComparer.InvariantCulture%2A?displayProperty=nameWithType> özelliği tarafından döndürülür.
- Sabit kültürün sözcük karşılaştırma kurallarını kullanarak büyük/küçük harfe ve kültüre duyarsız karşılaştırmalar. Bu <xref:System.StringComparer> nesnesi, <xref:System.StringComparer.InvariantCultureIgnoreCase%2A?displayProperty=nameWithType> özelliği tarafından döndürülür.
- Sıralı karşılaştırma. Bu <xref:System.StringComparer> nesnesi, <xref:System.StringComparer.Ordinal%2A?displayProperty=nameWithType> özelliği tarafından döndürülür.
- Büyük/küçük harfe duyarsız sıralı karşılaştırma. Bu <xref:System.StringComparer> nesnesi, <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> özelliği tarafından döndürülür.

### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort ve Array.BinarySearch

Varsayılan yorum: <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType>.

Herhangi bir veriyi bir koleksiyonda depoladığınızda veya bir dosyadan veya veritabanından kalıcı hale getirilmiş veriyi bir koleksiyonun içine okuduğunuzda geçerli kültürün değiştirilmesi, koleksiyon içindeki sabitleri geçersiz kılabilir. <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> yöntemi, aranacak dizideki öğelerin zaten sıralı olduğunu varsayar. <xref:System.Array.Sort%2A?displayProperty=nameWithType> yöntemi, dizideki herhangi bir dize öğesini sıralamak için, ayrı ayrı öğeleri düzenlemek amacıyla <xref:System.String.Compare%2A?displayProperty=nameWithType> yöntemini çağırır. Kültüre duyarlı bir karşılaştırıcı kullanmak, eğer dizi sıralanana ve içerikleri aranana kadar geçen zaman arasında kültür değişirse tehlikeli olabilir. Örneğin aşağıdaki kodda depolama ve alma işlemleri, `Thread.CurrentThread.CurrentCulture` özelliği tarafından dolaylı olarak sağlanan karşılaştırıcıda gerçekleşir. Eğer kültür `StoreNames` ve `DoesNameExist` arasında değişebilirse ve özellikle dizi içerikleri iki yöntem çağrısı arasında bir yerde kalıcı hale getirilirse, ikili arama başarısız olabilir.

[!code-csharp[Conceptual.Strings.BestPractices#7](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#7)]
 [!code-vb[Conceptual.Strings.BestPractices#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#7)]

Aşağıdaki örnekte, diziyi sıralamak ve aramak için aynı sıralı (kültüre duyarsız) karşılaştırma yöntemini kullanan önerilen bir yöntem görünür. Değişim kodu, iki örnekte `Line A` ve `Line B` olarak etiketlenen satırlarda yansıtılır.

[!code-csharp[Conceptual.Strings.BestPractices#8](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#8)]
[!code-vb[Conceptual.Strings.BestPractices#8](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#8)]

Eğer bu veriler kalıcı hale getirilirse ve kültürler arasında taşınırsa, ve kullanıcıya bu verileri sunmak için sıralama kullanılırsa, dilsel olarak daha iyi kullanıcı çıktısı için çalışan, ancak kültür değişikliklerinden etkilenmeyen <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> öğesini kullanmayı düşünebilirsiniz. Aşağıdaki örnek, diziyi sıralamak ve aramak üzere sabit kültürü kullanmak için önceki iki örneği değiştirir.

[!code-csharp[Conceptual.Strings.BestPractices#9](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect1.cs#9)]
[!code-vb[Conceptual.Strings.BestPractices#9](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect1.vb#9)]

### <a name="collections-example-hashtable-constructor"></a>Koleksiyonlar örneği: Hashtable Oluşturucusu

Karma dizeleri, dizelerin karşılaştırılma şeklinden etkilenen bir işlemin ikinci bir örneğini sağlar.

Aşağıdaki örnek, <xref:System.Collections.Hashtable> özelliği tarafından döndürülen <xref:System.StringComparer> nesnesini geçirerek bir <xref:System.StringComparer.OrdinalIgnoreCase%2A?displayProperty=nameWithType> nesnesi oluşturur. <xref:System.StringComparer>'dan türetilen bir <xref:System.StringComparer> sınıfı <xref:System.Collections.IEqualityComparer> arabirimini uyguladığından <xref:System.Collections.IEqualityComparer.GetHashCode%2A> yöntemi, karma tablosundaki dizelerin karma kodunu hesaplamak için kullanılır.

[!code-csharp[Conceptual.Strings.BestPractices#10](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.bestpractices/cs/indirect2.cs#10)]
[!code-vb[Conceptual.Strings.BestPractices#10](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.bestpractices/vb/indirect2.vb#10)]

## <a name="see-also"></a>Ayrıca bkz.

- [.NET uygulamalarında Genelleştirme](../globalization-localization/globalization.md)
