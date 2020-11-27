---
title: 'Uç Noktası: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
ms.openlocfilehash: b2c5022caa5abe6154a3cb4dd4281dd212599b74
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256488"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="552b9-102">Uç Noktası: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası</span><span class="sxs-lookup"><span data-stu-id="552b9-102">Endpoint: Security Validation and Authentication Failures Per Second</span></span>

<span data-ttu-id="552b9-103">Sayaç adı: güvenlik doğrulaması ve saniye başına kimlik doğrulama başarısızlığı</span><span class="sxs-lookup"><span data-stu-id="552b9-103">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="552b9-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="552b9-104">Description</span></span>  

 <span data-ttu-id="552b9-105">Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="552b9-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="552b9-106">Bu tür sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="552b9-106">Such problems include:</span></span>  
  
- <span data-ttu-id="552b9-107">İstemci belirteci iletiden okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="552b9-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="552b9-108">İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).</span><span class="sxs-lookup"><span data-stu-id="552b9-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="552b9-109">İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).</span><span class="sxs-lookup"><span data-stu-id="552b9-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="552b9-110">İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.</span><span class="sxs-lookup"><span data-stu-id="552b9-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="552b9-111">Şifre çözme hatası oluştu.</span><span class="sxs-lookup"><span data-stu-id="552b9-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="552b9-112">İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.</span><span class="sxs-lookup"><span data-stu-id="552b9-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="552b9-113">TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.</span><span class="sxs-lookup"><span data-stu-id="552b9-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="552b9-114">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür:</span><span class="sxs-lookup"><span data-stu-id="552b9-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="552b9-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="552b9-115">(N1-N0)/((D1-D0)/F)</span></span>
