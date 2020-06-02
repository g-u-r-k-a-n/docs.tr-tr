---
title: DataTable Oluşturma
description: Bağımsız olarak veya diğer .NET Framework nesneleri kullanarak, bir bellek içi ilişkisel veri tablosunu temsil eden ADO.NET içinde bir DataTable oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: 335137eeef02e590539c6d83e46cb39901a1e03f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286927"
---
# <a name="creating-a-datatable"></a>DataTable Oluşturma
Bir <xref:System.Data.DataTable> bellek içi ilişkisel veri tablosunu temsil eden bir tablosu, bağımsız olarak oluşturulup kullanılabilir veya diğer .NET Framework nesneleri tarafından, genellikle bir üyesi olarak kullanılabilir <xref:System.Data.DataSet> .  
  
 Uygun **DataTable** oluşturucusunu kullanarak bir **DataTable** nesnesi oluşturabilirsiniz. Bunu **DataTable** nesnesinin **Tables** koleksiyonuna eklemek Için **Add** metodunu kullanarak **veri kümesine** ekleyebilirsiniz.  
  
 Ayrıca, **DataAdapter** nesnesinin **Fill** veya **FillSchema** yöntemlerini **kullanarak veya** **veri kümesinin** **ReadXml**, **ReadXmlSchema**ya da **InferXmlSchema** yöntemlerini kullanarak önceden tanımlanmış veya Çıkarsanan xml şemasından **DataTable** nesneleri de oluşturabilirsiniz. Bir **veri kümesinin** **Tables** koleksiyonunun bir üyesi olarak bir **DataTable** ekledikten sonra, bunu başka bir **veri kümesinin**tablo koleksiyonuna ekleyemediğini unutmayın.  
  
 İlk olarak bir **DataTable**oluşturduğunuzda, bir şeması (yani bir yapı) yoktur. Tablonun şemasını tanımlamak için, nesneleri oluşturmanız ve <xref:System.Data.DataColumn> tablonun **Columns** koleksiyonuna eklemeniz gerekir. Ayrıca tablo için bir birincil anahtar sütunu tanımlayabilir ve tablonun **kısıtlamalar** koleksiyonuna **kısıtlama** nesneleri oluşturabilir ve ekleyebilirsiniz. Bir **DataTable**şemasını tanımladıktan sonra, tablodaki **satır** koleksiyonuna **DataRow** nesneleri ekleyerek tabloya veri satırları ekleyebilirsiniz.  
  
 DataTable oluştururken özellik için bir değer sağlamanız gerekmez <xref:System.Data.DataTable.TableName%2A> ; özelliği başka bir zaman belirtebilir veya **DataTable**boş bırakabilirsiniz. Ancak, bir **veri kümesine** **TableName** değeri olmayan bir tablo eklediğinizde, tabloya TABLE0 için "Table" Ile başlayarak, tablo*N*artımlı varsayılan adı verilir.  
  
> [!NOTE]
> Bir **TableName** değeri belirttiğinizde "tablo*N*" adlandırma kuralını önlemenize önerilir, çünkü sağladığınız ad **veri kümesindeki**mevcut bir varsayılan tablo adıyla çakışabilir. Sağlanan ad zaten varsa, bir özel durum oluşturulur.  
  
 Aşağıdaki örnek, bir **DataTable** nesnesinin örneğini oluşturur ve "Customers" adına atar.  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 Aşağıdaki örnek, bir **veri kümesinin** **Tables** koleksiyonuna ekleyerek bir **DataTable** örneği oluşturur.  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [DataTables](datatables.md)
- [DataAdapter’dan bir DataSet Doldurma](../populating-a-dataset-from-a-dataadapter.md)
- [XML’den DataSet Yükleme](loading-a-dataset-from-xml.md)
- [XML’den DataSet Schema Bilgilerini Yükleme](loading-dataset-schema-information-from-xml.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
