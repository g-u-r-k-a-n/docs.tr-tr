---
title: Özel Belirteç İşleyicileri
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
ms.openlocfilehash: ccf794b4c229bbc9b40ae7ec2fd649825122cecf
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040553"
---
# <a name="custom-token-handlers"></a><span data-ttu-id="286cb-102">Özel Belirteç İşleyicileri</span><span class="sxs-lookup"><span data-stu-id="286cb-102">Custom Token Handlers</span></span>
<span data-ttu-id="286cb-103">Bu konuda, WıF 'deki belirteç işleyicileri ve belirteçleri işlemek için nasıl kullanıldıkları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="286cb-103">This topic discusses token handlers in WIF and how they are used to process tokens.</span></span> <span data-ttu-id="286cb-104">Bu konuda, WıF içinde varsayılan olarak desteklenmeyen belirteç türleri için özel belirteç işleyicileri oluşturmak için gerekli olan özellikler de ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="286cb-104">The topic also covers what is necessary to create custom token handlers for token types that are not supported by default in WIF.</span></span>  
  
## <a name="introduction-to-token-handlers-in-wif"></a><span data-ttu-id="286cb-105">WıF içindeki belirteç Işleyicilerine giriş</span><span class="sxs-lookup"><span data-stu-id="286cb-105">Introduction to Token Handlers in WIF</span></span>  
 <span data-ttu-id="286cb-106">WıF, bir bağlı olan taraf (RP) uygulaması veya bir güvenlik belirteci hizmeti (STS) için belirteçleri oluşturmak, okumak, yazmak ve doğrulamak üzere güvenlik belirteci işleyicilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="286cb-106">WIF relies on security token handlers to create, read, write, and validate tokens for a relying party (RP) application or a security token service (STS).</span></span> <span data-ttu-id="286cb-107">Belirteç işleyicileri, WıF ardışık düzeninde özel bir belirteç işleyicisi eklemenize veya var olan bir belirteç işleyicisinin belirteçleri yönetme şeklini özelleştirmenize yönelik genişletilebilirlik noktalarıdır.</span><span class="sxs-lookup"><span data-stu-id="286cb-107">Token handlers are extensibility points for you to add a custom token handler in the WIF pipeline, or to customize the way that an existing token handler manages tokens.</span></span> <span data-ttu-id="286cb-108">WıF, işlevselliği gerektiği şekilde değiştirmek için değiştirilebilen ve tamamen geçersiz kılınabilen dokuz yerleşik güvenlik belirteci işleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="286cb-108">WIF provides nine built-in security token handlers that can be modified or entirely overridden to change the functionality as necessary.</span></span>  
  
## <a name="built-in-security-token-handlers-in-wif"></a><span data-ttu-id="286cb-109">WıF 'de yerleşik güvenlik belirteci Işleyicileri</span><span class="sxs-lookup"><span data-stu-id="286cb-109">Built-In Security Token Handlers in WIF</span></span>  
 <span data-ttu-id="286cb-110">WıF 4,5, soyut temel sınıftan türetilen dokuz güvenlik belirteci işleyici sınıfı içerir <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span><span class="sxs-lookup"><span data-stu-id="286cb-110">WIF 4.5 includes nine security token handler classes that derive from the abstract base class <xref:System.IdentityModel.Tokens.SecurityTokenHandler>:</span></span>  
  
- <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
- <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a><span data-ttu-id="286cb-111">Özel belirteç Işleyicisi ekleme</span><span class="sxs-lookup"><span data-stu-id="286cb-111">Adding a Custom Token Handler</span></span>  
 <span data-ttu-id="286cb-112">Basit Web belirteçleri (SWT) ve JSON Web belirteçleri (JWT) gibi bazı belirteç türlerinde, WıF tarafından sunulan yerleşik belirteç işleyicileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="286cb-112">Some token types, such as Simple Web Tokens (SWT) and JSON Web Tokens (JWT) do not have built-in token handlers provided by WIF.</span></span> <span data-ttu-id="286cb-113">Bu belirteç türleri ve yerleşik işleyicisi olmayan diğerleri için, bir özel belirteç işleyicisi oluşturmak için aşağıdaki adımları gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="286cb-113">For these token types and for others that do not have a built-in handler, you need to perform the following steps to create a custom token handler.</span></span>  
  
#### <a name="adding-a-custom-token-handler"></a><span data-ttu-id="286cb-114">Özel belirteç işleyicisi ekleme</span><span class="sxs-lookup"><span data-stu-id="286cb-114">Adding a custom token handler</span></span>  
  
1. <span data-ttu-id="286cb-115"><xref:System.IdentityModel.Tokens.SecurityTokenHandler>türetilen yeni bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="286cb-115">Create a new class that derives from <xref:System.IdentityModel.Tokens.SecurityTokenHandler>.</span></span>  
  
2. <span data-ttu-id="286cb-116">Aşağıdaki yöntemleri geçersiz kılın ve kendi uygulamanızı sağlayın:</span><span class="sxs-lookup"><span data-stu-id="286cb-116">Override the following methods and provide your own implementation:</span></span>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    - <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3. <span data-ttu-id="286cb-117">*Web. config* veya *app. config* dosyasındaki yeni özel belirteç işleyicisine, WIF için geçerli olan **\<System. IdentityModel >** bölümü içinde bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="286cb-117">Add a reference to the new custom token handler in the *Web.config* or *App.config* file, within the **\<system.identityModel>** section that applies to WIF.</span></span> <span data-ttu-id="286cb-118">Örneğin, aşağıdaki yapılandırma biçimlendirmesi **CustomToken** ad alanında bulunan **MyCustomTokenHandler** adlı yeni bir belirteç işleyicisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="286cb-118">For example, the following configuration markup specifies a new token handler named **MyCustomTokenHandler** that resides in the **CustomToken** namespace.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     <span data-ttu-id="286cb-119">Zaten yerleşik bir belirteç işleyicisine sahip olan bir belirteç türünü işlemek için kendi belirteç işleyicinizi sağlıyorsanız, varsayılan işleyiciyi bırakmak ve bunun yerine özel işleyicinizi kullanmak için bir **\<** öğesi eklemeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="286cb-119">Note that if you are providing your own token handler to handle a token type that already has a built-in token handler, you need to add a **\<remove>** element to drop the default handler and use your custom handler instead.</span></span> <span data-ttu-id="286cb-120">Örneğin, aşağıdaki yapılandırma varsayılan <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> özel belirteç işleyicisiyle değiştirir:</span><span class="sxs-lookup"><span data-stu-id="286cb-120">For example, the following configuration replaces the default <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> with the custom token handler:</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789" />  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
