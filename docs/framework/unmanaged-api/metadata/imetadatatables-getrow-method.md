---
title: IMetaDataTables::GetRow Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 01c4c1734aa0701f787a2b73787e9e4781901d42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672662"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="1355a-102">IMetaDataTables::GetRow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1355a-102">IMetaDataTables::GetRow Method</span></span>

<span data-ttu-id="1355a-103">Belirtilen tablo dizinindeki tabloda belirtilen satır dizinindeki satırı alır.</span><span class="sxs-lookup"><span data-stu-id="1355a-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1355a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1355a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1355a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1355a-105">Parameters</span></span>  

 `ixTbl`  
 <span data-ttu-id="1355a-106">'ndaki Satırın alınacağı tablonun dizini.</span><span class="sxs-lookup"><span data-stu-id="1355a-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="1355a-107">'ndaki Alınacak satırın dizini.</span><span class="sxs-lookup"><span data-stu-id="1355a-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="1355a-108">dışı Satır işaretçisinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1355a-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1355a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1355a-109">Remarks</span></span>  

  <span data-ttu-id="1355a-110">Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="1355a-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="1355a-111">GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği".</span><span class="sxs-lookup"><span data-stu-id="1355a-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="1355a-112">Belgeler çevrimiçi olarak kullanılabilir; bkz. [ecma C# ve ortak dil altyapısı standartları](../../../standard/components.md#applicable-standards) ve [standart ECMA-335-ortak DIL altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="1355a-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1355a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1355a-113">Requirements</span></span>  

 <span data-ttu-id="1355a-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1355a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1355a-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1355a-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1355a-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1355a-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1355a-117">**.NET Framework sürümleri**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1355a-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1355a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1355a-118">See also</span></span>

- [<span data-ttu-id="1355a-119">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1355a-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="1355a-120">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1355a-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
