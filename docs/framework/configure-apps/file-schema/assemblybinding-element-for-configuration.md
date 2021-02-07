---
description: 'İçin: öğesi hakkında daha fazla bilgi <assemblyBinding><configuration>'
title: <configuration> için <assemblyBinding> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 5cc3fc7cccd4b9dc7b62815734ff76e32e2243d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730115"
---
# <a name="assemblybinding-element-for-configuration"></a>\<configuration> için \<assemblyBinding> öğesi

Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<assemblyBinding>**

## <a name="syntax"></a>Syntax

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **özniteliði** | Gerekli öznitelik.<br><br>Derleme bağlaması için gereken XML ad alanını belirtir. Değer olarak "urn: schemas-microsoft-com: asm. v1" dizesini kullanın. |

## <a name="parent-element"></a>Üst öğe

|     | Description |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-element"></a>Alt öğe

|     | Description |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | Dahil edilecek bir yapılandırma dosyasını belirtir. |

## <a name="remarks"></a>Açıklamalar

[**\<linkedConfiguration>**](linkedconfiguration-element.md)Öğesi, uygulama yapılandırma dosyalarının derleme yapılandırma ayarlarını çoğaltmak yerine, bilinen konumlarda derleme yapılandırma dosyalarını içermesini sağlayarak bileşen derlemelerinin yönetimini basitleştirir.

> [!NOTE]
> **\<linkedConfiguration>** Windows yan yana bildirimleri olan uygulamalar için öğesi desteklenmez.

## <a name="example"></a>Örnek

Aşağıdaki örnek, yerel sabit diske bir yapılandırma dosyasının nasıl ekleneceğini göstermektedir:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
