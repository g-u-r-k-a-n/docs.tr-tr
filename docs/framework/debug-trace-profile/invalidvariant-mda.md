---
title: invalidVariant MDA
description: Yerel/yönetilmeyen öğesinden yönetilen koddan gelen bir çağrıda geçersiz bir VARYANTA karşılaşılırsa çağrılan ınvalidvariant yönetilen hata ayıklama Yardımcısı ' nı gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
ms.openlocfilehash: f0667a54e950ead27000eb6b93ebd547dea1cfb0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281316"
---
# <a name="invalidvariant-mda"></a>invalidVariant MDA

`invalidVariant`Yönetilen hata ayıklama Yardımcısı (MDA), `VARIANT` yerel veya yönetilmeyen koddan yönetilen koda yapılan bir çağrı sırasında geçersiz bir yapıyla karşılaşıldığında etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  

 Bir nesnenin bir nesneye sıralamasını içeren yerel ve yönetilen kod arasındaki geçiş sırasında beklenmeyen davranış `VARIANT` .  
  
## <a name="cause"></a>Nedeni  

 Yerel kod, yönetilen koda hatalı biçimlendirilmiş bir yapı geçirmektedir `VARIANT` .  Çalışma zamanı bunu `VARIANT` bir nesne için sıralama girişiminde bulunur ve geçerli DEĞILSE MDA öğesini etkinleştirir `VARIANT` . `VARIANT` `VARIANT` `VARTYPE` VT_EMPTY &#124; VT_BYREF ya da VT_VARIANT ile geçersiz bir örnek içerir `VARIANT` `VARTYPE` .  
  
## <a name="resolution"></a>Çözüm  

 ' İ geçirerek yerel veya yönetilmeyen kod `VARIANT` , `VARIANT` doğru şekilde oluşturulmuş ve başlatılmış olduğundan emin olmalıdır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  

 MDA çalışma zamanının davranışı üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  

 Çalışma zamanının `VARIANT` yönetilmeyen bir modül tarafından yönetilen koda geçersiz şekilde geçtiğini belirten BIR MDA iletisi.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
