---
title: ICorDebugModule2::SetJMCStatus Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
ms.openlocfilehash: cfa6df7a812559f05a4c57381a5007c9c90238e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709667"
---
# <a name="icordebugmodule2setjmcstatus-method"></a>ICorDebugModule2::SetJMCStatus Yöntemi

Bu ICorDebugModule2 içindeki tüm sınıfların tüm yöntemlerinin Yalnızca kendi kodum (JMC) durumunu, dizide yer alan ve ters değere göre ayarlanır hariç, belirtilen değere ayarlar `pTokens` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `bIsJustMycode`  
 'ndaki `true` Kodun ayıklanamayacağını ise olarak ayarlayın; Aksi takdirde, olarak ayarlayın `false` .  
  
 `cTokens`  
 'ndaki `pTokens` Dizinin boyutu.  
  
 `pTokens`  
 'ndaki `mdToken` Her biri JMC durumunun! olarak ayarlandığı bir yönteme başvuran bir değer dizisi `bIsJustMycode` .  
  
## <a name="remarks"></a>Açıklamalar  

 Dizide belirtilen her yöntemin JMC durumu `pTokens` değerin tersi olarak ayarlanır `bIsJustMycode` . Bu modüldeki diğer tüm yöntemlerin durumu `bIsJustMycode` değere ayarlanır.  
  
 `SetJMCStatus`Yöntemi Bu modüldeki önceki tüm JMC ayarlarını siler.  
  
 `SetJMCStatus`Tüm işlevler başarıyla ayarlandıysa yöntem S_OK HRESULT döndürür. İşaretlenen bazı işlevler hata ayıklanabilir değilse bir HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE döndürür `true` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
