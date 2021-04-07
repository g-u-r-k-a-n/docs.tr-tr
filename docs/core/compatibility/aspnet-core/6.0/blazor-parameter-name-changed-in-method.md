---
title: 'Son değişiklik: Blazor: parametre adı, talep Estimagefileasync yönteminde değiştirildi'
description: "Blazor başlıklı ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin: parametre adı, karşılandığından Estimagefileasync yönteminde değiştirildi"
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 61518ba246c1d390861261ecb5a9f18a5695c1fd
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496989"
---
# <a name="blazor-parameter-name-changed-in-requestimagefileasync-method"></a><span data-ttu-id="74713-103">Blazor: parametre adı, talep Estimagefileasync yönteminde değiştirildi</span><span class="sxs-lookup"><span data-stu-id="74713-103">Blazor: Parameter name changed in RequestImageFileAsync method</span></span>

<span data-ttu-id="74713-104">`RequestImageFileAsync`Yöntemin `maxWith` parametresi olarak yeniden adlandırıldı `maxWith` `maxWidth` .</span><span class="sxs-lookup"><span data-stu-id="74713-104">The `RequestImageFileAsync` method's `maxWith` parameter was renamed from `maxWith` to `maxWidth`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="74713-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="74713-105">Version introduced</span></span>

<span data-ttu-id="74713-106">6,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="74713-106">6.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="74713-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="74713-107">Old behavior</span></span>

<span data-ttu-id="74713-108">Parametre adı yazılmış `maxWith` .</span><span class="sxs-lookup"><span data-stu-id="74713-108">The parameter name is spelled `maxWith`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="74713-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="74713-109">New behavior</span></span>

<span data-ttu-id="74713-110">Parametre adı yazılmış `maxWidth` .</span><span class="sxs-lookup"><span data-stu-id="74713-110">The parameter name is spelled `maxWidth`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="74713-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="74713-111">Reason for change</span></span>

<span data-ttu-id="74713-112">Özgün parametre adı bir yazım hatası idi.</span><span class="sxs-lookup"><span data-stu-id="74713-112">The original parameter name was a typographical error.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="74713-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="74713-113">Recommended action</span></span>

<span data-ttu-id="74713-114">API 'de adlandırılmış parametreler kullanıyorsanız `RequestImageFile` , `maxWith` parametre adını olarak güncelleştirin `maxWidth` .</span><span class="sxs-lookup"><span data-stu-id="74713-114">If you're using named parameters in the `RequestImageFile` API, update the `maxWith` parameter name to `maxWidth`.</span></span> <span data-ttu-id="74713-115">Aksi takdirde, hiçbir değişiklik gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="74713-115">Otherwise, no change is necessary.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="74713-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="74713-116">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync`

-->
