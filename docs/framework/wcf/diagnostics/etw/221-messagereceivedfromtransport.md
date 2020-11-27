---
title: 221 - MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 47e871b70e3ef2419543b4710c2988736665cb46
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263106"
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="568dc-102">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="568dc-102">221 - MessageReceivedFromTransport</span></span>

## <a name="properties"></a><span data-ttu-id="568dc-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="568dc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="568dc-104">ID</span><span class="sxs-lookup"><span data-stu-id="568dc-104">ID</span></span>|<span data-ttu-id="568dc-105">221</span><span class="sxs-lookup"><span data-stu-id="568dc-105">221</span></span>|  
|<span data-ttu-id="568dc-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="568dc-106">Keywords</span></span>|<span data-ttu-id="568dc-107">EndToEndMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="568dc-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="568dc-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="568dc-108">Level</span></span>|<span data-ttu-id="568dc-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="568dc-109">Information</span></span>|  
|<span data-ttu-id="568dc-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="568dc-110">Channel</span></span>|<span data-ttu-id="568dc-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="568dc-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="568dc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="568dc-112">Description</span></span>  

 <span data-ttu-id="568dc-113">Bu olay, hizmet modeli aktarımdan bir ileti aldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="568dc-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="568dc-114">İleti</span><span class="sxs-lookup"><span data-stu-id="568dc-114">Message</span></span>  

 <span data-ttu-id="568dc-115">Dağıtıcı aktarımdan bir ileti aldı.</span><span class="sxs-lookup"><span data-stu-id="568dc-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="568dc-116">Bağıntı KIMLIĞI = = ' %1 '.</span><span class="sxs-lookup"><span data-stu-id="568dc-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="568dc-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="568dc-117">Details</span></span>  
  
|<span data-ttu-id="568dc-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="568dc-118">Data Item Name</span></span>|<span data-ttu-id="568dc-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="568dc-119">Data Item Type</span></span>|<span data-ttu-id="568dc-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="568dc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="568dc-121">Bağıntı Kimliği</span><span class="sxs-lookup"><span data-stu-id="568dc-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="568dc-122">`MessageSentToTransport`Bir hizmet veya istemciden bir olayı diğer uçta karşılık gelen bir olay ile ilişkilendirmek için kullanılan etkınlık kimliği `MessageReceivedFromTransport` .</span><span class="sxs-lookup"><span data-stu-id="568dc-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="568dc-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="568dc-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="568dc-124">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="568dc-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="568dc-125">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="568dc-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="568dc-126">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="568dc-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="568dc-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="568dc-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="568dc-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="568dc-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
