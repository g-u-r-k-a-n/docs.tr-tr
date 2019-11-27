---
title: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: f3fd0ed0388276f1400bf77d0abfb488634a45a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353600"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme (Visual Basic)

`My.Application.Log` nesnesi, çeşitli günlük dinleyicilerine bilgi yazabilir. Günlük dinleyicileri bilgisayarın yapılandırma dosyası tarafından yapılandırılır ve bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir. Bu konu, varsayılan ayarları ve uygulamanızın ayarlarının nasıl belirleneceğini açıklar.

Varsayılan çıkış konumları hakkında daha fazla bilgi için bkz. [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

### <a name="to-determine-the-listeners-for-myapplicationlog"></a>My. Application. log için dinleyicileri belirleme

1. Derlemenin yapılandırma dosyasını bulun. Derlemeyi geliştiriyorsanız, **Çözüm Gezgini**Visual Studio 'da App. config dosyasına erişebilirsiniz. Aksi takdirde, yapılandırma dosya adı ". config" ile eklenen derlemenin adıdır ve derlemeyle aynı dizinde bulunur.

    > [!NOTE]
    > Her derlemenin bir yapılandırma dosyası yoktur.

    Yapılandırma dosyası bir XML dosyasıdır.

2. `<sources>` bölümünde yer alan "DefaultSource" `name` özniteliğiyle birlikte `<source>` bölümünde `<listeners>` bölümünü bulun. `<sources>` bölümü, üst düzey `<configuration>` bölümünde `<system.diagnostics>` bölümünde bulunur.

    Bu bölümler yoksa, bilgisayarın yapılandırma dosyası `My.Application.Log` log dinleyicilerini yapılandırabilir. Aşağıdaki adımlarda, bilgisayar yapılandırma dosyasının neyi tanımladığı nasıl belirleneceği açıklanır:

    1. Bilgisayarın Machine. config dosyasını bulun. Genellikle, *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* dizininde bulunur, burada `SystemRoot` işletim sistemi dizinidir ve `frameworkVersion` .NET Framework sürümüdür.

        Machine. config dosyasındaki ayarlar bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir.

        Aşağıda listelenen isteğe bağlı öğeler yoksa, bunları oluşturabilirsiniz.

    2. En üst düzey `<system.diagnostics>` bölümündeki `<configuration>` bölümünde bulunan `<sources>` bölümündeki "DefaultSource" `name` özniteliğine sahip `<source>` bölümündeki `<listeners>` bölümünü bulun.

        Bu bölümler yoksa `My.Application.Log` yalnızca varsayılan günlük dinleyicilerine sahiptir.

3. <`listeners>` bölümünde <`add>` öğelerini bulun.

     Bu öğeler `My.Application.Log` kaynağına adlandırılmış günlük dinleyicileri ekler.

4. `<add>` öğelerini, üst düzey `<configuration>` bölümündeki `<system.diagnostics>` bölümünde bulunan `<sharedListeners>` bölümündeki günlük dinleyicilerinin adlarıyla bulun.

5. Birçok türdeki paylaşılan dinleyici için, dinleyicinin başlatma verileri, dinleyicinin verileri nerede yönlendirdiği hakkında bir açıklama içerir.

    - <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> dinleyicisi, giriş bölümünde açıklandığı gibi bir dosya günlüğüne yazar.

    - <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> dinleyicisi, `initializeData` parametresi tarafından belirtilen bilgisayar olay günlüğüne bilgi yazar. Bir olay günlüğünü görüntülemek için **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi**kullanabilirsiniz. Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md)bölümüne bakın.

    - <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> ve <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> dinleyicileri `initializeData` parametresinde belirtilen dosyaya yazar.

    - <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> dinleyicisi komut satırı konsoluna yazar.

    - Diğer günlük dinleyicisi türlerinin yazma bilgileri hakkında daha fazla bilgi için, bu türün belgelerine başvurun.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Nasıl Yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [.NET Framework'te ETW Olayları](../../../../framework/performance/etw-events.md)
- [Sorun Giderme: Günlük Dinleyicileri](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
