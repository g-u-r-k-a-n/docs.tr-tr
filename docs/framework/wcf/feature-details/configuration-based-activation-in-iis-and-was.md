---
description: "Hakkında daha fazla bilgi edinin: IIS 'de Configuration-Based etkinleştirme ve WAS"
title: IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: 7515e3f0d3035e1ab93c67980bd00eeb0a063d17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743375"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme

Normal olarak, Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (WAS) altında bir Windows Communication Foundation (WCF) hizmeti barındırdığında bir. svc dosyası sağlamanız gerekir. . Svc dosyası, hizmetin adını ve isteğe bağlı bir özel hizmet ana bilgisayar fabrikası içerir. Bu ek dosya yönetilebilirlik ek yükü ekler. Yapılandırma tabanlı etkinleştirme özelliği, gereksinimi bir. svc dosyasına ve bu nedenle ilişkili ek yüke karşı kaldırır.

## <a name="configuration-based-activation"></a>Yapılandırma Temelli Etkinleştirme

Yapılandırma tabanlı etkinleştirme,. svc dosyasına yerleştirilmesi için kullanılan meta verileri alır ve Web.config dosyasına koyar. <`serviceHostingEnvironment`> öğesi içinde <bir `serviceActivations`> öğesi vardır. <`serviceActivations`> öğesi içinde, bir veya daha fazla <`add`> öğesi, her barındırılan hizmet için bir öğedir. <`add`> öğesi, hizmet ve hizmet türü ya da hizmet ana bilgisayar fabrikası için göreli adresi ayarlamanıza olanak sağlayan öznitelikleri içerir. Aşağıdaki yapılandırma örnek kodu, bu bölümün nasıl kullanıldığını gösterir.

> [!NOTE]
> Her <`add`> öğesi bir hizmet veya bir fabrika özniteliği belirtmelidir. Hem Service hem de Factory özniteliklerinin belirtilmesine izin verilir.

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 Bu Web.config dosyasında, hizmet kaynak kodunu uygulamanın App_Code dizinine veya uygulamanın bin dizinine karmaşık bir derlemeye yerleştirebilirsiniz.

> [!NOTE]
>
> - Yapılandırma tabanlı etkinleştirme kullanılırken,. svc dosyalarında satır içi kod desteklenmez.
> - `relativeAddress`Öznitelik, " \<sub-directory> /Service.exe" veya "~/ \< Sub-Directory/Service. svc" gibi göreli bir adrese ayarlanmalıdır.
> - WCF ile ilişkili bilinen bir uzantısı olmayan göreli bir adresi kaydettiğinizde bir yapılandırma özel durumu oluşturulur.
> - Belirtilen göreli adres, sanal uygulamanın köküne göredir.
> - Yapılandırma hiyerarşik modeli nedeniyle, makine ve site düzeyindeki kayıtlı göreli adresler sanal uygulamalar tarafından devralınır.
> - Bir yapılandırma dosyasındaki kayıtlar, bir. svc,. xamlx,. xoml veya başka bir dosyanın ayarlarından önceliklidir.
> - IIS/WAS 'a gönderilen URI içindeki herhangi bir ' \ ' (ters eğik çizgi), otomatik olarak bir '/' (eğik çizgi) olarak dönüştürülür. ' \ ' İçeren bir göreli adres eklenirse ve IIS 'yi göreli adresi kullanan bir URI gönderirseniz, ters eğik çizgi eğik çizgiye dönüştürülür ve IIS onunla ilgili adresle eşleşemez. IIS, hiçbir eşleşme bulunamadığını belirten izleme bilgilerini gönderir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [Barındırma Hizmetleri](../hosting-services.md)
- [İş Akışı Hizmetlerini Barındırma Genel Bakış](hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [Windows Server App Fabric barındırma özellikleri](/previous-versions/appfabric/ee677189(v=azure.10))
