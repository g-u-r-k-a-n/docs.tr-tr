---
description: ': ICorProfilerInfo:: Setilınstrumentedcodemap yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerInfo::SetILInstrumentedCodeMap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: f9ed01b91f740a8bd95f4ad049076feb02363b8f
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760398"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap Yöntemi

Belirtilen Microsoft ara dili (MSIL) eşleme girdilerini kullanarak belirtilen işlev için bir kod Haritası ayarlar.

> [!NOTE]
> .NET Framework sürüm 2,0 ' de, `SetILInstrumentedCodeMap` `FunctionID` belirli bir uygulama etki alanında genel bir işlevi temsil eden bir üzerinde çağırmak, uygulama etki alanındaki bu işlevin tüm örneklerini etkiler.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a>Parametreler

`functionId` 'ndaki Kod eşlemesi ayarlanacak işlevin KIMLIĞI.

`fStartJit` 'ndaki Yöntemine yapılan çağrının `SetILInstrumentedCodeMap` , belirli bir için ilk değeri olup olmadığını belirten bir Boolean değer `FunctionID` . `fStartJit`Verilen için `true` ilk çağrıda ve daha sonra öğesine ayarlanır `SetILInstrumentedCodeMap` `FunctionID` `false` .

`cILMapEntries` 'ndaki Dizideki öğelerin sayısı `cILMapEntries` .

`rgILMapEntries` 'ndaki Her biri bir MSIL sapmasını belirten COR_IL_MAP yapıları dizisi.

## <a name="remarks"></a>Açıklamalar

Profil Oluşturucu genellikle bu yöntemi işaretlemek için (örneğin, belirli bir kaynak satırına ulaşıldığında bildirmek üzere) bir yöntemin kaynak koduna deyimler ekler. `SetILInstrumentedCodeMap` profil oluşturucunun özgün MSIL talimatlarını yeni konumlarına eşlemesine olanak sağlar. Bir profil oluşturucu, belirli bir yerel kenar için özgün MSIL sapmasını almak üzere [ICorProfilerInfo:: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) metodunu kullanabilir.

Hata ayıklayıcı, her bir eski kaydırın orijinal, değiştirilmemiş MSIL kodu içindeki bir MSIL denkleşeceğini ve her yeni kaydırın yeni, belgelenmiş koddaki MSIL denkleşeceğini varsayacaktır. Haritanın artan sırada sıralanması gerekir. Adımlamayı düzgün şekilde çalışmak için aşağıdaki yönergeleri izleyin:

- Belgelenmiş MSIL kodunu yeniden düzenleme.

- Özgün MSIL kodunu kaldırmayın.

- Haritadaki program veritabanı (PDB) dosyasındaki tüm sıra noktalarına ait girişleri dahil edin. Eşleme, eksik girişleri enterpolamıyor. Bu nedenle, aşağıdaki haritada verilmiştir:

  (0 eski, 0 yeni)

  (5 eski, 10 yeni)

  (9 eski, 20 yeni)

  - 0, 1, 2, 3 veya 4 ' ün eski bir kayması, 0 ' dan yeni bir uzaklığa eşlenecek.

  - 5, 6, 7 veya 8 ' in eski bir kayması, yeni %10 ' a eşlenir.

  - Daha eski bir 9 veya üzeri fark, 20. yeni uzaklığa eşlenir.

  - 0, 1, 2, 3, 4, 5, 6, 7, 8 ya da 9 ' un yeni bir kayması, 0 ' dan eski uzaklığa eşlenir.

  - 10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 ' un yeni bir kayması, 5 eski uzaklığa eşlenir.

  - 20 veya üzeri yeni bir konum, eski konum 9 ' A eşlenir.

.NET Framework 3,5 ve önceki sürümlerde, `rgILMapEntries` [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) yöntemini çağırarak diziyi ayırabilirsiniz. Çalışma zamanı bu belleğin sahipliğini aldığı için profil oluşturucu onu serbest bırakmayı denememelidir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
