---
description: ': ICorProfilerCallback:: ObjectReferences yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::ObjectReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
ms.openlocfilehash: 55ea6fae87ecb6534af322fc9d5055c8a247f37a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745118"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences Yöntemi

Belirtilen nesne tarafından başvurulan bellekteki nesneler hakkında profil oluşturucuyu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>Parametreler  

 `objectId`  
 'ndaki Nesnelere başvuran nesnenin KIMLIĞI.  
  
 `classId`  
 'ndaki Belirtilen nesnenin bir örneği olduğu sınıfın KIMLIĞI.  
  
 `cObjectRefs`  
 'ndaki Belirtilen nesnenin başvurduğu nesne sayısı (yani, dizideki öğelerin sayısı `objectRefIds` ).  
  
 `objectRefIds`  
 'ndaki Tarafından başvurulan nesnelerin bir dizi kimliği `objectId` .  
  
## <a name="remarks"></a>Açıklamalar  

 `ObjectReferences`Bir çöp toplama işlemi tamamlandıktan sonra yığında kalan her nesne için yöntemi çağırılır. Profil Oluşturucu bu geri aramadan bir hata döndürürse, profil oluşturma hizmetleri sonraki atık toplamaya kadar bu geri aramayı çağırmayı sona erecek.  
  
 `ObjectReferences`Geri çağırma [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) geri çağırması ile birlikte kullanılabilir ve çalışma zamanı için tamamen bir nesne başvurusu grafiği oluşturur. Ortak dil çalışma zamanı (CLR), her bir nesne başvurusunun yöntemi tarafından yalnızca bir kez bildirilmesini sağlar `ObjectReferences` .  
  
 `ObjectReferences`Çöp toplama nesnelerin ortasında olabileceğinden, tarafından döndürülen nesne kimlikleri geri çağırma sırasında geçerli değildir. Bu nedenle, profil oluşturucular bir çağrı sırasında nesneleri incelemeyi denememelidir `ObjectReferences` . [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) çağrıldığında, çöp toplama tamamlanmıştır ve denetleme güvenle yapılabilir.  
  
 Null değeri, `ClassId` `objectId` kaldırılması gereken bir türe sahip olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
