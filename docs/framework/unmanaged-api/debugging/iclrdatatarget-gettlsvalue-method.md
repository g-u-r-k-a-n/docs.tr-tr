---
title: ICLRDataTarget::GetTLSValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
ms.openlocfilehash: 205ad3af81fb6fabda5cbe291536f8858999f831
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113696"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="153f2-102">ICLRDataTarget::GetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="153f2-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="153f2-103">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel depolama alanından (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="153f2-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="153f2-104">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="153f2-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="153f2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="153f2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="153f2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="153f2-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="153f2-107">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="153f2-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="153f2-108">'ndaki Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="153f2-108">[in] The index of the location.</span></span> <span data-ttu-id="153f2-109">Bu değer, belirtilen iş parçacığının yerel deposunda geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="153f2-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="153f2-110">dışı Verilen TLS konumundan döndürülen değeri belirten `CLRDATA_ADDRESS` değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="153f2-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="153f2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="153f2-111">Remarks</span></span>  
 <span data-ttu-id="153f2-112">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="153f2-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="153f2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="153f2-113">Requirements</span></span>  
 <span data-ttu-id="153f2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="153f2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="153f2-115">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="153f2-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="153f2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="153f2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="153f2-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="153f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="153f2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="153f2-118">See also</span></span>

- [<span data-ttu-id="153f2-119">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="153f2-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
