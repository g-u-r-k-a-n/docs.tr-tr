---
title: ICLRStrongName::StrongNameTokenFromPublicKey Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: c727d4524bc40ab90eee90faf16788140a73ad9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677667"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="993ba-102">ICLRStrongName::StrongNameTokenFromPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="993ba-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>

<span data-ttu-id="993ba-103">Ortak anahtarı temsil eden bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="993ba-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="993ba-104">Tanımlayıcı ad belirteci, ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="993ba-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="993ba-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="993ba-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="993ba-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="993ba-106">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="993ba-107">'ndaki Tanımlayıcı ad imzasını oluşturmak için kullanılan anahtar çiftinin ortak bölümünü içeren [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) türünde bir yapı.</span><span class="sxs-lookup"><span data-stu-id="993ba-107">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="993ba-108">'ndaki Bayt cinsinden boyutu `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="993ba-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="993ba-109">dışı Geçilen anahtara karşılık gelen tanımlayıcı ad belirteci `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="993ba-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="993ba-110">Ortak dil çalışma zamanı, belirtecin döndürüleceği belleği ayırır.</span><span class="sxs-lookup"><span data-stu-id="993ba-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="993ba-111">Çağıran, [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) metodunu kullanarak bu belleği boşaltmalıdır.</span><span class="sxs-lookup"><span data-stu-id="993ba-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="993ba-112">dışı Döndürülen tanımlayıcı ad belirtecinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="993ba-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="993ba-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="993ba-113">Return Value</span></span>  

 <span data-ttu-id="993ba-114">`S_OK` Yöntem başarıyla tamamlanırsa; Aksi takdirde, hata belirten bir HRESULT değeri (bkz. bir liste için [genel HRESULT değerleri](/windows/win32/seccrypto/common-hresult-values) ).</span><span class="sxs-lookup"><span data-stu-id="993ba-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="993ba-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="993ba-115">Remarks</span></span>  

 <span data-ttu-id="993ba-116">Tanımlayıcı ad belirteci, meta verilerde anahtar bilgileri depolarken alan kazanmak için kullanılan bir ortak anahtarın kısaltılmış biçimidir.</span><span class="sxs-lookup"><span data-stu-id="993ba-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="993ba-117">Özellikle, tanımlayıcı ad belirteçleri, bağımlı derlemeye başvurmak için derleme başvurularında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="993ba-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="993ba-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="993ba-118">Requirements</span></span>  

 <span data-ttu-id="993ba-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="993ba-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="993ba-120">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="993ba-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="993ba-121">**Kitaplık:** mscoree.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="993ba-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="993ba-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="993ba-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="993ba-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="993ba-123">See also</span></span>

- [<span data-ttu-id="993ba-124">StrongNameGetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="993ba-124">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="993ba-125">PublicKeyBlob Yapısı</span><span class="sxs-lookup"><span data-stu-id="993ba-125">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="993ba-126">ICLRStrongName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="993ba-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
