---
title: GCLOHThreshold element
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451222"
---
# <a name="gclohthreshold-element"></a>GCLOHThreshold element

Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a>Sözdizimi

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br />Specifies the threshold size that causes objects to go on the large object heap.|

### <a name="enabled-attribute"></a>enabled attribute

|Değer|Açıklama|
|-----------|-----------------|
|`nnnn`|The threshold size, in bytes, that causes objects to go on the large object heap.|

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

This setting was introduced in .NET Framework 4.8.

## <a name="see-also"></a>Ayrıca bkz.

- [Run-time settings schema](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [Fundamentals of garbage collection](../../../../standard/garbage-collection/fundamentals.md)
- [NET Core run-time config options for GC](../../../../core/run-time-config/garbage-collector.md)
