---
title: 'ICorDebugSymbolProvider:: GetTypeProps yöntemi'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: 4738d35aabbc2197c796405e0657607f75ff685d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694509"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="ec4ee-102">ICorDebugSymbolProvider:: GetTypeProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="ec4ee-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>

<span data-ttu-id="ec4ee-103">Bir vtable içindeki göreli bir sanal adres (RVA) verilen genel parametrelerinin imza sayısı gibi bir türün özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ec4ee-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec4ee-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ec4ee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec4ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec4ee-105">Parameters</span></span>  

 `tableRva`  
 <span data-ttu-id="ec4ee-106">'ndaki Vtable içindeki göreli bir sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="ec4ee-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="ec4ee-107">'ndaki `signature` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="ec4ee-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="ec4ee-108">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ec4ee-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="ec4ee-109">dışı dışı Döndürülen dizinin boyutuna yönelik bir işaretçi `signature` .</span><span class="sxs-lookup"><span data-stu-id="ec4ee-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="ec4ee-110">dışı Tüm genel parametrelerin TypeSpec imzalarını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="ec4ee-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec4ee-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec4ee-111">Remarks</span></span>  

 <span data-ttu-id="ec4ee-112">Türün dizisinin gerekli boyutunu almak için `signature` , `cbSignature` bağımsız değişkenini 0 ve `signature` **null** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ec4ee-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="ec4ee-113">Yöntemi döndüğünde, `pcbSignature` dizi için gereken bayt sayısını içerir `signature` .</span><span class="sxs-lookup"><span data-stu-id="ec4ee-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec4ee-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec4ee-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec4ee-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec4ee-115">Requirements</span></span>  

 <span data-ttu-id="ec4ee-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec4ee-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec4ee-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ec4ee-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec4ee-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ec4ee-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec4ee-119">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec4ee-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4ee-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec4ee-120">See also</span></span>

- [<span data-ttu-id="ec4ee-121">GetMethodProps Metodu</span><span class="sxs-lookup"><span data-stu-id="ec4ee-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="ec4ee-122">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec4ee-122">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ec4ee-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ec4ee-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
