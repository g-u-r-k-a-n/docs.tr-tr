---
description: ': Idebugoto Attach:: oto Attach yöntemi hakkında daha fazla bilgi edinin'
title: IDebugAutoAttach::AutoAttach Yöntemi
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
ms.openlocfilehash: 8abd35b1d94fc074d4dafe424c52c274b1de1541
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800363"
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach Yöntemi

Sunucu tarafından çağrılan hata ayıklayıcı otomatik iliştirme işlemini gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `guidPort`  
 'ndaki Her zaman olarak ayarlayın `GUID_NULL` .  
  
 `dwPid`  
 'ndaki İşlem KIMLIĞI, normalde `GetCurrentProcessId` işlevle alındı.  
  
 `dwProgramType`  
 'ndaki Program türü: `AUTOATTACH_PROGRAM_WIN32` , `AUTOATTACH_PROGRAM_COMPLUS` , veya `AUTOATTACH_PROGRAM_UNKNOWN` .  
  
 `dwProgramId`  
 'ndaki Program KIMLIĞI.  
  
 `pszSessionId`  
 'ndaki Hata ayıklama fiili tarafından geçirilen dize.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Yöntem başarılı olursa S_OK.  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** Dbgoto Attach. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IDebugAutoAttach Arabirimi](idebugautoattach-interface.md)
