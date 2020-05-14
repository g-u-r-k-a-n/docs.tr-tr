---
title: 'ICorDebugVariableSymbol:: SetValue yöntemi'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: 38afd355938ec1beb1dbfd33de36116d25b07b4e
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397069"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="63b0e-102">ICorDebugVariableSymbol:: SetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="63b0e-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="63b0e-103">Bir bayt dizisinin değerini bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="63b0e-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63b0e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63b0e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63b0e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63b0e-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="63b0e-106">'ndaki Değişkenin değeri ayarlanacak başlangıç boşluğu.</span><span class="sxs-lookup"><span data-stu-id="63b0e-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="63b0e-107">Bu parametre, bir nesnedeki üye alanlarına yazılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63b0e-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="63b0e-108">'ndaki Bağlamını yeni değeri yansıtacak şekilde güncellenmesi gereken iş parçacığının iş parçacığı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="63b0e-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="63b0e-109">'ndaki İş parçacığı bağlamının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="63b0e-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="63b0e-110">'ndaki Değeri yazmak için kullanılan iş parçacığı bağlamı.</span><span class="sxs-lookup"><span data-stu-id="63b0e-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="63b0e-111">'ndaki Arabelleğin bayt cinsinden boyutu `pValue` .</span><span class="sxs-lookup"><span data-stu-id="63b0e-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="63b0e-112">'ndaki Ayarlanacak değeri içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="63b0e-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63b0e-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63b0e-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63b0e-114">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="63b0e-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63b0e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63b0e-115">Requirements</span></span>  
 <span data-ttu-id="63b0e-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63b0e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63b0e-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="63b0e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63b0e-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="63b0e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63b0e-119">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63b0e-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b0e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63b0e-120">See also</span></span>

- [<span data-ttu-id="63b0e-121">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63b0e-121">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="63b0e-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="63b0e-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
