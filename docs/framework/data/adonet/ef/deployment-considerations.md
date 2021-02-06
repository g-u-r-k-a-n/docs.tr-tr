---
description: 'Daha fazla bilgi edinin: dağıtım konuları (Entity Framework)'
title: Dağıtım değerlendirmeleri (Entity Framework)
ms.date: 03/30/2017
ms.assetid: 3a847a22-4eb8-4565-b18b-453bbca070db
ms.openlocfilehash: 8dc8212736c6eb8cddbb5a6d88ae7c30c5304f06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651008"
---
# <a name="deployment-considerations-entity-framework"></a>Dağıtım değerlendirmeleri (Entity Framework)

Bu konuda, veri erişimi için ADO.NET Entity Framework kullanan uygulamaları dağıtma hakkında bilgi sağlanır. Entity Framework hakkında daha fazla bilgi için bkz. [Başlarken.](getting-started.md)  
  
 Entity Framework, ile tümleşen bir araç kümesi sağlar ve Visual Studio 'da geliştirmeyi kolaylaştırır. Daha fazla bilgi için bkz. [ADO.NET varlık veri modeli araçları](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)). Bu konu, Entity Framework tabanlı bir uygulama dağıtmak için belirli teknolojilerin nasıl kullanılacağını tanımlamaz.  
  
 Visual Studio, ClickOnce dağıtımı gibi uygulamaların dağıtılması ve dağıtılması için tesis sağlar. Daha fazla bilgi için bkz. Visual Studio belgelerindeki [Uygulamaları ve bileşenleri dağıtma](/visualstudio/deployment/deploying-applications-services-and-components) .  
  
 Entity Framework kullanan bir uygulamayı dağıtırken aşağıdaki noktalar geçerlidir:  
  
- Entity Framework, .NET Framework 3,5 hizmet paketi 1 ' den (SP1) başlayarak .NET Framework bir bileşenidir. Entity Framework tabanlı bir uygulama dağıtımında .NET Framework 3,5 SP1 veya sonraki bir sürümün yüklü olduğundan emin olmanız gerekir.  
  
- Varlık Veri Modeli Sihirbazı tarafından kavramsal bir model oluşturulduğunda, uygulama yapılandırma dosyasında bir bağlantı dizesi oluşturulur. Model ve eşleme dosyaları uygulama kaynakları olarak gömülebilir veya çıkış dizinine kopyalanabilirler. Varsayılan olarak, katıştırılmış uygulama kaynakları olarak dağıtılır. `Metadata Artifact Processing`Bu seçeneklerden birini belirlemek için Entity Desisgner dosyasının özelliğini kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: model kopyalama ve dosyaları çıkış dizinine eşleme](/previous-versions/dotnet/netframework-4.0/cc716709(v=vs.100)).  
  
- Model ve eşleme bilgilerinin (kavramsal şema tanım dili (CSDL), mağaza şeması tanım dili (SSDL) ve eşleme belirtimi dili (MSL) ile ifade edilen) uygulamayla birlikte ve bağlantı dizesi tarafından belirtilen konumda dağıtıldığından emin olun. Daha fazla bilgi için bkz. [bağlantı dizeleri](connection-strings.md).  
  
- Model ve eşleme bilgilerini uygulama kaynakları olarak eklediğinizde, kavramsal model her güncelleştirildiği zaman uygulamayı yeniden derlemeniz ve yeniden dağıtmanız gerekir.  
  
- Entity Framework, .NET Framework bir bileşeni olduğundan, .NET Framework lisans sözleşmesinin izin verdiği şekilde uygulamanızla birlikte yeniden dağıtılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Entity Framework](index.md)
- [Geliştirme ve Dağıtım Konuları](development-and-deployment-considerations.md)
