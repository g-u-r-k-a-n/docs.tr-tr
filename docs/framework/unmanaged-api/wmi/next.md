---
title: Next işlevi (yönetilmeyen API Başvurusu)
description: Next işlevi bir Numaralandırmadaki sonraki özelliği alır.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 587e085f6fe9f6c19d3605c673cd3bd6f68162f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127372"
---
# <a name="next-function"></a><span data-ttu-id="7cbb8-103">Next işlevi</span><span class="sxs-lookup"><span data-stu-id="7cbb8-103">Next function</span></span>
<span data-ttu-id="7cbb8-104">Bir [beginenumeration](beginenumeration.md)çağrısıyla başlayan bir Numaralandırmadaki bir sonraki özelliği alır.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="7cbb8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cbb8-105">Syntax</span></span>

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="7cbb8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7cbb8-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="7cbb8-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="7cbb8-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`\
<span data-ttu-id="7cbb8-109">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-109">[in] Reserved.</span></span> <span data-ttu-id="7cbb8-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-110">This parameter must be 0.</span></span>

`pstrName`\
<span data-ttu-id="7cbb8-111">dışı Özellik adını içeren yeni bir `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="7cbb8-112">Ad gerekli değilse bu parametreyi `null` olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`\
<span data-ttu-id="7cbb8-113">dışı Özelliğin değeriyle doldurulmuş bir `VARIANT`.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="7cbb8-114">Değer gerekli değilse bu parametreyi `null` olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="7cbb8-115">İşlev bir hata kodu döndürürse, `pVal` geçirilen `VARIANT` değiştirilmemiş olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span>

`pvtType`\
<span data-ttu-id="7cbb8-116">dışı `CIMTYPE` değişkenine yönelik bir işaretçi (özelliğin türünün yerleştirildiği bir `LONG`).</span><span class="sxs-lookup"><span data-stu-id="7cbb8-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="7cbb8-117">Bu özelliğin değeri bir `VT_NULL_VARIANT`olabilir, bu durumda özelliğin gerçek türünü belirlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="7cbb8-118">Bu parametre de `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-118">This parameter can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="7cbb8-119">[out] `null`veya özelliğin kaynağına bilgi alan bir değer.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="7cbb8-120">Olası değerler için [açıklamalar] bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-120">See the [Remarks] section for possible values.</span></span>

## <a name="return-value"></a><span data-ttu-id="7cbb8-121">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="7cbb8-121">Return value</span></span>

<span data-ttu-id="7cbb8-122">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7cbb8-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7cbb8-123">Sabit</span><span class="sxs-lookup"><span data-stu-id="7cbb8-123">Constant</span></span>  |<span data-ttu-id="7cbb8-124">Değer</span><span class="sxs-lookup"><span data-stu-id="7cbb8-124">Value</span></span>  |<span data-ttu-id="7cbb8-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7cbb8-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="7cbb8-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="7cbb8-126">0x80041001</span></span> | <span data-ttu-id="7cbb8-127">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7cbb8-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7cbb8-128">0x80041008</span></span> | <span data-ttu-id="7cbb8-129">Bir parametre geçersiz.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="7cbb8-130">0x8004101D</span><span class="sxs-lookup"><span data-stu-id="7cbb8-130">0x8004101d</span></span> | <span data-ttu-id="7cbb8-131">[`BeginEnumeration`](beginenumeration.md) işlevine hiçbir çağrı yoktu.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="7cbb8-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="7cbb8-132">0x80041006</span></span> | <span data-ttu-id="7cbb8-133">Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="7cbb8-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="7cbb8-134">0x80041015</span></span> | <span data-ttu-id="7cbb8-135">Geçerli işlem ile Windows Yönetimi arasındaki uzak yordam çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-135">The remote procedure call between the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="7cbb8-136">0</span><span class="sxs-lookup"><span data-stu-id="7cbb8-136">0</span></span> | <span data-ttu-id="7cbb8-137">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="7cbb8-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="7cbb8-138">0x40005</span></span> | <span data-ttu-id="7cbb8-139">Numaralandırmada daha fazla özellik yok.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-139">There are no more properties in the enumeration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7cbb8-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7cbb8-140">Remarks</span></span>

<span data-ttu-id="7cbb8-141">Bu işlev [IWbemClassObject:: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-141">This function wraps a call to the [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) method.</span></span>

<span data-ttu-id="7cbb8-142">Bu yöntem ayrıca sistem özelliklerini de döndürür.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-142">This method also returns system properties.</span></span>

<span data-ttu-id="7cbb8-143">Özelliğin temeldeki türü bir nesne yolu, bir tarih veya saat ya da başka bir özel tür ise, döndürülen tür yeterli bilgi içermez.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="7cbb8-144">Çağıran, özelliğin bir nesne başvurusu, bir tarih veya saat ya da başka bir özel tür olup olmadığını belirlemesi için belirtilen özelliğin `CIMTYPE` incelemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="7cbb8-145">`plFlavor` `null`değilse, `LONG` değeri özelliğin kaynağı hakkında aşağıdaki gibi bilgileri alır:</span><span class="sxs-lookup"><span data-stu-id="7cbb8-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="7cbb8-146">Sabit</span><span class="sxs-lookup"><span data-stu-id="7cbb8-146">Constant</span></span>  |<span data-ttu-id="7cbb8-147">Değer</span><span class="sxs-lookup"><span data-stu-id="7cbb8-147">Value</span></span>  |<span data-ttu-id="7cbb8-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7cbb8-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="7cbb8-149">0x40</span><span class="sxs-lookup"><span data-stu-id="7cbb8-149">0x40</span></span> | <span data-ttu-id="7cbb8-150">Özelliği, standart bir sistem özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="7cbb8-151">0x20</span><span class="sxs-lookup"><span data-stu-id="7cbb8-151">0x20</span></span> | <span data-ttu-id="7cbb8-152">Bir sınıf için: özellik üst sınıftan devralınır.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-152">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="7cbb8-153">Bir örnek için: üst sınıftan Devralındığı sürece özelliği, örnek tarafından değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="7cbb8-154">0</span><span class="sxs-lookup"><span data-stu-id="7cbb8-154">0</span></span> | <span data-ttu-id="7cbb8-155">Bir sınıf için: özellik türetilmiş sınıfa aittir.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-155">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="7cbb8-156">Bir örnek için: özelliği örnek tarafından değiştirilir; diğer bir deyişle, bir değer sağlanmış veya bir niteleyici eklenmiş ya da değiştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="7cbb8-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7cbb8-157">Requirements</span></span>

<span data-ttu-id="7cbb8-158">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cbb8-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="7cbb8-159">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="7cbb8-159">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="7cbb8-160">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7cbb8-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7cbb8-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cbb8-161">See also</span></span>

- [<span data-ttu-id="7cbb8-162">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7cbb8-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
