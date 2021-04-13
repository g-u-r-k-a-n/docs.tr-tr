---
title: Simge ve İşleç Başvurusu
description: 'F # programlama dilinde kullanılan semboller ve işleçler hakkında bilgi edinin.'
ms.date: 08/15/2020
fl_keywords:
- '|>_FS'
ms.openlocfilehash: 2fddf538f007a971ee369b9118f02deb8408d3a6
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075556"
---
# <a name="symbol-and-operator-reference"></a>Sembol ve işleç başvurusu

Bu makale, F # dilinde kullanılan bir sembol ve işleç tablosu içerir.

## <a name="table-of-symbols-and-operators"></a>Semboller ve işleçler tablosu

Aşağıdaki tabloda, F # dilinde kullanılan semboller açıklanmakta ve daha fazla bilgi için simgenin ve bağlantıların kullanımları hakkında kısa bir açıklama sağlanmaktadır. Semboller ASCII karakter kümesi sıralamasına göre sıralanır.

|Sembol veya işleç|Bağlantılar|Description|
|------------------|-----|-----------|
|`!`|[Başvuru Hücreleri](../reference-cells.md)<br /><br />[Hesaplama İfadeleri](../computation-expressions.md)|<ul><li>Bir başvuru hücresine başvurur.<br /></li><li>Anahtar sözcüğünden sonra, bir iş akışı tarafından denetlenen şekilde anahtar sözcüğünün davranışının değiştirilmiş bir sürümünü belirtir.<br /></li></ul>|
|`!=`||<ul><li>F # içinde kullanılmıyor. `<>`Eşitsizlik işlemleri için kullanın.<br /></li></ul>|
|`"`|[Değişmez Değerler](../literals.md)<br /><br />[Dizeler](../strings.md)|<ul><li>Bir metin dizesini ayırır.<br /></li></ul>|
|`"""`|[Dizeler](../strings.md)|Tam metin dizesini ayırır. `@"..."`Dizedeki tek bir tırnak işareti kullanarak bir tırnak işareti karakteri belirtebilmeniz için ' den farklıdır.|
|`#`|[Derleyici Yönergeleri](../compiler-directives.md)<br /><br />[Esnek Türler](../flexible-types.md)|<ul><li>, Gibi bir Önişlemci veya derleyici yönergesine ön ekler `#light` .<br /></li><li>Bir türle birlikte kullanıldığında, bir türe veya türetilmiş türlerinden birine başvuran *esnek bir türü* gösterir.<br /></li></ul>|
|`$`||<ul><li>Derleyici tarafından üretilen belirli değişken ve işlev adları için dahili olarak kullanılır.<br /></li></ul>|
|`%`|[Aritmetik Işleçler](arithmetic-operators.md)<br /><br />[Kod Tırnak İşaretleri](../code-quotations.md)|<ul><li>Tam sayı kalanını hesaplar.<br /></li><li>Türü belirtilmiş kod tekliflerine yönelik ifade için kullanılır.<br /></li></ul>|
|`%%`|[Kod Tırnak İşaretleri](../code-quotations.md)|<ul><li>Türsüz kod tekliflerine yönelik ifadeleri ifade etmek için kullanılır.<br /></li></ul>|
|`%?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ kenar null yapılabilir bir tür olduğunda, tam sayı kalanını hesaplar.<br /></li></ul>|
|`&`|[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>Diğer dillerle birlikte çalışırken kullanılmak üzere kesilebilir değerin adresini hesaplar.<br /></li><li>VE desenlerinde kullanılır.<br /></li></ul>|
|`&&`|[Boole İşleçleri](boolean-operators.md)|<ul><li>Boole ve işlemi hesaplar.<br /></li></ul>|
|`&&&`|[Bit düzeyinde Işleçler](bitwise-operators.md)|<ul><li>Bit düzeyinde ve işlemi hesaplar.<br /></li></ul>|
|`'`|[Değişmez Değerler](../literals.md)<br /><br />[Otomatik Genelleştirme](../generics/automatic-generalization.md)|<ul><li>Tek karakterlik değişmez değer ayırır.<br /></li><li>Genel bir tür parametresini gösterir.<br /></li></ul>|
|<code>&#96;&#96;...&#96;&#96;</code>||<ul><li>Alternatif olarak, bir dil anahtar sözcüğü gibi yasal tanımlayıcı olmayan bir tanımlayıcıyı ayırır.<br /></li></ul>|
|`( )`|[Birim Türü](../unit-type.md)|<ul><li>Birim türünün tek bir değerini temsil eder.<br /></li></ul>|
|`(...)`|[Demetler](../tuples.md)<br /><br />[İşleç aşırı yüklemesi](../operator-overloading.md)|<ul><li>İfadelerin değerlendirileceği sırayı gösterir.<br /></li><li>Tanımlama grubu ayırır.<br /></li><li>İşleç tanımlarında kullanılır.<br /></li></ul>|
|`(*...*)`||<ul><li>Birden çok satıra yayılabilen bir yorumu ayırır.<br /></li></ul>|
|<code>(&#124;...&#124;)</code>|[Etkin Desenler](../active-patterns.md)|<ul><li>Etkin bir düzene ayırır. Ayrıca *muz klipleri* olarak da bilinir.<br /></li></ul>|
|`*`|[Aritmetik Işleçler](arithmetic-operators.md)<br /><br />[Demetler](../tuples.md)<br /><br />[Ölçü birimleri](../units-of-measure.md)|<ul><li>İkili işleç olarak kullanıldığında, sol ve sağ kenarları çarpar.<br /></li><li>Türlerde, bir tanımlama grubu içindeki eşlemeyi gösterir.<br /></li><li>Ölçü birimi türlerinde kullanılır.<br /></li></ul>|
|`*?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ kenar null yapılabilir bir tür olduğunda sol ve sağ kenarları çarpar.<br /></li></ul>|
|`**`|[Aritmetik Işleçler](arithmetic-operators.md)|<ul><li>Üs işlemi ( `x ** y` `x` kuvvetinin anlamı `y` ) hesaplar.<br /></li></ul>|
|`+`|[Aritmetik Işleçler](arithmetic-operators.md)|<ul><li>İkili işleç olarak kullanıldığında, sol ve sağ kenarları ekler.<br /></li><li>Birli işleç olarak kullanıldığında, pozitif miktarı gösterir. (Resmi olarak, işareti değişmeden aynı değeri üretir.)<br /></li></ul>|
|`+?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ kenar null yapılabilir bir tür olduğunda sol ve sağ kenarları ekler.<br /></li></ul>|
|`,`|[Demetler](../tuples.md)|<ul><li>Bir tanımlama grubunun öğelerini veya tür parametrelerini ayırır.<br /></li></ul>|
|`-`|[Aritmetik Işleçler](arithmetic-operators.md)|<ul><li>İkili işleç olarak kullanıldığında, sol taraftaki sağ tarafı çıkartır.<br /></li><li>Birli operatör olarak kullanıldığında, bir Olumsuzlaştırma işlemi gerçekleştirir.<br /></li></ul>|
|`-?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ taraftaki null yapılabilir bir tür olduğunda, sağ tarafı sol taraftan çıkartır.<br /></li></ul>|
|`->`|[İşlevler](../functions/index.md)<br /><br />[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>İşlev türlerinde, bağımsız değişkenleri ve dönüş değerlerini ayırır.<br /></li><li>Bir ifade verir (dizi ifadelerinde); `yield` anahtar kelimesiyle eşdeğerdir.<br /></li><li>Eşleşme ifadelerinde kullanılır<br /></li></ul>|
|`.`|[Üyeler](../members/index.md)<br /><br />[İlkel Türler](../basic-types.md)|<ul><li>Bir üyeye erişir ve adları tam bir ada ayırır.<br /></li><li>Kayan nokta numaralarında ondalık bir nokta belirtir.<br /></li></ul>|
|`..`|[Döngüler: `for...in` ifade](../loops-for-in-expression.md)|<ul><li>Bir aralığı belirtir.<br /></li></ul>|
|`.. ..`|[Döngüler: `for...in` ifade](../loops-for-in-expression.md)|<ul><li>Bir artım ile birlikte bir aralığı belirtir.<br /></li></ul>|
|`.[...]`|[Diziler](../arrays.md)|<ul><li>Bir dizi öğesine erişir.<br /></li></ul>|
|`/`|[Aritmetik Işleçler](arithmetic-operators.md)<br /><br />[Ölçü birimleri](../units-of-measure.md)|<ul><li>Sol tarafı (pay) sağ tarafa (payda) böler.<br /></li><li>Ölçü birimi türlerinde kullanılır.<br /></li></ul>|
|`/?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ kenar null yapılabilir bir tür olduğunda, sol tarafı sağ tarafla böler.<br /></li></ul>|
|`//`||<ul><li>Tek satırlık açıklamanın başlangıcını gösterir.<br /></li></ul>|
|`///`|[XML Belgeleri](../xml-documentation.md)|<ul><li>Bir XML açıklamasını gösterir.<br /></li></ul>|
|`:`|[İşlevler](../functions/index.md)|<ul><li>Bir tür ek açıklamasında bir parametre veya üye adını türünden ayırır.<br /></li></ul>|
|`::`|[Listeler](../lists.md)<br /><br />[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>Bir liste oluşturur. Sol taraftaki öğe, sağ taraftaki listenin başına eklenir.<br /></li><li>Bir listenin parçalarını ayırmak için kalıp eşleştirmesinde kullanılır.<br /></li></ul>|
|`:=`|[Başvuru Hücreleri](../reference-cells.md)|<ul><li>Başvuru hücresine bir değer atar.<br /></li></ul>|
|`:>`|[Atama ve Dönüştürmeler](../casting-and-conversions.md)|<ul><li>Bir türü hiyerarşide daha üst olan türe dönüştürür.<br /></li></ul>|
|`:?`|[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>`true`Değerin belirtilen türle eşleşip eşleşmediğini döndürür (bir alt tür ise dahil); Aksi takdirde, döndürür `false` (tür testi işleci).<br /></li></ul>|
|`:?>`|[Atama ve Dönüştürmeler](../casting-and-conversions.md)|<ul><li>Bir türü hiyerarşide daha düşük olan bir türe dönüştürür.<br /></li></ul>|
|`;`|[Ayrıntılı Sözdizimi](../verbose-syntax.md)<br /><br />[Listeler](../lists.md)<br /><br />[Kayıtlar](../records.md)|<ul><li>İfadeleri ayırır (çoğunlukla ayrıntılı sözdiziminde kullanılır).<br /></li><li>Bir listenin öğelerini ayırır.<br /></li><li>Bir kaydın alanlarını ayırır.<br /></li></ul>|
|`<`|[Aritmetik Işleçler](arithmetic-operators.md)|<ul><li>Küçüktür işlemini hesaplar.<br /></li></ul>|
|`<?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|Sağ kenar null yapılabilir bir tür olduğunda, işlemi küçüktür olarak hesaplar.|
|`<<`|[İşlevler](../functions/index.md)|<ul><li>İki işlevi ters sırada oluşturur; ikinci bir ilki yürütülür (geriye doğru bileşim işleci).<br /></li></ul>|
|`<<<`|[Bit düzeyinde Işleçler](bitwise-operators.md)|<ul><li>Sol taraftaki miktardaki miktarı, sağ tarafta belirtilen bit sayısıyla sola kaydırır.<br /></li></ul>|
|`<-`|[Değerler](../values/index.md)|<ul><li>Bir değişkene bir değer atar.<br /></li></ul>|
|`<...>`|[Otomatik Genelleştirme](../generics/automatic-generalization.md)|<ul><li>Sınırlandırlar tür parametreleri.<br /></li></ul>|
|`<>`|[Aritmetik Işleçler](arithmetic-operators.md)|<ul><li>`true`Sol kenar sağ tarafa eşit değilse döndürür; Aksi takdirde false döndürür.<br /></li></ul>|
|`<>?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ kenar null yapılabilir bir tür olduğunda "eşit değildir" işlemini hesaplar.<br /></li></ul>|
|`<=`|[Aritmetik Işleçler](arithmetic-operators.md)|<ul><li>`true`Sol tarafta sağ taraftan küçük veya ona eşit olursa döndürür; Aksi takdirde, döndürür `false` .<br /></li></ul>|
|`<=?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ kenar null yapılabilir bir tür olduğunda "küçüktür veya eşittir" işlemini hesaplar.<br /></li></ul>|
|<code>&#124;></code>|[İşlevler](../functions/index.md)|<ul><li>Sol tarafın sonucunu sağ taraftaki işleve geçirir (ileri kanal işleci).<br /></li></ul>|
|<code>&#124;&#124;></code>|[&#40; &#124;&#124;&#62; &#41;&#60; 1, 'T 2, ' U&#62; Işlevi](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#(%20%7C%7C%3E%20))|<ul><li>Sol taraftaki iki bağımsız değişkenin kayıt kümesini sağ taraftaki işleve geçirir.<br /></li></ul>|
|<code>&#124;&#124;&#124;></code>|[&#40; &#124;&#124;&#124;&#62; &#41;&#60; 1, 'T 2, 'T 3, ' U&#62; Işlevi](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#(%20%7C%7C%7C%3E%20))|<ul><li>Sol taraftaki üç bağımsız değişkenin kayıt kümesini sağ taraftaki işleve geçirir.<br /></li></ul>|
|<code>&lt;&#124;</code>|[İşlevler](../functions/index.md)|<ul><li>Sağ taraftaki ifadenin sonucunu sol taraftaki işleve geçirir (geriye doğru kanal işleci).<br /></li></ul>|
|<code>&lt;&#124;&#124;</code>|[&#40; &#60;&#124;&#124; &#41;&#60; 1, 'T 2, ' U&#62; Işlevi](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#(%20%3C%7C%7C%20))|<ul><li>Sağ taraftaki iki bağımsız değişkenin kayıt kümesini sol taraftaki işleve geçirir.<br /></li></ul>|
|<code>&lt;&#124;&#124;&#124;</code>|[&#40; &#60;&#124;&#124;&#124; &#41;&#60; 1, 'T 2, 'T 3, ' U&#62; Işlevi](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-operators.html#(%20%3C%7C%7C%7C%20))|<ul><li>Sağ taraftaki üç bağımsız değişkenin kayıt kümesini sol taraftaki işleve geçirir.<br /></li></ul>|
|`<@...@>`|[Kod Tırnak İşaretleri](../code-quotations.md)|<ul><li>Türü belirlenmiş bir kod teklifini ayırır.<br /></li></ul>|
|`<@@...@@>`|[Kod Tırnak İşaretleri](../code-quotations.md)|<ul><li>Türsüz bir kod teklifini ayırır.<br /></li></ul>|
|`=`|[Aritmetik Işleçler](arithmetic-operators.md)|<ul><li>`true`Sol tarafta sağ tarafa eşit olursa döndürür; Aksi takdirde, döndürür `false` .<br /></li></ul>|
|`=?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ kenar null yapılabilir bir tür olduğunda "eşittir" işlemini hesaplar.<br /></li></ul>|
|`==`||<ul><li>F # içinde kullanılmıyor. `=`Eşitlik işlemleri için kullanın.<br /></li></ul>|
|`>`|[Aritmetik Işleçler](arithmetic-operators.md)|<ul><li>`true`Sol kenar sağ taraftan büyükse döndürür; Aksi takdirde, döndürür `false` .<br /></li></ul>|
|`>?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ kenar null yapılabilir bir tür olduğunda "büyüktür" işlemini hesaplar.<br /></li></ul>|
|`>>`|[İşlevler](../functions/index.md)|<ul><li>İki işlevi (ileri birleşim işleci) bileşik olarak oluşturur.<br /></li></ul>|
|`>>>`|[Bit düzeyinde Işleçler](bitwise-operators.md)|<ul><li>Sol taraftaki miktardaki miktarı sağ tarafta belirtilen yer sayısına göre sağa kaydırır.<br /></li></ul>|
|`>=`|[Aritmetik Işleçler](arithmetic-operators.md)|<ul><li>`true`Sol tarafta sağ taraftan büyük veya ona eşit olursa döndürür; Aksi takdirde, döndürür `false` .<br /></li></ul>|
|`>=?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Sağ kenar null yapılabilir bir tür olduğunda "büyüktür veya eşittir" işlemini hesaplar.<br /></li></ul>|
|`?`|[Parametreler ve Bağımsız Değişkenler](../parameters-and-arguments.md)|<ul><li>İsteğe bağlı bir bağımsız değişken belirtir.<br /></li><li>Dinamik yöntem ve özellik çağrıları için işleç olarak kullanılır. Kendi uygulamanızı sağlamanız gerekir.<br /></li></ul>|
|`? ... <- ...`||<ul><li>Dinamik özellikleri ayarlamak için işleç olarak kullanılır. Kendi uygulamanızı sağlamanız gerekir.<br /></li></ul>|
|`?>=`, `?>`, `?<=`, `?<`, `?=`, `?<>`, `?+`, `?-`, `?*`, `?/`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>İlgili işleçlere sahip olmadan eşdeğer mi? null yapılabilir bir tür solda olan önek.<br /></li></ul>|
|`>=?`, `>?`, `<=?`, `<?`, `=?`, `<>?`, `+?`, `-?`, `*?`, `/?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>İlgili işleçlere sahip olmadan eşdeğer mi? sonek olarak null yapılabilir bir tür.<br /></li></ul>|
|`?>=?`, `?>?`, `?<=?`, `?<?`, `?=?`, `?<>?`, `?+?`, `?-?`, `?*?`, `?/?`|[Boş Değer Atanabilir İşleçler](nullable-operators.md)|<ul><li>Her iki taraf da null yapılabilir türler olduğunda, çevresindeki soru işaretleri olmadan karşılık gelen işleçlere eşdeğerdir.<br /></li></ul>|
|`@`|[Listeler](../lists.md)<br /><br />[Dizeler](../strings.md)|<ul><li>İki listeyi birleştirir.<br /></li><li>Bir dize sabit değerinden önce yerleştirildiğinde, kaçış karakterleri yorumu olmadan dizenin tam olarak yorumlanıp yorumlanmadığını gösterir.<br /></li></ul>|
|`[...]`|[Listeler](../lists.md)|<ul><li>Bir listenin öğelerini ayırır.<br /></li></ul>|
|<code>[&#124;...&#124;]</code>|[Diziler](../arrays.md)|<ul><li>Bir dizinin öğelerini ayırır.<br /></li></ul>|
|`[<...>]`|[Öznitelikler](../attributes.md)|<ul><li>Bir özniteliği ayırır.<br /></li></ul>|
|`\`|[Dizeler](../strings.md)|<ul><li>Sonraki karakteri çıkar; karakter ve dize değişmez değerlerinde kullanılır.<br /></li></ul>|
|`^`|[Statik Olarak Çözümlenmiş Tür Parametreleri](../generics/statically-resolved-type-parameters.md)<br /><br />[Dizeler](../strings.md)|<ul><li>Çalışma zamanında değil, derleme zamanında çözülmesi gereken tür parametrelerini belirtir.<br /></li><li>Dizeleri art arda ekler.<br /></li></ul>|
|`^^^`|[Bit düzeyinde Işleçler](bitwise-operators.md)|<ul><li>Bit düzeyinde dışlamalı veya işlemi hesaplar.<br /></li></ul>|
|`_`|[Eşleşme İfadeleri](../match-expressions.md)<br /><br />[Genel Türler](../generics/index.md)|<ul><li>Bir joker karakter deseninin olduğunu gösterir.<br /></li><li>Anonim bir genel parametre belirtir.<br /></li></ul>|
|<code>&#96;</code>|[Otomatik Genelleştirme](../generics/automatic-generalization.md)|<ul><li>Genel bir tür parametresini göstermek için dahili olarak kullanılır.<br /></li></ul>|
|`{...}`|[Diziler](../sequences.md)<br /><br />[Kayıtlar](../records.md)|<ul><li>Sıralama ifadelerini ve hesaplama ifadelerini ayırır.<br /></li><li>Kayıt tanımlarında kullanılır.<br /></li></ul>|
|<code>&#124;</code>|[Eşleşme İfadeleri](../match-expressions.md)|<ul><li>Bireysel eşleşme durumlarını, tek ayırt edici birleşim durumlarını ve numaralandırma değerlerini ayırır.<br /></li></ul>|
|<code>&#124;&#124;</code>|[Boole İşleçleri](boolean-operators.md)|<ul><li>Boole veya işlemi hesaplar.<br /></li></ul>|
|<code>&#124;&#124;&#124;</code>|[Bit düzeyinde Işleçler](bitwise-operators.md)|<ul><li>Bit düzeyinde OR işlemini hesaplar.<br /></li></ul>|
|`~~`|[İşleç aşırı yüklemesi](../operator-overloading.md)|<ul><li>Birli olumsuzlama işleci için bir aşırı yükleme bildirmek için kullanılır.<br /></li></ul>|
|`~~~`|[Bit düzeyinde Işleçler](bitwise-operators.md)|<ul><li>Bit düzeyinde işlem işlemini hesaplar.<br /></li></ul>|
|`~-`|[İşleç aşırı yüklemesi](../operator-overloading.md)|<ul><li>Birli eksi işleci için aşırı yükleme bildirmek için kullanılır.<br /></li></ul>|
|`~+`|[İşleç aşırı yüklemesi](../operator-overloading.md)|<ul><li>Birli artı işleci için aşırı yükleme bildirmek için kullanılır.<br /></li></ul>|

## <a name="operator-precedence"></a>İşleç önceliği

Aşağıdaki tabloda, F # dilinde işleçlerin ve diğer ifade anahtar sözcüklerinin öncelik sırası, en düşük önceliğe göre öncelik sırasına göre gösterilmektedir. Ayrıca, varsa, ilişkilendirilebilirliği de listelenmiştir.

|Operatör|İlişkilendirilebilirlik|
|--------|-------------|
|`as`|Sağ|
|`when`|Sağ|
|<code>&#124;</code> kapatıldığı|Sol|
|`;`|Sağ|
|`let`|İlişkilendirilebilir olmayan|
|`function`, `fun`, `match`, `try`|İlişkilendirilebilir olmayan|
|`if`|İlişkilendirilebilir olmayan|
|`not`|Sağ|
|`->`|Sağ|
|`:=`|Sağ|
|`,`|İlişkilendirilebilir olmayan|
|`or`, <code>&#124;&#124;</code>|Sol|
|`&`, `&&`|Sol|
|`:>`, `:?>`|Sağ|
|`<`*op*, `>` *op*, `=` , <code>&#124;</code> *op*, `&` *op*, `&` ,`$`<br /><br />(,,,, ve dahil `<<<` `>>>` <code>&#124;&#124;&#124;</code> `&&&` )|Sol|
|`^`*üs*<br /><br />(dahil `^^^` )|Sağ|
|`::`|Sağ|
|`:?`|İlişkilendirilebilir değil|
|`-`*op*, `+` *op*|Bu sembollerin ındüzeltilme kullanımları için geçerlidir|
|`*`*op*, `/` *op*, `%` *op*|Sol|
|`**`*üs*|Sağ|
|`f x` (işlev uygulaması)<br /><br />( `lazy x` , dahil `assert x` )|Sol|
|<code>&#124;</code> (model eşleştirme)|Sağ|
|önek işleçleri ( `+` *op*, `-` *op*, `%` , `%%` , `&` , `&&` , `!` *op*, `~` *op*)|Sol|
|`.`|Sol|
|`f(x)`|Sol|
|`f<`*türü*`>`|Sol|

F # özel operatör aşırı yüklemesini destekler. Bu, kendi işleçlerinizi tanımlayabilmeniz anlamına gelir. Önceki tabloda, *op* , yerleşik veya Kullanıcı tanımlı işleç karakterlerinin geçerli (muhtemelen boş) sırası olabilir. Bu nedenle, istenen öncelik düzeyini elde etmek üzere özel bir operatör için kullanılacak karakter dizisini belirlemek için bu tabloyu kullanabilirsiniz. `.`Derleyici önceliği belirlediğinde öndeki karakterler yok sayılır.

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](../index.md)
- [İşleç aşırı yüklemesi](../operator-overloading.md)
