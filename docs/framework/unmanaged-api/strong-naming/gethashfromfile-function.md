---
title: GetHashFromFile İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
ms.openlocfilehash: ee9f9cd9a9f35c6c54497ad382bb6f9817d186bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732378"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="c8e6e-102">GetHashFromFile İşlevi</span><span class="sxs-lookup"><span data-stu-id="c8e6e-102">GetHashFromFile Function</span></span>

<span data-ttu-id="c8e6e-103">Belirtilen dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8e6e-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="c8e6e-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="c8e6e-104">This function has been deprecated.</span></span> <span data-ttu-id="c8e6e-105">Bunun yerine [ICLRStrongName:: GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c8e6e-105">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8e6e-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c8e6e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8e6e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8e6e-107">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="c8e6e-108">'ndaki Karma yapılacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="c8e6e-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c8e6e-109">[in, out] Karma oluşturulurken kullanılacak algoritma.</span><span class="sxs-lookup"><span data-stu-id="c8e6e-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="c8e6e-110">Geçerli algoritmalar Win32 CryptoAPI tarafından tanımlı olanlardır.</span><span class="sxs-lookup"><span data-stu-id="c8e6e-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="c8e6e-111">`piHashAlg`0 olarak ayarlanırsa, CALG_SHA-1 varsayılan algoritma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8e6e-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c8e6e-112">dışı Oluşturulan karmayı içeren bir bayt dizisi.</span><span class="sxs-lookup"><span data-stu-id="c8e6e-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c8e6e-113">'ndaki İşaret eden arabelleğin en büyük boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="c8e6e-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c8e6e-114">dışı Döndürülen bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="c8e6e-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8e6e-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8e6e-115">Remarks</span></span>  

 <span data-ttu-id="c8e6e-116">Bu işlev, [GetHashFromFileW](gethashfromfilew-function.md)ile aynıdır, ancak dosya adı belirtimi UNICODE yerine ANSI olur.</span><span class="sxs-lookup"><span data-stu-id="c8e6e-116">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8e6e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8e6e-117">Requirements</span></span>  

 <span data-ttu-id="c8e6e-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8e6e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8e6e-119">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="c8e6e-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c8e6e-120">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c8e6e-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c8e6e-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8e6e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e6e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8e6e-122">See also</span></span>

- [<span data-ttu-id="c8e6e-123">GetHashFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8e6e-123">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="c8e6e-124">GetHashFromFileW Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8e6e-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="c8e6e-125">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8e6e-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
