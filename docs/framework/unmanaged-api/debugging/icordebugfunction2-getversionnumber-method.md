---
description: 'Daha fazla bilgi edinin: ICorDebugFunction2:: GetVersionNumber yöntemi'
title: ICorDebugFunction2::GetVersionNumber Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
ms.openlocfilehash: 7a703789099b82121c65214d6b1929e354405c8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692218"
---
# <a name="icordebugfunction2getversionnumber-method"></a>ICorDebugFunction2::GetVersionNumber Yöntemi

Bu işlevin Düzenle ve devam et sürümünü alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pnVersion`  
 dışı Bu ICorDebugFunction2 nesnesi tarafından temsil edilen işlevin sürüm numarası olan tamsayıya yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Çalışma zamanı, hata ayıklama oturumu sırasında her bir modüle gerçekleşen düzenleme sayısını izler. Bir işlevin sürüm numarası, işlevi sunan düzenleme sayısından bir daha fazla. İşlevin özgün sürümü sürüm 1 ' dir. Bu modülde her [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md) çağrıldığında sayı bir modül için artırılır. Bu nedenle, ilk ve üçüncü çağrısındaki bir işlevin gövdesi değiştirildiyse `ICorDebugModule2::ApplyChanges` , `GetVersionNumber` Bu işlev için sürüm 1, 2 veya 4 döndürebilir, sürüm 3 ' ü içermez. (Bu işlevin sürüm 3 ' ü yoktur.)  
  
 Sürüm numarası her modül için ayrı olarak izlenir. Bu nedenle, modül 1 üzerinde dört düzenleme gerçekleştirirseniz ve modül 2 ' de hiç bir işlem yaptıysanız, modül 1 ' deki bir sonraki düzenleme, modül 1 ' deki tüm düzenlenmiş işlevlere 6 sürüm numarası atar. Aynı düzenleme, modül 2 ' ye dokunursa modül 2 ' deki işlevler sürüm numarası 2 alır.  
  
 Yöntemi tarafından edinilen sürüm numarası `GetVersionNumber` [ICorDebugFunction:: GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md)tarafından elde edilenden daha düşük olabilir.  
  
 [ICorDebugCode:: GetVersionNumber](icordebugcode-getversionnumber-method.md) yöntemi ile aynı işlemi gerçekleştirir `ICorDebugFunction2::GetVersionNumber` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
