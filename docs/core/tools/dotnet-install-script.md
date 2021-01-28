---
title: dotnet-install scripts
description: .NET SDK ve paylaşılan çalışma zamanı yüklemek için DotNet-install betikleri hakkında bilgi edinin.
ms.date: 09/22/2020
ms.openlocfilehash: 1904d0322774de25aeba7e7a53ab36ce135d685d
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957889"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="868f7-103">DotNet-betiklerin başvurusunu yüklemeyi</span><span class="sxs-lookup"><span data-stu-id="868f7-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="868f7-104">Name</span><span class="sxs-lookup"><span data-stu-id="868f7-104">Name</span></span>

<span data-ttu-id="868f7-105">`dotnet-install.ps1` | `dotnet-install.sh` -.NET SDK ve paylaşılan çalışma zamanı yüklemek için kullanılan betik.</span><span class="sxs-lookup"><span data-stu-id="868f7-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="868f7-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="868f7-106">Synopsis</span></span>

<span data-ttu-id="868f7-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="868f7-107">Windows:</span></span>

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

<span data-ttu-id="868f7-108">Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="868f7-108">Linux/macOS:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

<span data-ttu-id="868f7-109">Bash betiği Ayrıca PowerShell anahtarlarını okur, bu sayede PowerShell anahtarlarını Linux/macOS sistemlerinde betiği ile birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="868f7-109">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

## <a name="description"></a><span data-ttu-id="868f7-110">Description</span><span class="sxs-lookup"><span data-stu-id="868f7-110">Description</span></span>

<span data-ttu-id="868f7-111">`dotnet-install`Betikler .NET SDK 'sının .net CLI ve paylaşılan çalışma zamanını içeren yönetici olmayan bir yüklemesini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="868f7-111">The `dotnet-install` scripts perform a non-admin installation of the .NET SDK, which includes the .NET CLI and the shared runtime.</span></span> <span data-ttu-id="868f7-112">İki komut dosyası vardır:</span><span class="sxs-lookup"><span data-stu-id="868f7-112">There are two scripts:</span></span>

* <span data-ttu-id="868f7-113">Windows üzerinde çalışacak bir PowerShell betiği.</span><span class="sxs-lookup"><span data-stu-id="868f7-113">A PowerShell script that works on Windows.</span></span>
* <span data-ttu-id="868f7-114">Linux/macOS üzerinde çalışacak bir bash betiği.</span><span class="sxs-lookup"><span data-stu-id="868f7-114">A bash script that works on Linux/macOS.</span></span>

### <a name="purpose"></a><span data-ttu-id="868f7-115">Amaç</span><span class="sxs-lookup"><span data-stu-id="868f7-115">Purpose</span></span>

 <span data-ttu-id="868f7-116">Betiklerin amaçlanan kullanımı sürekli tümleştirme (CI) senaryolarına yöneliktir; burada:</span><span class="sxs-lookup"><span data-stu-id="868f7-116">The intended use of the scripts is for Continuous Integration (CI) scenarios, where:</span></span>

* <span data-ttu-id="868f7-117">SDK 'nın Kullanıcı etkileşimi olmadan ve yönetici hakları olmadan yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="868f7-117">The SDK needs to be installed without user interaction and without admin rights.</span></span>
* <span data-ttu-id="868f7-118">SDK yüklemesinin birden çok CI çalıştırması arasında kalıcı olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="868f7-118">The SDK installation doesn't need to persist across multiple CI runs.</span></span>

  <span data-ttu-id="868f7-119">Tipik olay dizisi:</span><span class="sxs-lookup"><span data-stu-id="868f7-119">The typical sequence of events:</span></span>
  * <span data-ttu-id="868f7-120">CI tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="868f7-120">CI is triggered.</span></span>
  * <span data-ttu-id="868f7-121">CI, Bu betiklerin birini kullanarak SDK 'Yı yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="868f7-121">CI installs the SDK using one of these scripts.</span></span>
  * <span data-ttu-id="868f7-122">CI işini sonlandırır ve SDK yüklemesi dahil olmak üzere geçici verileri temizler.</span><span class="sxs-lookup"><span data-stu-id="868f7-122">CI finishes its work and clears temporary data including the SDK installation.</span></span>

<span data-ttu-id="868f7-123">Geliştirme ortamı ayarlamak veya uygulamaları çalıştırmak için, bu betikler yerine yükleyicileri kullanın.</span><span class="sxs-lookup"><span data-stu-id="868f7-123">To set up a development environment or to run apps, use the installers rather than these scripts.</span></span>

