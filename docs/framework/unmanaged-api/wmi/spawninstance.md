---
title: SpawnInstance işlevi (yönetilmeyen API Başvurusu)
description: SpawnInstance işlevi bir sınıfın yeni bir örneğini oluşturur.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 176bc83dd02381af8c2bc3995a37e7fee7c1bebf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732235"
---
# <a name="spawninstance-function"></a><span data-ttu-id="5e96f-103">SpawnInstance işlevi</span><span class="sxs-lookup"><span data-stu-id="5e96f-103">SpawnInstance function</span></span>

<span data-ttu-id="5e96f-104">Bir sınıfın yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5e96f-104">Creates a new instance of a class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5e96f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5e96f-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a><span data-ttu-id="5e96f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e96f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5e96f-107">'ndaki Bu parametre kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="5e96f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5e96f-108">'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5e96f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="5e96f-109">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="5e96f-109">[in] Reserved.</span></span> <span data-ttu-id="5e96f-110">Bu parametre 0 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e96f-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="5e96f-111">dışı Sınıfın yeni örneğine işaretçiyi alır.</span><span class="sxs-lookup"><span data-stu-id="5e96f-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="5e96f-112">Bir hata oluşursa, yeni bir nesne döndürülmez ve `ppNewInstance` değiştirilmemiş olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="5e96f-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="5e96f-113">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="5e96f-113">Return value</span></span>

<span data-ttu-id="5e96f-114">Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5e96f-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5e96f-115">Sabit</span><span class="sxs-lookup"><span data-stu-id="5e96f-115">Constant</span></span>  |<span data-ttu-id="5e96f-116">Değer</span><span class="sxs-lookup"><span data-stu-id="5e96f-116">Value</span></span>  |<span data-ttu-id="5e96f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e96f-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="5e96f-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="5e96f-118">0x80041020</span></span> | <span data-ttu-id="5e96f-119">`ptr` geçerli bir sınıf tanımı değil ve yeni örnekler üretilemedi.</span><span class="sxs-lookup"><span data-stu-id="5e96f-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="5e96f-120">Tamamlanmamış ya da [Putclasswmı](putclasswmi.md)çağırarak Windows yönetimine kaydedilmemiş.</span><span class="sxs-lookup"><span data-stu-id="5e96f-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5e96f-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5e96f-121">0x80041006</span></span> | <span data-ttu-id="5e96f-122">İşlemi gerçekleştirmek için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="5e96f-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5e96f-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5e96f-123">0x80041008</span></span> | <span data-ttu-id="5e96f-124">`ppNewClass`, `null` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5e96f-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5e96f-125">0</span><span class="sxs-lookup"><span data-stu-id="5e96f-125">0</span></span> | <span data-ttu-id="5e96f-126">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="5e96f-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5e96f-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e96f-127">Remarks</span></span>

<span data-ttu-id="5e96f-128">Bu işlev, [IWbemClassObject:: SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) yöntemine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="5e96f-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="5e96f-129">`ptr` Windows yönetiminden alınmış bir sınıf tanımı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e96f-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="5e96f-130">(Bir örnekten örnek oluşturma desteklendiğini, ancak döndürülen örnek boş olduğunu unutmayın.) Daha sonra bu sınıf tanımını yeni örnekler oluşturmak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="5e96f-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="5e96f-131">Örneği Windows yönetimine yazmayı düşünüyorsanız [Putınstancewmi](putinstancewmi.md) işlevine yapılan bir çağrı gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e96f-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="5e96f-132">Otomatik olarak döndürülen yeni nesne, `ppNewClass` geçerli nesnenin bir alt sınıfı olur.</span><span class="sxs-lookup"><span data-stu-id="5e96f-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="5e96f-133">Bu davranışın üzerine yazılamıyor.</span><span class="sxs-lookup"><span data-stu-id="5e96f-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="5e96f-134">Alt sınıfların (türetilmiş sınıflar) oluşturulabilmesi için başka bir yöntem yoktur.</span><span class="sxs-lookup"><span data-stu-id="5e96f-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="5e96f-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e96f-135">Requirements</span></span>  

 <span data-ttu-id="5e96f-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e96f-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e96f-137">**Üst bilgi:** WMINet_Utils. IDL</span><span class="sxs-lookup"><span data-stu-id="5e96f-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5e96f-138">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5e96f-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e96f-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e96f-139">See also</span></span>

- [<span data-ttu-id="5e96f-140">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5e96f-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
