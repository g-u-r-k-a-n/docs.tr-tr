---
title: ICLRStrongName::GetHashFromHandle Metodu
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
ms.openlocfilehash: 19d4518b7ec125df717b2f901bbd92cbd1b659bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135164"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="dad7d-102">ICLRStrongName::GetHashFromHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="dad7d-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="dad7d-103">Belirtilen karma algoritmasını kullanarak, belirtilen dosya tanıtıcısına sahip dosyanın içeriği üzerinde bir karma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dad7d-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dad7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dad7d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dad7d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dad7d-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="dad7d-106">'ndaki Karma hale getirilen dosyanın tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="dad7d-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="dad7d-107">[in, out] Karma algoritmayı belirten bir sabit.</span><span class="sxs-lookup"><span data-stu-id="dad7d-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="dad7d-108">Varsayılan algoritma için sıfır kullanın.</span><span class="sxs-lookup"><span data-stu-id="dad7d-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="dad7d-109">dışı Döndürülen karma arabelleği.</span><span class="sxs-lookup"><span data-stu-id="dad7d-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="dad7d-110">'ndaki İstenen en büyük boyut `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="dad7d-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="dad7d-111">dışı Döndürülen `pbHash`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="dad7d-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dad7d-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dad7d-112">Return Value</span></span>  
 <span data-ttu-id="dad7d-113">Yöntem başarıyla tamamlanırsa `S_OK`; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](https://go.microsoft.com/fwlink/?LinkId=213878) ).</span><span class="sxs-lookup"><span data-stu-id="dad7d-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dad7d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dad7d-114">Requirements</span></span>  
 <span data-ttu-id="dad7d-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dad7d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dad7d-116">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="dad7d-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dad7d-117">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="dad7d-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dad7d-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dad7d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad7d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dad7d-119">See also</span></span>

- [<span data-ttu-id="dad7d-120">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dad7d-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
