---
description: Atama işleçleri-C# başvurusu
title: Atama işleçleri-C# başvurusu
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 702652cc7ae05d6a2bfd419ebce55399b9403a52
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075439"
---
# <a name="assignment-operators-c-reference"></a>Atama işleçleri (C# Başvurusu)

Atama işleci, `=` sağ işleneninin değerini bir değişkene, [özelliğe](../../programming-guide/classes-and-structs/properties.md)veya kendi sol işleneni tarafından verilen bir [Dizin Oluşturucu](../../programming-guide/indexers/index.md) öğesine atar. Atama ifadesinin sonucu, sol işlenene atanan değerdir. Sağ işlenenin türü, sol işlenenin türüyle aynı veya örtülü olarak dönüştürülebilir olmalıdır.

Atama işleci, `=` doğru ilişkilendirilebilir, diğer bir deyişle, formun bir ifadesi

```csharp
a = b = c
```

şöyle değerlendirilir

```csharp
a = (b = c)
```

Aşağıdaki örnek, bir yerel değişken, bir özellik ve bir Dizin Oluşturucu öğesi olan atama işlecinin kullanımını sol işlenen olarak gösterir:

[!code-csharp-interactive[simple assignment](snippets/shared/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>ref atama işleci

C# 7,3 ' den başlayarak ref atama işlecini kullanarak `= ref` bir [ref yerel](../keywords/ref.md#ref-locals) veya [ref ReadOnly yerel](../keywords/ref.md#ref-readonly-locals) değişkenini yeniden atayabilirsiniz. Aşağıdaki örnek, ref atama işlecinin kullanımını gösterir:

[!code-csharp[ref assignment operator](snippets/shared/AssignmentOperator.cs#RefAssignment)]

Ref atama operatörü durumunda, her iki işleneni de aynı türde olmalıdır.

## <a name="compound-assignment"></a>Bileşik atama

Bir ikili işleci için `op` , formun bileşik atama ifadesi

```csharp
x op= y
```

eşdeğerdir

```csharp
x = x op y
```

hariç `x` yalnızca bir kez değerlendirilir.

Bileşik atama [Aritmetik](arithmetic-operators.md#compound-assignment), [Boole mantıksal](boolean-logical-operators.md#compound-assignment)ve [bit düzeyinde mantıksal ve kaydırma](bitwise-and-shift-operators.md#compound-assignment) işleçleri tarafından desteklenir.

## <a name="null-coalescing-assignment"></a>Null birleştirme ataması

C# 8,0 ' den başlayarak, sağ işleneninin değerini yalnızca sol taraftaki işlenenin ' `??=` i değerlendirildiğinde sol tarafından atamak için null birleşim atama işlecini kullanabilirsiniz `null` . Daha fazla bilgi için?? [ve?? = operatörler](null-coalescing-operator.md) makalesi.

## <a name="operator-overloadability"></a>Operatör overloadability

Kullanıcı tanımlı bir tür atama işlecini [aşırı yükleyemez](operator-overloading.md) . Ancak, Kullanıcı tanımlı bir tür, başka bir türe örtük bir dönüştürme tanımlayabilir. Bu şekilde, Kullanıcı tanımlı bir türün değeri bir değişkene, özelliğe veya başka bir türün Dizin Oluşturucu öğesine atanabilir. Daha fazla bilgi için bkz. [Kullanıcı tanımlı dönüştürme işleçleri](user-defined-conversion-operators.md).

Kullanıcı tanımlı bir tür, bileşik atama işlecini açıkça aşırı yükleyemez. Ancak, Kullanıcı tanımlı bir tür ikili bir işleci aşırı yükle, varsa `op` `op=` işleç da dolaylı olarak aşırı yüklenmiştir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [atama işleçleri](~/_csharplang/spec/expressions.md#assignment-operators) bölümüne bakın.

Ref atama işleci hakkında daha fazla bilgi için `= ref` bkz. [özellik teklifi Not](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [ref anahtar sözcüğü](../keywords/ref.md)
