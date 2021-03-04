---
title: DotNet aracı install komutu
description: DotNet aracı yükleme komutu, makinenizde belirtilen .NET aracını yükler.
ms.date: 02/14/2020
ms.openlocfilehash: 5cdc0e16c964a639ebae25ac5075f186af4a9842
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105010"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="81a48-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="81a48-103">dotnet tool install</span></span>

<span data-ttu-id="81a48-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="81a48-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="81a48-105">Name</span><span class="sxs-lookup"><span data-stu-id="81a48-105">Name</span></span>

<span data-ttu-id="81a48-106">`dotnet tool install` -Makinenizde belirtilen [.NET aracını](global-tools.md) yükleme.</span><span class="sxs-lookup"><span data-stu-id="81a48-106">`dotnet tool install` - Installs the specified [.NET tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="81a48-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="81a48-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a><span data-ttu-id="81a48-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81a48-108">Description</span></span>

<span data-ttu-id="81a48-109">Bu `dotnet tool install` komut, makinenizde .NET araçları yüklemenizi sağlayan bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="81a48-109">The `dotnet tool install` command provides a way for you to install .NET tools on your machine.</span></span> <span data-ttu-id="81a48-110">Komutunu kullanmak için aşağıdaki yükleme seçeneklerinden birini belirtin:</span><span class="sxs-lookup"><span data-stu-id="81a48-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="81a48-111">Genel bir aracı varsayılan konuma yüklemek için `--global` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="81a48-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="81a48-112">Bir genel aracı özel bir konuma yüklemek için `--tool-path` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="81a48-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="81a48-113">Yerel bir araç yüklemek için `--global` ve `--tool-path` seçeneklerini atlayın.</span><span class="sxs-lookup"><span data-stu-id="81a48-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="81a48-114">**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="81a48-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="81a48-115">Veya seçeneğini belirttiğinizde, genel araçlar varsayılan olarak aşağıdaki dizinlere yüklenir `-g` `--global` :</span><span class="sxs-lookup"><span data-stu-id="81a48-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="81a48-116">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="81a48-116">OS</span></span>          | <span data-ttu-id="81a48-117">Yol</span><span class="sxs-lookup"><span data-stu-id="81a48-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="81a48-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="81a48-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="81a48-119">Windows</span><span class="sxs-lookup"><span data-stu-id="81a48-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="81a48-120">Yerel araçlar, geçerli dizinin altındaki bir *. config* dizinindeki *dotnet-tools.js* dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="81a48-120">Local tools are added to a *dotnet-tools.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="81a48-121">Henüz bir bildirim dosyası yoksa, aşağıdaki komutu çalıştırarak oluşturun:</span><span class="sxs-lookup"><span data-stu-id="81a48-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="81a48-122">Daha fazla bilgi için bkz. [yerel araç yüklemesi](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="81a48-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="81a48-123">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="81a48-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="81a48-124">Yüklenecek .NET aracını içeren NuGet paketinin adı/KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="81a48-124">Name/ID of the NuGet package that contains the .NET tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="81a48-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="81a48-125">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="81a48-126">Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="81a48-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="81a48-127">Kullanılacak NuGet yapılandırma (*nuget.config*) dosyası.</span><span class="sxs-lookup"><span data-stu-id="81a48-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="81a48-128">Aracının yükleneceği [hedef çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="81a48-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="81a48-129">.NET SDK varsayılan olarak en uygun hedef çerçeveyi seçmenizi dener.</span><span class="sxs-lookup"><span data-stu-id="81a48-129">By default, the .NET SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="81a48-130">Yüklemenin Kullanıcı genelinde olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="81a48-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="81a48-131">`--tool-path`Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="81a48-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="81a48-132">Her ikisini de atlayarak `--global` `--tool-path` bir yerel araç yüklemesi belirtilir.</span><span class="sxs-lookup"><span data-stu-id="81a48-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="81a48-133">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="81a48-133">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="81a48-134">Genel aracın yükleneceği konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="81a48-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="81a48-135">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="81a48-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="81a48-136">YOL yoksa, komut onu oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="81a48-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="81a48-137">Her ikisini de atlayarak `--global` `--tool-path` bir yerel araç yüklemesi belirtilir.</span><span class="sxs-lookup"><span data-stu-id="81a48-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="81a48-138">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="81a48-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="81a48-139">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="81a48-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="81a48-140">Yüklenecek aracın sürümü.</span><span class="sxs-lookup"><span data-stu-id="81a48-140">The version of the tool to install.</span></span> <span data-ttu-id="81a48-141">Varsayılan olarak, en son kararlı paket sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="81a48-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="81a48-142">Aracının önizlemesini veya eski sürümlerini yüklemek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="81a48-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="81a48-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="81a48-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="81a48-144">Varsayılan konumda [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel araç olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="81a48-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="81a48-145">Özel bir Windows dizininde [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel bir araç olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="81a48-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="81a48-146">[Dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) , belirli bir Linux/MacOS dizininde küresel bir araç olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="81a48-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="81a48-147">[Dotnetme](https://www.nuget.org/packages/dotnetsay/) 'nin 2.0.0 sürümünü küresel bir araç olarak kurar.</span><span class="sxs-lookup"><span data-stu-id="81a48-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="81a48-148">Geçerli dizin için [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) 'ı yerel bir araç olarak kurar.</span><span class="sxs-lookup"><span data-stu-id="81a48-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="81a48-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81a48-149">See also</span></span>

- [<span data-ttu-id="81a48-150">.NET araçları</span><span class="sxs-lookup"><span data-stu-id="81a48-150">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="81a48-151">Öğretici: .NET CLı kullanarak .NET genel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="81a48-151">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="81a48-152">Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="81a48-152">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
