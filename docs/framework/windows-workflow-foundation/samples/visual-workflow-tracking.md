---
title: Görsel İş Akışı İzleme
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: 05f8fcf4c765998fc4e101d9dbef026d85b8b2fb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715516"
---
# <a name="visual-workflow-tracking"></a>Görsel İş Akışı İzleme
Bu örnek, [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]aracılığıyla kullanılabilen hata ayıklama işlevini kullanarak bir görsel iş akışı izleme uygulamasının nasıl yazılacağını gösterir.

## <a name="sample-details"></a>Örnek Ayrıntılar
 Uygulama, bir basit akış çizelgesi iş akışı yürütür (Workflow. xaml içinde tanımlanır) ve şu anda yürütülmekte olan iş akışını göstermek için iş akışı tasarımcısını yeniden barındırır. İş akışı yürütüldüğü sırada yürütülmekte olan etkinlik sarı bir ana hat ve hata ayıklama okuna sahip olarak gösterilir. Ayrıca, iş akışı tarafından oluşturulan izleme kayıtları da uygulama penceresinde görüntülenir. İş akışı izleme hakkında daha fazla bilgi için bkz. [Iş akışı izleme ve izleme](../workflow-tracking-and-tracing.md). İş akışı tasarımcısını yeniden barındırma hakkında daha fazla bilgi için bkz. [iş akışı Tasarımcısı yeniden barındırma](../rehosting-the-workflow-designer.md).

 İş akışı simülatörü iki sözlük tutarak çalışır. Biri, şu anda yürütülmekte olan etkinlik nesnesi ve etkinliğin örneklendiği XAML satır numarası arasında bir eşleme içerir. Diğeri etkinlik örnek KIMLIĞI ve etkinlik nesnesi arasında bir eşleme içerir. İzleme kayıtları, özel bir izleme profili kullanılarak yayınlandığından, uygulama şu anda yürütülmekte olan etkinliğin örnek KIMLIĞINI belirler ve onu oluşturan XAML dosyasına geri eşler. Daha sonra yeniden barındırılan iş akışı Tasarımcısı, tasarımcı yüzeyinde etkinliği vurgulaması ve iş akışı hata ayıklayıcıyla aynı yöntemi kullanmaktır, özellikle etkinliğin etrafında sarı bir kenarlık çizerek ve bu yöntemin sol tarafında bir sarı ok görüntülüyor. Layana.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2010 ' deki örnek dizinden Workflowsimülatör. sln dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Örneği çalıştırmak için CTRL + F5 tuşlarına basın. Bu, Iş akışı. xaml dosyasını yeniden barındırılan bir iş akışı Tasarımcısı penceresinde görüntüler.

4. **Dosya** menüsüne tıklayın ve **iş akışını Çalıştır...** seçeneğini belirleyin.

5. Şu anda yürütülmekte olan etkinliğin daha önce açıklandığı gibi vurgulandığını ve izleme kayıtlarının uygulama penceresinin sağ tarafında görüntülendiğini unutmayın.

6. İş akışı tamamlandığında, hangi etkinliğin karşılık geldiğini denetlemek için izleme kayıtlarının herhangi birine tıklayabilirsiniz.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`
