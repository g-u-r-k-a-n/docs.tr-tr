---
description: 'Hakkında daha fazla bilgi edinin: için <clear> öğesi <listeners><source>'
title: <clear>İçin için öğesi <listeners><source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 731c23c73b6d149bd37672e91eca1d70431b2789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639711"
---
# <a name="clear-element-for-listeners-for-source"></a>\<clear>İçin için öğesi \<listeners>\<source>

`Listeners`İzleme kaynağı için koleksiyonu temizler.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>Syntax  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  

 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
|`sources`|İzleme iletilerini Başlatan izleme kaynaklarını içerir.|  
|`source`|İzleme iletilerini Başlatan bir izleme kaynağını belirtir.|  
|`listeners`|İletileri toplayacak, depolayan ve yönlendiren dinleyicileri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 `<clear>`Öğesi, `Listeners` dahil olmak üzere bir izleme kaynağı için koleksiyondan tüm dinleyicileri kaldırır <xref:System.Diagnostics.DefaultTraceListener> . `<clear>` `<add>` Koleksiyonda başka hiçbir etkin dinleyici bulunmadığından emin olmak için öğesini kullanmadan önce öğesini kullanabilirsiniz.  
  
## <a name="configuration-file"></a>Yapılandırma Dosyası  

 Bu öğe makine yapılandırma dosyasında (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `<clear>` öğeleri kullanarak, `<add>` dinleyicileri `console` ve `textListener` `Listeners` izleme kaynağı koleksiyonuna eklemek için öğesinin nasıl kullanılacağını gösterir `TraceSourceApp` .  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [İzleme ve hata ayıklama ayarları şeması](index.md)
- [İz Dinleyicileri](../../../debug-trace-profile/trace-listeners.md)
