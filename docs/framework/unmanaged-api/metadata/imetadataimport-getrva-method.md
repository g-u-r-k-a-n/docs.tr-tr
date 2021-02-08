---
description: ': IMetaDataImport:: GetRVA metodu hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetRVA Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 8d6439bcad50a6311e7bb1408f4c86144a5026ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789170"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="16548-103">IMetaDataImport::GetRVA Metodu</span><span class="sxs-lookup"><span data-stu-id="16548-103">IMetaDataImport::GetRVA Method</span></span>

<span data-ttu-id="16548-104">Belirtilen belirteçle temsil edilen metodun veya alanın göreli sanal adresini (RVA) ve uygulama bayraklarını alır.</span><span class="sxs-lookup"><span data-stu-id="16548-104">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16548-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16548-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16548-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16548-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="16548-107">'ndaki İçin RVA 'yu döndürecek kod nesnesini temsil eden bir MethodDef veya FieldDef meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="16548-107">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="16548-108">Belirteç bir FieldDef ise, alan genel bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="16548-108">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="16548-109">dışı Belirteç tarafından temsil edilen kod nesnesinin göreli sanal adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="16548-109">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="16548-110">dışı Yöntemi için uygulama bayraklarının bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="16548-110">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="16548-111">Bu değer, [CorMethodImpl](cormethodimpl-enumeration.md) numaralandırmasındaki bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="16548-111">This value is a bitmask from the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="16548-112">Değeri `pdwImplFlags` yalnızca `tk` bir MethodDef belirtecidir geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="16548-112">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16548-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16548-113">Requirements</span></span>  

 <span data-ttu-id="16548-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16548-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16548-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="16548-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16548-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="16548-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16548-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16548-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16548-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16548-118">See also</span></span>

- [<span data-ttu-id="16548-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16548-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="16548-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16548-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
