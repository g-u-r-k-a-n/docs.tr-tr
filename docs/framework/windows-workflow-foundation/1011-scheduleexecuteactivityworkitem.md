---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: dc209fc41dc6b076dfb897880f753be51f7fb0ce
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239698"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="a3564-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="a3564-102">1011 - ScheduleExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="a3564-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a3564-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a3564-104">ID</span><span class="sxs-lookup"><span data-stu-id="a3564-104">ID</span></span>|<span data-ttu-id="a3564-105">1011</span><span class="sxs-lookup"><span data-stu-id="a3564-105">1011</span></span>|  
|<span data-ttu-id="a3564-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="a3564-106">Keywords</span></span>|<span data-ttu-id="a3564-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a3564-107">WFRuntime</span></span>|  
|<span data-ttu-id="a3564-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a3564-108">Level</span></span>|<span data-ttu-id="a3564-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="a3564-109">Verbose</span></span>|  
|<span data-ttu-id="a3564-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a3564-110">Channel</span></span>|<span data-ttu-id="a3564-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="a3564-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a3564-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3564-112">Description</span></span>  

 <span data-ttu-id="a3564-113">Bir ExecuteActivityWorkItem zamanlandığı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3564-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a3564-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a3564-114">Message</span></span>  

 <span data-ttu-id="a3564-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir ExecuteActivityWorkItem zamanlandı.</span><span class="sxs-lookup"><span data-stu-id="a3564-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a3564-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a3564-116">Details</span></span>  
  
|<span data-ttu-id="a3564-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a3564-117">Data Item Name</span></span>|<span data-ttu-id="a3564-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a3564-118">Data Item Type</span></span>|<span data-ttu-id="a3564-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3564-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a3564-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="a3564-120">Activity</span></span>|<span data-ttu-id="a3564-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="a3564-121">xs:string</span></span>|<span data-ttu-id="a3564-122">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="a3564-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="a3564-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a3564-123">DisplayName</span></span>|<span data-ttu-id="a3564-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="a3564-124">xs:string</span></span>|<span data-ttu-id="a3564-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="a3564-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="a3564-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a3564-126">InstanceId</span></span>|<span data-ttu-id="a3564-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="a3564-127">xs:string</span></span>|<span data-ttu-id="a3564-128">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="a3564-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a3564-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a3564-129">AppDomain</span></span>|<span data-ttu-id="a3564-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="a3564-130">xs:string</span></span>|<span data-ttu-id="a3564-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a3564-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
