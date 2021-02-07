---
description: 'Daha fazla bilgi edinin: ICorDebugAssembly3:: EnumerateContainedAssemblies yöntemi'
title: ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 8933500713661ef785eb3ce5abc574e512580b6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754088"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>ICorDebugAssembly3::EnumerateContainedAssemblies Yöntemi

Bu derlemede yer alan derlemeler için bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppAssemblies`  
 dışı Numaralandırıcı olan ICorDebugAssemblyEnum arabirimi nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 `S_OK` Bu `ICorDebugAssembly3` nesne bir kapsayıcıdır; Aksi takdirde, `S_FALSE` ve numaralandırması boştur.  
  
## <a name="remarks"></a>Açıklamalar  

 İçerilen derlemeleri listelemek için semboller gereklidir. Yoksa, yöntemi döndürür `S_FALSE` ve geçerli numaralandırıcı sağlanmaz.  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugAssembly3 Arabirimi](icordebugassembly3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
