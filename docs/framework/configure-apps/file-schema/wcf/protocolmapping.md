---
description: 'Hakkında daha fazla bilgi edinin: <protocolMapping>'
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: defdf3129122212dac9481dc5d8d48a0dfa94d72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786921"
---
# \<protocolMapping>

Aktarım Protokolü şemaları (örn. http, net. TCP, net. pipe, vs.) ve WCF bağlamaları arasında bir dizi varsayılan protokol eşlemesini tanımlamaya yönelik bir yapılandırma bölümünü temsil eder. Çalışma zamanında varsayılan uç noktalar oluştururken, Windows Communication Foundation (WCF) yapılandırılan eşlemelere bakar ve belirli bir tabanlı adres için hangi bağlamanın kullanılacağına karar verir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  

 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|Bir Aktarım Protokolü düzeni (örneğin, http, net. TCP, net. pipe, vb.) ve bir WCF bağlaması arasında bir varsayılan protokol eşlemesi içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|Tüm WCF yapılandırma öğelerinin kök öğesi.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki yapılandırma örneği machine.config dosyasında varsayılan protokol eşlemesini gösterir. machine.config dosyasını değiştirerek makine düzeyinde bu varsayılan eşlemeyi geçersiz kılabilirsiniz. Ya da uygulamayı yalnızca bir uygulamanın kapsamında geçersiz kılmak istiyorsanız, uygulama yapılandırma dosyanızda bu bölümü geçersiz kılabilir ve ayrı protokol şemaları için eşlemeyi değiştirebilirsiniz.  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
