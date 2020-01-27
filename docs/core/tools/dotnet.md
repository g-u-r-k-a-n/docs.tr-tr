---
title: DotNet komutu
description: DotNet komutu (.NET Core CLI araçları için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 06/04/2018
ms.openlocfilehash: fe90968560b58471c279fcd2097741ea476cef0b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734072"
---
# <a name="dotnet-command"></a>DotNet komutu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet`-.NET kaynak kodu ve ikili dosyaları yönetmeye yönelik bir araç.

## <a name="synopsis"></a>Özeti

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a>Açıklama

`dotnet` .NET kaynak kodu ve ikili dosyalarını yönetmeye yönelik bir araçtır. [`dotnet build`](dotnet-build.md) ve [`dotnet run`](dotnet-run.md)gibi belirli görevleri gerçekleştiren komutları açığa çıkarır. Her komut kendi bağımsız değişkenlerini tanımlar. Kısa yardım belgelerine erişmek için her komuttan sonra `--help` yazın.

`dotnet`, `dotnet myapp.dll`gibi bir uygulama DLL belirterek uygulamaları çalıştırmak için kullanılabilir. Dağıtım seçenekleri hakkında bilgi edinmek için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md) .

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`--additional-deps <PATH>`

Ek *. Deps. JSON* dosyasının yolu.

`--additionalprobingpath <PATH>`

Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.

`--depsfile`

Bir *Deps. JSON* dosyasının yolu.

Bir *Deps. JSON* dosyası, derleme çakışmalarını çözmek için kullanılan bağımlılıklar, derleme bağımlılıkları ve sürüm bilgilerinin bir listesini içerir. Bu dosya hakkında daha fazla bilgi için bkz. GitHub üzerinde [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) .

`-d|--diagnostics`

Tanılama çıkışını izin vermez.

`--fx-version <VERSION>`

Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.

`-h|--help`

`dotnet build --help`gibi belirli bir komutun belgelerini yazdırır. `dotnet --help`, kullanılabilir komutların bir listesini yazdırır.

`--info`

.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.

`--list-runtimes`

Yüklü .NET Core çalışma zamanlarını görüntüler.

`--list-sdks`

Yüklü .NET Core SDK 'larını görüntüler.

`--roll-forward-on-no-candidate-fx <N>`

Gerekli paylaşılan çerçeve kullanılabilir olmadığında davranışını tanımlar. `N` aşağıdakilerden biri olabilir:

- `0`-alt düzey sürüm iletmeyi devre dışı bırakın.
- `1`-önemli sürümde değil, küçük sürümde ilet. Bu varsayılan davranıştır.
- `2`-küçük ve büyük sürümlerde ilet.

 Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).

`--runtimeconfig`

*Runtimeconfig. JSON* dosyasının yolu.

*Runtimeconfig. JSON* dosyası, çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır. Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`. Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.

`--version`

Kullanımda olan .NET Core SDK sürümünü yazdırır.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`--additional-deps <PATH>`

Ek *. Deps. JSON* dosyasının yolu.

`--additionalprobingpath <PATH>`

Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.

`--depsfile`

Bir *Deps. JSON* dosyasının yolu.

Bir *Deps. JSON* dosyası, derleme çakışmalarını çözmek için kullanılan bağımlılıkların, derleme bağımlılıklarının ve sürüm bilgilerinin bir listesini içerir. Bu dosya hakkında daha fazla bilgi için bkz. [GitHub üzerinde çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

`-d|--diagnostics`

Tanılama çıkışını izin vermez.

`--fx-version <VERSION>`

Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.

`-h|--help`

`dotnet build --help`gibi belirli bir komutun belgelerini yazdırır. `dotnet --help`, kullanılabilir komutların bir listesini yazdırır.

`--info`

.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.

`--roll-forward-on-no-candidate-fx`

 `0`olarak ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır. Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).

`--runtimeconfig`

*Runtimeconfig. JSON* dosyasının yolu.

*Runtimeconfig. JSON* dosyası, çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır. Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`. Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.

`--version`

Kullanımda olan .NET Core SDK sürümünü yazdırır.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.

`--depsfile`

Bir *Deps. JSON* dosyasının yolu.