### <a name="recommended-version"></a><span data-ttu-id="868f7-124">Önerilen sürüm</span><span class="sxs-lookup"><span data-stu-id="868f7-124">Recommended version</span></span>

<span data-ttu-id="868f7-125">Betiklerin kararlı sürümünü kullanmanızı öneririz:</span><span class="sxs-lookup"><span data-stu-id="868f7-125">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="868f7-126">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="868f7-126">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="868f7-127">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="868f7-127">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

### <a name="script-behavior"></a><span data-ttu-id="868f7-128">Betik davranışı</span><span class="sxs-lookup"><span data-stu-id="868f7-128">Script behavior</span></span>

<span data-ttu-id="868f7-129">Her iki komut dosyası da aynı davranışa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="868f7-129">Both scripts have the same behavior.</span></span> <span data-ttu-id="868f7-130">Bunlar, CLı derleme bırakmalarından ZIP/tarbol dosyasını indirir ve varsayılan konuma veya tarafından belirtilen bir konuma yüklemeye devam ederler `-InstallDir|--install-dir` .</span><span class="sxs-lookup"><span data-stu-id="868f7-130">They download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span>

<span data-ttu-id="868f7-131">Varsayılan olarak, yükleme betikleri SDK 'Yı indirir ve yükler.</span><span class="sxs-lookup"><span data-stu-id="868f7-131">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="868f7-132">Yalnızca paylaşılan çalışma zamanını elde etmek istiyorsanız, `-Runtime|--runtime` bağımsız değişkenini belirtin.</span><span class="sxs-lookup"><span data-stu-id="868f7-132">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="868f7-133">Komut dosyası varsayılan olarak, geçerli oturum için $PATH yüklemesi konumunu ekler.</span><span class="sxs-lookup"><span data-stu-id="868f7-133">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="868f7-134">Bağımsız değişkenini belirterek bu varsayılan davranışı geçersiz kılın `-NoPath|--no-path` .</span><span class="sxs-lookup"><span data-stu-id="868f7-134">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span> <span data-ttu-id="868f7-135">Betik, `DOTNET_ROOT` ortam değişkenini ayarladı.</span><span class="sxs-lookup"><span data-stu-id="868f7-135">The script doesn't set the `DOTNET_ROOT` environment variable.</span></span>

