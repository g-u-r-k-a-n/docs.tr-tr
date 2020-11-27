---
title: SAML Belirteç Sağlayıcı
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: 97c3c89a94882000c529bae77f1a4d707b242d7e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262664"
---
# <a name="saml-token-provider"></a><span data-ttu-id="a0187-102">SAML Belirteç Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="a0187-102">SAML Token Provider</span></span>

<span data-ttu-id="a0187-103">Bu örnek, özel bir istemci SAML belirteci sağlayıcısının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0187-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="a0187-104">Güvenlik altyapısına kimlik bilgileri sağlamak için Windows Communication Foundation (WCF) içindeki bir belirteç sağlayıcısı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0187-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="a0187-105">Genel içindeki belirteç sağlayıcısı hedefi inceler ve güvenlik altyapısının iletiyi güvenli hale getirmek için uygun kimlik bilgilerini verir.</span><span class="sxs-lookup"><span data-stu-id="a0187-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="a0187-106">WCF varsayılan kimlik bilgileri Yöneticisi belirteç sağlayıcısıyla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="a0187-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="a0187-107">WCF Ayrıca bir CardSpace belirteç sağlayıcısıyla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="a0187-107">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="a0187-108">Özel belirteç sağlayıcıları aşağıdaki durumlarda faydalıdır:</span><span class="sxs-lookup"><span data-stu-id="a0187-108">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="a0187-109">Bu belirteç sağlayıcılarının ile çalışamadığınız bir kimlik bilgisi depoluğiniz varsa.</span><span class="sxs-lookup"><span data-stu-id="a0187-109">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="a0187-110">Kullanıcı, WCF istemci çerçevesi kimlik bilgilerini kullandığında, kimlik bilgilerini bir noktadan dönüştürmek için kendi özel mekanizmanızı sağlamak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="a0187-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="a0187-111">Özel bir belirteç oluşturuyorsanız.</span><span class="sxs-lookup"><span data-stu-id="a0187-111">If you are building a custom token.</span></span>

 <span data-ttu-id="a0187-112">Bu örnek, WCF istemci çerçevesinin dışından alınan bir SAML belirtecinin kullanılmasına izin veren bir özel belirteç sağlayıcısı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0187-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the WCF client framework to be used.</span></span>

 <span data-ttu-id="a0187-113">Özetlemek gerekirse, bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="a0187-113">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="a0187-114">Bir istemcinin özel bir belirteç sağlayıcısıyla nasıl yapılandırılabileceğini.</span><span class="sxs-lookup"><span data-stu-id="a0187-114">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="a0187-115">Bir SAML belirtecinin özel istemci kimlik bilgilerine nasıl geçirilebileceğini.</span><span class="sxs-lookup"><span data-stu-id="a0187-115">How a SAML token can be passed to the custom client credentials.</span></span>

- <span data-ttu-id="a0187-116">SAML belirtecinin WCF istemci çerçevesine nasıl sağlandığı.</span><span class="sxs-lookup"><span data-stu-id="a0187-116">How the SAML token is provided to the WCF client framework.</span></span>

- <span data-ttu-id="a0187-117">Sunucunun, sunucunun X. 509.440 sertifikasını kullanarak istemci tarafından nasıl doğrulandığını.</span><span class="sxs-lookup"><span data-stu-id="a0187-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="a0187-118">Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için iki uç nokta sunar. Her uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="a0187-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="a0187-119">Bağlama, Ileti güvenliği kullanan bir standart ile yapılandırılır `wsFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="a0187-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="a0187-120">Bir uç nokta, istemcinin simetrik bir kanıt anahtar kullanan bir SAML belirteci ile kimlik doğrulamasını, diğeri ise asimetrik bir kanıt anahtar kullanan bir SAML belirteci ile kimlik doğrulaması yapmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="a0187-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="a0187-121">Hizmet, davranışı kullanarak hizmet sertifikasını da yapılandırır `serviceCredentials` .</span><span class="sxs-lookup"><span data-stu-id="a0187-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="a0187-122">`serviceCredentials`Davranış, bir hizmet sertifikası yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a0187-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="a0187-123">Hizmet sertifikası, istemci tarafından hizmetin kimliğini doğrulamak ve ileti koruması sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0187-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="a0187-124">Aşağıdaki yapılandırma, bu konunun sonundaki Kurulum yönergelerinde açıklandığı şekilde, örnek kurulum sırasında yüklenen "localhost" sertifikasına başvurur.</span><span class="sxs-lookup"><span data-stu-id="a0187-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="a0187-125">`serviceCredentials`Davranış, SAML belirteçlerini imzalamak için güvenilen sertifikaları yapılandırmanıza de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a0187-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="a0187-126">Aşağıdaki yapılandırma, örnek sırasında yüklenen ' Gamze ' sertifikasına başvurur.</span><span class="sxs-lookup"><span data-stu-id="a0187-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>

```xml
<system.serviceModel>
 <services>
  <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
   <host>
    <baseAddresses>
     <!-- configure base address provided by host -->
     <add
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />
    </baseAddresses>
   </host>
   <!-- use base address provided by host -->
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->
   <endpoint address="calc/symm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->
   <endpoint address="calc/asymm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding2"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
 </services>

 <bindings>
  <wsFederationHttpBinding>
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->
   <binding name="Binding1">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="SymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->
   <binding name="Binding2">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="AsymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
  </wsFederationHttpBinding>
 </bindings>

 <behaviors>
  <serviceBehaviors>
   <behavior name="CalculatorServiceBehavior">
    <!--
    The serviceCredentials behavior allows one to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
    <serviceCredentials>
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->
      <knownCertificates>
       <add storeLocation="LocalMachine"
            storeName="TrustedPeople"
            x509FindType="FindBySubjectName"
            findValue="Alice"/>
      </knownCertificates>
     </issuedTokenAuthentication>
     <serviceCertificate storeLocation="LocalMachine"
                         storeName="My"
                         x509FindType="FindBySubjectName"
                         findValue="localhost"  />
    </serviceCredentials>
   </behavior>
  </serviceBehaviors>
 </behaviors>

