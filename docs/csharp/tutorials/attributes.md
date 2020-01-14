---
title: 'Öğretici: öznitelikleri kullanın-C#'
description: Özniteliklerin içinde C#nasıl çalıştığını öğrenin.
author: mgroves
ms.technology: csharp-fundamentals
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: 24cb7d35a89fda78511dc4ba725b69c5d601a008
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937465"
---
# <a name="use-attributes-in-c"></a>C\# öznitelikleri kullanma

Öznitelikler, bilgileri bildirimli bir şekilde kod ile ilişkilendirmenin bir yolunu sağlar. Ayrıca, çeşitli hedeflere uygulanabilen yeniden kullanılabilir bir öğe de sağlayabilir.

`[Obsolete]` özniteliğini göz önünde bulundurun. Bu sınıf, yapı, yöntem, Oluşturucu ve daha fazlasına uygulanabilir. Öğenin eski olduğunu _bildirir_ . Daha sonra bu özniteliği aramak için C# derleyiciye ve yanıt olarak bazı eylemler yapılır.

Bu öğreticide, kodunuza nasıl öznitelik ekleneceği, kendi öznitelerinizi nasıl oluşturacağınız ve kullanacağınız ve .NET Core 'da yerleşik bazı özniteliklerin nasıl kullanılacağı gösterilir.

