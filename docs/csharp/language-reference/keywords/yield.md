---
title: yield bağlamsal anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: d3fe4cf92ca17457bd541f092f5d146ba6c1c095
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794422"
---
# <a name="yield-c-reference"></a>yield (C# Başvurusu)

Bir ifadede `yield` [bağlamsal anahtar sözcüğünü](index.md#contextual-keywords) kullandığınızda, görünen yöntemin, işlecin veya `get` erişimcinin bir yineleyici olduğunu belirtirsiniz. Bir `yield` Yineleyici tanımlamak için kullanmak, özel bir koleksiyon türü için <xref:System.Collections.Generic.IEnumerator%601> <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> modelini uyguladığınızda açık bir ek sınıfa (bir sabit listesinin durumunu tutan sınıf için bkz. bir örnek için bkz.) gereksinimi ortadan kaldırır.

Aşağıdaki örnekte, `yield` ifadesinin iki formu gösterilmektedir.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Açıklamalar

Her öğeyi birer `yield return` birer döndürmek için bir ifade kullanırsınız.

Bir yineleyici yönteminden döndürülen sıra, [foreach](foreach-in.md) IFADESI veya LINQ sorgusu kullanılarak tüketilebilir. `foreach` Döngünün her yinelemesi yineleyici yöntemini çağırır. Yineleyici yönteminde `yield return` bir ifadeye ulaşıldığında, `expression` döndürülür ve koddaki geçerli konum korunur. Yürütme, yineleyici işlevinin bir sonraki çağrılmasında bu konumdan başlar.

Yinelemeyi sonlandırmak için bir `yield break` ifade kullanabilirsiniz.

Yineleyiciler hakkında daha fazla bilgi için bkz. [yineleyiciler](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Yineleyici yöntemleri ve get erişimcileri

Bir yineleyicinin bildirimi aşağıdaki gerekliliklerle uyuşmalıdır:

- Dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>olmalıdır.

- Bildirimin [in](in-parameter-modifier.md) [ref](ref.md) veya [Out](out-parameter-modifier.md) parametreleri olamaz.

Veya `yield` <xref:System.Collections.IEnumerator> `object`döndüren <xref:System.Collections.IEnumerable> bir yineleyici türü.  Yineleyici veya <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.IEnumerator%601>döndürürse, deyimde deyim `yield return` türünden genel tür parametresine örtük bir dönüştürme olmalıdır.

İçine `yield return` or `yield break` ifadesini ekleyemezsiniz:

- [Lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md) ve [Anonim yöntemler](../operators/delegate-operator.md).

- Güvenli olmayan bloklar içeren yöntemler. Daha fazla bilgi için bkz. [güvenli değil](unsafe.md).

## <a name="exception-handling"></a>Özel durum işleme

Bir `yield return` ifade, try-catch bloğunda bulunamaz. Bir `yield return` ifade, try-finally ifadesinin try bloğunda bulunabilir.

Bir `yield break` ifade bir try bloğunda veya catch bloğunda bulunabilir, ancak finally bloğunda yer alabilir.

`foreach` Gövde (yineleyici yönteminin dışında) bir özel durum oluşturursa, yineleyici yönteminde bir `finally` blok yürütülür.

## <a name="technical-implementation"></a>Teknik uygulama

Aşağıdaki kod bir yineleyici yönteminden `IEnumerable<string>` bir döndürür ve sonra öğeleri boyunca yinelenir.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

Çağrısı `MyIteratorMethod` , yönteminin gövdesini yürütmez. Bunun yerine, çağrı `IEnumerable<string>` `elements` değişkenine bir döndürür.

`foreach` Döngüsünün bir yinelemesinde, <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi için `elements`çağrılır. Bu çağrı, sonraki `MyIteratorMethod` `yield return` ifadeye ulaşılana kadar gövdesini yürütür. `yield return` Deyimi tarafından `element` döndürülen ifade, yalnızca döngü gövdesi tarafından tüketim için değişkenin değerini değil, öğesinin <xref:System.Collections.Generic.IEnumerator%601.Current%2A> `elements`özelliğini de bir `IEnumerable<string>`olarak belirler.

`foreach` Döngünün sonraki tekrarında, yineleyici gövdesinin yürütülmesi kaldığınız yerden devam eder, bir `yield return` ifadeye ulaştığında yeniden durdurulur. Yineleyici `foreach` yönteminin sonuna veya bir `yield break` ifadeye ulaşıldığında döngü tamamlanır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `for` döngüsünün içinde `yield return` olan bir ifade vardır. Yöntemi içindeki `foreach` ifade gövdesinin her yinelemesi, `Power` Yineleyici işlevine bir çağrı oluşturur. `Main` Yineleyici işlevine yapılan her çağrı, `yield return` `for` döngüsünün bir sonraki yinelemesi sırasında ortaya çıkan deyimin bir sonraki yürütmeye ilerler.

Yineleyici yönteminin dönüş türü <xref:System.Collections.IEnumerable>, yineleyici arabirim türü olan. Yineleyici yöntem çağrıldığında, bir sayının kuvvetlerini içeren sayılabilir bir nesne döndürür.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, yineleyici olan `get` bir erişimciyi gösterir. Örnekte, her `yield return` bir ifade Kullanıcı tanımlı bir sınıfın bir örneğini döndürür.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Yineleyiciler](../../iterators.md)
