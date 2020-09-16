---
title: İş Akışlarında Hata Ayıklama
ms.date: 03/30/2017
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
ms.openlocfilehash: 31c688f5f45b41f337176108486ec2074e1915a7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543842"
---
# <a name="debugging-workflows"></a>İş Akışlarında Hata Ayıklama

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] , geliştirme ortamından çalışan iş akışlarını hata ayıklama için çeşitli seçenekler sunar. İş akışlarının tasarımcıda, XAML 'de ve kodda hata ayıklaması yapılabilir.

## <a name="debugging-in-the-workflow-designer"></a>İş Akışı Tasarımcısı hata ayıklama

Kesme noktaları, etkinliği vurgulayarak ve <kbd>F9</kbd> tuşuna basarak veya etkinliğin bağlam menüsünü kullanarak iş akışı tasarımcısında etkinliklere ayarlanabilir. İş akışının yürütülmesi, iş akışı ana bilgisayarı hata ayıklama modunda çalıştırıldığında kesilir. Aşağıdaki ekran görüntüsünde, iş akışı yürütmesi bir kesme noktasında duraklatılır. Daha fazla bilgi için bkz. [iş akışı Tasarımcısı Iş akışlarında hata ayıklama](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).

## <a name="debugging-in-xaml"></a>XAML 'de hata ayıklama

Bir iş akışı, tasarımcıda bir kesme noktasında duraklatılmışsa, iş akışının XAML 'de hata ayıklaması de yapılabilir. XAML 'de yürütme noktasını görüntülemek için iş akışı yürütme duraklatıldığında iş akışı tasarımcısında **XAML görünümü** ' nü seçin. Çözüm Gezgini ' nden tasarımcıda iş akışını yeniden açarak, hata ayıklama tasarımcıya geri dönebilir. Daha fazla bilgi için bkz. [nasıl yapılır: iş akışı TASARıMCıSı xaml 'de hata ayıklama](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).

## <a name="debugging-in-code"></a>Kodda hata ayıklama

Bir kesme noktası ayarlamak için, kod bölmesinin sol kenar boşluğuna tıklayın veya imleci ayarlamak istediğiniz satırdaki imleç ile <kbd>F9</kbd> tuşuna basın.

## <a name="attaching-to-a-workflow-process"></a>Bir Iş akışı Işlemine iliştirme

İş akışı hata ayıklaması Ayrıca Visual Studio 'nun bir işleme iliştirmek için altyapısını destekler. Bu, iş akışı yazarının Internet Information Services (IIS) 7,0 gibi farklı bir konak ortamında çalışan bir iş akışında hata ayıklamasına olanak sağlar.

## <a name="remote-debugging"></a>Uzaktan Hata Ayıklama

Windows Workflow Foundation (WF) uzaktan hata ayıklama işlevleri, diğer Visual Studio bileşenleri için uzaktan hata ayıklama ile aynı şekilde çalışır. Uzaktan hata ayıklamayı kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzaktan hata ayıklamayı etkinleştirme](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100)).

> [!NOTE]
> İş akışı uygulaması x86 mimarisini hedefliyorsa ve 64 bitlik bir işletim sistemi çalıştıran bir bilgisayarda barındırılıyorsa, uzak bilgisayarda Visual Studio yüklü değilse veya iş akışı uygulamasının hedefi **herhangi BIR CPU**olarak değiştirilmediği takdirde uzaktan hata ayıklama çalışmaz.

## <a name="extending-the-workflow-debugging-service"></a>Iş akışı hata ayıklama hizmetini genişletme

İş akışı hata ayıklayıcısı hizmeti artık geneldir ve yeniden barındırılan bir tasarımcıda izleme, simülasyon ve hata ayıklama gibi özel uygulamalar oluşturmak için kullanılabilir. Daha fazla bilgi için <xref:System.Activities.Presentation.Debug.DebuggerService> makalesine bakın.
