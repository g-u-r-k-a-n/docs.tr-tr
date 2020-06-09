---
title: JSON ve XML ile AJAX Hizmeti Örneği
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 8f70b6aa2e61d01a075a6edb3fe490ef593e73b0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575959"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>JSON ve XML ile AJAX Hizmeti Örneği

Bu örnek, JavaScript Nesne Gösterimi (JSON) veya XML verileri döndüren zaman uyumsuz bir JavaScript ve XML (AJAX) hizmeti oluşturmak için Windows Communication Foundation (WCF) kullanımını gösterir. Bir Web tarayıcısı istemcisinden JavaScript kodu kullanarak bir AJAX hizmetine erişebilirsiniz. Bu örnek, [temel Ajax hizmet](basic-ajax-service.md) örneğinde oluşturulur.

Diğer AJAX örneklerinin aksine, bu örnek ASP.NET AJAX ve <xref:System.Web.UI.ScriptManager> denetimini kullanmaz. Bazı ek yapılandırmalar ile, WCF AJAX hizmetlerine JavaScript aracılığıyla herhangi bir HTML sayfasından erişilebilir ve bu senaryo burada gösterilmiştir. WCF 'yi ASP.NET AJAX ile kullanmayla ilgili bir örnek için bkz. [Ajax örnekleri](ajax.md).

Bu örnek, bir işlemin yanıt türünün JSON ve XML arasında nasıl değiştirileceğini gösterir. Bu işlevsellik, hizmetin ASP.NET AJAX tarafından veya bir HTML/JavaScript istemci sayfası tarafından erişilecek şekilde yapılandırılıp yapılandırılmadığına bakılmaksızın kullanılabilir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Non-ASP.NET AJAX istemcilerinin kullanımını etkinleştirmek için <xref:System.ServiceModel.Activation.WebServiceHostFactory> <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> . svc dosyasında (Not) kullanın. <xref:System.ServiceModel.Activation.WebServiceHostFactory><xref:System.ServiceModel.Description.WebHttpEndpoint>hizmete standart bir uç nokta ekler. Uç nokta,. svc dosyasına göre boş bir adreste yapılandırılır; Bu, hizmetin adresinin, `http://localhost/ServiceModelSamples/service.svc` işlem adından farklı ek sonekler olmadan olduğu anlamına gelir.

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>`

Web. config dosyasındaki aşağıdaki bölüm, uç noktada ek yapılandırma değişiklikleri yapmak için kullanılabilir. Ek değişiklik gerekmiyorsa bu, kaldırılabilir.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <!-- Use this element to configure the endpoint -->
      <standardEndpoint name="" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

İçin varsayılan veri biçimi <xref:System.ServiceModel.Description.WebHttpEndpoint> XML 'dir, ancak için varsayılan veri BIÇIMI <xref:System.ServiceModel.Description.WebScriptEndpoint> JSON olur. Daha fazla bilgi için bkz. [ASP.net olmadan WCF AJAX hizmetleri oluşturma](../feature-details/creating-wcf-ajax-services-without-aspnet.md).

Aşağıdaki örnekteki hizmet, iki işlem içeren standart bir WCF hizmetidir. Her iki işlem de, <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> davranışa özgü olan `webHttp` ve JSON/XML veri biçimi anahtarına hiçbir pul bulunmayan ve özniteliklerde gövde stilini gerektirir.

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

İşlemin yanıt biçimi XML olarak belirtilir, bu davranış için varsayılan ayardır [\<webHttp>](../../configure-apps/file-schema/wcf/webhttp.md) . Ancak, yanıt biçimini açıkça belirtmek iyi bir uygulamadır.

Diğer işlem `WebInvokeAttribute` özniteliğini kullanır ve yanıt IÇIN XML yerine AÇıKÇA JSON belirler.

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

Her iki durumda da işlemler `MathResult` Standart BIR WCF veri anlaşması türü olan karmaşık bir tür döndürdüğüne de göz önünde.

XmlAjaxClientPage. htm istemci Web sayfası, Kullanıcı **Hesaplama gerçekleştirme (JSON döndürme)** veya sayfadaki **Hesaplama (dönüş XML)** düğmelerini tıklattığında önceki Iki işlemden birini çağıran JavaScript kodunu içerir. Hizmeti çağırmak için kod bir JSON gövdesi oluşturur ve HTTP POST kullanarak gönderir. İstek, [temel Ajax hizmet](basic-ajax-service.md) örneği ve ASP.NET Ajax kullanan diğer örneklerin aksine, JavaScript 'te el ile oluşturulur.

```csharp
// Create HTTP request
var xmlHttp;
// Request instantiation code omitted…
// Result handler code omitted…

// Build the operation URL
var url = "service.svc/ajaxEndpoint/";
url = url + operation;

// Build the body of the JSON message
var body = '{"n1":';
body = body + document.getElementById("num1").value + ',"n2":';
body = body + document.getElementById("num2").value + '}';

// Send the HTTP request
xmlHttp.open("POST", url, true);
xmlHttp.setRequestHeader("Content-type", "application/json");
xmlHttp.send(body);
```

Hizmet yanıt verdiğinde, yanıt sayfadaki bir metin kutusunda başka işlem yapılmadan görüntülenir. Bu, kullanılan XML ve JSON veri biçimlerini doğrudan gözlemlemeye olanak tanımak için tanıtım amaçlı olarak uygulanır.

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümünde açıklandığı gibi XmlAjaxService. sln çözümünü oluşturun.

3. Öğesine gidin `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (proje dizininden tarayıcıda XmlAjaxClientPage. htm dosyasını açmayın).

## <a name="see-also"></a>Ayrıca bkz.

- [HTTP POST Kullanan AJAX Hizmeti](ajax-service-using-http-post.md)
