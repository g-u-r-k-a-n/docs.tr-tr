---
description: 'Daha fazla bilgi edinin: Windows Identity Foundation yapılandırma şeması'
title: Windows Identity Foundation Yapılandırma Şeması
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: 926b2dbe25359ebc789c95f75a59090c7e5a52e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725343"
---
# <a name="windows-identity-foundation-configuration-schema"></a>Windows Identity Foundation Yapılandırma Şeması

Bu bölümdeki konularda, Windows Identity Foundation (WıF) yapılandırma şeması hakkında bilgi sağlanmaktadır. Ayrıca, bir uygulamayı Framework tarafından sunulan sınıfları kullanarak WıF kullanacak şekilde yapılandırabilirsiniz. Bu sınıflar, şemadaki ilgili öğeleri ele alan bölümlerde belirtilmiştir. Aşağıdaki, WıF yapılandırma şeması tarafından sunulan temel XML etiketi yapısını gösterir. Öznitelikler atlanır. Vurgulanan Yorumlar şemanın ana bileşenlerini gösterir.  
  
```xml  
<configuration>  
    <system.identityModel>  
        <!-- Service Configuration -->  
        <identityConfiguration>  
            <caches>  
                <sessionSecurityTokenCache />  
                <tokenReplayCache />  
            </caches>  

            <certificateValidation>  
                <certificateValidator />
            </certificateValidation>  

            <claimsAuthenticationManager />  

            <claimsAuthorizationManager>  
                <optionalConfigurationElement>  
            </claimsAuthorizationManager>  

            <claimTypeRequired>  
                <claimType />
            </claimTypeRequired>  

            <tokenReplayDetection />  

            <!-- Security Token Handler Collection Configuration -->  
            <securityTokenHandlers>  
                <add>  
                    <!-- Can take an optional configuration element which can be one of  
                         the following or a custom element -->  
                    <samlSecurityTokenHandlerRequirement>  
                        <nameClaimType>  
                        <roleClaimType>
                    </samlSecurityTokenHandlerRequirement>  

                    <sessionSecurityTokenHandlerRequirement />  
                    <x509SecurityTokenHandlerRequirement />  
                    <userNameSecurityTokenHandlerRequirement />  
                </add>  
                <clear />  
                <remove />  
                <securityTokenHandlerConfiguration>  
                    <audienceUris>  
                        <add>  
                        <clear>  
                        <remove>  
                    </audienceUris>  

                    <caches>  
                        <sessionSecurityTokenCache />  
                        <tokenReplayCache />  
                    </caches>  

                    <certificateValidation>  
                        <certificateValidator>
                    </certificateValidation>  

                    <issuerNameRegistry>  
                        <!-- Can take an optional configuration element which can be   
                             the <trustedIssuers> element to configure a configuration-based  
                             issuer name registry or can be a custom element -->  
                        <trustedIssuers>  
                            <add>  
                            <clear>  
                            <remove>  
                        </trustedIssuers>  
                    </issuerNameRegistry>  

                    <issuerTokenResolver />  
                    <serviceTokenResolver />  
                    <tokenReplayDetection />  
                </securityTokenHandlerConfiguration>  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  

    <system.identityModel.services>  
        <!-- Federation Authentication Configuration -->  
        <federatedAuthentication>  
            <cookieHandler>  
                <chunkedCookieHandler />  
                <customCookieHandler />  
            </cookieHandler>  

            <serviceCertificate>  
                <certificateReference>  
            </serviceCertificate>  

            <wsFederation />  
        </federatedAuthentication>  
    </system.identityModel.services>  
</configuration>  
```  
  
## <a name="in-this-section"></a>Bu Bölümde  

[\<system.identityModel>](system-identitymodel.md) Uygulamalarda WıF seçeneklerini etkinleştirmek için yapılandırma sağlar.  
  
[\<system.identityModel.services>](system-identitymodel-services.md) WıF kullanarak Pasif Federasyon için yapılandırma sağlar. Oturum kimlik doğrulama modülünü (SAM) ve federal kimlik doğrulama modülünü (WSFAD) yapılandırır.
