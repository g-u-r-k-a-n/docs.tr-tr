---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_STATIC_TYPE numaralandırması'
title: COR_PRF_STATIC_TYPE Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
ms.openlocfilehash: b7171fe4e9c536d94109d46ae6cad9201a15bab9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789050"
---
# <a name="cor_prf_static_type-enumeration"></a>COR_PRF_STATIC_TYPE Numaralandırması

Bir alanın statik olup olmadığını ve bu durumda alan için geçerli olan statik kaliteyi gösterir. Bu değerler, alanın birden çok, farklı statik kalitede olduğunu göstermek için bit düzeyinde OR işlemi kullanılarak birleştirilebilir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|Alan statik değil.|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|Alan, uygulama etki alanı-statik ' dır.|  
|`COR_PRF_FIELD_THREAD_STATIC`|Alan, Thread-static ' dir.|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|Alan, bağlam statiktir.|  
|`COR_PRF_FIELD_RVA_STATIC`|Alan göreli sanal adres (RVA)-statik ' dır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Numaralandırmaları](profiling-enumerations.md)
