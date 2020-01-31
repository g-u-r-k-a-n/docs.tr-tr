---
title: ICorPublishProcess::GetProcessID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
ms.openlocfilehash: 4cc6bbde2c7367c1109ca73e66f2670a56b2cdbe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790552"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="dcffd-102">ICorPublishProcess::GetProcessID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dcffd-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="dcffd-103">Bu işlem için işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="dcffd-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcffd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcffd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcffd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dcffd-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="dcffd-106">dışı Bu [ICorPublishProcess](icorpublishprocess-interface.md) nesnesinin temsil ettiği işlemin tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dcffd-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcffd-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dcffd-107">Requirements</span></span>  
 <span data-ttu-id="dcffd-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcffd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcffd-109">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="dcffd-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="dcffd-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dcffd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcffd-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcffd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcffd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcffd-112">See also</span></span>

- [<span data-ttu-id="dcffd-113">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcffd-113">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
