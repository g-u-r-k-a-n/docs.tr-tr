---
description: temsilci işleci-C# başvurusu
title: temsilci işleci-C# başvurusu
ms.date: 09/25/2020
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: db2bf673db12e4a10741a26112820726a4b8aaee
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247663"
---
# <a name="delegate-operator-c-reference"></a>Delegate işleci (C# Başvurusu)

`delegate`İşleci, bir temsilci türüne dönüştürülebilen anonim bir yöntem oluşturur:

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> C# 3 ' ten başlayarak lambda ifadeleri anonim bir işlev oluşturmanın daha kısa ve açıklayıcı bir yolunu sağlar. Lambda ifadesi oluşturmak için [=> işlecini](lambda-operator.md) kullanın:
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> Lambda ifadelerinin özellikleri hakkında daha fazla bilgi için örneğin, dış değişkenleri yakalama, bkz. [lambda ifadeleri](lambda-expressions.md).

`delegate`İşlecini kullandığınızda parametre listesini atlayabilirsiniz. Bunu yaparsanız, oluşturulan anonim yöntem, aşağıdaki örnekte gösterildiği gibi, herhangi bir parametre listesiyle bir temsilci türüne dönüştürülebilir:

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

Bu, lambda ifadeleri tarafından desteklenmeyen anonim yöntemlerin tek işlevsellikleridir. Diğer tüm durumlarda, bir lambda ifadesi satır içi kod yazmak için tercih edilen bir yoldur.

C# 9,0 ile başlayarak, yöntemi tarafından kullanılmayan anonim bir yöntemin iki veya daha fazla giriş parametresini belirtmek için [atarsa](../../discards.md) ' u kullanabilirsiniz:

:::code language="csharp" source="snippets/shared/DelegateOperator.cs" id="SnippetDiscards" :::

Geriye dönük uyumluluk için, yalnızca tek bir parametre adlandırılmışsa `_` , `_` anonim bir yöntemde bu parametrenin adı olarak değerlendirilir.

C# 9,0 ' den itibaren, `static` anonim bir yöntemin bildiriminde değiştiricisini kullanabilirsiniz:

:::code language="csharp" source="snippets/shared/DelegateOperator.cs" id="SnippetStatic" :::

Statik anonim bir yöntem, kapsayan kapsamlardan yerel değişkenleri veya örnek durumunu yakalayabilir.

`delegate`Bir [temsilci türü](../builtin-types/reference-types.md#the-delegate-type)bildirmek için anahtar sözcüğünü de kullanabilirsiniz.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [=> işleci](lambda-operator.md)
