---
title: <listeners> için <source> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: d7641611e5d8257b49bc6a6abd0a2fadfde66e91
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697298"
---
# <a name="listeners-element-for-source"></a>\<kaynak > için \<dinleyicileri > öğesi
<xref:System.Diagnostics.TraceSource>için <xref:System.Diagnostics.TraceSource.Listeners%2A> koleksiyonuna dinleyici ekler veya kaldırır. Dinleyici, izleme çıkışını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)  
[ **System. diagnostics\<** &nbsp;&nbsp;>](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kaynakları >** ](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<kaynak >** ](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**dinleyicileri >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<listeners>   
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<> Ekle](add-element-for-listeners-for-source.md)|`Listeners` koleksiyonuna bir dinleyici ekler.|  
|[\<> Kaldır](remove-element-for-listeners-for-source.md)|`Listeners` koleksiyonundan bir dinleyiciyi kaldırır.|  
|[\<Temizle >](clear-element-for-listeners-for-source.md)|İzleme kaynağı için `Listeners` koleksiyonunu temizler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletilerini Başlatan izleme kaynaklarını içerir.|  
|`source`|İzleme iletilerini Başlatan bir izleme kaynağını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  
 Bu öğe makine yapılandırma dosyasında (Machine. config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `mySource` kaynağına bir konsol izleme dinleyicisi eklemek ve varsayılan izleme dinleyicisini kaldırmak için `<listeners>` öğesinin nasıl kullanılacağını gösterir.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceListener>
- [İzleme ve Hata Ayıklama Ayarları Şeması](index.md)
- [İzleme Dinleyicileri](../../../debug-trace-profile/trace-listeners.md)
