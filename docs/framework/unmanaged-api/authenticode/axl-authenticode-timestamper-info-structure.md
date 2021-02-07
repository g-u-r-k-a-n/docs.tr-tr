---
description: 'Daha fazla bilgi edinin: AXL_AUTHENTICODE_TIMESTAMPER_INFO yapısı'
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
ms.openlocfilehash: 35e30241c3c3b5747e247c57183e28e726c0cae3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747419"
---
# <a name="axl_authenticode_timestamper_info-structure"></a><span data-ttu-id="29b82-103">AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="29b82-103">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>

<span data-ttu-id="29b82-104">Authenticode zaman Stamper bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="29b82-104">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b82-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="29b82-105">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="29b82-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="29b82-106">Members</span></span>  
  
|<span data-ttu-id="29b82-107">Üye</span><span class="sxs-lookup"><span data-stu-id="29b82-107">Member</span></span>|<span data-ttu-id="29b82-108">Description</span><span class="sxs-lookup"><span data-stu-id="29b82-108">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="29b82-109">Bu yapının boyutu.</span><span class="sxs-lookup"><span data-stu-id="29b82-109">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="29b82-110">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="29b82-110">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="29b82-111">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="29b82-111">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="29b82-112">Zaman damgasının saati.</span><span class="sxs-lookup"><span data-stu-id="29b82-112">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="29b82-113">Zaman stamplayıcı zinciri bağlamı.</span><span class="sxs-lookup"><span data-stu-id="29b82-113">The time stamper’s chain context.</span></span>  <span data-ttu-id="29b82-114">[CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="29b82-114">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29b82-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29b82-115">See also</span></span>

- [<span data-ttu-id="29b82-116">Authenticode</span><span class="sxs-lookup"><span data-stu-id="29b82-116">Authenticode</span></span>](index.md)
