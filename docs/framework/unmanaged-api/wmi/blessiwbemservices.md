---
title: Blessıwbemservices işlevi (yönetilmeyen API Başvurusu)
description: Blessıwbemservices işlevi, Kullanıcı kimlik bilgilerinin bir IWbemServices sınıfına erişime izin verip vermediğini belirtir.
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 43ef617ee754c9dcd661b31abba6b17434563c22
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708159"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="196a4-103">BlessIWbemServices işlevi</span><span class="sxs-lookup"><span data-stu-id="196a4-103">BlessIWbemServices function</span></span>

<span data-ttu-id="196a4-104">Kullanıcı kimlik bilgilerinin belirtilen [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) sınıfına erişime izin verip vermediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="196a4-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="196a4-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="196a4-105">Syntax</span></span>  
  
```cpp
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="196a4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="196a4-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="196a4-107">'ndaki İzinleri gerekli olan [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="196a4-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="196a4-108">'ndaki Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="196a4-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="196a4-109">'ndaki İle ilişkili parola `strUser` .</span><span class="sxs-lookup"><span data-stu-id="196a4-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="196a4-110">'ndaki Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="196a4-110">[in] The domain name of the user.</span></span> <span data-ttu-id="196a4-111">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="196a4-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="196a4-112">'ndaki Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="196a4-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="196a4-113">'ndaki Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="196a4-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="196a4-114">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="196a4-114">Return value</span></span>

<span data-ttu-id="196a4-115">Bu işlev tarafından döndürülen aşağıdaki değerler *Winerror. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="196a4-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="196a4-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="196a4-116">Constant</span></span>  |<span data-ttu-id="196a4-117">Değer</span><span class="sxs-lookup"><span data-stu-id="196a4-117">Value</span></span>  |<span data-ttu-id="196a4-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="196a4-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="196a4-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="196a4-119">0x80070057</span></span> | <span data-ttu-id="196a4-120">Bir veya daha fazla bağımsız değişken geçersiz.</span><span class="sxs-lookup"><span data-stu-id="196a4-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="196a4-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="196a4-121">0x80004003</span></span> | <span data-ttu-id="196a4-122">`pIWbemServices`, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="196a4-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="196a4-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="196a4-123">0x80000008</span></span> | <span data-ttu-id="196a4-124">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="196a4-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="196a4-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="196a4-125">0x80000002</span></span> | <span data-ttu-id="196a4-126">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="196a4-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="196a4-127">0</span><span class="sxs-lookup"><span data-stu-id="196a4-127">0</span></span> | <span data-ttu-id="196a4-128">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="196a4-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="196a4-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="196a4-129">Requirements</span></span>  

 <span data-ttu-id="196a4-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="196a4-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="196a4-131">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="196a4-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="196a4-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="196a4-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="196a4-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="196a4-133">See also</span></span>

- [<span data-ttu-id="196a4-134">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="196a4-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
