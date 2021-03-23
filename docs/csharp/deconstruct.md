---
title: Demetleri ve diğer türleri ayrıştırma
description: Tanımlama gruplarını ve diğer türleri oluşturmayı öğrenin.
ms.technology: csharp-fundamentals
ms.date: 03/22/2021
ms.openlocfilehash: acacfb6a9401a3a888f9b8226798c95578f9fa45
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875830"
---
# <a name="deconstructing-tuples-and-other-types"></a>Demetleri ve diğer türleri ayrıştırma

Kayıt düzeni, bir yöntem çağrısından birden çok değer almanın hafif bir yolunu sağlar. Ancak, tanımlama grubunu aldıktan sonra ayrı öğelerini işlemeniz gerekir. Bu işlem, aşağıdaki örnekte gösterildiği gibi, öğe temelinde tek yapmanız gereken bir öğedir. `QueryCityData`Yöntemi 3 tanımlama grubu döndürür ve öğelerinden her biri ayrı bir işlemde bir değişkene atanır.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Bir nesneden birden çok alan ve özellik değeri alınması eşit bir şekilde olabilir: üye üye temelinde bir değişkene bir alan veya özellik değeri atamanız gerekir.

C# 7,0 ' den başlayarak, bir tanımlama grubundan birden fazla öğe alabilir veya tek bir *Yapı* işlemindeki bir nesneden birden fazla alan, özellik ve hesaplanan değer alabilirsiniz. Bir tanımlama grubu oluştururken, öğelerini ayrı değişkenlere atarsınız. Bir nesneyi kaldırdığınızda, seçili değerleri ayrı değişkenlere atarsınız.

## <a name="deconstructing-a-tuple"></a>Kayıt düzeni kaldırma

C# özellikleri, tek bir işlemde bir kayıt grubundaki tüm öğeleri paketlemenizi sağlayan tanımlama grupları için yerleşik destek sunar. Bir kayıt düzeni oluşturmak için genel sözdizimi, bir tanımlama sözdizimine benzer. bir atama ifadesinin sol tarafında parantez içine atanacak olan değişkenleri çevrelemektir. Örneğin, aşağıdaki ifade 4 kayıt öğelerinin öğelerini dört ayrı değişkene atar:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Tanımlama grubu oluşturmanın üç yolu vardır:

- Her alanın türünü parantez içinde açık bir şekilde bildirebilirsiniz. Aşağıdaki örnek, yöntemi tarafından döndürülen 3 kayıt düzeni oluşturmak için bu yaklaşımı kullanır `QueryCityData` .

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- `var`C# ' ın her değişkenin türünü bilmesi için anahtar sözcüğünü kullanabilirsiniz. `var`Anahtar sözcüğünü parantezlerin dışında yerleştirebilirsiniz. Aşağıdaki örnek, yöntem tarafından döndürülen 3 kayıt düzeni oluştururken tür çıkarımı kullanır `QueryCityData` .

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    `var`Anahtar sözcüğünü, parantez içindeki değişken bildirimlerinin herhangi biri veya tümü ile ayrı ayrı de kullanabilirsiniz.

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    Bu, kısabera ve önerilmez.

- Son olarak, tanımlama grubunu zaten önceden tanımlanmış değişkenler halinde oluşturabilirsiniz.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Kayıt grubundaki her alan aynı türde olsa bile, parantez dışında belirli bir tür belirtemezsiniz. Bu bir derleyici hatası oluşturur CS8136, "Deinşaat" var (...) ' formu, ' var ' için belirli bir türe izin vermez. ".

Ayrıca, kayıt düzeni öğelerinin her birini bir değişkene atamanız gerektiğini unutmayın. Herhangi bir öğeyi atlarsanız, derleyici CS8132 hatasını üretir, "' x ' öğelerinden oluşan bir demet ' y ' değişkenlerine parçalanamaz."

Bir oluşturma 'nın sol tarafındaki mevcut değişkenlere bildirimleri ve atamaları karıştırmayacağınızı unutmayın. Derleyici hata CS8184 oluşturuyor, "bir oluşturma, sol taraftaki bildirimleri ve ifadeleri karıştıramaz." üyeler yeni tanımlanan ve mevcut değişkenleri içerenleri içerir.

## <a name="deconstructing-tuple-elements-with-discards"></a>Kayıt düzeni öğeleri atma ile kaldırılıyor

Genellikle bir kayıt düzeni oluştururken yalnızca bazı öğelerin değerleriyle ilgileniyorsunuz. C# 7,0 ' den başlayarak,, değerlerini yok saymayı seçtiğiniz salt yazılır değişkenler olan, C# ' nin *atma* desteğinden faydalanabilirsiniz. Atma, bir atamada bir alt çizgi karakteriyle (" \_ ") belirtilir. İstediğiniz sayıda değeri atabilirsiniz; tümü, tek atma tarafından temsil edilir `_` .

