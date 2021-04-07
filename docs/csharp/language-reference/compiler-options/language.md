---
description: Dil özelliği kuralları için C# derleyici seçenekleri. Bu seçenekler derleyicinin belirli dil yapılarını nasıl yorumlayacağını denetler.
title: C# derleyici seçenekleri-dil özelliği kuralları
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- CheckForOverflowUnderflow compiler option [C#]
- AllowUnsafeBlocks compiler option [C#]
- DefineConstants compiler option [C#]
- LangVersion compiler option [C#]
- Nullable compiler option [C#]
ms.openlocfilehash: a7767d548e41e054006fb53cad47e8ab1f14b21b
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496715"
---
# <a name="c-compiler-options-for-language-feature-rules"></a>Dil özelliği kuralları için C# derleyici seçenekleri

Aşağıdaki seçenekler derleyicinin dil özelliklerini nasıl yorumlayacağını denetler. Yeni MSBuild sözdizimi **kalın** olarak gösterilir. Eski *csc.exe* sözdizimi içinde gösterilir `code style` .

- **Checkforoverflowyetersizliği**  /  `-checked` : taşma denetimleri oluştur.
- **AllowUnsafeBlocks**  /  `-unsafe` : ' unsafe ' koda izin ver.
- **Definesabitleri**  /  `-define` : koşullu derleme sembolleri tanımlayın.
- **Langversion**  /  `-langversion` : `default` (en son ana sürüm) veya `latest` (ikincil sürümler dahil en son sürüm) gibi dil sürümünü belirtin.
- **Null yapılabilir**  /  `-nullable` : Nullable bağlamı veya null yapılabilir uyarıları etkinleştirin.

## <a name="checkforoverflowunderflow"></a>Checkforoverflowyetersiz

**Checkforoverflowyetersizliği** seçeneği, veri türü aralığının dışında bir değer ile sonuçlanan bir tamsayı aritmetik ifadesinin çalışma zamanı özel durumuna neden olup olmadığını belirtir.  

```xml
<CheckForOverflowUnderflow>true</CheckForOverflowUnderflow>
```

Or anahtar sözcüğünün kapsamındaki tamsayı aritmetik bir ifade, `checked` `unchecked` **Checkforoverflowyetersizliği** seçeneğinin etkisine tabi değildir. Or anahtar sözcüğünün kapsamında olmayan bir tamsayı aritmetik ifade, `checked` `unchecked` veri türü aralığı dışında bir değer ile sonuçlanır ve **Denetim** `true` açısında olduğunda, bu ifade çalışma zamanında bir özel duruma neden olur. **Checkforoverflowyetersizliği** varsa `false` , bu ifade çalışma zamanında bir özel duruma neden olmaz. Bu seçenek için varsayılan değer `false` ; taşma denetimi devre dışı bırakıldı.

## <a name="allowunsafeblocks"></a>AllowUnsafeBlocks

**AllowUnsafeBlocks** derleyici seçeneği derlemek için [unsafe](../keywords/unsafe.md) anahtar sözcüğünü kullanan koda izin verir. Bu seçenek için varsayılan değer, `false` güvenli olmayan koda izin verilmiyor anlamına gelir.

```xml
<AllowUnsafeBlocks>true</AllowUnsafeBlocks>
```

Güvenli olmayan kod hakkında daha fazla bilgi için bkz. [güvenli olmayan kod ve işaretçiler](../unsafe-code.md).

## <a name="defineconstants"></a>Definesabitleri

**Definesabitleri** seçeneği, programınızın tüm kaynak kod dosyalarındaki sembolleri tanımlar.

```xml
<DefineConstants>name;name2</DefineConstants>
```

Bu seçenek, tanımlamak istediğiniz bir veya daha fazla simgenin adlarını belirtir. **Definesabitleri** seçeneği, derleme seçeneğinin projedeki tüm dosyalar için geçerli olması dışında [#define](../preprocessor-directives.md#defining-symbols) Önişlemci yönergesiyle aynı etkiye sahiptir. Kaynak dosyadaki bir [#undef](../preprocessor-directives.md#defining-symbols) yönergesi tanımı kaldırana kadar bir sembol kaynak dosyasında tanımlı kalır. `-define`Seçeneğini kullandığınızda, `#undef` bir dosyadaki bir yönergenin projedeki diğer kaynak kodu dosyaları üzerinde hiçbir etkisi olmaz. Kaynak dosyaları koşullu olarak derlemek için bu seçenek tarafından oluşturulan sembolleri [#if](../preprocessor-directives.md#conditional-compilation), [#else](../preprocessor-directives.md), [#elif](../preprocessor-directives.md#conditional-compilation)ve [#endif](../preprocessor-directives.md#conditional-compilation) kullanabilirsiniz. C# derleyicisi, kaynak kodunuzda kullanabileceğiniz hiçbir sembol veya makroyu tanımlar; Tüm sembol tanımlarının Kullanıcı tanımlı olması gerekir.

> [!NOTE]
> C# `#define` yönergesi, C++ gibi dillerde olduğu gibi bir simgeye değer verilmesini sağlar. Örneğin, `#define` bir makro oluşturmak veya bir sabit tanımlamak için kullanılamaz. Bir sabit tanımlamanız gerekiyorsa, bir `enum` değişken kullanın. C++ stili makro oluşturmak isterseniz, genel türler gibi alternatifleri göz önünde bulundurun. Makrolar dikkatle hataya açık olduğundan, C# kullanılmasına Izin vermez, ancak daha güvenli alternatifler sağlar.

## <a name="langversion"></a>LangVersion

Derleyicinin yalnızca seçili C# dil belirtiminde bulunan sözdizimini kabul etmesine neden olur.

```xml
<LangVersion>9.0</LangVersion>
```

Aşağıdaki değerler geçerlidir:

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

Varsayılan dil sürümü, uygulamanız için hedef çerçeveye ve SDK 'nın veya Visual Studio 'nun yüklü olduğu sürüme bağlıdır. Bu kurallar [C# dil sürümü oluşturma](../configure-language-version.md#defaults)bölümünde tanımlanmıştır.

C# uygulamanız tarafından başvurulan meta veriler **langversion** derleyici seçeneğine tabi değildir.

C# derleyicisinin her sürümü dil belirtimine uzantılar içerdiğinden, **langversion** size derleyicinin önceki bir sürümünün eşdeğer işlevlerini vermez.

Ayrıca, C# sürüm güncelleştirmeleri genellikle büyük .NET Framework sürümleriyle aynı olsa da yeni söz dizimi ve Özellikler ilgili Framework sürümüne bağlı değildir. Yeni özellikler, C# düzeltmesine göre de yayınlanan yeni bir derleyici güncelleştirmesi gerektirirken, her bir özellik kendi minimum .NET API 'sine veya NuGet paketlerini veya diğer kitaplıkları ekleyerek alt düzey çerçeveler üzerinde çalışmasına izin veren ortak dil çalışma zamanı gereksinimlerine sahiptir.

Kullandığınız **langversion** ayarından bağımsız olarak,. exe veya. dll dosyanızı oluşturmak için ortak dil çalışma zamanının güncel sürümünü kullanın. Tek bir istisna, **-langversion: ISO-1** altında çalışan arkadaş derlemelerinden ve [**moduleassemblyname**](advanced.md#moduleassemblyname).

C# dil sürümünü belirtmek için diğer yollar için bkz. [C# dil sürümü oluşturma](../configure-language-version.md).

Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A> ..

### <a name="c-language-specification"></a>C# dili belirtimi

| Sürüm          | Bağlantı                       | Açıklama                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| C# 7,0 ve üzeri |                            | Şu anda kullanılamıyor                                                 |
| C# 6,0           | [Bağlantısının][csharp-6]           | C# dil belirtimi sürüm 6-resmi olmayan taslak: .NET Foundation |
| C# 5,0           | [PDF’yi İndir][csharp-5]   | Standart ECMA-334 5 sürümü                                           |
| C# 3,0           | [BELGEYI indir][csharp-3]   | C# dil belirtimi sürüm 3,0: Microsoft Corporation            |
| C# 2,0           | [PDF’yi İndir][csharp-2]   | Standart ECMA-334 4 sürümü                                           |
| C# 1,2           | [BELGEYI indir][csharp-1.2] | C# dil belirtimi sürüm 1,2: Microsoft Corporation            |
| C# 1,0           | [BELGEYI indir][csharp-1]   | C# dil belirtimi sürüm 1,0: Microsoft Corporation            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

### <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Tüm dil özelliklerini desteklemek için gereken en düşük SDK sürümü

Aşağıdaki tabloda, SDK 'nın en düşük sürümü, ilgili dil sürümünü destekleyen C# derleyicisi ile listelenmektedir:

| C# sürümü | En düşük SDK sürümü                                                                  |
|------------|--------------------------------------------------------------------------------------|
| C# 8.0     | Microsoft Visual Studio/derleme araçları 2019, sürüm 16,3 veya .NET Core 3,0 SDK         |
| C# 7.3     | Microsoft Visual Studio/derleme araçları 2017, sürüm 15,7                               |
| C# 7.2     | Microsoft Visual Studio/derleme araçları 2017, sürüm 15,5                               |
| C# 7.1     | Microsoft Visual Studio/derleme araçları 2017, sürüm 15,3                               |
| C# 7.0     | Microsoft Visual Studio/derleme araçları 2017                                             |
| C# 6       | Microsoft Visual Studio/derleme araçları 2015                                             |
| C# 5       | Microsoft Visual Studio/derleme araçları 2012 veya paketlenmiş .NET Framework 4,5 derleyicisi      |
| C# 4       | Microsoft Visual Studio/derleme araçları 2010 veya paketlenmiş .NET Framework 4,0 derleyicisi      |
| C# 3       | Microsoft Visual Studio/derleme araçları 2008 veya paketlenmiş .NET Framework 3,5 derleyicisi      |
| C# 2       | Microsoft Visual Studio/derleme araçları 2005 veya paketlenmiş .NET Framework 2,0 derleyicisi      |
| C# 1.0/1.2 | Microsoft Visual Studio/derleme araçları .NET 2002 veya paketlenmiş .NET Framework 1,0 derleyicisi |

## <a name="nullable"></a>Null Atanabilir

**Null yapılabilir** seçeneği, null yapılabilir bağlamı belirtmenize olanak tanır.

```xml
<Nullable>enable</Nullable>
```

Bağımsız değişken,, veya ' den biri olmalıdır `enable` `disable` `warnings` `annotations` . `enable`Bağımsız değişkeni null yapılabilir bağlamı mümkün. Belirtildiğinde `disable` null yapılabilir bağlam devre dışı bırakılır. `warnings`Bağımsız değişkeni sağlanırken null yapılabilir uyarı bağlamı etkindir. `annotations`Bağımsız değişkenini belirtirken, null yapılabilir ek açıklama bağlamı etkindir.

Akış Analizi, çalıştırılabilir koddaki değişkenlerin null olduğunu anlamak için kullanılır. Bir değişkenin Çıkarsanan null olabilme, değişkenin belirtilen null değer alabilme durumu değerinden bağımsızdır. Yöntem çağrıları, koşullu olarak atlanırsa bile çözümlenir. Örneğin, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yayın modunda.

Aşağıdaki özniteliklerle açıklama eklenmiş yöntemlerin çağrılması, akış analizini de etkiler:

- Basit ön koşullar: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> ve <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute>
- Basit son koşullar: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> ve <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute>
- Koşullu koşul sonrası: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> ve <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute>
- <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (örneğin, `DoesNotReturnIf(false)` için <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) ve <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- Üye son koşullar: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> ve <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])>

> [!IMPORTANT]
> Global null yapılabilir bağlam, oluşturulan kod dosyaları için uygulanmaz. Bu ayardan bağımsız olarak, null yapılabilir bağlam, oluşturuldu olarak işaretlenen tüm kaynak dosyaları için *devre dışıdır* . Bir dosyanın oluşturulduğu şekilde işaretlenmiş dört yolu vardır:
>
> 1. . Editorconfig dosyasında, `generated_code = true` Bu dosya için geçerli olan bir bölümde belirtin.
> 1. `<auto-generated>` `<auto-generated/>` Dosyanın üst kısmına bir açıklama koyun. Bu, açıklama içindeki herhangi bir satırda olabilir, ancak açıklama bloğu dosyadaki ilk öğe olmalıdır.
> 1. Dosya adını *TemporaryGeneratedFile_* başlatın
> 1. Dosya adını *. Designer. cs*, *. generated. cs*, *. g. cs* veya *. g. ı. cs* ile sonlandırın.
>
> Oluşturucular, Önişlemci yönergesini kullanarak kabul edebilir [`#nullable`](../preprocessor-directives.md#nullable-context) .
