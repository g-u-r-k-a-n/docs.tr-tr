---
description: 'Daha fazla bilgi edinin: ULong veri türü (Visual Basic)'
title: ULong Veri Türü
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 5e47fc49e8e0a6df4d1fcc70174a8519752fd3e1
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104828"
---
# <a name="ulong-data-type-visual-basic"></a>ULong veri türü (Visual Basic)

0 ila 18446744073709551615 (1,84 ' den fazla 10 ^ 19 ' den fazla) değeri değişen işaretsiz 64 bitlik (8 baytlık) tamsayıları barındırır.

## <a name="remarks"></a>Açıklamalar

`ULong`Veri türünü, için çok büyük olan ikili verileri `UInteger` veya en büyük olası işaretsiz tamsayı değerlerini içerecek şekilde kullanın.

Varsayılan değeri 0 ' `ULong` dır.

## <a name="literal-assignments"></a>Değişmez değer atamaları

Bir `ULong` değişkeni bir ondalık değişmez değer, bir onaltılı sabit değer, sekizlik bir sabit değer veya (Visual Basic 2017 ' den başlayarak) ikili bir değişmez değer atayarak başlatabilir ve başlatabilirsiniz. Tamsayı sabit değeri aralığın dışındaysa `ULong` (diğer bir deyişle, değerinden küçükse <xref:System.UInt64.MinValue?displayProperty=nameWithType> veya ondan büyükse <xref:System.UInt64.MaxValue?displayProperty=nameWithType> , bir derleme hatası oluşur.

Aşağıdaki örnekte, ondalık, onaltılık ve ikili sabit değerler olarak temsil edilen 7.934.076.125 'e eşit tamsayılar `ULong` değerlere atanır.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> Ön eki veya bir `&h` `&H` onaltılık sabit değeri, öneki `&b` veya `&B` bir ikili sabit değer belirtmek için ön eki veya bir `&o` `&O` sekizlik sabit değeri göstermek için kullanın. Ondalık değişmez değerlerinin ön eki yok.

Visual Basic 2017 ' den başlayarak, `_` Aşağıdaki örnekte gösterildiği gibi, okunabilirliği geliştirmek için alt çizgi karakterini bir rakam ayırıcısı olarak da kullanabilirsiniz.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz. Örnek:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Sayısal değişmez değerler, `UL` `ul` Aşağıdaki örnekte gösterildiği gibi, veri türünü belirtmek için de veya [tür karakterini](../../programming-guide/language-features/data-types/type-characters.md) içerebilir `ULong` .

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Programlama ipuçları

- **Negatif sayılar.** `ULong`İşaretsiz bir tür olduğundan, negatif bir sayıyı temsil edemez. `-`Türü değerlendirilen bir ifadede birli eksi () işlecini kullanırsanız `ULong` , Visual Basic ifadeyi `Decimal` önce dönüştürür.

- **CLS uyumluluğu.** `ULong`Veri türü [ortak dil belirtiminin](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod onu kullanan bir bileşeni tüketmez.

- **Birlikte çalışma konuları.** Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimsiz değilseniz, gibi türlerin `ulong` diğer ortamlarda farklı bir veri genişliğine (32 bit) sahip olabileceğini aklınızda bulundurun. Böyle bir bileşene 32 bitlik bir bağımsız değişken geçiriyorsa, bunu `UInteger` `ULong` yönetilen Visual Basic kodunuzda değil olarak bildirin.

  Ayrıca, Otomasyon Windows 95, Windows 98, Windows ME veya Windows 2000 üzerinde 64 bit tamsayıları desteklemez. `ULong`Bu platformlarda bir Otomasyon bileşenine Visual Basic bağımsız değişken geçiremezsiniz.

- **Kan.** `ULong`, Ve için widens veri `Decimal` türü `Single` `Double` . Bu, `ULong` bir hatayla karşılaşmadan bu türlerden birine dönüştürebileceğiniz anlamına gelir <xref:System.OverflowException?displayProperty=nameWithType> .

- **Tür karakterleri.** Değişmez değer türü karakterlerinin `UL` bir sabit değere eklenmesi, `ULong` veri türüne zorlar. `ULong` tanımlayıcı türü karakteri yok.

- **Çerçeve türü.** .NET Framework karşılık gelen tür <xref:System.UInt64?displayProperty=nameWithType> yapısıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.UInt64>
- [Veri türleri](index.md)
- [Tür Dönüştürme İşlevleri](../functions/type-conversion-functions.md)
- [Dönüştürme Özeti](../keywords/conversion-summary.md)
- [Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Veri Türlerinin Etkili Kullanımı](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
