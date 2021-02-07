---
description: 'Daha fazla bilgi edinin: Creategeçmişini okuyucu Işlevi'
title: CreateHistoryReader İşlevi
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
ms.openlocfilehash: 0943f3d0f3322d34ed92c0a96b909e4d63ec5e7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761128"
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader İşlevi

Belirtilen dosya için bir geçmiş okuyucu oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a>Parametreler  

 `wzFilePath`  
 'ndaki Dosya yolu.  
  
 `ppHistoryReader`  
 dışı Başarılı tamamlandığında, geçmiş okuyucu için bir işaretçi içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki tabloda açıklanan değerlere ek olarak, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.  
  
|Dönüş kodu|Description|  
|-----------------|-----------------|  
|S_OK|Metodun başarıyla tamamlandığını gösterir.|  
|E_INVALIDARG|`wzFilePath`Bunun veya `ppHistoryReader` null bir başvuruya ayarlandığını gösterir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Kitaplık:** Fusion.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Genel Statik İşlevleri](fusion-global-static-functions.md)
