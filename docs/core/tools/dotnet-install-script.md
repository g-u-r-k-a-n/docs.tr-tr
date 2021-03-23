---
title: dotnet-install scripts
description: .NET SDK ve paylaşılan çalışma zamanı yüklemek için DotNet-install betikleri hakkında bilgi edinin.
ms.date: 09/22/2020
ms.openlocfilehash: 45b5a15bdbaa3f3167dd434e2600e33b69dc9b85
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875167"
---
# <a name="dotnet-install-scripts-reference"></a>DotNet-betiklerin başvurusunu yüklemeyi

## <a name="name"></a>Name

`dotnet-install.ps1` | `dotnet-install.sh` -.NET SDK ve paylaşılan çalışma zamanı yüklemek için kullanılan betik.

## <a name="synopsis"></a>Özeti

Windows:

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress] [-ProxyBypassList <LIST_OF_URLS>]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

Get-Help ./dotnet-install.ps1
```

Linux/macOS:

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

Bash betiği Ayrıca PowerShell anahtarlarını okur, bu sayede PowerShell anahtarlarını Linux/macOS sistemlerinde betiği ile birlikte kullanabilirsiniz.

## <a name="description"></a>Açıklama

`dotnet-install`Betikler .NET SDK 'sının .net CLI ve paylaşılan çalışma zamanını içeren yönetici olmayan bir yüklemesini gerçekleştirir. İki komut dosyası vardır:

* Windows üzerinde çalışacak bir PowerShell betiği.
* Linux/macOS üzerinde çalışacak bir bash betiği.

> [!NOTE]
> .NET telemetri verilerini toplar. Daha fazla bilgi edinmek ve devre dışı bırakmak için bkz. [.NET SDK telemetrisi](telemetry.md).

### <a name="purpose"></a>Amaç

 Betiklerin amaçlanan kullanımı sürekli tümleştirme (CI) senaryolarına yöneliktir; burada:

* SDK 'nın Kullanıcı etkileşimi olmadan ve yönetici hakları olmadan yüklenmesi gerekir.
* SDK yüklemesinin birden çok CI çalıştırması arasında kalıcı olması gerekmez.

  Tipik olay dizisi:
  * CI tetiklenir.
  * CI, Bu betiklerin birini kullanarak SDK 'Yı yüklüyor.
  * CI işini sonlandırır ve SDK yüklemesi dahil olmak üzere geçici verileri temizler.

Geliştirme ortamı ayarlamak veya uygulamaları çalıştırmak için, bu betikler yerine yükleyicileri kullanın.

### <a name="recommended-version"></a>Önerilen sürüm

Betiklerin kararlı sürümünü kullanmanızı öneririz:

- Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh>
- PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1>

### <a name="script-behavior"></a>Betik davranışı

Her iki komut dosyası da aynı davranışa sahiptir. Bunlar, CLı derleme bırakmalarından ZIP/tarbol dosyasını indirir ve varsayılan konuma veya tarafından belirtilen bir konuma yüklemeye devam ederler `-InstallDir|--install-dir` .

Varsayılan olarak, yükleme betikleri SDK 'Yı indirir ve yükler. Yalnızca paylaşılan çalışma zamanını elde etmek istiyorsanız, `-Runtime|--runtime` bağımsız değişkenini belirtin.

Komut dosyası varsayılan olarak, geçerli oturum için $PATH yüklemesi konumunu ekler. Bağımsız değişkenini belirterek bu varsayılan davranışı geçersiz kılın `-NoPath|--no-path` . Betik, `DOTNET_ROOT` ortam değişkenini ayarladı.

Betiği çalıştırmadan önce gerekli [bağımlılıkları](../install/windows.md#dependencies)yükler.

Bağımsız değişkenini kullanarak belirli bir sürümü yükleyebilirsiniz `-Version|--version` . Sürüm, gibi üç bölümden oluşan bir sürüm numarası olarak belirtilmelidir `2.1.0` . Sürüm belirtilmemişse, komut dosyası `latest` sürümü yüklenir.

Install betikleri, Windows 'da kayıt defterini güncelleştirmez. Yalnızca daraltılmış ikilileri indirir ve bir klasöre kopyalar. Kayıt defteri anahtarı değerlerinin güncelleştirilmesini istiyorsanız .NET yükleyicileri ' ni kullanın.

## <a name="options"></a>Seçenekler

- **`-Architecture|--architecture <ARCHITECTURE>`**

  Yüklenecek .NET ikililerinin mimarisi. Olası değerler şunlardır,,,, `<auto>` `amd64` `x64` `x86` `arm64` ve `arm` . Varsayılan değer `<auto>` , çalışmakta olan işletim sistemi mimarisini temsil eder.

- **`-AzureFeed|--azure-feed`**

  Yükleyicideki Azure akışına ait URL 'YI belirtir. Bu değeri değiştirmemenizi öneririz. `https://dotnetcli.azureedge.net/dotnet` varsayılan değerdir.

