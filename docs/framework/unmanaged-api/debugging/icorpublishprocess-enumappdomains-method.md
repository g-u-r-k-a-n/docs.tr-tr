---
title: ICorPublishProcess::EnumAppDomains Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
ms.openlocfilehash: 2acf8fb507ab617e066a31c9c2657b1ef0d18e47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693287"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="a4833-102">ICorPublishProcess::EnumAppDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4833-102">ICorPublishProcess::EnumAppDomains Method</span></span>

<span data-ttu-id="a4833-103">Bu [ICorPublishProcess](icorpublishprocess-interface.md)tarafından başvurulan işlemdeki uygulama etki alanları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="a4833-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4833-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a4833-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4833-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4833-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="a4833-106">dışı Bu işlemdeki uygulama etki alanları koleksiyonu aracılığıyla yinelemeye izin veren bir [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a4833-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4833-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4833-107">Remarks</span></span>  

 <span data-ttu-id="a4833-108">Uygulama etki alanlarının listesi, yöntemi çağrıldığında var olan uygulama etki alanlarının anlık görüntüsünü temel alır `EnumAppDomains` .</span><span class="sxs-lookup"><span data-stu-id="a4833-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="a4833-109">Bu yöntem, yeni bir güncel liste oluşturmak için birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4833-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="a4833-110">Mevcut listeler, bu yöntemin sonraki çağrılarından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="a4833-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="a4833-111">İşlem sonlandırıldıysa, `EnumAppDomains` CORDBG_E_PROCESS_TERMINATED HRESULT değeriyle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="a4833-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4833-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4833-112">Requirements</span></span>  

 <span data-ttu-id="a4833-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4833-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4833-114">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="a4833-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a4833-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a4833-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4833-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4833-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4833-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4833-117">See also</span></span>

- [<span data-ttu-id="a4833-118">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4833-118">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
