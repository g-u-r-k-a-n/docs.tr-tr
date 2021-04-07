---
title: Bir sınıf veya yapı için değer eşitliği tanımlama-C# Programlama Kılavuzu
description: Bir sınıf veya yapı için değer eşitliği tanımlama hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir kaynakları görüntüleyin.
ms.date: 03/26/2021
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: fd8e1e14650a836178534b44dc332215c0d0586a
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079459"
---
# <a name="how-to-define-value-equality-for-a-class-or-struct-c-programming-guide"></a>Bir sınıf veya yapı için değer eşitliği tanımlama (C# Programlama Kılavuzu)

[Kayıtlar](../classes-and-structs/records.md) otomatik olarak değer eşitlik uygular. `record` `class` Türü, verileri modellediğinde ve değer eşitlik uygulaması gerektiğinde bir yerine bir tanımlamayı düşünün.

Bir sınıf veya yapı tanımladığınızda, türün tür için özel bir değer eşitlik tanımı (veya denklik) oluşturmak mantıklı olup olmadığına karar verirsiniz. Genellikle, bir koleksiyona tür nesneleri eklemeyi veya birincil amaçları bir alan veya özellik kümesini depolamak istediğinizde değer eşitlik uygulamanız gerekir. Değer eşitlik tanımınızı, türdeki tüm alanların ve özelliklerin bir karşılaştırmasına dayandırıp veya tanımı bir alt küme üzerinde temel alabilirsiniz.

Her iki durumda da, hem sınıflarda hem de yapılarda, uygulamanız beş denklik garantisini izlemelidir (aşağıdaki kurallar için, `x` `y` ve null olmadığını varsayın `z` ):  
  
1. Yansımalı Özellik: `x.Equals(x)` döndürür `true` .
  
2. Simetrik özelliği: `x.Equals(y)` ile aynı değeri döndürür `y.Equals(x)` .
  
3. Geçişli Özellik: `(x.Equals(y) && y.Equals(z))` döndürürse `true` , `x.Equals(z)` döndürür `true` .
  
4. Art arda yapılan çağırmaları, `x.Equals(y)` x ve y tarafından başvurulan nesneler değiştirilmedikçe aynı değeri döndürür.  
  
5. Null olmayan herhangi bir değer null değerine eşit değildir. Ancak, `x.Equals(y)` null olduğunda bir özel durum oluşturur `x` . Bu, bağımsız değişkenine göre 1 veya 2 olan kuralları keser `Equals` .

Tanımladığınız herhangi bir yapı, <xref:System.ValueType?displayProperty=nameWithType> yöntemin geçersiz kılınmasına devraldığı bir değer eşitlik varsayılan uygulamasına sahiptir <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> . Bu uygulama, türündeki tüm alanları ve özellikleri incelemek için yansıma kullanır. Bu uygulama doğru sonuçlar üretse de, özellikle tür için yazdığınız özel bir uygulamayla karşılaştırıldığında nispeten yavaştır.  
  
Değer eşitlik için uygulama ayrıntıları sınıflar ve yapılar için farklıdır. Ancak, her iki sınıf ve yapı, eşitlik uygulamak için aynı temel adımları gerektirir:  
  
