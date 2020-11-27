---
title: Şüpheli Uygulanan İşlem/Saniye
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: 9162809ec467f282674e0ab21f7ce5e4d2222da4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249988"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="3659c-102">Şüpheli Uygulanan İşlem/Saniye</span><span class="sxs-lookup"><span data-stu-id="3659c-102">Transacted Operations In Doubt Per Second</span></span>

<span data-ttu-id="3659c-103">Sayaç adı: saniyede şüpheli Işlem sayısı.</span><span class="sxs-lookup"><span data-stu-id="3659c-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3659c-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3659c-104">Description</span></span>  

 <span data-ttu-id="3659c-105">Saniye içinde bu hizmette şüpheli bir sonuca sahip işlem işlemlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="3659c-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="3659c-106">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="3659c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="3659c-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="3659c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
