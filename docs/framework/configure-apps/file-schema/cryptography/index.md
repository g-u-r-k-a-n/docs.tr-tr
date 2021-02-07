---
description: 'Daha fazla bilgi edinin: şifreleme ayarları şeması'
title: Şifreleme Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: a7b3c020ed760aba24c9faf020281b7ad4bf3af7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730089"
---
# <a name="cryptography-settings-schema"></a>Şifreleme Ayarları Şeması

Şifreleme ayarları şeması, kolay algoritma adlarının şifreleme algoritmaları uygulayan sınıflara nasıl eşlendiğini belirten öğeleri içerir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|Öğe|Açıklama|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|Öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir **\<nameEntry>** .|  
|[**\<cryptoClass**>](cryptoclass-element.md)|Öğesinde bir kolay ad ile eşleşen bir şifreleme sınıfı içerir **\<nameEntry>** .|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|Şifreleme ayarlarını içerir.|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|Kolay adlarla sınıfların eşlemelerini içerir.|  
|[**\<mscorlib>** şifreleme ayarları için öğesi](mscorlib-element-for-cryptography-settings.md)|Öğesini içerir **\<cryptographySettings>** .|  
|[**\<nameEntry>**](nameentry-element.md)|Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.|  
|[**\<oidEntry>**](oidentry-element.md)|Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.|  
|[**\<oidMap>**](oidmap-element.md)|Sınıflara ASN. 1 OID eşlemelerini içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma dosyası şeması](../index.md)
- [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md)
