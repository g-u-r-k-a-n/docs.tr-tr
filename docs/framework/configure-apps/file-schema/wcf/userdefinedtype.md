---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 7a76e5a90fe3218bc0302501b71daa9de0b098bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854840"
---
# \<userDefinedType>
Hizmet sözleşmesine dahil edilecek Kullanıcı tanımlı bir tür (UDT) temsil eder.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<userDefinedTypes>**](userdefinedtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userDefinedType>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<comContracts>
  <comContract>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Okunabilir tür adını sağlayan bir dize içeren isteğe bağlı öznitelik. Bu, çalışma zamanı tarafından kullanılmaz, ancak bir okuyucunun türleri ayırt etmesine yardımcı olur.|  
|`TypeDefID`|Kayıtlı tür kitaplığı içinde belirli UDT türünü tanımlayan bir GUID dizesi.|  
|`TypeLibID`|Türü tanımlayan kayıtlı tür kitaplığını tanımlayan bir GUID dizesi.|  
|`TypeLibVersion`|Türü tanımlayan tür kitaplığı sürümünü tanımlayan bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`userDefinedTypes`|`userDefinedType`Öğelerin koleksiyonu.|  
  
## <a name="remarks"></a>Açıklamalar  
 COM+ tümleştirme çalışma zamanı, tür kitaplığını inceleyerek hizmet oluşturur. Bir COM+ bileşeni bir DEĞIŞKEN geçiren Yöntemler içerdiğinde, sistem çalışma zamanına göre geçirilecek gerçek türleri belirleyemez. Bu nedenle, bir DEĞIŞKEN içinde Kullanıcı tanımlı tür (UDT) geçirmeye çalıştığınızda, serileştirme için bilinen bir tür olmadığından başarısız olur.  
  
 Bu sorunu aşmak için, her türlü uygun hizmet sözleşmesinde bilinen türler olarak dahil edilmesini sağlamak üzere UDTs 'yi yapılandırma dosyasına ekleyebilirsiniz. Bunu yapmak için, UDT 'yi ve sözleşmeyi (Sözleşmelerinin) benzersiz şekilde belirlemeniz gerekir. Bu, diğer bir deyişle, onu kullanan özgün COM arabirimidir.  
  
 Aşağıdaki örnek, `userDefinedTypes` Bu amaçla yapılandırma dosyasının <> bölümüne iki özel udun eklenmesini gösterir.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <userDefinedTypes>
      <userDefinedType name="CustomerType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">
      </userDefinedType>
      <userDefinedType name="AddressType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">
      </userDefinedType>
    </userDefinedTypes>
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 Hizmet başlatıldığında, tümleştirme çalışma zamanı belirtilen türleri arar ve belirtilen sözleşmeler için bunları bilinen türler koleksiyonuna ekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [\<comContracts>](comcontracts.md)
- [COM+ uygulamalarıyla tümleştirme](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
