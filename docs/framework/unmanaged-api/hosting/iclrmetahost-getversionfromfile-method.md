---
title: ICLRMetaHost::GetVersionFromFile Metodu
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
ms.openlocfilehash: f5e0ead41ebd13c259c24fa0c02bcc9a3b33e0fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689452"
---
# <a name="iclrmetahostgetversionfromfile-method"></a>ICLRMetaHost::GetVersionFromFile Metodu

Bir derlemenin özgün .NET Framework derleme sürümünü (meta verilerde depolanır), dosya yolu olarak alır. Bu yöntem, [GetFileVersion](getfileversion-function.md) işlevinin yerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pwzFilePath`  
 'ndaki Tüm derleme dosyası yolu.  
  
 `pwzbuffer`  
 dışı Meta verilerde depolanan .NET Framework derleme sürümü, "v *A*" biçimindedir. *B*[.*X*] ". *A*, *B* ve *X* , ana sürüme, ikincil sürüme ve yapı numarasına karşılık gelen ondalık sayılardır. Bu dizenin uzunluğu MAX_PATH sınırlıdır.  
  
> [!NOTE]
> Bu çıktı, C:\Windows\Microsoft.NET\Framework. altında göründüğü gibi .NET Framework sürümünün dizin adıyla eşleşir.  
  
 Örnek değerler şunlardır "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" ve "v 4.0. *X*", burada *x* , yüklü yapı numarasına bağlıdır. "V" ön ekinin gerekli olduğunu unutmayın.  
  
 `pcchBuffer`  
 [in, out] `pwzbuffer` Arabellek taşmalarını önlemek için boyutu.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
|E_POINTER|`pwzbuffer` ya da `pcchBuffer` null.|  
|HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)|Arabellek çok küçük.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MetaHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRMetaHost Arabirimi](iclrmetahost-interface.md)
- [Hosting](index.md)
