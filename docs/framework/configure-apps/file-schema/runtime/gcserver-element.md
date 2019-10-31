---
title: <gcServer> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 98ecc7069df20a92492e9a6276a0d88331ccc0bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116663"
---
# <a name="gcserver-element"></a>\<gcServer > öğesi
Ortak dil çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<gcServer >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının sunucu çöp toplamayı çalıştırmasını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Sunucu çöp toplamayı çalıştırmaz. Bu varsayılandır.|  
|`true`|Sunucu çöp toplamayı çalıştırır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR) iki tür çöp toplamayı destekler: tüm sistemlerde kullanılabilen iş istasyonu çöp toplama ve çok işlemcili sistemlerde bulunan sunucu çöp toplama. CLR 'nin gerçekleştirdiği çöp toplamanın türünü denetlemek için `<gcServer>` öğesini kullanın. Sunucu çöp toplamanın etkinleştirilip etkinleştirilmediğini anlamak için <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> özelliğini kullanın.  
  
 Tek işlemcili bilgisayarlar için varsayılan iş istasyonu atık toplama en hızlı seçenek olmalıdır. İki işlemcili bilgisayarlar için iş istasyonu veya sunucu kullanılabilir. Sunucu çöp toplama, ikiden fazla işlemci için en hızlı seçenek olmalıdır.  
  
 Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir; makine yapılandırma dosyasında ise yok sayılır.  
  
> [!NOTE]
> .NET Framework 4 ve önceki sürümlerde, sunucu çöp toplama etkinleştirildiğinde eşzamanlı çöp toplama kullanılamaz. 4,5 .NET Framework başlayarak, sunucu çöp toplama işlemi eşzamanlı olur. Eş zamanlı olmayan sunucu çöp toplamayı kullanmak için `<gcServer>` öğesini `true` ve [\<gcConcurrent > öğesi](gcconcurrent-element.md) `false`olarak ayarlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sunucu çöp toplamayı mümkün bir şekilde sunar.  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [Eşzamanlı atık toplamayı devre dışı bırakmak için](gcconcurrent-element.md#to-disable-background-garbage-collection)
