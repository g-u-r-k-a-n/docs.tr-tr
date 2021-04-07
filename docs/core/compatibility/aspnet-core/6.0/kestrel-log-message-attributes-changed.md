---
title: 'Son değişiklik: Kestrel: günlük iletisi öznitelikleri değiştirildi'
description: "Kestrel başlıklı ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin: günlük iletisi öznitelikleri değiştirildi"
ms.author: scaddie
ms.date: 02/01/2021
ms.openlocfilehash: 09b0bc71b6c9935b9e7e4170f24869f4d45c97f6
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496884"
---
# <a name="kestrel-log-message-attributes-changed"></a><span data-ttu-id="7f3ea-103">Kestrel: günlük iletisi öznitelikleri değiştirildi</span><span class="sxs-lookup"><span data-stu-id="7f3ea-103">Kestrel: Log message attributes changed</span></span>

<span data-ttu-id="7f3ea-104">Kestrel günlük iletilerinde ilişkili kimlikler ve adlar vardır.</span><span class="sxs-lookup"><span data-stu-id="7f3ea-104">Kestrel log messages have associated IDs and names.</span></span> <span data-ttu-id="7f3ea-105">Bu öznitelikler farklı türlerde günlük iletilerini benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7f3ea-105">These attributes uniquely identify different kinds of log messages.</span></span> <span data-ttu-id="7f3ea-106">Bu kimliklerin ve adların bazıları yanlış yinelenmiş.</span><span class="sxs-lookup"><span data-stu-id="7f3ea-106">Some of those IDs and names were incorrectly duplicated.</span></span> <span data-ttu-id="7f3ea-107">Bu çoğaltma sorunu ASP.NET Core 6,0 ' de düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="7f3ea-107">This duplication problem is fixed in ASP.NET Core 6.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7f3ea-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7f3ea-108">Version introduced</span></span>

<span data-ttu-id="7f3ea-109">6.0</span><span class="sxs-lookup"><span data-stu-id="7f3ea-109">6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="7f3ea-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="7f3ea-110">Old behavior</span></span>

<span data-ttu-id="7f3ea-111">Aşağıdaki tabloda ASP.NET Core 6,0 ' dan önce etkilenen günlük iletilerinin durumu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7f3ea-111">The following table shows the state of the affected log messages before ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="7f3ea-112">İleti açıklaması</span><span class="sxs-lookup"><span data-stu-id="7f3ea-112">Message description</span></span>                   | <span data-ttu-id="7f3ea-113">Name</span><span class="sxs-lookup"><span data-stu-id="7f3ea-113">Name</span></span>                    | <span data-ttu-id="7f3ea-114">ID</span><span class="sxs-lookup"><span data-stu-id="7f3ea-114">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="7f3ea-115">HTTP/2 bağlantısı kapalı günlük iletileri</span><span class="sxs-lookup"><span data-stu-id="7f3ea-115">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="7f3ea-116">36</span><span class="sxs-lookup"><span data-stu-id="7f3ea-116">36</span></span> |
| <span data-ttu-id="7f3ea-117">HTTP/2 çerçeve gönderme günlüğü iletileri</span><span class="sxs-lookup"><span data-stu-id="7f3ea-117">HTTP/2 frame sending log messages</span></span>     | `Http2FrameReceived`    | <span data-ttu-id="7f3ea-118">37</span><span class="sxs-lookup"><span data-stu-id="7f3ea-118">37</span></span> |

## <a name="new-behavior"></a><span data-ttu-id="7f3ea-119">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="7f3ea-119">New behavior</span></span>

<span data-ttu-id="7f3ea-120">Aşağıdaki tabloda ASP.NET Core 6,0 ' de etkilenen günlük iletilerinin durumu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7f3ea-120">The following table shows the state of the affected log messages in ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="7f3ea-121">İleti açıklaması</span><span class="sxs-lookup"><span data-stu-id="7f3ea-121">Message description</span></span>                   | <span data-ttu-id="7f3ea-122">Name</span><span class="sxs-lookup"><span data-stu-id="7f3ea-122">Name</span></span>                    | <span data-ttu-id="7f3ea-123">ID</span><span class="sxs-lookup"><span data-stu-id="7f3ea-123">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="7f3ea-124">HTTP/2 bağlantısı kapalı günlük iletileri</span><span class="sxs-lookup"><span data-stu-id="7f3ea-124">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="7f3ea-125">48</span><span class="sxs-lookup"><span data-stu-id="7f3ea-125">48</span></span> |
| <span data-ttu-id="7f3ea-126">HTTP/2 çerçeve gönderme günlüğü iletileri</span><span class="sxs-lookup"><span data-stu-id="7f3ea-126">HTTP/2 frame sending log messages</span></span>     | `Http2FrameSending`     | <span data-ttu-id="7f3ea-127">49</span><span class="sxs-lookup"><span data-stu-id="7f3ea-127">49</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="7f3ea-128">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="7f3ea-128">Reason for change</span></span>

<span data-ttu-id="7f3ea-129">Farklı ileti türlerinin belirlenebilmesi için günlük kimlikleri ve adları benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7f3ea-129">Log IDs and names should be unique so different message types can be identified.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7f3ea-130">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7f3ea-130">Recommended action</span></span>

<span data-ttu-id="7f3ea-131">Eski kimliklere ve adlara başvuruda bulunan kod veya yapılandırmaya sahipseniz, bu başvuruları yeni kimlikleri ve adları kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="7f3ea-131">If you have code or configuration that references the old IDs and names, update those references to use the new IDs and names.</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
