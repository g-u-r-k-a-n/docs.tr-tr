---
title: Satır Durumları ve Satır Sürümleri
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 1b80ae78fad22989f99fb1e992d4978a192e0c66
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204534"
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="27423-102">Satır Durumları ve Satır Sürümleri</span><span class="sxs-lookup"><span data-stu-id="27423-102">Row States and Row Versions</span></span>

<span data-ttu-id="27423-103">ADO.NET satır durumlarını ve sürümlerini kullanarak tablolardaki satırları yönetir.</span><span class="sxs-lookup"><span data-stu-id="27423-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="27423-104">Satır durumu bir satırın durumunu belirtir; satır sürümleri, geçerli, orijinal ve varsayılan değerleri de dahil olmak üzere, değiştirildiğinde bir satırda depolanan değerleri korur.</span><span class="sxs-lookup"><span data-stu-id="27423-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="27423-105">Örneğin, bir satırdaki bir sütunda değişiklik yaptıktan sonra, satırda satır durumu `Modified` ve iki satır sürümü vardır: `Current` , geçerli satır değerlerini içeren ve `Original` sütun değiştirilmeden önce satır değerlerini içeren.</span><span class="sxs-lookup"><span data-stu-id="27423-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="27423-106">Her <xref:System.Data.DataRow> nesnenin, <xref:System.Data.DataRow.RowState%2A> satırın geçerli durumunu belirleyebilmek için incelemenize olanak tanıyan bir özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="27423-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="27423-107">Aşağıdaki tabloda her bir numaralandırma değerinin kısa bir açıklaması verilmiştir `RowState` .</span><span class="sxs-lookup"><span data-stu-id="27423-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="27423-108">RowState değeri</span><span class="sxs-lookup"><span data-stu-id="27423-108">RowState value</span></span>|<span data-ttu-id="27423-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27423-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="27423-110">`AcceptChanges`Satır oluşturulduğu veya bu yana yapılan son çağrıdan bu yana hiçbir değişiklik yapılmadı `DataAdapter.Fill` .</span><span class="sxs-lookup"><span data-stu-id="27423-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="27423-111">Satır tabloya eklenmiş, ancak `AcceptChanges` çağrılmadı.</span><span class="sxs-lookup"><span data-stu-id="27423-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="27423-112">Satırın bazı öğeleri değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="27423-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="27423-113">Satır bir tablodan silindi ve `AcceptChanges` çağrılmadı.</span><span class="sxs-lookup"><span data-stu-id="27423-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="27423-114">Satır herhangi bir parçası değil `DataRowCollection` .</span><span class="sxs-lookup"><span data-stu-id="27423-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="27423-115">`RowState`Yeni oluşturulan satırın ' i olarak ayarlanır `Detached` .</span><span class="sxs-lookup"><span data-stu-id="27423-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="27423-116">`DataRow`Yöntemi çağırarak yeni öğesine eklendikten sonra `DataRowCollection` `Add` `RowState` özelliğin değeri olarak ayarlanır `Added` .</span><span class="sxs-lookup"><span data-stu-id="27423-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="27423-117">`Detached` , `DataRowCollection` yöntemi kullanılarak veya yöntemi tarafından izlenen bir satır için de ayarlanır `Remove` `Delete` `AcceptChanges` .</span><span class="sxs-lookup"><span data-stu-id="27423-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="27423-118">`AcceptChanges`,, Veya üzerinde çağrıldığında <xref:System.Data.DataSet> , <xref:System.Data.DataTable> <xref:System.Data.DataRow> satır durumu olan tüm satırlar `Deleted` kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="27423-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="27423-119">Kalan satırlara satır durumu verilir `Unchanged` ve satır sürümündeki değerlerin satır `Original` `Current` sürümü değerleriyle üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="27423-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="27423-120">`RejectChanges`Çağrıldığında, satır durumu olan tüm satırlar `Added` kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="27423-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="27423-121">Kalan satırlara satır durumu verilir `Unchanged` ve satır sürümündeki değerlerin satır `Current` `Original` sürümü değerleriyle üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="27423-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="27423-122"><xref:System.Data.DataRowVersion>Aşağıdaki örnekte gösterildiği gibi, sütun başvurusuyla bir parametre geçirerek bir satırın farklı satır sürümlerini görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27423-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="27423-123">Aşağıdaki tabloda her bir numaralandırma değerinin kısa bir açıklaması verilmiştir `DataRowVersion` .</span><span class="sxs-lookup"><span data-stu-id="27423-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="27423-124">DataRowVersion değeri</span><span class="sxs-lookup"><span data-stu-id="27423-124">DataRowVersion value</span></span>|<span data-ttu-id="27423-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27423-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="27423-126">Satır için geçerli değerler.</span><span class="sxs-lookup"><span data-stu-id="27423-126">The current values for the row.</span></span> <span data-ttu-id="27423-127">Bu satır sürümü, içeren satırlar için mevcut değil `RowState` `Deleted` .</span><span class="sxs-lookup"><span data-stu-id="27423-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="27423-128">Belirli bir satır için varsayılan satır sürümü.</span><span class="sxs-lookup"><span data-stu-id="27423-128">The default row version for a particular row.</span></span> <span data-ttu-id="27423-129">`Added`, `Modified` , Veya satırı için varsayılan satır sürümü `Deleted` `Current` .</span><span class="sxs-lookup"><span data-stu-id="27423-129">The default row version for an `Added`, `Modified`, or `Deleted` row is `Current`.</span></span> <span data-ttu-id="27423-130">Bir satırın varsayılan satır sürümü `Detached` `Proposed` .</span><span class="sxs-lookup"><span data-stu-id="27423-130">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="27423-131">Satır için özgün değerler.</span><span class="sxs-lookup"><span data-stu-id="27423-131">The original values for the row.</span></span> <span data-ttu-id="27423-132">Bu satır sürümü, içeren satırlar için mevcut değil `RowState` `Added` .</span><span class="sxs-lookup"><span data-stu-id="27423-132">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="27423-133">Satır için önerilen değerler.</span><span class="sxs-lookup"><span data-stu-id="27423-133">The proposed values for the row.</span></span> <span data-ttu-id="27423-134">Bu satır sürümü bir satırdaki düzenleme işlemi sırasında veya bir parçası olmayan bir satır için mevcuttur `DataRowCollection` .</span><span class="sxs-lookup"><span data-stu-id="27423-134">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="27423-135">`DataRow` <xref:System.Data.DataRow.HasVersion%2A> Yöntemini çağırarak ve bir bağımsız değişken olarak geçirerek, bir 'nin belirli bir satır sürümüne sahip olup olmadığını test edebilirsiniz `DataRowVersion` .</span><span class="sxs-lookup"><span data-stu-id="27423-135">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="27423-136">Örneğin, `DataRow.HasVersion(DataRowVersion.Original)` `false` çağrılmadan önce yeni eklenen satırlara dönecektir `AcceptChanges` .</span><span class="sxs-lookup"><span data-stu-id="27423-136">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="27423-137">Aşağıdaki kod örneği, bir tablonun silinen tüm satırlarındaki değerleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="27423-137">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="27423-138">`Deleted` satırların bir `Current` satır sürümü olmadığından, sütun değerlerine erişirken geçiş yapmanız gerekir `DataRowVersion.Original` .</span><span class="sxs-lookup"><span data-stu-id="27423-138">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="27423-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27423-139">See also</span></span>

- [<span data-ttu-id="27423-140">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="27423-140">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="27423-141">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="27423-141">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="27423-142">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="27423-142">DataAdapters and DataReaders</span></span>](../dataadapters-and-datareaders.md)
- [<span data-ttu-id="27423-143">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="27423-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
