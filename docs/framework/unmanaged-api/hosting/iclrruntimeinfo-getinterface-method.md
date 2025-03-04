---
description: ': ICLRRuntimeInfo:: GetInterface yöntemi hakkında daha fazla bilgi edinin'
title: ICLRRuntimeInfo::GetInterface Metodu
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
ms.openlocfilehash: 5a5c55823ff9954735a712423d8aaab1256c947d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637137"
---
# <a name="iclrruntimeinfogetinterface-method"></a>ICLRRuntimeInfo::GetInterface Metodu

CLR 'yi geçerli işleme yükler ve [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md)ve [ımetadatadağıtıserex](../metadata/imetadatadispenser-interface.md)gibi çalışma zamanı arabirimi işaretçilerini döndürür.  
  
 Bu yöntem, `CorBindTo` [KULLANıMDAN kaldırılan clr barındırma işlevleri](deprecated-clr-hosting-functions.md) bölümündeki tüm * işlevlerinin yerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>Parametreler  

 `rclsid`  
 'ndaki Coclass için CLSID arabirimi.  
  
 `riid`  
 'ndaki İstenen arabirimin IID 'si `rclsid` .  
  
 `ppUnk`  
 dışı Sorgulanan arabirime yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`ppUnk` null.|  
|E_OUTOFMEMORY|İsteği işlemek için yeterli kullanılabilir bellek yok.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Farklı bir çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesine zaten bağlıydı.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem CLR 'nin yüklenmesine, ancak başlatılmamasını sağlar.  
  
 Aşağıdaki tabloda ve için desteklenen birleşimler gösterilmektedir `rclsid` `riid` .  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|CLSID_CorMetaDataDispenser|IID_IMetaDataDispenser, IID_IMetaDataDispenserEx|  
|CLSID_CorMetaDataDispenserRuntime|IID_IMetaDataDispenser, IID_IMetaDataDispenserEx|  
|CLSID_CorRuntimeHost|IID_ICorRuntimeHost|  
|CLSID_CLRRuntimeHost|IID_ICLRRuntimeHost|  
|CLSID_TypeNameFactory|IID_ITypeNameFactory|  
|CLSID_CLRDebuggingLegacy|IID_ICorDebug|  
|||  
|CLSID_CLRStrongName|IID_ICLRStrongName|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRRuntimeInfo Arabirimi](iclrruntimeinfo-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [Hosting](index.md)
