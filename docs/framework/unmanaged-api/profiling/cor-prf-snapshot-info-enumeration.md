---
title: COR_PRF_SNAPSHOT_INFO Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 5290db008bfe5727ed5899c2ed6f7e41ae9a353a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716362"
---
# <a name="cor_prf_snapshot_info-enumeration"></a>COR_PRF_SNAPSHOT_INFO Numaralandırması

Profil oluşturucunun [StackSnapshotCallback](stacksnapshotcallback-function.md) işlevine yapılan her çağrıda bir yığın anlık görüntüsüne ne kadar veri geçirileceğini belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üyeler|Açıklama|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|Parametresi dışında tüm parametrelerin değerlerinin geçirilmesi gerektiğini gösterir `StackSnapshotCallback` `context` .|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Parametresi dahil tüm parametrelerin değerlerinin geçirilmesi gerektiğini gösterir `StackSnapshotCallback` `context` .|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Daha basit, alternatif bir yığın yürüme algoritmasının kullanılacağını gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Numaralandırma tarafından verilen değerler, `COR_PRF_SNAPSHOT_INFO` [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metoduna parametre olarak geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DoStackSnapshot Yöntemi](icorprofilerinfo2-dostacksnapshot-method.md)
- [Profil Oluşturma Numaralandırmaları](profiling-enumerations.md)
