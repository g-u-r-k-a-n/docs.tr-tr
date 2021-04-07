---
description: "C 'deki yönetilmeyen türler hakkında bilgi edinin #"
title: Yönetilmeyen türler-C# başvurusu
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 13e8d4238a85201d46acabdf3103bdc7254ecfe8
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497404"
---
# <a name="unmanaged-types-c-reference"></a>Yönetilmeyen türler (C# Başvurusu)

Bir tür, aşağıdaki türlerden biri ise, **yönetilmeyen bir türdür** :

- `sbyte`,,, `byte` `short` `ushort` , `int` , `uint` , `long` , `ulong` , `char` , `float` , `double` , `decimal` , veya `bool`
- Herhangi bir [numaralandırma](enum.md) türü
- Herhangi bir [işaretçi](../unsafe-code.md#pointer-types) türü
- Yalnızca yönetilmeyen türlerin ve C# 7,3 ve önceki sürümlerde bulunan alanları içeren Kullanıcı tanımlı [Yapı](struct.md) türleri, oluşturulmuş bir tür değildir (en az bir tür bağımsız değişkeni içeren bir tür)

C# 7,3 ' den başlayarak, bir tür parametresinin işaretçi olmayan, null atanamaz yönetilmeyen bir tür olduğunu belirtmek için [ `unmanaged` kısıtlamasını](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) kullanabilirsiniz.

C# 8,0 ' den başlayarak, aşağıdaki örnekte gösterildiği gibi, yönetilmeyen türlerin alanlarını içeren *oluşturulmuş* bir yapı türü de yönetilmdir:

[!code-csharp[unmanaged constructed types](snippets/shared/UnmanagedTypes.cs#ProgramExample)]

Genel bir yapı, yönetilmeyen ve yönetilmeyen oluşturulmuş türlerin kaynağı olabilir. Yukarıdaki örnek, genel bir struct tanımlar `Coords<T>` ve yönetilmeyen oluşturulmuş türlerin örneklerini gösterir. Yönetilmeyen bir tür örneği `Coords<object>` . Yönetilmeyen değildir çünkü türünde alanları vardır `object` , yönetilmeyen değildir. Oluşturulan *Tüm* türlerin yönetilmeyen türler olmasını istiyorsanız, `unmanaged` genel bir yapının tanımında kısıtlamayı kullanın:

[!code-csharp[unmanaged constraint in type definition](snippets/shared/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [işaretçi türleri](~/_csharplang/spec/unsafe-code.md#pointer-types) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [İşaretçi türleri](../unsafe-code.md#pointer-types)
- [Bellek ve aralıkla ilgili türler](../../../standard/memory-and-spans/index.md)
- [sizeof işleci](../operators/sizeof.md)
- [stackalloc](../operators/stackalloc.md)
