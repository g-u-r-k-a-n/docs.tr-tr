---
description: 'Hakkında daha fazla bilgi edinin: CreateDebuggingInterfaceFromVersion Function for Silverlight'
title: Silverlight için CreateDebuggingInterfaceFromVersion İşlevi
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
ms.openlocfilehash: 8c61593f2e912260ecca65efce9f905ce56e88dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801455"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>Silverlight için CreateDebuggingInterfaceFromVersion İşlevi

[CreateVersionStringFromModule işlevinden](createversionstringfrommodule-function.md)döndürülen ortak dil çalışma zamanı (CLR) sürüm dizesini kabul eder ve karşılık gelen bir hata ayıklayıcı arabirimini (genellikle, [ICorDebug](icordebug-interface.md)) döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `szDebuggeeVersion`\
 'ndaki [CreateVersionStringFromModule işlevi](createversionstringfrommodule-function.md)tarafından döndürülen hedef hata ayıklanan clr 'nin sürüm dizesi.  
  
 `ppCordb`\
 dışı COM nesnesine () yönelik işaretçiye yönelik işaretçi `IUnknown` . Bu nesne, döndürülmeden önce bir [ICorDebug](icordebug-interface.md) nesnesine atacaktır.  
  
## <a name="return-value"></a>Dönüş Değeri

 `S_OK`\
 `ppCordb`[ICorDebug arabirimi](icordebug-interface.md) arabirimini uygulayan geçerli bir nesneye başvurur.  
  
 `E_INVALIDARG`\
 `szDebuggeeVersion`Ya da `ppCordb` null.  
  
 `CORDBG_E_DEBUG_COMPONENT_MISSING`\
 CLR hata ayıklaması için gerekli bir bileşen bulunamıyor. _mscordbi.dll_ ya da _mscordaccore.dll_ hedef CoreCLR.dll aynı dizinde bulunamadı.  
  
 `CORDBG_E_INCOMPATIBLE_PROTOCOL`\
 mscordbi.dll ya da mscordaccore.dll, hedef CoreCLR.dll aynı sürümde değil.  
  
 `E_FAIL` (veya diğer `E_` dönüş kodları) \
 [ICorDebug arabirimi](icordebug-interface.md)döndürülemiyor.  
  
## <a name="remarks"></a>Açıklamalar

 Döndürülen arabirim, hedef işlemdeki bir CLR 'ye ekleme ve CLR 'nin çalıştığı yönetilen kodda hata ayıklama için tesisler sağlar.  
  
## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** dbgshim. h  
  
 **Kitaplık:** dbgshim.dll  
  
 **.NET Framework sürümleri:** 3,5 SP1
