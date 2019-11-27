---
title: IBindingDisplay::GetCurrentDisplay Yöntemi
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
ms.openlocfilehash: 9294dbf1caddd4b607185de54efd2b4764e6ca35
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448497"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="7d089-102">IBindingDisplay::GetCurrentDisplay Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d089-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="7d089-103">Geçerli bağlama görüntüleme bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d089-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d089-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d089-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d089-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d089-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="7d089-106">[Out, retval] Bağlama görünen bilgilerini içeren bir SAFEARRAY işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7d089-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d089-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d089-107">Remarks</span></span>  
 <span data-ttu-id="7d089-108">[IBindingDisplay:: InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) yöntemi daha önce başarılı olmalıdır ve program bir hata ayıklayıcı tarafından durdurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d089-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="7d089-109">Çağıranın, [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy)kullanarak döndürülen `SAFEARRAY` belleği serbest bırakma gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d089-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d089-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d089-110">Requirements</span></span>  
 <span data-ttu-id="7d089-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d089-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d089-112">**Üst bilgi:** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="7d089-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="7d089-113">**Kitaplık:** BindingDisplay. IDL</span><span class="sxs-lookup"><span data-stu-id="7d089-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="7d089-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d089-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d089-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d089-115">See also</span></span>

- [<span data-ttu-id="7d089-116">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d089-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="7d089-117">InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d089-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
