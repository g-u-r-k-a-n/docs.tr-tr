---
title: GetCLRIdentityManager İşlevi
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
ms.openlocfilehash: 3c6def32c63e3557a4de72baf7b1c3e67feb4891
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136522"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="f9870-102">GetCLRIdentityManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="f9870-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="f9870-103">Ortak dil çalışma zamanının (CLR) kimlikleri yönetmesine izin veren bir arabirime yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f9870-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="f9870-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="f9870-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9870-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9870-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9870-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9870-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="f9870-107">'ndaki Hangi arabirimin alınacağını belirten bir `REFIID` (bir arabirim tanımlayıcısı).</span><span class="sxs-lookup"><span data-stu-id="f9870-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="f9870-108">Bu değer IID_ICLRAssemblyIdentityManager ya da IID_ICLRHostBindingPolicyManager olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9870-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="f9870-109">dışı Bir [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) veya [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f9870-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9870-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9870-110">Remarks</span></span>  
 <span data-ttu-id="f9870-111">`GetCLRIdentityManager` işleve bir işaretçi almak için [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="f9870-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9870-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9870-112">Requirements</span></span>  
 <span data-ttu-id="f9870-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9870-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9870-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f9870-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9870-115">**Kitaplık:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="f9870-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="f9870-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9870-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9870-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9870-117">See also</span></span>

- [<span data-ttu-id="f9870-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f9870-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
