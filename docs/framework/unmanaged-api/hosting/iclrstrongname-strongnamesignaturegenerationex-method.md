---
description: ': ICLRStrongName:: StrongNameSignatureGenerationEx Yöntemi hakkında daha fazla bilgi edinin'
title: ICLRStrongName::StrongNameSignatureGenerationEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
ms.openlocfilehash: 911f55aa509c25eb0d95d6d2a31c9f715af2080d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781876"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="33dd3-103">ICLRStrongName::StrongNameSignatureGenerationEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33dd3-103">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>

<span data-ttu-id="33dd3-104">Belirtilen bayrağa göre belirtilen derleme için bir tanımlayıcı ad imzası üretir.</span><span class="sxs-lookup"><span data-stu-id="33dd3-104">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33dd3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33dd3-105">Syntax</span></span>  
  
```cpp
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33dd3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33dd3-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="33dd3-107">'ndaki Tanımlayıcı ad imzasının üretilecektir derlemenin bildirimini içeren dosyanın yolu.</span><span class="sxs-lookup"><span data-stu-id="33dd3-107">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="33dd3-108">'ndaki Ortak/özel anahtar çiftini içeren anahtar kapsayıcısının adı.</span><span class="sxs-lookup"><span data-stu-id="33dd3-108">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="33dd3-109">`pbKeyBlob`Null ise, `wszKeyContainer` şifreleme hizmet sağlayıcısı (CSP) içinde geçerli bir kapsayıcı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="33dd3-109">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="33dd3-110">Bu durumda, kapsayıcıda depolanan anahtar çifti dosyayı imzalamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33dd3-110">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="33dd3-111">`pbKeyBlob`Null değilse, anahtar çiftinin anahtar ikili büyük nesne (blob) içinde yer aldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="33dd3-111">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="33dd3-112">'ndaki Ortak/özel anahtar çifti işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="33dd3-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="33dd3-113">Bu çift Win32 işlevi tarafından oluşturulan biçimdedir `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="33dd3-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="33dd3-114">`pbKeyBlob`Null ise, tarafından belirtilen anahtar kapsayıcının `wszKeyContainer` anahtar çiftini içermesi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="33dd3-114">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="33dd3-115">'ndaki Bayt cinsinden boyutu `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="33dd3-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="33dd3-116">dışı Ortak dil çalışma zamanının imzayı döndürdüğü konuma yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="33dd3-116">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="33dd3-117">`ppbSignatureBlob`Null ise, çalışma zamanı imzayı tarafından belirtilen dosyada depolar `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="33dd3-117">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="33dd3-118">`ppbSignatureBlob`Null değilse, ortak dil çalışma zamanı, imzanın geri döndürüleceği alanı ayırır.</span><span class="sxs-lookup"><span data-stu-id="33dd3-118">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="33dd3-119">Çağıranın [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanarak bu alanı boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33dd3-119">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="33dd3-120">dışı Döndürülen imzanın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="33dd3-120">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="33dd3-121">'ndaki Aşağıdaki değerlerden biri veya daha fazlası:</span><span class="sxs-lookup"><span data-stu-id="33dd3-121">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="33dd3-122">`SN_SIGN_ALL_FILES` (0x00000001)-bağlantılı modüller için tüm karmaların yeniden hesaplanması.</span><span class="sxs-lookup"><span data-stu-id="33dd3-122">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="33dd3-123">`SN_TEST_SIGN` (0x00000002)-derlemeyi test-imzala.</span><span class="sxs-lookup"><span data-stu-id="33dd3-123">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33dd3-124">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="33dd3-124">Return Value</span></span>  

 <span data-ttu-id="33dd3-125">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="33dd3-125">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33dd3-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33dd3-126">Remarks</span></span>  

 <span data-ttu-id="33dd3-127">İmza `wszFilePath` boyutunu imzayı oluşturmadan hesaplamak için null değerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="33dd3-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="33dd3-128">İmza doğrudan dosyada depolanabilir veya çağırana geri döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="33dd3-128">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="33dd3-129">`SN_SIGN_ALL_FILES`Belirtilirse, ancak bir ortak anahtar dahil edilmez (hem hem de `pbKeyBlob` null ise `wszFilePath` ), bağlantılı modüllerin karmaları yeniden hesaplanır, ancak derleme yeniden imzalanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="33dd3-129">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="33dd3-130">`SN_TEST_SIGN`Belirtilmişse, derlemenin tanımlayıcı bir adla imzalandığını göstermek için ortak dil çalışma zamanı üst bilgisi değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="33dd3-130">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33dd3-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33dd3-131">Requirements</span></span>  

 <span data-ttu-id="33dd3-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33dd3-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33dd3-133">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="33dd3-133">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="33dd3-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="33dd3-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33dd3-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33dd3-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33dd3-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33dd3-136">See also</span></span>

- [<span data-ttu-id="33dd3-137">StrongNameSignatureGeneration Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33dd3-137">StrongNameSignatureGeneration Method</span></span>](iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="33dd3-138">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33dd3-138">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
