---
description: "Değer türleri, türleri ve C 'de yerleşik olanlar hakkında bilgi edinin #"
title: Değer türleri-C# başvurusu
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 64c9e9eba2495531cfef8a603d53fb21c95c87a4
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599401"
---
# <a name="value-types-c-reference"></a>Değer türleri (C# Başvurusu)

*Değer türleri* ve [başvuru türleri](../keywords/reference-types.md) , C# türlerinin iki ana kategorileridir. Değer türünde bir değişken türün bir örneğini içerir. Bu, bir tür örneğine başvuru içeren bir başvuru türü değişkeninden farklıdır. Varsayılan olarak, [atama](../operators/assignment-operator.md), bir yönteme bir bağımsız değişken geçirme ve bir yöntem sonucu döndürme, değişken değerleri kopyalanır. Değer türü değişkenler söz konusu olduğunda, karşılık gelen tür örnekleri kopyalanır. Aşağıdaki örnekte bu davranış gösterilmektedir:

[!code-csharp[copy of values](snippets/shared/ValueTypes.cs#ValueTypeCopied)]

Yukarıdaki örnekte gösterildiği gibi, bir değer türü değişkeni üzerindeki işlemler, değişkende depolanan yalnızca değer türü örneğini etkiler.

Değer türü bir başvuru türünün veri üyesini içeriyorsa, bir değer türü örneği kopyalandığında yalnızca başvuru türü örneğine başvuru kopyalanır. Hem Copy hem de orijinal değer türü örneğinin aynı başvuru türü örneğine erişimi vardır. Aşağıdaki örnekte bu davranış gösterilmektedir:

[!code-csharp[shallow copy](snippets/shared/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> Kodunuzu daha az hataya açık ve daha sağlam hale getirmek için, değişmez değer türlerini tanımlayın ve kullanın. Bu makale yalnızca gösterim amacıyla kesilebilir değer türlerini kullanır.

## <a name="kinds-of-value-types-and-type-constraints"></a>Değer türleri ve tür kısıtlamaları türleri

Değer türü aşağıdaki iki türden biri olabilir:

- veri ve ilgili işlevleri kapsülleyen bir [Yapı türü](struct.md)
- bir adlandırılmış sabitler kümesi tarafından tanımlanan ve bir seçimi veya seçenek bileşimini temsil eden bir [numaralandırma türü](enum.md)

[Null yapılabilir bir değer türü](nullable-value-types.md) , `T?` temel alınan değer türünün tüm değerlerini `T` ve ek bir [null](../keywords/null.md) değeri temsil eder. `null`Null atanabilir bir değer türü olmadığı takdirde, değer türünde bir değişkene atayamazsınız.

Bir tür parametresinin null yapılamayan bir değer türü olduğunu belirtmek için [ `struct` kısıtlamasını](../../programming-guide/generics/constraints-on-type-parameters.md) kullanabilirsiniz. Hem yapı hem de numaralandırma türleri `struct` kısıtlamayı karşılar. C# 7,3 ' den başlayarak, bir `System.Enum` tür parametresinin bir numaralandırma türü olduğunu belirtmek için bir temel sınıf kısıtlamasında ( [enum kısıtlaması](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)olarak bilinir) kullanabilirsiniz.

## <a name="built-in-value-types"></a>Yerleşik değer türleri

C# *basit türler* olarak da bilinen aşağıdaki yerleşik değer türlerini sağlar:

- [Tamsayı sayısal türler](integral-numeric-types.md)
- [Kayan nokta sayısal türleri](floating-point-numeric-types.md)
- Boole değeri temsil eden [bool](bool.md)
- Unicode UTF-16 karakterini temsil eden [karakter](char.md)

Tüm basit türler yapı türlerdir ve bazı ek işlemlere izin veren diğer yapı türlerinden farklıdır:

- Basit bir tür değeri sağlamak için sabit değerler kullanabilirsiniz. Örneğin, `'A'` türünün bir sabit değeri `char` ve `2001` türünün bir sabit değeri `int` .

- [Const](../keywords/const.md) anahtar sözcüğüyle basit türlerin sabitlerini bildirebilirsiniz. Diğer yapı türlerinde sabitler olması mümkün değildir.

- İşlenenleri basit türlerin tüm sabitleri olan sabit ifadeler, derleme zamanında değerlendirilir.

C# 7,0 ' den başlayarak, c# [değer tanımlama gruplarını](value-tuples.md)destekler. Değer tanımlama grubu bir değer türüdür, ancak basit bir tür değildir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Değer türleri](~/_csharplang/spec/types.md#value-types)
- [Basit türler](~/_csharplang/spec/types.md#simple-types)
- [Değişkenler](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [Başvuru türleri](../keywords/reference-types.md)
