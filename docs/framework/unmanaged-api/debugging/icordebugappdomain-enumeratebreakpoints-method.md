---
title: ICorDebugAppDomain::EnumerateBreakpoints Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
ms.openlocfilehash: 20c8a1987e48a88a3b8c92cf9f36fb58166cda9e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715994"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a>ICorDebugAppDomain::EnumerateBreakpoints Yöntemi

Uygulama etki alanındaki tüm etkin kesme noktaları için bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppBreakpoints`  
 dışı Uygulama etki alanındaki tüm etkin kesme noktaları için numaralandırıcı olan ICorDebugBreakpointEnum nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Numaralandırıcı, işlev kesme noktaları ve veri kesme noktaları da dahil olmak üzere tüm kesme noktaları türlerini içerir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
