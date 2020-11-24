---
title: 'ICorProfilerInfo7:: GetInMemorySymbolsLength yöntemi'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 46ffa5cb4fac6988240d32cb1939cc25bdf0a412
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686078"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="2d66a-102">ICorProfilerInfo7:: GetInMemorySymbolsLength yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d66a-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>

<span data-ttu-id="2d66a-103">[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="2d66a-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="2d66a-104">Bellek içi sembol akışının uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2d66a-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d66a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2d66a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d66a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d66a-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="2d66a-107">'ndaki Bellek içi akışı içeren modülün tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="2d66a-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="2d66a-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="2d66a-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="2d66a-109">dışı Bir değere yönelik, `DWORD` yöntemin döndürdüğü bir işaretçi, akışın uzunluğunu bayt olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="2d66a-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d66a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2d66a-110">Return Value</span></span>  

 <span data-ttu-id="2d66a-111">Bu yöntem, `S_OK` sıfır (0) olsa bile, bellek akışının uzunluğu belirlenebileceği takdirde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2d66a-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="2d66a-112">Yöntemi `CORPROF_E_MODULE_IS_DYNAMIC` , yöntemi kullanılarak oluşturulduysa döndürür <xref:System.Reflection.Emit?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2d66a-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d66a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d66a-113">Remarks</span></span>  

 <span data-ttu-id="2d66a-114">Modülün bellek içi sembolleri varsa, akışın uzunluğu içine yerleştirilir `pCountSymbolBytes` .</span><span class="sxs-lookup"><span data-stu-id="2d66a-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="2d66a-115">Modülün bellek içi sembolleri yoksa `*pCountSymbolBytes = 0` .</span><span class="sxs-lookup"><span data-stu-id="2d66a-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d66a-116">Geçerli uygulama Reflection. yayma 'yi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="2d66a-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="2d66a-117">Modül Reflection. yayma kullanılarak oluşturulduysa, yöntemi döndürür `CORPROF_E_MODULE_IS_DYNAMIC` .</span><span class="sxs-lookup"><span data-stu-id="2d66a-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d66a-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d66a-118">Requirements</span></span>  

 <span data-ttu-id="2d66a-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d66a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d66a-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2d66a-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2d66a-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2d66a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d66a-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d66a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d66a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d66a-123">See also</span></span>

- [<span data-ttu-id="2d66a-124">ICorProfilerInfo7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d66a-124">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
