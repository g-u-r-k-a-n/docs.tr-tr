---
description: ': ICorProfilerObjectEnum arabirimi hakkında daha fazla bilgi edinin'
title: ICorProfilerObjectEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum
helpviewer_keywords:
- ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type:
- apiref
ms.openlocfilehash: a41900c104818566704af0070a8cd3c6cf1bba8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781369"
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum Arabirimi

[Ngen.exe (yerel görüntü Oluşturucu)](../../tools/ngen-exe-native-image-generator.md)tarafından oluşturulan dondurulmuş nesnelerden oluşan bir koleksiyon aracılığıyla sırayla yinelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](icorprofilerobjectenum-clone-method.md)|Bu arabirimin kopyasına bir arabirim işaretçisi alır `ICorProfilerObjectEnum` .|  
|[GetCount Yöntemi](icorprofilerobjectenum-getcount-method.md)|Koleksiyondaki dondurulmuş nesnelerin toplam sayısını alır.|  
|[Next Yöntemi](icorprofilerobjectenum-next-method.md)|Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı nesne koleksiyonundan belirtilen sayıda bitişik nesneyi alır.|  
|[Reset Yöntemi](icorprofilerobjectenum-reset-method.md)|Bu Numaralandırıcı imlecini sıranın başlangıç konumuna taşımaktır.|  
|[Skip Yöntemi](icorprofilerobjectenum-skip-method.md)|Belirtilen sayıda öğe atlanabilmesi için, bu Numaralandırıcının imlecini geçerli konumundan ilerletir.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorProfilerObjectEnum`Arabirim bir Numaralandırıcı. Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar. Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilgili sorunlardan kaçınarak.  
  
 Arabirime bir işaretçi almak için [ICorProfilerInfo2:: EnumModuleFrozenObjects](icorprofilerinfo2-enummodulefrozenobjects-method.md) kullanın `ICorProfilerObjectEnum` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [EnumModuleFrozenObjects Yöntemi](icorprofilerinfo2-enummodulefrozenobjects-method.md)
