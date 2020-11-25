---
title: GetObjectText işlevi (yönetilmeyen API Başvurusu)
description: GetObjectText işlevi, MOF sözdiziminde bir nesnenin metinsel işlemesini döndürür.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6ad2b29202222d594cc7976a13929002164314a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718377"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="03914-103">GetObjectText işlevi</span><span class="sxs-lookup"><span data-stu-id="03914-103">GetObjectText function</span></span>

<span data-ttu-id="03914-104">Yönetilen Nesne Biçimi (MOF) sözdiziminde nesnenin metinsel işlemesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="03914-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="03914-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="03914-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
);
```  

## <a name="parameters"></a><span data-ttu-id="03914-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03914-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="03914-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="03914-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="03914-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="03914-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="03914-109">'ndaki Normalde 0.</span><span class="sxs-lookup"><span data-stu-id="03914-109">[in] Normally 0.</span></span> <span data-ttu-id="03914-110">`WBEM_FLAG_NO_FLAVORS`(Veya 0x1) belirtilirse, niteleyiciler yayma veya Flavor bilgisi olmadan dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="03914-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

<span data-ttu-id="03914-111">`pstrObjectText` dışı `null` Açık giriş işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="03914-111">`pstrObjectText` [out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="03914-112">Dönüşte, `BSTR` NESNENIN MOF sözdizimi işleme içeren yeni bir ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="03914-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="03914-113">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="03914-113">Return value</span></span>

<span data-ttu-id="03914-114">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="03914-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="03914-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="03914-115">Constant</span></span>  |<span data-ttu-id="03914-116">Değer</span><span class="sxs-lookup"><span data-stu-id="03914-116">Value</span></span>  |<span data-ttu-id="03914-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="03914-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="03914-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="03914-118">0x80041001</span></span> | <span data-ttu-id="03914-119">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="03914-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="03914-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="03914-120">0x80041008</span></span> | <span data-ttu-id="03914-121">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="03914-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="03914-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="03914-122">0x80041006</span></span> | <span data-ttu-id="03914-123">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="03914-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="03914-124">0</span><span class="sxs-lookup"><span data-stu-id="03914-124">0</span></span> | <span data-ttu-id="03914-125">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="03914-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="03914-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03914-126">Remarks</span></span>

<span data-ttu-id="03914-127">Bu işlev, [IWbemClassObject:: GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="03914-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="03914-128">Döndürülen MOF metni nesneyle ilgili tüm bilgileri içermiyor, ancak özgün nesneyi yeniden oluşturmak için yalnızca MOF derleyicisi için yeterli bilgi yok.</span><span class="sxs-lookup"><span data-stu-id="03914-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="03914-129">Örneğin, hiçbir yayılmış niteleyici veya üst sınıf özelliği dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="03914-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="03914-130">Aşağıdaki algoritma bir yöntemin parametrelerinin metnini yeniden oluşturmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="03914-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="03914-131">Parametreler, tanımlayıcı değerlerinin sırasıyla yeniden sıralandır.</span><span class="sxs-lookup"><span data-stu-id="03914-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="03914-132">Ve olarak belirtilen parametreler `[in]` `[out]` tek bir parametre içinde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="03914-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>

<span data-ttu-id="03914-133">`pstrObjectText` işlev çağrıldığında bir öğesine işaretçi olmalıdır `null` ; işaretçi serbest bırakılmadığı için yöntem çağrısından önce geçerli olan bir dizeye işaret etmelidir.</span><span class="sxs-lookup"><span data-stu-id="03914-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="03914-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03914-134">Requirements</span></span>  

<span data-ttu-id="03914-135">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03914-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03914-136">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="03914-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="03914-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="03914-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03914-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03914-138">See also</span></span>

- [<span data-ttu-id="03914-139">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="03914-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
