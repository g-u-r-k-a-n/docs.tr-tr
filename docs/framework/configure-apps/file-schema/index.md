---
description: 'Hakkında daha fazla bilgi edinin: .NET Framework için yapılandırma dosyası şeması'
title: .NET Framework için yapılandırma dosyası şeması
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: eac6d14f29f5ae0eeb65efe5a1416b8f40583be3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729959"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>.NET Framework için yapılandırma dosyası şeması

Yapılandırma dosyaları, uygulamalarınız için ayarları değiştirmek ve ilkeleri ayarlamak için kullanabileceğiniz standart XML dosyalarıdır. .NET Framework yapılandırma şeması, uygulamalarınızın davranışını denetlemek için yapılandırma dosyalarında kullanabileceğiniz öğelerden oluşur. Bu bölümün içindekiler tablosu, başlatma, çalışma zamanı, ağ ve diğer yapılandırma ayarları türleri için şema hiyerarşisini yansıtır.

Yapılandırma dosyalarının türleri, biçimi ve konumu hakkında daha fazla bilgi için bkz. [uygulamaları yapılandırma](../index.md). Yapılandırma dosyalarını doğrudan düzenlemek istiyorsanız, XML hakkında bilgi edinin.

> [!IMPORTANT]
> Yapılandırma dosyalarındaki XML etiketleri ve öznitelikleri büyük/küçük harfe duyarlıdır.

## <a name="in-this-section"></a>Bu bölümde

[**\<configuration>** Dosyalarında](configuration-element.md)\
Tüm yapılandırma dosyaları için en üst düzey öğe.

[**\<assemblyBinding>** Dosyalarında](assemblybinding-element-for-configuration.md)\
Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.

[**\<linkedConfiguration>** Dosyalarında](linkedconfiguration-element.md)\
Dahil edilecek bir yapılandırma dosyasını belirtir.

[Başlangıç ayarları şeması](./startup/index.md)\
Ortak dil çalışma zamanının hangi sürümünü kullanacağınızı belirten öğeler.

[Çalışma zamanı ayarları şeması](./runtime/index.md)\
Bütünleştirilmiş kod bağlamayı ve çalışma zamanı davranışını yapılandıran öğeler.

[Ağ ayarları şeması](./network/index.md)\
.NET Framework internet 'e nasıl bağlandığını belirten öğeler.

[Şifreleme ayarları şeması](./cryptography/index.md)\
Kolay algoritma adlarını şifreleme algoritmaları uygulayan sınıflarla eşleyen öğeler.

[Yapılandırma bölümleri şeması](configuration-sections-schema.md)\
Özel ayarlar için yapılandırma bölümleri oluşturmak ve kullanmak için kullanılan öğeler.

[İzleme ve hata ayıklama ayarları şeması](./trace-debug/index.md)\
İzleme anahtarlarını ve dinleyicileri belirten öğeler.

[Derleyici ve dil sağlayıcısı ayarları şeması](./compiler/index.md)\
Kullanılabilir dil sağlayıcıları için derleyici yapılandırması belirten öğeler.

[Uygulama ayarları şeması](application-settings-schema.md)\
Windows Forms veya ASP.NET uygulamasının uygulama kapsamlı ve kullanıcı kapsamlı ayarları depolamasına ve almasına olanak tanıyan öğeler.

[Uygulama ayarları şeması](./appsettings/index.md)\
Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.

[Web ayarları şeması](./web/index.md)\
ASP.NET 'ın IIS gibi bir konak uygulamasıyla nasıl çalıştığını yapılandırmaya yönelik öğeler. *Aspnet.config* dosyalarında kullanılır.

[Windows Forms yapılandırma şeması](winforms/index.md)\
Çoklu izleyici ve yüksek DPı desteği gibi özelleştirmeler içeren Windows Forms uygulama yapılandırması bölümündeki tüm öğeler.

[WCF yapılandırma şeması](./wcf/index.md)\
WCF hizmetini ve istemci uygulamalarını yapılandırmanızı sağlayan tüm öğeler.

[WCF yönerge söz dizimi](./wcf-directive/index.md)\
`@ServiceHost`. Svc derleyicisi tarafından kullanılan sayfaya özgü öznitelikleri tanımlayan yönergesini açıklar.

[WıF yapılandırma şeması](windows-identity-foundation/index.md)\
Windows Identity Foundation (WıF) yapılandırma şemasının tüm öğeleri.

## <a name="related-sections"></a>İlgili bölümler

[Uzaktan iletişim ayarları şeması](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))\
Uzaktan iletişim uygulayan istemci ve sunucu uygulamalarını yapılandıran öğeleri açıklar.

[ASP.NET ayarları şeması](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))\
ASP.NET Web uygulamalarının davranışını denetleyen öğeleri açıklar.

[Web Hizmetleri ayarları şeması](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))\
ASP.NET Web Hizmetleri ve istemcilerinin davranışını denetleyen öğeleri açıklar.

[.NET Framework uygulamalarını yapılandırma](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))\
.NET Framework güvenlik, derleme bağlama ve uzaktan iletişimin nasıl yapılandırılacağını açıklar.
