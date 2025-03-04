---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: GetAppDomainStaticAddress yöntemi'
title: ICorProfilerInfo2::GetAppDomainStaticAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
ms.openlocfilehash: 4ef8511e75a18f7626fa7a30ea194140de051bb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753243"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a>ICorProfilerInfo2::GetAppDomainStaticAddress Yöntemi

Belirtilen uygulama etki alanının kapsamındaki belirtilen uygulama etki alanı-statik alanının adresini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parametreler  

 `classId`  
 'ndaki İstenen uygulama etki alanı-statik alanını içeren sınıfın sınıf KIMLIĞI.  
  
 `fieldToken`  
 'ndaki İstenen uygulama etki alanı-statik alanı için meta veri belirteci.  
  
 `appDomainId`  
 'ndaki İstenen statik alan için kapsam olan uygulama etki alanının KIMLIĞI.  
  
 `ppAddress`  
 dışı Belirtilen uygulama etki alanı içindeki statik alanın adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetAppDomainStaticAddress`Yöntemi aşağıdakilerden birini döndürebilir:  
  
- Belirtilen bağlamda verilen statik alana bir adres atanmadığı takdirde bir CORPROF_E_DATAINCOMPLETE HRESULT.  
  
- Çöp toplama yığınında olabilecek nesnelerin adresleri. Bu adresler çöp toplamadan sonra geçersiz hale gelebilmelidir, bu nedenle çöp toplama işleminden sonra profil oluşturucular geçerli olduğunu varsaymamalıdır.  
  
 Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetAppDomainStaticAddress` tüm statik alanları için CORPROF_E_DATAINCOMPLETE döndürür, ancak bazı statik alanlar zaten başlatılmış ve atık toplama nesnelerini kök olarak oluşturacak olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
