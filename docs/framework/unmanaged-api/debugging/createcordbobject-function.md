---
description: 'Daha fazla bilgi edinin: CreateCordbObject Işlevi'
title: CreateCordbObject İşlevi
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: b6a585fc89f780b22f842127e1923414dbb8230f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801481"
---
# <a name="createcordbobject-function"></a>CreateCordbObject İşlevi

Uzak bir işlemde yönetilen bir hata ayıklama oturumunun örneğini oluşturma işlevselliği sağlayan bir hata ayıklayıcı arabirimi ([ICorDebug](icordebug-interface.md)) oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `iDebuggerVersion`  
 'ndaki Hedef işlemin hata ayıklayıcı sürümü. Bu parametre, uzaktan hata ayıklama için CorDebugVersion_2_0 olmalıdır.  
  
 `ppCordb`  
 dışı [ICorDebug](icordebug-interface.md) arabirimine verilecek ve döndürülen bir nesne işaretçisinin işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 S_OK  
 İşlemdeki CLRs sayısı başarıyla belirlendi ve karşılık gelen tanıtıcı ve yol dizileri doğru şekilde dolduruldu.  
  
 E_INVALIDARG  
 `ppCordb` null veya `iDebuggerVersion` CorDebugVersion_2_0 değil.  
  
 E_OUTOFMEMORY  
 İçin yeterli bellek ayrılamıyor `ppCordb`  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Diğer sorunlar.  
  
## <a name="remarks"></a>Açıklamalar  

 ' De döndürülen [ICorDebug](icordebug-interface.md) arabirimi, `ppCordb` tüm yönetilen hata ayıklama Hizmetleri için en üst düzey hata ayıklama arabirimidir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h  
  
 **Kitaplık:** mscordbi_macx86.dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
