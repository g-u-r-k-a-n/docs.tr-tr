---
title: .NET Core komut satırı arabirimi (CLı) araçları
description: .NET Core komut satırı arabirimi (CLı) araçları ve özelliklerine genel bakış.
ms.date: 08/14/2017
ms.openlocfilehash: f19dcb19fb9d0203b3d3795c3fdc0b026c4c60e3
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163221"
---
# <a name="net-core-command-line-interface-cli-tools"></a><span data-ttu-id="bcfaa-103">.NET Core komut satırı arabirimi (CLı) araçları</span><span class="sxs-lookup"><span data-stu-id="bcfaa-103">.NET Core command-line interface (CLI) tools</span></span>

<span data-ttu-id="bcfaa-104">.NET Core komut satırı arabirimi (CLı), .NET uygulamaları geliştirmeye yönelik platformlar arası bir araç zinciridir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-104">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing .NET applications.</span></span> <span data-ttu-id="bcfaa-105">CLı, tümleşik geliştirme ortamları (IDN 'ler), düzenleyiciler ve derleme yöneticileri gibi daha üst düzey araçların geri kalanı olan bir temelidir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-105">The CLI is a foundation upon which higher-level tools, such as integrated development environments (IDEs), editors, and build orchestrators, can rest.</span></span>

## <a name="installation"></a><span data-ttu-id="bcfaa-106">Yükleme</span><span class="sxs-lookup"><span data-stu-id="bcfaa-106">Installation</span></span>

<span data-ttu-id="bcfaa-107">Yerel yükleyicileri kullanın veya yükleme kabuğu betikleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="bcfaa-107">Either use the native installers or use the installation shell scripts:</span></span>

