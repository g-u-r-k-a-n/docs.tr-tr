---
description: 'Daha fazla bilgi edinin: <cryptoClass> öğesi'
title: <cryptoClass> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: 503a079ea78a71a11e4c750a629cf67c9244a25d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698946"
---
# <a name="cryptoclass-element"></a>\<cryptoClass> Öğesi

Öğesinde bir kolay ad ile eşleşen bir şifreleme sınıfı içerir [\<nameEntry>](nameentry-element.md) .  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**

## <a name="syntax"></a>Syntax  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`customClassName`|Gerekli öznitelik.<br /><br /> Şifreleme sınıfıyla ilgili bilgileri içerir. Sınıfınız için kısa bir ad sağlamak üzere bu özniteliği kullanın. [Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize belirtmeniz gerekir.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`cryptoClasses`|Öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir [\<nameEntry>](nameentry-element.md) .|  
|`cryptographySettings`|Şifreleme ayarlarını içerir.|  
|`cryptoNameMapping`|Kolay adlarla sınıfların eşlemelerini içerir.|  
|`mscorlib`|Öğesini içerir [\<cryptographySettings>](cryptographysettings-element.md) .|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, **\<cryptoClass>** bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için öğesinin nasıl kullanılacağını gösterir. Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma dosyası şeması](../index.md)
- [Şifreleme ayarları şeması](index.md)
- [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md)
- [Şifreleme Sınıflarını Yapılandırma](../../configure-cryptography-classes.md)
