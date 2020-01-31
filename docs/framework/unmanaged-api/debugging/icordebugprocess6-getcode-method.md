---
title: ICorDebugProcess6::GetCode Metodu
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: 1588728f486ffb3db583439de05aff34e3dc59f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792276"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="e1c57-102">ICorDebugProcess6::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="e1c57-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="e1c57-103">Belirli bir kod adresindeki yönetilen kodla ilgili bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="e1c57-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1c57-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1c57-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1c57-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1c57-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="e1c57-106">'ndaki Yönetilen kod segmentinin başlangıç adresini belirten [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="e1c57-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="e1c57-107">dışı Yönetilen kod segmentini temsil eden bir "ICorDebugCode" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e1c57-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1c57-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1c57-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1c57-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1c57-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1c57-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1c57-110">Requirements</span></span>  
 <span data-ttu-id="e1c57-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1c57-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1c57-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e1c57-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1c57-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e1c57-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1c57-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1c57-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c57-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1c57-115">See also</span></span>

- [<span data-ttu-id="e1c57-116">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1c57-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="e1c57-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e1c57-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
