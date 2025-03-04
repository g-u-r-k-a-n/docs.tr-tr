---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugDataTarget2:: EnumerateThreadIDs yöntemi'
title: ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 5bbda67e6c6de81e9de566a68f772f324d79b92f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710562"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a>ICorDebugDataTarget2::EnumerateThreadIDs Yöntemi

Etkin iş parçacığı kimliklerinin bir listesini döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 Cthreadıds  
 'ndaki Kimlikleri döndürülebilecek en fazla iş parçacığı sayısı.  
  
 Pcthreadıds  
 dışı `ULONG32` Diziye yazılan iş parçacığı kimliklerinin gerçek sayısını gösteren bir işaretçisi `pThreadIds` .  
  
 Pthreadıds  
 Bir dizi iş parçacığı tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md). **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugDataTarget2 Arabirimi](icordebugdatatarget2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
