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
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="53c01-102">DataSet’e Var Olan Kısıtlamaları Ekleme</span><span class="sxs-lookup"><span data-stu-id="53c01-102">Adding Existing Constraints to a DataSet</span></span>

<span data-ttu-id="53c01-103">**DataAdapter** 'ın **fill** yöntemi bir <xref:System.Data.DataSet> yalnızca bir veri kaynağından tablo sütunları ve satırlarıyla doldurur; kısıtlamalar genellikle veri kaynağı tarafından ayarlanmış olsa da **Fill** yöntemi bu şema bilgilerini varsayılan olarak **veri kümesine** eklemez.</span><span class="sxs-lookup"><span data-stu-id="53c01-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="53c01-104">Bir veri **kümesini** bir veri kaynağından mevcut birincil anahtar kısıtlaması bilgileriyle doldurmak Için, **DataAdapter**'ın **FillSchema** metodunu çağırabilir ya da **DataAdapter** 'ın **MissingSchemaAction** özelliğini ayarlayabilirsiniz **Fill**çağrılmadan önce **AddWithKey** 'e.</span><span class="sxs-lookup"><span data-stu-id="53c01-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="53c01-105">Bu, veri **kümesindeki** birincil anahtar kısıtlamalarının veri kaynağında olanları yansıttığından emin olur.</span><span class="sxs-lookup"><span data-stu-id="53c01-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="53c01-106">Yabancı anahtar kısıtlama bilgileri dahil değildir ve [DataTable kısıtlamalarında](./dataset-datatable-dataview/datatable-constraints.md)gösterildiği gibi açık bir şekilde oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="53c01-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](./dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
<span data-ttu-id="53c01-107">Verilerle doldurulmadan önce şema bilgilerini bir veri **kümesine** eklemek, birincil anahtar kısıtlamalarının veri **kümesindeki**<xref:System.Data.DataTable> nesnelerine dahil edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="53c01-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="53c01-108">Sonuç olarak, veri **kümesini** dolduracak ek çağrılar yapıldığında, birincil anahtar sütun bilgileri her **DataTable**'daki geçerli satırlarla veri kaynağındaki yeni satırları eşleştirmek için kullanılır ve tablolardaki güncel verilerin üzerine yazılır. veri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="53c01-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="53c01-109">Şema bilgileri olmadan veri kaynağındaki yeni satırlar veri **kümesine**eklenir ve yinelenen satırlara yol açar.</span><span class="sxs-lookup"><span data-stu-id="53c01-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53c01-110">Bir veri kaynağındaki sütun otomatik artırma, **FillSchema** yöntemi veya WITH **AddWithKey**Için bir **MissingSchemaAction** Ile **Fill** yöntemi olarak tanımlanmışsa, **AutoIncrement** özelliği ile bir **DataColumn** oluşturur `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="53c01-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="53c01-111">Ancak, **oto ıncrementstep** ve **oto ıncrementseed** değerlerini kendiniz ayarlamanız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="53c01-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="53c01-112">Sütunları otomatik artırma hakkında daha fazla bilgi için bkz. [AutoIncrement sütunları oluşturma](./dataset-datatable-dataview/creating-autoincrement-columns.md).</span><span class="sxs-lookup"><span data-stu-id="53c01-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](./dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
<span data-ttu-id="53c01-113">**FillSchema** kullanmak veya **MissingSchemaAction** 'ı **AddWithKey** olarak ayarlamak, birincil anahtar sütun bilgilerini belirlemede veri kaynağında fazladan işlem yapılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="53c01-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="53c01-114">Bu ek işlem performansı azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="53c01-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="53c01-115">Tasarım zamanında birincil anahtar bilgilerini biliyorsanız, en iyi performansı elde etmek için birincil anahtar sütununu veya sütunları açıkça belirtmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="53c01-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="53c01-116">Bir tabloya yönelik birincil anahtar bilgilerini açıkça ayarlama hakkında daha fazla bilgi için bkz. [birincil anahtarları tanımlama](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="53c01-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>
  
<span data-ttu-id="53c01-117">Aşağıdaki kod örneği, **FillSchema**kullanarak bir **veri kümesine** şema bilgilerinin nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="53c01-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**:</span></span>
  
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
  
<span data-ttu-id="53c01-118">Aşağıdaki kod örneği, **Fill** yönteminin **MissingSchemaAction. AddWithKey** özelliğini kullanarak bir **veri kümesine** şema bilgilerinin nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="53c01-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method:</span></span>
  
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
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="53c01-119">Birden çok sonuç kümesini işleme</span><span class="sxs-lookup"><span data-stu-id="53c01-119">Handling multiple result sets</span></span>  

<span data-ttu-id="53c01-120">**DataAdapter** , **SelectCommand**'ten döndürülen birden çok sonuç kümesiyle karşılaşırsa, **veri kümesinde**birden çok tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53c01-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="53c01-121">Tablolar, "Table0" yerine **tablo** ile **başlayarak tablo** *N*' nin sıfır tabanlı artımlı varsayılan adı olarak verilecek.</span><span class="sxs-lookup"><span data-stu-id="53c01-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="53c01-122">Bir tablo adı **FillSchema** yöntemine bir bağımsız değişken olarak geçirilirse, tablolara "TableName0" yerine **TableName** ile başlayarak **TableName** *N*'nin sıfır tabanlı artımlı adı verilir.</span><span class="sxs-lookup"><span data-stu-id="53c01-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53c01-123">Birden çok sonuç kümesi döndüren bir komut için **OleDbDataAdapter** nesnesinin **FillSchema** yöntemi çağrılırsa, yalnızca ilk sonuç kümesinden şema bilgisi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="53c01-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="53c01-124">**OleDbDataAdapter**kullanarak birden çok sonuç kümesi için şema bilgilerini döndürürken, **AddWithKey** Için bir **MissingSchemaAction** belirtmeniz ve **dolguyu** çağırırken şema bilgilerini edinmeniz önerilir yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="53c01-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53c01-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53c01-125">See also</span></span>

- [<span data-ttu-id="53c01-126">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="53c01-126">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="53c01-127">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="53c01-127">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="53c01-128">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="53c01-128">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="53c01-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="53c01-129">ADO.NET Overview</span></span>](ado-net-overview.md)
