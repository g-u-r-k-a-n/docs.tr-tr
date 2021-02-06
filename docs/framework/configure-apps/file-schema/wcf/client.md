---
description: 'Hakkında daha fazla bilgi edinin: <client>'
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 9765460602738f49963ea521b3f00ed7c63cc568
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638866"
---
# \<client>

`client`Öğesi, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a>Syntax

```xml
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

 Yok

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|Bu istemcinin bağlanabileceği uç noktaları belirten bir uç nokta öğeleri koleksiyonu içerir.|
|[\<metadata>](metadata.md)|Meta verileri işlemeye yönelik ayarları içerir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|Tüm Windows Communication Foundation (WCF) yapılandırma öğelerinin kök öğesi.|

## <a name="remarks"></a>Açıklamalar

 `client`Bölümü, bir istemcinin bağlanabileceği uç noktaların listesini tanımlar. İstemci bölümünde listelenen her bir uç nokta kendi bağlamasını, davranışını ve sözleşmesini tanımlar. Ve özniteliklerinin birleşimiyle benzersiz şekilde tanımlanır `name` `contract` . İstemci kodu, `name` istemcinin uyguladığı hizmet için bir uç noktaya bağlanmak üzere öğesini belirtir. `name`Özniteliği atlanırsa, uç noktası uyguladığı sözleşmenin varsayılan uç noktası olarak davranır.

 Ayrıca, bu bölüm meta verileri işlemeye yönelik ayarları da belirtir.

## <a name="example"></a>Örnek

```xml
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [WCF İstemci Yapılandırması](../../../wcf/feature-details/client-configuration.md)
- [İstemciler](../../../wcf/feature-details/clients.md)
