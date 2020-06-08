---
title: ICorProfilerCallback::AssemblyLoadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: ce4a842bc71ff144e46efb0d6f7068dfca9d207d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500448"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="8f725-102">ICorProfilerCallback::AssemblyLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f725-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="8f725-103">Profiler 'ın bir derlemenin yüklemeyi bitirmiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="8f725-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f725-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8f725-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f725-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f725-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="8f725-106">\[' de], yüklenmiş derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8f725-106">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="8f725-107">\[içinde] derlemenin başarıyla yüklenip yüklenmediğini belirten bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="8f725-107">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f725-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f725-108">Remarks</span></span>  
 <span data-ttu-id="8f725-109">Değeri `assemblyId` , `AssemblyLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="8f725-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="8f725-110">Derlemeyi yüklemenin bazı bölümleri geri aramadan sonra devam edebilir `AssemblyLoadFinished` .</span><span class="sxs-lookup"><span data-stu-id="8f725-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="8f725-111">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f725-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="8f725-112">Ancak, içinde başarılı bir HRESULT, `hrStatus` sadece derlemeyi yüklemenin ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f725-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f725-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f725-113">Requirements</span></span>  
 <span data-ttu-id="8f725-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f725-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f725-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8f725-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f725-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8f725-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f725-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f725-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f725-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f725-118">See also</span></span>

- [<span data-ttu-id="8f725-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f725-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
