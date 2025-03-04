---
title: <xmlSerializer> Öğesi
description: <xmlSerializer>Öğesi XmlSerializer 'ın ilerleme durumunun gerçekleştirilip yapılmadığını belirtir.
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 6f368880c97a21dc3e9593ecb2319d265a1b8932
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676497"
---
# <a name="xmlserializer-element"></a>\<xmlSerializer> Öğesi

Belirtir ilerleme durumunu ek bir denetim olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> yapılır.  
  
 \<configuration>  
\<system.xml.serialization>  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**Checkdeserializeavanslar**|Belirtir olup olmadığını ilerleme durumunu <xref:System.Xml.Serialization.XmlSerializer> denetlenir. Özniteliği "true" veya "false" olarak ayarlayın. Varsayılan değer "true" dır.|  
|**useLegacySerializationGeneration**|Belirtir olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> C# kod bir dosyaya yazmak ve sonra da bir derlemeye derlemek tarafından derlemeleri oluşturan eski serileştirme oluşturma kullanır. Varsayılan değer **false**'dur.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.xml.serialization> Dosyalarında](system-xml-serialization-element.md)|İçin yapılandırma ayarlarını içeren <xref:System.Xml.Serialization.XmlSerializer> ve <xref:System.Xml.Serialization.XmlSchemaImporter> sınıfları.|  
  
## <a name="remarks"></a>Açıklamalar  

 Varsayılan olarak, <xref:System.Xml.Serialization.XmlSerializer> Güvenilmeyen verilerin serisi kaldırılırken olası hizmet reddi saldırılarına karşı ek bir güvenlik katmanı sağlar. Bunu seri durumundan çıkarma sırasında sonsuz döngü algılamak deneyerek yapar. Böyle bir koşul algılanırsa, şu iletiyle bir özel durum oluşturulur: "Iç hata: seri kaldırma, temel alınan akışın üzerinde ilerleyemedi."  
  
 Bu iletiyi alan değil gerekmeyen gösteren bir saldırı hizmet reddi devam ediyor. Bazı ender durumlarda, yanlış Pozitif sonsuz döngü algılama mekanizması oluşturur ve yasal gelen ileti için özel durum. Özel uygulamanızda bu ek koruma katmanı tarafından meşru iletiler reddedilmekte olduğunu fark ederseniz **Checkdeserializeavanslar** özniteliğini "false" olarak ayarlayın.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği **Checkdeserializeavanslar** özniteliğini "false" olarak ayarlar.  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Serialization.XmlSerializer>
- [\<system.xml.serialization> Dosyalarında](system-xml-serialization-element.md)
- [XML ve SOAP serileştirme](xml-and-soap-serialization.md)
