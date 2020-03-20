---
title: BlessIWbemServices fonksiyonu (Yönetilmeyen API Başvurusu)
description: BlessIWbemServices işlevi, kullanıcı kimlik bilgilerinin bir IWbemServices sınıfına erişime izin verip vermediğini gösterir.
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
ms.openlocfilehash: 4b15af840cc00b3ec261604db4f3625c6b975d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176870"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="b58ec-103">BlessIWbemServices işlevi</span><span class="sxs-lookup"><span data-stu-id="b58ec-103">BlessIWbemServices function</span></span>
<span data-ttu-id="b58ec-104">Kullanıcı kimlik bilgilerinin belirtilen [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) sınıfına erişime izin verip vermediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b58ec-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b58ec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b58ec-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="b58ec-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b58ec-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="b58ec-107">[içinde] İzinlerin gerekli olduğu [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) nesnesine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b58ec-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="b58ec-108">[içinde] Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="b58ec-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="b58ec-109">[içinde] `strUser`' ile ilişkili parola</span><span class="sxs-lookup"><span data-stu-id="b58ec-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="b58ec-110">[içinde] Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="b58ec-110">[in] The domain name of the user.</span></span> <span data-ttu-id="b58ec-111">Daha fazla bilgi için [ConnectServerWmi](connectserverwmi.md) işlevine bakın.</span><span class="sxs-lookup"><span data-stu-id="b58ec-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="b58ec-112">[içinde] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="b58ec-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="b58ec-113">[içinde] Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="b58ec-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="b58ec-114">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="b58ec-114">Return value</span></span>

<span data-ttu-id="b58ec-115">Bu işlev tarafından döndürülen aşağıdaki değerler *WinError.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b58ec-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b58ec-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="b58ec-116">Constant</span></span>  |<span data-ttu-id="b58ec-117">Değer</span><span class="sxs-lookup"><span data-stu-id="b58ec-117">Value</span></span>  |<span data-ttu-id="b58ec-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b58ec-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="b58ec-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="b58ec-119">0x80070057</span></span> | <span data-ttu-id="b58ec-120">Bir veya daha fazla bağımsız değişken geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="b58ec-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="b58ec-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="b58ec-121">0x80004003</span></span> | <span data-ttu-id="b58ec-122">`pIWbemServices``null`.</span><span class="sxs-lookup"><span data-stu-id="b58ec-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="b58ec-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="b58ec-123">0x80000008</span></span> | <span data-ttu-id="b58ec-124">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b58ec-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="b58ec-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="b58ec-125">0x80000002</span></span> | <span data-ttu-id="b58ec-126">İşlemi gerçekleştirmek için yetersiz bellek kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b58ec-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="b58ec-127">0</span><span class="sxs-lookup"><span data-stu-id="b58ec-127">0</span></span> | <span data-ttu-id="b58ec-128">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="b58ec-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="b58ec-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b58ec-129">Requirements</span></span>  

 <span data-ttu-id="b58ec-130">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b58ec-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b58ec-131">**Üstbilgi:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b58ec-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b58ec-132">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b58ec-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b58ec-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b58ec-133">See also</span></span>

- [<span data-ttu-id="b58ec-134">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b58ec-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
