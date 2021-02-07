---
description: ': ICorPublish:: EnumProcesses yöntemi hakkında daha fazla bilgi edinin'
title: ICorPublish::EnumProcesses Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 2451f179301eff4caca966568f966d145e269f51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722002"
---
# <a name="icorpublishenumprocesses-method"></a>ICorPublish::EnumProcesses Yöntemi

Bu bilgisayarda çalışan yönetilen işlemlere yönelik bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `Type`  
 Alınacak işlemin türünü belirten [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) numaralandırması değeri. Geçerli sürümde yalnızca COR_PUB_MANAGEDONLY geçerlidir.  
  
 `ppIEnum`  
 İşlemlerin numaralandırıcısı olan [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) örneğinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Numaralandırıcının işlem koleksiyonu, yöntemi çağrıldığında çalışan işlemlerin anlık görüntüsünü temel alır `EnumProcesses` . Numaralandırıcı çağrılmadan önce ya da başlamadan önce sonlanacak herhangi bir işlem içermez `EnumProcesses` .  
  
 `EnumProcesses`Yöntemi bu [ICorPublish](icorpublish-interface.md) örneğinde birden çok kez çağrılabilir ve bu işlem, yeni bir güncel koleksiyon oluşturur. Mevcut koleksiyonlar, yönteminin sonraki çağrılarından etkilenmeyecektir `EnumProcesses` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublish Arabirimi](icorpublish-interface.md)
