---
description: 'Hakkında daha fazla bilgi edinin: <remove> NameValueSectionHandler ve DictionarySectionHandler için öğesi'
title: <remove> NameValueSectionHandler ve DictionarySectionHandler için öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: bf1434b257aa014c8f46e34f2d57d109bd510452
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740086"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<remove> NameValueSectionHandler ve DictionarySectionHandler için öğesi

Daha önce tanımlanmış bir ayarı kaldırır.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>Syntax

```xml
<add remove="key" />
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **anahtar**   | Gerekli öznitelik.<br><br>Kaldırılacak ayarın adını belirtir. |

## <a name="parent-element"></a>Üst öğe

| Öğe | Açıklama |
| ------- | ------------|
| [**\<sectionName>** Dosyalarında](custom-element-2.md) | Ve sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> . |

## <a name="child-elements"></a>Alt öğeleri

Yok

## <a name="remarks"></a>Açıklamalar

**\<remove>** Uygulamanızı yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan ayarları kaldırabilmeniz için öğesini kullanabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, **\<remove>** daha önce makine yapılandırma dosyasında tanımlanan ayarları kaldırmak için bir uygulama yapılandırma dosyasında öğesinin nasıl kullanılacağını gösterir.

Aşağıdaki makine yapılandırma dosyası kodu, bölümünü bildirir **\<mySection>** ve iki ayar ekler `key1` `key2` :

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

Aşağıdaki uygulama yapılandırma dosyası kodu, bu `key2` ayarı öğesinden kaldırır **\<mySection>** :

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
