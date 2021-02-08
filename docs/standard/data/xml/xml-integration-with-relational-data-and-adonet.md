---
description: 'Hakkında daha fazla bilgi edinin: Ilişkisel verilerle XML tümleştirmesi ve ADO.NET'
title: İlişkisel Veriler ve ADO.NET ile XML Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: f6ebb1a1-f2ca-49b9-92c9-0150940cf6e6
ms.openlocfilehash: 324142861de0b2018199f15ad5de7d3fe3654768
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782747"
---
# <a name="xml-integration-with-relational-data-and-adonet"></a>İlişkisel Veriler ve ADO.NET ile XML Tümleştirmesi

**XmlDataDocument** sınıfı, **XmlDocument**'ın TÜRETILMIŞ bir sınıfıdır ve XML verisi içerir. **XmlDataDocument** 'in avantajı, ilişkisel ve hiyerarşik veriler arasında bir köprü sağlar. Bu, bir **veri kümesine** bağlanabilen ve iki sınıfta bulunan veriler üzerinde yapılan değişiklikleri eşitleyebileceğiniz bir **XmlDocument** . Bir **veri kümesine** bağlanan bir **XmlDocument** , XML 'nin ilişkisel verilerle tümleştirilmesine olanak tanır ve verilerinizin XML veya ilişkisel biçimde temsil edilebilmesi gerekmez. Her ikisini de yapabilirsiniz ve verilerin tek bir gösterimiyle sınırlandırmayın.  
  
 Verilerin iki görünümde kullanılabilir olmasının avantajları şunlardır:  
  
- Bir XML belgesinin yapılandırılmış bölümü bir veri kümesiyle eşleştirilebilir ve etkili bir şekilde depolanabilir, dizine alınmış ve aranabilir.  
  
- Dönüşümler, doğrulama ve gezinme, ilişkisel olarak depolanan XML verilerinde bir imleç modeli aracılığıyla etkili bir şekilde yapılabilir. Her zaman, XML 'nin bir **XmlDocument** modelinde depolandığından, ilişkisel yapılara karşı daha etkili bir şekilde yapılabilir.  
  
- **Veri kümesi** , XML 'nin bir bölümünü saklayabilir. Diğer bir deyişle, yalnızca ilgili öğeleri ve ilgilendiğiniz öznitelikleri bir **veri kümesine** depolamak için **XPath** veya **XslTransform** kullanabilirsiniz. Buradan, değişiklikler, **XmlDataDocument**'teki daha büyük verilere yayılırken, verilerin daha küçük, filtrelenmiş bir alt kümesiyle yapılabilir.  
  
 Ayrıca, SQL Server veri **kümesine** yüklenmiş veriler üzerinde bir dönüştürme de çalıştırabilirsiniz. Diğer bir seçenek de .NET Framework sınıfları stili yönetilen WinForm ve WebForm denetimlerini bir XML giriş akışından doldurulmuş bir **veri kümesine** bağlamak olur.  
  
 Bir **XmlDataDocument** , **XslTransform**' ı desteklemeye ek olarak, ilişkisel verileri **XPath** sorguları ve doğrulama için kullanıma sunar.  Temel olarak, tüm XML Hizmetleri ilişkisel veriler üzerinden kullanılabilir ve denetim bağlama, CodeGen vb. gibi ilişkisel tesisler, XML uygunluğa ödün vermeden, yapılandırılmış bir XML projeksiyonu üzerinden kullanılabilir.  
  
 **XmlDataDocument** bir **XmlDocument** ÖĞESINDEN DEVRALıNDıĞıNDAN, W3C DOM uygulamasının bir uygulamasını sağlar. **XmlDataDocument** 'in ilişkilendirildiği ve içindeki verilerinin bir alt kümesini depoladığı olgu, bir **veri kümesi** herhangi bir şekilde bir **XmlDocument** olarak kullanımını kısıtlamaz veya değiştirmez. Bir **XmlDocument** kullanmak için yazılan kod, bir **XmlDataDocument**'e karşı değiştirilmeden çalışmaktadır. **Veri kümesi** , tabloları, sütunları, ilişkileri ve kısıtlamaları tanımlayarak aynı verilerin ilişkisel görünümünü sağlar ve tek başına, bellek içi kullanıcı veri deposudur.  
  
 Aşağıdaki çizimde XML verilerinde veri **kümesi** ve **XmlDataDocument** ile birlikte bulunan farklı ilişkilendirmeler gösterilmektedir:
  
 ![XML veri kümesiyle farklı ilişkilendirmeleri gösteren diyagram.](./media/xml-integration-with-relational-data-and-adonet/xml-integration-relational-data-adodotnet.gif)  
  
 Çizimde XML verilerinin doğrudan bir **veri kümesine** yüklenebileceği gösterilmektedir ve bu, ILIŞKISEL şekilde XML ile doğrudan işleme sağlar. Ya da, XML DOM 'ın türetilmiş bir sınıfına yüklenebilir, bu, **XmlDataDocument**' dir ve daha sonra **veri kümesiyle** yüklenip eşitlenir. **Veri kümesi ve** **XmlDataDocument** tek bir veri kümesi üzerinden eşitlendiğinden, bir depodaki verilerde yapılan değişiklikler diğer depoya yansıtılır.  
  
 **XmlDataDocument** , **XmlDocument** içindeki tüm düzen ve gezinme özelliklerini devralır. **XmlDataDocument** 'in ve devralınmış özelliklerinin kullanıldığı zamanlar, bir **veri KÜMESIYLE** eşitlendiğinde, XML 'i doğrudan **veri kümesine** yüklemeye kıyasla daha uygun bir seçenektir. Aşağıdaki tabloda, **veri kümesini** yüklemek için kullanılacak yöntemi seçerken göz önünde bulundurmanız gereken öğeler gösterilmektedir.  
  
|XML 'ı doğrudan bir veri kümesine yükleme|Bir XmlDataDocument ile bir veri kümesiyle ne zaman eşitleneceğini|  
|----------------------------------------------|-----------------------------------------------------------|  
|Veri **kümesindeki** verilerin sorguları XPath 'ten SQL kullanılarak daha kolay.|Veri **kümesindeki** veriler üzerinde XPath sorguları gerekir.|  
|Kaynak XML 'de öğe sıralamasını koruma kritik değildir.|Kaynak XML 'de öğe sıralamasını koruma kritik öneme sahiptir.|  
|Öğe ve biçimlendirme arasındaki boşluk, kaynak XML 'de korunması gerekmez.|Kaynak XML 'de boşluk ve biçimlendirme koruması kritik öneme sahiptir.|  
  
 Bir **veri kümesinin** içine ve DıŞıNA doğrudan XML yükleme ve yazma için, bkz. xml 'den veri kümesi [yükleme](../../../framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) ve [XML verisi olarak veri kümesi yazma](../../../framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).  
  
 **Veri kümesinin** bir **XmlDataDocument** 'ten yüklenmesi gereksinimlerinize göre, bkz. [XML belgesi ile veri kümesini eşitleme](../../../framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet içinde XML kullanma](../../../framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
