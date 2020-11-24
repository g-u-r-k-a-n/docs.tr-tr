---
title: IMetaDataTables::GetTableInfo Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
ms.openlocfilehash: 65943ac169106a95feaff7d44017444e65764b60
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672545"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="91ce5-102">IMetaDataTables::GetTableInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="91ce5-102">IMetaDataTables::GetTableInfo Method</span></span>

<span data-ttu-id="91ce5-103">Belirtilen tablonun adını, satır boyutunu, satır sayısını, sütun sayısını ve anahtar sütun dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="91ce5-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ce5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="91ce5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91ce5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91ce5-105">Parameters</span></span>  

 `ixTbl`  
 <span data-ttu-id="91ce5-106">'ndaki Özelliklerini döndürülecek tablonun tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="91ce5-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="91ce5-107">dışı Bir tablo satırının bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="91ce5-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="91ce5-108">dışı Tablodaki satır sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="91ce5-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="91ce5-109">dışı Tablodaki sütun sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="91ce5-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="91ce5-110">dışı Anahtar sütununun dizinine yönelik bir işaretçi veya tabloda anahtar sütunu yoksa-1.</span><span class="sxs-lookup"><span data-stu-id="91ce5-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="91ce5-111">dışı Tablo adı işaretçisinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="91ce5-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91ce5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91ce5-112">Requirements</span></span>  

 <span data-ttu-id="91ce5-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91ce5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91ce5-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="91ce5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="91ce5-115">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="91ce5-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="91ce5-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91ce5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ce5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91ce5-117">See also</span></span>

- [<span data-ttu-id="91ce5-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91ce5-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="91ce5-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91ce5-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
