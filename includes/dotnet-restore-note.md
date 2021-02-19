---
ms.openlocfilehash: f22ee4accf9ff00814fa540adce4b9ecc6686da4
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2021
ms.locfileid: "90537748"
---
<span data-ttu-id="e8b89-101">,,,, [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) Ve gibi geri yükleme gerektiren tüm komutlar tarafından örtük olarak çalıştırıldığı için çalıştırmanız gerekmez `dotnet new` `dotnet build` `dotnet run` `dotnet test` `dotnet publish` `dotnet pack` .</span><span class="sxs-lookup"><span data-stu-id="e8b89-101">You don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build`, `dotnet run`, `dotnet test`, `dotnet publish`, and `dotnet pack`.</span></span> <span data-ttu-id="e8b89-102">Örtük geri yüklemeyi devre dışı bırakmak için `--no-restore` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8b89-102">To disable implicit restore, use the `--no-restore` option.</span></span>

<span data-ttu-id="e8b89-103">`dotnet restore`Bu komut, açıkça geri yükleme işleminin, Azure DevOps Services veya derleme sistemlerindeki [sürekli tümleştirme yapıları](/azure/devops/build-release/apps/aspnet/build-aspnet-core) gibi, geri yüklemenin ne zaman gerçekleşeceğini açıkça denetmasının gerektiği bazı senaryolarda de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e8b89-103">The `dotnet restore` command is still useful in certain scenarios where explicitly restoring makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control when the restore occurs.</span></span>

<span data-ttu-id="e8b89-104">NuGet beslemelerini yönetme hakkında daha fazla bilgi için [ `dotnet restore` belgelerine](../docs/core/tools/dotnet-restore.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e8b89-104">For information about how to manage NuGet feeds, see the [`dotnet restore` documentation](../docs/core/tools/dotnet-restore.md).</span></span>
