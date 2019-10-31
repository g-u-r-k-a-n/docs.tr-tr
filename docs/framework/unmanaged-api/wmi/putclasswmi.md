---
title: PutClassWmi işlevi (yönetilmeyen API Başvurusu)
description: PutClassWmi işlevi yeni bir sınıf oluşturur veya var olan bir sınıfı güncelleştirir.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 95a5e1f6339bde9dfe5c5ad9f989fc06e10fa7f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101786"
---
# <a name="putclasswmi-function"></a><span data-ttu-id="bf41e-103">PutClassWmi işlevi</span><span class="sxs-lookup"><span data-stu-id="bf41e-103">PutClassWmi function</span></span>

<span data-ttu-id="bf41e-104">Yeni bir sınıf oluşturur veya var olan bir sınıfı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="bf41e-104">Creates a new class or updates an existing one.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="bf41e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf41e-105">Syntax</span></span>

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="bf41e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf41e-106">Parameters</span></span>

`pObject`\
<span data-ttu-id="bf41e-107">'ndaki Geçerli bir sınıf tanımına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bf41e-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="bf41e-108">Tüm gerekli özellik değerleriyle doğru başlatılmış olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf41e-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`\
<span data-ttu-id="bf41e-109">'ndaki Bu işlevin davranışını etkileyen bayrakların birleşimi.</span><span class="sxs-lookup"><span data-stu-id="bf41e-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="bf41e-110">Aşağıdaki değerler *Wbemcli. h* üstbilgi dosyasında tanımlanmıştır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bf41e-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bf41e-111">Sabit</span><span class="sxs-lookup"><span data-stu-id="bf41e-111">Constant</span></span>  |<span data-ttu-id="bf41e-112">Değer</span><span class="sxs-lookup"><span data-stu-id="bf41e-112">Value</span></span>  |<span data-ttu-id="bf41e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf41e-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="bf41e-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="bf41e-114">0x20000</span></span> | <span data-ttu-id="bf41e-115">Ayarlanırsa, WMI değişiklik yapılan Flavor ile hiçbir niteleyicileri depolamaz.</span><span class="sxs-lookup"><span data-stu-id="bf41e-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> <br> <span data-ttu-id="bf41e-116">Ayarlanmamışsa, bu nesnenin yerelleştirilmemiş olduğu varsayılır ve tüm niteleyiciler bu örnekle birlikte depolanır.</span><span class="sxs-lookup"><span data-stu-id="bf41e-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="bf41e-117">0</span><span class="sxs-lookup"><span data-stu-id="bf41e-117">0</span></span> | <span data-ttu-id="bf41e-118">Yoksa sınıfı oluşturun veya zaten varsa üzerine yazın.</span><span class="sxs-lookup"><span data-stu-id="bf41e-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="bf41e-119">1\.</span><span class="sxs-lookup"><span data-stu-id="bf41e-119">1</span></span> | <span data-ttu-id="bf41e-120">Sınıfını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="bf41e-120">Update the class.</span></span> <span data-ttu-id="bf41e-121">Çağrının başarılı olması için sınıfın mevcut olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf41e-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="bf41e-122">2</span><span class="sxs-lookup"><span data-stu-id="bf41e-122">2</span></span> | <span data-ttu-id="bf41e-123">Sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bf41e-123">Create the class.</span></span> <span data-ttu-id="bf41e-124">Sınıf zaten mevcutsa çağrı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="bf41e-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="bf41e-125">0x10</span><span class="sxs-lookup"><span data-stu-id="bf41e-125">0x10</span></span> | <span data-ttu-id="bf41e-126">Bayrak, yarı zaman uyumlu bir çağrıya neden olur.</span><span class="sxs-lookup"><span data-stu-id="bf41e-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="bf41e-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="bf41e-127">0x10000</span></span> | <span data-ttu-id="bf41e-128">Bu sınıfın değiştiğini göstermek için, push sağlayıcıları `PutClassWmi` çağırırken bu bayrağı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf41e-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="bf41e-129">0</span><span class="sxs-lookup"><span data-stu-id="bf41e-129">0</span></span> | <span data-ttu-id="bf41e-130">Türetilmiş sınıf yoksa ve bu sınıfın örneği yoksa bir sınıfın güncelleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf41e-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="bf41e-131">Ayrıca değişiklik, açıklama niteleyicisi gibi önemli niteleyicilere ise tüm durumlarda güncelleştirmelere izin verir.</span><span class="sxs-lookup"><span data-stu-id="bf41e-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="bf41e-132">Sınıfın örnekleri veya değişiklikleri önemli niteleyicilere sahipse güncelleştirme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="bf41e-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="bf41e-133">0x20</span><span class="sxs-lookup"><span data-stu-id="bf41e-133">0x20</span></span> | <span data-ttu-id="bf41e-134">Değişiklik alt sınıflarla çakışmaya neden olmadığı sürece alt sınıflar olsa bile sınıfların güncelleştirmelerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="bf41e-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="bf41e-135">Örneğin, bu bayrak, alt sınıfların hiçbirinde daha önce bahsedilen temel sınıfa yeni bir özelliğin eklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="bf41e-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="bf41e-136">Sınıfta örnek varsa, güncelleştirme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="bf41e-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="bf41e-137">0x40</span><span class="sxs-lookup"><span data-stu-id="bf41e-137">0x40</span></span> | <span data-ttu-id="bf41e-138">çakışan alt sınıflar varsa sınıfların güncelleştirmelerini zorlar.</span><span class="sxs-lookup"><span data-stu-id="bf41e-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="bf41e-139">Örneğin, bu bayrak bir alt sınıfta bir sınıf niteleyicisi tanımlanmışsa bir güncelleştirmeyi zorlar ve temel sınıf var olan aynı niteleyiciyi eklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="bf41e-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with the existing one.</span></span> <span data-ttu-id="bf41e-140">Zorlama modunda, alt sınıfta çakışan niteleyiciyi silerek TIS çakışması çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="bf41e-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`\
<span data-ttu-id="bf41e-141">'ndaki Genellikle, bu değer `null`.</span><span class="sxs-lookup"><span data-stu-id="bf41e-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="bf41e-142">Aksi takdirde, istenen sınıfları sağlayan sağlayıcı tarafından kullanılabilen bir [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) örneğine yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="bf41e-142">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="bf41e-143">dışı `null`, bu parametre kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="bf41e-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="bf41e-144">`lFlags` `WBEM_FLAG_RETURN_IMMEDIATELY`içeriyorsa, işlev hemen `WBEM_S_NO_ERROR`ile döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf41e-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="bf41e-145">`ppCallResult` parametresi, yeni bir [ıwbemcallresult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) nesnesine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="bf41e-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="bf41e-146">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="bf41e-146">Return value</span></span>

