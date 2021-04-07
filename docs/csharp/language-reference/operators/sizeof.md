---
description: sizeof işleci-C# başvurusu
title: sizeof işleci-C# başvurusu
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 6685cdb4fba2460ee4a47b004aa6911ab76235a4
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497378"
---
# <a name="sizeof-operator-c-reference"></a>sizeof işleci (C# Başvurusu)

`sizeof`İşleci, verilen türdeki bir değişken tarafından bulunan bayt sayısını döndürür. İşlecin bağımsız değişkeni, yönetilmeyen bir `sizeof` [türün](../builtin-types/unmanaged-types.md) veya yönetilmeyen tür olarak [Kısıtlanmış](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) bir tür parametresinin adı olmalıdır.

`sizeof`Operatör [güvenli olmayan](../keywords/unsafe.md) bir bağlam gerektiriyor. Ancak, aşağıdaki tabloda sunulan ifadeler derleme zamanında karşılık gelen sabit değerlere değerlendirilir ve güvenli olmayan bir bağlam gerektirmez:

|Expression|Sabit değer|
|---------|---------------|
|`sizeof(sbyte)`|1|
|`sizeof(byte)`|1|
|`sizeof(short)`|2|
|`sizeof(ushort)`|2|
|`sizeof(int)`|4|
|`sizeof(uint)`|4|
|`sizeof(long)`|8|
|`sizeof(ulong)`|8|
|`sizeof(char)`|2|
|`sizeof(float)`|4|
|`sizeof(double)`|8|
|`sizeof(decimal)`|16|
|`sizeof(bool)`|1|

Ayrıca, `sizeof` işlecin işleneni bir [sabit](../builtin-types/enum.md) listesi türünün adı olduğunda güvenli olmayan bir bağlam kullanmanıza gerek kalmaz.

Aşağıdaki örnek işlecinin kullanımını gösterir `sizeof` :

[!code-csharp[sizeof examples](snippets/shared/SizeOfOperator.cs)]

`sizeof`İşleci, yönetilen bellekte ortak dil çalışma zamanı tarafından ayrılacak bayt sayısını döndürür. [Yapı](../builtin-types/struct.md) türleri için bu değer, yukarıdaki örnekte gösterildiği gibi herhangi bir doldurma içerir. İşlecinin sonucu, `sizeof` <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> *yönetilmeyen* bellekteki bir türün boyutunu döndüren yönteminin sonuçlarından farklılık gösterebilir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sizeof işleci](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [İşaretçi bağlantılı işleçler](pointer-related-operators.md)
- [İşaretçi türleri](../unsafe-code.md#pointer-types)
- [Bellek ve aralıkla ilgili türler](../../../standard/memory-and-spans/index.md)
- [.NET içindeki Genel Türler](../../../standard/generics/index.md)
