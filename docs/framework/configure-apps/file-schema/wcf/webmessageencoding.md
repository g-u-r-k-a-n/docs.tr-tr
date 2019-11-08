---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: 4aa87acaf9080959ba8b53e3ec3216314dc745b6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732587"
---
# <a name="webmessageencoding"></a>webMessageEncoding \<
Düz metin XML, JavaScript Nesne Gösterimi (JSON) ileti kodlamaları ve "ham" ikili içeriğin Windows Communication Foundation (WCF) bağlamasında kullanıldığı zaman okunmalarını ve yazılmasını sağlar.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webMessageEncoding >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`maxReadPoolSize`|Yeni okuyucu ayırmadan aynı anda okunabilecek ileti miktarı. Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir. Her iç kodlayıcıda (Text, JSON ve "RAW") her biri için varsayılan değer 64 okuyucudır.<br /><br /> Bu sayının artırılması, bellek tüketimini artırır, ancak yeni bir tane oluşturmak yerine zaten oluşturulmuş olan havuzdan okuyucuları kullanabildiğinden, Encoder 'ı gelen iletilerin ani patlayıcılarıyla uğraşmak üzere hazırlar.|  
|`maxWritePoolSize`|Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti miktarı. Daha büyük havuz boyutları, daha büyük bir çalışma kümesinin maliyetinde sistem etkinliğini daha dayanıklı hale getirir. Her iç kodlayıcıda (Text, JSON ve "RAW") her biri için varsayılan değer 16 yazıcıdır.<br /><br /> Bu sayının artırılması bellek tüketimini artırır, ancak yeni olanlar oluşturmak yerine zaten oluşturulan havuzdan yazarları kullanabilmesi nedeniyle kodlayıcıyı, giden iletilerin ani burdıklarıyla uğraşmak üzere hazırlar.|  
|`writeEncoding`|Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını belirtir. Geçerli değerler şunlardır:<br /><br /> -Unicodefffebir kodlama: Unicode Big endian kodlaması.<br />-Utf16TextEncoding: Unicode kodlaması.<br />-Utf8TextEncoding: 8 bit kodlama.<br /><br /> Varsayılan değer Utf8TextEncoding ' dir. Bu öznitelik <xref:System.Text.Encoding>türündedir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar. Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\< bağlama >](bindings.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kodlama bir iletiyi bir bayt dizisine dönüştürme işlemidir. Kod çözme işlemi ters işlemdir. Bu süreçler bir karakter kodlamasının belirtimini gerektirir.  
  
 `webMessageEncoding` öğesi, düz metin XML ve JSON kodlamaları ve "ham" ikili verileri işlemek için bir dizi iç kodlayıcıya temsilci seçerek işe yarar. Bu temsili bir bileşik ileti Kodlayıcısı tarafından yapılır.  
  
 Bu bağlama öğesi ve onun bileşik Kodlayıcı, `webHttpBinding` öğesi tarafından kullanılan SOAP mesajlaşma kullanmayan senaryolarda kodlamayı denetlemek için kullanılır. Bu senaryolar "düz eski XML" (POX), temsili durum aktarımı (REST), gerçekten basit dağıtım (RSS) ve Atom dağıtımı ve zaman uyumsuz JavaScript ve XML (AJAX) içerir. Bileşik ileti Kodlayıcısı SOAP veya WS-Addressing desteklemez.  
  
 Binding öğesi `writeEncoding` özniteliği kullanılarak bir yazma karakteri kodlaması ile yapılandırılabilir. Sağlanan <xref:System.Text.Encoding> değeri, JSON ve metin XML durumları için yazma davranışını belirtir. Okuma sırasında, herhangi bir geçerli ileti kodlaması ve metin kodlaması anlaşılmıştır.  
  
 `maxReadPoolSize` ve `maxWritePoolSize`, sırasıyla ayrılacak en fazla okuyucu ve yazıcı sayısını ayarlamak için de kullanılabilir. Varsayılan olarak 64 okuyucular ve 16 yazıcı ayrılır.  
  
 Varsayılan Karmaşıklık kısıtlamaları Ayrıca, uç nokta işleme kaynaklarını bağlamak üzere ileti karmaşıklığı kullanmayı deneyen bir hizmet reddi (DOS) saldırısı sınıfına karşı korumak için [\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) öğesi kullanılarak ayarlanır.  
  
## <a name="example"></a>Örnek  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [İleti Kodlama](message-encoding.md)
- [İleti Kodlayıcı Seçme](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
