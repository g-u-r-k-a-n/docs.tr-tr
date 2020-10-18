---
title: Özel Bir Şifreleme Algoritması Belirtme
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 3b4690071ac148966601a1c0f50edfd5a9fd52fc
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163239"
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Özel Bir Şifreleme Algoritması Belirtme
WCF, verileri şifrelerken veya dijital imzaları hesaplarken kullanılacak özel bir şifre algoritması belirtmenize olanak tanır. Bu işlem aşağıdaki adımlarla yapılır:  
  
1. Öğesinden bir sınıf türet <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2. Algoritmayı kaydetme  
  
3. Bağlamayı <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> türetilmiş sınıfla yapılandırın.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>SecurityAlgorithmSuite 'ten bir sınıf türet  
 , <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> Güvenlikle ilgili çeşitli işlemler gerçekleştirirken kullanılacak algoritmayı belirtmenize olanak tanıyan soyut bir temel sınıftır. Örneğin, dijital imza için bir karma hesaplama veya bir iletiyi şifreleme. Aşağıdaki kod, öğesinden bir sınıfın nasıl türetileceğini göstermektedir <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> :  
  
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
  
## <a name="register-the-custom-algorithm"></a>Özel algoritmayı Kaydet  
 Kayıt, bir yapılandırma dosyasında ya da kesinlik bir kod içinde yapılabilir. Bir özel algoritmayı kaydetmek, bir şifreleme hizmeti sağlayıcısı ve diğer ad uygulayan bir sınıf arasında eşleme oluşturularak yapılır. Diğer ad daha sonra WCF hizmeti bağlamasındaki algoritmayı belirtirken kullanılan bir URI ile eşleştirilir. Aşağıdaki yapılandırma kod parçacığında özel bir algoritmanın config 'e nasıl kaydedileceği gösterilmektedir:  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://contoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <> öğesinin altındaki bölüm `cryptoClasses` , SHA256CryptoServiceProvider ve "SHA256CSP" diğer adı arasında eşlemeyi oluşturur. <`nameEntry`> öğesi, "SHA256CSP" diğer adı ve BELIRTILEN URL arasında eşleme oluşturur `http://contoso.com/CustomAlgorithms/CustomHashAlgorithm` .  
  
 Özel algoritmayı kodda kaydetmek için <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> yöntemini kullanın. Bu yöntem her iki eşlemeyi de oluşturur. Aşağıdaki örnek, bu yöntemin nasıl çağrılacağını göstermektedir:  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://contoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Bağlamayı yapılandırma  
 Bağlama <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> ayarlarında, aşağıdaki kod parçacığında gösterildiği gibi özel türetilmiş sınıfı belirterek bağlamayı yapılandırırsınız:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Tüm kod örnekleri için bkz. [WCF güvenlik örneğindeki şifreleme çevikliği](../samples/cryptographic-agility-in-wcf-security.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet ve İstemcileri Güvenli Hale Getirme](../feature-details/securing-services-and-clients.md)
- [Hizmetleri Güvenli Hale Getirme](../securing-services.md)
- [Güvenliğe genel bakış](../feature-details/security-overview.md)
- [Güvenlik Kavramları](../feature-details/security-concepts.md)
