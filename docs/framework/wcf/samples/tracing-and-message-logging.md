---
title: İleti İzleme ve Kaydetme
description: Bu WFC örneğini kullanarak izlemeleri ve ileti günlüklerini görüntülemek için hizmet Izleme Görüntüleyicisi aracı 'nı (SvcTraceViewer.exe) nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: ec29ac03e8930bd30ccd7e90dce3993ca9e7443a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255422"
---
# <a name="tracing-and-message-logging"></a>İleti İzleme ve Kaydetme

Bu örnek, izleme ve ileti günlüğe kaydetmenin nasıl etkinleştirileceğini gösterir. Ortaya çıkan izlemeler ve ileti günlükleri, [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenir. Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="tracing"></a>İzleme  

 Windows Communication Foundation (WCF), ad alanında tanımlanan izleme mekanizmasını kullanır <xref:System.Diagnostics> . Bu izleme modelinde, izleme verileri uygulamaların uygulayan izleme kaynakları tarafından üretilir. Her kaynak bir ad ile tanımlanır. İzleme tüketicileri, bilgi almak istedikleri izleme kaynakları için izleme dinleyicileri oluşturur. İzleme verileri almak için izleme kaynağı için bir dinleyici oluşturmanız gerekir. WCF 'de, hizmet modeli izleme kaynağı ayarlanarak hizmetin veya istemcinin yapılandırma dosyasına aşağıdaki kod eklenerek bu yapılabilir `switchValue` :  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 İzleme kaynakları hakkında daha fazla bilgi için [Izlemeyi yapılandırma](../diagnostics/tracing/configuring-tracing.md) konusunun Kaynak izleme bölümüne bakın.  
  
## <a name="activity-tracing-and-propagation"></a>Etkinlik Izleme ve yayma  

 `ActivityTracing` `propagateActivity` `true` `system.ServiceModel` Hem istemci hem de hizmet için izleme kaynaklarında etkinleştirilmiş ve olarak ayarlanmış olması, mantıksal işlem (etkinlik) birimleri içinde, uç noktaların içindeki etkinliklerde (etkinlik aktarımları aracılığıyla) ve birden çok uç noktayı kapsayan etkinliklerde (etkinlik kimliği yayma aracılığıyla) izleme bağıntısını sağlar.  
  
 Bu üç mekanizma (Etkinlikler, aktarımlar ve yayma), hizmet Izleme Görüntüleyicisi aracını kullanarak bir hatanın kök nedenini daha hızlı bulmanıza yardımcı olabilir. Daha fazla bilgi için bkz. [bağıntılı izlemeleri ve sorun gidermeyi görüntülemek Için hizmet Izleme görüntüleyicisini kullanma](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Kullanıcı tanımlı etkinlik izlemeleri oluşturarak ServiceModel tarafından sunulan izlemeyi genişletmek mümkündür. Kullanıcı tanımlı etkinlik izleme, kullanıcının şunları yapmak için izleme etkinlikleri oluşturmasına izin verir:  
  
- İzlemeleri mantıksal iş birimlerine göre gruplandırın.  
  
- Aktarımlar ve yayma aracılığıyla etkinlikleri ilişkilendirme.  
  
- WCF izlemenin (örneğin, bir günlük dosyasının disk alanı maliyeti) performans maliyetini azaltır.  
  
 Kullanıcı tanımlı etkinlik izleme hakkında daha fazla bilgi için lütfen [genişletme izleme](extending-tracing.md) örneğine bakın.  
  
## <a name="message-logging"></a>İleti Günlüğe Kaydetme  

 İleti günlüğe kaydetme her ikisi de herhangi bir WCF uygulamasının istemcisinde ve hizmetinde etkinleştirilebilir. İleti günlüğe kaydetmeyi etkinleştirmek için, istemci veya hizmete aşağıdaki kodu eklemeniz gerekir:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 İleti kaydedildiğinde, izleme türü istemcide mi yoksa sunucuda mı izlenmekte olduğuna bağlıdır. Örneğin, bir istemciye gönderilen "Ekle" iletisi, istemcideki "TransportWrite" kategorisinin altında izleniyorsa, hizmette "TransportRead" kategorisinin altında aynı ileti de izlenmektedir.  
  
 <xref:System.Diagnostics>İstemci App.config dosyasının veya hizmetin Web.config dosyasının bölümüne aşağıdaki kodu ekleyerek izleme dinleyicisini yapılandırın:  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 İletiler, yapılandırma dosyasında belirtilen hedef dizinde XML biçiminde günlüğe kaydedilir.  
  
> [!NOTE]
> İzleme dosyaları, başlangıçta günlük dizini oluşturulmadan oluşturulmaz. C:\logs\ dizininin var olduğundan emin olun veya dinleyici yapılandırmasında alternatif bir günlük dizini belirtin. Daha fazla bilgi için bu belgenin sonundaki ilk kurulum yönergelerine bakın.  
  
 İleti günlüğü hakkında daha fazla bilgi için bkz. [Ileti günlüğe kaydetmeyi yapılandırma](../diagnostics/configuring-message-logging.md) konusuna bakın.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Izleme ve Ileti günlüğü örneğini çalıştırmadan önce, hizmet için C:\logs\ dizinini oluşturarak. svclog dosyalarını öğesine yazın. Bu dizinin adı yapılandırma dosyasında günlüğe kaydedilecek izlemeler ve iletilerin yolu olarak tanımlanır ve değiştirilebilir. Kullanıcı ağ hizmetine Günlükler dizinine yazma erişimi verin.  
  
3. Çözümün C#, C++ veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../diagnostics/tracing/index.md)
- [AppFabric Izleme örnekleri](/previous-versions/appfabric/ff383407(v=azure.10))