</system.serviceModel>
```

 <span data-ttu-id="a0187-127">Aşağıdaki adımlarda, özel bir SAML belirteci sağlayıcısının nasıl geliştirilmesi ve WCF: güvenlik çerçevesi ile tümleştirme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a0187-127">The following steps show how to develop a custom SAML token provider and integrate it with WCF: security framework:</span></span>

1. <span data-ttu-id="a0187-128">Özel bir SAML belirteci sağlayıcısı yazın.</span><span class="sxs-lookup"><span data-stu-id="a0187-128">Write a custom SAML token provider.</span></span>

     <span data-ttu-id="a0187-129">Örnek, oluşturma zamanında sağlanmış bir SAML onaylama işlemi temel alınarak bir güvenlik belirteci döndüren özel bir SAML belirteci sağlayıcısı uygular.</span><span class="sxs-lookup"><span data-stu-id="a0187-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>

     <span data-ttu-id="a0187-130">Bu görevi gerçekleştirmek için, özel belirteç sağlayıcısı <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfından türetilir ve yöntemi geçersiz kılar <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> .</span><span class="sxs-lookup"><span data-stu-id="a0187-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="a0187-131">Bu yöntem, oluşturur ve yeni bir döndürür `SecurityToken` .</span><span class="sxs-lookup"><span data-stu-id="a0187-131">This method creates and returns a new `SecurityToken`.</span></span>

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
     // Create a SamlSecurityToken from the provided assertion
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);

     // Create a SecurityTokenSerializer that will be used to
     // serialize the SamlSecurityToken
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();
     // Create a memory stream to write the serialized token into
     // Use an initial size of 64Kb
     MemoryStream s = new MemoryStream(UInt16.MaxValue);

     // Create an XmlWriter over the stream
     XmlWriter xw = XmlWriter.Create(s);

     // Write the SamlSecurityToken into the stream
     ser.WriteToken(xw, samlToken);

     // Seek back to the beginning of the stream
     s.Seek(0, SeekOrigin.Begin);

     // Load the serialized token into a DOM
     XmlDocument dom = new XmlDocument();
     dom.Load(s);

     // Create a KeyIdentifierClause for the SamlSecurityToken
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();

    // Return a GenericXmlToken from the XML for the
    // SamlSecurityToken, the proof token, the valid from and valid
    // until times from the assertion and the key identifier clause
    // created above
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);
    }
    ```

