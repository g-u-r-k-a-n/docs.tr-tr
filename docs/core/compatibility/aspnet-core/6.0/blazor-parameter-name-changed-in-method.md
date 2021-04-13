---
title: 'Son değişiklik: Blazor : parametre adı, talep Estimagefileasync yönteminde değiştirildi'
description: "ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin Blazor : talep tahmini Gefileasync yönteminde parametre adı değiştirildi"
no-loc:
- Blazor
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 06fe2b0cff17630e09da3f80c506684f1b26e9d4
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107292281"
---
# <a name="blazor-parameter-name-changed-in-requestimagefileasync-method"></a><span data-ttu-id="6718e-103">Blazor: Parametre adı, karşılandığından Estimagefileasync yönteminde değiştirildi</span><span class="sxs-lookup"><span data-stu-id="6718e-103">Blazor: Parameter name changed in RequestImageFileAsync method</span></span>

<span data-ttu-id="6718e-104">`RequestImageFileAsync`Yöntemin `maxWith` parametresi olarak yeniden adlandırıldı `maxWith` `maxWidth` .</span><span class="sxs-lookup"><span data-stu-id="6718e-104">The `RequestImageFileAsync` method's `maxWith` parameter was renamed from `maxWith` to `maxWidth`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="6718e-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="6718e-105">Version introduced</span></span>

<span data-ttu-id="6718e-106">ASP.NET Core 6,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="6718e-106">ASP.NET Core 6.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="6718e-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="6718e-107">Old behavior</span></span>

<span data-ttu-id="6718e-108">Parametre adı yazılmış `maxWith` .</span><span class="sxs-lookup"><span data-stu-id="6718e-108">The parameter name is spelled `maxWith`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="6718e-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="6718e-109">New behavior</span></span>

<span data-ttu-id="6718e-110">Parametre adı yazılmış `maxWidth` .</span><span class="sxs-lookup"><span data-stu-id="6718e-110">The parameter name is spelled `maxWidth`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="6718e-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="6718e-111">Reason for change</span></span>

<span data-ttu-id="6718e-112">Özgün parametre adı bir yazım hatası idi.</span><span class="sxs-lookup"><span data-stu-id="6718e-112">The original parameter name was a typographical error.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="6718e-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6718e-113">Recommended action</span></span>

<span data-ttu-id="6718e-114">API 'de adlandırılmış parametreler kullanıyorsanız `RequestImageFile` , `maxWith` parametre adını olarak güncelleştirin `maxWidth` .</span><span class="sxs-lookup"><span data-stu-id="6718e-114">If you're using named parameters in the `RequestImageFile` API, update the `maxWith` parameter name to `maxWidth`.</span></span> <span data-ttu-id="6718e-115">Aksi takdirde, hiçbir değişiklik gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6718e-115">Otherwise, no change is necessary.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="6718e-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6718e-116">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync`

-->
