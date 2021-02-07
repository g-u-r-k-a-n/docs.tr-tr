---
description: 'Hakkında daha fazla bilgi edinin: <messageSenderAuthentication>'
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: e98388eafce24b0f19647364b6bbec94ee6ba135
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749330"
---
# \<messageSenderAuthentication>

İleti gönderici tarafından kullanılan eş sertifika için kimlik doğrulama ayarlarını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`certificateValidationMode`|İsteğe bağlı sabit listesi. Kimlik bilgilerini doğrulamak için kullanılan beş moddan birini belirtir. Bu öznitelik türü <xref:System.ServiceModel.Security.X509CertificateValidationMode> . Olarak ayarlanırsa `Custom` , bir `customCertificateValidator` de sağlanmalıdır.|  
|`customCertificateValidatorType`|İsteğe bağlı dize. Özel bir türü doğrulamak için kullanılan bir tür ve derlemeyi belirtir. Bu öznitelik `certificateValidationMode` , olarak ayarlandığında ayarlanmalıdır `Custom` . Bu öznitelik türü <xref:System.IdentityModel.Selectors.X509CertificateValidator> . Windows Communication Foundation (WCF), eş sertifikayı güvenilir kişiler deposuna karşı doğrulayan bir varsayılan eş sertifika Doğrulayıcısı sağlar. Ayrıca, sertifikanın geçerli bir köke zincirde olduğunu doğrular. Farklı bir davranış belirtmek için özel bir doğrulayıcı uygulayabilir ve bu özniteliği özel Doğrulayıcısı işaret etmek için kullanabilirsiniz.|  
|`revocationMode`|İsteğe bağlı sabit listesi. Sertifika iptal modunu belirtir. Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> . Sistem, eş sertifikanın iptal edilmiş sertifika listesinde arayarak iptal edilmediğini doğrular. Bu denetim, çevrimiçi ya da önbelleğe alınmış bir iptal listesine karşı yapılabilir. İptal denetimi, bu öznitelik NoCheck olarak ayarlanarak kapatılabilir.|  
|`trustedStoreLocation`|İsteğe bağlı sabit listesi. Eş sertifikanın WCF güvenlik sistemi tarafından doğrulandığı güvenilen depo konumunu belirtir. Bu öznitelik türü <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|Eş düğüm için geçerli kimlik bilgilerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 İleti kimlik doğrulaması seçilirse, bu öğenin yapılandırılması gerekir. Çıkış kanalları için, her ileti tarafından belirtilen sertifika kullanılarak imzalanır [\<certificate>](certificate-element.md) . Uygulamaya teslim edilmeden önce tüm iletiler, bu öğenin özniteliği tarafından belirtilen Doğrulayıcı kullanılarak ileti kimlik bilgisine karşı denetlenir `customCertificateValidatorType` . Doğrulayıcı kimlik bilgisini kabul edebilir veya reddedebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [Sertifikalarla Çalışma](../../../wcf/feature-details/working-with-certificates.md)
- [Eşler Arası Ağ](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Eş kanal Iletisi kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Eş kanal özel kimlik doğrulaması](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Eş Kanalı Uygulamalarını Güvenli Hale Getirme](../../../wcf/feature-details/securing-peer-channel-applications.md)
