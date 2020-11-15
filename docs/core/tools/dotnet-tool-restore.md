---
title: DotNet aracı geri yükleme komutu
description: DotNet aracı geri yükleme komutu, makinenizde geçerli dizin için kapsamdaki .NET yerel araçları 'nı yükler.
ms.date: 02/14/2020
ms.openlocfilehash: 1b7fd10102f2c957b3eb235f6897b60bc8ca9c07
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634278"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="e9c8c-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="e9c8c-103">dotnet tool restore</span></span>

<span data-ttu-id="e9c8c-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="e9c8c-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e9c8c-105">Name</span><span class="sxs-lookup"><span data-stu-id="e9c8c-105">Name</span></span>

<span data-ttu-id="e9c8c-106">`dotnet tool restore` -Makinenizde geçerli dizin için kapsamdaki .NET yerel araçları yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e9c8c-106">`dotnet tool restore` - Installs on your machine the .NET local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e9c8c-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="e9c8c-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a><span data-ttu-id="e9c8c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9c8c-108">Description</span></span>

<span data-ttu-id="e9c8c-109">`dotnet tool restore`Komutu, geçerli dizinin kapsamındaki araç bildirim dosyasını bulur ve içinde listelenen araçları kurar.</span><span class="sxs-lookup"><span data-stu-id="e9c8c-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="e9c8c-110">Bildirim dosyaları hakkında daha fazla bilgi için bkz. [yerel araç yükleyip](global-tools.md#install-a-local-tool) [yerel bir araç çağırma](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="e9c8c-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="options"></a><span data-ttu-id="e9c8c-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e9c8c-111">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="e9c8c-112">Kullanılacak NuGet yapılandırma ( *nuget.config* ) dosyası.</span><span class="sxs-lookup"><span data-stu-id="e9c8c-112">The NuGet configuration ( *nuget.config* ) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="e9c8c-113">Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="e9c8c-113">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="e9c8c-114">Bildirim dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="e9c8c-114">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="e9c8c-115">Paralel olarak birden çok projenin geri yüklenmesini engelleyin.</span><span class="sxs-lookup"><span data-stu-id="e9c8c-115">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="e9c8c-116">Paket kaynağı başarısızlıklarını uyarı olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="e9c8c-116">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="e9c8c-117">Paketleri ve http isteklerini önbelleğe vermeyin.</span><span class="sxs-lookup"><span data-stu-id="e9c8c-117">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="e9c8c-118">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya).</span><span class="sxs-lookup"><span data-stu-id="e9c8c-118">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="e9c8c-119">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e9c8c-119">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e9c8c-120">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e9c8c-120">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e9c8c-121">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="e9c8c-121">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="e9c8c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9c8c-122">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="e9c8c-123">Geçerli dizin için yerel araçları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="e9c8c-123">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9c8c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9c8c-124">See also</span></span>

- [<span data-ttu-id="e9c8c-125">.NET araçları</span><span class="sxs-lookup"><span data-stu-id="e9c8c-125">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="e9c8c-126">Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="e9c8c-126">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
