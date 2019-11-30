---
title: 'Nasıl yapılır: Entity Framework sağlayıcı ile akışları özelleştirme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: 16c3741068d19fb55d8acfd28e4f83df633b0b09
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569162"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Nasıl yapılır: Entity Framework sağlayıcı ile akışları özelleştirme (WCF Veri Hizmetleri)
WCF Veri Hizmetleri, bir varlık özelliklerinin AtomPub protokolünde tanımlı kullanılmayan öğelerle eşlenilmesi için bir veri hizmeti yanıtında atom serileştirmesini özelleştirmenize olanak sağlar. Bu konuda, Entity Framework sağlayıcısı kullanılarak bir. edmx dosyasında tanımlanan bir veri modelinde varlık türleri için eşleme özniteliklerinin nasıl tanımlanacağı gösterilmektedir. Daha fazla bilgi için bkz. [akış özelleştirmesi](feed-customization-wcf-data-services.md).  
  
 Bu konu başlığında, veri modelini içeren araç tarafından oluşturulan. edmx dosyasını el ile değiştirirsiniz. Veri modeli uzantıları Entity Desisgner tarafından desteklenmediğinden dosyayı el ile değiştirmeniz gerekir. Varlık Veri Modeli araçlarının üretmesindeki. edmx dosyası hakkında daha fazla bilgi için bkz. [. edmx dosyasına genel bakış (Entity Framework)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)). Bu konudaki örnek, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıflarını kullanır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Northwind. edmx dosyasını akış özelleştirme öznitelikleri eklemek üzere el ile değiştirmek için  
  
1. **Çözüm Gezgini**, `Northwind.edmx` dosyasına sağ tıklayın ve ardından **birlikte Aç**' a tıklayın.  
  
2. **Birlikte Aç-Northwind. edmx** iletişim kutusunda, **XML Düzenleyicisi**' ni seçin ve ardından **Tamam**' a tıklayın.  
  
3. `ConceptualModels` öğesini bulun ve mevcut `Customers` varlık türünü, akış özelleştirmesi eşleme özniteliklerini içeren aşağıdaki öğeyle değiştirin:  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4. Değişiklikleri kaydedin ve Northwind. edmx dosyasını kapatın.  
  
5. Seçim Northwind. edmx dosyasına sağ tıklayın ve ardından **özel araç Çalıştır**' a tıklayın.  
  
     Bu, gerekli olabilecek nesne katmanı dosyasını yeniden oluşturur.  
  
6. Projeyi yeniden derleyin.  
  
## <a name="example"></a>Örnek  
 Önceki örnekte URI `http://myservice/Northwind.svc/Customers('ALFKI')`için aşağıdaki sonuç döndürülür.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework Sağlayıcısı](entity-framework-provider-wcf-data-services.md)
