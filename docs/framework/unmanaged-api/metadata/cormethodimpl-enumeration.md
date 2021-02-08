---
description: 'Daha fazla bilgi edinin: CorMethodImpl numaralandırması'
title: CorMethodImpl Numaralandırması
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
ms.openlocfilehash: 157db81a72742f1f2aae7e95249b819b2396ef4b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784398"
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl Numaralandırması

Yöntem uygulama özelliklerini tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`miCodeTypeMask`|Kod türünü tanımlayan bayraklar.|  
|`miIL`|Yöntem uygulamasının Microsoft ara dil (MSIL) olduğunu belirtir.|  
|`miNative`|Yöntem uygulamasının yerel olduğunu belirtir.|  
|`miOPTIL`|Yöntem uygulamasının OPTIL olduğunu belirtir.|  
|`miRuntime`|Yöntem uygulamasının ortak dil çalışma zamanı tarafından sağlandığını belirtir.|  
|`miManagedMask`|Kodun yönetilip yönetilmediğini belirten bayraklar.|  
|`miUnmanaged`|Yöntem uygulamasının yönetilmediğini belirtir.|  
|`miManaged`|Yöntem uygulamasının yönetileceğini belirtir.|  
|`miForwardRef`|Yöntemin tanımlandığını belirtir. Bu bayrak birincil olarak birleştirme senaryolarında kullanılır.|  
|`miPreserveSig`|Bir HRESULT dönüştürmesi için yöntem imzasının karıştırılamıyor olduğunu belirtir.|  
|`miInternalCall`|Ortak dil çalışma zamanı tarafından iç kullanım için ayrılmıştır.|  
|`miSynchronized`|Yöntemin gövdesinde tek iş parçacıklı olduğunu belirtir.|  
|`miNoInlining`|Metodun satır içine alınamıyor olduğunu belirtir.|  
|`miAggressiveInlining`|Mümkünse yöntemin satır içine alınmış olması gerektiğini belirtir.|  
|`miNoOptimization`|Yöntemin iyileştirilmemelidir.|  
|`miMaxMethodImplVal`|İçin geçerli en büyük değer `CorMethodImpl` .|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
