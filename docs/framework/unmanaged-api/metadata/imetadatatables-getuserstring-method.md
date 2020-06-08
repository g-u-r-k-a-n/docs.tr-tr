---
title: IMetaDataTables::GetUserString Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserString
helpviewer_keywords:
- IMetaDataTables::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 35b8f0d6-9aba-4714-adb2-62020a38fb7e
topic_type:
- apiref
ms.openlocfilehash: 21ce66722e069573b651ada950b64ef6d97220fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501150"
---
# <a name="imetadatatablesgetuserstring-method"></a><span data-ttu-id="55905-102">IMetaDataTables::GetUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="55905-102">IMetaDataTables::GetUserString Method</span></span>

<span data-ttu-id="55905-103">Geçerli kapsamdaki dize sütununda belirtilen dizinde sabit kodlanmış dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="55905-103">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>

## <a name="syntax"></a><span data-ttu-id="55905-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="55905-104">Syntax</span></span>

```cpp
HRESULT GetUserString (
    [in]  ULONG       ixUserString,
    [out] ULONG       *pcbData,
    [out] const void  **ppData
);
```

## <a name="parameters"></a><span data-ttu-id="55905-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55905-105">Parameters</span></span>

`ixUserString`\
<span data-ttu-id="55905-106">'ndaki Sabit kodlanmış dizenin alınacağı dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="55905-106">[in] The index value from which the hard-coded string will be retrieved.</span></span>

`pcbData`\
<span data-ttu-id="55905-107">dışı Boyutu için bir işaretçi `ppData` .</span><span class="sxs-lookup"><span data-stu-id="55905-107">[out] A pointer to the size of `ppData`.</span></span>

`ppData`\
<span data-ttu-id="55905-108">dışı Döndürülen dizeye bir işaretçi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="55905-108">[out] A pointer to a pointer to the returned string.</span></span>

## <a name="requirements"></a><span data-ttu-id="55905-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55905-109">Requirements</span></span>

<span data-ttu-id="55905-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55905-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="55905-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="55905-111">**Header:** Cor.h</span></span>

<span data-ttu-id="55905-112">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="55905-112">**Library:** Used as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="55905-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55905-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="55905-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55905-114">See also</span></span>

- [<span data-ttu-id="55905-115">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55905-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="55905-116">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55905-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
