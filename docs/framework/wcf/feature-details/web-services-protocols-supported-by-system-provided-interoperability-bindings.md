---
description: 'Hakkında daha fazla bilgi edinin: System-Provided birlikte çalışabilirlik bağlamaları tarafından desteklenen Web Hizmetleri protokolleri'
title: Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: a970cdffe864861f4b6f0163d21a69648c777726
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704361"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Sistem Tarafından Sağlanan Birlikte Kullanılabilirlik Bağlamaları ile Desteklenen Web Hizmeti Protokolleri

Windows Communication Foundation (WCF), Web Hizmetleri belirtimleri olarak bilinen bir belirtim kümesini destekleyen Web Hizmetleri ile birlikte çalışmak için oluşturulmuştur. WCF, birlikte çalışabilirlik en iyi uygulamaları için hizmet yapılandırmasını basitleştirmek amacıyla, birlikte çalışabilen üç sistem tarafından sunulan bağlama sağlar: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> , <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> ve <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> . Yapılandırılmış bilgi standartları (OASU) standartlarına karşı bir kuruluşla birlikte çalışabilirlik için, WCF, birlikte çalışabilen bir sistem tarafından sağlanmış bağlama içerir: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType> . WCF, meta veri yayını için iki birlikte çalışabilen ve sistem tarafından belirtilen bağlamaları içerir: [\<mexHttpBinding>](../../configure-apps/file-schema/wcf/mexhttpbinding.md) ve [\<mexHttpsBinding>](../../configure-apps/file-schema/wcf/mexhttpsbinding.md) . Bu konuda, sistem tarafından sunulan birlikte çalışabilen bağlamaların desteklediği özellikler listelenmiştir.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>BasicHttpBinding, wsHttpBinding, ws2007HttpBinding ve wsDualHttpBinding bağlamaları tarafından desteklenen Web Hizmetleri protokolleri  
  
### <a name="all-bindings"></a>Tüm bağlamalar  

 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md), [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) , Ve [\<ws2007HttpBinding>](../../configure-apps/file-schema/wcf/ws2007httpbinding.md) bağlamaları aşağıdaki protokolleri destekler.  
  
