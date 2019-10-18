---
title: DataSet’e Var Olan Kısıtlamaları Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 267d6489d39f86fc06b35de8cf30dad74f501b0b
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523241"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>DataSet’e Var Olan Kısıtlamaları Ekleme

**DataAdapter** 'ın **fill** yöntemi bir <xref:System.Data.DataSet> yalnızca bir veri kaynağından tablo sütunları ve satırlarıyla doldurur; kısıtlamalar genellikle veri kaynağı tarafından ayarlanmış olsa da **Fill** yöntemi bu şema bilgilerini varsayılan olarak **veri kümesine** eklemez. Bir veri **kümesini** bir veri kaynağından mevcut birincil anahtar kısıtlaması bilgileriyle doldurmak Için, **DataAdapter**'ın **FillSchema** metodunu çağırabilir ya da **DataAdapter** 'ın **MissingSchemaAction** özelliğini ayarlayabilirsiniz **Fill**çağrılmadan önce **AddWithKey** 'e. Bu, veri **kümesindeki** birincil anahtar kısıtlamalarının veri kaynağında olanları yansıttığından emin olur. Yabancı anahtar kısıtlama bilgileri dahil değildir ve [DataTable kısıtlamalarında](./dataset-datatable-dataview/datatable-constraints.md)gösterildiği gibi açık bir şekilde oluşturulmalıdır.  
  
Verilerle doldurulmadan önce şema bilgilerini bir veri **kümesine** eklemek, birincil anahtar kısıtlamalarının veri **kümesindeki**<xref:System.Data.DataTable> nesnelerine dahil edilmesini sağlar. Sonuç olarak, veri **kümesini** dolduracak ek çağrılar yapıldığında, birincil anahtar sütun bilgileri her **DataTable**'daki geçerli satırlarla veri kaynağındaki yeni satırları eşleştirmek için kullanılır ve tablolardaki güncel verilerin üzerine yazılır. veri kaynağı. Şema bilgileri olmadan veri kaynağındaki yeni satırlar veri **kümesine**eklenir ve yinelenen satırlara yol açar.  
  
> [!NOTE]
> Bir veri kaynağındaki sütun otomatik artırma, **FillSchema** yöntemi veya WITH **AddWithKey**Için bir **MissingSchemaAction** Ile **Fill** yöntemi olarak tanımlanmışsa, **AutoIncrement** özelliği ile bir **DataColumn** oluşturur `true` olarak ayarlayın. Ancak, **oto ıncrementstep** ve **oto ıncrementseed** değerlerini kendiniz ayarlamanız gerekecektir. Sütunları otomatik artırma hakkında daha fazla bilgi için bkz. [AutoIncrement sütunları oluşturma](./dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
**FillSchema** kullanmak veya **MissingSchemaAction** 'ı **AddWithKey** olarak ayarlamak, birincil anahtar sütun bilgilerini belirlemede veri kaynağında fazladan işlem yapılmasını gerektirir. Bu ek işlem performansı azaltabilir. Tasarım zamanında birincil anahtar bilgilerini biliyorsanız, en iyi performansı elde etmek için birincil anahtar sütununu veya sütunları açıkça belirtmenizi öneririz. Bir tabloya yönelik birincil anahtar bilgilerini açıkça ayarlama hakkında daha fazla bilgi için bkz. [birincil anahtarları tanımlama](./dataset-datatable-dataview/defining-primary-keys.md).
  
Aşağıdaki kod örneği, **FillSchema**kullanarak bir **veri kümesine** şema bilgilerinin nasıl ekleneceğini göstermektedir:
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
Aşağıdaki kod örneği, **Fill** yönteminin **MissingSchemaAction. AddWithKey** özelliğini kullanarak bir **veri kümesine** şema bilgilerinin nasıl ekleneceğini göstermektedir:
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a>Birden çok sonuç kümesini işleme  

**DataAdapter** , **SelectCommand**'ten döndürülen birden çok sonuç kümesiyle karşılaşırsa, **veri kümesinde**birden çok tablo oluşturur. Tablolar, "Table0" yerine **tablo** ile **başlayarak tablo** *N*' nin sıfır tabanlı artımlı varsayılan adı olarak verilecek. Bir tablo adı **FillSchema** yöntemine bir bağımsız değişken olarak geçirilirse, tablolara "TableName0" yerine **TableName** ile başlayarak **TableName** *N*'nin sıfır tabanlı artımlı adı verilir.  
  
> [!NOTE]
> Birden çok sonuç kümesi döndüren bir komut için **OleDbDataAdapter** nesnesinin **FillSchema** yöntemi çağrılırsa, yalnızca ilk sonuç kümesinden şema bilgisi döndürülür. **OleDbDataAdapter**kullanarak birden çok sonuç kümesi için şema bilgilerini döndürürken, **AddWithKey** Için bir **MissingSchemaAction** belirtmeniz ve **dolguyu** çağırırken şema bilgilerini edinmeniz önerilir yöntemidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [DataSets, DataTables ve DataViews](./dataset-datatable-dataview/index.md)
- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
