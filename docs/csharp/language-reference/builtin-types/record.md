---
title: Kayıtlar-C# başvurusu
description: "C 'de kayıt türü hakkında bilgi edinin #"
ms.date: 02/25/2021
f1_keywords:
- record_CSharpKeyword
helpviewer_keywords:
- record keyword [C#]
- record type [C#]
ms.openlocfilehash: 067046a66c6eb1f314c123de8bde2d023f1f374a
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255122"
---
# <a name="records-c-reference"></a>Kayıtlar (C# Başvurusu)

C# 9 ' dan başlayarak, `record` verileri kapsüllemek için yerleşik işlevsellik sağlayan bir [başvuru türü](reference-types.md) tanımlamak için anahtar sözcüğünü kullanırsınız. Konumsal parametreleri veya standart özellik sözdizimini kullanarak, değişmez özelliklerle kayıt türleri oluşturabilirsiniz:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="PositionalRecord":::
:::code language="csharp" source="snippets/shared/RecordType.cs" id="ImmutableRecord":::

Ayrıca, değişebilir Özellikler ve alanlarla kayıt türleri de oluşturabilirsiniz:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="MutableRecord":::

Kayıtlar değişebilir olsa da, Bunlar öncelikle sabit veri modellerini desteklemeye yöneliktir. Kayıt türü aşağıdaki özellikleri sunar:

* [Sabit özelliklerle başvuru türü oluşturmak için kısa sözdizimi](#positional-syntax-for-property-definition)
* Veri merkezli bir başvuru türü için yerleşik davranış yararlı olur:
  * [Değer eşitlik](#value-equality)
  * [Geri dönüşlü mutasyon için kısa sözdizimi](#nondestructive-mutation)
  * [Görüntüleme için yerleşik biçimlendirme](#built-in-formatting-for-display)
* [Devralma hiyerarşileri için destek](#inheritance)

Ayrıca, değer eşitlik ve çok az davranış sağlayan veri merkezli türler tasarlamak için [yapı türlerini](struct.md) de kullanabilirsiniz. Ancak görece büyük veri modelleri için yapı türlerinin bazı dezavantajları vardır:

* Devralma desteği yoktur.
* Değer eşitliğini belirlemede daha az verimlidir. Değer türlerinde, <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> yöntemi tüm alanları bulmak için yansıma kullanır. Kayıtlar için derleyici `Equals` yöntemini oluşturur. Uygulamada, kayıtlardaki değer eşitlik uygulaması yaşamları daha hızlıdır.
* Her örnek tüm verilerin tamamen bir kopyasına sahip olduğundan, bazı senaryolarda daha fazla bellek kullanırlar. Kayıt türleri [başvuru türlerdir](reference-types.md), bu nedenle bir kayıt örneği yalnızca verilerin bir başvurusunu içerir.

## <a name="positional-syntax-for-property-definition"></a>Özellik tanımı için Konumsal sözdizimi

Bir kaydın özelliklerini bildirmek ve bir örnek oluştururken özellik değerlerini başlatmak için Konumsal parametreleri kullanabilirsiniz:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="InstantiatePositional":::

Özellik tanımı için Konumsal sözdizimini kullandığınızda, derleyici şunları oluşturur:

* Kayıt bildiriminde belirtilen her Konumsal parametre için genel bir init-tek otomatik uygulanan özellik. [Yalnızca bir init](../keywords/init.md) özelliği, oluşturucuda veya bir özellik başlatıcısı kullanılarak ayarlanabilir.
* Parametreleri, kayıt bildiriminde konumsal parametrelerle eşleşen bir birincil Oluşturucu.
* `Deconstruct` `out` Kayıt bildiriminde belirtilen her Konumsal parametre için parametreye sahip bir yöntem. Bu yöntem yalnızca iki veya daha fazla Konumsal parametre varsa sağlanır. Yöntemi konumsal sözdizimi kullanılarak tanımlanan özellikleri kaldırır; Standart özellik sözdizimi kullanılarak tanımlanan özellikleri yoksayar.

Oluşturulan otomatik uygulanan özellik tanımı istediğiniz gibi değilse, aynı ada sahip kendi özelliğini tanımlayabilirsiniz. Bunu yaparsanız, oluşturulan Oluşturucu ve Deconstructor Özellik tanımınızı kullanacaktır. Örneğin, aşağıdaki örnek `FirstName` yerine konumsal özelliği yapar `internal` `public` .

:::code language="csharp" source="snippets/shared/RecordType.cs" id="PositionalWithManualProperty":::

Kayıt türü herhangi bir Konumsal özellik bildirmek zorunda değildir. Herhangi bir konum özelliği olmadan bir kayıt bildirebilir ve aşağıdaki örnekte olduğu gibi ek alanlar ve özellikler bildirebilirsiniz:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="MixedSyntax":::

Standart özellik söz dizimini kullanarak Özellikler tanımlayabilir ancak erişim değiştiricisini atlarsanız, Özellikler örtülü olarak bulunur `public` .
<!-- Todo -- Explain issues surrounding use of attributes on positional properties. -->

## <a name="immutability"></a>Değiştirilemezlik

Kayıt türü sabit değildir. Özellikleri, `set` erişimciler ve olmayan alanlarla bildirebilirsiniz `readonly` . Ancak kayıtlar değişebilir, ancak değişmez veri modelleri oluşturmayı kolaylaştırır.

Kullanım açısından kullanılabilirlik, iş parçacığı açısından güvenli olması için veri merkezli bir türün olması gerektiğinde veya karma bir tabloda aynı kalan bir karma koda bağlı olduğunuzda yararlı olabilir. Ancak tüm veri senaryoları için uygun olmayan bir şekilde kullanılabilirlik yoktur. Örneğin, [Entity Framework Core](/ef/core/), sabit varlık türleriyle güncellemeyi desteklemez.

Konumsal parametrelerden oluşturulup veya erişimciler belirtilerek basit bir şekilde kullanılabilirlik sağlamak için yalnızca Init özellikleri `init` .  Başlatma işleminden sonra değer türü özelliklerinin değerini veya başvuru türü özelliklerinin başvurusunu değiştiremezsiniz. Ancak, başvuru türü bir özelliğin başvurduğu veriler değiştirilebilir. Aşağıdaki örnek, bir başvuru türü sabit özelliğinin (Bu durumda bir dizi)) içeriğinin değişebilir olduğunu gösterir:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="ShallowImmutability":::

Kayıt türlerine özgü özellikler derleyici birleştirilmemiş yöntemler tarafından uygulanır ve bu yöntemlerin hiçbiri, nesne durumunu değiştirerek değişiklik imkanlarını önler.

## <a name="value-equality"></a>Değer eşitlik

Değer eşitliği, türlerin eşleşmesi ve tüm özellik ve alan değerleri eşleşiyorsa bir kayıt türünün iki değişkeninin eşit olduğu anlamına gelir. Diğer başvuru türleri için eşitlik, kimlik anlamına gelir. Diğer bir deyişle, bir başvuru türünün iki değişkeni aynı nesneye başvurduklarında eşittir.

Bazı veri modelleri için başvuru eşitliği gereklidir. Örneğin, [Entity Framework Core](/ef/core/) kavramsal bir varlık olan varlık türünün yalnızca bir örneğini kullandığından emin olmak için başvuru eşitliğine bağlıdır. Bu nedenle, kayıt türleri Entity Framework Core varlık türleri olarak kullanım için uygun değildir.

Aşağıdaki örnek, kayıt türlerinin değer eşitliğini gösterir:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="Equality":::

Değer eşitliği uygulamak için, derleyici aşağıdaki yöntemleri birleştirmelidir:

* Bir geçersiz kılma <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> .

  Bu yöntem, <xref:System.Object.Equals(System.Object,System.Object)?displayProperty=nameWithType> her iki parametre de null olmadığında statik metodun temeli olarak kullanılır.

* `Equals`Parametresi kayıt türü olan bir sanal yöntem. Bu yöntem uygular <xref:System.IEquatable%601> .

* Bir geçersiz kılma <xref:System.Object.GetHashCode?displayProperty=nameWithType> .

* Operatörlerin ve geçersiz kılmaları `==` `!=` .

Türler ' de `class` , eşitlik yöntemlerini ve işleçleri değer eşitlik elde etmek için el ile geçersiz kılabilirsiniz, ancak bu kodun geliştirilmesi ve test edilmesi zaman alabilir ve hataya açıktır. Bu işlevin yerleşik olması, özellikler veya alanlar eklendiğinde veya değiştirildiğinde özel geçersiz kılma kodunu güncelleştirmeye neden olan hataları önler.

Bu sentezlenmiş yöntemlerin herhangi birini değiştirmek için kendi uygulamalarınızı yazabilirsiniz. Bir kayıt türünün herhangi bir sentezlenmiş yöntemin imzasıyla eşleşen bir yöntemi varsa, derleyici bu yöntemi birleştirmez.

`Equals`Bir kayıt türünde kendi uygulamanızı sağlarsanız, bir de uygulamasını sağlayın `GetHashCode` .

## <a name="nondestructive-mutation"></a>Geri dönüşlü mutasyon

Bir kayıt örneğinin sabit özelliklerini mukumanız gerekirse, geri dönüşlü bir zaman `with` elde etmek için bir ifade kullanabilirsiniz . Bir `with` ifade, belirtilen özellikler ve alanlarla değiştirilen mevcut bir kayıt örneğinin kopyası olan yeni bir kayıt örneği oluşturur. Aşağıdaki örnekte gösterildiği gibi, değiştirilecek değerleri belirtmek için [nesne Başlatıcısı](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) sözdizimini kullanın:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="WithExpressions":::

`with`İfade, konumsal özellikleri veya standart özellik söz dizimi kullanılarak oluşturulan özellikleri ayarlayabilir. Konumsal olmayan özelliklerin `init` `set` bir ifadede değişmesi için bir veya erişimcisi olmalıdır `with` .

Bir `with` ifadenin sonucu *basit bir kopyadır*. Bu, başvuru özelliği için yalnızca bir örneğe olan başvurunun kopyalandığı anlamına gelir. Hem özgün kayıt hem de kopya aynı örneğe bir başvuru ile sona erdir.

Bu özelliği uygulamak için derleyici bir Clone yöntemi ve bir kopya Oluşturucu birleştirmelidir. Oluşturucu, kopyalanacak kaydın bir örneğini alır ve Clone metodunu çağırır. Bir `with` ifade kullandığınızda, derleyici kopya oluşturucuyu çağıran kodu oluşturur ve sonra ifadede belirtilen özellikleri ayarlar `with` .

Farklı kopyalama davranışına ihtiyacınız varsa, kendi kopya oluşturucunuzu yazabilirsiniz. Bunu yaparsanız, derleyici bir tane birleştirmez. `private`Kayıt varsa oluşturucuyu yapın `sealed` , aksi takdirde yapın `protected` .

Kopyalama yöntemini geçersiz kılamazsınız ve adında bir üye oluşturamazsınız `Clone` . Kopya yönteminin gerçek adı derleyici tarafından oluşturulmuştur.

## <a name="built-in-formatting-for-display"></a>Görüntüleme için yerleşik biçimlendirme

Kayıt türlerinde <xref:System.Object.ToString%2A> , ortak özelliklerin ve alanların adlarını ve değerlerini görüntüleyen bir derleyici tarafından oluşturulan yöntem vardır. `ToString`Yöntemi aşağıdaki biçimde bir dize döndürür:

> \<record type name> { \<property name> = \<value>, \<property name> = \<value>, ...}

Başvuru türleri için, özelliğin başvurduğu nesnenin tür adı, özellik değeri yerine görüntülenir. Aşağıdaki örnekte, dizi bir başvuru türüdür, bu nedenle `System.String[]` gerçek dizi öğesi değerleri yerine görüntülenir:

```
Person { FirstName = Nancy, LastName = Davolio, ChildNames = System.String[] }
```

Bu özelliği uygulamak için, derleyici sanal bir `PrintMembers` yöntemi ve bir <xref:System.Object.ToString%2A> geçersiz kılmayı birleştirir.
`ToString`Geçersiz kılma, <xref:System.Text.StringBuilder> tür adı ve ardından bir açılış ayracı ile bir nesne oluşturur. `PrintMembers`Özellik adları ve değerler eklemek için öğesini çağırır, sonra da kapanış ayracını ekler. Aşağıdaki örnek, sentezleştirilmiş geçersiz kılmanın neleri içerdiğini gösteren kodu gösterir:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="ToStringOverrideDefault":::

Kendi uygulamanızı `PrintMembers` veya `ToString` geçersiz kılma işlemini sağlayabilirsiniz. Örnekler, bu makalenin ilerleyen kısımlarında [ `PrintMembers` türetilen kayıtlardaki biçimlendirme](#printmembers-formatting-in-derived-records) bölümünde verilmiştir.

## <a name="inheritance"></a>Devralma

Bir kayıt, başka bir kayıttan devralınabilir. Ancak, bir kayıt bir sınıftan devralınabilir ve bir sınıf bir kayıttan devralınabilir.

### <a name="positional-parameters-in-derived-record-types"></a>Türetilmiş kayıt türlerinde Konumsal parametreler

Türetilmiş kayıt, temel kayıt birincil oluşturucusunda bulunan tüm parametrelerin konumsal parametrelerini bildirir. Temel kayıt bu özellikleri bildirir ve başlatır. Türetilmiş kayıt onları gizlemez, ancak temel kaydında bildirilmeyen parametreler için Özellikler oluşturur ve başlatır.

Aşağıdaki örnek, konumsal Özellik söz dizimi ile devralmayı göstermektedir:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="PositionalInheritance":::

### <a name="equality-in-inheritance-hierarchies"></a>Devralma hiyerarşilerinde eşitlik

İki kayıt değişkeninin eşit olması için, çalışma zamanı türünün eşit olması gerekir. Kapsayan değişkenlerin türleri farklı olabilir. Bu, aşağıdaki kod örneğinde gösterilmektedir:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="InheritanceEquality":::

Örnekte, tüm örnekler aynı özelliklere ve aynı özellik değerlerine sahiptir. Ancak `student == teacher` , `False` her ikisi de `Person` -tür değişkenleri olsa da `student == student2` , `True` biri `Person` değişken ve diğeri bir `Student` değişken olsa da döndürür.

Bu davranışı uygulamak için derleyici, `EqualityContract` kaydın türüyle eşleşen bir nesne döndüren bir özelliği sentezler <xref:System.Type> . Bu, eşitlik için Denetim sırasında nesnelerin çalışma zamanı türünü karşılaştırmalarını sağlar. Bir kaydın temel türü ise, `object` Bu özellik olur `virtual` . Temel tür başka bir kayıt türü ise, bu özellik bir geçersiz kılma olur. Kayıt türü ise, `sealed` Bu özellik olur `sealed` .

Türetilmiş bir türün iki örneğini karşılaştırırken, birleştirilmiş eşitlik yöntemleri temel ve türetilmiş türlerin tüm özelliklerini bir eşitlik için denetler. Sentezlenmiş `GetHashCode` Yöntem, `GetHashCode` temel türde ve türetilmiş kayıt türünde belirtilen tüm özelliklerden ve alanlardan yöntemini kullanır.

### <a name="with-expressions-in-derived-records"></a>`with` türetilmiş kayıtlardaki ifadeler

Sentezlenmiş kopya yöntemi bir [covaryant dönüş türü](~/_csharplang/proposals/csharp-9.0/covariant-returns.md)kullandığından, `with` ifadenin sonucu ifadenin işleneni ile aynı çalışma zamanı türüne sahip. Çalışma zamanı türünün tüm özellikleri kopyalanırlar, ancak aşağıdaki örnekte gösterildiği gibi yalnızca derleme zamanı türünün özelliklerini ayarlayabilirsiniz:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="WithExpressionInheritance":::

### <a name="printmembers-formatting-in-derived-records"></a>`PrintMembers` türetilmiş kayıtlarda biçimlendirme

`PrintMembers`Türetilmiş bir kayıt türünün sentezlenmiş yöntemi temel uygulamayı çağırır. Sonuç `ToString` olarak, aşağıdaki örnekte gösterildiği gibi, hem türetilmiş hem de temel türlerin tüm ortak özellikleri ve alanları çıkışa dahil edilir:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="ToStringInheritance":::

Yöntemi için kendi uygulamanızı sağlayabilirsiniz `PrintMembers` . Bunu yaparsanız, aşağıdaki imzayı kullanın:

* `sealed`Öğesinden türetilen bir kayıt için `object` (bir temel kayıt bildirmez): `private bool PrintMembers(StringBuilder builder)` ;
* Başka bir `sealed` Kayıttan türetilen kayıt için: `protected sealed override bool PrintMembers(StringBuilder builder)` ;
* `sealed`Nesnesinden türetilmiş ve türetilen bir kayıt için:`protected virtual bool PrintMembers(StringBuilder builder);`
* Başka bir kayıttan olmayan ve türetilen bir kayıt için `sealed` : `protected override bool PrintMembers(StringBuilder builder);`

İşte, `PrintMembers` biri nesneden türeyen bir kayıt türü için ve diğeri başka bir kayıttan türetilen kayıt türü için, birleştirilmiş yöntemlerin yerini alan bir kod örneği aşağıdadır:

:::code language="csharp" source="snippets/shared/RecordType.cs" id="PrintMembersImplementation":::

### <a name="deconstructor-behavior-in-derived-records"></a>Türetilmiş kayıtlarda Oluşturucu kaldırma davranışı

`Deconstruct`Türetilmiş bir kaydın yöntemi, derleme zamanı türünün tüm konumsal özelliklerinin değerlerini döndürür. Değişken türü bir temel kayıt ise, nesne türetilmiş türe yayınlanmadığı müddetçe yalnızca temel kayıt özellikleri kaldırılır. Aşağıdaki örnekte, türetilmiş bir kayıttaki bir Deconstructor çağrısı gösterilmektedir.

:::code language="csharp" source="snippets/shared/RecordType.cs" id="DeconstructorInheritance":::

## <a name="generic-constraints"></a>Genel kısıtlamalar

Bir türün kayıt olmasını gerektiren genel kısıtlama yoktur. Kısıtlamayı karşılayan kayıtlar `class` . Belirli bir kayıt türü hiyerarşisinde kısıtlama yapmak için, kısıtlamayı temel bir sınıf olacak şekilde temel kayda koyun. Daha fazla bilgi için bkz. [tür parametrelerindeki kısıtlamalar](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sınıflar](~/_csharplang/spec/classes.md) bölümüne bakın.

C# 9 ve sonraki sürümlerde tanıtılan özellikler hakkında daha fazla bilgi için aşağıdaki özellik teklifi notlarına bakın:

- [Kayıtlar](~/_csharplang/proposals/csharp-9.0/records.md)
- [Yalnızca Init ayarlayıcıları](~/_csharplang/proposals/csharp-9.0/init.md)
- [Birlikte değişken dönüşler](~/_csharplang/proposals/csharp-9.0/covariant-returns.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Tasarım yönergeleri-sınıf ve yapı arasında seçim yapma](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Tasarım yönergeleri-yapı tasarımı](../../../standard/design-guidelines/struct.md)
- [Sınıflar ve yapılar](../../programming-guide/classes-and-structs/index.md)
- [`with` ifadesini](../operators/with-expression.md)