<span data-ttu-id="bf41e-147">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bf41e-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bf41e-148">Sabit</span><span class="sxs-lookup"><span data-stu-id="bf41e-148">Constant</span></span>  |<span data-ttu-id="bf41e-149">Değer</span><span class="sxs-lookup"><span data-stu-id="bf41e-149">Value</span></span>  |<span data-ttu-id="bf41e-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf41e-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="bf41e-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="bf41e-151">0x80041003</span></span> | <span data-ttu-id="bf41e-152">Kullanıcının sınıfları oluşturma veya değiştirme izni yok.</span><span class="sxs-lookup"><span data-stu-id="bf41e-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="bf41e-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="bf41e-153">0x80041001</span></span> | <span data-ttu-id="bf41e-154">Belirtilmeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bf41e-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="bf41e-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="bf41e-155">0x80041010</span></span> | <span data-ttu-id="bf41e-156">Belirtilen sınıf geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="bf41e-156">The specified class is not valid.</span></span> <span data-ttu-id="bf41e-157">Genellikle, `pObject` bir örnek nesnesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf41e-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bf41e-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bf41e-158">0x80041008</span></span> | <span data-ttu-id="bf41e-159">Parametre geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="bf41e-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="bf41e-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="bf41e-160">0x80041016</span></span> | <span data-ttu-id="bf41e-161">Belirtilen sınıf adı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="bf41e-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="bf41e-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="bf41e-162">0x80041025</span></span> | <span data-ttu-id="bf41e-163">Bir alt sınıfı geçersiz kılacak bir değişiklik yapmak için girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="bf41e-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="bf41e-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="bf41e-164">0x80041019</span></span> | <span data-ttu-id="bf41e-165">`WBEM_FLAG_CREATE_ONLY` bayrağı belirtildi, ancak sınıf zaten var.</span><span class="sxs-lookup"><span data-stu-id="bf41e-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="bf41e-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="bf41e-166">0x80041002</span></span> | <span data-ttu-id="bf41e-167">`WBEM_FLAG_UPDATE_ONLY` `lFlags`belirtildi ve sınıf bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="bf41e-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="bf41e-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="bf41e-168">0x80041020</span></span> | <span data-ttu-id="bf41e-169">Sınıflar için gereken özellikler hepsi ayarlanmamış.</span><span class="sxs-lookup"><span data-stu-id="bf41e-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bf41e-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bf41e-170">0x80041006</span></span> | <span data-ttu-id="bf41e-171">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="bf41e-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="bf41e-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="bf41e-172">0x80041033</span></span> | <span data-ttu-id="bf41e-173">WMI, büyük olasılıkla durmuş ve yeniden başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="bf41e-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="bf41e-174">[Connectserverwmi](connectserverwmi.md) ' i yeniden çağırın.</span><span class="sxs-lookup"><span data-stu-id="bf41e-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="bf41e-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="bf41e-175">0x80041015</span></span> | <span data-ttu-id="bf41e-176">Geçerli işlem ve WMI arasındaki uzak yordam çağrısı (RPC) bağlantısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="bf41e-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="bf41e-177">0</span><span class="sxs-lookup"><span data-stu-id="bf41e-177">0</span></span> | <span data-ttu-id="bf41e-178">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="bf41e-178">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="bf41e-179">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf41e-179">Remarks</span></span>

<span data-ttu-id="bf41e-180">Bu işlev, [IWbemServices::P utClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) yöntemine yapılan çağrıyı sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="bf41e-180">This function wraps a call to the [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) method.</span></span>

<span data-ttu-id="bf41e-181">Kullanıcı, bir alt çizgi karakteriyle başlayan veya biten adlara sahip sınıflar oluşturmayabilir.</span><span class="sxs-lookup"><span data-stu-id="bf41e-181">The user may not create classes with names that begin or end with an underscore character.</span></span>

<span data-ttu-id="bf41e-182">İşlev çağrısı başarısız olursa, [GetErrorInfo](geterrorinfo.md) işlevini çağırarak ek hata bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf41e-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="bf41e-183">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf41e-183">Requirements</span></span>

<span data-ttu-id="bf41e-184">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf41e-184">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="bf41e-185">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="bf41e-185">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="bf41e-186">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bf41e-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bf41e-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf41e-187">See also</span></span>

- [<span data-ttu-id="bf41e-188">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bf41e-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
