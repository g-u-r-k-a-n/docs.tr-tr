---
title: ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
ms.openlocfilehash: 69a7501d9b887b9504067409356bf302c47466e7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090249"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="92867-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92867-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="92867-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="92867-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="92867-104">Çerçevede yerel değişken için bir Numaralandırıcı alır ve isteğe bağlı olarak profil oluşturucu yeniden JIT araçlarına eklenen değişkenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="92867-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92867-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92867-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92867-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92867-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="92867-107">'ndaki Profil Oluşturucu yeniden JIT araçlarına eklenen değişkenlerin çerçeveye dahil edilip edilmeyeceğini belirten bir [ılcodekind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) numaralandırma üyesi.</span><span class="sxs-lookup"><span data-stu-id="92867-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="92867-108">dışı Bu çerçevedeki yerel değişkenlerin numaralandırıcısının bulunduğu bir "ICorDebugValueEnum" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="92867-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92867-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92867-109">Remarks</span></span>  
 <span data-ttu-id="92867-110">Bu yöntem, isteğe bağlı olarak profil oluşturucu yeniden JIT araçları 'nda eklenen değişkenlere erişmesi dışında, [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) yöntemine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="92867-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="92867-111">`flags` `ILCODE_ORIGINAL_IL` ayarlanması [ICorDebugILFrame:: EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)çağrısı ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="92867-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="92867-112">`flags` `ILCODE_REJIT_IL` olarak ayarlamak, hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere erişmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="92867-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="92867-113">Ara dil (IL) görünmüyorsa, numaralandırma boştur ve Yöntem `S_OK`döndürür.</span><span class="sxs-lookup"><span data-stu-id="92867-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="92867-114">Numaralandırıcı etkin olmayabilir, bu, çalışan yöntemdeki tüm yerel değişkenleri içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="92867-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92867-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92867-115">Requirements</span></span>  
 <span data-ttu-id="92867-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92867-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92867-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="92867-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92867-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="92867-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92867-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92867-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92867-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92867-120">See also</span></span>

- [<span data-ttu-id="92867-121">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92867-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="92867-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="92867-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="92867-123">ReJIT: nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="92867-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
