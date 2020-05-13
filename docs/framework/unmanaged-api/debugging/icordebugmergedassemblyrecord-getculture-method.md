---
title: 'Icordebugmergedassemblyrecord:: GetCulture yöntemi'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: f73aac169cc048a87aca3bfc325cf8c6243012e9
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207866"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="39ef3-102">Icordebugmergedassemblyrecord:: GetCulture yöntemi</span><span class="sxs-lookup"><span data-stu-id="39ef3-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="39ef3-103">Derlemenin kültür adı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="39ef3-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39ef3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39ef3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39ef3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39ef3-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="39ef3-106">'ndaki Arabellekteki karakterlerin sayısı `szCulture` .</span><span class="sxs-lookup"><span data-stu-id="39ef3-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="39ef3-107">dışı Gerçekte arabelleğe yazılan karakterlerin sayısı `szCulture` .</span><span class="sxs-lookup"><span data-stu-id="39ef3-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="39ef3-108">dışı Kültür adını içeren bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="39ef3-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39ef3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39ef3-109">Remarks</span></span>  
 <span data-ttu-id="39ef3-110">Kültür adı, "en-US" (Ingilizce (Birleşik Devletler) kültürü için) veya "nötr" (nötr kültür için) gibi bir kültürü tanımlayan benzersiz bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="39ef3-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39ef3-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="39ef3-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39ef3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39ef3-112">Requirements</span></span>  
 <span data-ttu-id="39ef3-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39ef3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39ef3-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="39ef3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39ef3-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="39ef3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39ef3-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39ef3-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39ef3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39ef3-117">See also</span></span>

- [<span data-ttu-id="39ef3-118">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39ef3-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="39ef3-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="39ef3-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
