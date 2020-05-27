---
title: IValidator::FormatEventInfo Yöntemi
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
ms.openlocfilehash: 0c60631b5e034bc46d74412440d35d526359d043
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008579"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="ed996-102">IValidator::FormatEventInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed996-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="ed996-103">Belirtilen doğrulama hatasına karşılık gelen hata iletisini alır.</span><span class="sxs-lookup"><span data-stu-id="ed996-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed996-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ed996-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed996-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed996-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="ed996-106">'ndaki Doğrulama hata işleyicisine geçirilen HRESULT değeri.</span><span class="sxs-lookup"><span data-stu-id="ed996-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="ed996-107">'ndaki `VEContext`Doğrulama hatası hakkında bağlam bilgilerini içeren bir örnek.</span><span class="sxs-lookup"><span data-stu-id="ed996-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="ed996-108">[in, out] Döndürülen hata iletisini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ed996-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="ed996-109">'ndaki Hata iletisinin en fazla uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="ed996-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="ed996-110">'ndaki Hatayı açıklayan ek parametreler içeren bir güvenli dizi.</span><span class="sxs-lookup"><span data-stu-id="ed996-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed996-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed996-111">Requirements</span></span>  
 <span data-ttu-id="ed996-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed996-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed996-113">**Üst bilgi:** IValidator. IDL, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="ed996-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="ed996-114">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ed996-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed996-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed996-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
