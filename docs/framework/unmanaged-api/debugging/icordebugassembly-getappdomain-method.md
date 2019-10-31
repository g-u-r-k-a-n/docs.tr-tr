---
title: ICorDebugAssembly::GetAppDomain Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
ms.openlocfilehash: 53042e722809a6574396648529c677d749154716
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132735"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="74e6f-102">ICorDebugAssembly::GetAppDomain Metodu</span><span class="sxs-lookup"><span data-stu-id="74e6f-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="74e6f-103">Bu `ICorDebugAssembly` örneğini içeren uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="74e6f-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74e6f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74e6f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74e6f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74e6f-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="74e6f-106">dışı Uygulama etki alanını temsil eden ICorDebugAppDomain arabiriminin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="74e6f-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74e6f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74e6f-107">Remarks</span></span>  
 <span data-ttu-id="74e6f-108">Bu derleme sistem bütünleştirilmiş kodu ise, `GetAppDomain` null döndürür.</span><span class="sxs-lookup"><span data-stu-id="74e6f-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74e6f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74e6f-109">Requirements</span></span>  
 <span data-ttu-id="74e6f-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74e6f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74e6f-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="74e6f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74e6f-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="74e6f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74e6f-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74e6f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
