---
title: marshalCleanupError MDA
description: Geçici yapıları temizlerken beklenmeyen bir hata oluştuğundan çağrılan Marshalcleanuıperror yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
ms.openlocfilehash: e65136f022caa7b1e18a27f7b97a4ef4c27f42d3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271205"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError MDA

`marshalCleanupError`Ortak dil çalışma zamanı (CLR), yerel ve yönetilen kod sınırları arasında veri türlerini sıralama için kullanılan geçici yapıları ve belleği temizlemeye çalışırken bir hatayla karşılaştığında, yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  

 Yerel ve yönetilen kod geçişleri yaparken bellek sızıntısı oluşur, iş parçacığı kültürü gibi çalışma zamanı durumu geri yüklenmez veya temizleme sırasında hatalar oluşur <xref:System.Runtime.InteropServices.SafeHandle> .  
  
## <a name="cause"></a>Nedeni  

 Geçici yapılar temizlenirken beklenmeyen bir hata oluştu.  
  
## <a name="resolution"></a>Çözüm  

 <xref:System.Runtime.InteropServices.SafeHandle>Hatalar için tüm yıkıcıyı, sonlandırıcıyı ve özel sıralayıcı uygulamalarını inceleyin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  

 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  

 Temizleme sırasında başarısız olan işlemi bildiren bir ileti.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
