---
title: ICLRStrongName::StrongNameTokenFromAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
ms.openlocfilehash: 90a7e60e35e1fc555681102ffa62967eb5ac01fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671544"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="c9793-102">ICLRStrongName::StrongNameTokenFromAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9793-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>

<span data-ttu-id="c9793-103">Belirtilen derleme dosyasından bir tanımlayıcı ad belirteci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c9793-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9793-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c9793-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9793-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9793-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="c9793-106">'ndaki Bütünleştirilmiş kod için Taşınabilir çalıştırılabilir (PE) dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="c9793-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="c9793-107">dışı Döndürülen tanımlayıcı ad belirteci.</span><span class="sxs-lookup"><span data-stu-id="c9793-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="c9793-108">dışı Tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c9793-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9793-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c9793-109">Return Value</span></span>  

 <span data-ttu-id="c9793-110">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="c9793-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9793-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9793-111">Remarks</span></span>  

 <span data-ttu-id="c9793-112">Tanımlayıcı ad belirteci, ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="c9793-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="c9793-113">Belirteç, derlemeyi imzalamak için kullanılan ortak anahtardan oluşturulan 64 bitlik bir karmadır.</span><span class="sxs-lookup"><span data-stu-id="c9793-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="c9793-114">Belirteç, derlemenin tanımlayıcı adının bir parçasıdır ve derleme meta verilerinden okunabilir.</span><span class="sxs-lookup"><span data-stu-id="c9793-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="c9793-115">Belirteç oluşturulduktan sonra, ayrılan belleği serbest bırakmak için [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9793-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9793-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9793-116">Requirements</span></span>  

 <span data-ttu-id="c9793-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9793-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9793-118">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c9793-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c9793-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c9793-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9793-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9793-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9793-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9793-121">See also</span></span>

- [<span data-ttu-id="c9793-122">StrongNameTokenFromAssemblyEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9793-122">StrongNameTokenFromAssemblyEx Method</span></span>](iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="c9793-123">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9793-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
