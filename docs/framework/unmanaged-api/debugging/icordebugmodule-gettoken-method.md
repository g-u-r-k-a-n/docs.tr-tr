---
description: ': ICorDebugModule:: GetToken metodu hakkında daha fazla bilgi edinin'
title: ICorDebugModule::GetToken Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
ms.openlocfilehash: fd1bc4bc397e7f81c77f2fe784c68dbaaceb2695
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660173"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="6e39f-103">ICorDebugModule::GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e39f-103">ICorDebugModule::GetToken Method</span></span>

<span data-ttu-id="6e39f-104">Bu modül için tablo girişi belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="6e39f-104">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e39f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e39f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e39f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e39f-106">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="6e39f-107">dışı `mdModule` Modülün meta verilerine başvuran belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6e39f-107">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e39f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e39f-108">Remarks</span></span>  

 <span data-ttu-id="6e39f-109">Belirteç [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md)ve [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) meta veri alma arabirimlerine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="6e39f-109">The token can be passed to the [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e39f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e39f-110">Requirements</span></span>  

 <span data-ttu-id="6e39f-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e39f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e39f-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6e39f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e39f-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6e39f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e39f-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e39f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e39f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e39f-115">See also</span></span>

- [<span data-ttu-id="6e39f-116">Meta veri</span><span class="sxs-lookup"><span data-stu-id="6e39f-116">Metadata</span></span>](../metadata/index.md)
