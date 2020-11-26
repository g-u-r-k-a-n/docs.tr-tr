---
title: IXCLRDataProcess Arabirimi
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 376ec2b840bc17c79ed1f27c17a8ddd22c37a0f4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245360"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess Arabirimi

İşlem hakkındaki bilgileri sorgulamak için yöntemler sağlar.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>Yöntemler

| Yöntem                                                                                                                                               | Açıklama                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetRuntimeNameByAddress](ixclrdataprocess-getruntimenamebyaddress-method.md)                     | Verilen adres için bir ad alır.                                                               |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | Bir `AppDomain` işlem içinde kendi benzersiz kimliğine göre alır.                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | Bir işlemin modüllerini numaralandırmak için bir tanıtıcı sağlar.                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | Bu işlemin modüllerini numaralandırır.                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | Modül numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | Verilen bir adresten başlayarak Yöntem örneklerinin numaralandırılacağı bir tanıtıcı sağlar `AppDomain` . |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | Bir adres uzaklığında başlayarak bu işlemin Yöntem örneklerini numaralandırır.                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | Örnek numaralandırması sırasında kullanılan iç yineleyiciler tarafından kullanılan kaynakları serbest bırakır.             |

## <a name="remarks"></a>Açıklamalar

Bu arabirim çalışma zamanının içinde bulunur ve herhangi bir üst bilgi veya kitaplık dosyası aracılığıyla gösterilmez. Ancak, `IUnknown` `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` normal com mekanizmalarından elde edilebilir GUID ile TÜRETILEN bir com arabirimidir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).
**Üst bilgi:** Seçim  
**Kitaplık:** Seçim  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama](index.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