Aşağıdaki örnek, atma ile başlıkların kullanımını gösterir. Bu `QueryCityDataForYears` Yöntem, şehir adı, alanı, bir yıl, bu yıl için şehir popülasyonu, ikinci bir yıl ve bu ikinci yıl için şehir popülasyonu içeren 6 tanımlama grubu döndürür. Örnek, bu iki yıl arasındaki popülasyondaki değişikliği gösterir. Kayıt kümesinden kullanılabilen veriler, şehir alanıyla ilgilentik ve tasarım zamanında şehir adını ve iki tarihi biliyoruz. Sonuç olarak, yalnızca kayıt düzeninde depolanan iki popülasyon değeri ile ilgileniyoruz ve kalan değerlerini atma olarak işleyebilir.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

## <a name="deconstructing-user-defined-types"></a>Kullanıcı tanımlı türleri kaldırma

C#, [`record`](#deconstructing-a-record-type) ve [DictionaryEntry](xref:System.Collections.DictionaryEntry.Deconstruct%2A) türleri dışındaki demet olmayan türler oluşturmak için yerleşik destek sunmaz. Ancak, bir sınıfın yazarı, bir struct veya Interface olarak, bir veya daha fazla yöntem uygulayarak tür örneklerinin çıkarılması için izin verebilirsiniz `Deconstruct` . Yöntemi void döndürür ve kaldırılacak her değer, yöntem imzasında bir [Out](language-reference/keywords/out-parameter-modifier.md) parametresi ile belirtilir. Örneğin, `Deconstruct` bir sınıfın aşağıdaki yöntemi `Person` Birinci, orta ve soyadı döndürür:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Daha sonra `Person` `p` , aşağıdaki gibi bir atamayla adlı sınıfının bir örneğini kaldırabilirsiniz:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Aşağıdaki örnek, `Deconstruct` bir nesnesinin özelliklerinin çeşitli birleşimlerini döndürmek için yöntemini aşırı yükler `Person` . Tek tek aşırı yükleme dönüşü:

- Ad ve soyadı.
- Birinci, orta ve soyadı.
- Ad, soyadı, şehir adı ve durum adı.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

`Deconstruct`Aynı sayıda parametreye sahip birden çok yöntem belirsiz. `Deconstruct`Farklı sayıda parametreye veya "parametre sayısına" sahip yöntemleri tanımlamaya dikkat etmeniz gerekir. `Deconstruct` aynı sayıda parametreye sahip Yöntemler aşırı yükleme çözümlemesi sırasında ayırt edilemez.

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Kullanıcı tanımlı bir türü atma ile kaldırma

[Tanımlama grupları](#deconstructing-tuple-elements-with-discards)ile yaptığınız gibi, bir yöntem tarafından döndürülen seçili öğeleri yoksaymak için atarsa ' u kullanabilirsiniz `Deconstruct` . Her atma "" adlı bir değişken tarafından tanımlanır \_ ve tek bir ayrıştırma işlemi birden çok atma içerebilir.

Aşağıdaki örnek, bir `Person` nesnesini dört dizeye (ilk ve son adlar, şehir ve eyalet) ayırır, ancak son adı ve durumu atar.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Uzantı yöntemiyle kullanıcı tanımlı bir tür kaldırma

Bir sınıf, yapı veya arabirim yazmadıysanız, ilgilendiğiniz değerleri döndürmek için bir veya daha fazla `Deconstruct` [genişletme yöntemi](programming-guide/classes-and-structs/extension-methods.md) uygulayarak o türdeki nesneleri yine de oluşturabilirsiniz.

Aşağıdaki örnek `Deconstruct` , sınıfı için iki genişletme yöntemini tanımlar <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> . İlki, özelliğin özelliklerini gösteren, türü, statik mi, örnek mi olduğunu, salt okunurdur ve dizine eklenip eklenmeyeceğini içeren bir değerler kümesi döndürür. İkincisi, özelliğin erişilebilirliğini gösterir. Get ve set erişimcilerinin erişilebilirliği farklı olabileceğinden, Boole değerleri özelliğin ayrı Get ve set erişimcilerine sahip olup olmadığını ve varsa aynı erişilebilirliği içerip içermediğini gösterir. Yalnızca bir erişimci varsa veya hem Get hem de set erişimcisinin aynı erişilebilirliği varsa `access` değişkeni, özelliğin erişilebilirliğini bir bütün olarak gösterir. Aksi takdirde, Get ve set erişimcilerinin erişilebilirliği `getAccess` ve değişkenleri tarafından gösterilir `setAccess` .

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="deconstructing-a-record-type"></a>Bir türü kaldırma `record`

İki veya daha fazla Konumsal parametre kullanarak bir [kayıt](language-reference/builtin-types/record.md) türü bildirdiğinizde, derleyici, `Deconstruct` `out` bildirimdeki her Konumsal parametre için parametresiyle bir yöntem oluşturur `record` . Daha fazla bilgi için, bkz. [özellik tanımı Için konumsal sözdizimi](language-reference/builtin-types/record.md#positional-syntax-for-property-definition) ve [türetilmiş kayıtlarda Deconstructor davranışı](language-reference/builtin-types/record.md#deconstructor-behavior-in-derived-records).

## <a name="see-also"></a>Ayrıca bkz.

- [Atılanlar](discards.md)
- [Demet türleri](language-reference/builtin-types/value-tuples.md)
