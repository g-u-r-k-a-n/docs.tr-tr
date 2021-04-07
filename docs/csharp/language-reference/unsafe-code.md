---
title: Güvenli olmayan kod, veri işaretçileri ve işlev işaretçileri
description: Güvenli olmayan kod, işaretçiler ve işlev işaretçileri hakkında bilgi edinin. C#, bellek veya işlev işaretçilerini doğrudan işlemek üzere bu özellikleri kullanmak için güvenli olmayan bir bağlam bildirmeniz gerekir.
ms.date: 04/01/2021
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 9c55fc48b5805ba38dcf289cb5e03626cf3e96ec
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106499130"
---
# <a name="unsafe-code-and-pointer-types"></a>Güvenli olmayan kod ve işaretçi türleri

Yazdığınız C# kodunun çoğu "verifili güvenli kod" dir. *Doğruıda güvenli kod* .NET araçları 'nın kodun güvenli olduğunu doğrulayabileceği anlamına gelir. Genel olarak, güvenli kod işaretçiler kullanılarak belleğe doğrudan erişemez. Ayrıca ham bellek ayırmaz. Bunun yerine yönetilen nesneler oluşturur.

C# [`unsafe`](keywords/unsafe.md) , içinde *doğrulanamayan* kod yazabileceğiniz bir bağlamı destekler. Bir `unsafe` bağlamda, kod işaretçiler kullanabilir, bellek ayırır ve serbest bellek blokları kullanabilir ve işlev işaretçileri kullanarak yöntemleri çağırabilir. C# ' deki güvenli olmayan kod, tehlikeli değildir; yalnızca güvenliği doğrulanamayan bir koddur.

Güvenli olmayan kod aşağıdaki özelliklere sahiptir:

