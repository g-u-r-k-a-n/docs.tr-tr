---
description: C# Anahtar Sözcükleri
title: C# Anahtar Sözcükleri
ms.date: 03/17/2021
f1_keywords:
- cs.keywords
helpviewer_keywords:
- keywords [C#]
- C# language, keywords
- Visual C#, keywords
- '@ keyword'
ms.custom: updateeachrelease
ms.openlocfilehash: 7fe4c82f3736232ffc5f0d32694d7c8dbb90f7a8
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075504"
---
# <a name="c-keywords"></a>C# Anahtar Sözcükleri

Anahtar sözcükler, derleyiciye özel anlamlara sahip olan önceden tanımlanmış, ayrılmış tanımlayıcılardır. Bunlar, ön ek olarak içermedikleri sürece programınızda tanımlayıcı olarak kullanılamaz `@` . Örneğin, `@if` geçerli bir tanımlayıcıdır, ancak `if` bunun nedeni `if` bir anahtar sözcüktür.  
  
 Bu konudaki ilk tablo, bir C# programının herhangi bir bölümünde ayrılmış tanımlayıcılar olan anahtar sözcükleri listeler. Bu konudaki ikinci tablo, C# ' deki bağlamsal anahtar sözcükleri listeler. Bağlamsal anahtar sözcüklerde yalnızca sınırlı program bağlamında özel anlamı vardır ve bu bağlamın dışında tanımlayıcılar olarak kullanılabilir. Genellikle, C# diline yeni anahtar sözcükler eklendikçe, önceki sürümlerde yazılmış programları bozmamak için bağlamsal anahtar sözcükler olarak eklenirler.  
  
|||||  
|---|---|---|---|  
|[Soyut](abstract.md)|[gerektiği](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|
|[break](break.md)|[bayt](../builtin-types/integral-numeric-types.md)|[harflerini](switch.md)|[yakalaya](try-catch.md)|
|[char](../builtin-types/char.md)|[checked](checked.md)|[sınıfı](class.md)|[const](const.md)|
|[devam](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[ğini](../builtin-types/reference-types.md)|
|[gösterme](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[yardımının](../builtin-types/enum.md)|
|[olay](event.md)|[anlaşılır](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[yanlýþ](../builtin-types/bool.md)|
|[finally](try-finally.md)|[Düzenle](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[:](for.md)|
|[Foreach](foreach-in.md)|[goto](goto.md)|[kullandıysanız](if-else.md)|[indirgen](../operators/user-defined-conversion-operators.md)|
|['ndaki](in.md)|[int](../builtin-types/integral-numeric-types.md)|[arayüz](interface.md)|[internal](internal.md)|
|[is](is.md)|[ine](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[uzayına](namespace.md)|
|[Yeni](../operators/new-operator.md)|[null](null.md)|[nesne](../builtin-types/reference-types.md)|[işlecinde](../operators/operator-overloading.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[özelleştirme](private.md)|
|[protected](protected.md)|[genel](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[SByte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)|
|[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](../builtin-types/reference-types.md)|
|[sýný](../builtin-types/struct.md)|[değiştirebilirsiniz](switch.md)|[this](this.md)|[throw](throw.md)|
|[değeri](../builtin-types/bool.md)|[almaya](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[olmayan](unchecked.md)|[olmayabilecek](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[kullanarak](using.md)|[sanal](virtual.md)|[void](../builtin-types/void.md)|[volatile](volatile.md)|
|[while](while.md)||||

## <a name="contextual-keywords"></a>Bağlamsal anahtar sözcükler

 Bağlam anahtar sözcüğü kodda belirli bir anlamı sağlamak için kullanılır, ancak C# dilinde ayrılmış bir sözcük değildir. Ve gibi bazı bağlamsal anahtar sözcükler `partial` `where` , iki veya daha fazla bağlamda özel anlamlara sahiptir.  
  
||||  
|---|---|---|  
|[add](add.md)|[and](../operators/patterns.md#logical-patterns)|[ek](extern-alias.md)|
|[ascending](ascending.md)|[async](async.md)|[await](../operators/await.md)|
|[by](by.md)|[descending](descending.md)|[dynamic](../builtin-types/reference-types.md)|
|[eşittir](equals.md)|[Kaynak](from-clause.md)|[Al](get.md)|
|[Genel](../operators/namespace-alias-qualifier.md)|[grup](group-clause.md)|[init](init.md)|
|[birleştirin](into.md)|[ayrılma](join-clause.md)|[atalım](let-clause.md)|
|[nameof](../operators/nameof.md)|[nint](../builtin-types/nint-nuint.md)|[başlatılmadı](../operators/patterns.md#logical-patterns)|
|[NotNull](../../programming-guide/generics/constraints-on-type-parameters.md#notnull-constraint)|[nuınt](../builtin-types/nint-nuint.md)|[dayanır](on.md)|
|[veya](../operators/patterns.md#logical-patterns)|[OrderBy](orderby-clause.md)|[Kısmi (tür)](partial-type.md)|
|[partial (Yöntem)](partial-method.md)|[kayıtlar](../../programming-guide/classes-and-structs/records.md)|[temizlenmesine](remove.md)|
|[seçin](select-clause.md)|[kurmak](set.md)|[yönetilmeyen (genel tür kısıtlaması)](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)|
|[değer](value.md)|[l](var.md)|[when (filtre koşulu)](when.md)|
|[where (genel tür kısıtlaması)](where-generic-type-constraint.md)|[WHERE (sorgu yan tümcesi)](where-clause.md)|[örneklerini şununla değiştirin:](../operators/with-expression.md)|
|[yield](yield.md)|||

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