> [!NOTE]
> Meta verileri yayımlamak için kullanılan bağlamalar hakkında daha fazla bilgi için, bu konunun devamındaki "sistem tarafından sunulan meta veri bağlamaları" bölümüne bakın.  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|Aktarım|HTTP 1,1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> `BasicHttpBinding`, `WSHttpBinding` ve `WS2007HttpBinding` http ve https aktarımlarını kullanın.|  
|Mesajlaşma|MTOM|[MTOM](https://www.w3.org/TR/soap12-mtom/)<br /><br /> `basicHttpBinding`, `wsHttpBinding` ve `ws2007HttpBinding` destek Ileti Iletimi iyileştirme MEKANIZMASı (MTOM). Varsayılan olarak kullanılmaz. MTOM 'yi kullanmak için `messageEncoding` özniteliğini olarak ayarlayın `"Mtom"` .<br /><br /> Örnek:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Meta veri|WSDL 1,1|[WSDL 1,1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF, hizmetleri anlatmak için Web Hizmetleri Açıklama Dili (WSDL) kullanır.|  
|Meta veri|WS-Policy|[WS Ilkesi](https://www.w3.org/Submission/WS-Policy/)<br /><br /> WCF, hizmet gereksinimlerini ve yeteneklerini anlatmak için WS-Policy belirtimini, etki alanına özgü onaylarla birlikte kullanır.|  
|Meta veri|WS-Policy 1,5|[WS-Policy 1,5](https://www.w3.org/TR/2007/CR-ws-policy-20070605/)<br /><br /> WCF, hizmet gereksinimlerini ve yeteneklerini anlatmak için WS-Policy belirtimini, etki alanına özgü onaylarla birlikte kullanır.|  
|Meta veri|WS-PolicyAttachment|[WS-PolicyAttachment](http://specs.xmlsoap.org/ws/2004/09/policy/ws-policyattachment.pdf)<br /><br /> WCF, Web Hizmetleri Açıklama Dili (WSDL) içindeki çeşitli kapsamlara ilke ifadeleri eklemek için WS-PolicyAttachment uygular.|  
|Meta veri|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF, XML şeması, WSDL ve WS Ilkesini almak için WS-MetadataExchange uygular.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|Mesajlaşma|SOAP 1,1|[SOAP 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)<br /><br /> Temel profil 1,1 ' ye uygun olarak, `basicHttpBinding` Öğesı SOAP 1,1 ileti protokolünü uygular.|  
|Güvenlik|WSS SOAP Iletisi güvenliği 1,0|[WSS SOAP Iletisi güvenliği 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Temel güvenlik profiline uygun olarak `basicHttpBinding` öğesi, Kullanıcı adı/parola ve X. 509.440 tabanlı güvenlik için Web Hizmetleri güvenliği (WSS) soap Iletisi güvenlik 1,0 belirtimini uygular.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği UsernameToken profili 1,0|[WSS SOAP Iletisi güvenliği UsernameToken profili 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği X. 509.440 sertifika belirteci profili 1,0|[WSS SOAP Iletisi güvenliği X. 509.440 sertifika belirteci profili 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding ve wsDualHttpBinding  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|Mesajlaşma|SOAP 1,2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Mesajlaşma çerçevesi](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (HTTP bağlama dahil)](https://www.w3.org/TR/soap12-part2/)|  
|Mesajlaşma|WS-Addressing 2005/08|[Web Hizmetleri adresleme 1,0-çekirdek](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Hizmetleri adresleme 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)<br /><br /> , `wsHttpBinding` `ws2007HttpBinding` Ve `wsDualHttpBinding` zaman uyumsuz mesajlaşma, ileti bağıntısı ve taşıma için nötr adresleme mekanizmalarını etkinleştirmek üzere World Wide Web Konsorsiyumu (W3C) WS-Addressing önerisi uygulayın.<br /><br /> WCF, bu, WS-* belirtimleri tarafından izin verilse de WS-Addressing üstbilgilerinin şifrelenmesini desteklemez.|  
|Mesajlaşma|WS-Addressing 1,0-meta veriler|[Ws-Addressing 1,0 meta verileri](https://www.w3.org/2007/05/addressing/metadata/) ServiceMetadata davranışındaki ilke sürümü ayarlanarak ve PolicyVersion, 1,2 (varsayılan) olarak ayarlandığında, WSDL WS-Addressing açıklaması, PolicyVersion ayarı 1,5 olarak ayarlandığında, WSDL açıklaması, ws-Addressing meta verileri ile uyumlu olduğundan bu protokol için destek etkinleştirilir.<br /><br /> WCF, bu, WS-* belirtimleri tarafından izin verilse de WS-Addressing üstbilgilerinin şifrelenmesini desteklemez.|  
|Güvenlik|WSS SOAP Iletisi güvenliği 1,0|[WSS SOAP Iletisi güvenliği 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> `securityMode`Özniteliği "wsSecurityOverHttp" (varsayılan) olarak ayarlandığında ve parametreler bir alt öğe kullanılarak yapılandırıldığında kullanın `wsSecurity` .<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği UsernameToken profili 1,1|[WSS SOAP Iletisi güvenliği UsernameToken profili 1,0](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> `wsSecurity`Öğenin `authenticationMode` özniteliği "username" olarak ayarlandığında kullanın.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği X. 509.440 sertifika belirteci profili 1,1|[WSS SOAP Iletisi güvenliği X. 509.440 sertifika belirteci profili 1,1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)<br /><br /> `wsSecurity`Öğenin `authenticationMode` özniteliği "Kullanıcı adı", "sertifika" veya "hiçbiri" olarak ayarlandığında ileti koruması için kullanın. Ayrıca, `wsSecurity` öğenin `authenticationMode` özniteliği "sertifika" olarak ayarlandığında istemci kimlik doğrulaması için bunu kullanın.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Güvenlik|WSS SOAP Iletisi güvenliği Kerberos belirteç profili 1,1|[WSS SOAP Iletisi güvenliği Kerberos belirteç profili 1,1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)<br /><br /> `wsSecurity`Öğenin `authenticationMode` özniteliği "Windows" olarak ayarlandığında kimlik doğrulama ve ileti koruması için kullanın.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Güvenlik|WS-SecureConversation|[WS-SecureConversation](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> `security/@mode`Özniteliği "Message" olarak ayarlandığında ve `message/@establishSecurityContext` özniteliği "true" (varsayılan) olarak ayarlandığında güvenli bir oturum sağlamak için kullanın.|  
|Güvenlik|WS-Trust|[WS-Trust](http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf)<br /><br /> WS-SecureConversation tarafından kullanılır (yukarıya bakın).|  
|Güvenilir Mesajlaşma|WS-ReliableMessaging|[WS-ReliableMessaging](http://specs.xmlsoap.org/ws/2005/02/rm/ws-reliablemessaging.pdf)<br /><br /> Bağlama kullanılmak üzere yapılandırıldığında kullanın `reliableSession` .<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|İşlemler|WS-AtomicTransaction|[WS-AtomicTransaction](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)<br /><br /> İşlem yöneticileri arasındaki iletişim için kullanın. WCF istemcileri ve hizmetleri her zaman yerel işlem yöneticilerini kullanır.|  
|İşlemler|WS-Coordination|[WS koordinasyonu](/previous-versions/ms951231(v=msdn.10))<br /><br /> `flowTransactions`Öznitelik "Allowed" veya "Required" olarak ayarlandığında işlem bağlamını akışa almak için kullanın.<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding ve ws2007FederationHttpBinding  

 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)Ve [\<ws2007FederationHttpBinding>](../../configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) öğeleri, üçüncü bir tarafın bir istemcinin kimliğini doğrulamak için kullanılan bir belirteç verdiği federe senaryolar için destek sağlamak üzere sunulmuştur. Tarafından kullanılan protokollerin yanı sıra, şunları `wsHttpBinding` `wsFederationHttpBinding` kullanır:  
  
- `WS-Trust` belirteç verme için.  
  
- En yaygın olarak verilen belirteç biçimi için WSS güvenlik onayları biçimlendirme dili (SAML) belirteç profili 1,0 ve 1,1.  
  
 Örnek:  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'/>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 Daha fazla bilgi için bkz. [Federasyon](federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>System-Provided meta veri bağlamaları  

 Aşağıdaki tablolarda, sınıfı tarafından sunulan, sistem tarafından sunulan birlikte çalışabilen meta veri bağlamaları tarafından desteklenen protokoller açıklanır <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> .  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  

 [\<mexHttpBinding>](../../configure-apps/file-schema/wcf/mexhttpbinding.md)Bağlama, aşağıdaki protokolleri destekler. Bu bağlamayı kullanma hakkında daha fazla bilgi için bkz. [meta verileri yayımlama](publishing-metadata.md).  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|Aktarım|HTTP 1,1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)|  
|Mesajlaşma|SOAP 1,2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Mesajlaşma çerçevesi](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (HTTP bağlama dahil)](https://www.w3.org/TR/soap12-part2/)|  
|Mesajlaşma|WS-Addressing 2005/08|[Web Hizmetleri adresleme 1,0-çekirdek](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Hizmetleri adresleme 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Meta veri|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF, XML şeması, WSDL ve WS Ilkesini almak için WS-MetadataExchange uygular.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  

 [\<mexHttpsBinding>](../../configure-apps/file-schema/wcf/mexhttpsbinding.md) aşağıdaki protokolleri destekler. Bu bağlamayı kullanma hakkında daha fazla bilgi için bkz. [meta verileri yayımlama](publishing-metadata.md).  
  
|Kategori|Protokol|Belirtim ve kullanım|  
|--------------|--------------|-----------------------------|  
|Aktarım|HTTP 1,1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> Taşıma güvenliği etkin.|  
|Mesajlaşma|SOAP 1,2|[Primer](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Mesajlaşma çerçevesi](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (HTTP bağlama dahil)](https://www.w3.org/TR/soap12-part2/)|  
|Mesajlaşma|WS-Addressing 2005/08|[Web Hizmetleri adresleme 1,0-çekirdek](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Web Hizmetleri adresleme 1,0-SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Meta veri|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF, XML şeması, WSDL ve WS Ilkesini almak için WS-MetadataExchange uygular.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Tarafından Sağlanan Bağlamalar](../system-provided-bindings.md)
- [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding>](../../configure-apps/file-schema/wcf/mexhttpbinding.md)
