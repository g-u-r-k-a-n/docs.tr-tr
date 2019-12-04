---
title: İzlemeyi Genişletme
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 64f9d18b68e5f2604631a72579eb45bf7f7b8372
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716391"
---
# <a name="extending-tracing"></a>İzlemeyi Genişletme
Bu örnek, istemci ve hizmet kodunda Kullanıcı tanımlı etkinlik izlemeleri yazarak Windows Communication Foundation (WCF) izleme özelliğinin nasıl genişletileceğini gösterir. Bu, kullanıcının mantıksal iş birimlerine izleme etkinlikleri ve grup izlemeleri oluşturmalarına olanak sağlar. Ayrıca, etkinlikleri aktarımlar (aynı uç nokta içinde) ve yayma (uç noktalar arasında) ile ilişkilendirmek mümkündür. Bu örnekte, izleme hem istemci hem de hizmet için etkinleştirilmiştir. İstemci ve hizmet yapılandırma dosyalarında izlemenin nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [izleme ve mesaj günlüğü](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>İzleme ve etkinlik yayma  
 Kullanıcı tanımlı etkinlik izleme, kullanıcının izlemeleri mantıksal iş birimlerine göre gruplamak, aktarımlar ve yayma aracılığıyla etkinlikleri ilişkilendirmek ve WCF izlemenin performans maliyetini azaltmak (örneğin, disk alanı maliyeti) için kendi izleme etkinliklerini oluşturmalarına olanak tanır. bir günlük dosyası).  
  
### <a name="adding-custom-sources"></a>Özel kaynak ekleme  
 Kullanıcı tanımlı izlemeler, hem istemci hem de hizmet koduna eklenebilir. İstemci veya hizmet yapılandırma dosyalarına izleme kaynakları eklemek, bu özel izlemelerin [hizmet Izleme Görüntüleyicisi aracında (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)kaydedilip görüntülenmesine izin verir. Aşağıdaki kod, `ServerCalculatorTraceSource` adlı Kullanıcı tanımlı izleme kaynağının yapılandırma dosyasına nasıl ekleneceğini gösterir.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a>Etkinlikleri ilişkilendirme  
 Etkinlikleri doğrudan uç noktalar arasında ilişkilendirmek için, `propagateActivity` özniteliği `System.ServiceModel` izleme kaynağında `true` olarak ayarlanmalıdır. Ayrıca, WCF etkinliklerinde ilerlemeden izlemeleri yaymak için, ServiceModel etkinliği Izlemenin kapalı olması gerekir. Bu, aşağıdaki kod örneğinde görülebilir.  
  
> [!NOTE]
> ServiceModel etkinlik Izlemenin kapatılması, `switchValue` özelliği tarafından belirtilen izleme düzeyiyle aynı değildir ve kapalı olarak ayarlanır.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Performans maliyetini azallama  
 `ActivityTracing` `System.ServiceModel` izleme kaynağında devre dışı olarak ayarlamak, yalnızca Kullanıcı tanımlı etkinlik izlemelerini içeren bir izleme dosyası oluşturur, hiçbir ServiceModel etkinlik izleme dahil değildir. Bu, çok daha küçük boyutta bir günlük dosyasına neden olur. Ancak, WCF işleme izlemelerinin ilişkilendirilmesi için fırsat kaybolur.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
