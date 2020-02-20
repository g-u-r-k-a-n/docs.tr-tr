---
title: DotNet yardım komutu
description: DotNet yardım komutu, belirtilen komut için çevrimiçi daha ayrıntılı belgeler gösterir.
ms.date: 02/14/2020
ms.openlocfilehash: f5d9221ae18653451a3bf97dc82fae396ae4e288
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503720"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="0786b-103">DotNet yardım başvurusu</span><span class="sxs-lookup"><span data-stu-id="0786b-103">dotnet help reference</span></span>

<span data-ttu-id="0786b-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="0786b-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0786b-105">Adı</span><span class="sxs-lookup"><span data-stu-id="0786b-105">Name</span></span>

<span data-ttu-id="0786b-106">`dotnet help`-belirtilen komut için çevrimiçi daha ayrıntılı belgeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="0786b-106">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0786b-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="0786b-107">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="0786b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0786b-108">Description</span></span>

<span data-ttu-id="0786b-109">`dotnet help` komutu, docs.microsoft.com adresinde belirtilen komutla ilgili daha ayrıntılı bilgi için başvuru sayfasını açar.</span><span class="sxs-lookup"><span data-stu-id="0786b-109">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="0786b-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="0786b-110">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="0786b-111">.NET Core CLI komutunun adı.</span><span class="sxs-lookup"><span data-stu-id="0786b-111">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="0786b-112">Geçerli CLı komutlarının bir listesi için bkz. [CLI komutları](index.md#cli-commands).</span><span class="sxs-lookup"><span data-stu-id="0786b-112">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="0786b-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="0786b-113">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="0786b-114">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0786b-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="0786b-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0786b-115">Examples</span></span>

- <span data-ttu-id="0786b-116">[DotNet yeni](dotnet-new.md) komutunun belgeler sayfasını açar:</span><span class="sxs-lookup"><span data-stu-id="0786b-116">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

  ```dotnetcli
  dotnet help new
  ```
