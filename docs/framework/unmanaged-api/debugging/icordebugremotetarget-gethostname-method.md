---
title: ICorDebugRemoteTarget::GetHostName Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
ms.openlocfilehash: f177d441da3bd967750781e487d9fed42bc132f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791943"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="c080e-102">ICorDebugRemoteTarget::GetHostName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c080e-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="c080e-103">Uzaktan hata ayıklama hedef makinesinin tam etki alanı adını veya IPv4 adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c080e-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="c080e-104">IPV6 Şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="c080e-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c080e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c080e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="c080e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c080e-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="c080e-107">'ndaki `szHostName` arabelleğinin karakter cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c080e-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="c080e-108">Bu parametre 0 (sıfır) ise, `szHostName` null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c080e-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="c080e-109">dışı Ana bilgisayar adı veya IP adresi içinde null Sonlandırıcı dahil olmak üzere karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="c080e-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="c080e-110">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="c080e-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="c080e-111">dışı Ana bilgisayar adını veya IP adresini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="c080e-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c080e-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c080e-112">Return Value</span></span>  
 <span data-ttu-id="c080e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c080e-113">S_OK</span></span>  
 <span data-ttu-id="c080e-114">Ana bilgisayar adı veya IP adresi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c080e-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="c080e-115">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="c080e-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c080e-116">Ana bilgisayar adı veya IP adresi döndürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="c080e-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c080e-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c080e-117">Remarks</span></span>  
 <span data-ttu-id="c080e-118">Bu yöntem, hata ayıklayıcı yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c080e-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="c080e-119">Bu, birden çok çağrı paradigmasını izlemelidir: ilk çağrıda, çağıran `cchHostName` ve `szHostName`için null değerini geçirir ve `pcchHostName` gereken arabelleğin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c080e-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="c080e-120">İkinci çağrıda, daha önce döndürülen boyut `cchHostName`geçirilir ve `szHostName`uygun boyutta bir arabellek geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c080e-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c080e-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c080e-121">Requirements</span></span>  
 <span data-ttu-id="c080e-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c080e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c080e-123">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="c080e-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c080e-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c080e-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c080e-125">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c080e-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c080e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c080e-126">See also</span></span>

- [<span data-ttu-id="c080e-127">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c080e-127">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="c080e-128">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c080e-128">ICorDebug Interface</span></span>](icordebug-interface.md)
