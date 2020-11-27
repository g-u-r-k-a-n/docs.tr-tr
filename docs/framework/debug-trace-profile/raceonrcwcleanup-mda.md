---
title: raceOnRCWCleanup MDA
description: RCW başka bir iş parçacığında veya .NET 'teki iş parçacığı yığınında kullanılıyorsa etkinleştirilen Esrcwcleanup yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: 393c5ea44108445a9a1a9d16e7d1d192eced5740
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271453"
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup MDA

`raceOnRCWCleanup`Yönetilen hata ayıklama Yardımcısı (MDA), ortak dil çalışma zamanı (CLR), bir çalışma zamanı çağrılabilir sarmalayıcı (RCW), yöntemi gibi bir komut kullanılarak yapıldığında bir [çalışma zamanında çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) kullanımda olduğunu algıladığında etkinleştirilir <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> .  
  
## <a name="symptoms"></a>Belirtiler  

 Ya da benzer bir yöntemi kullanarak bir RCW boşaltmasından veya sonrasında ihlal veya bellek bozulmasına erişin <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> .  
  
## <a name="cause"></a>Nedeni  

 RCW, başka bir iş parçacığında veya boşaltma iş parçacığı yığınında kullanılıyor.  Kullanımda olan bir RCW yayımlanamaz.  
  
## <a name="resolution"></a>Çözüm  

 Geçerli ya da diğer iş parçacıklarında kullanımda olabilecek bir RCW boşaltımı yok.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  

 Bu MDA, CLR üzerinde hiçbir etkisi yoktur.  
  
## <a name="output"></a>Çıkış  

 Hatayı açıklayan bir ileti.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
