---
title: Sınıflar, yapılar ve kayıtlar-C# Programlama Kılavuzu
description: C# ' de sınıfların, yapıların (yapıların) ve kayıtların kullanımını açıklar.
ms.date: 04/06/2021
helpviewer_keywords:
- structs [C#], about structs
- records [C#], about records
- classes [C#], overview
- C# language, structs
- C# language, records
- C# language, objects
- objects [C#]
- C# language, classes
ms.openlocfilehash: 69b62160699ef43343a89fe8bb3deaa2fb3523ba
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075465"
---
# <a name="classes-structs-and-records-c-programming-guide"></a>Sınıflar, yapılar ve kayıtlar (C# Programlama Kılavuzu)

Sınıflar ve yapılar, .NET 'teki ortak tür sisteminin temel yapılarıdır. C# 9, bir tür sınıf olan kayıtları ekler. Her biri, mantıksal birim olarak birbirine ait bir veri kümesini ve davranışları kapsülleyen bir veri yapısıdır. Veri ve davranışlar, sınıf, yapı veya kaydın *üyeleridir* ve bu makalede daha sonra listelendiği gibi yöntemleri, özellikleri, olayları vb. içerirler.

Bir sınıf, yapı veya kayıt bildirimi, çalışma zamanında örnek veya nesne oluşturmak için kullanılan bir şema gibidir. Adlı bir sınıf, yapı veya kayıt tanımlarsanız `Person` , `Person` türünün adıdır. Türünde bir değişken bildirirseniz ve başladıysanız bir `p` `Person` `p` nesne veya örneği olarak ifade edilir `Person` . Aynı türde birden çok örnek `Person` oluşturulabilir ve her bir örnek, özelliklerinde ve alanlarında farklı değerlere sahip olabilir.  
  
Bir sınıf veya kayıt bir başvuru türüdür. Türün bir nesnesi oluşturulduğunda, nesnenin atandığı değişken yalnızca o belleğe yönelik bir başvuru barındırır. Nesne başvurusu yeni bir değişkene atandığında, yeni değişken özgün nesneye başvurur. Her ikisi de aynı verilere başvurduğundan, bir değişken aracılığıyla yapılan değişiklikler diğer değişkene yansıtılır.
  
Struct bir değer türüdür. Bir struct oluşturulduğunda, yapının atandığı değişken yapının gerçek verilerini barındırır. Yapı yeni bir değişkene atandığında, kopyalanır. Bu nedenle, yeni değişken ve özgün değişken aynı verilerin iki ayrı kopyasını içerir. Bir kopyada yapılan değişiklikler diğer kopyayı etkilemez.  
  
Genel olarak, sınıflar daha karmaşık davranışı modellemek veya bir sınıf nesnesi oluşturulduktan sonra değiştirilmesi amaçlanan veriler için kullanılır. Yapılar, öncelikle yapı oluşturulduktan sonra değiştirilmesi amaçlanan verileri içeren küçük veri yapıları için idealdir. Kayıt türleri, öncelikle nesne oluşturulduktan sonra değiştirilmesi amaçlanan verileri içeren daha büyük veri yapılarına yöneliktir.
  
## <a name="example"></a>Örnek

 Aşağıdaki örnekte, `CustomClass` `ProgrammingGuide` ad alanındaki üç üye vardır: örnek Oluşturucu, adlı bir özellik `Number` ve adlı bir yöntem `Multiply` . `Main` `Program` Sınıfındaki yöntemi, bir örneği (nesne) oluşturur `CustomClass` ve nesnenin yöntemi ile özelliğine nokta gösterimi kullanılarak erişilir.
  
 :::code language="csharp" source="../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs" id="Snippet1":::  
  
## <a name="encapsulation"></a>Kapsül  

 *Kapsülleme* bazen nesne odaklı programlamanın ilk ve prensibi olarak adlandırılır. Kapsülleme ilkelerine göre, bir sınıf veya yapı, üyelerinin her birinin ne şekilde erişilebilir olduğunu belirtebilir sınıfın veya yapının dışında kod alma. Sınıf veya derleme dışından kullanılması amaçlanmayan Yöntemler ve değişkenler, kodlama hataları veya kötü amaçlı yazılımlar için potansiyelini sınırlamak üzere gizlenebilir. Daha fazla bilgi için bkz. [nesne odaklı programlama](../../tutorials/intro-to-csharp/object-oriented-programming.md).

## <a name="members"></a>Üyeler

Tüm Yöntemler, alanlar, sabitler, Özellikler ve olaylar bir tür içinde bildirilmelidir; Bunlara tür *üyeleri* denir. C# dilinde, bazı dillerde olduğu gibi genel değişkenler veya yöntemler yoktur. Bir programın giriş noktası bile, `Main` yöntemi bir sınıf veya yapı içinde bildirilmelidir (örtük olarak [en üst düzey deyimler](../main-and-command-args/top-level-statements.md)söz konusu olduğunda).

Aşağıdaki liste, bir sınıf, yapı veya kayıtta bildirilebilecek çeşitli üye türlerini içerir.
  
- [Alanlar](./fields.md)  
- [Sabitler](./constants.md)
- [Özellikler](./properties.md)
- [Yöntemler](./methods.md)
- [Oluşturucular](./constructors.md)
- [Ekinlikler](../events/index.md)
- [Sonlandırıcılar](./destructors.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [İşleçler](../../language-reference/operators/index.md)
- [İç içe türler](./nested-types.md)
  
## <a name="accessibility"></a>Erişilebilirlik  

 Bazı yöntemler ve özellikler, *istemci kodu* olarak bilinen bir sınıf veya yapı dışındaki koddan çağrılmalıdır veya erişilmek üzere tasarlanmıştır. Diğer yöntemler ve özellikler yalnızca sınıfta veya yapıda kullanım için olabilir. Yalnızca amaçlanan istemci kodunun ulaşabilmesi için kodunuzun erişilebilirliğini sınırlandırmamak önemlidir. Aşağıdaki erişim değiştiricilerini kullanarak türlerinizi ve üyelerinin istemci koduna ne kadar erişilebilir olduğunu belirtirsiniz:

- [genel](../../language-reference/keywords/public.md)
- [protected](../../language-reference/keywords/protected.md)
- [internal](../../language-reference/keywords/internal.md)
- [protected internal](../../language-reference/keywords/protected-internal.md)
- [özelleştirme](../../language-reference/keywords/private.md)
- [özel korumalı](../../language-reference/keywords/private-protected.md).

Varsayılan Erişilebilirlik ' dir `private` . Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).  
  
## <a name="inheritance"></a>Devralma  

Sınıflar (ancak yapılar değil) devralma kavramını destekler. Başka bir sınıftan ( *temel sınıf*) türetilen bir sınıf, oluşturucular ve sonlandırıcılar hariç temel sınıfın tüm genel, korunan ve dahili üyelerini otomatik olarak içerir. Daha fazla bilgi için bkz. [Devralma](./inheritance.md) ve çok [biçimlilik](./polymorphism.md).
  
Sınıflar [Özet](../../language-reference/keywords/abstract.md)olarak, bir veya daha fazla yönteminin bir uygulama olmadığı anlamına gelir. Soyut sınıflar doğrudan örneklenemez, ancak eksik uygulamayı sağlayan diğer sınıflar için temel sınıf olarak görev yapabilir. Sınıflar, diğer sınıfların bunlardan devralmasını engellemek için [Sealed](../../language-reference/keywords/sealed.md) olarak da bildirilemez. Daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](./abstract-and-sealed-classes-and-class-members.md).
  
## <a name="interfaces"></a>Arabirimler  

Sınıflar, yapılar ve kayıtlar birden çok arabirimi kalýtýmla alabilir. Bir arabirimden devralması için, türün arabirimde tanımlanmış tüm yöntemleri uyguladığı anlamına gelir. Daha fazla bilgi için bkz. [arabirimler](../interfaces/index.md).  
  
## <a name="generic-types"></a>Genel Türler  

 Sınıflar, yapılar ve kayıtlar bir veya daha fazla tür parametresiyle tanımlanabilir. İstemci kodu, türün bir örneğini oluşturduğunda türü sağlar. Örneğin, <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic> ad alanındaki sınıfı bir tür parametresiyle tanımlanmıştır. İstemci kodu `List<string>` `List<int>` , listenin tutacağız türü belirtmek için bir veya örneği oluşturur. Daha fazla bilgi için bkz. [Genel türler](../generics/index.md).  
  
## <a name="static-types"></a>Statik türler  

Sınıflar (ancak yapılar veya kayıtlar değil) [statik](../../language-reference/keywords/static.md)olarak bildirilemez. Statik bir sınıf yalnızca statik üyeler içerebilir ve `new` anahtar sözcüğüyle başlatılamaz. Program yüklendiğinde sınıfın bir kopyası belleğe yüklenir ve onun üyelerine sınıf adından erişilir. Sınıflar, yapılar ve kayıtlar statik üyeler içerebilir. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).
  
## <a name="nested-types"></a>İç içe Geçmiş Türler

Bir sınıf, yapı veya kayıt başka bir sınıf, yapı veya kayıt içinde iç içe olabilir. Daha fazla bilgi için bkz. [Iç Içe türler](./nested-types.md).
  
## <a name="partial-types"></a>Kısmi türler  

Bir sınıf, yapı veya yöntemin bir parçasını bir kod dosyasında ve farklı bir kod dosyasındaki başka bir bölüme tanımlayabilirsiniz. Daha fazla bilgi için bkz. [kısmi sınıflar ve Yöntemler](./partial-classes-and-methods.md).
  
## <a name="object-initializers"></a>Nesne başlatıcıları  

Yapıcısını açıkça çağırmadan sınıf veya yapı nesneleri ve nesne koleksiyonları oluşturabilir ve başlatabilir. Daha fazla bilgi için bkz. [nesne ve koleksiyon başlatıcıları](./object-and-collection-initializers.md).  
  
## <a name="anonymous-types"></a>Anonim Türler  

Adlandırılmış bir sınıf oluşturmak için uygun veya gerekli olmadığı durumlarda (örneğin, bir listeyi kalıcı hale getirmek veya başka bir yönteme geçirmek zorunda değilsiniz veri yapıları içeren bir liste doldururken), anonim türler kullanırsınız. Daha fazla bilgi için bkz. [anonim türler](./anonymous-types.md).
  
## <a name="extension-methods"></a>Uzantı Metotları  

Metotları özgün türe ait gibi çağrılabilecek ayrı bir tür oluşturarak, türetilmiş sınıf oluşturmadan bir sınıfı "genişletebilirsiniz". Daha fazla bilgi için bkz. [Uzantı yöntemleri](./extension-methods.md).
  
## <a name="implicitly-typed-local-variables"></a>Örtülü Olarak Yazılan Yerel Değişkenler  

Bir sınıf veya yapı yöntemi içinde, derleyicinin derleme zamanında bir değişkenin türünü belirlemesini söylemek için örtük yazma kullanabilirsiniz. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](./implicitly-typed-local-variables.md).

## <a name="records"></a>Kayıtlar

C# 9 `record` , bir sınıf veya yapı yerine oluşturabileceğiniz bir başvuru türü olan türü tanıtır. Kayıtlar, sabit türlerde verileri kapsüllemek için yerleşik davranışa sahip sınıflardır. Bir kayıt aşağıdaki özellikleri sağlar:

* Sabit özelliklere sahip bir başvuru türü oluşturmak için kısa sözdizimi.

* Değer eşitlik.

  Kayıt türünün iki değişkeni, kayıt türü tanımları özdeş ise eşittir ve her alan için her iki kayıttaki değerler eşittir. Bu, başvuru eşitliği kullanan sınıflardan farklıdır: bir sınıf türünün iki değişkeni aynı nesneye başvurduklarında eşittir.

* Geri dönüşlü mutasyon için kısa sözdizimi.

  Bir `with` ifade, var olan Örneğin bir kopyası olan ancak belirtilen özellik değerleri değişmiş olan yeni bir kayıt örneği oluşturmanıza olanak sağlar.

* Görüntüleme için yerleşik biçimlendirme.

  `ToString`Yöntemi, kayıt türü adını ve ortak özelliklerin adlarını ve değerlerini yazdırır.

* Devralma hiyerarşileri için destek.

  Bir kayıt, bir struct değil, kapsamakta olan bir sınıf olduğundan devralma desteklenir.

Daha fazla bilgi için bkz. [kayıtlar](../../language-reference/builtin-types/record.md).

## <a name="c-language-specification"></a>C# Dil Belirtimi  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar](./classes.md)
- [Nesneler](./objects.md)
- [Yapı türleri](../../language-reference/builtin-types/struct.md)
- [Kayıtlar](../../language-reference/builtin-types/record.md)  
- [C# Programlama Kılavuzu](../index.md)
