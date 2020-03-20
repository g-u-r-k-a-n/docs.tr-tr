---
title: Özel Bir Şifreleme Algoritması Belirtme
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 673d177a665e265d77f0221e0a00f4b814c8795c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186482"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="c218b-102">Özel Bir Şifreleme Algoritması Belirtme</span><span class="sxs-lookup"><span data-stu-id="c218b-102">Specifying a Custom Crypto Algorithm</span></span>
<span data-ttu-id="c218b-103">WCF, verileri şifrelerken veya dijital imzaları hesaplarken kullanmak üzere özel bir şifreleme algoritması belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c218b-103">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="c218b-104">Bu, aşağıdaki adımlarla yapılır:</span><span class="sxs-lookup"><span data-stu-id="c218b-104">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="c218b-105">Bir sınıf türetme<xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span><span class="sxs-lookup"><span data-stu-id="c218b-105">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="c218b-106">Algoritmayı kaydedin</span><span class="sxs-lookup"><span data-stu-id="c218b-106">Register the algorithm</span></span>  
  
3. <span data-ttu-id="c218b-107">Bağlayıcıyı <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>türetilmiş sınıfla yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="c218b-107">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="c218b-108">SecurityAlgorithmSuite'ten bir sınıf türetin</span><span class="sxs-lookup"><span data-stu-id="c218b-108">Derive a class from SecurityAlgorithmSuite</span></span>  
 <span data-ttu-id="c218b-109">Çeşitli <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> güvenlik le ilgili işlemleri gerçekleştirirken kullanılacak algoritmayı belirtmenize olanak tanıyan soyut bir taban sınıftır.</span><span class="sxs-lookup"><span data-stu-id="c218b-109">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="c218b-110">Örneğin, dijital imza için karma hesaplama veya bir iletiyi şifreleme.</span><span class="sxs-lookup"><span data-stu-id="c218b-110">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="c218b-111">Aşağıdaki kod, bir sınıfın nasıl <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>türetileni gösterir:</span><span class="sxs-lookup"><span data-stu-id="c218b-111">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="c218b-112">Özel Algoritmayı Kaydedin</span><span class="sxs-lookup"><span data-stu-id="c218b-112">Register the Custom Algorithm</span></span>  
 <span data-ttu-id="c218b-113">Kayıt bir yapılandırma dosyasında veya zorunlu kodda yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="c218b-113">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="c218b-114">Özel bir algoritmayı kaydetme, bir kripto hizmet sağlayıcısı ve takma ad uygulayan bir sınıf arasında eşleme oluşturarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="c218b-114">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="c218b-115">Takma ad daha sonra WCF hizmetinin bağlama algoritması belirtilirken kullanılan bir URI eşlenir.</span><span class="sxs-lookup"><span data-stu-id="c218b-115">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="c218b-116">Aşağıdaki yapılandırma snippet config özel bir algoritma nasıl kaydolunacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c218b-116">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://constoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="c218b-117"><`cryptoClasses`> öğesi altındaki bölüm SHA256CryptoServiceProvider ve takma adı "SHA256CSP" arasında eşleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c218b-117">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="c218b-118"><`nameEntry`> öğesi "SHA256CSP" diğer adı ile belirtilen URL `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`arasındaki eşlemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c218b-118">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`.</span></span>  
  
 <span data-ttu-id="c218b-119">Özel algoritmayı koda kaydetmek <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c218b-119">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="c218b-120">Bu yöntem her iki eşleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c218b-120">This method creates both mappings.</span></span> <span data-ttu-id="c218b-121">Aşağıdaki örnek, bu yöntemin nasıl çağrıldığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="c218b-121">The following example shows how to call this method:</span></span>  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="c218b-122">Bağlamayı Yapılandır</span><span class="sxs-lookup"><span data-stu-id="c218b-122">Configure the Binding</span></span>  
 <span data-ttu-id="c218b-123">Aşağıdaki kod snippet gösterildiği <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>gibi bağlama ayarlarında özel türemiş sınıf belirterek bağlama yapılandırırsınız:</span><span class="sxs-lookup"><span data-stu-id="c218b-123">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="c218b-124">Tam bir kod örneği için [WCF Security örneğindeki Şifreleme Çevikliği'ne](../samples/cryptographic-agility-in-wcf-security.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="c218b-124">For a complete code example, see the [Cryptographic Agility in WCF Security](../samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c218b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c218b-125">See also</span></span>

- [<span data-ttu-id="c218b-126">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c218b-126">Securing Services and Clients</span></span>](../feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c218b-127">Hizmetleri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c218b-127">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="c218b-128">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c218b-128">Security Overview</span></span>](../feature-details/security-overview.md)
- [<span data-ttu-id="c218b-129">Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="c218b-129">Security Concepts</span></span>](../feature-details/security-concepts.md)
