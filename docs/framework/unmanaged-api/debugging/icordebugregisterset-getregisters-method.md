---
description: ': ICorDebugRegisterSet:: Getyazmaçları yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugRegisterSet::GetRegisters Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: efb0f19fe9eb823912203b82267803739fc3e2cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690853"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters Metodu

Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `mask`  
 'ndaki Hangi yazmaç değerlerinin alınacağını belirten bir bit maskesi. Her bit bir kayda karşılık gelir. Bir bit olarak ayarlandıysa, kaydın değeri alınır; Aksi takdirde, kaydın değeri alınmadı.  
  
 `regCount`  
 'ndaki Alınacak kayıt değerlerinin sayısı.  
  
 `regBuffer`  
 dışı `CORDB_REGISTER` Her biri bir yazmaç değeri alan bir nesne dizisi.  
  
## <a name="remarks"></a>Açıklamalar  

 Dizinin boyutu, bit maskesinde bir tane olarak ayarlanan bit sayısına eşit olmalıdır. `regCount`Parametresi, kayıt değerlerini alacak arabellekteki öğelerin sayısını belirtir. Değer, `regCount` maskenin gösterdiği kayıt sayısı için çok küçük ise, üstteki numaralandırılmış Yazmaçları kümeden kesilecek. `regCount`Değer çok büyükse, kullanılmamış `regBuffer` öğeler değiştirilmemiş olur.  
  
 Bit maskesi kullanılamayan bir kaydı belirtirse, `GetRegisters` Bu kayıt için belirsiz bir değer döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet Arabirimi](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)
