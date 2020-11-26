---
title: exceptionSwallowedOnCallFromCom MDA
description: .NET 'teki exceptionSwallowedOnCallFromCOM Managed hata ayıklama Yardımcısı ' nı gözden geçirin. Bu MDA, bir özel durum oluşturulursa, ancak bunu raporlamak için iyi bir yol olmadığında meydana gelir.
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 11daccb4d1e757bf2fae25858d706eee5921c509
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244359"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom MDA

`exceptionSwallowedOnCallFromCOM`Yönetilen hata ayıklama Yardımcısı (MDA), yönetilmeyen BIR HRESULT dönüş türüne sahip olmayan bir yöntem aracılığıyla com 'dan çağrılan ortak dil çalışma zamanı (CLR) kodundan bir özel durum oluştuğunda etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  

 COM 'tan yönetilen bileşen çağrısı, FALSE veya 0 değeri ile döndürür. Alternatif olarak, yöntemin bir void dönüş türü varsa, yöntemin yürütülmesi sırasında bir özel durumun oluşturulduğunu belirten bir işaret olmayabilir. Bu durumda, özel durum sessizce yakalanacaktır ve yürütme COM çağıranına döndürülür.  
  
## <a name="cause"></a>Nedeni  

 Bir özel durum oluşturuldu, ancak bunu raporlamak için geçerli bir yol yok.  
  
## <a name="resolution"></a>Çözüm  

 Yalnızca bilgilendirme, bir hatanın göstergesi olması gerekmez.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  

 Bu MDA, CLR üzerinde hiçbir etkisi yoktur. Yalnızca sessizce yakalanan özel durumlarla ilgili verileri raporlar.  
  
## <a name="output"></a>Çıkış  

 Yöntem adı, tür adı ve özel durum iletisi içeren bilgilendirici ileti.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