2. <span data-ttu-id="a0187-132">Özel güvenlik belirteci Yöneticisi yazın.</span><span class="sxs-lookup"><span data-stu-id="a0187-132">Write custom security token manager.</span></span>

     <span data-ttu-id="a0187-133"><xref:System.IdentityModel.Selectors.SecurityTokenManager>Sınıfı, <xref:System.IdentityModel.Selectors.SecurityTokenProvider> <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> metoduna öğesine geçirilen belirli bir oluşturmak için kullanılır `CreateSecurityTokenProvider` .</span><span class="sxs-lookup"><span data-stu-id="a0187-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="a0187-134">Belirteç kimlik doğrulaması ve belirteç seri hale getirici oluşturmak için bir güvenlik belirteci Yöneticisi de kullanılır, ancak bunlar bu örnek kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="a0187-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="a0187-135">Bu örnekte, özel güvenlik belirteci Yöneticisi <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfından devralır ve `CreateSecurityTokenProvider` geçilen BELIRTEÇ gereksinimleri SAML belirtecinin istendiğini GÖSTERIYORSA özel SAML belirteci sağlayıcısını döndürmek için yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a0187-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="a0187-136">İstemci kimlik bilgileri sınıfı (bkz. Adım 3) bir onaylama belirtmediğinden, güvenlik belirteci Yöneticisi uygun bir örnek oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0187-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>

    ```csharp
    public class SamlSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
     SamlClientCredentials samlClientCredentials;

     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)
      : base(samlClientCredentials)
     {
      // Store the creating client credentials
      this.samlClientCredentials = samlClientCredentials;
     }

     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )
     {
      // If token requirement matches SAML token return the
      // custom SAML token provider
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")
      {
       // Retrieve the SAML assertion and proof token from the
       // client credentials
       SamlAssertion assertion = this.samlClientCredentials.Assertion;
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;

       // If either the assertion of proof token is null...
       if (assertion == null || prooftoken == null)
       {
        // ...get the SecurityBindingElement and then the
        // specified algorithm suite
        SecurityBindingElement sbe = null;
        SecurityAlgorithmSuite sas = null;

        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))
        {
         sas = sbe.DefaultAlgorithmSuite;
        }

        // If the token requirement is for a SymmetricKey based token..
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)
        {
         // Create a symmetric proof token
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );
         // and a corresponding assertion based on the claims specified in the client credentials
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);
        }
        // otherwise...
        else
        {
         // Create an asymmetric proof token
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();
         // and a corresponding assertion based on the claims
         // specified in the client credentials
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );
        }
       }

       // Create a SamlSecurityTokenProvider based on the assertion and proof token
       return new SamlSecurityTokenProvider(assertion, prooftoken);
      }
      // otherwise use base implementation
      else
      {
       return base.CreateSecurityTokenProvider(tokenRequirement);
      }
    }
    ```

3. <span data-ttu-id="a0187-137">Özel bir istemci kimlik bilgisi yazın.</span><span class="sxs-lookup"><span data-stu-id="a0187-137">Write a custom client credential.</span></span>

     <span data-ttu-id="a0187-138">İstemci kimlik bilgileri sınıfı, istemci ara sunucusu için yapılandırılan kimlik bilgilerini temsil etmek için kullanılır ve belirteç kimlik doğrulaması, belirteç sağlayıcıları ve belirteç serileştiricisini almak için kullanılan bir güvenlik belirteci Yöneticisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0187-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>

    ```csharp
    public class SamlClientCredentials : ClientCredentials
    {
     ClaimSet claims;
     SamlAssertion assertion;
     SecurityToken proofToken;

     public SamlClientCredentials() : base()
     {
      // Set SupportInteractive to false to suppress Cardspace UI
      base.SupportInteractive = false;
     }

     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )
     {
      // Just do reference copy given sample nature
      this.assertion = other.assertion;
      this.claims = other.claims;
      this.proofToken = other.proofToken;
     }

     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }

     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }
     public ClaimSet Claims { get { return claims; } set { claims = value; } }

     protected override ClientCredentials CloneCore()
     {
      return new SamlClientCredentials(this);
     }

     public override SecurityTokenManager CreateSecurityTokenManager()
     {
      // return custom security token manager
      return new SamlSecurityTokenManager(this);
     }
    }
    ```

