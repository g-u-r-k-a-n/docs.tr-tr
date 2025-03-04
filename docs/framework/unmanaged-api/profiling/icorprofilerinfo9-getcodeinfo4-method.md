---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo9:: GetCodeInfo4 yöntemi'
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: c7897e266fbb84d44df719c127e24bd375b560bb
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759097"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a>ICorProfilerInfo9:: GetCodeInfo4 yöntemi

Yerel kod başlangıç adresi verildiğinde, bu kodu depolayan sanal bellek bloklarını döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a>Parametreler

`pNativeCodeStartAddress` 'ndaki Yerel bir işlevin başlangıcına yönelik bir işaretçi.

`cCodeInfos` 'ndaki `codeInfos` Dizinin boyutu.

`pcCodeInfos` dışı [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarının toplam sayısına yönelik bir işaretçi.

`codeInfos` dışı Arayan tarafından sağlanmış arabellek. Yöntem çağrıldıktan sonra, `COR_PRF_CODE_INFO` her biri yerel kod bloğunu açıklayan bir yapı dizisi içerir.

## <a name="remarks"></a>Açıklamalar

`GetCodeInfo4`Yöntemi, bir yöntemin farklı yerel sürümleri için kod bilgilerini aramak dışında, [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md)ile benzerdir.

> [!NOTE]
> `GetCodeInfo4` bir çöp toplama tetiklenebilir.

Kapsamlar, artan ortak ara dil (CıL) kaydırmasının sırasına göre sıralanır.

`GetCodeInfo4`Geri döndüğünde, `codeInfos` arabelleğin tüm [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapılarını içerecek kadar büyük olduğunu doğrulamanız gerekir. Bunu yapmak için değerini `cCodeInfos` parametresinin değeriyle karşılaştırın `cchName` . `cCodeInfos` [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısının boyutuna göre ayrılmışsa `pcCodeInfos` , daha büyük bir arabellek ayırarak, `codeInfos` `cCodeInfos` Yeni, daha büyük boyutla güncelleştirin ve `GetCodeInfo4` yeniden çağırın.

Alternatif olarak, `GetCodeInfo4` `codeInfos` doğru arabellek boyutunu elde etmek için ilk olarak sıfır uzunluklu bir arabellek ile çağrı yapabilirsiniz. Daha sonra `codeInfos` arabellek boyutunu ' de döndürülen değere ayarlayabilir `pcCodeInfos` , [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) yapısının boyutuyla çarpılır ve `GetCodeInfo4` yeniden çağırabilirsiniz.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET sürümleri:**[!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo9 Arabirimi](ICorProfilerInfo9-interface.md)
