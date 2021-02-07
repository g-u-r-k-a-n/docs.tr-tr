---
description: Entity Framework sağlayıcısı hakkında daha fazla bilgi edinin (WCF Veri Hizmetleri)
title: Entity Framework sağlayıcısı (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 0c321ca49520c9b2957a807c01175bea8ee7ae3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766055"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Entity Framework sağlayıcısı (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Veri Hizmetleri gibi, ADO.NET Entity Framework bir varlık ilişkisi modelinin türü olan Varlık Veri Modeli temel alır. Entity Framework, işlemleri *kavramsal model* olarak adlandırılan varlık veri modeli uygulamasına karşı, bir veri kaynağına karşı eşdeğer işlemlere dönüştürür. Bu, Entity Framework ilişkisel verileri temel alan veri Hizmetleri için ideal bir sağlayıcı ve Entity Framework destekleyen bir veri sağlayıcısına sahip tüm veritabanları WCF Veri Hizmetleri ile kullanılabilir. Entity Framework desteklemekte olan veri kaynaklarının bir listesi için, bkz. [Entity Framework Providers](/ef/ef6/fundamentals/providers/).
  
 Kavramsal modelde, varlık kapsayıcısı hizmetin köküdür. Verilerin bir veri hizmeti tarafından sunukullanabilmesi için önce Entity Framework bir kavramsal model tanımlamanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: ADO.NET Entity Framework veri kaynağı kullanarak veri hizmeti oluşturma](create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
 WCF Veri Hizmetleri, bir varlık için eşzamanlılık belirteci tanımlamanızı sağlayarak iyimser eşzamanlılık modelini destekler. Varlığın bir veya daha fazla özelliği içeren bu eşzamanlılık belirteci, istenen, güncellenen veya silinen verilerde bir değişikliğin oluşup oluşmadığını anlamak için veri hizmeti tarafından kullanılır. İstekteki eTag öğesinden alınan belirteç değerleri varlığın geçerli değerlerinden farklıysa, veri hizmeti tarafından bir özel durum oluşturulur. Bir özelliğin eşzamanlılık belirtecinin bir parçası olduğunu göstermek için özniteliği `ConcurrencyMode="Fixed"` Entity Framework sağlayıcısı tarafından tanımlanan veri modeline uygulamalısınız. Eşzamanlılık belirteci bir anahtar özellik veya bir gezinti özelliği içeremez. Daha fazla bilgi için bkz. [veri hizmetini güncelleştirme](updating-the-data-service-wcf-data-services.md).  
  
 Entity Framework hakkında daha fazla bilgi edinmek için bkz. [Entity Framework genel bakış](../adonet/ef/overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
- [Yansıma Sağlayıcısı](reflection-provider-wcf-data-services.md)
- [Varlık Veri Modeli](../adonet/entity-data-model.md)
