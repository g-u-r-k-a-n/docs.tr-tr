---
description: 'Daha fazla bilgi edinin: ICorDebugProcess2:: GetReferenceValueFromGCHandle yöntemi'
title: ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
ms.openlocfilehash: 02047dee9116d34a365242f2a532766eb60e1c81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650250"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle Metodu

Bir atık toplama tanıtıcısına sahip olan, belirtilen yönetilen nesneye bir başvuru işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `handle`  
 'ndaki Bir atık toplama tanıtıcısına sahip yönetilen bir nesne için bir işaretçi. Bu değer bir <xref:System.IntPtr> nesnedir ve <xref:System.Runtime.InteropServices.GCHandle> yönetilen nesne için öğesinden alınabilir.  
  
 `pOutValue`  
 dışı Belirtilen yönetilen nesneye bir başvuruyu temsil eden ICorDebugReferenceValue nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Döndürülen başvuru değerini bir çöp toplama başvuru değeri ile karıştırmayın.  
  
 Döndürülen başvuru normal bir başvuru gibi davranır. Bir kesme noktasından sonra kod yürütme devam ettiğinde devre dışıdır. Hedef nesnenin ömrü, başvuru değerinin yaşam süresinden etkilenmez.  
  
> [!NOTE]
> `GetReferenceValueFromGCHandle`Yöntemi tanıtıcıyı doğrulamaz. Bu nedenle, `GetReferenceValueFromGCHandle` Yöntem hata ayıklayıcıyı ve geçersiz bir tanıtıcı geçiriliyorsa kodun ayıklanmasına neden olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
