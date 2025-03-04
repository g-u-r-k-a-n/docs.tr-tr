---
title: invalidGCHandleCookie MDA
description: Geçersiz bir IntPtr tanımlama bilgisinden bir GCHandle dönüştürme denendiğinde etkinleştirilen ınvalidgchandtacookie yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: 36806498445da78c8d9dd5c51c1903b253a39da0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272611"
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie MDA

`invalidGCHandleCookie`Geçersiz bir <xref:System.IntPtr> tanımlama bilgisinden öğesine dönüştürme denendiğinde yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir <xref:System.Runtime.InteropServices.GCHandle> .  
  
## <a name="symptoms"></a>Belirtiler  

 ' Dan ' i kullanmaya veya almaya çalışırken erişim ihlalleri ve bellek bozulması gibi tanımsız davranışlar <xref:System.Runtime.InteropServices.GCHandle> <xref:System.IntPtr> .  
  
## <a name="cause"></a>Nedeni  

 Tanımlama bilgisi büyük olasılıkla bir ' dan oluşturulmadığı için geçersiz, <xref:System.Runtime.InteropServices.GCHandle> <xref:System.Runtime.InteropServices.GCHandle> zaten serbest bırakılmış olan bir tanımlama bilgisidir, <xref:System.Runtime.InteropServices.GCHandle> farklı bir uygulama etki alanındaki bir tanımlama bilgisidir veya yerel koda bir <xref:System.Runtime.InteropServices.GCHandle> atama denendiğinde, clr 'ye geri geçirilmiş <xref:System.IntPtr> .  
  
## <a name="resolution"></a>Çözüm  

 İçin geçerli bir <xref:System.IntPtr> tanımlama bilgisi belirtin <xref:System.Runtime.InteropServices.GCHandle> .  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  

 Bu MDA etkinleştirildiğinde, hata ayıklayıcı artık kök nesneleri nesnelerine geri izleyemez çünkü geri geçirilen tanımlama bilgisi değerleri, MDA etkin olmadığında döndürülmeden farklı.  
  
## <a name="output"></a>Çıkış  

 Geçersiz <xref:System.IntPtr> tanımlama bilgisi değeri bildirildi.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
