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
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="d368d-103">Windows Identity Foundation Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="d368d-103">Windows Identity Foundation Configuration Schema</span></span>

<span data-ttu-id="d368d-104">Bu bölümdeki konularda, Windows Identity Foundation (WıF) yapılandırma şeması hakkında bilgi sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d368d-104">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="d368d-105">Ayrıca, bir uygulamayı Framework tarafından sunulan sınıfları kullanarak WıF kullanacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d368d-105">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="d368d-106">Bu sınıflar, şemadaki ilgili öğeleri ele alan bölümlerde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d368d-106">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="d368d-107">Aşağıdaki, WıF yapılandırma şeması tarafından sunulan temel XML etiketi yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d368d-107">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="d368d-108">Öznitelikler atlanır.</span><span class="sxs-lookup"><span data-stu-id="d368d-108">Attributes are omitted.</span></span> <span data-ttu-id="d368d-109">Vurgulanan Yorumlar şemanın ana bileşenlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d368d-109">Highlighted comments indicate major components of the schema.</span></span>  
  
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
  
## <a name="in-this-section"></a><span data-ttu-id="d368d-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d368d-110">In This Section</span></span>  

<span data-ttu-id="d368d-111">[\<system.identityModel>](system-identitymodel.md) Uygulamalarda WıF seçeneklerini etkinleştirmek için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="d368d-111">[\<system.identityModel>](system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
<span data-ttu-id="d368d-112">[\<system.identityModel.services>](system-identitymodel-services.md) WıF kullanarak Pasif Federasyon için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="d368d-112">[\<system.identityModel.services>](system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="d368d-113">Oturum kimlik doğrulama modülünü (SAM) ve federal kimlik doğrulama modülünü (WSFAD) yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d368d-113">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
