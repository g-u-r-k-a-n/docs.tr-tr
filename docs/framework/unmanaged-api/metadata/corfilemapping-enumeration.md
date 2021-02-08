---
description: 'Daha fazla bilgi edinin: CorFileMapping numaralandırması'
title: CorFileMapping Numaralandırması
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 0fc3916e75c576a6b133ba8a49c00eec6c9bac19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784476"
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping Numaralandırması

[IMetaDataInfo:: GetFileMapping](imetadatainfo-getfilemapping-method.md) metoduna yapılan çağrıdan döndürülen dosya eşlemesinin türünü tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`fmFlat`|Dosya bir veri dosyası olarak eşlendi. Yani, `SEC_IMAGE` bayrak Microsoft Win32 işlevine geçirilmedi `CreateFileMapping` .|  
|`fmExecutableImage`|Dosya, bayrağı ile işlevi ya da işlevi kullanılarak yürütme için eşlenir `LoadLibrary` `CreateFileMapping` `SEC_IMAGE` .|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
- [GetFileMapping Yöntemi](imetadatainfo-getfilemapping-method.md)
