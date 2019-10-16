---
title: Saniyede Başarısız Olan Çağrı
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: e7c0b53f4c2b1a7e87a5791b44e452ec9146c459
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321118"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="2880e-102">Saniyede Başarısız Olan Çağrı</span><span class="sxs-lookup"><span data-stu-id="2880e-102">Calls Failed Per Second</span></span>
<span data-ttu-id="2880e-103">Sayaç adı: başarısız çağrı/saniye</span><span class="sxs-lookup"><span data-stu-id="2880e-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="2880e-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2880e-104">Description</span></span>  
 <span data-ttu-id="2880e-105">Saniye içinde bu işlemdeki işlenmemiş özel durumları olan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="2880e-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="2880e-106">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanmış olan [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="2880e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2880e-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="2880e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="2880e-108">Bu işlemde işlenmeyen bir özel durum olduğunda bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="2880e-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2880e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2880e-109">See also</span></span>

- [<span data-ttu-id="2880e-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="2880e-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