<span data-ttu-id="868f7-136">Betiği çalıştırmadan önce gerekli [bağımlılıkları](../install/windows.md#dependencies)yükler.</span><span class="sxs-lookup"><span data-stu-id="868f7-136">Before running the script, install the required [dependencies](../install/windows.md#dependencies).</span></span>

<span data-ttu-id="868f7-137">Bağımsız değişkenini kullanarak belirli bir sürümü yükleyebilirsiniz `-Version|--version` .</span><span class="sxs-lookup"><span data-stu-id="868f7-137">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="868f7-138">Sürüm, gibi üç bölümden oluşan bir sürüm numarası olarak belirtilmelidir `2.1.0` .</span><span class="sxs-lookup"><span data-stu-id="868f7-138">The version must be specified as a three-part version number, such as `2.1.0`.</span></span> <span data-ttu-id="868f7-139">Sürüm belirtilmemişse, komut dosyası `latest` sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="868f7-139">If the version isn't specified, the script installs the `latest` version.</span></span>

<span data-ttu-id="868f7-140">Install betikleri, Windows 'da kayıt defterini güncelleştirmez.</span><span class="sxs-lookup"><span data-stu-id="868f7-140">The install scripts do not update the registry on Windows.</span></span> <span data-ttu-id="868f7-141">Yalnızca daraltılmış ikilileri indirir ve bir klasöre kopyalar.</span><span class="sxs-lookup"><span data-stu-id="868f7-141">They just download the zipped binaries and copy them to a folder.</span></span> <span data-ttu-id="868f7-142">Kayıt defteri anahtarı değerlerinin güncelleştirilmesini istiyorsanız .NET yükleyicileri ' ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="868f7-142">If you want registry key values to be updated, use the .NET installers.</span></span>

## <a name="options"></a><span data-ttu-id="868f7-143">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="868f7-143">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="868f7-144">Yüklenecek .NET ikililerinin mimarisi.</span><span class="sxs-lookup"><span data-stu-id="868f7-144">Architecture of the .NET binaries to install.</span></span> <span data-ttu-id="868f7-145">Olası değerler şunlardır,,,, `<auto>` `amd64` `x64` `x86` `arm64` ve `arm` .</span><span class="sxs-lookup"><span data-stu-id="868f7-145">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="868f7-146">Varsayılan değer `<auto>` , çalışmakta olan işletim sistemi mimarisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="868f7-146">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="868f7-147">Yükleyicideki Azure akışına ait URL 'YI belirtir.</span><span class="sxs-lookup"><span data-stu-id="868f7-147">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="868f7-148">Bu değeri değiştirmemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="868f7-148">We recommended that you don't change this value.</span></span> <span data-ttu-id="868f7-149">`https://dotnetcli.azureedge.net/dotnet` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="868f7-149">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="868f7-150">Yükleme için kaynak kanalını belirtir.</span><span class="sxs-lookup"><span data-stu-id="868f7-150">Specifies the source channel for the installation.</span></span> <span data-ttu-id="868f7-151">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="868f7-151">The possible values are:</span></span>

  - <span data-ttu-id="868f7-152">`Current` -En güncel sürüm.</span><span class="sxs-lookup"><span data-stu-id="868f7-152">`Current` - Most current release.</span></span>
  - <span data-ttu-id="868f7-153">`LTS` -Long-Term destek kanalı (desteklenen en güncel sürüm).</span><span class="sxs-lookup"><span data-stu-id="868f7-153">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="868f7-154">Belirli bir yayını temsil eden X. Y biçimindeki iki bölümlü sürüm (örneğin, `2.1` veya `3.0` ).</span><span class="sxs-lookup"><span data-stu-id="868f7-154">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="868f7-155">Dal adı: Örneğin, `release/3.1.1xx` veya `master` (gecelik yayınlar için).</span><span class="sxs-lookup"><span data-stu-id="868f7-155">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="868f7-156">Bir önizleme kanalından sürüm yüklemek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="868f7-156">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="868f7-157">Bir kanalın adını [yükleyiciler ve Ikili dosyalar](https://github.com/dotnet/core-sdk#installers-and-binaries)bölümünde listelendiği şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="868f7-157">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="868f7-158">`LTS` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="868f7-158">The default value is `LTS`.</span></span> <span data-ttu-id="868f7-159">.NET destek kanalları hakkında daha fazla bilgi için bkz. [.net destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sayfası.</span><span class="sxs-lookup"><span data-stu-id="868f7-159">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="868f7-160">Ayarlanırsa, betik yüklemeyi gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="868f7-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="868f7-161">Bunun yerine, mevcut .NET CLı sürümünü tutarlı bir şekilde yüklemek için kullanılacak komut satırını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="868f7-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET CLI.</span></span> <span data-ttu-id="868f7-162">Örneğin, sürümünü belirtirseniz `latest` , bu komutun bir yapı betiğine göre belirleyici olarak kullanılabilmesi için belirli bir sürümle birlikte bir bağlantı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="868f7-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="868f7-163">Ayrıca, kendiniz yüklemeyi veya indirmeyi tercih ediyorsanız ikilinin konumunu da görüntüler.</span><span class="sxs-lookup"><span data-stu-id="868f7-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="868f7-164">Azure akışına eklemek için sorgu dizesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="868f7-164">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="868f7-165">Bu, URL 'nin genel olmayan BLOB depolama hesaplarını kullanmak üzere değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="868f7-165">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--help`**

  <span data-ttu-id="868f7-166">Betiğe yönelik yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="868f7-166">Prints out help for the script.</span></span> <span data-ttu-id="868f7-167">Yalnızca Bash betiği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="868f7-167">Applies only to bash script.</span></span> <span data-ttu-id="868f7-168">PowerShell için kullanın `Get-Help ./dotnet-install.ps1` .</span><span class="sxs-lookup"><span data-stu-id="868f7-168">For PowerShell, use `Get-Help ./dotnet-install.ps1`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="868f7-169">Yükleme yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="868f7-169">Specifies the installation path.</span></span> <span data-ttu-id="868f7-170">Dizin yoksa oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="868f7-170">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="868f7-171">Varsayılan değer, Windows üzerinde *%LocalAppData%\microsoft\dotnet* ve Linux/MacOS üzerinde */usr/share/DotNet* değeridir.</span><span class="sxs-lookup"><span data-stu-id="868f7-171">The default value is *%LocalAppData%\Microsoft\dotnet* on Windows and */usr/share/dotnet* on Linux/macOS.</span></span> <span data-ttu-id="868f7-172">İkili dosyalar doğrudan bu dizine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="868f7-172">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="868f7-173">SDK sürümünü belirlemekte kullanılacak bir [global.js](global-json.md) dosya için bir yol belirtir.</span><span class="sxs-lookup"><span data-stu-id="868f7-173">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="868f7-174">Dosyadaki *global.js* için bir değer olmalıdır `sdk:version` .</span><span class="sxs-lookup"><span data-stu-id="868f7-174">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="868f7-175">[Azure Content Delivery Network (CDN)](/azure/cdn/cdn-overview) ile indirmeyi devre dışı bırakır ve önbelleğe alınmamış akışı doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="868f7-175">Disables downloading from the [Azure Content Delivery Network (CDN)](/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="868f7-176">Ayarlanırsa, yükleme klasörü geçerli oturum için yola aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="868f7-176">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="868f7-177">Varsayılan olarak, komut dosyası yolu değiştirir ve bu, .NET CLı 'yı yüklemeden hemen sonra kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="868f7-177">By default, the script modifies the PATH, which makes the .NET CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="868f7-178">Ayarlanırsa, yükleyici Web istekleri yaparken proxy 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="868f7-178">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="868f7-179">(Yalnızca Windows için geçerlidir.)</span><span class="sxs-lookup"><span data-stu-id="868f7-179">(Only valid for Windows.)</span></span>

- **`-ProxyBypassList <LIST_OF_URLS>`**

  <span data-ttu-id="868f7-180">İle ayarlandıysa `ProxyAddress` , proxy 'yi atlayacak, virgülle ayrılmış URL 'lerin bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="868f7-180">If set with `ProxyAddress`, provides a list of comma-separated urls that will bypass the proxy.</span></span> <span data-ttu-id="868f7-181">(Yalnızca Windows için geçerlidir.)</span><span class="sxs-lookup"><span data-stu-id="868f7-181">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="868f7-182">Ayarlanırsa, yükleyici proxy adresini kullanırken geçerli kullanıcının kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="868f7-182">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="868f7-183">(Yalnızca Windows için geçerlidir.)</span><span class="sxs-lookup"><span data-stu-id="868f7-183">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="868f7-184">Tüm SDK 'Yı değil yalnızca paylaşılan çalışma zamanını kurar.</span><span class="sxs-lookup"><span data-stu-id="868f7-184">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="868f7-185">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="868f7-185">The possible values are:</span></span>

  - <span data-ttu-id="868f7-186">`dotnet` - `Microsoft.NETCore.App` paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="868f7-186">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="868f7-187">`aspnetcore` - `Microsoft.AspNetCore.App` paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="868f7-187">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="868f7-188">`windowsdesktop` - `Microsoft.WindowsDesktop.App` paylaşılan çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="868f7-188">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- <span data-ttu-id="868f7-189">**`--runtime-id <RID>` Kullanım dışı**</span><span class="sxs-lookup"><span data-stu-id="868f7-189">**`--runtime-id <RID>` [Deprecated]**</span></span>

  <span data-ttu-id="868f7-190">Araçların yüklendiği [çalışma zamanı tanımlayıcısını](../rid-catalog.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="868f7-190">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="868f7-191">`linux-x64`Taşınabilir Linux için kullanın.</span><span class="sxs-lookup"><span data-stu-id="868f7-191">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="868f7-192">(Yalnızca Linux/macOS için ve .NET Core 2,1 öncesi sürümler için geçerlidir.)</span><span class="sxs-lookup"><span data-stu-id="868f7-192">(Only valid for Linux/macOS and for versions earlier than .NET Core 2.1.)</span></span>

  **`--os <OPERATING_SYSTEM>`**

  <span data-ttu-id="868f7-193">Araçların yüklendiği işletim sistemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="868f7-193">Specifies the operating system for which the tools are being installed.</span></span> <span data-ttu-id="868f7-194">Olası değerler şunlardır: `osx` , `linux` , `linux-musl` , `freebsd` , `rhel.6` .</span><span class="sxs-lookup"><span data-stu-id="868f7-194">Possible values are: `osx`, `linux`, `linux-musl`, `freebsd`, `rhel.6`.</span></span> <span data-ttu-id="868f7-195">(.NET Core 2,1 ve üzeri için geçerlidir.)</span><span class="sxs-lookup"><span data-stu-id="868f7-195">(Valid for .NET Core 2.1 and later.)</span></span>

  <span data-ttu-id="868f7-196">Parametresi isteğe bağlıdır ve yalnızca komut dosyası tarafından algılanan işletim sistemini geçersiz kılmak gerektiğinde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="868f7-196">The parameter is optional and should only be used when it's required to override the operating system that is detected by the script.</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="868f7-197">Bu parametre artık kullanılmıyor ve betiğin gelecekteki bir sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="868f7-197">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="868f7-198">Önerilen alternatif, `-Runtime|--runtime` seçenektir.</span><span class="sxs-lookup"><span data-stu-id="868f7-198">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="868f7-199">Tüm SDK 'Yı değil yalnızca paylaşılan çalışma zamanı bitlerini kurar.</span><span class="sxs-lookup"><span data-stu-id="868f7-199">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="868f7-200">Bu seçenek belirtmeye eşdeğerdir `-Runtime|--runtime dotnet` .</span><span class="sxs-lookup"><span data-stu-id="868f7-200">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="868f7-201">Zaten varsa *dotnet.exe* sürümü bulunmayan dosyaları yüklemeyi atlar.</span><span class="sxs-lookup"><span data-stu-id="868f7-201">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="868f7-202">Bu yükleyici tarafından kullanılan önbelleğe alınmamış akışın URL 'sini değiştirmeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="868f7-202">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="868f7-203">Bu değeri değiştirmemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="868f7-203">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="868f7-204">Tanılama bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="868f7-204">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="868f7-205">Belirli bir derleme sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="868f7-205">Represents a specific build version.</span></span> <span data-ttu-id="868f7-206">Olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="868f7-206">The possible values are:</span></span>

  - <span data-ttu-id="868f7-207">`latest` -Kanalda en son derleme ( `-Channel` seçeneğiyle kullanılır).</span><span class="sxs-lookup"><span data-stu-id="868f7-207">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="868f7-208">Belirli bir derleme sürümünü temsil eden X. Y. Z biçimindeki üç bölümden oluşan sürüm; seçeneğinin yerini alır `-Channel` .</span><span class="sxs-lookup"><span data-stu-id="868f7-208">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="868f7-209">Örneğin: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="868f7-209">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="868f7-210">Belirtilmemişse, `-Version` Varsayılan olarak olur `latest` .</span><span class="sxs-lookup"><span data-stu-id="868f7-210">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="868f7-211">Örnekler</span><span class="sxs-lookup"><span data-stu-id="868f7-211">Examples</span></span>

- <span data-ttu-id="868f7-212">En son uzun süreli desteklenen (LTS) sürümü varsayılan konuma yükler:</span><span class="sxs-lookup"><span data-stu-id="868f7-212">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="868f7-213">Windows:</span><span class="sxs-lookup"><span data-stu-id="868f7-213">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="868f7-214">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="868f7-214">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="868f7-215">3,1 kanaldan en son sürümü belirtilen konuma yükler:</span><span class="sxs-lookup"><span data-stu-id="868f7-215">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="868f7-216">Windows:</span><span class="sxs-lookup"><span data-stu-id="868f7-216">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="868f7-217">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="868f7-217">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="868f7-218">Paylaşılan çalışma zamanının 3.0.0 sürümünü yükler:</span><span class="sxs-lookup"><span data-stu-id="868f7-218">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="868f7-219">Windows:</span><span class="sxs-lookup"><span data-stu-id="868f7-219">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="868f7-220">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="868f7-220">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="868f7-221">Bir kurumsal proxy 'nin arkasında betiği alma ve 2.1.2 'yi sürümünü yüklemeye (yalnızca Windows):</span><span class="sxs-lookup"><span data-stu-id="868f7-221">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="868f7-222">Betiği alın ve .NET CLı tek bir Oluşturucu örnekleri yükler:</span><span class="sxs-lookup"><span data-stu-id="868f7-222">Obtain script and install .NET CLI one-liner examples:</span></span>

  <span data-ttu-id="868f7-223">Windows:</span><span class="sxs-lookup"><span data-stu-id="868f7-223">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="868f7-224">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="868f7-224">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="868f7-225">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="868f7-225">See also</span></span>

- [<span data-ttu-id="868f7-226">.NET yayınları</span><span class="sxs-lookup"><span data-stu-id="868f7-226">.NET releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="868f7-227">.NET çalışma zamanı ve SDK indirme Arşivi</span><span class="sxs-lookup"><span data-stu-id="868f7-227">.NET Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)
