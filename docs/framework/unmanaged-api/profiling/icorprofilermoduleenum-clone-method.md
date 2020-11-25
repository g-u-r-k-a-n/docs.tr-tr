---
title: ICorProfilerModuleEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: ae9f6b7865a80e3edc4cae8fd1298e5eed864377
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722836"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="c2c38-102">ICorProfilerModuleEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2c38-102">ICorProfilerModuleEnum::Clone Method</span></span>

<span data-ttu-id="c2c38-103">Bu [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) arabiriminin bir kopyasına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="c2c38-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c38-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c2c38-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2c38-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2c38-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="c2c38-106">dışı Sırasıyla bu [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) arabiriminin kopyasına işaret eden arabirim işaretçisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c2c38-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="c2c38-107">Numaralandırıcı kopyası kendi numaralandırma durumunu bu numaralandırıcıda ayrı olarak tutar.</span><span class="sxs-lookup"><span data-stu-id="c2c38-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="c2c38-108">Ancak, kopyanın ilk imleç konumu, bu Numaralandırıcının geçerli imleç konumuyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c2c38-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2c38-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2c38-109">Requirements</span></span>  

 <span data-ttu-id="c2c38-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2c38-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2c38-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c2c38-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2c38-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c2c38-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2c38-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2c38-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c38-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2c38-114">See also</span></span>

- [<span data-ttu-id="c2c38-115">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2c38-115">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="c2c38-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c2c38-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
