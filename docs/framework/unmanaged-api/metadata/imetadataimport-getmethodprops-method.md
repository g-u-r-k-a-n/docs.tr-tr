---
title: IMetaDataImport::GetMethodProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
ms.openlocfilehash: 4a258ce9121a287929ca5bc39c480f1ca2596e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437466"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="93391-102">IMetaDataImport::GetMethodProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93391-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="93391-103">Belirtilen MethodDef belirtecinin başvurduğu metotla ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="93391-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93391-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93391-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93391-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93391-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="93391-106">'ndaki Meta verilerini döndürecek yöntemi temsil eden MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="93391-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="93391-107">dışı Yöntemi uygulayan türü temsil eden bir TypeDef belirtecinin Işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="93391-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="93391-108">dışı Metodun adına sahip bir arabelleğin Işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="93391-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="93391-109">'ndaki İstenen `szMethod`boyutu.</span><span class="sxs-lookup"><span data-stu-id="93391-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="93391-110">dışı `szMethod`geniş karakterdeki boyut Işaretçisi veya kesme durumunda, yöntem adındaki geniş karakterlerin gerçek sayısı.</span><span class="sxs-lookup"><span data-stu-id="93391-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="93391-111">dışı Yöntemiyle ilişkili bayrakların bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="93391-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="93391-112">dışı Metodun ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="93391-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="93391-113">dışı `ppvSigBlob`bayt cinsinden boyut Işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="93391-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="93391-114">dışı Metodun göreli sanal adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="93391-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="93391-115">dışı Yöntemi için herhangi bir uygulama bayraklarının bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="93391-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93391-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93391-116">Requirements</span></span>  
 <span data-ttu-id="93391-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93391-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93391-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="93391-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="93391-119">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="93391-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="93391-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93391-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93391-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93391-121">See also</span></span>

- [<span data-ttu-id="93391-122">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93391-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="93391-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93391-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
