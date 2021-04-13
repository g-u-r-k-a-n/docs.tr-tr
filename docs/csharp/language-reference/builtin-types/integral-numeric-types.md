---
title: Integral sayısal türleri-C# başvurusu
description: İntegral sayısal türlerin her biri için aralığı, depolama boyutunu ve kullanımları öğrenin.
ms.date: 04/10/2021
f1_keywords:
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- short_CSharpKeyword
- ushort_CSharpKeyword
- int_CSharpKeyword
- uint_CSharpKeyword
- long_CSharpKeyword
- ulong_CSharpKeyword
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 21e6595e477fd48d0e5f39f5b4f1f7c5893a8840
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369588"
---
# <a name="integral-numeric-types--c-reference"></a>Integral sayısal türleri (C# Başvurusu)

*İntegral sayısal türleri* tamsayı sayılarını temsil eder. Tüm integral sayısal türleri [değer türlerdir](value-types.md). Bunlar ayrıca [basit türlerdir](value-types.md#built-in-value-types) ve [değişmez değerler](#integer-literals)ile başlatılabilir. Tüm integral sayısal türler [Aritmetik](../operators/arithmetic-operators.md), [bit düzeyinde mantıksal](../operators/bitwise-and-shift-operators.md), [karşılaştırma](../operators/comparison-operators.md)ve [eşitlik](../operators/equality-operators.md) işleçlerini destekler.

## <a name="characteristics-of-the-integral-types"></a>İntegral türlerinin özellikleri

C# aşağıdaki önceden tanımlanmış integral türlerini destekler:

|C# türü/anahtar sözcüğü|Aralık|Boyut|.NET türü|
|----------|-----------|----------|-------------|
|`sbyte`|-128-127|İmzalanan 8 bit tamsayı|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0-255|İşaretsiz 8 bit tamsayı|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32.768-32.767|İmzalanan 16 bit tamsayı|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0-65.535|İşaretsiz 16 bit tamsayı|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2.147.483.648-2.147.483.647|İmzalanan 32 bit tamsayı|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|0-4.294.967.295|İşaretsiz 32 bit tamsayı|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9223372036854775808-9.223.372.036.854.775.807|İmzalanan 64 bit tamsayı|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|0-18446744073709551615|İşaretsiz 64 bit tamsayı|<xref:System.UInt64?displayProperty=nameWithType>|
|`nint`|Platforma bağlıdır|İmzalanan 32 bit veya 64 bit tamsayı|<xref:System.IntPtr?displayProperty=nameWithType>|
|`nuint`|Platforma bağlıdır|İşaretsiz 32 bit veya 64 bit tamsayı|<xref:System.UIntPtr?displayProperty=nameWithType>|

Son iki hariç tüm tablo satırlarında, en soldaki sütundan her bir C# Type anahtar sözcüğü karşılık gelen .NET türü için bir diğer addır. Anahtar sözcüğü ve .NET tür adı, değiştirilebilir. Örneğin, aşağıdaki bildirimler aynı türdeki değişkenleri bildirir:

```csharp
int a = 123;
System.Int32 b = 123;
```

`nint` `nuint` Tablonun son iki satırı içindeki ve türleri yerel boyutlu tamsayılardır. Bunlar, belirtilen .NET türleri tarafından dahili olarak temsil edilir, ancak her durumda anahtar sözcüğü ve .NET türü birbirini değiştirmez. Derleyici, `nint` ve için ve `nuint` işaretçi türleri için sağlamayan tamsayı türleri olarak işlemler ve dönüştürmeler sağlar `System.IntPtr` `System.UIntPtr` . Daha fazla bilgi için bkz. [ `nint` ve `nuint` türleri](nint-nuint.md).

Her integral türünün varsayılan değeri sıfırdır `0` . Yerel ölçekli türler hariç tüm integral türlerin her biri, `MinValue` `MaxValue` Bu türün en düşük ve en büyük değerini sağlayan sabitler içerir.

<xref:System.Numerics.BigInteger?displayProperty=nameWithType>Üst veya alt sınır olmadan işaretli bir tamsayıyı temsil etmek için yapıyı kullanın.

## <a name="integer-literals"></a>Tamsayı sabit değerleri

Tamsayı sabit değerleri

- *Decimal*: herhangi bir ön ek olmadan
- *onaltılı*: `0x` veya `0X` öneki
- *ikili*: `0b` veya `0B` önekiyle (C# 7,0 ve üzeri sürümlerde kullanılabilir)

Aşağıdaki kod, her birine bir örnek gösterir:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

Yukarıdaki örnek ayrıca `_` C# 7,0 ile başlayarak desteklenen bir *rakam ayırıcısı* olarak kullanımını gösterir. Rakam ayırıcısını her türlü sayısal sabit değer ile kullanabilirsiniz.

Bir tamsayı sabit değerinin türü, soneki tarafından aşağıdaki şekilde belirlenir:

- Değişmez değerin son eki yoksa, türü, değeri gösterilebileceği aşağıdaki türlerin birincsahiptir: `int` , `uint` , `long` , `ulong` .

  > [!NOTE]
  > Değişmez değerler pozitif değer olarak yorumlanır. Örneğin, değişmez değer `0xFF_FF_FF_FF` `4294967295` türün numarası `uint` ile aynı bit gösterimine sahip olsa da, tür sayısını temsil eder `-1` `int` . Belirli türde bir değere ihtiyacınız varsa, bu türe bir sabit değer atayın. `unchecked`Bir sabit değer hedef türünde temsil edilenemez işlecini kullanın. Örneğin, `unchecked((int)0xFF_FF_FF_FF)` üretir `-1` .

- Sabit değer veya tarafından sonekli ise `U` `u` , türü, değeri gösterilebileceği aşağıdaki türlerin birincsahiptir: `uint` , `ulong` .
- Sabit değer veya tarafından sonekli ise `L` `l` , türü, değeri gösterilebileceği aşağıdaki türlerin birincsahiptir: `long` , `ulong` .

  > [!NOTE]
  > Küçük harfli harfi `l` sonek olarak kullanabilirsiniz. Ancak, bu bir derleyici uyarısı oluşturur, çünkü harf `l` rakamla karışıyor olabilir `1` . `L`Açıklık için kullanın.

- Sabit değer,,,,,, veya ile sonsabitidir, `UL` `Ul` `uL` `ul` `LU` `Lu` `lU` `lu` türü `ulong` .

Bir tamsayı değişmez değeri ile temsil edilen değer aşarsa <xref:System.UInt64.MaxValue?displayProperty=nameWithType> , bir derleyici hatası [CS1021](../../misc/cs1021.md) oluşur.

Bir tamsayı sabit değerinin belirlenen türü ise `int` ve değişmez değer tarafından temsil edilen değer hedef türün aralığı içindeyse, değer örtük olarak,,,,, veya olarak dönüştürülebilir `sbyte` `byte` `short` `ushort` `uint` `ulong` `nint` `nuint` :

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Yukarıdaki örnekte gösterildiği gibi, değişmez değerin değeri hedef türü Aralık içinde değilse, bir derleyici hatası [CS0031](../../misc/cs0031.md) oluşur.

Ayrıca, bir tamsayı değişmez değeri ile temsil edilen değeri, değişmez değer türü dışında bir türe dönüştürmek için bir cast da kullanabilirsiniz:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Dönüşümler

Herhangi bir integral sayısal türü diğer tüm integral sayısal türlerine dönüştürebilirsiniz. Hedef türü kaynak türünün tüm değerlerini depolayabiliyorsanız, dönüştürme örtük olur. Aksi takdirde, açık bir dönüştürme gerçekleştirmek için bir [atama ifadesi](../operators/type-testing-and-cast.md#cast-expression) kullanmanız gerekir. Daha fazla bilgi için bkz. [yerleşik sayısal dönüştürmeler](numeric-conversions.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Integral türleri](~/_csharplang/spec/types.md#integral-types)
- [Tamsayı sabit değerleri](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Değer türleri](value-types.md)
- [Kayan nokta türleri](floating-point-numeric-types.md)
- [Standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
- [.NET Sayısal Değerleri](../../../standard/numerics.md)
