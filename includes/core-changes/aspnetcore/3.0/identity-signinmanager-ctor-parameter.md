---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032788"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="0b2e5-101">Kimlik: SignInManager Oluşturucusu yeni parametreyi kabul ediyor</span><span class="sxs-lookup"><span data-stu-id="0b2e5-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="0b2e5-102">ASP.NET Core 3,0 ' den başlayarak, oluşturucuya yeni bir `IUserConfirmation<TUser>` parametre eklenmiştir `SignInManager` .</span><span class="sxs-lookup"><span data-stu-id="0b2e5-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="0b2e5-103">Daha fazla bilgi için bkz. [DotNet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="0b2e5-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0b2e5-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0b2e5-104">Version introduced</span></span>

<span data-ttu-id="0b2e5-105">3,0</span><span class="sxs-lookup"><span data-stu-id="0b2e5-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0b2e5-106">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="0b2e5-106">Reason for change</span></span>

<span data-ttu-id="0b2e5-107">Değişiklik için mosyon, kimlik içinde yeni e-posta/onay akışları için destek eklemektir.</span><span class="sxs-lookup"><span data-stu-id="0b2e5-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0b2e5-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0b2e5-108">Recommended action</span></span>

<span data-ttu-id="0b2e5-109">El ile oluşturuyorsanız `SignInManager` , `IUserConfirmation` sağlama veya bağımlılık ekleme için bir uygulama sağlayın.</span><span class="sxs-lookup"><span data-stu-id="0b2e5-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="0b2e5-110">Kategori</span><span class="sxs-lookup"><span data-stu-id="0b2e5-110">Category</span></span>

<span data-ttu-id="0b2e5-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0b2e5-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0b2e5-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0b2e5-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
