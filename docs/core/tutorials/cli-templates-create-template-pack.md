---
title: DotNet New için bir şablon paketi oluşturma
description: DotNet yeni komut için bir şablon paketi oluşturacak bir csproj dosyası oluşturmayı öğrenin.
author: adegeo
ms.date: 03/26/2021
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 343104f9609c59e7da24f857de6a7fc29803e2df
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255395"
---
# <a name="tutorial-create-a-template-pack"></a>Öğretici: şablon paketi oluşturma

.NET ile, projeler, dosyalar ve hatta kaynaklar üreten şablonlar oluşturabilir ve dağıtabilirsiniz. Bu öğretici, komutuyla kullanmak üzere şablon oluşturmayı, yüklemeyi ve kaldırmayı öğretir ve bir serinin üçüncü bölümüdür `dotnet new` .

Serinin bu bölümünde şunları nasıl yapacağınızı öğreneceksiniz:

> [!div class="checklist"]
>
> * \*Bir şablon paketi oluşturmak için bir. csproj projesi oluşturma
> * Paketleme için proje dosyasını yapılandırma
> * NuGet paket dosyasından şablon yükler
> * Bir şablonu paket KIMLIĞIYLE kaldır

## <a name="prerequisites"></a>Önkoşullar

* Bu öğretici serisinin [1](cli-templates-create-item-template.md) . ve [2. bölümünü](cli-templates-create-project-template.md) doldurun.

  Bu öğretici, Bu öğreticinin ilk iki bölümünde oluşturulan iki şablonu kullanır. Şablonu, klasör olarak _working\templates \\_ klasörüne kopyaladığınız sürece farklı bir şablon kullanabilirsiniz.

* Bir Terminal açın ve _çalışma \\_ klasörüne gidin.

## <a name="create-a-template-pack-project"></a>Şablon paketi projesi oluşturma

Bir şablon paketi, bir dosyada paketlenmiş bir veya daha fazla şablondur. Bir paketi yüklediğinizde veya kaldırdığınızda, paketin içerdiği tüm şablonlar sırasıyla eklenir veya kaldırılır. Bu öğretici serisinin önceki kısımları yalnızca bireysel şablonlarla birlikte çalışmıştır. Paketlenmiş olmayan bir şablonu paylaşmak için, şablon klasörünü kopyalamanız ve bu klasör aracılığıyla kurmanız gerekir. Bir şablon paketi içinde birden fazla şablon olabileceğinden ve tek bir dosya olduğundan, paylaşma daha kolay olur.

Şablon paketleri, bir NuGet paketi (_. nupkg_) dosyası tarafından temsil edilir. Tüm NuGet paketleri gibi, şablon paketini bir NuGet akışına de yükleyebilirsiniz. `dotnet new -i`Komut, bir NuGet paketi akışından şablon paketi yüklemeyi destekler. Ayrıca, bir _. nupkg_ dosyasından doğrudan bir şablon paketi de yükleyebilirsiniz.

Normalde, kod derlemek ve bir ikili oluşturmak için C# proje dosyası kullanırsınız. Ancak, proje bir şablon paketi oluşturmak için de kullanılabilir. _. Csproj_ ayarlarını değiştirerek, bu kodun herhangi bir kodu derlemesine engel olabilir ve bunun yerine şablonlarınızın tüm varlıklarını kaynak olarak dahil edebilirsiniz. Bu proje oluşturulduğunda, bir şablon paketi NuGet paketi oluşturur.

Oluşturacağınız paket, daha önce oluşturulan [öğe şablonunu](cli-templates-create-item-template.md) ve [paket şablonunu](cli-templates-create-project-template.md) içerir. İki şablonu _working\templates \\_ klasörüne grupladığımızda, _. csproj_ dosyası için _çalışma_ klasörünü kullanabiliriz.

Terminalinizde _çalışma_ klasörüne gidin. Yeni bir proje oluşturun ve adı `templatepack` ve çıkış klasörünü geçerli klasöre ayarlayın.

```dotnetcli
dotnet new console -n templatepack -o .
```

`-n`Parametresi _. csproj_ dosya adını _templatepack. csproj_ olarak ayarlar. `-o`Parametresi, geçerli dizindeki dosyaları oluşturur. Aşağıdaki çıktıya benzer bir sonuç görmeniz gerekir.

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

Ardından, en sevdiğiniz düzenleyicide _templatepack. csproj_ dosyasını açın ve IÇERIĞI aşağıdaki XML ile değiştirin:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>

    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
    <NoWarn>$(NoWarn);NU5128</NoWarn>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

`<PropertyGroup>`YUKARıDAKI XML 'deki ayarlar üç gruba bölünmüştür. İlk grup, bir NuGet paketi için gereken özelliklerle ilgilidir. Bu üç `<Package*>` ayar, bir NuGet akışında paketinizi tanımlamak Için NuGet paket özellikleriyle birlikte olmalıdır. Özellikle `<PackageId>` değer, şablon paketini dizin yolu yerine tek bir adla kaldırmak için kullanılır. Ayrıca, bir NuGet akışından şablon paketini yüklemek için de kullanılabilir. Ve gibi geri kalan ayarlar `<Title>` , `<PackageTags>` NuGet akışında görüntülenecek meta verilerle birlikte olmalıdır. NuGet ayarları hakkında daha fazla bilgi için bkz. [NuGet ve MSBuild özellikleri](/nuget/reference/msbuild-targets).

