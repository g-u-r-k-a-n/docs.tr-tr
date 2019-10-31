---
title: StrongNameKeyGenEx İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
ms.openlocfilehash: 63ddd90f3a8090853d10f03052915d10e1503ea6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125211"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="9c1c9-102">StrongNameKeyGenEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="9c1c9-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="9c1c9-103">Tanımlayıcı ad kullanımı için belirtilen anahtar boyutuyla yeni bir ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="9c1c9-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-104">This function has been deprecated.</span></span> <span data-ttu-id="9c1c9-105">Bunun yerine [ICLRStrongName:: StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c1c9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c1c9-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c1c9-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c1c9-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="9c1c9-108">'ndaki İstenen anahtar kapsayıcısı adı.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-108">[in] The requested key container name.</span></span> <span data-ttu-id="9c1c9-109">`wszKeyContainer`, boş olmayan bir dize veya geçici bir ad oluşturmak için null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9c1c9-110">'ndaki Anahtarın kaydedilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="9c1c9-111">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="9c1c9-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="9c1c9-112">0x00000000-`wszKeyContainer` bir geçici anahtar kapsayıcısı adı oluşturmak için null olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="9c1c9-113">0x00000001 (`SN_LEAVE_KEY`)-anahtarın kayıtlı olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="9c1c9-114">'ndaki Anahtarın bit cinsinden istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="9c1c9-115">dışı Döndürülen ortak/özel anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="9c1c9-116">dışı `ppbKeyBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c1c9-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9c1c9-117">Return Value</span></span>  
 <span data-ttu-id="9c1c9-118">başarılı tamamlamada `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c1c9-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c1c9-119">Remarks</span></span>  
 <span data-ttu-id="9c1c9-120">1,0 ve 1,1 .NET Framework sürümleri, bir derlemeyi güçlü bir adla imzalamak için 1024 bit `dwKeySize` gerektirir; sürüm 2,0, 2048 bit anahtarlar için destekler.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="9c1c9-121">Anahtar alındıktan sonra, ayrılan belleği serbest bırakmak için [StrongNameFreeBuffer](strongnamefreebuffer-function.md) işlevini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="9c1c9-122">`StrongNameKeyGenEx` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c1c9-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c1c9-123">Requirements</span></span>  
 <span data-ttu-id="9c1c9-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c1c9-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c1c9-125">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="9c1c9-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9c1c9-126">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9c1c9-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c1c9-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c1c9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1c9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c1c9-128">See also</span></span>

- [<span data-ttu-id="9c1c9-129">StrongNameKeyGenEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c1c9-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="9c1c9-130">StrongNameKeyGen Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c1c9-130">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="9c1c9-131">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c1c9-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
