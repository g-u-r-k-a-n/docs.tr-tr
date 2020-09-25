---
title: Verileri Sıralama ve Filtreleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 89e2fdf656fb06ee545ba936f033646ad86182d4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183383"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="ab915-102">Verileri Sıralama ve Filtreleme</span><span class="sxs-lookup"><span data-stu-id="ab915-102">Sorting and Filtering Data</span></span>

<span data-ttu-id="ab915-103">, <xref:System.Data.DataView> Bir içindeki verileri sıralamak ve filtrelemek için çeşitli yollar sağlar <xref:System.Data.DataTable> :</span><span class="sxs-lookup"><span data-stu-id="ab915-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
- <span data-ttu-id="ab915-104"><xref:System.Data.DataView.Sort%2A>Özelliğini kullanarak tek veya birden çok sütun sıralama düzeni belirtebilir ve ASC (artan) ve DESC (azalan) parametreleri dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab915-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
- <span data-ttu-id="ab915-105"><xref:System.Data.DataView.ApplyDefaultSort%2A>Özelliğini, tablonun birincil anahtar sütununa veya sütunlarına göre artan sırada otomatik olarak bir sıralama düzeni oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab915-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="ab915-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> yalnızca **sıralama** özelliği null veya boş bir dize olduğunda ve tablonun tanımlı bir birincil anahtarı olduğunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ab915-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
- <span data-ttu-id="ab915-107"><xref:System.Data.DataView.RowFilter%2A>Özelliğini, sütun değerlerine göre satır alt kümelerini belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab915-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="ab915-108">**RowFilter** özelliği için geçerli ifadeler hakkında daha fazla bilgi için, sınıfının özelliği için başvuru bilgilerine bakın <xref:System.Data.DataColumn.Expression%2A> <xref:System.Data.DataColumn> .</span><span class="sxs-lookup"><span data-stu-id="ab915-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="ab915-109">Verilerin bir alt kümesinin dinamik görünümünü sağlamanın aksine veriler üzerinde belirli bir sorgunun sonuçlarını döndürmek istiyorsanız, <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> **RowFilter** özelliğini ayarlamak yerine en iyi performansı elde etmek için **DataView** 'ın veya yöntemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab915-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="ab915-110">**RowFilter** özelliğinin ayarlanması, verilerin dizinini yeniden oluşturur, uygulamanıza ek yük ekler ve performansı azaltır.</span><span class="sxs-lookup"><span data-stu-id="ab915-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="ab915-111">**RowFilter** özelliği, bir bağlantılı denetimin filtrelenmiş sonuçları görüntülediği veriye dayalı bir uygulamada en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab915-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="ab915-112">**Find** ve **FindRows** yöntemleri, dizinin yeniden oluşturulmasını gerektirmeden geçerli dizinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="ab915-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="ab915-113">**Find** ve **FindRows** yöntemleri hakkında daha fazla bilgi Için bkz. [satırları bulma](finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="ab915-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](finding-rows.md).</span></span>  
  
- <span data-ttu-id="ab915-114"><xref:System.Data.DataView.RowStateFilter%2A>Hangi satır sürümlerinin görüntüleneceği belirlemek için özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab915-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="ab915-115">**DataView** , temel alınan satırın **RowState** öğesine bağlı olarak hangi satır sürümünün sergileceğini dolaylı olarak yönetir.</span><span class="sxs-lookup"><span data-stu-id="ab915-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="ab915-116">Örneğin, **RowStateFilter** , **DataViewRowState. Deleted**olarak ayarlandıysa, **geçerli** satır sürümü bulunmadığından **DataView** , **silinen** tüm satırların **orijinal** satır sürümünü kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="ab915-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="ab915-117">**DataRowView**'ın **ROWVERSION** özelliğini kullanarak bir satırın hangi satır sürümünün gösterilmesini belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab915-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="ab915-118">Aşağıdaki tabloda, **DataViewRowState**seçenekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ab915-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="ab915-119">DataViewRowState seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ab915-119">DataViewRowState options</span></span>|<span data-ttu-id="ab915-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab915-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="ab915-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="ab915-121">**CurrentRows**</span></span>|<span data-ttu-id="ab915-122">Tüm **değişmemiş**, **eklenen**ve **değiştirilen** satırların **geçerli** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="ab915-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="ab915-123">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="ab915-123">This is the default.</span></span>|  
    |<span data-ttu-id="ab915-124">**Eklenirse**</span><span class="sxs-lookup"><span data-stu-id="ab915-124">**Added**</span></span>|<span data-ttu-id="ab915-125">Tüm **eklenen** satırların **geçerli** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="ab915-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="ab915-126">**Silindi**</span><span class="sxs-lookup"><span data-stu-id="ab915-126">**Deleted**</span></span>|<span data-ttu-id="ab915-127">**Silinen** tüm satırların **orijinal** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="ab915-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="ab915-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="ab915-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="ab915-129">**Değiştirilen** tüm satırların **geçerli** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="ab915-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="ab915-130">**Modifiedorijinal**</span><span class="sxs-lookup"><span data-stu-id="ab915-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="ab915-131">**Değiştirilen** tüm satırların **orijinal** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="ab915-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="ab915-132">**Hiçbiri**</span><span class="sxs-lookup"><span data-stu-id="ab915-132">**None**</span></span>|<span data-ttu-id="ab915-133">Satır yok.</span><span class="sxs-lookup"><span data-stu-id="ab915-133">No rows.</span></span>|  
    |<span data-ttu-id="ab915-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="ab915-134">**OriginalRows**</span></span>|<span data-ttu-id="ab915-135">Tüm **değişmemiş**, **değiştirilen**ve **silinen** satırların **orijinal** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="ab915-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="ab915-136">**Değiştirilmediği**</span><span class="sxs-lookup"><span data-stu-id="ab915-136">**Unchanged**</span></span>|<span data-ttu-id="ab915-137">**Değişmeyen** tüm satırların **geçerli** satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="ab915-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="ab915-138">Satır durumları ve satır sürümleri hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="ab915-138">For more information about row states and row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="ab915-139">Aşağıdaki kod örneği, stoktaki birim sayısının yeniden sipariş düzeyine eşit veya daha küçük olduğu, önce Tedarikçi KIMLIĞI ve ardından ürün adına göre sıralanmış tüm ürünleri gösteren bir görünüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab915-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab915-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab915-140">See also</span></span>

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="ab915-141">DataViews</span><span class="sxs-lookup"><span data-stu-id="ab915-141">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="ab915-142">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ab915-142">ADO.NET Overview</span></span>](../ado-net-overview.md)
