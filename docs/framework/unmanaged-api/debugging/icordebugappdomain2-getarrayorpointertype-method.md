---
description: ': ICorDebugAppDomain2:: GetArrayOrPointerType yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugAppDomain2::GetArrayOrPointerType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: e42d105e807bdb8c81f2d6f8ef6c2f65a4081d98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754231"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a><span data-ttu-id="7d72f-103">ICorDebugAppDomain2::GetArrayOrPointerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d72f-103">ICorDebugAppDomain2::GetArrayOrPointerType Method</span></span>

<span data-ttu-id="7d72f-104">Belirtilen türde bir diziyi veya belirtilen türe bir işaretçi ya da başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="7d72f-104">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d72f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d72f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d72f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d72f-106">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="7d72f-107">'ndaki Oluşturulacak temel yerel türü (bir dizi, işaretçi veya başvuru) belirten CorElementType numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="7d72f-107">[in] A value of the CorElementType enumeration that specifies the underlying native type (an array, pointer, or reference) to be created.</span></span>  
  
 `nRank`  
 <span data-ttu-id="7d72f-108">'ndaki Dizinin derece (yani boyut sayısı).</span><span class="sxs-lookup"><span data-stu-id="7d72f-108">[in] The rank (that is, number of dimensions) of the array.</span></span> <span data-ttu-id="7d72f-109">`elementType`Bir işaretçi veya başvuru türü belirtiyorsa bu değer 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d72f-109">This value must be 0 if `elementType` specifies a pointer or reference type.</span></span>  
  
 `pTypeArg`  
 <span data-ttu-id="7d72f-110">'ndaki Oluşturulacak dizi, işaretçi veya başvurunun türünü temsil eden ICorDebugType nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d72f-110">[in] A pointer to an ICorDebugType object that represents the type of array, pointer, or reference to be created.</span></span>  
  
 `ppType`  
 <span data-ttu-id="7d72f-111">dışı `ICorDebugType` Oluşturulan diziyi, işaretçi türünü veya başvuru türünü temsil eden nesnenin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d72f-111">[out] A pointer to the address of an `ICorDebugType` object that represents the constructed array, pointer type, or reference type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d72f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d72f-112">Remarks</span></span>  

 <span data-ttu-id="7d72f-113">*ElementType* değeri aşağıdakilerden biri olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="7d72f-113">The value of *elementType* must be one of the following:</span></span>  
  
- <span data-ttu-id="7d72f-114">ELEMENT_TYPE_PTR</span><span class="sxs-lookup"><span data-stu-id="7d72f-114">ELEMENT_TYPE_PTR</span></span>  
  
- <span data-ttu-id="7d72f-115">ELEMENT_TYPE_BYREF</span><span class="sxs-lookup"><span data-stu-id="7d72f-115">ELEMENT_TYPE_BYREF</span></span>  
  
- <span data-ttu-id="7d72f-116">ELEMENT_TYPE_ARRAY veya ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="7d72f-116">ELEMENT_TYPE_ARRAY or ELEMENT_TYPE_SZARRAY</span></span>  
  
 <span data-ttu-id="7d72f-117">*ElementType* değeri ELEMENT_TYPE_PTR veya element_type_byref, *nRank* sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d72f-117">If the value of *elementType* is ELEMENT_TYPE_PTR or ELEMENT_TYPE_BYREF, *nRank* must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d72f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d72f-118">Requirements</span></span>  

 <span data-ttu-id="7d72f-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d72f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d72f-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d72f-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d72f-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7d72f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d72f-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d72f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