4. <span data-ttu-id="a0187-139">İstemciyi özel istemci kimlik bilgilerini kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a0187-139">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="a0187-140">Örnek, varsayılan istemci kimlik bilgisi sınıfını siler ve istemcinin özel istemci kimlik bilgisini kullanabilmesi için yeni istemci kimlik bilgisi sınıfını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0187-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>

    ```csharp
    // Create new credentials class
    SamlClientCredentials samlCC = new SamlClientCredentials();

    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");

    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");

    // Create some claims to put in the SAML assertion
    IList<Claim> claims = new List<Claim>();
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));
    ClaimSet claimset = new DefaultClaimSet(claims);
    samlCC.Claims = claimset;

    // set new credentials
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);
    ```

 <span data-ttu-id="a0187-141">Hizmette, arayanla ilişkili talepler görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a0187-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="a0187-142">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a0187-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a0187-143">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a0187-143">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="a0187-144">Toplu Iş dosyası kurulumu</span><span class="sxs-lookup"><span data-stu-id="a0187-144">Setup Batch File</span></span>

 <span data-ttu-id="a0187-145">Bu örneğe eklenen Setup.bat Batch dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikayla yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0187-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="a0187-146">Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0187-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="a0187-147">Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0187-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="a0187-148">Sunucu sertifikası oluşturuluyor:</span><span class="sxs-lookup"><span data-stu-id="a0187-148">Creating the server certificate:</span></span>

     <span data-ttu-id="a0187-149">Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0187-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="a0187-150">`%SERVER_NAME%`Değişken, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0187-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="a0187-151">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a0187-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="a0187-152">Bu toplu iş dosyasındaki varsayılan değer localhost 'tur.</span><span class="sxs-lookup"><span data-stu-id="a0187-152">The default value in this batch file is localhost.</span></span>

     <span data-ttu-id="a0187-153">Sertifika, LocalMachine depolama konumu altında (kişisel) deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="a0187-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="a0187-154">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="a0187-154">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="a0187-155">Setup.bat Batch dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="a0187-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="a0187-156">Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a0187-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="a0187-157">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="a0187-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="a0187-158">Veren sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="a0187-158">Creating the issuer certificate.</span></span>

     <span data-ttu-id="a0187-159">Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak veren sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0187-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="a0187-160">`%USER_NAME%`Değişken, verenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0187-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="a0187-161">Kendi verenin adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a0187-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="a0187-162">Bu toplu iş dosyasındaki varsayılan değer gamze 'dir.</span><span class="sxs-lookup"><span data-stu-id="a0187-162">The default value in this batch file is Alice.</span></span>

     <span data-ttu-id="a0187-163">Sertifika, CurrentUser Store konumu altında My deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="a0187-163">The certificate is stored in My store under the CurrentUser store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="a0187-164">Verenin sertifikasını sunucunun Güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="a0187-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>

     <span data-ttu-id="a0187-165">Setup.bat Batch dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="a0187-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="a0187-166">Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a0187-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="a0187-167">İstemci güvenilen kök sertifikasında kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), sunucu sertifika deposunu veren sertifikaya doldurmanın bu adımı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a0187-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="a0187-168">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="a0187-168">To set up and build the sample</span></span>

1. <span data-ttu-id="a0187-169">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a0187-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a0187-170">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a0187-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a0187-171">Bu örneğe yönelik yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a0187-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="a0187-172">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a0187-172">To run the sample on the same computer</span></span>

1. <span data-ttu-id="a0187-173">Visual Studio 2012 komut isteminde örnek yükleme klasöründen yönetici ayrıcalıklarıyla Çalıştır Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a0187-173">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="a0187-174">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="a0187-174">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a0187-175">Setup.bat Batch dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a0187-175">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="a0187-176">Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni, Setup.bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="a0187-176">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="a0187-177">Service\bin. 'den başlatma Service.exe</span><span class="sxs-lookup"><span data-stu-id="a0187-177">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="a0187-178">\Client\bin. 'den başlatma Client.exe</span><span class="sxs-lookup"><span data-stu-id="a0187-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="a0187-179">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a0187-179">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="a0187-180">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a0187-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="a0187-181">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a0187-181">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="a0187-182">Hizmet ikili dosyaları için hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a0187-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="a0187-183">Hizmet programı dosyalarını hizmet bilgisayarındaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a0187-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="a0187-184">Ayrıca, Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a0187-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="a0187-185">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikasına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0187-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="a0187-186">Service.exe.config dosyasının bu yeni sertifika adını yansıtması için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0187-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="a0187-187">Setup.bat Batch dosyasını değiştirerek sunucu sertifikası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0187-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="a0187-188">setup.bat dosyasının, yönetici ayrıcalıklarıyla açılmış bir Visual Studio için Geliştirici Komut İstemi çalıştırılması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a0187-188">Note that the setup.bat file must be run in a Developer Command Prompt for Visual Studio window opened with administrator privileges.</span></span> <span data-ttu-id="a0187-189">`%SERVER_NAME%`Değişkeni, hizmeti barındırmak için kullanılan bilgisayarın tam ana bilgisayar adına ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0187-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="a0187-190">Sunucu sertifikasını istemcinin CurrentUser-TrustedPeople deposuna kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a0187-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="a0187-191">Sunucu sertifikası, istemci güvenilir veren tarafından verildiğinde bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a0187-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="a0187-192">Hizmet bilgisayarındaki Service.exe.config dosyasında, temel adresin değerini localhost yerine tam nitelikli bir bilgisayar adı belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a0187-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="a0187-193">Hizmet bilgisayarında, komut isteminden Service.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a0187-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="a0187-194">İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a0187-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="a0187-195">İstemci bilgisayardaki Client.exe.config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a0187-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="a0187-196">İstemci bilgisayarda, `Client.exe` bir komut istemi penceresinden başlatın.</span><span class="sxs-lookup"><span data-stu-id="a0187-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="a0187-197">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a0187-197">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="a0187-198">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="a0187-198">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="a0187-199">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a0187-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
