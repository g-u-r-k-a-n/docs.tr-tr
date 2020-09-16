---
title: DotNet NuGet güncelleştirme kaynağı komutu
description: DotNet NuGet Update Source komutu, NuGet yapılandırma dosyalarınızda var olan bir kaynağı güncelleştirir.
ms.date: 03/20/2020
ms.openlocfilehash: a8658c78c095ad4b9272d97200e1d6466cbe658b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537860"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="1f6d4-103">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="1f6d4-103">dotnet nuget update source</span></span>

<span data-ttu-id="1f6d4-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="1f6d4-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1f6d4-105">Name</span><span class="sxs-lookup"><span data-stu-id="1f6d4-105">Name</span></span>

<span data-ttu-id="1f6d4-106">`dotnet nuget update source` -Bir NuGet kaynağını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1f6d4-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="1f6d4-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a><span data-ttu-id="1f6d4-108">Description</span><span class="sxs-lookup"><span data-stu-id="1f6d4-108">Description</span></span>

<span data-ttu-id="1f6d4-109">`dotnet nuget update source`Komut, NuGet yapılandırma dosyalarınızda var olan bir kaynağı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="1f6d4-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="1f6d4-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="1f6d4-111">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="1f6d4-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1f6d4-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="1f6d4-113">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-113">The NuGet configuration file.</span></span> <span data-ttu-id="1f6d4-114">Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="1f6d4-115">Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="1f6d4-116">Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="1f6d4-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="1f6d4-117">Kimliği doğrulanmış bir kaynağa bağlanırken kullanılacak parola.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="1f6d4-118">Paket kaynağının yolu.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="1f6d4-119">Parola şifrelemesini devre dışı bırakarak taşınabilir paket kaynak kimlik bilgilerinin depolanmasını mümkün.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="1f6d4-120">Kimliği doğrulanmış bir kaynağa bağlanılırken kullanılacak Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="1f6d4-121">Bu kaynak için geçerli kimlik doğrulama türlerinin virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="1f6d4-122">`basic`Sunucu ntlm veya anlaşma duyurur ise ve şirket içi Azure DevOps Server BIR Pat kullanırken, kimlik bilgilerinizin temel mekanizma kullanılarak gönderilmesi gerekiyorsa, bunu olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="1f6d4-123">Diğer geçerli değerler,,, ve içerir, `negotiate` `kerberos` `ntlm` `digest` ancak bu değerlerin yararlı olması çok düşüktür.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="1f6d4-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1f6d4-124">Examples</span></span>

- <span data-ttu-id="1f6d4-125">Şu ada sahip bir kaynağı güncelleştirin `mySource` :</span><span class="sxs-lookup"><span data-stu-id="1f6d4-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="1f6d4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f6d4-126">See also</span></span>

- [<span data-ttu-id="1f6d4-127">NuGet.config dosyalardaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="1f6d4-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="1f6d4-128">Sources komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="1f6d4-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
