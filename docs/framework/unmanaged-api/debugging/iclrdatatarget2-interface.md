---
description: 'Daha fazla bilgi edinin: ICLRDataTarget2 Interface'
title: ICLRDataTarget2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: 9ba6d11ea043d3b6ba85544b47e063f585854af8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794851"
---
# <a name="iclrdatatarget2-interface"></a>ICLRDataTarget2 Arabirimi

Hedef işlemdeki sanal bellek bölgelerini işlemek için veri erişim Hizmetleri katmanı tarafından kullanılan [ICLRDataTarget](iclrdatatarget-interface.md) 'nin bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AllocVirtual Yöntemi](iclrdatatarget2-allocvirtual-method.md)|Hedef işlemin adres alanında belleği ayırır.|  
|[FreeVirtual Yöntemi](iclrdatatarget2-freevirtual-method.md)|Hedef işlemin adres alanında daha önce ayrılan belleği boşaltır.|  
  
## <a name="remarks"></a>Açıklamalar  

 API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir. Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur. Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** ClrData. IDL, ClrData. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRDataTarget Arabirimi](iclrdatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
