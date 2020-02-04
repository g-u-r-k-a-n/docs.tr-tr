---
title: Paketler, Metapackages ve çerçeveler-.NET Core
description: Paketler, Metapackages ve çerçeveler için terminoloji öğrenin.
author: richlander
ms.date: 06/20/2016
ms.openlocfilehash: 657519edf1c0860ee3222c71ce85723e19029a9d
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965899"
---
# <a name="packages-metapackages-and-frameworks"></a>Paketler, meta paketler ve çerçeveler

.NET Core, NuGet paketlerinden oluşan bir platformdur. Bazı ürün deneyimleri, başka bir deyişle çok büyük olan paketlerin ayrıntılı tanımlarından faydalanır. Bu kaba uyum sağlamak için, .NET Core, hassas bir paket kümesi ve bir [metapackage](#metapackages)adı verilen bir paket türü olan kaba parçalar halinde dağıtılır.

.NET Core paketlerinin her biri, çerçeveler olarak temsil edilen birden çok .NET uygulamasında çalışmayı destekler. Bu çerçevelerin bazıları, .NET Framework temsil eden `net46`gibi geleneksel çerçeveler. Farklı bir küme, çerçeveleri tanımlamak için yeni bir model oluşturan "paket tabanlı çerçeveler" olarak düşünülebilir yeni çerçeveler. Bu paket tabanlı çerçeveler tamamen oluşturulur ve paketler olarak tanımlanır ve paketler ve çerçeveler arasında güçlü bir ilişki oluşturulur.

## <a name="packages"></a>Paketler

.NET Core, temel elemanlar, üst düzey veri türleri, uygulama bileşim türleri ve ortak yardımcı programlar sağlayan bir dizi pakete ayrılır. Bu paketlerin her biri aynı ada sahip tek bir derlemeyi temsil eder. Örneğin, [System. Runtime paketi](https://www.nuget.org/packages/System.Runtime) System. Runtime. dll dosyasını içerir.

Paketleri hassas bir şekilde tanımlamanın avantajları vardır:

- Ayrıntılı paketler, diğer paketlerin görece sınırlı testinde kendi zamanlamalarıyla birlikte sevk edebilir.
- Hassas paketler, farklı işletim sistemi ve CPU desteği sağlayabilir.
- Hassas paketler yalnızca bir kitaplığa özgü bağımlılıklara sahip olabilir.
- Başvurulmayan paketler uygulama dağıtımının bir parçası olmadığından, uygulamalar daha küçüktür.

Bu avantajlardan bazıları yalnızca belirli durumlarda kullanılır. Örneğin, NET Core paketleri genellikle aynı platform desteğiyle aynı zamanlamaya göre gönderilir. Bakım durumunda, düzeltmeler dağıtılabilir ve küçük tek paket güncelleştirmeleri olarak yüklenebilir. Değişikliğin dar kapsamı nedeniyle, bir düzeltilmesi gereken doğrulama ve zaman tek bir kitaplık için gerekenlerle sınırlıdır.

Aşağıda .NET Core için anahtar NuGet paketlerinin bir listesi verilmiştir:

- [System. Runtime](https://www.nuget.org/packages/System.Runtime) -<xref:System.Object>, <xref:System.String>, <xref:System.Array>, <xref:System.Action>ve <xref:System.Collections.Generic.IList%601>dahil olmak üzere en temel .NET Core paketi.
- [System. Collections](https://www.nuget.org/packages/System.Collections) -<xref:System.Collections.Generic.List%601> ve <xref:System.Collections.Generic.Dictionary%602>dahil olmak üzere genel Koleksiyonlar kümesi (birincil).
- [System .net. http](https://www.nuget.org/packages/System.Net.Http) -<xref:System.Net.Http.HttpClient> ve <xref:System.Net.Http.HttpResponseMessage>dahil olmak üzere http ağ iletişimi için bir tür kümesi.
- [System. IO. FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) -<xref:System.IO.File> ve <xref:System.IO.Directory>dahil olmak üzere yerel veya ağa bağlı disk tabanlı depolamaya okuma ve yazma için bir tür kümesi.
- [System. LINQ](https://www.nuget.org/packages/System.Linq) -`Enumerable` ve <xref:System.Linq.ILookup%602>dahil olmak üzere nesneleri sorgulamak için bir tür kümesi.
- [System. Reflection](https://www.nuget.org/packages/System.Reflection) -<xref:System.Reflection.Assembly>, <xref:System.Reflection.TypeInfo> ve <xref:System.Reflection.MethodInfo>dahil olmak üzere türleri yükleme, İnceleme ve etkinleştirme için bir tür kümesi.

Genellikle, her paketi eklemek yerine bir [metapackage](#metapackages)dahil edilmesi daha kolay ve daha sağlamdır. Ancak, tek bir pakete ihtiyacınız olduğunda, bu dosyayı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvuran aşağıdaki örnekte olduğu gibi ekleyebilirsiniz.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

## <a name="metapackages"></a>Metapackages

Metapackage, birlikte anlamlı olan bir paket kümesini açıklamak için bir NuGet paket kuralıdır. Metapackage, bağımlılıkları yaparak bu paket kümesini temsil eder. Metapackage, isteğe bağlı olarak bir çerçeve belirterek paket kümesi için bir çerçeve oluşturabilir.

.NET Core araçlarının önceki sürümleri (Project. JSON ve csproj tabanlı araçlar) varsayılan olarak hem çerçeve hem de metapackage ' i belirtti. Ancak şu anda metapackage, her metapackage bir hedef çerçeveye bağlı olması için hedef Framework tarafından örtük olarak başvuruluyor. Örneğin, `netstandard1.6` Framework NetStandard. Library sürüm 1.6.0 metapackage 'e başvurur. Benzer şekilde, `netcoreapp2.1` Framework Microsoft. NETCore. App sürüm 2.1.0 metapackage 'e başvurur. Daha fazla bilgi için bkz. [.NET Core SDK örtük metapackage paket başvurusu](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md).

Bir çerçeveyi hedeflemek ve bir metapackage 'e dolaylı olarak başvurmak anlamına gelir, aslında, bağımlı paketlerin her birine bir başvuruyu tek bir hareket olarak eklersiniz. Bu, bu paketlerdeki tüm kitaplıkların IntelliSense (veya benzer deneyim) ve uygulamanızı yayımlaması için kullanılabilir olmasını sağlar.

Metapackages kullanmanın avantajları vardır:

- Büyük bir hassas paket kümesine başvurmak için kullanışlı bir kullanıcı deneyimi sağlar.
- Sınanmış ve birlikte çalışan bir paket kümesini (belirli sürümler dahil) tanımlar.

.NET Standard metapackage:

- [Netstandard. Library](https://www.nuget.org/packages/NETStandard.Library) -.NET Standard parçası olan kitaplıkları açıklar. .NET Standard destekleyen tüm .NET uygulamaları için geçerlidir (örneğin, .NET Framework, .NET Core ve mono). `netstandard` çerçevesini belirler.

Temel .NET Core meta paketleri şunlardır:

- [Microsoft. NETCore. app](https://www.nuget.org/packages/Microsoft.NETCore.App) -.NET Core dağıtımının parçası olan kitaplıkları açıklar. `.NETCoreApp` çerçevesini belirler. Daha küçük `NETStandard.Library`bağlıdır.
- [Microsoft. AspNetCore. app](https://www.nuget.org/packages/Microsoft.AspNetCore.App) -üçüncü taraf bağımlılıkları içerenler dışında ASP.NET Core ve Entity Framework Core desteklenen tüm paketleri içerir. Daha fazla bilgi için bkz. [Microsoft. AspNetCore. app metapackage ASP.NET Core](/aspnet/core/fundamentals/metapackage-app) .
- [Microsoft. AspNetCore. All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) -ASP.NET Core ve Entity Framework Core tarafından kullanılan ASP.NET Core, Entity Framework Core ve dahili ve üçüncü taraf bağımlılıklarından desteklenen tüm paketleri içerir. Daha fazla bilgi için bkz. [Microsoft. AspNetCore. tüm metapackage for ASP.NET Core 2. x](/aspnet/core/fundamentals/metapackage) .
- [Microsoft. NETCore. taşınabilir. uyumluluk](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) -mscorlib tabanlı taşınabilir sınıf kitaplıklarının (PCLS) .NET Core üzerinde çalışmasını sağlayan bir uyumluluk ve uyumluluk listesi kümesi.

## <a name="frameworks"></a>Çerçeveler

.NET Core paketlerinin her biri bir çalışma zamanı çerçevesi kümesini destekler. Çerçeveler, belirli bir çerçeveyi hedeflediğinizde kullanabileceğiniz kullanılabilir bir API kümesini (ve potansiyel olarak diğer özellikleri) anlatmaktadır. Yeni API 'Ler eklendikçe bunlar sürümlüdür.

Örneğin, [System. IO. FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) aşağıdaki çerçeveleri destekler:

- . NETFramework, sürüm = 4.6
- . NETStandard, sürüm = 1.3
- 6 Xamarin Platformu (örneğin, xamarinios10)

Çerçevelerin tanımlandığı iki farklı yolu örneklerle aynı olduğundan, bu çerçevelerin ilk ikisini de kontrast açısından yararlı olur:

- `.NETFramework,Version=4.6` Framework, .NET Framework 4,6 ' deki kullanılabilir API 'Leri temsil eder. .NET Framework 4,6 başvuru Derlemeleriyle derlenen kitaplıklar oluşturabilir ve ardından bu kitaplıkları bir net46 lib klasöründeki NuGet paketlerinde dağıtabilirsiniz. Bu, .NET Framework 4,6 ' i hedefleyen veya onunla uyumlu olan uygulamalar için kullanılacaktır. Bu, tüm çerçeveleri geleneksel olarak nasıl çalıştık.

- `.NETStandard,Version=1.3` Framework, paket tabanlı bir çerçevedir. Altyapısı, Framework bakımından API 'Leri tanımlamak ve göstermek için çerçeveyi hedefleyen paketlere bağımlıdır.

## <a name="package-based-frameworks"></a>Paket tabanlı çerçeveler

Çerçeveler ve paketler arasında iki yönlü bir ilişki vardır. İlk bölüm, belirli bir çerçeve için kullanılabilir API 'Leri tanımlama, örneğin `netstandard1.3`. `netstandard1.3` (veya `netstandard1.0`gibi uyumlu çerçeveler) hedef paketler `netstandard1.3`için kullanılabilir olan API 'Leri tanımlar. Bu, döngüsel bir tanım gibi kalabilir, ancak değildir. "Paket tabanlı" olan sanallaştırılan, Framework API tanımı paketlerden gelir. Framework hiç API tanımlamaz.

İlişkinin ikinci bölümü varlık seçiminden oluşur. Paketler, birden çok çerçeve için varlıklar içerebilir. Bir dizi paket ve/veya Metapaket için bir başvuru verildiğinde, Framework hangi varlığın seçilmesi gerektiğini (örneğin `net46` veya `netstandard1.3`) belirlemekte gereklidir. Doğru varlığı seçmek önemlidir. Örneğin, bir `net46` varlık büyük olasılıkla .NET Framework 4,0 veya .NET Core 1,0 ile uyumlu olmayabilir.

Bu ilişkiyi aşağıdaki görüntüde görebilirsiniz. *API* , *Framework 'ü*hedefler ve tanımlar. *Çerçeve* , *varlık seçimi*için kullanılır. *Varlık* size API sağlar.

![Paket tabanlı çerçeve oluşturma](./media/packages/package-framework.png)

.NET Core ile kullanılan iki birincil paket tabanlı çerçeve şunlardır:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

.NET Standard ([hedef çerçeve bilinen](../standard/frameworks.md)adı: `netstandard`) çerçevesi, tarafından tanımlanan ve [.NET Standard](../standard/net-standard.md)üzerine oluşturulan API 'leri temsil eder. Birden çok çalışma zamanında çalıştırılması amaçlanan kitaplıkların bu çerçeveyi hedeflemesi gerekir. .NET Core, .NET Framework ve mono/Xamarin gibi .NET Standard uyumlu herhangi bir çalışma zamanında desteklenecektir. Bu çalışma zamanlarının her biri, uyguladıkları API 'Lere bağlı olarak bir .NET Standard sürümleri kümesini destekler.

`netstandard` Framework [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) metapackage 'e dolaylı olarak başvurur. Örneğin, aşağıdaki MSBuild proje dosyası, projenin, [`NETStandard.Library` sürüm 1,6](https://www.nuget.org/packages/NETStandard.Library/1.6.0) metapackage 'e başvuran `netstandard1.6`hedeflediğini belirtir.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Ancak, proje dosyasındaki çerçeve ve metapackage başvurularının eşleşmesi gerekmez ve meta paket sürümünden daha düşük bir çerçeve sürümü belirtmek için proje dosyanızdaki `<NetStandardImplicitPackageVersion>` öğesini kullanabilirsiniz. Örneğin, aşağıdaki proje dosyası geçerlidir.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

`netstandard1.3` hedeflemek ve `NETStandard.Library`1.6.0 sürümünü kullanmak garip görünebilir. Metapackage eski `netstandard` sürümleri için destek koruduğundan, bu geçerli bir kullanım durumdur. Bu durum, metapackage 'in 1.6.0 sürümünde standartlaştırılmış ve çeşitli `netstandard` sürümlerini hedefleyen tüm kitaplıklarınız için kullanabilmeniz durumunda olabilir. Bu yaklaşımda, önceki sürümleri değil yalnızca `NETStandard.Library` 1.6.0 geri yüklemeniz gerekir.

Tersi geçerli olmaz: `NETStandard.Library`1.3.0 sürümü ile `netstandard1.6` hedefleme. Alt sürüm metapackage, daha yüksek bir Framework için herhangi bir varlık sunmadığından, daha düşük bir alt pakete sahip daha yüksek bir çerçeveyi hedeflenemez. Metapackages için sürüm oluşturma düzeni, meta paketlerin tanımladıkları çerçevenin en yüksek sürümüyle eşleşmesini onaylar. Sürüm oluşturma düzeninin sanallaştırarak, `NETStandard.Library` ilk sürümü v 1.6.0, `netstandard1.6` varlıkları içerir. (Önceki örneğe sahip simetri için, burada v 1.3.0 kullanılır, ancak aslında yoktur.)

### <a name="net-core-application"></a>.NET Core uygulaması

.NET Core ([hedef çerçeve bilinen](../standard/frameworks.md)adı: `netcoreapp`) çerçevesi, .NET Core dağıtımı ve sağladığı konsol uygulama modeliyle birlikte gelen paketleri ve Ilişkili API 'leri temsil eder. .NET Core Uygulamaları, yalnızca .NET Core üzerinde çalışmasını amaçlanan kitaplıklar olması gerektiği için, konsol uygulama modelini hedeflerken, bu çerçeveyi kullanmalıdır. Bu Framework 'ün kullanılması, uygulamaları ve kitaplıkları yalnızca .NET Core üzerinde çalışır şekilde kısıtlar.

`Microsoft.NETCore.App` metapackage `netcoreapp` çerçevesini hedefler. `NETStandard.Library` paketi tarafından sağlanan ~ 40 ve ek olarak ~ 20 daha fazla ~ 60 kitaplığına erişim sağlar. Ek API 'lere erişim sağlamak için `netstandard`gibi `netcoreapp` veya uyumlu çerçeveleri hedefleyen ek kitaplıklara başvurabilirsiniz.

`Microsoft.NETCore.App` tarafından sağlanan ek kitaplıkların çoğu, bağımlılıklarının diğer `netstandard` kitaplıkları tarafından karşılanıp karşılanmadığı `netstandard` de hedef. Bu da `netstandard` kitaplıklarının bu paketlere bağımlılık olarak başvurmasına yol açabilir.
