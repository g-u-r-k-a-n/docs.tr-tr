---
description: ': ICorDebugSymbolProvider:: GetMethodLocalSymbols yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: GetMethodLocalSymbols yöntemi'
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
ms.openlocfilehash: f4eaac208d98b25ae4a53acfd977d354c6f6ac1b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659822"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a>ICorDebugSymbolProvider:: GetMethodLocalSymbols yöntemi

Yöntemin yerel sembollerini, bu yöntemin göreli sanal adresi (RVA) verildiğinde alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `nativeRVA`  
 'ndaki Metodun yerel göreli sanal adresi.  
  
 `cRequestedSymbols`  
 'ndaki İstenen yerel semboller sayısı.  
  
 `pcFetchedSymbols`  
 dışı Yöntemi tarafından alınan sembol sayısına yönelik bir işaretçi.  
  
 `pcFetchedSymbols`  
 dışı Metodun yerel sembollerini içeren [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) dizisine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu yöntem yalnızca .NET Native kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetMethodParameterSymbols Yöntemi](icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [ICorDebugSymbolProvider Arabirimi](icordebugsymbolprovider-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
