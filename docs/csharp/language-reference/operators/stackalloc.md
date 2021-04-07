---
description: stackalloc ifadesi-C# başvurusu
title: stackalloc ifadesi-C# başvurusu
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 42867ff1b5acffaf62639a31a5bdd3b4055e252a
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497469"
---
# <a name="stackalloc-expression-c-reference"></a>stackalloc ifadesi (C# Başvurusu)

Bir `stackalloc` ifade, yığında bir bellek bloğunu ayırır. Yöntem yürütme sırasında oluşturulan bir yığın ayrılmış bellek bloğu, bu yöntem döndüğünde otomatik olarak atılır. İle ayrılmış belleği açık bir şekilde serbest bırakılamaz `stackalloc` . Yığın tarafından ayrılan bellek bloğu [çöp toplamaya](../../../standard/garbage-collection/index.md) tabi değildir ve bir [ `fixed` ifadesiyle](../keywords/fixed-statement.md)sabitlenemez.

Bir `stackalloc` ifadenin sonucunu aşağıdaki türlerden birinin değişkenine atayabilirsiniz:

- <xref:System.Span%601?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi C# 7,2 veya sonraki bir sürümünden itibaren <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> :

  [!code-csharp[stackalloc span](snippets/shared/StackallocOperator.cs#AssignToSpan)]

  Bir veya değişkenine bir yığın ayrılmış bellek bloğu atadığınızda, [güvenli olmayan](../keywords/unsafe.md) bir bağlam kullanmanız gerekmez <xref:System.Span%601> <xref:System.ReadOnlySpan%601> .

  Bu türlerle çalıştığınızda, `stackalloc` Aşağıdaki örnekte gösterildiği gibi [koşullu](conditional-operator.md) veya atama ifadelerinde bir ifade kullanabilirsiniz:

  [!code-csharp[stackalloc expression](snippets/shared/StackallocOperator.cs#AsExpression)]

  C# 8,0 ' den başlayarak, `stackalloc` <xref:System.Span%601> <xref:System.ReadOnlySpan%601> Aşağıdaki örnekte gösterildiği gibi, bir veya değişkenine izin verildiğinde, diğer ifadelerin içindeki bir ifadeyi kullanabilirsiniz:

  [!code-csharp[stackalloc in nested expressions](snippets/shared/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <xref:System.Span%601> <xref:System.ReadOnlySpan%601> Mümkün olduğunda yığın tarafından ayrılan bellekle çalışmak için veya türlerini kullanmanızı öneririz.

- Aşağıdaki örnekte gösterildiği gibi bir [işaretçi türü](../unsafe-code.md#pointer-types):

  [!code-csharp[stackalloc pointer](snippets/shared/StackallocOperator.cs#AssignToPointer)]

  Yukarıdaki örnekte gösterildiği gibi, `unsafe` işaretçi türleriyle çalışırken bir bağlam kullanmanız gerekir.

  İşaretçi türleri söz konusu olduğunda, `stackalloc` değişkeni başlatmak için yalnızca yerel değişken bildiriminde bir ifade kullanabilirsiniz.

Yığındaki kullanılabilir bellek miktarı sınırlıdır. Yığında çok fazla bellek ayırırsanız, bir oluşturulur <xref:System.StackOverflowException> . Bundan kaçınmak için aşağıdaki kuralları izleyin:

- Tahsis ettiğiniz bellek miktarını sınırlayın `stackalloc` :

  [!code-csharp[limit stackalloc](snippets/shared/StackallocOperator.cs#LimitStackalloc)]

  Yığında kullanılabilir bellek miktarı kodun yürütüldüğü ortama bağlı olduğundan, gerçek sınır değerini tanımlarken koruyucu olun.

- `stackalloc`İçindeki döngüleri kullanmaktan kaçının. Bellek bloğunu bir döngü dışında ayırın ve döngü içinde yeniden kullanın.

Yeni ayrılan belleğin içeriği tanımlı değil. Kullanmadan önce onu başlatmalısınız. Örneğin, <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> tüm öğeleri türünün varsayılan değerine ayarlayan yöntemini kullanabilirsiniz `T` .

C# 7,3 ' den başlayarak, dizi başlatıcısı sözdizimini kullanarak yeni ayrılan belleğin içeriğini tanımlayabilirsiniz. Aşağıdaki örnek bunu yapmak için çeşitli yollar göstermektedir:

[!code-csharp[stackalloc initialization](snippets/shared/StackallocOperator.cs#StackallocInit)]

İfadesinde `stackalloc T[E]` , `T` yönetilmeyen bir [tür](../builtin-types/unmanaged-types.md) olmalıdır ve `E` negatif olmayan bir [tamsayı](../builtin-types/integral-numeric-types.md) değeri olarak değerlendirilmelidir.

## <a name="security"></a>Güvenlik

Kullanımı, `stackalloc` ortak dil çalışma zamanında (CLR) arabellek taşması algılama özelliklerini otomatik olarak etkinleştirmektedir. Bir arabellek taşması algılanırsa, kötü amaçlı kodun yürütülmesi olasılığını en aza indirmek için işlem mümkün olduğunca hızlı bir şekilde sonlandırılır.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yığın ayırma](~/_csharplang/spec/unsafe-code.md#stack-allocation) bölümüne ve [ `stackalloc` iç içe bağlamlarda izin ver](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) Özellik teklifi notuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [İşaretçi bağlantılı işleçler](pointer-related-operators.md)
- [İşaretçi türleri](../unsafe-code.md#pointer-types)
- [Bellek ve aralıkla ilgili türler](../../../standard/memory-and-spans/index.md)
- [Stackalloc 'un DOS ve yapılmaması](https://vcsjones.dev/2020/02/24/stackalloc/)
