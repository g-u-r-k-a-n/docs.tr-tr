---
title: ICorDebugStepper::SetUnmappedStopMask Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
ms.openlocfilehash: 50fad8b38a6b33d0ddbb2f0f20676296c3d66737
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698773"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask Yöntemi

Yürütmenin durdurmayacak eşlenmemiş kodun türünü belirten bir değer ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `mask`  
 'ndaki Hata ayıklayıcının yürütmeyi durdurulacağı eşlenmemiş kodun türünü belirten CorDebugUnmappedStop numaralandırması değeri.  
  
 Varsayılan değer STOP_OTHER_UNMAPPED. STOP_UNMANAGED değeri yalnızca birlikte çalışma hata ayıklaması ile geçerlidir.  
  
## <a name="remarks"></a>Açıklamalar  

 Hata ayıklayıcı, Microsoft ara dili (MSIL) için karşılık gelen hiçbir eşleme olmayan bir tam zamanında (JıT) derleme bulduğunda, bu tür eşlenmemiş kod belirten bayrak ayarlandıysa yürütmeyi halliyorlar. Aksi halde, bu adım saydam olarak devam eder.  
  
 Hata ayıklayıcı bir yöntemi girmek için bir Stepper kullanmıyorsa, eşlenmemiş kod üzerinde adım adım değildir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
