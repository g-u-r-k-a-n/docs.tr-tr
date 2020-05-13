---
title: ICorDebugRegisterSet::GetRegisters Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 40de06d47654337542d2c80dc325f8201335312a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379148"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="30c25-102">ICorDebugRegisterSet::GetRegisters Metodu</span><span class="sxs-lookup"><span data-stu-id="30c25-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="30c25-103">Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="30c25-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30c25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30c25-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30c25-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30c25-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="30c25-106">'ndaki Hangi yazmaç değerlerinin alınacağını belirten bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="30c25-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="30c25-107">Her bit bir kayda karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="30c25-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="30c25-108">Bir bit olarak ayarlandıysa, kaydın değeri alınır; Aksi takdirde, kaydın değeri alınmadı.</span><span class="sxs-lookup"><span data-stu-id="30c25-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="30c25-109">'ndaki Alınacak kayıt değerlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="30c25-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="30c25-110">dışı `CORDB_REGISTER`Her biri bir yazmaç değeri alan bir nesne dizisi.</span><span class="sxs-lookup"><span data-stu-id="30c25-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30c25-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30c25-111">Remarks</span></span>  
 <span data-ttu-id="30c25-112">Dizinin boyutu, bit maskesinde bir tane olarak ayarlanan bit sayısına eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30c25-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="30c25-113">`regCount`Parametresi, kayıt değerlerini alacak arabellekteki öğelerin sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="30c25-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="30c25-114">Değer, `regCount` maskenin gösterdiği kayıt sayısı için çok küçük ise, üstteki numaralandırılmış Yazmaçları kümeden kesilecek.</span><span class="sxs-lookup"><span data-stu-id="30c25-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="30c25-115">`regCount`Değer çok büyükse, kullanılmamış `regBuffer` öğeler değiştirilmemiş olur.</span><span class="sxs-lookup"><span data-stu-id="30c25-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="30c25-116">Bit maskesi kullanılamayan bir kaydı belirtirse, `GetRegisters` Bu kayıt için belirsiz bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="30c25-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30c25-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30c25-117">Requirements</span></span>  
 <span data-ttu-id="30c25-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30c25-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30c25-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="30c25-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30c25-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="30c25-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30c25-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30c25-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c25-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30c25-122">See also</span></span>

- [<span data-ttu-id="30c25-123">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30c25-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="30c25-124">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30c25-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
