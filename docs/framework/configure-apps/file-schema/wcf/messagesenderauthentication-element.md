---
description: 'Daha fazla bilgi edinin: <messageSenderAuthentication> öğesi'
title: <messageSenderAuthentication> öğesi
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 03c1cd626e7c3ad71026c076df3d757419810d74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749343"
---
# <a name="messagesenderauthentication-element"></a>\<messageSenderAuthentication> öğesi

Eşler arası ileti gönderenler için kimlik doğrulama seçeneklerini belirtir.  
  
 Eşler arası programlama hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](../../../wcf/feature-details/peer-to-peer-networking.md).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`customCertificateValidatorType`|Özel bir türü doğrulamak için kullanılan tür ve derleme. Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` .|  
|`certificateValidationMode`|Kimlik bilgilerini doğrulamak için kullanılan üç moddan birini belirtir. Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır.|  
|`revocationMode`|İptal edilen bir sertifika listesini (CRL) denetlemek için kullanılan modlardan biri.|  
|`trustedStoreLocation`|İki sistem depolama konumlarından biri: `LocalMachine` veya `CurrentUser` . Bu değer, bir hizmet sertifikası istemciye anlaşılırken kullanılır. Doğrulama, belirtilen depo konumundaki **güvenilir kişiler** deposuna göre gerçekleştirilir.|  
  
## <a name="customcertificatevalidatortype-attribute"></a>Customcercertificate Atevalidatortype özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|İsteğe bağlı. Türü bulmak için kullanılan tür adını ve derlemeyi ve diğer verileri belirtir. En azından, bir ad alanı ve tür adı gereklidir. İsteğe bağlı bilgiler şunları içerir: derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci.|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|İsteğe bağlı. Aşağıdaki değerlerden biri: `None` ,,, `PeerTrust` `ChainTrust` `PeerOrChainTrust` , `Custom` . Varsayılan değer: `ChainTrust`. Varsayılan değer: `ChainTrust`.<br /><br /> Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="revocationmode-attribute"></a>revocationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Aşağıdaki değerlerden biri: `NoCheck` , `Online` , `Offline` . Varsayılan değer: `Online`.<br /><br /> Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Sabit Listesi|Şu değerlerden biri: `LocalMachine` veya `CurrentUser` . Varsayılan değer: `CurrentUser`. İstemci uygulaması bir sistem hesabı altında çalışıyorsa, sertifika genellikle altında olur `LocalMachine` . İstemci uygulaması bir kullanıcı hesabı altında çalışıyorsa, sertifika genellikle içinde olur `CurrentUser` . Varsayılan değer: `CurrentUser`.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|İstemcinin kimliğini bir eş hizmette doğrulamak için kullanılan kimlik bilgisini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 İleti kimlik doğrulaması seçilirse, bu öğenin yapılandırılması gerekir. Çıkış kanalları için, her ileti tarafından belirtilen sertifika kullanılarak imzalanır [\<certificate>](certificate-element.md) . Uygulamaya teslim edilmeden önce tüm iletiler, bu öğenin özniteliği tarafından belirtilen Doğrulayıcı kullanılarak ileti kimlik bilgisine karşı denetlenir `customCertificateValidatorType` . Doğrulayıcı kimlik bilgisini kabul edebilir veya reddedebilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod ileti gönderici doğrulama modunu olarak ayarlar `PeerOrChainTrust` .  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
- [Eşler Arası Ağ](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../wcf/feature-details/securing-peer-channel-applications.md)
