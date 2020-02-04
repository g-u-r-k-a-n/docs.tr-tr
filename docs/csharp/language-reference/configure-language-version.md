---
title: C#dil sürümü oluşturma C# -kılavuz
description: C# Dil sürümünün projenize göre nasıl belirlendiği hakkında bilgi edinin ve bunu el ile ayarlayabileceğiniz farklı değerler.
ms.date: 07/10/2019
ms.openlocfilehash: 3c1035d983660ea0a945e4d4b7b72c69736c90cb
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980138"
---
# <a name="c-language-versioning"></a>C#dil sürümü oluşturma

En son C# derleyici, projenizin hedef çerçevesine veya çerçevelerine göre varsayılan dil sürümünü belirler. Bunun nedeni, C# dilin her .NET uygulamasında kullanılamayan türleri veya çalışma zamanı bileşenlerini kullanan özelliklere sahip olması olabilir. Bu Ayrıca, projenizin her türlü hedefi için varsayılan olarak en yüksek uyumlu dil sürümünü almanızı sağlar.

Bu makaledeki kurallar, Visual Studio 2019 veya .NET Core 3,0 SDK ile sunulan derleyici için geçerlidir. Visual C# Studio 2017 yüklemesinin parçası olan derleyiciler veya daha önceki .NET Core SDK sürümleri, varsayılan olarak C# 7,0 ' dir. 

## <a name="defaults"></a>Varsayılanları

Derleyici, bu kurallara göre bir varsayılan değer belirler:

|Hedef çerçeve|sürümü|C#dil sürümü varsayılanı|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2,0|C# 7.3|
|.NET Standard|'in|C# 7.3|
|.NET Framework|tüm|C# 7.3|

## <a name="default-for-previews"></a>Önizlemeler için varsayılan

Projeniz karşılık gelen önizleme dili sürümüne sahip bir önizleme çerçevesini hedefliyorsa, kullanılan dil sürümü önizleme dili sürümüdür. Bu, yayımlanmış bir .NET Core sürümünü hedefleyen projelerinizi etkilemeden, herhangi bir ortamda bu önizleme ile çalışmak için garanti edilen en son özellikleri kullanmanızı sağlar.

## <a name="override-a-default"></a>Varsayılanı geçersiz kıl

C# Sürümünüzü açıkça belirtmeniz gerekiyorsa, bunu birkaç şekilde yapabilirsiniz:

- [Proje dosyanızı](#edit-the-project-file)el ile düzenleyin.
- [Bir alt dizinde birden çok proje için](#configure-multiple-projects)dil sürümünü ayarlayın.
- [`-langversion` derleyici seçeneğini](compiler-options/langversion-compiler-option.md)yapılandırın.

### <a name="edit-the-project-file"></a>Proje dosyasını düzenleme

Proje dosyanızdaki dil sürümünü ayarlayabilirsiniz. Örneğin, önizleme özelliklerine açıkça erişim istiyorsanız, şöyle bir öğe ekleyin:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Değer `preview`, derleyicinizin desteklediği en son C# önizleme dili sürümünü kullanır.

### <a name="configure-multiple-projects"></a>Birden çok proje yapılandırma

Birden çok projeyi yapılandırmak için, `<LangVersion>` öğesini içeren bir **Dizin. Build. props** dosyası oluşturabilirsiniz. Bunu genellikle çözüm dizininizde yapabilirsiniz. Aşağıdakileri çözüm dizininizde bir **Dizin. Build. props** dosyasına ekleyin:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Şimdi, bu dosyayı içeren dizinin her alt dizinindeki derlemeler Önizleme C# sürümünü kullanacaktır. Daha fazla bilgi için, [yapınızı özelleştirme](/visualstudio/msbuild/customize-your-build)başlıklı makaleye bakın.

## <a name="c-language-version-reference"></a>C#dil sürümü başvurusu

Aşağıdaki tabloda tüm geçerli C# dil sürümleri gösterilmektedir. Daha eskiyse, derleyicisinin her değeri anlayamayabilir. .NET Core 3,0 ' i yüklerseniz, listelenen her şeye erişim sahibi olursunuz.

|Değer|Açıklama|
|------------|-------------|
|önizleme|Derleyici, en son önizleme sürümündeki tüm geçerli dil sözdizimini kabul eder.|
|latest|Derleyici derleyicinin en son yayınlanan sürümünden (ikincil sürüm dahil) söz dizimini kabul eder.|
|Latestana|Derleyici derleyicinin en son yayınlanan ana sürümünden söz dizimini kabul eder.|
|8.0|Derleyici yalnızca C# 8,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|7.3|Derleyici yalnızca C# 7,3 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|7.2|Derleyici yalnızca C# 7,2 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|7.1|Derleyici yalnızca C# 7,1 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|7|Derleyici yalnızca C# 7,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|6|Derleyici yalnızca C# 6,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|5|Derleyici yalnızca C# 5,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|4|Derleyici yalnızca C# 4,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|3|Derleyici yalnızca C# 3,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|ISO-2|Derleyici yalnızca ISO/ıEC 23270:2006 C# (2,0) içinde bulunan söz dizimini kabul eder. |
|ISO-1|Derleyici yalnızca ISO/ıEC 23270:2003 C# (1.0/1.2) içinde bulunan söz dizimini kabul eder. |