1. [Sanal](../../language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> yöntemi geçersiz kılın. Çoğu durumda, uygulamanız `bool Equals( object obj )` yalnızca `Equals` arabirimin uygulanması olan türe özgü yöntemi çağırmalıdır <xref:System.IEquatable%601?displayProperty=nameWithType> . (Bkz. 2. adım.)  
  
2. <xref:System.IEquatable%601?displayProperty=nameWithType>Bir türe özgü Yöntem sağlayarak arabirimini uygulayın `Equals` . Bu, gerçek denklik karşılaştırmasının gerçekleştirildiği yerdir. Örneğin, sizin yazarken yalnızca bir veya iki alanı karşılaştırarak eşitlik tanımlamaya karar verebilirsiniz. ' Den özel durum oluşturmayın `Equals` . Devralmayla ilişkili sınıflar için:

   * Bu yöntem yalnızca sınıfında belirtilen alanları incelemelidir. `base.Equals`Temel sınıfta bulunan alanları incelemek için çağırmalıdır. ( `base.Equals` Türü doğrudan öğesinden devralırsa <xref:System.Object> , ' <xref:System.Object> nin uygulanması <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> bir başvuru eşitlik denetimi gerçekleştirdiğinden, ' i çağırmayın.)

   * Yalnızca karşılaştırılan değişkenlerin çalışma zamanı türleri aynıysa, iki değişken eşit kabul edilmelidir. Ayrıca, `IEquatable` `Equals` bir değişkenin çalışma zamanı ve derleme zamanı türleri farklıysa, çalışma zamanı türü için yöntemi uygulamasının kullanıldığından emin olun. Çalışma zamanı türlerinin her zaman doğru şekilde karşılaştırıldığından emin olmak için tek bir strateji, `IEquatable` yalnızca sınıflarda uygulama amaçlıdır `sealed` . Daha fazla bilgi için bu makalenin ilerleyen kısımlarında bulunan [sınıf örneğine](#class-example) bakın.
  
3. İsteğe bağlı ancak önerilir: [==](../../language-reference/operators/equality-operators.md#equality-operator-) ve [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) işleçlerini aşırı yükleme.  
  
4. <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>Değer eşitliği olan iki nesnenin aynı karma kodu üretmesi için geçersiz kılın.  
  
5. İsteğe bağlı: "büyüktür" veya "küçüktür" tanımlarını desteklemek Için, <xref:System.IComparable%601> türü için arabirimi uygulayın ve ayrıca [<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) ve [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-) işleçlerini aşırı yüklere ekleyebilirsiniz.  

> [!NOTE]
> C# 9,0 ' den başlayarak, gereksiz ortak kod olmadan değer eşitlik semantiğini almak için kayıtları kullanabilirsiniz.

## <a name="class-example"></a>Sınıf örneği

Aşağıdaki örnek, bir sınıfta (başvuru türü) nasıl değer eşitlik uygulanacağını gösterir.

:::code language="csharp" source="snippets/how-to-define-value-equality-for-a-type/ValueEqualityClass/Program.cs":::

Sınıflarda (başvuru türleri), her iki yöntemin varsayılan uygulanması, bir <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> değer eşitlik denetimi değil, bir başvuru eşitlik karşılaştırması gerçekleştirir. Bir uygulayıcının sanal yöntemi geçersiz kıldığında amaç, bu değere eşitlik semantiğini vermektir.

`==`Ve `!=` işleçleri, sınıf tarafından aşırı yüklenmese bile sınıflarla birlikte kullanılabilir. Ancak, varsayılan davranış bir başvuru eşitlik denetimi gerçekleştirdir. Bir sınıfında, yöntemini aşırı yüklüyorsanız, `Equals` `==` ve `!=` işleçlerini aşırı yükletmelisiniz, ancak gerekli değildir.

> [!IMPORTANT]
> Yukarıdaki örnek kod, her devralma senaryosunu bekleme yöntemine göre işleyemeyebilir. Aşağıdaki kodu inceleyin:
>
> ```csharp
> TwoDPoint p1 = new ThreeDPoint(1, 2, 3);
> TwoDPoint p2 = new ThreeDPoint(1, 2, 4);
> Console.WriteLine(p1.Equals(p2)); // output: True
> ```
>
> Bu kod `p1` `p2` , değerlerin farklılığı eşit olmasına rağmen eşittir `z` . Derleyici, `TwoDPoint` `IEquatable` derleme zamanı türüne göre uygulamasını bir kez çektiğinden, fark yok sayılır.
>
> Türlerin yerleşik değer eşitliği `record` Bu doğru gibi senaryoları işler. `TwoDPoint`Ve `ThreeDPoint` türleri ise `record` , sonucu `p1.Equals(p2)` olur `False` . Daha fazla bilgi için bkz. [ `record` tür devralma hiyerarşilerindeki eşitlik](../../language-reference/builtin-types/record.md#equality-in-inheritance-hierarchies).

## <a name="struct-example"></a>Struct örneği

Aşağıdaki örnek, bir yapıda değer eşitlik 'nın nasıl uygulanacağını gösterir (değer türü):

:::code language="csharp" source="snippets/how-to-define-value-equality-for-a-type/ValueEqualityStruct/Program.cs":::
  
Yapılar için, varsayılan uygulamasının (sürümünde <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> geçersiz kılınan sürüm <xref:System.ValueType?displayProperty=nameWithType> ), türdeki her alanın değerlerini karşılaştırmak için yansıma kullanarak bir değer eşitlik denetimi gerçekleştirir. Bir uygulayıcının bir yapıda sanal yöntemi geçersiz kıldığında `Equals` Amaç, eşitlik denetimini gerçekleştirmeye yönelik daha verimli bir yol sağlamaktır ve isteğe bağlı olarak yapının alanının veya özelliklerinin bir alt kümesinde karşılaştırmayı temel alır.
  
[==](../../language-reference/operators/equality-operators.md#equality-operator-)Struct, açıkça aşırı yüklemediği müddetçe ve [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) işleçleri bir struct üzerinde çalışamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Eşitlik karşılaştırmaları](equality-comparisons.md)
- [C# programlama kılavuzu](../index.md)
