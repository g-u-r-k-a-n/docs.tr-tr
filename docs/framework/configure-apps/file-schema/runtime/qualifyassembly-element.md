---
description: 'Daha fazla bilgi edinin: <qualifyAssembly> öğesi'
title: <qualifyAssembly> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 16891cca40d907d0ca32aea7f610e84305fcd0e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802468"
---
# <a name="qualifyassembly-element"></a>\<qualifyAssembly> Öğesi

Kısmi bir ad kullanıldığında dinamik olarak yüklenmesi gereken derlemenin tam adını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`partialName`|Gerekli öznitelik.<br /><br /> Kodda göründüğü gibi derlemenin kısmi adını belirtir.|  
|`fullName`|Gerekli öznitelik.<br /><br /> Derlemenin genel derleme önbelleğinde göründüğü haliyle tam adını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`assemblyBinding`|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>Kısmi derleme adlarını kullanarak yöntemi çağırmak, ortak dil çalışma zamanının derlemeyi yalnızca uygulama temel dizininde aramasını sağlar. **\<qualifyAssembly>** Tüm derleme bilgilerini (ad, sürüm, ortak anahtar belirteci ve kültür) sağlamak ve ortak dil çalışma zamanının genel derleme önbelleğinde derlemeyi aramasını sağlamak için uygulama yapılandırma dosyanızda öğesini kullanın.  
  
 **FullName** özniteliği, derleme kimliğinin dört alanını içermelidir: ad, sürüm, ortak anahtar belirteci ve kültür. **PartialName** özniteliği kısmen bir derlemeye başvurmalıdır. En azından derlemenin metin adını (en yaygın durum) belirtmeniz gerekir, ancak sürüm, ortak anahtar belirteci veya kültürü (ya da dört ' un herhangi bir birleşimini değil) dahil edebilirsiniz. **PartialName** , çağrın içinde belirtilen ad ile aynı olmalıdır. Örneğin, `"math"` yapılandırma dosyanızda **partialName** özniteliği olarak belirtemezsiniz ve kodunuzda çağrı yapabilirsiniz `Assembly.Load("math, Version=3.3.3.3")` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, çağrısını mantıksal olarak etkinleştirir `Assembly.Load("math")` `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` .  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Çalışma Zamanının Derlemelerin Konumunu Bulması](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Kısmi derleme başvuruları](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
