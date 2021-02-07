---
description: 'Daha fazla bilgi edinin: <settings> öğesi (ağ ayarları)'
title: <settings> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: e6ed242e68ac9a9e2c20067d66681bbcd51fcc50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712980"
---
# <a name="settings-element-network-settings"></a>\<settings> Öğesi (Ağ Ayarları)

Ad alanı için temel ağ seçeneklerini yapılandırır <xref:System.Net?displayProperty=nameWithType> .  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a>Syntax  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  

 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[httpListener](httplistener-element-network-settings.md)|Sınıf tarafından kullanılan parametreleri özelleştirir <xref:System.Net.HttpListener> .|  
|[httpWebRequest](httpwebrequest-element-network-settings.md)|Web isteği parametrelerini özelleştirir.|  
|[IPv6](ipv6-element-network-settings.md)|Internet Protokolü sürüm 6 (IPv6) desteğini sunar.|  
|[\<performanceCounter> Öğesi (ağ ayarları)](performancecounter-element-network-settings.md)|Ağ performans sayaçlarını etkinleştirilir.|  
|[servicePointManager](servicepointmanager-element-network-settings.md)|Ağ kaynaklarına bağlantıları yapılandırır.|  
|[yuvasının](socket-element-network-settings.md)|Yuva işlemlerinin tamamlama bağlantı noktalarını kullanıp kullanmadığını belirtir.|  
|[\<webProxyScript> Öğesi (ağ ayarları)](webproxyscript-element-network-settings.md)|Web proxy 'lerini keşfetme için kullanılan betiğin özelliklerini yapılandırır.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|.NET Framework ağa nasıl bağlanacağını belirten ayarları içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="configuration-files"></a>Yapılandırma Dosyaları  

 Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine.config) kullanılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net?displayProperty=nameWithType>
- [Ağ ayarları şeması](index.md)
