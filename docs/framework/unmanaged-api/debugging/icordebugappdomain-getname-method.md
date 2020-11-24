---
title: ICorDebugAppDomain::GetName Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 501a4543940437bfe2a6cb0952aed8184107150c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672168"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="56f57-102">ICorDebugAppDomain::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56f57-102">ICorDebugAppDomain::GetName Method</span></span>

<span data-ttu-id="56f57-103">Uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="56f57-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f57-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="56f57-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56f57-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56f57-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="56f57-106">'ndaki `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="56f57-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="56f57-107">Bu yöntemi sorgu moduna almak için bu değeri sıfır olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="56f57-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="56f57-108">dışı Adın boyutuna veya aslında ' de döndürülen karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="56f57-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="56f57-109">Sorgu modunda, bu değer çağıranın ad için ne kadar büyük bir arabellek ayrılacağını bilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="56f57-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="56f57-110">dışı Uygulama etki alanının adını depolayan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="56f57-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56f57-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56f57-111">Remarks</span></span>  

 <span data-ttu-id="56f57-112">Bir hata ayıklayıcı, `GetName` ad için gereken bir arabellek boyutunu almak üzere yöntemi bir kez çağırır.</span><span class="sxs-lookup"><span data-stu-id="56f57-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="56f57-113">Hata ayıklayıcı arabelleği ayırır ve sonra arabelleği dolduracak ikinci kez yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="56f57-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="56f57-114">Adın boyutunu almak için ilk çağrı *sorgu modu* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="56f57-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f57-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56f57-115">Requirements</span></span>  

 <span data-ttu-id="56f57-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56f57-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56f57-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="56f57-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56f57-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="56f57-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56f57-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56f57-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
