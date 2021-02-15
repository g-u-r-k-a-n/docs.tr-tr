---
description: "Hakkında daha fazla bilgi edinin: EventLogSource 'ta belirtilen kaynak adı, EventLogName içinde belirtilenden farklı bir günlüğe kayıtlı"
title: EventLogSource 'da belirtilen kaynak adı, EventLogName içinde belirtilenden farklı bir günlüğe kayıtlı
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: d6b9c1265276f94369d37e6ac55604b761fb9bcc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455463"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>EventLogSource 'da belirtilen kaynak adı, EventLogName içinde belirtilenden farklı bir günlüğe kayıtlı

, `EventLog` Farklı bir günlüğe kayıtlı bir kaynağa başvurmaya çalışıyor. Bir olay günlüğüne giriş yazıyorsanız, özelliğini belirtmeniz gerekir <xref:System.Diagnostics.EventLog.Source%2A> . <xref:System.Diagnostics.EventLog.Source%2A>Özelliği, bileşenini olay günlüğüne geçerli bir giriş kaynağı olarak kaydeder. Tek bir kaynak, aynı anda yalnızca bir olay günlüğü ile ilişkilendirilebilir (ve bu nedenle girdileri yazılabilir).  
  
 Varsayılan olarak, ilk olarak bileşeninizi geçerli bir kaynak olarak kaydettirmeden bir girdi yazmaya çalışırsanız, sistem, kaynak dize olarak özelliğin değerini kullanarak kaynağı otomatik olarak olay günlüğüne kaydeder <xref:System.Diagnostics.EventLog.Source%2A> .  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Kaynağın doğru günlüğe kaydedildiğinden emin olun. Bunu yapmak için, <xref:System.Diagnostics.EventLog.CreateEventSource%2A> uygulamanızı olay günlüğüne benzersiz bir şekilde tanımlayan bir dize belirtmek için yöntemini veya aşırı yüklemelerinin birini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay günlüklerini yönetme](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))
- [Olay günlüğü başvuruları](/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))
- [Nasıl yapılır: uygulamanızı olay günlüğü girdilerinin kaynağı olarak ekleme](/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))
- [Nasıl yapılır: olay kaynağını kaldırma](/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))
