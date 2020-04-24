---
title: <system.xml.serialization> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 02027a238bc9a2f82963ea841584d2bb3c6446c6
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410541"
---
# <a name="systemxmlserialization-element"></a>\<System. xml. Serialization> öğesi

XML serileştirmesini denetlemek için en üst düzey öğe. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).

\<yapılandırma> \
\<System. xml. Serialization>

## <a name="syntax"></a>Sözdizimi

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<dateTimeSerialization> öğesi](../../../docs/standard/serialization/datetimeserialization-element.md)|Serileştirme modu belirler <xref:System.DateTime> nesneleri.|
|[\<SchemaImporterExtensions> öğesi](../../../docs/standard/serialization/schemaimporterextensions-element.md)|Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<yapılandırma> öğesi](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir <xref:System.DateTime> nesnenin serileştirme modunun ve tarafından kullanılan türlerin .NET Framework türlerine ne <xref:System.Xml.Serialization.XmlSchemaImporter> zaman ekleneceğini gösterir.

```xml
<system.xml.serialization>
    <xmlSerializer checkDeserializeAdvances="false" />
    <dateTimeSerialization mode = "Local" />
    <schemaImporterExtensions>
        <add
        name = "MobileCapabilities"
        type = "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> öğesi](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<SchemaImporterExtensions> öğesi](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [\<SchemaImporterExtensions \<Için> öğesi ekleme>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
