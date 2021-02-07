---
description: ': CreateInstallReferenceEnum Işlevi hakkında daha fazla bilgi'
title: CreateInstallReferenceEnum İşlevi
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: cc7551707cb46bcf0c475a0095684dbc790836e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761159"
---
# <a name="createinstallreferenceenum-function"></a>CreateInstallReferenceEnum İşlevi

Belirtilen derlemeye ait başvuruların bir listesini temsil eden bir [IInstallReferenceEnum](iinstallreferenceenum-interface.md) örneği için bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parametreler  

 `ppRefEnum`  
 dışı Döndürülen `IInstallReferenceEnum` işaretçi.  
  
 `pName`  
 'ndaki Başvuruların numaralandırılacağı derlemeyi tanımlayan [IAssemblyName](iassemblyname-interface.md) .  
  
 `dwFlags`  
 'ndaki Numaralandırıcının davranışını etkileyen bayraklar.  
  
 `pvReserved`  
 'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır. `pvReserved` null bir başvuru olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **Kitaplık:** Fusion.dll ve Mscorwks.dll. Doğru .NET Framework sürümünü hedefliyorsanız emin olmak için Mscorwks.dll yerine Fusion.dll kullanın.  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IInstallReferenceEnum Arabirimi](iinstallreferenceenum-interface.md)
- [IAssemblyName Arabirimi](iassemblyname-interface.md)
- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
