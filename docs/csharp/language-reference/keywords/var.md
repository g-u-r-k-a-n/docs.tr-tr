---
description: var-C# başvurusu
title: var-C# başvurusu
ms.date: 10/02/2020
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: b3590ebbcff0894b7864cd4a227a6ea068de42a2
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075517"
---
# <a name="var-c-reference"></a>var (C# Başvurusu)

C# 3 ' ten başlayarak, yöntem kapsamında belirtilen değişkenlerin örtülü bir "tür" olması olabilir `var` . Örtük olarak yazılmış bir yerel değişken, türü kendi kendinize bildirdiyseniz olduğu gibi kesin şekilde yazılır, ancak derleyici türü belirler. Aşağıdaki iki bildirimi `i` işlevsel olarak eşdeğerdir:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

> [!IMPORTANT]
> `var` [Null yapılabilir başvuru türleri](../builtin-types/nullable-reference-types.md) etkinken kullanıldığında, ifade türü null yapılabilir olmasa bile her zaman null yapılabilir bir başvuru türü anlamına gelir.

`var`Anahtar sözcüğünün yaygın kullanımı, Oluşturucu çağırma ifadeleridir. Kullanımı, `var` Aşağıdaki örnekte gösterildiği gibi değişken bildiriminde ve nesne örneklemede bir tür adı yinelemenize izin verir:

```csharp
var xs = new List<int>();
```

C# 9,0 ' den başlayarak, bir alternatif olarak, hedef türü belirtilmiş bir [ `new` ifade](../operators/new-operator.md) kullanabilirsiniz:

```csharp
List<int> xs = new();
List<int>? ys = new();
```

Model eşleme ' de `var` anahtar sözcüğü bir [ `var` düzende](../operators/patterns.md#var-pattern)kullanılır.

## <a name="example"></a>Örnek

Aşağıdaki örnek iki sorgu ifadesini gösterir. İlk ifadede öğesinin kullanımına `var` izin verilir, ancak sorgu sonucunun türü açıkça bir olarak belirtilemediğinden gerekli değildir `IEnumerable<string>` . Ancak, ikinci ifadede, `var` sonucun anonim türlerin bir koleksiyonu olmasına izin verir ve bu türün adı derleyicinin kendisi hariç erişilebilir değildir. Kullanımı, `var` sonuç için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır. Örneğin #2, `foreach` yineleme değişkeninin `item` de örtük olarak yazılmış olması gerektiğini unutmayın.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Örtük olarak yazılan yerel değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [LINQ sorgu işlemlerinde tür ilişkileri](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
