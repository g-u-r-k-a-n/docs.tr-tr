---
description: Fixed ekstresi-C# başvurusu
title: Fixed ekstresi-C# başvurusu
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 2af9c4311e8326d6df933ec5d4c38354fe021e5c
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497573"
---
# <a name="fixed-statement-c-reference"></a>fixed Deyimi (C# Başvurusu)

`fixed`İfade, çöp toplayıcısının taşınabilir bir değişkenin yerini değiştirmesini engeller. `fixed`Deyime yalnızca [güvenli olmayan](unsafe.md) bir bağlamda izin verilir. `fixed` [Sabit boyutlu arabellekler](../unsafe-code.md#fixed-size-buffers)oluşturmak için anahtar sözcüğünü de kullanabilirsiniz.

`fixed`İfade, yönetilen bir değişkene bir işaretçi ayarlar ve deyimin yürütülmesi sırasında bu değişkene "PIN" koyar. Taşınabilir olarak yönetilen değişkenlere yönelik işaretçiler yalnızca bir bağlamda yararlıdır `fixed` . Bağlam olmadan `fixed` çöp toplama, değişkenleri tahmin edilmemiş şekilde yeniden konumlandırmaya yönelik olabilir. C# derleyicisi yalnızca bir ifadede yönetilen değişkene bir işaretçi atamanızı sağlar `fixed` .

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#1)]

Bir diziyi, dizeyi, sabit boyutlu arabelleği veya bir değişkenin adresini kullanarak bir işaretçiyi başlatabilirsiniz. Aşağıdaki örnek, değişken adreslerinin, dizilerin ve dizelerin kullanımını göstermektedir:

[!code-csharp[Initializing fixed size buffers](snippets/FixedKeywordExamples.cs#2)]

C# 7,3 ' den başlayarak, `fixed` ifade diziler, dizeler, sabit boyutlu arabellekler veya yönetilmeyen değişkenlerin ötesinde ek türler üzerinde çalışır. Adlı bir yöntemi uygulayan herhangi bir tür `GetPinnableReference` sabitlenebilir. , `GetPinnableReference` `ref` [Yönetilmeyen türde](../builtin-types/unmanaged-types.md)bir değişken döndürmelidir. .Net <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> Core 2,0 ' de sunulan .net türleri bu düzenin kullanımını ve sabitlenebilir. Bu, aşağıdaki örnekte gösterilmiştir:

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#FixedSpan)]

Bu modele katılması gereken türler oluşturuyorsanız, bu <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> düzenin uygulanması örneği için bkz..

Aynı türde olan birden çok işaretçi tek bir bildirimde başlatılabilir:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Farklı türlerin işaretçilerini başlatmak için `fixed` Aşağıdaki örnekte gösterildiği gibi deyimlerini iç içe geçirebilirsiniz.

[!code-csharp[Initializing multiple pointers](snippets/FixedKeywordExamples.cs#3)]

Deyimdeki kod yürütüldükten sonra, sabitlenmiş değişkenler sabitlenir ve çöp toplamaya tabidir. Bu nedenle, bu değişkenleri deyimin dışında işaret etmez `fixed` . Bildiriminde belirtilen değişkenler, `fixed` Bu ifadeye göre kapsamlandırılır ve daha kolay hale getirir:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

`fixed`Deyimlerde başlatılan işaretçiler salt okunur değişkenlerdir. İşaretçi değerini değiştirmek istiyorsanız, ikinci bir işaretçi değişkeni bildirmeniz ve bunu değiştirmeniz gerekir. İfadede belirtilen değişken `fixed` değiştirilemez:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Yığın üzerinde bellek ayırabilirsiniz, burada çöp toplamaya tabi değildir ve bu nedenle sabitlenmiş olması gerekmez. Bunu yapmak için bir [ `stackalloc` ifade](../operators/stackalloc.md)kullanın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [fixed deyimin](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [olmayabilecek](unsafe.md)
- [İşaretçi türleri](../unsafe-code.md#pointer-types)
- [Sabit boyutlu arabellekler](../unsafe-code.md#fixed-size-buffers)
