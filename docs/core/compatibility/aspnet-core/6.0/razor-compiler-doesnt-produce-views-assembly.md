---
title: 'Son değişiklik: Razor : derleyici artık tek bir derleme oluşturuyor'
description: ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin ve Razor derleyicinin artık iki ayrı derleme oluşturmak için iki adımlı derleme işlemi kullanmaz.
no-loc:
- Razor
ms.date: 04/08/2021
ms.openlocfilehash: 8b6817563c4670aebfe681d5f24c8e309d2500ad
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299296"
---
# <a name="razor-compiler-no-longer-produces-a-views-assembly"></a><span data-ttu-id="16fe0-103">Razor: Derleyici artık bir görünümler derlemesi üretmez</span><span class="sxs-lookup"><span data-stu-id="16fe0-103">Razor: Compiler no longer produces a Views assembly</span></span>

<span data-ttu-id="16fe0-104">RazorDerleyici artık bir uygulamada tanımlanan cshtml görünümlerini içeren ayrı bir *Views.dll* dosyası üretmez.</span><span class="sxs-lookup"><span data-stu-id="16fe0-104">The Razor compiler no longer produces a separate *Views.dll* file that contains the CSHTML views defined in an application.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="16fe0-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="16fe0-105">Version introduced</span></span>

<span data-ttu-id="16fe0-106">ASP.NET Core 6,0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="16fe0-106">ASP.NET Core 6.0 Preview 3</span></span>

## <a name="old-behavior"></a><span data-ttu-id="16fe0-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="16fe0-107">Old behavior</span></span>

<span data-ttu-id="16fe0-108">Önceki sürümlerde Razor derleyici, iki dosya üreten iki adımlı bir derleme işlemi kullanır:</span><span class="sxs-lookup"><span data-stu-id="16fe0-108">In previous versions, the Razor compiler utilizes a two-step compilation process that produces two files:</span></span>

- <span data-ttu-id="16fe0-109">Uygulama türlerini içeren bir ana *AppName.dll* derlemesi.</span><span class="sxs-lookup"><span data-stu-id="16fe0-109">A main *AppName.dll* assembly that contains application types.</span></span>
- <span data-ttu-id="16fe0-110">Uygulamada tanımlanan oluşturulmuş görünümleri içeren bir *AppName.Views.dll* derlemesi.</span><span class="sxs-lookup"><span data-stu-id="16fe0-110">An *AppName.Views.dll* assembly that contains the generated views that are defined in the app.</span></span> <span data-ttu-id="16fe0-111">Oluşturulan görünüm türleri `public` ve `AspNetCore` ad alanı altında.</span><span class="sxs-lookup"><span data-stu-id="16fe0-111">Generated view types are `public` and under the `AspNetCore` namespace.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="16fe0-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="16fe0-112">New behavior</span></span>

<span data-ttu-id="16fe0-113">Hem görünümler hem de uygulama türleri tek bir *AppName.dll* derlemesine dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="16fe0-113">Both views and application types are included in a single *AppName.dll* assembly.</span></span> <span data-ttu-id="16fe0-114">Görünüm türleri erişilebilirlik değiştiricilerine sahiptir `internal` ve `sealed` Varsayılan olarak `AspNetCoreGeneratedDocument` ad alanı altında bulunur.</span><span class="sxs-lookup"><span data-stu-id="16fe0-114">View types have the accessibility modifiers `internal` and `sealed`, by default, and are included under the `AspNetCoreGeneratedDocument` namespace.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="16fe0-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="16fe0-115">Reason for change</span></span>

<span data-ttu-id="16fe0-116">İki adımlı derleme işlemini kaldırma:</span><span class="sxs-lookup"><span data-stu-id="16fe0-116">Removing the two-step compilation process:</span></span>

* <span data-ttu-id="16fe0-117">Görünümleri kullanan uygulamalar için derleme performansını geliştirir Razor .</span><span class="sxs-lookup"><span data-stu-id="16fe0-117">Improves build performance for applications that use Razor views.</span></span>
* <span data-ttu-id="16fe0-118">RazorGörünümlerin Visual Studio için "sık yükleme" deneyimine katılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="16fe0-118">Allows Razor views to participate in the "hot reload" experience for Visual Studio.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="16fe0-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="16fe0-119">Recommended action</span></span>

<span data-ttu-id="16fe0-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="16fe0-120">None.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="16fe0-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="16fe0-121">Affected APIs</span></span>

<span data-ttu-id="16fe0-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="16fe0-122">None.</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
