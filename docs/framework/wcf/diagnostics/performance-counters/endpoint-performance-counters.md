---
description: Daha fazla bilgi için bkz. uç nokta performans sayaçları
title: Uç Noktası Performans Sayaçları
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 60cd94d5d954c87f4b37469688ee809a13fa3cb4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771242"
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="dfded-103">Uç Noktası Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="dfded-103">Endpoint Performance Counters</span></span>

<span data-ttu-id="dfded-104">Uç nokta performans sayaçları, bir uç noktanın iletileri nasıl kabul ettiğini gösteren verileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="dfded-104">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="dfded-105">Performans `ServiceModelEndpoint 4.0.0.0` İzleyicisi ile görüntülenirken Performans nesnesi altında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="dfded-105">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="dfded-106">Örnekler bu model kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="dfded-106">The instances are named using this pattern:</span></span>  
  
`(ServiceName).(ContractName)@(endpoint listener address)`  
  
 <span data-ttu-id="dfded-107">Veriler tek tek işlemler için toplanmaya benzerdir, ancak yalnızca uç nokta boyunca toplanır.</span><span class="sxs-lookup"><span data-stu-id="dfded-107">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="dfded-108">Performans sayacı örneğinin adının uzunluğu için bir sınır vardır.</span><span class="sxs-lookup"><span data-stu-id="dfded-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="dfded-109">Bir Windows Communication Foundation (WCF) sayaç örneği adı en fazla uzunluğu aştığında, WCF örnek adının bir bölümünü bir karma değerle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="dfded-109">When a Windows Communication Foundation (WCF) counter instance name exceeds the maximum length, WCF replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfded-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfded-110">See also</span></span>

- [<span data-ttu-id="dfded-111">Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="dfded-111">Performance Counters</span></span>](index.md)
