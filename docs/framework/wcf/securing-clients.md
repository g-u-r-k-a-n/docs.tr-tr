---
title: İstemcileri Güvenli Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: b7f720b83a858c8739d2f7b9bf63d29c54b914e0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242259"
---
# <a name="securing-clients"></a>İstemcileri Güvenli Hale Getirme

Windows Communication Foundation (WCF) ' de, hizmet istemcilerin güvenlik gereksinimlerini belirler. Diğer bir deyişle, hizmet kullanılacak güvenlik modunu ve istemcinin bir kimlik bilgisi sağlayıp sağlamamayacağını belirtir. Bu nedenle, bir istemciyi güvenli hale getirme işlemi basittir: hizmetten alınan meta verileri (yayımlandıysa) kullanın ve bir istemci oluşturun. Meta veriler, istemcinin nasıl yapılandırılacağını belirtir. Hizmet istemcinin kimlik bilgilerini vermesini gerektiriyorsa, gereksinime uygun bir kimlik bilgisi edinmeniz gerekir. Bu konu, işlemi daha ayrıntılı bir şekilde ele alır. Güvenli hizmet oluşturma hakkında daha fazla bilgi için bkz. [hizmetleri güvenli hale getirme](securing-services.md).  
  
## <a name="the-service-specifies-security"></a>Hizmet güvenliği belirtir  

 Varsayılan olarak, WCF bağlamaları güvenlik özellikleri etkinleştirilmiştir. (Özel durum <xref:System.ServiceModel.BasicHttpBinding> .) Bu nedenle, hizmet WCF kullanılarak oluşturulduysa kimlik doğrulama, gizlilik ve bütünlüğü sağlamak için güvenlik uygulayacağız. Bu durumda, hizmetin sağladığı meta veriler, güvenli bir iletişim kanalı kurmak için ne gerektirdiğini gösterir. Hizmet meta verileri herhangi bir güvenlik gereksinimi içermiyorsa, bir hizmette HTTP üzerinden Güvenli Yuva Katmanı (SSL) gibi bir güvenlik düzeni getirmenin bir yolu yoktur. Ancak, hizmet istemcinin bir kimlik bilgisi vermesini gerektiriyorsa, istemci geliştiricisi, dağıtıcı veya yönetici istemcinin hizmete kendi kimliğini doğrulamak için kullanacağı gerçek kimlik bilgisini sağlamalıdır.  
  
## <a name="obtaining-metadata"></a>Meta verileri alma  

 İstemci oluştururken, ilk adım istemcinin iletişim kurduğu hizmetin meta verilerini elde etmek olacaktır. Bu, iki şekilde yapılabilir. İlk olarak, hizmet bir meta veri değişimi (MEX) uç noktası yayımladığında veya meta verilerini HTTP ya da HTTPS üzerinden kullanılabilir hale yapıyorsa, meta verileri [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)kullanarak indirebilir, bu da bir istemci için hem kod dosyaları hem de bir yapılandırma dosyası oluşturur. (Aracı kullanma hakkında daha fazla bilgi için bkz. [WCF Istemcisi kullanarak hizmetlere erişme](accessing-services-using-a-wcf-client.md).) Hizmet bir MEX uç noktası yayımlamaz ve meta verilerini HTTP ya da HTTPS üzerinden kullanılabilir hale yapmadığından, güvenlik gereksinimlerini ve meta verileri açıklayan belgeler için hizmet oluşturucuya başvurmanız gerekir.  
  
> [!IMPORTANT]
> Meta verilerin güvenilir bir kaynaktan gelmesi ve üzerinde oynanmamasını öneririz. HTTP protokolü kullanılarak alınan meta veriler şifresiz metin olarak gönderilir ve üzerinde oynanmış olabilir. Hizmet <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> özelliklerini KULLANıYORSA, https protokolünü kullanarak verileri indirmek için sağlanan HIZMET Oluşturucu URL 'sini kullanın.  
  
