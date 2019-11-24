---
title: IMetaDataTables::GetNextUserString Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
ms.openlocfilehash: 44ae2d16563220f8f5b81b6f609dee7df715fd0e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447399"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="1a9bd-102">IMetaDataTables::GetNextUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="1a9bd-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="1a9bd-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a9bd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a9bd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a9bd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a9bd-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="1a9bd-106">[in] An index value from the current string column.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="1a9bd-107">[out] A pointer to the row index of the next string in the column.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a9bd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a9bd-108">Remarks</span></span>  
 <span data-ttu-id="1a9bd-109">We do not recommend the use of this method, because it does not return consistent results.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="1a9bd-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span><span class="sxs-lookup"><span data-stu-id="1a9bd-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="1a9bd-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a9bd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a9bd-112">Requirements</span></span>  
 <span data-ttu-id="1a9bd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a9bd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a9bd-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1a9bd-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a9bd-115">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a9bd-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a9bd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a9bd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a9bd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a9bd-117">See also</span></span>

- [<span data-ttu-id="1a9bd-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a9bd-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="1a9bd-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a9bd-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