- Yöntemler, türler ve kod blokları güvenli olmayan şekilde tanımlanabilir.
- Bazı durumlarda, güvenli olmayan kod, dizi sınırları denetimlerini kaldırarak bir uygulamanın performansını artırabilir.
- İşaretçi gerektiren yerel işlevleri çağırdığınızda güvenli olmayan kod gereklidir.
- Güvenli olmayan kod kullanmak güvenlik ve kararlılık riskleri sağlar.
- Güvenli olmayan bloklar içeren kodun [**AllowUnsafeBlocks**](compiler-options/language.md#allowunsafeblocks) derleyici seçeneğiyle derlenmesi gerekir.

## <a name="pointer-types"></a>İşaretçi türleri

Güvenli olmayan bir bağlamda, bir tür, bir değer türüne ek olarak bir işaretçi türü veya bir başvuru türü olabilir. Bir işaretçi türü bildirimi, aşağıdaki biçimlerden birini alır:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

`*`Bir işaretçi türündeki öğesinden önce belirtilen tür, **başvurulan tür** olarak adlandırılır. Yalnızca [yönetilmeyen bir tür](builtin-types/unmanaged-types.md) , başvurulan bir tür olabilir.

İşaretçi türleri [nesneden](builtin-types/reference-types.md) aktarılmaz ve işaretçi türleri ve arasında dönüştürme yok `object` . Ayrıca, kutulama ve kutudan çıkarma işaretçileri desteklemez. Ancak, farklı işaretçi türleri ve işaretçi türleri ve tamsayı türleri arasında dönüştürme yapabilirsiniz.

Aynı bildirimde birden çok işaretçi bildirdiğinizde, yıldız işaretini ( `*` ) yalnızca temel alınan türle birlikte yazarsınız. Her işaretçi adının öneki olarak kullanılmaz. Örnek:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Bir işaretçi, bir işaretçiye işaret eden bir nesne başvurusu atık olarak toplanabileceğinden, bir başvuruya veya başvuru içeren bir [yapıya](builtin-types/struct.md) işaret edebilir. Çöp toplayıcı, bir nesnenin herhangi bir işaretçi türü tarafından işaret edilip edilmeyeceğini izlememez.

Türündeki işaretçi değişkeninin değeri, `MyType*` türünde bir değişkenin adresidir `MyType` . Aşağıda, işaretçi türü bildirimi örnekleri verilmiştir:

- `int* p`: `p` tamsayı olan bir işaretçidir.
- `int** p`: bir `p` tamsayı işaretçisinin işaretçisi.
- `int*[] p`: `p` tamsayılara yönelik işaretçilerin tek boyutlu bir dizisidir.
- `char* p`: bir `p` char işaretçisi.
- `void* p`: `p` bilinmeyen bir tür işaretçisi.

İşaretçi yöneltme işleci, `*` işaretçi değişkeni tarafından işaret edilen konumdaki içeriğe erişmek için kullanılabilir. Örneğin, aşağıdaki bildirimi ele alalım:

```csharp
int* myVariable;
```

İfade, `*myVariable` içinde bulunan `int` adreste bulunan değişkeni gösterir `myVariable` .

[ `fixed` Deyimdeki](keywords/fixed-statement.md)makalelerde birçok işaretçiyle ilgili birkaç örnek vardır. Aşağıdaki örnek, `unsafe` anahtar sözcüğünü ve ifadesini kullanır `fixed` ve iç işaretçinin nasıl artırılacağını gösterir.  Bu kodu çalıştırmak için bir konsolun Ana işlevine yapıştırabilirsiniz. Bu örneklerin [**AllowUnsafeBlocks**](compiler-options/language.md#allowunsafeblocks) derleyici seçenek kümesiyle derlenmesi gerekir.

:::code language="csharp" source="snippets/unsafe-code/FixedKeywordExamples.cs" ID="5":::

Yöneltme işlecini türündeki bir işaretçiye uygulayamazsınız `void*` . Ancak, boş bir işaretçiyi başka herhangi bir türü dönüştürmek veya bunun tersini yapmak için bir yayın kullanabilirsiniz.

Bir işaretçi olabilir `null` . Yönlendirme işlecini bir null işaretçiye uygulamak, uygulama tarafından tanımlanan bir davranışa neden olur.

Yöntemler arasında işaretçiler geçirmek tanımsız davranışlara neden olabilir. Bir `in` , `out` veya `ref` parametresi ya da işlev sonucu olarak yerel bir değişkene bir işaretçi döndüren bir yöntem düşünün. İşaretçi sabit bir blokta ayarlandıysa, işaret ettiği değişken artık sabit olamaz.

Aşağıdaki tabloda, güvenli olmayan bir bağlamda işaretçiler üzerinde işlem yapabilecek işleçler ve deyimler listelenmektedir:

|İşleç/Deyim|Kullanın|
|-------------------------|---------|
|`*`|İşaretçi yöneltmesi gerçekleştirir.|
|`->`|Bir yapının bir üyesine bir işaretçi yoluyla erişir.|
|`[]`|Bir işaretçiyi dizine ekler.|
|`&`|Bir değişkenin adresini alır.|
|`++` ve `--`|İşaretçileri artırır ve azaltır.|
|`+` ve `-`|İşaretçi aritmetiği gerçekleştirir.|
|`==`, `!=` , `<` , `>` , `<=` ve `>=`|İşaretçileri karşılaştırır.|
|[`stackalloc`](operators/stackalloc.md)|Yığında bellek ayırır.|
|[`fixed` Ekstre](keywords/fixed-statement.md)|Adresinin bulunamaması için bir değişkeni geçici olarak sabitler.|

İşaretçiyle ilgili işleçler hakkında daha fazla bilgi için bkz. [işaretçi ile ilgili işleçler](operators/pointer-related-operators.md).

Herhangi bir işaretçi türü örtük olarak bir türe dönüştürülebilir `void*` . Herhangi bir işaretçi türüne değer atanabilir `null` . Herhangi bir işaretçi türü, açıkça atama ifadesi kullanan başka bir işaretçi türüne dönüştürülebilir. Ayrıca, herhangi bir integral türünü bir işaretçi türüne veya herhangi bir işaretçi türüne bir integral türüne dönüştürebilirsiniz. Bu dönüşümler açık bir tür dönüştürme gerektirir.

Aşağıdaki örnek bir öğesine dönüştürür `int*` `byte*` . İşaretçinin, değişkenin en düşük adresli baytını işaret ettiğini unutmayın. Sonucu büyük ölçüde arttırdığınızda `int` (4 bayt), değişkenin kalan baytlarını görüntüleyebilirsiniz.

:::code language="csharp" source="snippets/unsafe-code/Conversions.cs" ID="Conversion":::

## <a name="fixed-size-buffers"></a>Sabit boyutlu arabellekler

C# ' de, bir veri yapısında sabit boyutlu bir diziye sahip bir arabellek oluşturmak için [fixed](keywords/fixed-statement.md) ifadesini kullanabilirsiniz. Sabit boyutlu arabellekler, diğer dillerdeki veya platformlardaki veri kaynaklarıyla birlikte çalışan Yöntemler yazdığınızda faydalıdır. Sabit dizi, normal yapı üyeleri için izin verilen herhangi bir özniteliği veya değiştiricilerini alabilir. Tek kısıtlama, dizi türünün,,,,,,,, `bool` `byte` `char` `short` `int` `long` `sbyte` `ushort` `uint` , `ulong` ,, `float` veya `double` olması olabilir.

```csharp
private fixed char name[30];
```

Güvenli kodda, dizi içeren bir C# yapısı dizi öğelerini içermez. Struct, bunun yerine öğelerine bir başvuru içerir. Bir yapıda sabit boyutlu bir diziyi, [güvenli olmayan](keywords/unsafe.md) bir kod bloğunda kullanıldığında bir [yapıya](builtin-types/struct.md) katıştırabilirsiniz.

Aşağıdaki boyut, `struct` bir başvuru olduğundan dizideki öğelerin sayısına bağlı değildir `pathName` :

:::code language="csharp" source="snippets/unsafe-code/FixedKeywordExamples.cs" ID="6":::

`struct`, Güvenli olmayan kodda gömülü bir dizi içerebilir. Aşağıdaki örnekte, `fixedBuffer` dizisinin sabit bir boyutu vardır. `fixed`İlk öğe için bir işaretçi oluşturmak üzere bir ifade kullanırsınız. Bu işaretçi aracılığıyla dizinin öğelerine erişirsiniz. `fixed`İfade, `fixedBuffer` örnek alanını bellekte belirli bir konuma sabitsabitler.

:::code language="csharp" source="snippets/unsafe-code/FixedKeywordExamples.cs" ID="7":::

128 öğe `char` dizisinin boyutu 256 bayttır. Sabit boyutlu [char](builtin-types/char.md) arabellekleri, kodlamadan bağımsız olarak her zaman karakter başına 2 bayt sürer. Bu dizi boyutu, karakter arabelleklerinin API yöntemlerine veya ya da yapı birimleri için sıralanmasına karşın aynı olur `CharSet = CharSet.Auto` `CharSet = CharSet.Ansi` . Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.

Yukarıdaki örnekte `fixed` , C# 7,3 ile başlayarak kullanılabilir olan sabitleme olmadan alanlara erişme gösterilmektedir.

Diğer bir yaygın sabit boyutlu dizi [bool](builtin-types/bool.md) dizidir. Bir `bool` dizideki öğeler her zaman boyutu 1 bayttır. `bool` diziler, bit dizileri veya arabellekleri oluşturmak için uygun değildir.

Sabit boyutlu arabellekler ile derlenir ve <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType> Bu, ortak dil çalışma zamanına (CLR) bir türün, bulunabilecek bir yönetilmeyen dizi içerdiğini söyler. [Stackalloc](operators/stackalloc.md) kullanılarak ayrılan bellek Ayrıca clr 'de arabellek taşması algılama özelliklerini otomatik olarak sunar. Önceki örnekte, bir sabit boyut arabelleğinin bir içinde nasıl yer aldığı gösterilmektedir `unsafe struct` .

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

Için derleyici tarafından oluşturulan C# `Buffer` aşağıdaki gibidir:

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

Sabit boyutlu arabellekler aşağıdaki yollarla normal dizilerden farklıdır:

- Yalnızca bir `unsafe` bağlamda kullanılabilir.
- Yalnızca yapıların örnek alanları olabilir.
- Bunlar her zaman vektörleridir veya tek boyutlu dizilerdir.
- Bildirimin uzunluğu içermesi gerekir, örneğin `fixed char id[8]` . Kullanamazsınız `fixed char id[]` .

## <a name="how-to-use-pointers-to-copy-an-array-of-bytes"></a>Bayt dizisine kopyalamak için işaretçileri kullanma

Aşağıdaki örnek, baytları bir diziden diğerine kopyalamak için işaretçileri kullanır.

Bu örnek, yönteminde işaretçiler kullanmanıza olanak tanıyan [unsafe](keywords/unsafe.md) anahtar sözcüğünü kullanır `Copy` . [Fixed](keywords/fixed-statement.md) deyimleri, kaynak ve hedef dizilere işaretçiler bildirmek için kullanılır. `fixed`İfade, kaynak ve hedef dizilerinin konumunu çöp toplama tarafından taşınmayacak şekilde *sabitler* . Blok tamamlandığında diziler için bellek blokları `fixed` sabitlenemez. `Copy`Bu örnekteki yöntem `unsafe` anahtar sözcüğünü kullandığından, [**AllowUnsafeBlocks**](compiler-options/language.md#allowunsafeblocks) derleyici seçeneğiyle derlenmesi gerekir.

Bu örnek, ikinci bir yönetilmeyen işaretçi yerine dizinler kullanılarak her iki dizinin öğelerine erişir. `pSource`Ve `pTarget` işaretçilerinin bildirimi dizileri sabitler. Bu özellik C# 7,3 ile başlayarak kullanılabilir.

:::code language="csharp" source="snippets/unsafe-code/FixedKeywordExamples.cs" ID="8":::

## <a name="function-pointers"></a>İşlev işaretçileri

C#, [`delegate`](builtin-types/reference-types.md#the-delegate-type) güvenli işlev işaretçisi nesneleri tanımlamak için türler sağlar. Bir temsilciyi çağırmak, öğesinden türetilmiş bir türün örneklenmesini <xref:System.Delegate?displayProperty=nameWithType> ve yöntemine bir sanal yöntem çağrısını yapmayı içerir `Invoke` . Bu sanal çağrı `callvirt` Il yönergesini kullanır. Performans açısından kritik kod yollarında `calli` Il yönergesini kullanmak daha etkilidir.

Sözdizimini kullanarak bir işlev işaretçisi tanımlayabilirsiniz `delegate*` . Derleyici, `calli` bir nesneyi başlatmak ve çağırmak yerine yönergeyi kullanarak işlevi çağırır `delegate` `Invoke` . Aşağıdaki kod `delegate` `delegate*` , aynı türde iki nesneyi birleştirmek için bir veya kullanan iki yöntem bildirir. İlk yöntem bir <xref:System.Func%603?displayProperty=nameWithType> temsilci türü kullanır. İkinci yöntem `delegate*` aynı parametrelere ve dönüş türüne sahip bir bildirim kullanır:

:::code language="csharp" source="snippets/unsafe-code/FunctionPointers.cs" ID="UseDelegateOrPointer":::

Aşağıdaki kod, statik bir yerel işlevi nasıl bildirebileceğinizi ve `UnsafeCombine` Bu yerel işleve yönelik bir işaretçi kullanarak yöntemi çağırmayı gösterir:

:::code language="csharp" source="snippets/unsafe-code/FunctionPointers.cs" ID="InvokeViaFunctionPointer":::

Yukarıdaki kod, işlev işaretçisi olarak erişilen işlev üzerindeki kuralların birkaçını gösterir:

- İşlev işaretçileri, yalnızca bir `unsafe` bağlamda bildirilemez.
- `delegate*`(Veya döndüren `delegate*` ) Yöntemler, yalnızca bir `unsafe` bağlamda çağrılabilir.
- `&`Bir işlevin adresini elde etmek için olan işlece yalnızca işlevlerde izin verilir `static` . (Bu kural hem üye işlevleri hem de yerel işlevler için geçerlidir).

Sözdizimi, `delegate` türleri bildirme ve işaretçiler kullanma ile paraleller içeriyor. `*`Üzerindeki sonek, `delegate` bildirimin bir *işlev işaretçisi* olduğunu gösterir. Bir `&` işlev işaretçisine bir yöntem grubu atanırken işlemin, yöntemin adresini aldığını belirtir.

`delegate*`Anahtar sözcüklerini ve kullanarak bir için çağırma kuralı belirtebilirsiniz `managed` `unmanaged` . Ayrıca, `unmanaged` işlev işaretçileri için, çağırma kuralını belirtebilirsiniz. Aşağıdaki bildirimlerde her birinin örnekleri gösterilmektedir. İlk bildirim, `managed` varsayılan olan çağırma kuralını kullanır. Sonraki üç `unmanaged` çağrı kuralını kullanır. Her biri ECMA 335 çağırma kurallarından birini belirtir: `Cdecl` , `Stdcall` , `Fastcall` veya `Thiscall` . Son bildirimler, `unmanaged` platform için varsayılan çağırma kuralını seçmek üzere clr 'yi, çağıran kuralını kullanır. CLR, çalışma zamanında çağrı kuralını seçer.

:::code language="csharp" source="snippets/unsafe-code/FunctionPointers.cs" ID="UnmanagedFunctionPointers":::

C# 9,0 için [işlev işaretçisi](~/_csharplang/proposals/csharp-9.0/function-pointers.md) teklifinde işlev işaretçileri hakkında daha fazla bilgi edinebilirsiniz.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [güvenli olmayan kod](~/_csharplang/spec/unsafe-code.md) bölümüne bakın.
