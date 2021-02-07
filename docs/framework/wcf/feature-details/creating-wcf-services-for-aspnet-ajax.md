---
description: 'Hakkında daha fazla bilgi edinin: ASP.NET AJAX için WCF Hizmetleri oluşturma'
title: ASP.NET AJAX için WCF Hizmetleri Oluşturma
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: e4ab977db5632de0c9e825e03369506d4917709f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705128"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>ASP.NET AJAX için WCF Hizmetleri Oluşturma

Microsoft ASP.NET AJAX, yanıt veren ve tanıdık kullanıcı arabirimi öğeleriyle zengin bir kullanıcı deneyimi içeren Web sayfalarını hızlı bir şekilde oluşturmanıza olanak sağlar. ASP.NET AJAX, tarayıcılar arası ECMAScript (JavaScript) ve dinamik HTML (DHTML) teknolojilerini birleştiren ve bunları ASP.NET 2,0 sunucu tabanlı geliştirme platformuyla tümleştiren istemci komut dosyası kitaplıkları sağlar. ASP.NET AJAX kullanarak, Web uygulamalarınızın Kullanıcı deneyimini ve verimliliğini geliştirebilirsiniz.

ASP.NET AJAX, istemci-komut dosyası kitaplıklarından ve güçlü bir geliştirme çerçevesi sağlamak üzere tümleştirilmiş sunucu bileşenlerinden oluşur. Bir ASP.NET sayfasından bir hizmete erişmek için: hizmet URL 'SI sayfada ASP.NET betik Yöneticisi denetimine eklendikten sonra, tam olarak normal bir JavaScript işlev çağrısı gibi görünen JavaScript kodu kullanılarak hizmet işlemleri çağrılabilir.

En Windows Communication Foundation (WCF) Hizmetleri, uygun bir ASP.NET AJAX uç noktası eklenerek ASP.NET AJAX ile uyumlu bir hizmet olarak kullanıma sunulabilir.

Visual Studio kullanıyorsanız, ASP.NET Web siteleri veya Web uygulamaları ile çalışırken **Yeni öğe Ekle** iletişim kutusunda bulunan AJAX etkinleştirilmiş WCF Hizmetleri için önceden oluşturulmuş bir şablon kullanabilirsiniz.

Visual Studio şablonlarını kullanmıyorsanız, ASP.NET AJAX uç noktası oluşturmanın iki yolu vardır:

- Herhangi bir yapılandırma kullanmadan dinamik ana bilgisayar etkinleştirmesini kullanarak uç nokta oluşturun. Bu, WCF yapılandırma sistemini tanımıyorsanız en temel yaklaşımdır. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma kullanmadan ASP.NET AJAX uç noktası ekleme](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).

- Yapılandırma kullanarak bir WCF hizmetine AJAX özellikli bir uç nokta ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET AJAX uç noktası eklemek Için yapılandırma kullanma](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).

[WCF Web http programlama modeli genel bakış](wcf-web-http-programming-model-overview.md) bölümünde açıklanan Web programlama modeli, ASP.NET AJAX hizmetleriyle birlikte kullanılabilir. Özellikle:

- <xref:System.ServiceModel.Web.WebGetAttribute>Ve <xref:System.ServiceModel.Web.WebInvokeAttribute> ÖZNITELIKLERINI kullanarak http get ve http post fiilleri arasından seçim yapabilirsiniz. Doğru şekilde kullanılırsa, bu, uygulamanızın performansını önemli ölçüde iyileştirebilecek. Daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET AJAX uç noktaları IÇIN http post ve http get istekleri arasında seçim yapma](http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).

- <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A>Ve <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> özelliklerini, hizmetinizin varsayılan JAVASCRIPT nesne GÖSTERIMI (JSON) yerine XML verisi döndürmesini sağlamak için kullanabilirsiniz. Bunu ASP.NET AJAX çerçevesiyle yapmak, JavaScript istemcisinin bir XML DOM nesnesi almasına neden olur.

  > [!WARNING]
  > Bu işlemin çalışması için işlem, içerik türünü Text/XML olarak ayarlamış olmalıdır. Aksi halde, JavaScript istemcisi XML DOM nesnesi yerine XML içeren bir dize alır.

    Aşağıda, içerik türü uygun şekilde ayarlanmış XML verileri döndüren bir işlem örneği verilmiştir:

  ```csharp
  [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]
  public XElement GetData()
  {
      XElement x;
      //Get some data here...

      WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";
      return x;
  }
  ```

- <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> ASP.NET AJAX ile uyumluluk gerekliyse, ve özniteliklerinde başka hiçbir özellik değiştirilemez. ASP.NET AJAX çağırma kuralları ihlal olmadığı sürece web programlama modelinin diğer yönleri de kullanılabilir.

 Daha gelişmiş senaryolar, WCF 'de AJAX desteğinin bazı ek ayrıntılarının anlaşılması gerekir:

- JavaScript kullanılarak verilerin AJAX sayfa istemcisi ile WCF hizmeti arasında nasıl aktarılacağını anlamak ve .NET Framework türlerin JavaScript türleriyle nasıl eşlendikleri hakkında ayrıntılar için bkz. [JSON ve diğer veri aktarımı biçimleri Için destek](support-for-json-and-other-data-transfer-formats.md).

- ASP.NET özelliklerinden yararlanmak için, örneğin, URL tabanlı kimlik doğrulaması ve ASP.NET oturum bilgisine erişme, yapılandırma yoluyla ASP.NET uyumluluk modunu etkinleştirmek isteyebilirsiniz.

WCF 'deki AJAX uç noktaları, ASP.NET AJAX Framework olmadan da tüketilebilir. Bunun yapılması, WCF 'de AJAX desteğinin destek mimarisinin anlaşılmasını gerektirir. Bu mimarinin bir açıklaması için bkz. [WCF Web http programlama nesne modeli](wcf-web-http-programming-object-model.md). Bu yaklaşımı gösteren bir kod örneği için bkz. [JSON ve XML Ile AJAX Hizmeti](../samples/ajax-service-with-json-and-xml-sample.md).

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](wcf-web-http-programming-model.md)
- [Nasıl yapılır: Yapılandırma Kullanmadan ASP.NET AJAX Uç Noktası Ekleme](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)
- [Nasıl yapılır: ASP.NET AJAX Uç Noktası Eklemek için Yapılandırma Kullanma](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
- [Nasıl yapılır: ASP.NET AJAX Uç Noktaları için HTTP POST ve HTTP GET İstekleri Arasında Seçim Yapma](http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
