---
title: ICorConfiguration::SetDebuggerThreadControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
ms.openlocfilehash: 0f6a369691ab2e4e9fd2e5d9731fb1dc0a42ba11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127792"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="ba578-102">ICorConfiguration::SetDebuggerThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba578-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="ba578-103">Hata ayıklama hizmetlerinin, ortak dil çalışma zamanı (CLR) iş parçacıklarının engellediği ve hata ayıklama için engellemesi kaldırıldığından, geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ba578-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba578-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba578-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba578-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba578-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="ba578-106">'ndaki Hata ayıklama Hizmetleri tarafından iş parçacıklarının engellenmesini ve engellemesini kaldırma hakkında bilgi veren bir [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ba578-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba578-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba578-107">Requirements</span></span>  
 <span data-ttu-id="ba578-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba578-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba578-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ba578-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba578-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ba578-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba578-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba578-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba578-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba578-112">See also</span></span>

- [<span data-ttu-id="ba578-113">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba578-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
