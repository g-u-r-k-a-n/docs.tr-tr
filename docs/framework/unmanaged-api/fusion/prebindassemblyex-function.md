---
title: PreBindAssemblyEx İşlevi
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
ms.openlocfilehash: a729249f7b0681941a0b1a478dbe2c0d9d6cd01c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723967"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="35846-102">PreBindAssemblyEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="35846-102">PreBindAssemblyEx Function</span></span>

<span data-ttu-id="35846-103">Bir derlemenin ilke sonrası görünen adını alır.</span><span class="sxs-lookup"><span data-stu-id="35846-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="35846-104">Bu işlev .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="35846-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35846-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="35846-105">Syntax</span></span>  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="35846-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35846-106">Parameters</span></span>  

 `pAppCtx`  
 <span data-ttu-id="35846-107">'ndaki Uygulama bağlamını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="35846-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="35846-108">'ndaki Derleme adını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="35846-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="35846-109">'ndaki Üst derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="35846-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="35846-110">Bu parametre yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="35846-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="35846-111">'ndaki Çalışma zamanı sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="35846-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="35846-112">dışı İlke sonrası görünen adını içerir.</span><span class="sxs-lookup"><span data-stu-id="35846-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="35846-113">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="35846-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="35846-114">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="35846-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35846-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35846-115">Remarks</span></span>  

 <span data-ttu-id="35846-116">`ppNamePostPolicy`Output parametresi yalnızca Işlev HRESULT FUSION_E_REF_DEF_MISMATCH döndürürse ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="35846-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="35846-117">Aksi halde, null olur.</span><span class="sxs-lookup"><span data-stu-id="35846-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35846-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35846-118">Requirements</span></span>  

 <span data-ttu-id="35846-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35846-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35846-120">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="35846-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="35846-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="35846-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="35846-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35846-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35846-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35846-123">See also</span></span>

- [<span data-ttu-id="35846-124">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="35846-124">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
