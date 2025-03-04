---
description: 'Daha fazla bilgi edinin: <trace> öğesi'
title: <trace> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 470bc300911656a9c9951e52e3883ba5c8b01c59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750331"
---
# <a name="trace-element"></a>\<trace> Öğesi

İzleme iletilerini toplayıp depolayan, depolayan ve yönlendiren dinleyicileri içerir.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`autoflush`|İsteğe bağlı öznitelik.<br /><br /> İzleme dinleyicilerinin her yazma işleminden sonra çıktı arabelleğini otomatik olarak temizlemesini belirtir.|  
|`indentsize`|İsteğe bağlı öznitelik.<br /><br /> Girintilendirmek için boşluk sayısını belirtir.|  
|`useGlobalLock`|İsteğe bağlı öznitelik.<br /><br /> Genel kilidin kullanılıp kullanılmayacağını belirtir.|  
  
## <a name="autoflush-attribute"></a>Oto Temizleme özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|, Çıkış arabelleğini otomatik olarak temizlemez. Bu varsayılan seçenektir.|  
|`true`|Çıktı arabelleğini otomatik olarak temizler.|  
  
## <a name="usegloballock-attribute"></a>useGlobalLock özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Dinleyicisi iş parçacığı güvenli ise, genel kilidi kullanmaz; Aksi takdirde, genel kilidi kullanır.|  
|`true`|Dinleyicinin iş parçacığı güvenli olup olmamasına bakılmaksızın genel kilidi kullanır. Bu varsayılan seçenektir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|İletileri toplayan, depolayan ve yönlendiren bir dinleyici belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|İletileri ve bir izleme anahtarının ayarlandığı düzeyi depolayan, depolayan ve yönlendiren izleme dinleyicilerini belirtir.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir `<trace>` dinleyicinin koleksiyona eklemek için öğesinin nasıl kullanılacağını gösterir `MyListener` `Listeners` . `MyListener` adlı bir dosya oluşturur `MyListener.log` ve çıktıyı dosyaya yazar. `useGlobalLock`Özniteliği olarak ayarlanır `false` ; Bu, izleme dinleyicisi iş parçacığı güvenli ise genel kilidin kullanılmasına neden olur. `autoflush`Özniteliği olarak ayarlanır `true` ; Bu, İzleme dinleyicisinin, yöntemin çağrılmasının ne olursa olsun dosyaya yazmasına neden olur <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> . `indentsize`Öznitelik 0 (sıfır) olarak ayarlanır, bu da yöntem çağrıldığında dinleyicinin sıfır boşluk girintilemesini sağlar <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> .  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [İzleme ve hata ayıklama ayarları şeması](index.md)