Bir *Deps. JSON* dosyası, derleme çakışmalarını çözmek için kullanılan bağımlılıkların, derleme bağımlılıklarının ve sürüm bilgilerinin bir listesini içerir. Bu dosya hakkında daha fazla bilgi için bkz. [GitHub üzerinde çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

`-d|--diagnostics`

Tanılama çıkışını izin vermez.

`--fx-version <VERSION>`

Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.

`-h|--help`

`dotnet build --help`gibi belirli bir komutun belgelerini yazdırır. `dotnet --help`, kullanılabilir komutların bir listesini yazdırır.

`--info`

.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.

`--runtimeconfig`

*Runtimeconfig. JSON* dosyasının yolu.

*Runtimeconfig. JSON* dosyası, çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır. Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`. Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.

`--version`

Kullanımda olan .NET Core SDK sürümünü yazdırır.

---

## <a name="dotnet-commands"></a>dotnet komutları

### <a name="general"></a>Genel

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

| Komut                                       | İşlev                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | .NET Core uygulaması oluşturur.                                     |
| [dotnet build-server](dotnet-build-server.md) | Bir yapı tarafından başlatılan sunucularla etkileşime girer.                          |
| [dotnet clean](dotnet-clean.md)               | Derleme çıktılarını temizle.                                                |
| [dotnet help](dotnet-help.md)                 | Komutu için çevrimiçi daha ayrıntılı belgeler gösterir.           |
| [dotnet migrate](dotnet-migrate.md)           | Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.  |
| [dotnet msbuild](dotnet-msbuild.md)           | MSBuild komut satırına erişim sağlar.                        |
| [dotnet new](dotnet-new.md)                   | Belirli bir C# şablon F# için bir veya projesini başlatır.                |
| [dotnet pack](dotnet-pack.md)                 | Kodunuzun bir NuGet paketini oluşturur.                               |
| [dotnet publish](dotnet-publish.md)           | .NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md)           | Belirli bir uygulama için bağımlılıkları geri yükler.                  |
| [dotnet run](dotnet-run.md)                   | Uygulamayı kaynaktan çalıştırır.                                   |
| [dotnet sln](dotnet-sln.md)                   | Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.       |
| [dotnet store](dotnet-store.md)               | Derlemeleri çalışma zamanı paket deposunda depolar.                     |
| [dotnet test](dotnet-test.md)                 | Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

| Komut                             | İşlev                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | .NET Core uygulaması oluşturur.                                     |
| [dotnet clean](dotnet-clean.md)     | Derleme çıktılarını temizle.                                              |
| [dotnet help](dotnet-help.md)       | Komutu için çevrimiçi daha ayrıntılı belgeler gösterir.           |
| [dotnet migrate](dotnet-migrate.md) | Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.  |
| [dotnet msbuild](dotnet-msbuild.md) | MSBuild komut satırına erişim sağlar.                        |
| [dotnet new](dotnet-new.md)         | Belirli bir C# şablon F# için bir veya projesini başlatır.                |
| [dotnet pack](dotnet-pack.md)       | Kodunuzun bir NuGet paketini oluşturur.                               |
| [dotnet publish](dotnet-publish.md) | .NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md) | Belirli bir uygulama için bağımlılıkları geri yükler.                  |
| [dotnet run](dotnet-run.md)         | Uygulamayı kaynaktan çalıştırır.                                   |
| [dotnet sln](dotnet-sln.md)         | Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.       |
| [dotnet store](dotnet-store.md)     | Derlemeleri çalışma zamanı paket deposunda depolar.                     |
| [dotnet test](dotnet-test.md)       | Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

| Komut                             | İşlev                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | .NET Core uygulaması oluşturur.                                     |
| [dotnet clean](dotnet-clean.md)     | Derleme çıktılarını temizle.                                              |
| [dotnet migrate](dotnet-migrate.md) | Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.  |
| [dotnet msbuild](dotnet-msbuild.md) | MSBuild komut satırına erişim sağlar.                        |
| [dotnet new](dotnet-new.md)         | Belirli bir C# şablon F# için bir veya projesini başlatır.                |
| [dotnet pack](dotnet-pack.md)       | Kodunuzun bir NuGet paketini oluşturur.                               |
| [dotnet publish](dotnet-publish.md) | .NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md) | Belirli bir uygulama için bağımlılıkları geri yükler.                  |
| [dotnet run](dotnet-run.md)         | Uygulamayı kaynaktan çalıştırır.                                   |
| [dotnet sln](dotnet-sln.md)         | Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.       |
| [dotnet test](dotnet-test.md)       | Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.                                     |

---

### <a name="project-references"></a>Proje başvuruları

Komut | İşlev
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Bir proje başvurusu ekler.
[dotnet list reference](dotnet-list-reference.md) | Proje başvurularını listeler.
[dotnet remove reference](dotnet-remove-reference.md) | Proje başvurusunu kaldırır.

### <a name="nuget-packages"></a>NuGet paketleri

Komut | İşlev
--- | ---
[dotnet add package](dotnet-add-package.md) | Bir NuGet paketi ekler.
[dotnet remove package](dotnet-remove-package.md) | Bir NuGet paketini kaldırır.

### <a name="nuget-commands"></a>NuGet komutları

Komut | İşlev
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Sunucudan bir paketi siler veya listesini kaldırır.
[dotnet nuget locals](dotnet-nuget-locals.md) | Http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.
[dotnet nuget push](dotnet-nuget-push.md) | Bir paketi sunucuya gönderir ve yayımlar.

### <a name="global-tools-commands"></a>Küresel araçlar komutları

[.NET Core küresel araçlar](global-tools.md) .NET Core SDK 2.1.300 ile başlayarak kullanılabilir:

Komut | İşlev
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Makinenize küresel bir araç kurar.
[dotnet tool list](dotnet-tool-list.md) | Makinenizde varsayılan dizinde veya belirtilen yolda yüklü olan tüm genel araçları listeler.
[dotnet tool install](dotnet-tool-uninstall.md) | Bir genel aracı makinenizden kaldırır.
[dotnet tool update](dotnet-tool-update.md) | Makinenizde küresel bir aracı güncelleştirir.

### <a name="additional-tools"></a>Ek araçlar

.NET Core SDK 2.1.300 ile başlayarak, yalnızca .NET Core SDK bir parçası olarak yalnızca `DotnetCliToolReference` kullanılarak proje temelinde kullanılabilen birçok araç vardır. Bu araçlar aşağıdaki tabloda listelenmiştir:

| Aracı                                              | İşlev                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| geliştirme-CERT                                         | Geliştirme sertifikaları oluşturur ve yönetir.                |
| [aşv](/ef/core/miscellaneous/cli/dotnet)           | Komut satırı araçlarını Entity Framework Core.                    |
| SQL-Cache                                         | Önbellek komut satırı araçlarını SQL Server.                         |
| [Kullanıcı gizli dizileri](/aspnet/core/security/app-secrets) | Geliştirme Kullanıcı gizli dizilerini yönetir.                            |
| [Servisi](/aspnet/core/tutorials/dotnet-watch)      | Dosyalar değiştiğinde bir komutu çalıştıran bir dosya İzleyicisi başlatır. |

Her araç hakkında daha fazla bilgi için `dotnet <tool-name> --help`yazın.

## <a name="examples"></a>Örnekler

Yeni bir .NET Core konsol uygulaması oluşturur:

`dotnet new console`

Belirli bir uygulama için bağımlılıkları geri yükle:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Belirli bir dizinde bir proje ve onun bağımlılıklarını oluşturun:

`dotnet build`

`myapp.dll`gibi bir uygulama DLL 'SI çalıştırın:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Ortam değişkenleri

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`DOTNET_PACKAGES`

Genel paketler klasörü. Ayarlanmamışsa, varsayılan olarak UNIX veya Windows üzerinde `%userprofile%\.nuget\packages` `~/.nuget/packages`.

`DOTNET_SERVICING`

Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir. Telemetri özelliğinin (değerler `true`, `1`veya `yes` kabul edilir) devre dışı bırakmak için `true` olarak ayarlayın. Aksi takdirde, telemetri özelliklerine (değerler `false`, `0`veya `no` kabul edilir) kabul etmek için `false` olarak ayarlayın. Ayarlanmamışsa, varsayılan `false` ve telemetri özelliği etkindir.

`DOTNET_MULTILEVEL_LOOKUP`

.NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir. Ayarlanmamışsa, varsayılan olarak `true`olur. Genel konumdan çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olmak için `false` olarak ayarlayın (değerler `0` veya `false` kabul edilir). Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

`0`olarak ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır. Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`DOTNET_PACKAGES`

Birincil paket önbelleği. Ayarlanmamışsa, varsayılan olarak UNIX veya Windows üzerinde `%userprofile%\.nuget\packages` `$HOME/.nuget/packages`.

`DOTNET_SERVICING`

Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir. Telemetri özelliğinin (değerler `true`, `1`veya `yes` kabul edilir) devre dışı bırakmak için `true` olarak ayarlayın. Aksi takdirde, telemetri özelliklerine (değerler `false`, `0`veya `no` kabul edilir) kabul etmek için `false` olarak ayarlayın. Ayarlanmamışsa, varsayılan `false` ve telemetri özelliği etkindir.

`DOTNET_MULTILEVEL_LOOKUP`

.NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir. Ayarlanmamışsa, varsayılan olarak `true`olur. Genel konumdan çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olmak için `false` olarak ayarlayın (değerler `0` veya `false` kabul edilir). Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

`DOTNET_PACKAGES`

Birincil paket önbelleği. Ayarlanmamışsa, varsayılan olarak UNIX veya Windows üzerinde `%userprofile%\.nuget\packages` `$HOME/.nuget/packages`.

`DOTNET_SERVICING`

Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir. Telemetri özelliğinin (değerler `true`, `1`veya `yes` kabul edilir) devre dışı bırakmak için `true` olarak ayarlayın. Aksi takdirde, telemetri özelliklerine (değerler `false`, `0`veya `no` kabul edilir) kabul etmek için `false` olarak ayarlayın. Ayarlanmamışsa, varsayılan `false` ve telemetri özelliği etkindir.

---

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md)
