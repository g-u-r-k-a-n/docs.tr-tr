---
title: IMetaDataTables::GetNextString Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
ms.openlocfilehash: b79dbdd64ac171d1bc4cd30b96ee76b4a853afb6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727256"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="68091-102">IMetaDataTables::GetNextString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68091-102">IMetaDataTables::GetNextString Method</span></span>

<span data-ttu-id="68091-103">Geçerli tablo sütunundaki sonraki dizenin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="68091-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68091-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="68091-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68091-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68091-105">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="68091-106">'ndaki Dize tablosu sütunundan dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="68091-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="68091-107">dışı Sütundaki sonraki dizenin dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="68091-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68091-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68091-108">Requirements</span></span>  

 <span data-ttu-id="68091-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68091-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68091-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="68091-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68091-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="68091-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="68091-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68091-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68091-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68091-113">See also</span></span>

- [<span data-ttu-id="68091-114">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68091-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="68091-115">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68091-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
