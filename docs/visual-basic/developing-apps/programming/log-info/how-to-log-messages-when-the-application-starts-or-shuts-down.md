---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: uygulama başladığında veya kapandığında Iletileri günlüğe kaydetme (Visual Basic)'
title: 'Nasıl yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 545a57c3666aa12e3763961d05067face9fe324a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775194"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Nasıl Yapılır: Uygulama Başlarken veya Kapanırken İletileri Günlüğe Kaydetme (Visual Basic)

`My.Application.Log` `My.Log` Uygulamanızda gerçekleşen olaylar hakkındaki bilgileri günlüğe kaydetmek için ve nesnelerini kullanabilirsiniz. Bu örnek `My.Application.Log.WriteEntry` , `Startup` `Shutdown` izleme bilgilerini yazmak için yönteminin ve olaylarıyla birlikte nasıl kullanılacağını gösterir.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Uygulamanın olay işleyicisi koduna erişmek için  
  
1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' i seçin.  
  
2. **Uygulama** sekmesine tıklayın.  
  
3. Kod düzenleyicisini açmak için **uygulama olaylarını görüntüle** düğmesine tıklayın.  
  
     Bu, ApplicationEvents. vb dosyasını açar.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Uygulama başladığında iletileri günlüğe kaydetmek için  
  
1. ApplicationEvents. vb dosyasını kod düzenleyicisinde açın. **Genel** menüsünde **MyApplication olayları**' nı seçin.  
  
2. **Bildirimler** menüsünde, **Başlangıç**' ı seçin.  
  
     Uygulama, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> ana uygulama çalışmadan önce olayı başlatır.  
  
3. `My.Application.Log.WriteEntry`Yöntemini `Startup` olay işleyicisine ekleyin.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Uygulama kapandığında iletileri günlüğe kaydetmek için  
  
1. ApplicationEvents. vb dosyasını kod düzenleyicisinde açın. **Genel** menüsünde **MyApplication olayları**' nı seçin.  
  
2. **Bildirimler** menüsünde, **kapatır**' ı seçin.  
  
     Uygulama, uygulamayı kapatmadan <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> önce ana uygulama çalıştırıldıktan sonra başlatır.  
  
3. `My.Application.Log.WriteEntry`Yöntemini `Shutdown` olay işleyicisine ekleyin.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a>Örnek  

 Kod düzenleyicisinde uygulama olaylarına erişmek için **Proje tasarımcısını** kullanabilirsiniz. Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md)
