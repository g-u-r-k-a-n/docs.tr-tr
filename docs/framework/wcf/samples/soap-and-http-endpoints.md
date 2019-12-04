---
title: SOAP ve HTTP Uç Noktaları
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: 93f410b8b8632b0158d0a52b12845f1e8cec132c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716680"
---
# <a name="soap-and-http-endpoints"></a>SOAP ve HTTP Uç Noktaları
Bu örnek, bir RPC tabanlı hizmetin nasıl uygulanacağını ve SOAP biçiminde ve WCF Web programlama modelini kullanarak "düz eski XML" (POX) biçiminde nasıl kullanıma sunılacağını gösterir. Hizmetin HTTP bağlaması hakkında daha fazla bilgi için bkz. [temel http hizmet](../../../../docs/framework/wcf/samples/basic-http-service.md) örneği. Bu örnek, farklı bağlamalar kullanılarak SOAP ve HTTP üzerinden aynı hizmeti açığa çıkarmak için ilgili ayrıntılara odaklanılır.  
  
## <a name="demonstrates"></a>Gösterir  
 WCF kullanarak bir RPC hizmetini SOAP ve HTTP üzerinden gösterme.  
  
## <a name="discussion"></a>Tartışma  
 Bu örnek iki bileşenden oluşur: bir WCF hizmeti içeren bir Web uygulaması projesi (hizmet) ve SOAP ve HTTP bağlamaları kullanarak hizmet işlemlerini çağıran bir konsol uygulaması (Istemci).  
  
 WCF hizmeti, giriş olarak geçirilmiş dizeyi yankı eden 2 işlem –`GetData` ve `PutData` sunar. Hizmet işlemlerine <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute>açıklama eklenir. Bu öznitelikler, bu işlemlerin HTTP projeksiyonunu denetler. Bunlara ek olarak, <xref:System.ServiceModel.OperationContractAttribute>ile açıklanırlar ve bu, SOAP bağlamaları üzerinden gösterilmesini sağlar. Hizmetin `PutData` yöntemi HTTP durum kodu kullanılarak HTTP üzerinden geri gönderilen ve SOAP üzerinden SOAP hatası olarak geri gönderilen bir <xref:System.ServiceModel.Web.WebFaultException>oluşturur.  
  
 Web. config dosyası, WCF hizmetini 3 uç nokta ile yapılandırır:  
  
- SOAP tabanlı istemciler tarafından erişim için hizmet meta verilerini kullanıma sunan ~/Service.svc/mex uç noktası.  
  
- HTTP bağlamasını kullanarak istemcilerin hizmete erişmesini sağlayan ~/Service.svc/HTTP uç noktası.  
  
- İstemcilerin HTTP bağlama üzerinden SOAP kullanarak hizmete erişmesine izin veren ~/Service.svc/SOAP uç noktası.  
  
 HTTP uç noktası, `helpEnabled` `true`olarak ayarlanan bir <`webHttp`> standart uç nokta ile yapılandırılır. Sonuç olarak, hizmet HTTP tabanlı istemcilerin hizmete erişmek için kullanabileceği, ~/Service.svc/http/Help konumunda bir XHTML tabanlı yardım sayfası sunar.  
  
 İstemci projesi, bir SOAP proxy ( **hizmet başvurusu Ekle**aracılığıyla oluşturulur) kullanarak hizmete erişmeyi ve <xref:System.Net.WebClient>kullanarak hizmete erişimi gösterir.  
  
 Örnek, Web 'de barındırılan bir hizmetten ve konsol uygulamasından oluşur. Konsol uygulaması çalışırken, istemci hizmete istekler yapar ve ilgili bilgileri, yanıtlardan konsol penceresine yazar.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1. SOAP ve HTTP uç noktaları örneği için çözümü açın.  
  
2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3. Zaten açık değilse, CTRL + W, S tuşlarına basarak **Çözüm Gezgini** penceresini açın.  
  
4. **Çözüm Gezgini** penceresinden, **hizmet** projesine sağ tıklayın ve **Yeni örnek Başlat** menüsünün görünmesi için imleci **hata ayıklama** bağlam menüsü seçeneğinin üzerine getirin. **Yeni örnek Başlat**' a tıklayın. Bu, hizmeti barındıran ASP.NET geliştirme sunucusunu başlatır.  
  
5. Çözüm Gezgini Windows 'da, Istemci projesine sağ tıklayın ve **Yeni örnek Başlat** menüsünün görünmesi Için Imleci **hata ayıklama** bağlam menüsü seçeneğinin üzerine getirin. **Yeni örnek Başlat**' a tıklayın.  
  
6. İstemci Konsolu penceresi görünür ve çalışan hizmetin URI 'sini ve çalışan hizmet için HTML yardım sayfasının URI 'sini sağlar. Herhangi bir noktada, yardım sayfasının URI 'sini bir tarayıcıda yazarak HTML yardım sayfasını görüntüleyebilirsiniz.  
  
7. Örnek çalışırken, istemci geçerli etkinliğin durumunu yazar.  
  
8. İstemci konsol uygulamasını sonlandırmak için herhangi bir tuşa basın.  
  
9. Hizmetin hata ayıklamasını durdurmak için SHIFT + F5 tuşlarına basın.  
  
10. Windows bildirim alanında, ASP.NET Development Server simgesine sağ tıklayın ve bağlam menüsünden **Durdur** ' u seçin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
