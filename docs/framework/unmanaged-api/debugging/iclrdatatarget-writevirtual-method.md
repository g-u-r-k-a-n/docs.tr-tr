---
title: ICLRDataTarget::WriteVirtual Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
ms.openlocfilehash: bd2f67c2d7230d3873b4dc0df73ac1be778a0828
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179103"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="4da59-102">ICLRDataTarget::WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4da59-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="4da59-103">Belirtilen arabellekten belirtilen sanal bellek adresine veri yazar.</span><span class="sxs-lookup"><span data-stu-id="4da59-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da59-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4da59-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4da59-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4da59-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="4da59-106">[içinde] Sanal bellek adresini depolayan bir CLRDATA_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="4da59-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="4da59-107">[içinde] Yazılacak verileri depolayan bir arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4da59-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="4da59-108">[içinde] Yazılacak bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="4da59-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="4da59-109">[çıkış] Yazılan baytların gerçek sayısına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4da59-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4da59-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4da59-110">Requirements</span></span>  
 <span data-ttu-id="4da59-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4da59-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4da59-112">**Üstbilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4da59-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4da59-113">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4da59-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4da59-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4da59-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da59-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4da59-115">See also</span></span>

- [<span data-ttu-id="4da59-116">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4da59-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
