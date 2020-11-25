---
title: ICLRDataTarget::Request Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
ms.openlocfilehash: 4d0cf22b4b0644d6b25d6b3ef884718cb9ca1e42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723798"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="7ee1f-102">ICLRDataTarget::Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ee1f-102">ICLRDataTarget::Request Method</span></span>

<span data-ttu-id="7ee1f-103">Uygulama tarafından tanımlanan bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ee1f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7ee1f-104">Syntax</span></span>  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ee1f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ee1f-105">Parameters</span></span>  

 `reqCode`  
 <span data-ttu-id="7ee1f-106">'ndaki Kullanıcı tanımlı.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="7ee1f-107">'ndaki Gelen istek için kullanılan giriş arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="7ee1f-108">'ndaki İsteği içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="7ee1f-109">'ndaki Yanıt için kullanılan çıkış arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="7ee1f-110">dışı Yanıtı içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ee1f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ee1f-111">Remarks</span></span>  

 <span data-ttu-id="7ee1f-112">`Request`Yöntemi, belirtilmeyen özel işlemlerin eklenmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="7ee1f-113">Diğer bir deyişle, bu yöntem, arabirim tanımının düzeltilmesi gerekmeden genişletilebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="7ee1f-114">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ee1f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ee1f-115">Requirements</span></span>  

 <span data-ttu-id="7ee1f-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ee1f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ee1f-117">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="7ee1f-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7ee1f-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7ee1f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ee1f-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ee1f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee1f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ee1f-120">See also</span></span>

- [<span data-ttu-id="7ee1f-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ee1f-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
