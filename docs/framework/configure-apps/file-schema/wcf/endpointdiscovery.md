---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 98b1655f42b7b43604ed4ab9d66870ec204a9590
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398015"
---
# \<endpointDiscovery>
Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|enabled|Bu uç noktada bulunabilirliği etkin olup olmadığını belirten bir Boolean değer. Varsayılan değer: `false`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|Uç nokta için kapsam URI 'Leri koleksiyonu. Birden fazla kapsam URI 'si tek bir uç noktayla ilişkilendirilebilir.|  
|[\<extensions>](extensions.md)[/ \<endpointDiscovery> ]|Bir uç nokta için yayımlanacak özel meta verileri belirtmenizi sağlayan XML öğelerinin koleksiyonu.|  
|\<types>|Aranacak arabirimlerin bir koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
|||  
  
## <a name="remarks"></a>Açıklamalar  
 Uç noktanın davranış yapılandırmasına eklendiğinde ve `enabled` özniteliği olarak ayarlandığında `true` , bu yapılandırma öğesi bulunabilirliği sağlar. Ayrıca, [\<scopes>](scopes.md) sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilen özel kapsam URI 'leri belirtmek için alt öğesini ve [\<extensions>](extensions.md) Standart bulunabilir meta VERILERI (EPR, ContractTypeName, BindingName, scope ve ListenURI) ile birlikte yayımlanması gereken özel meta verileri belirtmek için de kullanabilirsiniz.  
  
 Bu yapılandırma öğesi, [\<serviceDiscovery>](servicediscovery.md) keşfedilebilirlik için hizmet düzeyi denetimini sağlayan öğesine bağımlıdır. Bu, yapılandırmada yoksa, bu öğenin ayarlarının yoksayılacağı anlamına gelir [\<serviceDiscovery>](servicediscovery.md) .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma örneği, bir uç nokta için yayımlanacak filtre kapsamlarını ve uzantı meta verilerini belirtir.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
