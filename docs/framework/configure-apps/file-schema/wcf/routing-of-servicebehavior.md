---
description: 'Hakkında daha fazla bilgi <routing> edinin: <serviceBehavior>'
title: <routing> / <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 1d8a056d708b3c42aeccf3e46a0703b3fc78a17d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786895"
---
# <a name="routing-of-servicebehavior"></a>\<routing> / \<serviceBehavior>

Yönlendirme yapılandırmasına dinamik değişiklik yapılmasına izin vermek için yönlendirme hizmetine çalışma zamanı erişimi sağlar.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|filterTable|Yönlendirme hizmeti tarafından değerlendirilecek filtreleri içeren yönlendirme tablosunun adını belirten bir dize. Bu değer `name` , bölümündeki bir öğenin özniteliğiyle eşleşmelidir [\<filterTable>](filtertable.md) [\<filterTables>](filtertables.md) .|  
|yalnızca routeonheader|Filtrenin hem ileti gövdesini hem de üstbilgiyi veya yalnızca üstbilgiyi incelemenizi belirten bir Boole değeri. Varsayılan değer: `true`.|  
|soapProcessingEnabled|SOAP işlemenin gerçekleşmesi gerekip gerekmediğini belirten bir Boolean değer.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Hizmetin davranış yapılandırmasına eklendiğinde, bu yapılandırma öğesi hizmet için yönlendirmeyi sağlar. Bu öğedeki hizmet tarafından kullanılacak gerçek yönlendirme tablosunu belirtebilirsiniz.  
  
 Bu yapılandırma bölümünü kullanarak, dağıtım düzeniniz değiştiğinde hareket halindeyken yönlendirme ayarlarınızı değiştirebilirsiniz. Çalışma zamanında, kendi yönlendirme uzantınızı yeni yönlendirme ayarlarıyla kaydedebilirsiniz ve yönlendirme hizmeti, yeni iletiler ve oturumlar için güncelleştirilmiş yapılandırma bilgilerini kullanmaya başlar. böylece, başlatıldıklarında hangi kuralların yerinde olduğunu kullanarak uçuş iletileri/oturumlarından çıkılıyor.  Bu sayede, çalışma zamanı sırasında yönlendirme hizmetinin oturum güvenli, geri dönüşüm için daha az yeniden yapılandırılması yapabilirsiniz.  
