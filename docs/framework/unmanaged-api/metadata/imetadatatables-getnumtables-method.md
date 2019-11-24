---
title: IMetaDataTables::GetNumTables Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNumTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNumTables
helpviewer_keywords:
- GetNumTables method [.NET Framework metadata]
- IMetaDataTables::GetNumTables method [.NET Framework metadata]
ms.assetid: 8196f2a3-bbf2-45d3-a6cd-74502c356644
topic_type:
- apiref
ms.openlocfilehash: ab864b251a989056bc34b2c7c6658964556f9ac1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449504"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="a3be0-102">IMetaDataTables::GetNumTables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3be0-102">IMetaDataTables::GetNumTables Method</span></span>
<span data-ttu-id="a3be0-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span><span class="sxs-lookup"><span data-stu-id="a3be0-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3be0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3be0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3be0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3be0-105">Parameters</span></span>  
 `pcTables`  
 <span data-ttu-id="a3be0-106">[out] A pointer to the number of tables in the current instance scope.</span><span class="sxs-lookup"><span data-stu-id="a3be0-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3be0-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3be0-107">Requirements</span></span>  
 <span data-ttu-id="a3be0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3be0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3be0-109">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a3be0-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a3be0-110">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3be0-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a3be0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3be0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3be0-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3be0-112">See also</span></span>

- [<span data-ttu-id="a3be0-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3be0-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="a3be0-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3be0-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
