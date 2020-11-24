---
title: 'Icordebugvariablehomeenum:: Next yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
ms.openlocfilehash: 4ef4ed19033b0857b9970ee8103bbd92f383898c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679539"
---
# <a name="icordebugvariablehomeenumnext-method"></a>Icordebugvariablehomeenum:: Next yöntemi

Bir işlevdeki yerel değişkenler ve bağımsız değişkenler hakkında bilgi içeren, belirtilen [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği sayısını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `celt`  
 'ndaki Alınacak nesne sayısı.  
  
 `homes`  
 Her biri bir işlevin yerel değişkeni veya bağımsız değişkeni hakkında bilgi sağlayan [ıcordebugvariablehome](icordebugvariablehome-interface.md) nesnesine işaret eden bir işaretçiler dizisi.  
  
 `pceltFetched`  
 dışı Gerçekte nesnelerde döndürülen örneklerin sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntemi aşağıdaki değerleri döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|Yöntem başarıyla tamamlandı.|  
|`S_FALSE`|İçinde yansıtıldıkça alınan örneklerin gerçek sayısı `pceltFetched` , istenen örnek sayısından daha az.|  
  
## <a name="remarks"></a>Açıklamalar  

 [Icordebugvariablehomeenum:: Next](icordebugvariablehomeenum-next-method.md) yöntemi, `celt` Numaralandırıcının geçerli konumundan başlayarak en fazla nesne alır. Yöntemi döndürüldüğünde, `pceltFetched` alınan nesnelerin gerçek sayısını içerir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHomeEnum Arabirimi](icordebugvariablehomeenum-interface.md)
- [ICorDebugVariableHome Arabirimi](icordebugvariablehome-interface.md)
