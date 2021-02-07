---
description: 'Hakkında daha fazla bilgi edinin: <exposedMethod>'
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 7bf271ba03ee16c6a45726e2bcb522bf6f55d441
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664736"
---
# \<exposedMethod>

Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan bir COM+ yöntemini temsil eder.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan COM+ yöntemini içeren bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<exposedMethods>](exposedmethods.md)|[\<exposedMethod>](exposedmethod.md)Öğelerin koleksiyonu.|  
  
## <a name="remarks"></a>Açıklamalar  

 COM+ tümleştirme yapılandırma aracı (ComSvcConfig.exe), bir COM arabiriminden oluşturulan hizmet sözleşmesinde görünecek belirli yöntemler eklemek için kullanılabilir.  
  
 Örneğin, ' de com arabiriminden üç adlandırılmış yöntemi eklemek için aşağıdaki komutu kullanabilirsiniz `IFinances` `ItemOrders` . Finans bileşeni, oluşturulan hizmet sözleşmesine.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 Ayrıca ComSvcConfig.exe çalıştırdığınızda, daha önce bahsedilen yöntemleri öğe olarak listeleyerek aşağıdaki hizmet sözleşmesini oluşturur [\<exposedMethod>](exposedmethod.md) .  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 Hizmet başlatma sırasında çalışma zamanı, yalnızca öğe listesine dahil olan yöntemleri inceleyerek ve ekleyerek bir hizmet sözleşmesi oluşturmaya çalışır [\<exposedMethod>](exposedmethod.md) . Hizmet sözleşmesine dahil olmayan her arabirim yöntemi için bir izleme oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [COM+ uygulamalarıyla tümleştirme](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
