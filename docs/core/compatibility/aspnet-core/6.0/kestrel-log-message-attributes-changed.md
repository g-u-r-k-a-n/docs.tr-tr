---
title: 'Son değişiklik: Kestrel: günlük iletisi öznitelikleri değiştirildi'
description: "Kestrel başlıklı ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin: günlük iletisi öznitelikleri değiştirildi"
ms.author: scaddie
ms.date: 02/01/2021
ms.openlocfilehash: daeb9ae418f343a00e9563ef3e2b5090a7f016a9
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255174"
---
# <a name="kestrel-log-message-attributes-changed"></a><span data-ttu-id="b14bc-103">Kestrel: günlük iletisi öznitelikleri değiştirildi</span><span class="sxs-lookup"><span data-stu-id="b14bc-103">Kestrel: Log message attributes changed</span></span>

<span data-ttu-id="b14bc-104">Kestrel günlük iletilerinde ilişkili kimlikler ve adlar vardır.</span><span class="sxs-lookup"><span data-stu-id="b14bc-104">Kestrel log messages have associated IDs and names.</span></span> <span data-ttu-id="b14bc-105">Bu öznitelikler farklı türlerde günlük iletilerini benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b14bc-105">These attributes uniquely identify different kinds of log messages.</span></span> <span data-ttu-id="b14bc-106">Bu kimliklerin ve adların bazıları yanlış yinelenmiş.</span><span class="sxs-lookup"><span data-stu-id="b14bc-106">Some of those IDs and names were incorrectly duplicated.</span></span> <span data-ttu-id="b14bc-107">Bu çoğaltma sorunu ASP.NET Core 6,0 ' de düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="b14bc-107">This duplication problem is fixed in ASP.NET Core 6.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b14bc-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b14bc-108">Version introduced</span></span>

<span data-ttu-id="b14bc-109">ASP.NET Core 6,0</span><span class="sxs-lookup"><span data-stu-id="b14bc-109">ASP.NET Core 6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="b14bc-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="b14bc-110">Old behavior</span></span>

<span data-ttu-id="b14bc-111">Aşağıdaki tabloda ASP.NET Core 6,0 ' dan önce etkilenen günlük iletilerinin durumu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b14bc-111">The following table shows the state of the affected log messages before ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="b14bc-112">İleti açıklaması</span><span class="sxs-lookup"><span data-stu-id="b14bc-112">Message description</span></span>                   | <span data-ttu-id="b14bc-113">Name</span><span class="sxs-lookup"><span data-stu-id="b14bc-113">Name</span></span>                    | <span data-ttu-id="b14bc-114">ID</span><span class="sxs-lookup"><span data-stu-id="b14bc-114">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="b14bc-115">HTTP/2 bağlantısı kapalı günlük iletileri</span><span class="sxs-lookup"><span data-stu-id="b14bc-115">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="b14bc-116">36</span><span class="sxs-lookup"><span data-stu-id="b14bc-116">36</span></span> |
| <span data-ttu-id="b14bc-117">HTTP/2 çerçeve gönderme günlüğü iletileri</span><span class="sxs-lookup"><span data-stu-id="b14bc-117">HTTP/2 frame sending log messages</span></span>     | `Http2FrameReceived`    | <span data-ttu-id="b14bc-118">37</span><span class="sxs-lookup"><span data-stu-id="b14bc-118">37</span></span> |

## <a name="new-behavior"></a><span data-ttu-id="b14bc-119">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="b14bc-119">New behavior</span></span>

<span data-ttu-id="b14bc-120">Aşağıdaki tabloda ASP.NET Core 6,0 ' de etkilenen günlük iletilerinin durumu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b14bc-120">The following table shows the state of the affected log messages in ASP.NET Core 6.0.</span></span>

| <span data-ttu-id="b14bc-121">İleti açıklaması</span><span class="sxs-lookup"><span data-stu-id="b14bc-121">Message description</span></span>                   | <span data-ttu-id="b14bc-122">Name</span><span class="sxs-lookup"><span data-stu-id="b14bc-122">Name</span></span>                    | <span data-ttu-id="b14bc-123">ID</span><span class="sxs-lookup"><span data-stu-id="b14bc-123">ID</span></span> |
|---------------------------------------|-------------------------|----|
| <span data-ttu-id="b14bc-124">HTTP/2 bağlantısı kapalı günlük iletileri</span><span class="sxs-lookup"><span data-stu-id="b14bc-124">HTTP/2 connection closed log messages</span></span> | `Http2ConnectionClosed` | <span data-ttu-id="b14bc-125">48</span><span class="sxs-lookup"><span data-stu-id="b14bc-125">48</span></span> |
| <span data-ttu-id="b14bc-126">HTTP/2 çerçeve gönderme günlüğü iletileri</span><span class="sxs-lookup"><span data-stu-id="b14bc-126">HTTP/2 frame sending log messages</span></span>     | `Http2FrameSending`     | <span data-ttu-id="b14bc-127">49</span><span class="sxs-lookup"><span data-stu-id="b14bc-127">49</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="b14bc-128">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b14bc-128">Reason for change</span></span>

<span data-ttu-id="b14bc-129">Farklı ileti türlerinin belirlenebilmesi için günlük kimlikleri ve adları benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b14bc-129">Log IDs and names should be unique so different message types can be identified.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b14bc-130">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b14bc-130">Recommended action</span></span>

<span data-ttu-id="b14bc-131">Eski kimliklere ve adlara başvuruda bulunan kod veya yapılandırmaya sahipseniz, bu başvuruları yeni kimlikleri ve adları kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="b14bc-131">If you have code or configuration that references the old IDs and names, update those references to use the new IDs and names.</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
