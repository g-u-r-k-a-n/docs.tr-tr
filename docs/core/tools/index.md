---
title: .NET CLı
titleSuffix: ''
description: .NET CLı ve özelliklerine genel bakış.
ms.topic: overview
ms.date: 02/13/2020
ms.openlocfilehash: 6a12e2d16afe36092c10e14a7465fa3bdbb23f32
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633862"
---
# <a name="net-cli-overview"></a>.NET CLı genel bakış

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

.NET komut satırı arabirimi (CLı), .NET uygulamaları geliştirmeye, oluşturmaya, çalıştırmaya ve yayımlamaya yönelik platformlar arası bir araç zinciridir.

.Net CLı, [.NET SDK 'ya](../sdk.md)dahildir. .NET SDK 'yı yüklemeyi öğrenmek için bkz. [.NET Core 'U yüklemek](../install/windows.md).

## <a name="cli-commands"></a>CLI komutları

Aşağıdaki komutlar varsayılan olarak yüklenir:

### <a name="basic-commands"></a>Temel komutlar

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a>Proje değişikliği komutları

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a>Gelişmiş komutlar

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a>Araç yönetimi komutları

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- [`tool restore`](global-tools.md#install-a-local-tool) 3,0 .NET Core SDK bu yana kullanılabilir.
- [`tool run`](global-tools.md#invoke-a-local-tool) 3,0 .NET Core SDK bu yana kullanılabilir.
- [`tool uninstall`](dotnet-tool-uninstall.md)

Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır. Araçları kendiniz yazabilir veya üçüncü taraflarca yazılmış Araçları yükleyebilirsiniz. Araçlar genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir. Daha fazla bilgi için bkz. [.net araçlarına genel bakış](global-tools.md).

## <a name="command-structure"></a>Komut yapısı

CLı komut yapısı, [sürücüden ("DotNet")](#driver), [komuttan](#command)ve muhtemelen komut [bağımsız değişkenlerinden](#arguments) ve [seçeneklerden](#options)oluşur. Bu kalıbı, yeni bir konsol uygulaması oluşturma ve aşağıdaki komutlar *my_app* adlı bir dizinden yürütüldüğünde gösterildiği gibi komut satırından çalıştırma gıbı birçok CLI işlemi içinde görürsünüz:

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>Sürücü

Sürücü [DotNet](dotnet.md) olarak adlandırılır ve [çerçeveye bağlı bir uygulama](../deploying/index.md) çalıştırarak ya da bir komut yürüten iki sorumluluklara sahiptir.

Çerçeveye bağımlı bir uygulama çalıştırmak için, uygulamayı sürücüden sonra belirtin, örneğin, `dotnet /path/to/my_app.dll` . Komutu, uygulamanın DLL 'sinin bulunduğu klasörden yürütürken yalnızca yürütün `dotnet my_app.dll` . .NET çalışma zamanının belirli bir sürümünü kullanmak istiyorsanız, `--fx-version <VERSION>` seçeneğini kullanın ( [DotNet komut](dotnet.md) başvurusuna bakın).

Sürücüye bir komut sağlarsanız, `dotnet.exe` CLI komutu yürütme işlemini başlatır. Örnek:

```dotnetcli
dotnet build
```

İlk olarak, sürücü kullanılacak SDK sürümünü belirler. Dosyada [global.js](global-json.md) yoksa, SDK 'nın en son sürümü kullanılabilir. Bu, makinede en son nelerin olduğuna bağlı olarak önizleme veya kararlı bir sürüm olabilir.  SDK sürümü belirlendikten sonra, komutunu yürütür.

### <a name="command"></a>Komut

Komut bir eylem gerçekleştirir. Örneğin, `dotnet build` derleme kodu. `dotnet publish` kodu yayımlar. Komutlar, bir kural kullanılarak konsol uygulaması olarak uygulanır `dotnet {command}` .

### <a name="arguments"></a>Arguments

Komut satırında geçirdiğiniz bağımsız değişkenler çağrılan komutun bağımsız değişkenlerdir. Örneğin, çalıştırdığınızda `dotnet publish my_app.csproj` `my_app.csproj` bağımsız değişkeni yayımlanacak projeyi belirtir ve `publish` komutuna geçirilir.

### <a name="options"></a>Seçenekler

Komut satırında geçirdiğiniz seçenekler çağrılan komuta yönelik seçeneklerdir. Örneğin, yürüttüğünüzde `dotnet publish --output /build_output` , `--output` seçeneği ve değeri `publish` komutuna geçirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet/SDK GitHub deposu](https://github.com/dotnet/sdk/)
- [.NET yükleme kılavuzu](../install/windows.md)
