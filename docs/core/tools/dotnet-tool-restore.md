---
title: DotNet aracı geri yükleme komutu
description: DotNet aracı geri yükleme komutu, makinenizde geçerli dizin için kapsamdaki .NET yerel araçları 'nı yükler.
ms.date: 02/14/2020
ms.openlocfilehash: 3425bc6b78fd53f578c209013f83b006305dbb81
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242935"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="d891e-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="d891e-103">dotnet tool restore</span></span>

<span data-ttu-id="d891e-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="d891e-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d891e-105">Adı</span><span class="sxs-lookup"><span data-stu-id="d891e-105">Name</span></span>

<span data-ttu-id="d891e-106">`dotnet tool restore` -Geçerli dizin için kapsamdaki .NET yerel araçlarını yükleme.</span><span class="sxs-lookup"><span data-stu-id="d891e-106">`dotnet tool restore` - Installs the .NET local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d891e-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="d891e-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a><span data-ttu-id="d891e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d891e-108">Description</span></span>

<span data-ttu-id="d891e-109">`dotnet tool restore`Komutu, geçerli dizinin kapsamındaki araç bildirim dosyasını bulur ve içinde listelenen araçları kurar.</span><span class="sxs-lookup"><span data-stu-id="d891e-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="d891e-110">Bildirim dosyaları hakkında daha fazla bilgi için bkz. [yerel araç yükleyip](global-tools.md#install-a-local-tool) [yerel bir araç çağırma](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="d891e-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="options"></a><span data-ttu-id="d891e-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d891e-111">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="d891e-112">Kullanılacak NuGet yapılandırma (*nuget.config*) dosyası.</span><span class="sxs-lookup"><span data-stu-id="d891e-112">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="d891e-113">Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="d891e-113">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="d891e-114">Bildirim dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="d891e-114">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="d891e-115">Paralel olarak birden çok projenin geri yüklenmesini engelleyin.</span><span class="sxs-lookup"><span data-stu-id="d891e-115">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="d891e-116">Paket kaynağı başarısızlıklarını uyarı olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="d891e-116">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="d891e-117">Paketleri ve http isteklerini önbelleğe vermeyin.</span><span class="sxs-lookup"><span data-stu-id="d891e-117">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="d891e-118">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya).</span><span class="sxs-lookup"><span data-stu-id="d891e-118">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="d891e-119">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d891e-119">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="d891e-120">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d891e-120">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d891e-121">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="d891e-121">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="d891e-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="d891e-122">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="d891e-123">Geçerli dizin için yerel araçları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="d891e-123">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="d891e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d891e-124">See also</span></span>

- [<span data-ttu-id="d891e-125">.NET araçları</span><span class="sxs-lookup"><span data-stu-id="d891e-125">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="d891e-126">Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="d891e-126">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