## <a name="validating-security"></a>Güvenlik doğrulanıyor  

 Meta veri kaynakları iki geniş kategoriye ayrılabilir: güven kaynakları ve güvenilir olmayan kaynaklar. Bir kaynağa güveniyorsanız ve bu kaynağın güvenli MEX uç noktasından istemci kodunu ve diğer meta verileri indirdiyseniz, istemciyi oluşturabilir, doğru kimlik bilgileriyle sağlayabilir ve bunu başka bir kaygısız çalıştırabilirsiniz.  
  
 Ancak, daha az bilgi sahibi olduğunuz bir kaynaktan bir istemciyi ve meta verileri indirmeyi tercih ederseniz, kodun kullandığı güvenlik ölçümlerini doğrulamaya dikkat edin. Örneğin, hizmet gizlilik ve bütünlük (en azından) talep etmediği takdirde bir hizmete kişisel veya finansal bilgilerinizi gönderen bir istemci oluşturmanız gerekir. Bu tür bilgiler kendileri tarafından görülebilmesi için hizmetin sahibine bu tür bilgileri açıklamasını istediğiniz ölçüde güvenmelisiniz.  
  
 Kural olarak, bu nedenle, güvenilmeyen bir kaynaktan kod ve meta verileri kullanırken, gereken güvenlik düzeyini karşıladığından emin olmak için kodu ve meta verileri denetleyin.  
  
## <a name="setting-a-client-credential"></a>Istemci kimlik bilgilerini ayarlama  

 İstemcide istemci kimlik bilgisinin ayarlanması iki adımdan oluşur:  
  
1. Hizmetin gerektirdiği *istemci kimlik bilgisi türünü* saptayın. Bu, iki yöntemden biri tarafından gerçekleştirilir. İlk olarak, Service Creator 'tan belgeleriniz varsa, hizmetin gerektirdiği istemci kimlik bilgisi türünü (varsa) belirtmelidir. İkincisi, Svcutil.exe aracı tarafından yalnızca bir yapılandırma dosyanız varsa, hangi kimlik bilgisi türünün gerekli olduğunu belirlemek için bireysel bağlamaları inceleyebilirsiniz.  
  
2. Gerçek istemci kimlik bilgilerini belirtin. Gerçek istemci kimlik bilgisine, türü ayırt etmek için *istemci kimlik bilgileri değeri* denir. Örneğin, istemci kimlik bilgileri türü bir sertifika belirtiyorsa, hizmet güvenlerini bir sertifika yetkilisi tarafından verilen bir X. 509.440 sertifikası sağlamanız gerekir.  
  
### <a name="determining-the-client-credential-type"></a>Istemci kimlik bilgisi türünü belirleme  

 Svcutil.exe aracı tarafından oluşturulan yapılandırma dosyasına sahipseniz, [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) hangi istemci kimlik bilgisi türünün gerekli olduğunu belirlemek için bölümünü inceleyin. Bölümünün içinde güvenlik gereksinimlerini belirten bağlama öğeleri bulunur. Özellikle, \<security> her bağlamanın öğesini inceleyin. Bu öğe, `mode` üç olası değerden ( `Message` , `Transport` , veya) birine ayarlayabileceğiniz özniteliği içerir `TransportWithMessageCredential` . Özniteliğin değeri modu belirler ve mod alt öğelerin hangisinin önemli olduğunu belirler.  
  
 Öğesi ya ya da öğesi ya da `<security>` `<transport>` `<message>` her ikisini birden içerebilir. Önemli öğesi, güvenlik moduyla eşleşen bir öğedir. Örneğin, aşağıdaki kod, güvenlik modunun olduğunu `"Message"` ve öğesi için istemci kimlik bilgisi türünü belirtir `<message>` `"Certificate"` . Bu durumda, `<transport>` öğesi yoksayılabilir. Ancak, `<message>` öğesi bir X. 509.440 sertifikasının sağlanması gerektiğini belirtir.  

