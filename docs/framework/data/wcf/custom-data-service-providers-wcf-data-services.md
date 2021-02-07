---
description: 'Daha fazla bilgi edinin: özel veri hizmeti sağlayıcıları (WCF Veri Hizmetleri)'
title: Özel veri hizmeti sağlayıcıları (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
ms.openlocfilehash: df0cafae46cfdbd71a96341686a9200f032a9938
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766159"
---
# <a name="custom-data-service-providers-wcf-data-services"></a>Özel veri hizmeti sağlayıcıları (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Veri Hizmetleri, geç bağlanan veri türlerine göre bir veri modeli tanımlamanızı sağlayan bir dizi sağlayıcı içerir.  
  
|Sağlayıcı|Description|  
|--------------|-----------------|  
|Meta veri sağlayıcısı|Bu, arabirimi uygulayarak çalışma zamanında özel bir veri modeli tanımlamanızı sağlayan temel özel veri hizmeti sağlayıcısıdır <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> .|  
|Sorgu sağlayıcısı|Bu sağlayıcı, arabirimi kullanılarak tanımlanan özel bir veri modeline karşı sorguları yürütmenizi sağlar <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> . Sorgu sağlayıcısı, arabirimini uygulayarak oluşturulur <xref:System.Data.Services.Providers.IDataServiceQueryProvider> .|  
|Güncelleştirme sağlayıcısı|Bu sağlayıcı, özel bir veri hizmeti sağlayıcısında sunulan türlerde güncelleştirmeler yapmanızı ve eşzamanlılık yönetimini yapmanızı sağlar. Arabirim uygulama tarafından bir güncelleştirme sağlayıcısı oluşturulur <xref:System.Data.Services.Providers.IDataServiceUpdateProvider>|  
|Sayfalama sağlayıcısı|Bu sağlayıcı, sunucu odaklı disk belleği desteğini etkinleştirmek için özel veri hizmeti sağlayıcısıyla birlikte kullanılır. Özel veri hizmeti için bir sayfalama sağlayıcısı, arabirimi uygulayarak oluşturulur <xref:System.Data.Services.Providers.IDataServicePagingProvider> .|  
|Akış sağlayıcısı|Bu sağlayıcı, ikili büyük nesne veri türlerini akış olarak kullanıma sunmanızı sağlar. Bir akış sağlayıcısı, arabirimi uygulayarak oluşturulur <xref:System.Data.Services.Providers.IDataServiceStreamProvider> . Akış sağlayıcısı ayrıca Entity Framework ve yansıma veri kaynağı sağlayıcılarıyla birlikte kullanılabilir. Daha fazla bilgi için bkz. [Akış sağlayıcısı](streaming-provider-wcf-data-services.md).|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
- [Entity Framework Sağlayıcısı](entity-framework-provider-wcf-data-services.md)
- [Yansıma Sağlayıcısı](reflection-provider-wcf-data-services.md)
