---
description: 'Daha fazla bilgi edinin: CLR_DEBUGGING_VERSION yapısı'
title: CLR_DEBUGGING_VERSION Yapısı
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
ms.openlocfilehash: 2d274a91948b98dc309cd5670c3dd3bf6cd01e2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772789"
---
# <a name="clr_debugging_version-structure"></a>CLR_DEBUGGING_VERSION Yapısı

Hata ayıklama amacıyla ortak dil çalışma zamanının (CLR) ürün sürümünü tanımlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`wStructVersion`|Yapı sürüm numarası|  
|`wMajor`|Ana sürüm numarası.|  
|`wMinor`|İkincil sürüm numarası.|  
|`wBuild`|Yapı numarası.|  
|`wRevision`|Düzeltme numarası.|  
  
## <a name="remarks"></a>Açıklamalar  

 `CLR_DEBUGGING_VERSION`Yapı COR_VERSION yapısıyla aynıdır, ancak `CLR_DEBUGGING_VERSION` Yapı ek bir yapı sürümü alanı ( `wStructVersion` ) sağlar. Şu anda bu alanın sıfır olarak ayarlanması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
