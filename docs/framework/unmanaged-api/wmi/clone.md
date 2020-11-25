---
title: Clone işlevi (yönetilmeyen API Başvurusu)
description: Clone işlevi, geçerli birinin tamamen kopyası olan yeni bir nesne döndürür.
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: aecbf750b42626629dcb5aef369978a2e2bd002a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708120"
---
# <a name="clone-function"></a><span data-ttu-id="b27ba-103">Clone işlevi</span><span class="sxs-lookup"><span data-stu-id="b27ba-103">Clone function</span></span>

<span data-ttu-id="b27ba-104">Geçerli nesnenin tamamen kopyası olan yeni bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="b27ba-104">Returns a new object that is a complete clone of the current object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b27ba-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b27ba-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [out] IWbemClassObject**  ppCopy
);
```  

## <a name="parameters"></a><span data-ttu-id="b27ba-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b27ba-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b27ba-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b27ba-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b27ba-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b27ba-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="b27ba-109">dışı Tamamen tek olan yeni bir nesne `ptr` .</span><span class="sxs-lookup"><span data-stu-id="b27ba-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="b27ba-110">Bu bağımsız değişken `null` geçerli nesnenin kopyasını alırsa olamaz.</span><span class="sxs-lookup"><span data-stu-id="b27ba-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="b27ba-111">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="b27ba-111">Return value</span></span>

<span data-ttu-id="b27ba-112">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b27ba-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b27ba-113">Sabit</span><span class="sxs-lookup"><span data-stu-id="b27ba-113">Constant</span></span>  |<span data-ttu-id="b27ba-114">Değer</span><span class="sxs-lookup"><span data-stu-id="b27ba-114">Value</span></span>  |<span data-ttu-id="b27ba-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b27ba-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="b27ba-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b27ba-116">0x80041001</span></span> | <span data-ttu-id="b27ba-117">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b27ba-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b27ba-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b27ba-118">0x80041008</span></span> | <span data-ttu-id="b27ba-119">`null` bir parametre olarak belirtildi ve bu kullanımda yasal değil.</span><span class="sxs-lookup"><span data-stu-id="b27ba-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b27ba-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b27ba-120">0x80041006</span></span> | <span data-ttu-id="b27ba-121">Nesneyi kopyalamak için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="b27ba-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b27ba-122">0</span><span class="sxs-lookup"><span data-stu-id="b27ba-122">0</span></span> | <span data-ttu-id="b27ba-123">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="b27ba-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b27ba-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b27ba-124">Remarks</span></span>

<span data-ttu-id="b27ba-125">Bu işlev, [IWbemClassObject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="b27ba-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="b27ba-126">Kopyalanmış nesne, başvuru sayısı 1 olan bir COM nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="b27ba-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="b27ba-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b27ba-127">Requirements</span></span>  

 <span data-ttu-id="b27ba-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b27ba-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b27ba-129">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="b27ba-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b27ba-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b27ba-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b27ba-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b27ba-131">See also</span></span>

- [<span data-ttu-id="b27ba-132">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b27ba-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
