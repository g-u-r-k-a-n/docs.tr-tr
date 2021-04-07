---
title: 'Son değişiklik: ara yazılım: özel durum Işleyici ara yazılımı, işleyici bulunmazsa özgün özel durum oluşturur'
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: özel durum Işleyici ara yazılımı, işleyici bulunmazsa özgün özel durum oluşturur"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c28e09e544ac01c04a23fb7d2e73f3fdc242e9cd
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497950"
---
# <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a><span data-ttu-id="d105b-103">Ara yazılım: özel durum Işleyicisi ara yazılımı, işleyici bulunmazsa özgün özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="d105b-103">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>

<span data-ttu-id="d105b-104">5,0 ASP.NET Core önce, [özel durum Işleyici ara yazılımı](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) yapılandırılmış özel durum işleyicisini bir özel durum oluştuğunda yürütür.</span><span class="sxs-lookup"><span data-stu-id="d105b-104">Before ASP.NET Core 5.0, the [Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) executes the configured exception handler when an exception has occurred.</span></span> <span data-ttu-id="d105b-105">Aracılığıyla yapılandırılan özel durum işleyicisi bulunamazsa, <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> BIR HTTP 404 yanıtı üretilir.</span><span class="sxs-lookup"><span data-stu-id="d105b-105">If the exception handler, configured via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath>, can't be found, an HTTP 404 response is produced.</span></span> <span data-ttu-id="d105b-106">Yanıt şu şekilde yanıltıcıdır:</span><span class="sxs-lookup"><span data-stu-id="d105b-106">The response is misleading in that it:</span></span>

* <span data-ttu-id="d105b-107">Kullanıcı hatası gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="d105b-107">Seems to be a user error.</span></span>
* <span data-ttu-id="d105b-108">Sunucu üzerinde bir özel durumun gerçekleştiği gerçeğini gizler.</span><span class="sxs-lookup"><span data-stu-id="d105b-108">Obscures the fact that an exception occurred on the server.</span></span>

<span data-ttu-id="d105b-109">ASP.NET Core 5,0 ' deki yanıltıcı hatayı gidermek için, `ExceptionHandlerMiddleware` özel durum işleyicisi bulunamazsa özgün özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d105b-109">To address the misleading error in ASP.NET Core 5.0, the `ExceptionHandlerMiddleware` throws the original exception if the exception handler can't be found.</span></span> <span data-ttu-id="d105b-110">Sonuç olarak, sunucu tarafından bir HTTP 500 yanıtı üretilir.</span><span class="sxs-lookup"><span data-stu-id="d105b-110">As a result, an HTTP 500 response is produced by the server.</span></span> <span data-ttu-id="d105b-111">Yanıt, oluşan hata ayıklanırken sunucu günlüklerinde İncelenme daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d105b-111">The response will be easier to examine in the server logs when debugging the error that occurred.</span></span>

<span data-ttu-id="d105b-112">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 25288](https://github.com/dotnet/aspnetcore/issues/25288).</span><span class="sxs-lookup"><span data-stu-id="d105b-112">For discussion, see GitHub issue [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d105b-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d105b-113">Version introduced</span></span>

<span data-ttu-id="d105b-114">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="d105b-114">5.0 RC 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="d105b-115">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="d105b-115">Old behavior</span></span>

<span data-ttu-id="d105b-116">Yapılandırılmış özel durum işleyicisi bulunamazsa, özel durum Işleyicisi ara yazılımı bir HTTP 404 yanıtı üretir.</span><span class="sxs-lookup"><span data-stu-id="d105b-116">The Exception Handler Middleware produces an HTTP 404 response if the configured exception handler can't be found.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="d105b-117">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="d105b-117">New behavior</span></span>

<span data-ttu-id="d105b-118">Özel durum Işleyici ara yazılımı, yapılandırılmış özel durum işleyicisi bulunamazsa özgün özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d105b-118">The Exception Handler Middleware throws the original exception if the configured exception handler can't be found.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d105b-119">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="d105b-119">Reason for change</span></span>

<span data-ttu-id="d105b-120">HTTP 404 hatası, sunucuda bir özel durumun gerçekleşmediğini açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d105b-120">The HTTP 404 error doesn't make it obvious that an exception occurred on the server.</span></span> <span data-ttu-id="d105b-121">Bu değişiklik şunları açık hale getirmek için bir HTTP 500 hatası üretir:</span><span class="sxs-lookup"><span data-stu-id="d105b-121">This change produces an HTTP 500 error to make it obvious that:</span></span>

* <span data-ttu-id="d105b-122">Sorun bir kullanıcı hatasından kaynaklanmıyor.</span><span class="sxs-lookup"><span data-stu-id="d105b-122">The problem isn't caused by a user error.</span></span>
* <span data-ttu-id="d105b-123">Sunucuda bir özel durumla karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="d105b-123">An exception was encountered on the server.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d105b-124">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d105b-124">Recommended action</span></span>

<span data-ttu-id="d105b-125">API değişikliği yok.</span><span class="sxs-lookup"><span data-stu-id="d105b-125">There are no API changes.</span></span> <span data-ttu-id="d105b-126">Tüm mevcut uygulamalar derlenmeye ve çalıştırmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="d105b-126">All existing apps will continue to compile and run.</span></span> <span data-ttu-id="d105b-127">Oluşturulan özel durum sunucu tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="d105b-127">The exception thrown is handled by the server.</span></span> <span data-ttu-id="d105b-128">Örneğin, özel durum [Kestrel](/aspnet/core/fundamentals/servers/kestrel) veya [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys)tarafından http 500 hata yanıtına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="d105b-128">For example, the exception is converted to an HTTP 500 error response by [Kestrel](/aspnet/core/fundamentals/servers/kestrel) or [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d105b-129">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d105b-129">Affected APIs</span></span>

<span data-ttu-id="d105b-130">Yok</span><span class="sxs-lookup"><span data-stu-id="d105b-130">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