- **`-Channel|--channel <CHANNEL>`**

  Yükleme için kaynak kanalını belirtir. Olası değerler şunlardır:

  - `Current` -En güncel sürüm.
  - `LTS` -Long-Term destek kanalı (desteklenen en güncel sürüm).
  - Belirli bir yayını temsil eden X. Y biçimindeki iki bölümlü sürüm (örneğin, `2.1` veya `3.0` ).
  - Dal adı: Örneğin, `release/3.1.1xx` veya `master` (gecelik yayınlar için). Bir önizleme kanalından sürüm yüklemek için bu seçeneği kullanın. Bir kanalın adını [yükleyiciler ve Ikili dosyalar](https://github.com/dotnet/core-sdk#installers-and-binaries)bölümünde listelendiği şekilde kullanın.

  `LTS` varsayılan değerdir. .NET destek kanalları hakkında daha fazla bilgi için bkz. [.net destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sayfası.

- **`-DryRun|--dry-run`**

  Ayarlanırsa, betik yüklemeyi gerçekleştirmez. Bunun yerine, mevcut .NET CLı sürümünü tutarlı bir şekilde yüklemek için kullanılacak komut satırını görüntüler. Örneğin, sürümünü belirtirseniz `latest` , bu komutun bir yapı betiğine göre belirleyici olarak kullanılabilmesi için belirli bir sürümle birlikte bir bağlantı görüntüler. Ayrıca, kendiniz yüklemeyi veya indirmeyi tercih ediyorsanız ikilinin konumunu da görüntüler.

- **`-FeedCredential|--feed-credential`**

  Azure akışına eklemek için sorgu dizesi olarak kullanılır. Bu, URL 'nin genel olmayan BLOB depolama hesaplarını kullanmak üzere değiştirilmesini sağlar.

- **`--help`**

  Betiğe yönelik yardım yazdırır. Yalnızca Bash betiği için geçerlidir. PowerShell için kullanın `Get-Help ./dotnet-install.ps1` .

- **`-InstallDir|--install-dir <DIRECTORY>`**

  Yükleme yolunu belirtir. Dizin yoksa oluşturulur. Varsayılan değer, Windows üzerinde *%LocalAppData%\microsoft\dotnet* ve Linux/MacOS üzerinde */usr/share/DotNet* değeridir. İkili dosyalar doğrudan bu dizine yerleştirilir.

- **`-JSonFile|--jsonfile <JSONFILE>`**

  SDK sürümünü belirlemekte kullanılacak bir [global.js](global-json.md) dosya için bir yol belirtir. Dosyadaki *global.js* için bir değer olmalıdır `sdk:version` .

- **`-NoCdn|--no-cdn`**

  [Azure Content Delivery Network (CDN)](/azure/cdn/cdn-overview) ile indirmeyi devre dışı bırakır ve önbelleğe alınmamış akışı doğrudan kullanır.

- **`-NoPath|--no-path`**

  Ayarlanırsa, yükleme klasörü geçerli oturum için yola aktarılmaz. Varsayılan olarak, komut dosyası yolu değiştirir ve bu, .NET CLı 'yı yüklemeden hemen sonra kullanılabilir hale getirir.

- **`-ProxyAddress`**

  Ayarlanırsa, yükleyici Web istekleri yaparken proxy 'yi kullanır. (Yalnızca Windows için geçerlidir.)

- **`-ProxyBypassList <LIST_OF_URLS>`**

  İle ayarlandıysa `ProxyAddress` , proxy 'yi atlayacak, virgülle ayrılmış URL 'lerin bir listesini sağlar. (Yalnızca Windows için geçerlidir.)

- **`ProxyUseDefaultCredentials`**

  Ayarlanırsa, yükleyici proxy adresini kullanırken geçerli kullanıcının kimlik bilgilerini kullanır. (Yalnızca Windows için geçerlidir.)

- **`-Runtime|--runtime <RUNTIME>`**

  Tüm SDK 'Yı değil yalnızca paylaşılan çalışma zamanını kurar. Olası değerler şunlardır:

  - `dotnet` - `Microsoft.NETCore.App` paylaşılan çalışma zamanı.
  - `aspnetcore` - `Microsoft.AspNetCore.App` paylaşılan çalışma zamanı.
  - `windowsdesktop` - `Microsoft.WindowsDesktop.App` paylaşılan çalışma zamanı.

- **`--runtime-id <RID>` Kullanım dışı**

  Araçların yüklendiği [çalışma zamanı tanımlayıcısını](../rid-catalog.md) belirtir. `linux-x64`Taşınabilir Linux için kullanın. (Yalnızca Linux/macOS için ve .NET Core 2,1 öncesi sürümler için geçerlidir.)

  **`--os <OPERATING_SYSTEM>`**

  Araçların yüklendiği işletim sistemini belirtir. Olası değerler şunlardır: `osx` , `linux` , `linux-musl` , `freebsd` , `rhel.6` . (.NET Core 2,1 ve üzeri için geçerlidir.)

  Parametresi isteğe bağlıdır ve yalnızca komut dosyası tarafından algılanan işletim sistemini geçersiz kılmak gerektiğinde kullanılmalıdır.

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > Bu parametre artık kullanılmıyor ve betiğin gelecekteki bir sürümünde kaldırılabilir. Önerilen alternatif, `-Runtime|--runtime` seçenektir.

  Tüm SDK 'Yı değil yalnızca paylaşılan çalışma zamanı bitlerini kurar. Bu seçenek belirtmeye eşdeğerdir `-Runtime|--runtime dotnet` .

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  Zaten varsa *dotnet.exe* sürümü bulunmayan dosyaları yüklemeyi atlar.

- **`-UncachedFeed|--uncached-feed`**

  Bu yükleyici tarafından kullanılan önbelleğe alınmamış akışın URL 'sini değiştirmeye izin verir. Bu değeri değiştirmemenizi öneririz.

- **`-Verbose|--verbose`**

  Tanılama bilgilerini görüntüler.

- **`-Version|--version <VERSION>`**

  Belirli bir derleme sürümünü temsil eder. Olası değerler şunlardır:

  - `latest` -Kanalda en son derleme ( `-Channel` seçeneğiyle kullanılır).
  - Belirli bir derleme sürümünü temsil eden X. Y. Z biçimindeki üç bölümden oluşan sürüm; seçeneğinin yerini alır `-Channel` . Örneğin: `2.0.0-preview2-006120`.

  Belirtilmemişse, `-Version` Varsayılan olarak olur `latest` .

## <a name="examples"></a>Örnekler

- En son uzun süreli desteklenen (LTS) sürümü varsayılan konuma yükler:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- 3,1 kanaldan en son sürümü belirtilen konuma yükler:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- Paylaşılan çalışma zamanının 3.0.0 sürümünü yükler:

  Windows:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- Bir kurumsal proxy 'nin arkasında betiği alma ve 2.1.2 'yi sürümünü yüklemeye (yalnızca Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Betiği alın ve .NET CLı tek bir Oluşturucu örnekleri yükler:

  Windows:

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET yayınları](https://github.com/dotnet/core/releases)
- [.NET çalışma zamanı ve SDK indirme Arşivi](https://github.com/dotnet/core/blob/main/release-notes/download-archive.md)