`<TargetFramework>`Projeyi derlemek ve paketetmek için paket komutunu çalıştırdığınızda MSBuild 'in düzgün çalışması için ayar ayarlanmalıdır.

Sonraki üç ayar, projeyi, oluşturulduğu zaman NuGet paketindeki uygun klasöre dahil etmek için doğru şekilde yapılandırmaya yönelik olmalıdır.

Son ayar, şablon paketi projelerine uygulanan bir uyarı iletisini bastırır.

`<ItemGroup>`İki ayar içerir. İlk olarak, `<Content>` ayar _Şablonlar_ klasöründeki her şeyi içerik olarak içerir. Ayrıca, derlenmiş kodların (şablonlarınızı test etmeniz ve derlediğiniz) dahil edilmesini engellemek için herhangi bir _bin_ klasörünü veya _obj_ klasörünü dışarıda bırakmak üzere ayarlanır. İkincisi, `<Compile>` ayar tüm kod dosyalarını nerede bulunduklarında bağımsız olarak derlemeden dışlar. Bu ayar, şablon paketi oluşturmak için kullanılan projenin _Şablonlar_ klasörü hiyerarşisindeki kodu derlemeye çalışmamasını engeller.

## <a name="build-and-install"></a>Oluşturma ve yüklemeyi

Proje dosyasını kaydedin. Şablon paketini oluşturmadan önce, klasör yapınızı doğru olduğundan emin olun. Paketetmek istediğiniz herhangi bir şablon, kendi klasöründe _Şablonlar_ klasörüne yerleştirilmelidir. Klasör yapısı şuna benzer görünmelidir:

```console
working
│   templatepack.csproj
└───templates
    ├───extensions
    │   └───.template.config
    │           template.json
    └───consoleasync
        └───.template.config
                template.json
```

_Şablonlar_ klasörü iki klasöre sahiptir: _Uzantılar_ ve _consoleasync_.

Terminalinizde, _çalışma_ klasöründen `dotnet pack` komutunu çalıştırın. Bu komut, projenizi oluşturur ve aşağıdaki çıktıda gösterildiği gibi _Working\bin\debug_ klasöründe bir NuGet paketi oluşturur:

```console
C:\working> dotnet pack

Microsoft (R) Build Engine version 16.8.0+126527ff1 for .NET
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

Sonra, komutuyla şablon paketi dosyasını yükler `dotnet new -i PATH_TO_NUPKG_FILE` .

```console
C:\working> dotnet new -i C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name               Language          Tags
--------------------------------------------      -------------------      ------------      ----------------------
Example templates: string extensions              stringext                [C#]              Common/Code
Console Application                               console                  [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync             [C#]              Common/Console/C#9
Class library                                     classlib                 [C#], F#, VB      Common/Library
```

NuGet paketini bir NuGet akışına yüklediyseniz, `dotnet new -i PACKAGEID` `PACKAGEID` `<PackageId>` _. csproj_ dosyasındaki ayarla aynı olan komutunu kullanabilirsiniz. Bu paket KIMLIĞI, NuGet paket tanımlayıcısı ile aynıdır.

## <a name="uninstall-the-template-pack"></a>Şablon paketini kaldırma

Şablon paketini, _. nupkg_ dosyasıyla doğrudan veya NuGet akışı ile nasıl yükletiğinize bakılmaksızın, bir şablon paketinin kaldırılması aynı olur. Kaldırmak istediğiniz `<PackageId>` şablonun öğesini kullanın. Komutunu çalıştırarak yüklenen şablonların bir listesini alabilirsiniz `dotnet new -u` .

```dotnetcli
C:\working> dotnet new -u

Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ProjectTemplates.2.2
    Details:
      NuGetPackageId: Microsoft.DotNet.Common.ProjectTemplates.2.2
      Version: 1.0.2-beta4
      Author: Microsoft
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
    Uninstall Command:
      dotnet new -u Microsoft.DotNet.Common.ProjectTemplates.2.2

... cut to save space ...

  AdatumCorporation.Utility.Templates
    Details:
      NuGetPackageId: AdatumCorporation.Utility.Templates
      Version: 1.0.0
      Author: Me
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
    Uninstall Command:
      dotnet new -u AdatumCorporation.Utility.Templates
```

`dotnet new -u AdatumCorporation.Utility.Templates`Şablonu kaldırmak için ' i çalıştırın. `dotnet new`Komutu, daha önce yüklediğiniz şablonları atlamanızı gerektiren yardım bilgilerini çıktı olarak alırsınız.

Tebrikler! bir şablon paketi yüklediniz ve kaldırdık.

## <a name="next-steps"></a>Sonraki adımlar

Zaten öğrendiğiniz şablonlar hakkında daha fazla bilgi edinmek için, [DotNet yeni makale Için özel şablonlar](../tools/custom-templates.md) bölümüne bakın.

* [DotNet/şablon oluşturma GitHub deposu wiki](https://github.com/dotnet/templating/wiki)
* [DotNet/DotNet-şablon-örnek GitHub deposu](https://github.com/dotnet/dotnet-template-samples)
* [JSON Şema deposundaki şemada *template.js*](http://json.schemastore.org/template)
