---
title: ITypeName::GetModifiers Yöntemi
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
ms.openlocfilehash: c96764749a766f3b4bbff4cf6512677a47197f4c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095826"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="c2f03-102">ITypeName::GetModifiers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2f03-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="c2f03-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="c2f03-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2f03-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2f03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c2f03-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2f03-105">Requirements</span></span>  
 <span data-ttu-id="c2f03-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2f03-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2f03-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c2f03-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2f03-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c2f03-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2f03-109">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2f03-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f03-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2f03-110">See also</span></span>

- [<span data-ttu-id="c2f03-111">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c2f03-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
