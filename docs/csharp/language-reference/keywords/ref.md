---
description: ref anahtar sözcüğü-C# başvurusu
title: ref anahtar sözcüğü-C# başvurusu
ms.date: 03/29/2021
f1_keywords:
- ref_CSharpKeyword
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 3392e560eaf0bac39cf4e9707574fd2bb3d96057
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079446"
---
# <a name="ref-c-reference"></a>ref (C# Başvurusu)

`ref`Anahtar sözcüğü, bir değerin başvuruya göre geçtiğini gösterir. Dört farklı bağlamda kullanılır:

- Bir yöntem imzasında ve bir yöntem çağrısında, bir bağımsız değişkeni başvuruya göre bir yönteme geçirmek için. Daha fazla bilgi için bkz. [bir bağımsız değişkeni başvuruya göre geçirme](#passing-an-argument-by-reference).
- Bir yöntem imzasında, çağıran öğesine başvuruya göre bir değer döndürün. Daha fazla bilgi için bkz. [Başvuru dönüş değerleri](#reference-return-values).
- Bir üye gövdesinde, bir başvuru dönüş değerinin, çağıranın değiştirme amaçladığı bir başvuru olarak yerel olarak depolandığını belirtmek için. Ya da yerel bir değişkenin başvuruya göre başka bir değere eriştiği anlamına gelebilir. Daha fazla bilgi için bkz. [ref Yereller](#ref-locals).
- Bir `struct` bildiriminde bir veya bir bildirmek için `ref struct` `readonly ref struct` . Daha fazla bilgi için [yapı türleri](../builtin-types/struct.md) makalesinin [ `ref` struct](../builtin-types/struct.md#ref-struct) bölümüne bakın.

## <a name="passing-an-argument-by-reference"></a>Bir bağımsız değişkeni başvuruya göre geçirme

Bir yöntemin parametre listesinde kullanıldığında, `ref` anahtar sözcüğü bir bağımsız değişkenin değere göre değil başvuruya göre geçtiğini gösterir. `ref`Anahtar sözcüğü, bir değişken olması gereken bağımsız değişken için biçimsel parametreye bir diğer ad getirir. Diğer bir deyişle, parametresindeki tüm işlemler bağımsız değişkende yapılır.

Örneğin, çağıranın yerel bir değişken ifadesi veya dizi öğesi erişim ifadesi geçirdiğini varsayalım. Çağrılan yöntem daha sonra ref parametresinin başvurduğu nesnenin yerini alabilir. Bu durumda, çağıran yerel değişkeni veya dizi öğesi, yöntemi döndürüldüğünde yeni nesneye başvurur.

> [!NOTE]
> Başvuru türü kavramıyla başvuruya göre geçirme kavramını karıştırmayın. İki kavram aynı değildir. Bir yöntem parametresi `ref` , bir değer türü veya bir başvuru türü olmasına bakılmaksızın değiştirilebilir. Başvuru ile geçirildiğinde bir değer türünün kutulenmesi yoktur.  

Bir parametre kullanmak için `ref` , `ref` Aşağıdaki örnekte gösterildiği gibi yöntem tanımı ve çağırma yöntemi anahtar sözcüğünü açıkça kullanmalıdır. (Çağırma yöntemi `ref` BIR COM çağrısı yapılırken atlayabilir.)

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

Bir veya parametresine geçirilen bir bağımsız değişken `ref` `in` geçirilmeden önce başlatılmalıdır. Bu gereksinim, bağımsız değişkenlerin geçirilmeden önce açıkça başlatılması gereken [Out](out-parameter-modifier.md) parametrelerinden farklıdır.

Bir sınıfın üyelerinin yalnızca `ref` ,, veya ile farklı imzaları olamaz `in` `out` . Bir türün iki üyesi arasındaki tek fark, bir `ref` parametre içeriyorsa ve diğeri `out` veya parametresi varsa bir derleyici hatası oluşur `in` . Aşağıdaki kod, örneğin derlenmiyor.  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

Ancak, bir yöntem bir `ref` , `in` veya `out` parametresi olduğunda ve diğeri, aşağıdaki örnekte gösterildiği gibi değere göre geçirilen bir parametreye sahip olduğunda Yöntemler aşırı yüklenebilir.
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 İmza eşleştirmesi gerektiren diğer durumlarda,,, ve,, ve ' ı gizleme veya geçersiz kılma,,, `in` `ref` ve birbirini `out` eşleştirmeyin.  
  
 Özellikler değişken değildir. Bunlar yöntemlerdir ve `ref` parametrelere geçirilemez.  
  
 `ref` `in` `out` Aşağıdaki tür yöntemler için, ve anahtar sözcüklerini kullanamazsınız:  
  
- Zaman [uyumsuz](async.md) değiştirici kullanarak tanımladığınız zaman uyumsuz yöntemler.  
- Bir [yield return](yield.md) veya bildiri içeren Yineleyici yöntemleri `yield break` .

[uzantı yöntemlerinin](../../programming-guide/classes-and-structs/extension-methods.md) bu anahtar sözcüklerin kullanımıyla ilgili kısıtlamaları da vardır:

- `out`Anahtar sözcüğü, bir genişletme yönteminin ilk bağımsız değişkeninde kullanılamaz.
- `ref`Anahtar sözcüğü, bağımsız değişken bir struct olmadığında ya da genel bir tür struct olarak kısıtlanmamışsa Genişletme yönteminin ilk bağımsız değişkeninde kullanılamaz.
- `in`İlk bağımsız değişken bir struct olmadığı müddetçe anahtar sözcüğü kullanılamaz. `in`Anahtar sözcüğü, bir struct gibi sınırlandırsalar bile herhangi bir genel tür üzerinde kullanılamaz.

## <a name="passing-an-argument-by-reference-an-example"></a>Bir bağımsız değişkeni başvuruya göre geçirme: bir örnek

Önceki örneklerde değer türleri başvuruya göre geçer. Başvuru `ref` türlerini başvuruya göre geçirmek için anahtar sözcüğünü de kullanabilirsiniz. Başvuru türü başvuruya göre geçirilme yöntemi, çağrılan yöntemin, başvuru parametresinin çağırıcının başvurduğu nesneyi değiştirmesini sağlar. Nesnenin depolama konumu, başvuru parametresi değeri olarak yöntemine geçirilir. Parametresinin depolama konumundaki değeri değiştirirseniz (yeni bir nesneyi işaret etmek için), çağıranın başvurduğu depolama konumunu da değiştirirsiniz. Aşağıdaki örnek, bir başvuru türünün örneğini bir parametre olarak geçirir `ref` .
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

Başvuru türlerini değere ve başvuruya göre geçirme hakkında daha fazla bilgi için bkz. [Reference-Type parametrelerini geçirme](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Başvuru dönüş değerleri

Başvuru dönüş değerleri (veya ref dönüşler), bir yöntemin çağırana başvuruya göre döndürdüğü değerlerdir. Diğer bir deyişle, çağıran bir yöntem tarafından döndürülen değeri değiştirebilir ve bu değişiklik çağırma yöntemindeki nesnenin durumunda yansıtılır.

Bir başvuru dönüş değeri `ref` anahtar sözcüğü kullanılarak tanımlanır:

- Metot imzasında. Örneğin, aşağıdaki yöntem imzası, `GetCurrentPrice` yöntemin başvuruya göre bir değer döndürdüğünü gösterir <xref:System.Decimal> .

```csharp
public ref decimal GetCurrentPrice()
```

- `return`Belirteç ve `return` yöntemin içindeki bir ifadede döndürülen değişken. Örnek:

```csharp
return ref DecimalArray[0];
```

Çağıranın nesnenin durumunu değiştirmesi için, başvuru dönüş değeri açıkça bir [ref yerel](#ref-locals)olarak tanımlanmış bir değişkene depolanmalıdır.

Burada hem yöntem imzasını hem de Yöntem gövdesini gösteren daha tamamlanmış bir ref Return örneği verilmiştir.

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Çağrılan yöntem, `ref readonly` değeri başvuruya göre döndürmek için dönüş değerini de bildirebilir ve çağıran kodun döndürülen değeri değiştiremeyeceğini zorunlu kılabilir. Çağırma yöntemi, değeri yerel bir [ref salt okunur](#ref-readonly-locals) değişkeninde depolayarak döndürülen değeri kopyalamayı önleyebilir.

Bir örnek için, bkz. [bir başvuru dönüşleri ve ref Yereller örneği](#a-ref-returns-and-ref-locals-example).

## <a name="ref-locals"></a>Başvuru yerelleri

Kullanılarak döndürülen değerlere başvurmak için bir başvuru yerel değişkeni kullanılır `return ref` . Bir ref yerel değişkeni, ref olmayan bir dönüş değeri olarak başlatılamaz. Diğer bir deyişle, başlatmanın sağ tarafı bir başvuru olmalıdır. Ref Local değerindeki tüm değişiklikler, metodu, yöntemi başvuruya göre döndürülen nesnenin durumuna yansıtılır.

Anahtar sözcüğünü iki yerde kullanarak bir ref yerel tanımlayın `ref` :

- Değişken bildiriminden önce.
- Başvuruya göre değeri döndüren yöntemine yapılan çağrıdan hemen önce.

Örneğin, aşağıdaki ifade adlı bir yöntem tarafından döndürülen bir başvuru yerel değeri tanımlar `GetEstimatedValue` :

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Başvuruya göre bir değere aynı şekilde erişebilirsiniz. Bazı durumlarda, başvuruya göre değere erişmek, potansiyel olarak pahalı bir kopyalama işlemini önleyerek performansı artırır. Örneğin, aşağıdaki ifade bir değere başvurmak için kullanılan bir ref yerel değişkeninin nasıl tanımlanacağını göstermektedir.

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

Her iki örnekte, `ref` anahtar sözcüğü her iki yerde de kullanılmalıdır veya derleyici hata CS8172 oluşturuyor, "bir değere sahip bir başvuru değişkeni başlatılamaz."

C# 7,3 ' den başlayarak, deyimin yineleme değişkeni `foreach` bir ref yerel veya ref ReadOnly yerel değişkeni olabilir. Daha fazla bilgi için [foreach ifadesi](foreach-in.md) makalesine bakın.

Ayrıca C# 7,3 ' den itibaren, ref [atama işleciyle](../operators/assignment-operator.md#ref-assignment-operator)bir ref yerel veya ref ReadOnly yerel değişkenini yeniden atayabilirsiniz.

## <a name="ref-readonly-locals"></a>Ref ReadOnly Yereller

Ref salt okunur yerel, imzası ve kullanımları olan bir yöntem veya özellik tarafından döndürülen değerlere başvurmak için kullanılır `ref readonly` `return ref` . `ref readonly`Değişken, yerel bir `ref` değişkenin özelliklerini bir değişkenle birleştirir `readonly` : Bu, atandığı depolamanın diğer adıdır ve değiştirilemez.

## <a name="a-ref-returns-and-ref-locals-example"></a>Bir ref, ve ref Yereller örneği döndürür

Aşağıdaki örnek `Book` , ve iki alanı olan bir sınıfı tanımlar <xref:System.String> `Title` `Author` . Ayrıca `BookCollection` , özel nesne dizisi içeren bir sınıfı tanımlar `Book` . Bağımsız kitap nesneleri, yöntemi çağırarak başvuruya göre döndürülür `GetBookByTitle` .

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

Çağıran, yöntem tarafından döndürülen değeri `GetBookByTitle` bir ref yerel olarak depoladığında, çağıranın dönüş değeri için yaptığı değişiklikler, `BookCollection` Aşağıdaki örnekte gösterildiği gibi nesnesine yansıtılır.

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli verimli kod yazma](../../write-safe-efficient-code.md)
- [Ref dönüşler ve ref yerel ayarlar](../../programming-guide/classes-and-structs/ref-returns.md)
- [Koşullu başvuru ifadesi](../operators/conditional-operator.md#conditional-ref-expression)
- [Parametreleri Geçirme](../../programming-guide/classes-and-structs/passing-parameters.md)
- [Yöntem Parametreleri](method-parameters.md)
- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
