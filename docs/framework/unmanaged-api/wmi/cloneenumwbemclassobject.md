---
title: CloneEnumWbemClassObject işlevi (yönetilmeyen API Başvurusu)
description: CloneEnumWbemClassObject işlevi bir Numaralandırıcı 'nın mantıksal bir kopyasını oluşturur.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fa8a7f436c018e3e083be452d300eb21e17f93f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708133"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="46c40-103">CloneEnumWbemClassObject işlevi</span><span class="sxs-lookup"><span data-stu-id="46c40-103">CloneEnumWbemClassObject function</span></span>

<span data-ttu-id="46c40-104">Bir Numaralandırıcının mantıksal bir kopyasını oluşturur ve geçerli konumunu bir numaralandırıcıda korur.</span><span class="sxs-lookup"><span data-stu-id="46c40-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="46c40-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="46c40-105">Syntax</span></span>

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum,
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject,
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority
);
```

## <a name="parameters"></a><span data-ttu-id="46c40-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46c40-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="46c40-107">dışı Yeni bir [ıenumwbemclassobject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="46c40-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="46c40-108">'ndaki Yetkilendirme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="46c40-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="46c40-109">'ndaki Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="46c40-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="46c40-110">dışı Kopyalanacak [ıenumwbemclassobject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="46c40-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="46c40-111">'ndaki Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="46c40-111">[in] The user name.</span></span> <span data-ttu-id="46c40-112">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="46c40-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="46c40-113">'ndaki Parola.</span><span class="sxs-lookup"><span data-stu-id="46c40-113">[in] The password.</span></span> <span data-ttu-id="46c40-114">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="46c40-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="46c40-115">'ndaki Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="46c40-115">[in] The domain name of the user.</span></span> <span data-ttu-id="46c40-116">Daha fazla bilgi için bkz. [Connectserverwmi](connectserverwmi.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="46c40-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="46c40-117">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="46c40-117">Return value</span></span>

<span data-ttu-id="46c40-118">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="46c40-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="46c40-119">Sabit</span><span class="sxs-lookup"><span data-stu-id="46c40-119">Constant</span></span>  |<span data-ttu-id="46c40-120">Değer</span><span class="sxs-lookup"><span data-stu-id="46c40-120">Value</span></span>  |<span data-ttu-id="46c40-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46c40-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="46c40-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="46c40-122">0x80041001</span></span> | <span data-ttu-id="46c40-123">Genel bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="46c40-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="46c40-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="46c40-124">0x80041008</span></span> | <span data-ttu-id="46c40-125">Bir parametre geçersiz.</span><span class="sxs-lookup"><span data-stu-id="46c40-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="46c40-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="46c40-126">0x80041006</span></span> | <span data-ttu-id="46c40-127">Yeterli bellek yok. işlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="46c40-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="46c40-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="46c40-128">0x80041015</span></span> | <span data-ttu-id="46c40-129">Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="46c40-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="46c40-130">0</span><span class="sxs-lookup"><span data-stu-id="46c40-130">0</span></span> | <span data-ttu-id="46c40-131">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="46c40-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="46c40-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46c40-132">Remarks</span></span>

<span data-ttu-id="46c40-133">Bu işlev, [ıenumwbemclassobject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="46c40-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="46c40-134">Bu yöntem yalnızca bir "en iyi çaba" kopyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46c40-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="46c40-135">Birçok CıM nesnesinin dinamik doğası nedeniyle, yeni Numaralandırıcı kaynak numaralandırıcı olarak aynı nesne kümesini Numaralandırmıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="46c40-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="46c40-136">İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46c40-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="46c40-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="46c40-137">Example</span></span>

<span data-ttu-id="46c40-138">Bir örnek için, bkz. [ıenumwbemclassobject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="46c40-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="46c40-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46c40-139">Requirements</span></span>

 <span data-ttu-id="46c40-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46c40-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="46c40-141">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="46c40-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="46c40-142">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="46c40-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="46c40-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46c40-143">See also</span></span>

- [<span data-ttu-id="46c40-144">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="46c40-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
