---
title: .NET proje SDK 'sına genel bakış
titleSuffix: ''
description: .NET proje SDK 'Ları hakkında bilgi edinin.
ms.date: 09/17/2020
ms.topic: conceptual
no-loc:
- EmbeddedResource
- Compile
- None
ms.openlocfilehash: e5a6d0a1c988818e507936b567fa0188675cedc3
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432653"
---
# <a name="net-project-sdks"></a>.NET projesi SDK 'Ları

.NET Core ve .NET 5,0 ve üzeri projeler yazılım geliştirme seti (SDK) ile ilişkilendirilir. Her *Proje SDK 'sı* , bir dizi MSBuild [hedefi](/visualstudio/msbuild/msbuild-targets) ve kodu derleme, paketleme ve yayımlama ile ilgili [görevlerden](/visualstudio/msbuild/msbuild-tasks) oluşur. Proje SDK 'Sına başvuran bir proje bazen bir *SDK stili proje* olarak adlandırılır.

## <a name="available-sdks"></a>Kullanılabilir SDK 'lar

Aşağıdaki SDK 'lar kullanılabilir:

| ID | Description | Depo|
| - | - | - |
| `Microsoft.NET.Sdk` | .NET SDK | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | .NET [Web SDK 'sı](/aspnet/core/razor-pages/web-sdk) | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Razor` | .NET [Razor SDK 'sı](/aspnet/core/razor-pages/sdk) |
| `Microsoft.NET.Sdk.Worker` | .NET Worker hizmeti SDK 'Sı |
| `Microsoft.NET.Sdk.WindowsDesktop` | Windows Forms (WinForms) ve Windows Presentation Foundation (WPF) içeren .NET [Masaüstü SDK 'sı](msbuild-props-desktop.md).\* | <https://github.com/dotnet/winforms> ve <https://github.com/dotnet/wpf> |

.NET SDK, .NET için temel SDK 'dir. Diğer SDK 'lar .NET SDK 'ya başvuru sağlar ve diğer SDK 'lar ile ilişkili projelere tüm .NET SDK özellikleri de mevcuttur. Örneğin, Web SDK 'sı, hem .NET SDK hem de Razor SDK 'ya bağlıdır.

Ayrıca kendi SDK 'nizi, NuGet aracılığıyla dağıtılabilecek şekilde yazabilirsiniz.

\* .NET 5,0 ' den başlayarak Windows Forms ve Windows Presentation Foundation (WPF) projeleri yerine .NET SDK () belirtmelidir `Microsoft.NET.Sdk` `Microsoft.NET.Sdk.WindowsDesktop` . Bu projeler için, `TargetFramework` ve için `net5.0-windows` ayarı `UseWPF` `UseWindowsForms` `true` Windows Masaüstü SDK 'sını otomatik olarak içeri aktarır. Projeniz .NET 5,0 veya üstünü hedefliyorsa ve `Microsoft.NET.Sdk.WindowsDesktop` SDK 'yı belirtirse, derleme uyarısı NETSDK1137 alırsınız.

## <a name="project-files"></a>Proje dosyaları

.NET projeleri [MSBuild](/visualstudio/msbuild/msbuild) biçimine dayalıdır. C# projeleri için *. csproj* ve F # projelerinde *. fsproj* gibi uzantılara sahıp proje dosyaları, XML biçimindedir. MSBuild proje dosyasının kök öğesi [Proje](/visualstudio/msbuild/project-element-msbuild) öğesidir. `Project`Öğesi `Sdk` Hangi SDK (ve sürümü) kullanacağınızı belirten isteğe bağlı bir özniteliğe sahiptir. .NET araçlarını kullanmak ve kodunuzu derlemek için, `Sdk` özniteliğini [kullanılabilir SDK](#available-sdks) 'lar tablosundaki kimliklerden birine ayarlayın.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

NuGet 'den gelen bir SDK belirtmek için, adın sonundaki sürümü ekleyin veya *global.js* dosyadaki adı ve sürümü belirtin.

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

SDK 'yı belirtmenin bir başka yolu da en üst düzey [SDK](/visualstudio/msbuild/sdk-element-msbuild) öğesidir:

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

Bu yollarla bir SDK 'ya başvurmak, .NET için proje dosyalarını büyük ölçüde basitleştirir. Proje değerlendirilirken MSBuild, `Sdk.props` Proje dosyasının üst kısmına ve alt kısmına örtük içeri aktarmalar ekler `Sdk.targets` .

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> Bir Windows makinesinde, *%ProgramFiles%\dotnet\sdk \\ [Version] \Sdks\Microsoft.net.Sdk\Sdk* klasöründe *SDK. props* ve *SDK. targets* dosyaları bulunabilir.

### <a name="preprocess-the-project-file"></a>Proje dosyasını ön işleme

SDK ve hedefleri komutu kullanılarak eklendikten sonra, tam genişletilmiş projeyi MSBuild olarak görebilirsiniz `dotnet msbuild -preprocess` . Komutun [ön işlem](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) anahtarı [`dotnet msbuild`](../tools/dotnet-msbuild.md) hangi dosyaların içeri aktarılacağını, kaynaklarını ve derleme için gerçekten projeyi oluşturmadan yapıya katkılarını gösterir.

Projede birden çok hedef çerçeve varsa, komutun sonuçlarını MSBuild özelliği olarak belirterek yalnızca bir çerçeveye odaklayın. Örneğin:

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

## <a name="default-includes-and-excludes"></a>Varsayılan içerme ve dışladığı

[ `Compile` Öğelerin](/visualstudio/msbuild/common-msbuild-project-items#compile), [katıştırılmış kaynakların](/visualstudio/msbuild/common-msbuild-project-items#embeddedresource)ve [ `None` öğelerin](/visualstudio/msbuild/common-msbuild-project-items#none) varsayılan dahil ve hariç olması SDK 'da tanımlanmıştır. SDK olmayan .NET Framework projelerinin aksine, varsayılanlar en yaygın kullanım durumlarını kapsadığından proje dosyanızda bu öğeleri belirtmeniz gerekmez. Bu davranış, proje dosyasını daha küçük ve gerektiğinde daha kolay anlaşılır ve düzenlenebilir hale getirir.

Aşağıdaki tabloda, .NET SDK 'sında hangi öğelerin ve hangi [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) dahil olduğu ve dışlandıkları gösterilmektedir:

| Öğe           | Glob 'yi dahil et                              | Glob 'yi hariç tut                                                  | Glob 'yi kaldır              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Compile           | \*\*/\*. cs (veya diğer dil uzantıları) | \*\*/\*kullanıcısını  \*\*/\*.\* PROJ  \*\*/\*. sln  \*\*/\*. vssscc  | Yok                      |
| EmbeddedResource  | \*\*/\*. resx                              | \*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc     | Yok                      |
| None              | \*\*/\*                                   | \*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc     | \*\*/\*.cs \*\*/\*. resx |

> [!NOTE]
> Ve `./bin` `./obj` MSBuild özellikleriyle temsil edilen ve klasörleri, `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` Varsayılan olarak genelleştirmeler 'tan çıkarılır. Dışlayarak [DefaultItemExcludes özelliği](msbuild-props.md#defaultitemexcludes)tarafından temsil edilir.

.NET masaüstü SDK 'sının WPF için daha fazla içerme ve dışladığı vardır. Daha fazla bilgi için bkz. [WPF varsayılan içerme ve dışladığı](msbuild-props-desktop.md#wpf-default-includes-and-excludes).

### <a name="build-errors"></a>Derleme hataları

Proje dosyanızda bu öğelerden herhangi birini açıkça tanımlarsanız, büyük olasılıkla aşağıdakine benzer bir "NETSDK1022" derleme hatası alırsınız:

> Yinelenen ' Compile ' öğeleri eklendi. .NET SDK, Compile Varsayılan olarak proje dizininizdeki ' ' öğelerini içerir. Proje dosyanızdaki bu öğeleri kaldırabilir ya da Compile bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' EnableDefault Items ' özelliğini ' false ' olarak ayarlayabilirsiniz.

> Yinelenen ' EmbeddedResource ' öğeleri eklendi. .NET SDK, EmbeddedResource Varsayılan olarak proje dizininizdeki ' ' öğelerini içerir. Proje dosyanızdaki bu öğeleri kaldırabilir ya da EmbeddedResource bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' EnableDefault Items ' özelliğini ' false ' olarak ayarlayabilirsiniz.

Hataları gidermek için aşağıdakilerden birini yapın:

- `Compile` `EmbeddedResource` `None` Önceki tabloda listelenenlerin bulunduğu açık, veya öğeleri kaldırın.

- Tüm örtük dosya eklemeyi devre dışı bırakmak için [Enabledefaultıtems özelliğini](msbuild-props.md#enabledefaultitems) olarak ayarlayın `false` :

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  Uygulamanızla yayımlanacak dosyaları belirtmek istiyorsanız, bu gibi bilinen MSBuild mekanizmalarını yine de kullanabilirsiniz (örneğin, `Content` öğesi).

- `Compile` `EmbeddedResource` `None` [Enabledefault Compile öğelerini](msbuild-props.md#enabledefaultcompileitems), [enabledefault EmbeddedResource öğelerini](msbuild-props.md#enabledefaultembeddedresourceitems)veya [enabledefault None Items](msbuild-props.md#enabledefaultnoneitems) özelliğini şu şekilde ayarlayarak yalnızca, veya genelleştirmeler öğesini seçmeli olarak devre dışı bırakın `false` :

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  Yalnızca genelleştirmeler 'yi devre dışı bırakırsanız `Compile` , Visual Studio 'daki Çözüm Gezgini, \* öğe olarak da dahil olmak üzere projenin bir parçası olarak. cs öğelerini gösterir `None` . Örtük glob 'yi devre dışı bırakmak için `None` , `EnableDefaultNoneItems` çok olarak ayarlayın `false` .

## <a name="implicit-package-references"></a>Örtük paket başvuruları

.NET Core 1,0-2,2 veya .NET Standard 1,0-2,0 hedeflenirken, .NET SDK belirli *metapaketlerine* örtük başvurular ekler. Metapackage, yalnızca diğer paketlerdeki bağımlılıklardan oluşan çerçeve tabanlı bir pakettir. Meta paketlere, proje dosyanızın [TargetFramework](msbuild-props.md#targetframework) veya [targetçerçeveler](msbuild-props.md#targetframeworks) özelliğinde belirtilen hedef Framework 'ler temelinde örtülü olarak başvurulur.

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp2.1</TargetFramework>
</PropertyGroup>
```

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
</PropertyGroup>
```

Gerekirse, [DisableImplicitFrameworkReferences](msbuild-props.md#disableimplicitframeworkreferences) özelliğini kullanarak örtük paket başvurularını devre dışı bırakabilir ve yalnızca ihtiyacınız olan çerçevelere veya paketlere açık başvurular ekleyebilirsiniz.

Öneri

- .NET Framework, .NET Core 1,0-2,2 veya .NET Standard 1,0-2,0 ' i hedeflerken, `Microsoft.NETCore.App` `NETStandard.Library` proje dosyanızdaki bir öğe aracılığıyla veya metapaketlerine açık bir başvuru eklemeyin `<PackageReference>` . .NET Core 1,0-2,2 ve .NET Standard 1,0-2,0 projeleri için, bu meta paketlere örtük olarak başvurulur. .NET Framework projeleri için, `NETStandard.Library` .NET Standard tabanlı bir NuGet paketi kullanılırken herhangi bir sürümü gerekiyorsa, NuGet bu sürümü otomatik olarak yüklenir.
- .NET Core 1,0-2,2 ' i hedeflerken çalışma zamanının belirli bir sürümüne ihtiyacınız varsa, `<RuntimeFrameworkVersion>` metapackage 'e başvurmak yerine projenizdeki özelliği kullanın (örneğin, `1.0.4` ). Örneğin, [kendi içinde olan dağıtımlar](../deploying/index.md#publish-self-contained)kullanıyorsanız, 1.0.0 LTS çalışma zamanının belirli bir düzeltme eki sürümüne ihtiyacınız bulunabilir.
- `NETStandard.Library`.NET Standard 1,0-2,0 ' i hedeflerken metapackage 'ın belirli bir sürümüne ihtiyacınız varsa, `<NetStandardImplicitPackageVersion>` özelliğini kullanabilir ve ihtiyacınız olan sürümü ayarlayabilirsiniz.

## <a name="build-events"></a>Derleme olayları

SDK stili projelerde, veya adında bir MSBuild hedefi kullanın `PreBuild` `PostBuild` ve `BeforeTargets` özelliğini `PreBuild` veya `AfterTargets` özelliğini ayarlayın `PostBuild` .

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>
> - MSBuild hedefleri için herhangi bir ad kullanabilirsiniz. Ancak, Visual Studio IDE tanır `PreBuild` ve `PostBuild` hedefler, bu nedenle bu adları kullanarak IDE 'deki komutları düzenleyebilirsiniz.
> - Özellikler ve, gibi `PreBuildEvent` `PostBuildEvent` makrolar çözümlenmediği için SDK stili projelerde önerilmez `$(ProjectDir)` . Örneğin, aşağıdaki kod desteklenmez:
>
> ```xml
> <PropertyGroup>
>   <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
> </PropertyGroup>
> ```

## <a name="customize-the-build"></a>Derlemeyi özelleştirme

[Bir derlemeyi özelleştirmek](/visualstudio/msbuild/customize-your-build)için çeşitli yollar vardır. Bir [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) veya [DotNet](../tools/index.md) komutuna bir bağımsız değişken olarak geçirerek bir özelliği geçersiz kılmak isteyebilirsiniz. Ayrıca, özelliği proje dosyasına veya bir *Dizin. Build. props* dosyasına ekleyebilirsiniz. .NET projelerinin yararlı özelliklerinin bir listesi için bkz. [.NET SDK projeleri Için MSBuild başvurusu](msbuild-props.md).

### <a name="custom-targets"></a>Özel hedefler

.NET projeleri, paketi tüketen projeler tarafından kullanılmak üzere özel MSBuild hedeflerini ve özelliklerini paketleyebilir. Şunları yapmak istediğinizde bu tür bir genişletilebilirlik kullanın:

- Yapı sürecini genişletin.
- Oluşturulan dosyalar gibi yapı sürecinin yapılarına erişin.
- Yapılandırmanın çağrıldığı yapılandırmayı inceleyin.

Dosyaları forma `<package_id>.targets` veya `<package_id>.props` (örneğin, `Contoso.Utility.UsefulStuff.targets` ) projenin *Build* klasörüne yerleştirerek özel derleme hedefleri veya özellikleri eklersiniz.

Aşağıdaki XML, bir *. csproj* dosyasındaki, [`dotnet pack`](../tools/dotnet-pack.md) komuta neyin paketlenecek olduğunu bildiren bir kod parçacıdır. `<ItemGroup Label="dotnet pack instructions">`Öğesi, hedef dosyalarını paketin içindeki *derleme* klasörüne koyar. `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">`Öğesi derlemeler ve *. JSON* dosyalarını *Build* klasörüne koyar.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...

</Project>
```

Projenizde özel bir hedef kullanmak için `PackageReference` pakete ve sürümüne işaret eden bir öğesi ekleyin. Araçların aksine, özel hedefler paketi, tüketen projenin bağımlılık kapanışına dahil edilir.

Özel hedefin nasıl kullanılacağını yapılandırabilirsiniz. Bir MSBuild hedefi olduğundan, belirli bir hedefe bağlı olabilir, başka bir hedeften sonra çalıştırılabilir veya komutu kullanılarak el ile çağrılabilir `dotnet msbuild -t:<target-name>` . Ancak, daha iyi bir kullanıcı deneyimi sağlamak için proje başına araçları ve özel hedefleri birleştirebilirsiniz. Bu senaryoda, proje başına aracı her türlü parametreyi kabul eder ve [`dotnet msbuild`](../tools/dotnet-msbuild.md) hedefi yürüten gerekli çağrıya çevirir. Bu tür sinerjiden bahsederek denemelerini 'nin bir örneğini projede [MVP Zirvesi 2016 Hackathon örnekleri](https://github.com/dotnet/MVPSummitHackathon2016) deposunda görebilirsiniz [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) .

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core 'ı yükler](../install/index.yml)
- [MSBuild proje SDK 'larını kullanma](/visualstudio/msbuild/how-to-use-project-sdk)
- [NuGet ile özel MSBuild hedeflerini ve props paketleme](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