```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"
                      realm="" />  
           <message clientCredentialType="Certificate"
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  

 `clientCredentialType`Özniteliği, `"Windows"` Aşağıdaki örnekte gösterildiği gibi, olarak ayarlandıysa, gerçek bir kimlik bilgisi değeri sağlamanız gerekmediğini unutmayın. Bunun nedeni, Windows tümleşik güvenliği 'nin istemcisini çalıştıran kişinin gerçek kimlik bilgisini (Kerberos belirteci) sunmakta olması.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>Istemci kimlik bilgisi değerini ayarlama  

 İstemcinin bir kimlik bilgisi sağlaması gerektiğini tespit ediyorsanız, istemcisini yapılandırmak için uygun yöntemi kullanın. Örneğin, bir istemci sertifikası ayarlamak için <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemini kullanın.  
  
 Ortak bir kimlik bilgisi biçimi X. 509.440 sertifikasıdır. Kimlik bilgisini iki şekilde sağlayabilirsiniz:  
  
- İstemci kodunuzda programlama yoluyla ( `SetCertificate` yöntemini kullanarak).  
  
 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)İstemci için yapılandırma dosyasının bir bölümünü ekleyerek ve `clientCredentials` öğesini kullanarak (aşağıda gösterilmiştir).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Kodda bir \<clientCredentials> değer ayarlama  

 Kodda bir değer ayarlamak için [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) , <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> sınıfının özelliğine erişmeniz gerekir <xref:System.ServiceModel.ClientBase%601> . Özelliği, <xref:System.ServiceModel.Description.ClientCredentials> Aşağıdaki tabloda gösterildiği gibi çeşitli kimlik bilgileri türlerine erişime izin veren bir nesne döndürür.  
  
|ClientCredential özelliği|Açıklama|Notlar|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Şunu döndürür <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|İstemci tarafından hizmette kimlik doğrulaması yapmak için sunulan bir X. 509.440 sertifikasını temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Şunu döndürür <xref:System.ServiceModel.Security.HttpDigestClientCredential>|Bir HTTP Digest kimlik bilgisini temsil eder. Kimlik bilgisi, Kullanıcı adı ve parolasının bir karmasıdır.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Şunu döndürür <xref:System.ServiceModel.Security.IssuedTokenClientCredential>|Federasyon senaryolarında yaygın olarak kullanılan bir güvenlik belirteci hizmeti tarafından verilen özel bir güvenlik belirtecini temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Şunu döndürür <xref:System.ServiceModel.Security.PeerCredential>|Windows etki alanındaki bir eş ağ üzerinde katılım için eş kimlik bilgisini temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Şunu döndürür <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|Bant dışı bir anlaşmede hizmet tarafından sağlanan X. 509.952 sertifikasını temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Şunu döndürür <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|Bir Kullanıcı adı ve parola çiftini temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Şunu döndürür <xref:System.ServiceModel.Security.WindowsClientCredential>|Bir Windows istemci kimlik bilgisini (Kerberos kimlik bilgisi) temsil eder. Sınıfının özellikleri salt okunurdur.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Yapılandırmada bir \<clientCredentials> değer ayarlama  

 Kimlik bilgisi değerleri, öğesinin alt öğeleri olarak bir uç nokta davranışı kullanılarak belirtilir [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) . Kullanılan öğe, istemci kimlik bilgisi türüne bağlıdır. Örneğin, aşağıdaki örnek, <kullanarak bir X. 509.440 sertifikası ayarlamak için yapılandırmayı gösterir [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) .  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
 Yapılandırmada istemci kimlik bilgilerini ayarlamak için [\<endpointBehaviors>](../configure-apps/file-schema/wcf/endpointbehaviors.md) yapılandırma dosyasına bir öğe ekleyin. Ayrıca, aşağıdaki örnekte gösterildiği gibi, eklenen davranış öğesi, `behaviorConfiguration` öğesinin özniteliği [ \<endpoint> \<client> ](../configure-apps/file-schema/wcf/endpoint-of-client.md) kullanılarak hizmetin uç noktasına bağlanmalıdır. Özniteliğin değeri, `behaviorConfiguration` davranış özniteliğinin değeriyle eşleşmelidir `name` .  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
> Bazı istemci kimlik bilgileri değerleri, uygulama yapılandırma dosyaları (örneğin, Kullanıcı adı ve parola) veya Windows Kullanıcı ve parola değerleri kullanılarak ayarlanamaz. Bu kimlik bilgisi değerleri yalnızca kodda belirtilebilir.  
  
 İstemci kimlik bilgisini ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Istemci kimlik bilgisi değerlerini belirtme](how-to-specify-client-credential-values.md).  
  
> [!NOTE]
> `ClientCredentialType``SecurityMode`, `"TransportWithMessageCredential",` Aşağıdaki örnek yapılandırmada gösterildiği gibi olarak ayarlandığında yoksayılır.  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"
               establishSecurityContext="false"
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)
- [Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)
- [Hizmetleri Güvenli Hale Getirme](securing-services.md)
- [WCF İstemcisi Kullanarak Hizmetlere Erişme](accessing-services-using-a-wcf-client.md)
- [Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme](how-to-specify-client-credential-values.md)
- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme](how-to-specify-the-client-credential-type.md)
