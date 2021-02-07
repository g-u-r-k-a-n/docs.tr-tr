---
description: 'Hakkında daha fazla bilgi edinin: <webHttpEndpoint>'
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: d1bcda1fc97dece833c8163e5facbefe614af0ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682598"
---
# \<webHttpEndpoint>

Bu yapılandırma öğesi [\<webHttpBinding>](webhttpbinding.md) , otomatik olarak davranışını ekleyen bir sabit bağlamaya sahip standart uç nokta tanımlar [\<webHttp>](webhttp.md) . Bir REST hizmeti yazarken bu uç noktayı kullanın.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled etkin|Otomatik biçim seçiminin etkin olup olmadığını gösteren bir Boole değeri.<br /><br /> Otomatik Biçim Seçimi etkinleştirildiğinde altyapı, `Accept` istek iletisinin üstbilgisini ayrıştırır ve en uygun yanıt biçimini belirler. `Accept`Üst bilgi uygun bir yanıt biçimi belirtmezse, altyapı `Content-Type` istek iletisini veya işlemin varsayılan yanıt biçimini kullanır.|  
|defaultOutgoingResponseFormat|Varsayılan giden yanıt biçimini belirten bir özniteliği. Bu öznitelik <xref:System.ServiceModel.Web.WebMessageFormat> türü|  
|Yardım etkin|Uç nokta için HTTP yardım sayfasının etkinleştirilip etkinleştirilmediğini belirten bir Boolean değer.|  
|webEndpointType|Uç noktanın türünü belirten bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Özelliklerinden biri veya daha fazlası (adres, bağlama, sözleşme) düzeltilen, önceden tanımlanmış uç noktalar koleksiyonu.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