## <a name="prerequisites"></a>Prerequisites
Makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. Yükleme yönergelerini [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz.
Bu uygulamayı Windows, Ubuntu Linux, macOS veya bir Docker kapsayıcısında çalıştırabilirsiniz.
En sevdiğiniz kod düzenleyicinizi yüklemeniz gerekir. Aşağıdaki açıklamalar açık kaynaklı, platformlar arası düzenleyici olan [Visual Studio Code](https://code.visualstudio.com/) kullanır. Bununla birlikte, rahat olan her türlü aracı kullanabilirsiniz.

## <a name="create-the-application"></a>Uygulamayı oluşturma

Tüm araçları yüklemişseniz, yeni bir .NET Core uygulaması oluşturun. Komut satırı Oluşturucuyu kullanmak için, en sevdiğiniz kabukta aşağıdaki komutu yürütün:

`dotnet new console`

Bu komut, tam kemikler .NET Core proje dosyaları oluşturur. Bu projeyi derlemek için gereken bağımlılıkları geri yüklemek için `dotnet restore` yürütmeniz gerekir.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Programı yürütmek için `dotnet run`kullanın. Konsola "Hello, World" çıkışını görmeniz gerekir.

## <a name="how-to-add-attributes-to-code"></a>Koda öznitelikler ekleme

' C#De, öznitelikleri `Attribute` temel sınıfından devraldığı sınıflardır. `Attribute` devralan herhangi bir sınıf, diğer kod parçalarında "Tag" sıralaması olarak kullanılabilir.
Örneğin, `ObsoleteAttribute`adlı bir öznitelik vardır. Bu, kodun artık kullanılmıyor olduğunu ve artık kullanılmaması gerektiğini bildirmek için kullanılır. Bu özniteliği bir sınıfa, örneğin köşeli ayraçları kullanarak yerleştirebilirsiniz.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]

Sınıfı `ObsoleteAttribute`çağrıldığında yalnızca kodda `[Obsolete]` kullanılması gerekir. Bu, C# aşağıdaki bir kuraldır.
' I seçerseniz tam adı `[ObsoleteAttribute]` kullanabilirsiniz.

Bir sınıf kullanım dışı olarak işaretlenirken, *neden* kullanımdan kalktı ve/veya bunun yerine *ne tür* bir bilgi sağlamanız yararlı olur. Bunu, kullanılmayan özniteliğe bir String parametresi geçirerek yapın.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Dize, `var attr = new ObsoleteAttribute("some string")`yazarken olduğu gibi `ObsoleteAttribute` oluşturucusuna bağımsız değişken olarak geçirilir.

Öznitelik oluşturucusuna yönelik parametreler basit türler/değişmez değerler: `bool, int, double, string, Type, enums, etc` ve bu türlerin dizileri ile sınırlıdır.
Bir ifade veya değişken kullanamazsınız. Konumsal veya adlandırılmış parametrelerin kullanımı ücretsizdir.

## <a name="how-to-create-your-own-attribute"></a>Kendi öznitelerinizi oluşturma

Bir öznitelik oluşturmak `Attribute` temel sınıfından devralma kadar basittir.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Yukarıdaki gibi, artık kod tabanında başka bir öznitelik olarak `[MySpecial]` (veya `[MySpecialAttribute]`) kullanabilirsiniz.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

`ObsoleteAttribute` gibi .NET temel sınıf kitaplığındaki öznitelikler, derleyicinin içindeki belirli davranışları tetikler. Ancak, oluşturduğunuz herhangi bir öznitelik yalnızca meta veri olarak davranır ve yürütülen öznitelik sınıfı içinde herhangi bir koda neden olmaz. Bu meta verileri kodunuzun başka bir yerinde (daha sonra öğreticide daha sonra) uygulamak sizin için önemlidir.

Burada izlemek için bir ' Gotcha ' bulunur. Yukarıda belirtildiği gibi, öznitelikleri kullanırken yalnızca belirli türlerin bağımsız değişken olarak geçirilmesine izin verilir. Ancak, bir öznitelik türü oluştururken, derleyici bu C# parametreleri oluşturmamak için bunu durdurmaz. Aşağıdaki örnekte, yalnızca iyi şekilde derlenen bir oluşturucuya sahip bir öznitelik oluşturduğdum.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Ancak, bu oluşturucuyu öznitelik söz dizimi ile kullanamazsınız.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Yukarıdaki `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type` gibi bir derleyici hatasına neden olur

## <a name="how-to-restrict-attribute-usage"></a>Öznitelik kullanımını kısıtlama

Öznitelikler, bir dizi "hedef" üzerinde kullanılabilir. Yukarıdaki örneklerde bunları sınıflarda gösterilmektedir, ancak bunlar üzerinde de kullanılabilir:

* Derleme
* Sınıf
* Oluşturucu
* Temsilci
* Enum
* Olay
* Alan
* GenericParameter
* Arabirim
* Yöntem
* Modülü
* Parametre
* Özellik
* ReturnValue
* Yapı

Bir öznitelik sınıfı oluşturduğunuzda, varsayılan olarak, C# bu özniteliği olası öznitelik hedeflerinin herhangi birinde kullanmanıza izin verir. Öznitelerinizi belirli hedeflere kısıtlamak istiyorsanız, öznitelik sınıfınıza `AttributeUsageAttribute` kullanarak bunu yapabilirsiniz. Bu, öznitelik üzerindeki bir özniteliği!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Yukarıdaki özniteliği bir sınıf veya yapı olmayan bir şeye koymaya çalışırsanız, `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations` gibi bir derleyici hatası alacaksınız

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Bir kod öğesine eklenen öznitelikleri kullanma

Öznitelikler meta veri olarak davranır. Dışarı hiçbir dışa zorlama olmadan aslında hiçbir şey yapmaz.

Öznitelikleri bulmak ve üzerinde işlem yapmak için, [yansıma](../programming-guide/concepts/reflection.md) genellikle gereklidir. Bu öğreticide yansıma derinlemesine bir savunma ele alınmayacak, ancak temel fikir, yansıma ' de C# diğer kodu incelediği için kod yazmanıza olanak tanır.

Örneğin, bir sınıf hakkında bilgi almak için yansıma kullanabilirsiniz (kodunuzun baş `using System.Reflection;` ekleyin):

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Bu, şöyle bir şey yazdıracaktır: `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

`TypeInfo` bir nesneniz (veya bir `MemberInfo`, `FieldInfo`, vb) varsa, `GetCustomAttributes` yöntemini kullanabilirsiniz. Bu, `Attribute` nesnelerinin bir koleksiyonunu döndürür.
Ayrıca, `GetCustomAttribute` kullanabilir ve bir öznitelik türü belirtebilirsiniz.

Aşağıda, `MyClass` için bir `MemberInfo` örneği üzerinde `GetCustomAttributes` kullanılmasına bir örnek verilmiştir (daha önce gördük daha önce üzerinde bir `[Obsolete]` özniteliği vardır).

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Bu işlem konsola yazdıracaktır: `Attribute on MyClass: ObsoleteAttribute`. `MyClass`diğer öznitelikleri eklemeyi deneyin.

Bu `Attribute` nesnelerinin örneklendiği unutulmamalıdır geç. Diğer bir deyişle, `GetCustomAttribute` veya `GetCustomAttributes`kullanana kadar bunlar örneklenemez.
Bunlar her seferinde de örneklenmiştir. Bir satırda `GetCustomAttributes` iki kez çağrılması, `ObsoleteAttribute`iki farklı örnek döndürür.

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Temel sınıf kitaplığındaki (BCL) ortak öznitelikler

Öznitelikler birçok araç ve çerçeve tarafından kullanılır. NUnit, NUnit Test Çalıştırıcısı tarafından kullanılan `[Test]` ve `[TestFixture]` gibi öznitelikleri kullanır. ASP.NET MVC `[Authorize]` gibi öznitelikleri kullanır ve MVC eylemleri üzerinde çapraz kesme sorunları gerçekleştirmek için bir eylem filtresi çerçevesi sağlar. [Postsharp](https://www.postsharp.net) , ' de C#en boy yönelimli programlamaya izin vermek için öznitelik sözdizimini kullanır.

.NET Core temel sınıf kitaplıklarında yerleşik olarak bulunan bazı önemli öznitelikleri aşağıda verilmiştir:

* `[Obsolete]`. Bu bir tane Yukarıdaki örneklerde kullanılmıştır ve `System` ad alanında bulunur. Değişen kod tabanı hakkında bildirime dayalı belgeler sağlamak yararlıdır. Bir ileti bir dize biçiminde sağlanıyor ve bir derleyici uyarısına bir derleyici hatasına iletmek için başka bir Boolean parametresi kullanılabilir.

* `[Conditional]`. Bu öznitelik `System.Diagnostics` ad alanıdır. Bu öznitelik yöntemlere (veya öznitelik sınıflarına) uygulanabilir. Oluşturucuya bir dize geçirmeniz gerekir.
Bu dize bir `#define` yönergeyle eşleşmiyorsa, bu yönteme yapılan çağrılar (ancak yöntemin kendisi değil) C# derleyici tarafından kaldırılır. Genellikle bu, hata ayıklama (Tanılama) amaçlarıyla kullanılır.

* `[CallerMemberName]`. Bu öznitelik, parametrelerde kullanılabilir ve `System.Runtime.CompilerServices` ad alanında bulunabilir. Bu, başka bir yöntemi çağıran yöntemin adını eklemek için kullanılan bir özniteliktir. Bu, genellikle çeşitli kullanıcı arabirimi çerçevelerinde INotifyPropertyChanged uygularken ' sihirli dizeler ' ' i ortadan kaldırmanın bir yolu olarak kullanılır. Örneğin:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

Yukarıdaki kodda, bir sabit `"Name"` dize olması gerekmez. Bu, typo ile ilgili hataları önlemeye yardımcı olabilir ve ayrıca daha yumuşak yeniden düzenleme/yeniden adlandırma sağlar.

## <a name="summary"></a>Özet

Öznitelikler bildirime dayalı güç sağlar C#, ancak bunlar bir meta veri biçimidir ve kendilerine göre hareket ederler.
