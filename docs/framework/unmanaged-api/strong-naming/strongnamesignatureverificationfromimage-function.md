---
title: StrongNameSignatureVerificationFromImage İşlevi
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
ms.openlocfilehash: 5c12ca20deee06fcaca68365644fd9dff95379ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121154"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="ca6c6-102">StrongNameSignatureVerificationFromImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="ca6c6-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="ca6c6-103">Zaten bellekle eşlenmiş bir derlemenin ilişkili ortak anahtar için geçerli olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="ca6c6-104">Bu işlev kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-104">This function has been deprecated.</span></span> <span data-ttu-id="ca6c6-105">Bunun yerine [ICLRStrongName:: Strongnamedoğrulamaları Icationfromımage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca6c6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca6c6-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca6c6-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca6c6-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="ca6c6-108">'ndaki Eşlenen derleme bildiriminin göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="ca6c6-109">'ndaki Eşlenen görüntünün bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="ca6c6-110">'ndaki Doğrulama davranışını etkileyen bayraklar.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="ca6c6-111">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ca6c6-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="ca6c6-112">`SN_INFLAG_FORCE_VER` (0x00000001)-kayıt defteri ayarlarını geçersiz kılmak gerekli olsa bile doğrulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="ca6c6-113">`SN_INFLAG_INSTALL` (0x00000002)-Bu görüntüde gerçekleştirilen ilk doğrulamanın olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="ca6c6-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004)-önbelleğin yalnızca yönetici ayrıcalıklarına sahip olan kullanıcılar için erişime izin verolacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="ca6c6-115">`SN_INFLAG_USER_ACCESS` (0x00000008)-derlemenin yalnızca geçerli kullanıcı için erişilebilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="ca6c6-116">`SN_INFLAG_ALL_ACCESS` (0x00000010)-önbelleğin erişim kısıtlaması garantisi sunmayacak olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="ca6c6-117">`SN_INFLAG_RUNTIME` (0x80000000)-iç hata ayıklama için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="ca6c6-118">dışı Ek çıkış bilgileri için bayrak.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="ca6c6-119">Aşağıdaki değer desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ca6c6-119">The following value is supported:</span></span>  
  
- <span data-ttu-id="ca6c6-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-Bu değer, kayıt defteri ayarları nedeniyle doğrulamanın başarılı olduğunu belirtmek için `false` olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca6c6-121">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ca6c6-121">Return Value</span></span>  
 <span data-ttu-id="ca6c6-122">başarılı tamamlamada `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca6c6-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca6c6-123">Remarks</span></span>  
 <span data-ttu-id="ca6c6-124">`StrongNameSignatureVerificationFromImage` işlevi başarıyla tamamlanmazsa, en son oluşturulan hatayı almak için [StrongNameErrorInfo](strongnameerrorinfo-function.md) işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca6c6-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca6c6-125">Requirements</span></span>  
 <span data-ttu-id="ca6c6-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca6c6-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca6c6-127">**Üst bilgi:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ca6c6-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ca6c6-128">**Kitaplık:** Mscoree. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ca6c6-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="ca6c6-129">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca6c6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca6c6-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca6c6-130">See also</span></span>

- [<span data-ttu-id="ca6c6-131">StrongNameSignatureVerificationFromImage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca6c6-131">StrongNameSignatureVerificationFromImage Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="ca6c6-132">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca6c6-132">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