- <span data-ttu-id="bcfaa-108">Yerel yükleyiciler öncelikle geliştiricinin makinelerinde kullanılır ve desteklenen her platformun yerel yükleme mekanizmasını kullanır. Örneğin, Windows üzerinde Ubuntu veya MSI paketlerinde DEB paketleri.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-108">The native installers are primarily used on developer's machines and use each supported platform's native install mechanism, for instance, DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="bcfaa-109">Bu yükleyiciler, geliştirici tarafından anında kullanılmak üzere ortamı yükler ve yapılandırır, ancak makinede yönetici ayrıcalıkları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-109">These installers install and configure the environment for immediate use by the developer but require administrative privileges on the machine.</span></span> <span data-ttu-id="bcfaa-110">Yükleme yönergelerini [.NET Core yükleme kılavuzunda](https://aka.ms/dotnetcoregs)görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-110">You can view the installation instructions in the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>
- <span data-ttu-id="bcfaa-111">Kabuk betikleri öncelikle yapı sunucularını ayarlamak için veya araçları yönetici ayrıcalıkları olmadan yüklemek istediğinizde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-111">Shell scripts are primarily used for setting up build servers or when you wish to install the tools without administrative privileges.</span></span> <span data-ttu-id="bcfaa-112">Betikleri yükleme, el ile yüklenmesi gereken makineye önkoşulları yüklemez.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-112">Install scripts don't install prerequisites on the machine, which must be installed manually.</span></span> <span data-ttu-id="bcfaa-113">Daha fazla bilgi için bkz. [komut dosyası başvurusunu install konusu](dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="bcfaa-113">For more information, see the [install script reference topic](dotnet-install-script.md).</span></span> <span data-ttu-id="bcfaa-114">Sürekli tümleştirme (CI) derleme sunucunuzda CLı 'yı ayarlama hakkında daha fazla bilgi için bkz. [.NET Core SDK ve araçları sürekli tümleştirme (CI) Içinde kullanma](using-ci-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="bcfaa-114">For information on how to set up CLI on your continuous integration (CI) build server, see [Using .NET Core SDK and tools in Continuous Integration (CI)](using-ci-with-cli.md).</span></span>

<span data-ttu-id="bcfaa-115">Varsayılan olarak, CLı yan yana (SxS) bir şekilde yüklenir. bu nedenle, CLı araçlarının birden çok sürümü tek bir makinede birlikte bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-115">By default, the CLI installs in a side-by-side (SxS) manner, so multiple versions of the CLI tools can coexist on a single machine.</span></span> <span data-ttu-id="bcfaa-116">Birden çok sürümün yüklü olduğu bir makinede hangi sürümün kullanıldığını belirleme, [sürücü](#driver) bölümünde daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-116">Determining which version is used on a machine where multiple versions are installed is explained in more detail in the [Driver](#driver) section.</span></span>

## <a name="cli-commands"></a><span data-ttu-id="bcfaa-117">CLı komutları</span><span class="sxs-lookup"><span data-stu-id="bcfaa-117">CLI commands</span></span>

<span data-ttu-id="bcfaa-118">Aşağıdaki komutlar varsayılan olarak yüklenir:</span><span class="sxs-lookup"><span data-stu-id="bcfaa-118">The following commands are installed by default:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bcfaa-119">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="bcfaa-119">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="bcfaa-120">**Temel komutlar**</span><span class="sxs-lookup"><span data-stu-id="bcfaa-120">**Basic commands**</span></span>

- [<span data-ttu-id="bcfaa-121">new</span><span class="sxs-lookup"><span data-stu-id="bcfaa-121">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="bcfaa-122">restore</span><span class="sxs-lookup"><span data-stu-id="bcfaa-122">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="bcfaa-123">derlemeyi</span><span class="sxs-lookup"><span data-stu-id="bcfaa-123">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="bcfaa-124">publish</span><span class="sxs-lookup"><span data-stu-id="bcfaa-124">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="bcfaa-125">çalışmaz</span><span class="sxs-lookup"><span data-stu-id="bcfaa-125">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="bcfaa-126">sınamanız</span><span class="sxs-lookup"><span data-stu-id="bcfaa-126">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="bcfaa-127">VSTest</span><span class="sxs-lookup"><span data-stu-id="bcfaa-127">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="bcfaa-128">pack</span><span class="sxs-lookup"><span data-stu-id="bcfaa-128">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="bcfaa-129">geçirme</span><span class="sxs-lookup"><span data-stu-id="bcfaa-129">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="bcfaa-130">temizlenemedi</span><span class="sxs-lookup"><span data-stu-id="bcfaa-130">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="bcfaa-131">sln</span><span class="sxs-lookup"><span data-stu-id="bcfaa-131">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="bcfaa-132">Yardım</span><span class="sxs-lookup"><span data-stu-id="bcfaa-132">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="bcfaa-133">saklayabilir</span><span class="sxs-lookup"><span data-stu-id="bcfaa-133">store</span></span>](dotnet-store.md)

<span data-ttu-id="bcfaa-134">**Proje değiştirme komutları**</span><span class="sxs-lookup"><span data-stu-id="bcfaa-134">**Project modification commands**</span></span>

- [<span data-ttu-id="bcfaa-135">Paket ekle</span><span class="sxs-lookup"><span data-stu-id="bcfaa-135">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="bcfaa-136">Başvuru Ekle</span><span class="sxs-lookup"><span data-stu-id="bcfaa-136">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="bcfaa-137">paketi kaldır</span><span class="sxs-lookup"><span data-stu-id="bcfaa-137">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="bcfaa-138">başvuruyu kaldır</span><span class="sxs-lookup"><span data-stu-id="bcfaa-138">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="bcfaa-139">liste başvurusu</span><span class="sxs-lookup"><span data-stu-id="bcfaa-139">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="bcfaa-140">**Gelişmiş komutlar**</span><span class="sxs-lookup"><span data-stu-id="bcfaa-140">**Advanced commands**</span></span>

- [<span data-ttu-id="bcfaa-141">NuGet silme</span><span class="sxs-lookup"><span data-stu-id="bcfaa-141">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="bcfaa-142">NuGet Yereller</span><span class="sxs-lookup"><span data-stu-id="bcfaa-142">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="bcfaa-143">NuGet gönderim</span><span class="sxs-lookup"><span data-stu-id="bcfaa-143">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="bcfaa-144">MSBUILD</span><span class="sxs-lookup"><span data-stu-id="bcfaa-144">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="bcfaa-145">DotNet install betiği</span><span class="sxs-lookup"><span data-stu-id="bcfaa-145">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bcfaa-146">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="bcfaa-146">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="bcfaa-147">**Temel komutlar**</span><span class="sxs-lookup"><span data-stu-id="bcfaa-147">**Basic commands**</span></span>

- [<span data-ttu-id="bcfaa-148">new</span><span class="sxs-lookup"><span data-stu-id="bcfaa-148">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="bcfaa-149">restore</span><span class="sxs-lookup"><span data-stu-id="bcfaa-149">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="bcfaa-150">derlemeyi</span><span class="sxs-lookup"><span data-stu-id="bcfaa-150">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="bcfaa-151">publish</span><span class="sxs-lookup"><span data-stu-id="bcfaa-151">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="bcfaa-152">çalışmaz</span><span class="sxs-lookup"><span data-stu-id="bcfaa-152">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="bcfaa-153">sınamanız</span><span class="sxs-lookup"><span data-stu-id="bcfaa-153">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="bcfaa-154">VSTest</span><span class="sxs-lookup"><span data-stu-id="bcfaa-154">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="bcfaa-155">pack</span><span class="sxs-lookup"><span data-stu-id="bcfaa-155">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="bcfaa-156">geçirme</span><span class="sxs-lookup"><span data-stu-id="bcfaa-156">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="bcfaa-157">temizlenemedi</span><span class="sxs-lookup"><span data-stu-id="bcfaa-157">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="bcfaa-158">sln</span><span class="sxs-lookup"><span data-stu-id="bcfaa-158">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="bcfaa-159">**Proje değiştirme komutları**</span><span class="sxs-lookup"><span data-stu-id="bcfaa-159">**Project modification commands**</span></span>

- [<span data-ttu-id="bcfaa-160">Paket ekle</span><span class="sxs-lookup"><span data-stu-id="bcfaa-160">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="bcfaa-161">Başvuru Ekle</span><span class="sxs-lookup"><span data-stu-id="bcfaa-161">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="bcfaa-162">paketi kaldır</span><span class="sxs-lookup"><span data-stu-id="bcfaa-162">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="bcfaa-163">başvuruyu kaldır</span><span class="sxs-lookup"><span data-stu-id="bcfaa-163">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="bcfaa-164">liste başvurusu</span><span class="sxs-lookup"><span data-stu-id="bcfaa-164">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="bcfaa-165">**Gelişmiş komutlar**</span><span class="sxs-lookup"><span data-stu-id="bcfaa-165">**Advanced commands**</span></span>

- [<span data-ttu-id="bcfaa-166">NuGet silme</span><span class="sxs-lookup"><span data-stu-id="bcfaa-166">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="bcfaa-167">NuGet Yereller</span><span class="sxs-lookup"><span data-stu-id="bcfaa-167">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="bcfaa-168">NuGet gönderim</span><span class="sxs-lookup"><span data-stu-id="bcfaa-168">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="bcfaa-169">MSBUILD</span><span class="sxs-lookup"><span data-stu-id="bcfaa-169">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="bcfaa-170">DotNet install betiği</span><span class="sxs-lookup"><span data-stu-id="bcfaa-170">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="bcfaa-171">CLı, projeleriniz için ek araçlar belirtmenize olanak tanıyan bir genişletilebilirlik modeli benimsemektedir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-171">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="bcfaa-172">Daha fazla bilgi için [.NET Core CLI genişletilebilirlik modeli](extensibility.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-172">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="bcfaa-173">Komut yapısı</span><span class="sxs-lookup"><span data-stu-id="bcfaa-173">Command structure</span></span>

<span data-ttu-id="bcfaa-174">CLı komut yapısı, [sürücüden ("DotNet")](#driver), [komuttan](#command)ve muhtemelen komut [bağımsız değişkenlerinden](#arguments) ve [seçeneklerden](#options)oluşur.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-174">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="bcfaa-175">Bu kalıbı, yeni bir konsol uygulaması oluşturma ve aşağıdaki komutlar *my_app*adlı bir dizinden yürütüldüğünde gösterildiği gibi komut satırından çalıştırma gıbı birçok CLI işlemi içinde görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="bcfaa-175">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="bcfaa-176">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="bcfaa-176">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="bcfaa-177">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="bcfaa-177">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="bcfaa-178">Sürücü</span><span class="sxs-lookup"><span data-stu-id="bcfaa-178">Driver</span></span>

<span data-ttu-id="bcfaa-179">Sürücü [DotNet](dotnet.md) olarak adlandırılır ve [çerçeveye bağlı bir uygulama](../deploying/index.md) çalıştırarak ya da bir komut yürüten iki sorumluluklara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-179">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="bcfaa-180">Çerçeveye bağımlı bir uygulama çalıştırmak için, uygulamayı sürücüden sonra belirtin, örneğin, `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-180">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="bcfaa-181">Uygulamanın DLL 'sinin bulunduğu klasörden komutu yürütürken `dotnet my_app.dll`yürütmek yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-181">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="bcfaa-182">.NET Core çalışma zamanının belirli bir sürümünü kullanmak istiyorsanız, `--fx-version <VERSION>` seçeneğini kullanın ( [DotNet komut](dotnet.md) başvurusuna bakın).</span><span class="sxs-lookup"><span data-stu-id="bcfaa-182">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="bcfaa-183">Sürücüye bir komut sağlarsanız, `dotnet.exe` CLı komutu yürütme işlemini başlatır.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-183">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="bcfaa-184">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bcfaa-184">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="bcfaa-185">İlk olarak, sürücü kullanılacak SDK sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-185">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="bcfaa-186">[' Global. json '](global-json.md)yoksa SDK 'nın kullanılabilir en son sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-186">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="bcfaa-187">Bu, makinede en son nelerin olduğuna bağlı olarak önizleme veya kararlı bir sürüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-187">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="bcfaa-188">SDK sürümü belirlendikten sonra, komutunu yürütür.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-188">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="bcfaa-189">Komut</span><span class="sxs-lookup"><span data-stu-id="bcfaa-189">Command</span></span>

<span data-ttu-id="bcfaa-190">Komut bir eylem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-190">The command performs an action.</span></span> <span data-ttu-id="bcfaa-191">Örneğin, `dotnet build` derleme kodu.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-191">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="bcfaa-192">`dotnet publish` kodu yayınlar.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-192">`dotnet publish` publishes code.</span></span> <span data-ttu-id="bcfaa-193">Komutlar bir `dotnet {command}` kuralı kullanılarak konsol uygulaması olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-193">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="bcfaa-194">Arguments</span><span class="sxs-lookup"><span data-stu-id="bcfaa-194">Arguments</span></span>

<span data-ttu-id="bcfaa-195">Komut satırında geçirdiğiniz bağımsız değişkenler çağrılan komutun bağımsız değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-195">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="bcfaa-196">Örneğin, `dotnet publish my_app.csproj`yürüttüğünüzde, `my_app.csproj` bağımsız değişkeni yayımlanacak projeyi belirtir ve `publish` komutuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-196">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="bcfaa-197">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="bcfaa-197">Options</span></span>

<span data-ttu-id="bcfaa-198">Komut satırında geçirdiğiniz seçenekler çağrılan komuta yönelik seçeneklerdir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-198">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="bcfaa-199">Örneğin `dotnet publish --output /build_output`yürüttüğünüzde, `--output` seçeneği ve değeri `publish` komutuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-199">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="bcfaa-200">Project. JSON 'dan geçiş</span><span class="sxs-lookup"><span data-stu-id="bcfaa-200">Migration from project.json</span></span>

<span data-ttu-id="bcfaa-201">*Project. JSON*tabanlı projeler oluşturmak için Preview 2 araçları 'nı kullandıysanız, sürüm araçları ile kullanmak üzere projenizi MSBuild/ *. csproj* 'a geçirme hakkında bilgi edinmek için [DotNet geçiş](dotnet-migrate.md) konusuna başvurun.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-201">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="bcfaa-202">Preview 2 araçları 'nın yayınlanmasından önce oluşturulan .NET Core projeleri için, [DNX 'ten .NET Core CLI (Project. JSON) ' den geçiş yapma bölümündeki kılavuzdan](../migration/from-dnx.md) sonra projeyi el ile güncelleştirin ve `dotnet migrate` kullanın ya da projelerinizi doğrudan yükseltin.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-202">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="bcfaa-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcfaa-203">See also</span></span>

- [<span data-ttu-id="bcfaa-204">DotNet/CLı GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="bcfaa-204">dotnet/CLI GitHub Repository</span></span>](https://github.com/dotnet/cli/)
- [<span data-ttu-id="bcfaa-205">.NET Core yükleme kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bcfaa-205">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
