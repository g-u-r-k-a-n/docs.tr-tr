---
title: 'Hizmet: Saniyede Hatalı Çağrı'
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: 211240d5bef7fe31a36f636313b48a2b9e15b239
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556017"
---
# <a name="service-calls-faulted-per-second"></a><span data-ttu-id="94b0c-102">Hizmet: Saniyede Hatalı Çağrı</span><span class="sxs-lookup"><span data-stu-id="94b0c-102">Service: Calls Faulted Per Second</span></span>
<span data-ttu-id="94b0c-103">Sayaç adı: saniye başına hatalı çağrı.</span><span class="sxs-lookup"><span data-stu-id="94b0c-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="94b0c-104">Description</span><span class="sxs-lookup"><span data-stu-id="94b0c-104">Description</span></span>  
 <span data-ttu-id="94b0c-105">Saniye içinde bu hizmete hata döndüren çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="94b0c-105">Number of calls that have returned faults to this service in a second.</span></span>  
  
 <span data-ttu-id="94b0c-106">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="94b0c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="94b0c-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="94b0c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="94b0c-108">Windows Communication Foundation (WCF) uygulamalarında, hizmet yöntemleri SOAP hata iletilerini kullanarak işlem hata bilgilerini iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="94b0c-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="94b0c-109">SOAP hataları, bir hizmet işleminin meta verilerinde bulunan ileti türleridir ve bu nedenle, istemcilerinin yürütmesini daha sağlam veya etkileşimli hale getirmek için kullanabileceği bir hata sözleşmesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="94b0c-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="94b0c-110">SOAP hataları, XML biçiminde istemcilere belirtilediğinden, bunlar çok fazla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="94b0c-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b0c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94b0c-111">See also</span></span>

- [<span data-ttu-id="94b0c-112">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="94b0c-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
