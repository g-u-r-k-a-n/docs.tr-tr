---
description: 'Daha fazla bilgi edinin: ICorDebugNativeFrame2:: GetStackParameterSize Yöntemi'
title: ICorDebugNativeFrame2::GetStackParameterSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
ms.openlocfilehash: 08a17ced0be75737c1c49aa3f9bb42b13bbe8aa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722340"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a>ICorDebugNativeFrame2::GetStackParameterSize Yöntemi

X86 işletim sistemlerindeki yığındaki parametrelerin birikmiş boyutunu döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a>Parametreler  

 `pSize`  
 dışı Yığındaki parametrelerin birikimli boyutuna yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Yığın boyutu başarıyla döndürüldü.|  
|S_FALSE|`GetStackParameterSize` , x86 olmayan bir platformda çağrıldı.|  
|E_FAIL|`The size of the parameters could not be returned`.|  
|E_INVALIDARG|`pSize``null`.|  
  
## <a name="exceptions"></a>Özel durumlar  
  
## <a name="remarks"></a>Açıklamalar  

 [Icordebugstackyürüme](icordebugstackwalk-interface.md) yöntemleri, yığına gönderilen parametrelerin yığın işaretçisini ayarlamadığında. Bunun yerine, tarafından döndürülen değeri, `GetStackParameterSize` bir yerel unwinder, parametreler için ayarlanacak şekilde, yığın işaretçisini ayarlamak için kullanabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugNativeFrame2 Arabirimi](icordebugnativeframe2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
