---
title: Performans Sayaçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 0b63cdc145ff8806c26b255500bcb2a132e9ef9f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596506"
---
# <a name="using-performance-counters"></a>Performans Sayaçlarını Kullanma
Bu örnek, Windows Communication Foundation (WCF) performans sayaçlarına nasıl erişileceğini ve Kullanıcı tanımlı performans sayaçlarının nasıl oluşturulacağını gösterir. Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnekte istemci, hizmetin dört yöntemini çağırır `ICalculator` . İstemci, Kullanıcı tarafından kesintiye gelinceye kadar bunu yapmaya devam eder. Hizmet değişmeden kalır.  
  
 Aşağıdaki örnek yapılandırmada gösterildiği gibi, hizmetinin Web. config dosyasının Tanılama bölümünde performans sayaçları etkinleştirilir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 Bu görev, [yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak da yapılabilir.  
  
 Performans sayaçları etkinleştirildiğinde, hizmet için tüm WCF performans sayacı paketi etkinleştirilir. .NET Framework, performans verilerini otomatik olarak üç düzeyde tutar: `ServiceModelService` , `ServiceModelEndpoint` ve `ServiceModelOperation` . Bu düzeylerin her biri, "çağrı", "saniyedeki çağrı" ve "güvenlik çağrıları yetkilendirilmemiş" gibi performans sayaçlarına sahiptir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
### <a name="to-view-performance-data"></a>Performans verilerini görüntülemek için  
  
1. Sırasıyla **Başlat**, **Çalıştır..**. ' a tıklayarak performans Izleyicisi aracını başlatın, `perfmon` **Tamam** ' a tıklayın, Tamam ' a tıklayın veya denetim masasından, **Yönetim Araçları** ' nı seçin ve **performans**' ı çift  
  
    > [!NOTE]
    > Örnek kod çalışmadığı sürece sayaç ekleyemezsiniz.  
  
2. Seçerek listelenen performans sayaçlarını kaldırın ve Sil tuşuna basın.  
  
3. Grafik bölmesine sağ tıklayıp **Sayaç Ekle**' yı seçerek WCF sayaçlarını ekleyin. **Sayaç Ekle** iletişim kutusunda, performans nesnesi açılan listesi kutusunda **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 veya ServiceModelService 3.0.0.0 öğesini** seçin. Listeden görüntülemek istediğiniz sayaçları seçin.  
  
    > [!NOTE]
    > Bilgisayarda çalışan bir WCF hizmeti yoksa, bir hizmet için WCF performans sayacı yoktur.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Sayaçları etkinleştirmek üzere yapılandırma düzenleyicisini kullanmak için  
  
1. SvcConfigEditor. exe ' nin bir örneğini açın.  
  
2. Dosya menüsünde **Aç** ' a ve ardından **yapılandırma dosyası...** öğesine tıklayın.  
  
3. Örnek uygulamanın hizmet klasörüne gidin ve Web. config dosyasını açın.  
  
4. Yapılandırma ağacında **Tanılamalar** ' a tıklayın.  
  
5. **Tanılama** penceresindeki **performans sayacını** ' tümünü ' gösterecek şekilde değiştirin.  
  
6. Yapılandırma dosyasını kaydedin ve düzenleyiciden çıkın.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Izleme örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
