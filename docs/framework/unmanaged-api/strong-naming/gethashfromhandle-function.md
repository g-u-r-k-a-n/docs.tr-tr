---
title: GetHashFromHandle İşlevi
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
ms.openlocfilehash: 904dcb707e704cfec2dba4e6587f7e3acaf7b538
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732339"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="feea2-102">GetHashFromHandle İşlevi</span><span class="sxs-lookup"><span data-stu-id="feea2-102">GetHashFromHandle Function</span></span>

<span data-ttu-id="feea2-103">Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="feea2-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="feea2-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="feea2-104">This function has been deprecated.</span></span> <span data-ttu-id="feea2-105">Bunun yerine [ICLRStrongName:: GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="feea2-105">Use the [ICLRStrongName::GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feea2-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="feea2-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="feea2-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="feea2-107">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="feea2-108">'ndaki Karma hale getirilen dosyanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="feea2-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="feea2-109">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="feea2-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="feea2-110">Varsayılan algoritma için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="feea2-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="feea2-111">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="feea2-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="feea2-112">'ndaki İstenen en büyük boyut `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="feea2-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="feea2-113">dışı Döndürülen bayt cinsinden boyutu `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="feea2-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feea2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feea2-114">Requirements</span></span>  

 <span data-ttu-id="feea2-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feea2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feea2-116">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="feea2-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="feea2-117">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="feea2-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="feea2-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feea2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feea2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="feea2-119">See also</span></span>

- [<span data-ttu-id="feea2-120">GetHashFromHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feea2-120">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="feea2-121">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="feea2-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
