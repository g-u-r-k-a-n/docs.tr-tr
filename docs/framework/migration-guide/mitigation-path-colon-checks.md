---
title: 'Risk azaltma: yol Iki nokta denetimleri'
description: Uygun sürücü ayırıcı sözdizimi (iki nokta üst üste) için denetimleri desteklemek üzere .NET Framework 4.6.2 ' de yapılan değişiklikler hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: 03f1c7249549aae7e3bef986c97fb5f320fbeb2f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283464"
---
# <a name="mitigation-path-colon-checks"></a>Risk azaltma: yol Iki nokta denetimleri

.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, daha önce desteklenmeyen yolları (hem uzunluk hem de biçim bakımından) desteklemeye yönelik bir dizi değişiklik yapılmıştır. Özellikle, uygun sürücü ayırıcı söz dizimini (iki nokta üst üste) denetler.  
  
## <a name="impact"></a>Etki  

 Bu değişiklikler, <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemlerinin daha önce DESTEKLEDIĞI bazı URI yollarını engeller.  
  
## <a name="mitigation"></a>Risk azaltma  

 Daha önce ve yöntemleri tarafından desteklenmeyen önceden kabul edilebilir bir yol sorununu geçici olarak çözmek için aşağıdakileri <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> yapabilirsiniz <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> :  
  
- Düzeni bir URL 'den el ile kaldırın. Örneğin, `file://` BIR URL 'den kaldırın.  
  
- URI 'yi bir oluşturucuya geçirin <xref:System.Uri> ve özelliğin değerini alın <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> .  
  
- Anahtarı olarak ayarlayarak yeni yol normalleştirmesini geri çevirin `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> `true` .  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
