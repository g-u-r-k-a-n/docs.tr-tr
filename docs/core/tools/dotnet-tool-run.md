---
title: DotNet aracı Run komutu
description: DotNet aracı Run komutu, yerel bir araç çağırır.
ms.date: 02/14/2020
ms.openlocfilehash: 116ecb61748a0ca70ed385b279b11b939748f4a8
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634161"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="cff9b-103">dotnet tool run</span><span class="sxs-lookup"><span data-stu-id="cff9b-103">dotnet tool run</span></span>

<span data-ttu-id="cff9b-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="cff9b-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cff9b-105">Name</span><span class="sxs-lookup"><span data-stu-id="cff9b-105">Name</span></span>

<span data-ttu-id="cff9b-106">`dotnet tool run` -Yerel bir araç çağırır.</span><span class="sxs-lookup"><span data-stu-id="cff9b-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cff9b-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="cff9b-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
```

## <a name="description"></a><span data-ttu-id="cff9b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cff9b-108">Description</span></span>

<span data-ttu-id="cff9b-109">`dotnet tool run`Komutu, geçerli dizinin kapsamındaki araç bildirim dosyalarını arar.</span><span class="sxs-lookup"><span data-stu-id="cff9b-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="cff9b-110">Belirtilen araca bir başvuru bulduğunda, aracı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="cff9b-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="cff9b-111">Daha fazla bilgi için bkz. [yerel bir araç çağırma](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="cff9b-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="cff9b-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="cff9b-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="cff9b-113">Çalıştırılacak aracın komut adı.</span><span class="sxs-lookup"><span data-stu-id="cff9b-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="cff9b-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="cff9b-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="cff9b-115">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="cff9b-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="cff9b-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="cff9b-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="cff9b-117">`dotnetsay`Yerel Aracı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="cff9b-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="cff9b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cff9b-118">See also</span></span>

- [<span data-ttu-id="cff9b-119">.NET araçları</span><span class="sxs-lookup"><span data-stu-id="cff9b-119">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="cff9b-120">Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="cff9b-120">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
