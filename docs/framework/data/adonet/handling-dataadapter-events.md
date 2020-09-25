---
title: DataAdapter Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: a2c2dc71cc9e5c445fd05534dad5ad47fd66f436
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194732"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="3728d-102">DataAdapter Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="3728d-102">Handling DataAdapter Events</span></span>

<span data-ttu-id="3728d-103">ADO.NET, <xref:System.Data.Common.DataAdapter> veri kaynağındaki verilerde yapılan değişikliklere yanıt vermek için kullanabileceğiniz üç olay sunar.</span><span class="sxs-lookup"><span data-stu-id="3728d-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="3728d-104">Aşağıdaki tabloda `DataAdapter` Olaylar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3728d-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="3728d-105">Olay</span><span class="sxs-lookup"><span data-stu-id="3728d-105">Event</span></span>|<span data-ttu-id="3728d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3728d-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="3728d-107">Bir satırdaki GÜNCELLEŞTIRME, ekleme veya SILME işlemi (metotlardan birine yapılan bir çağrı ile `Update` ) başlamak üzere.</span><span class="sxs-lookup"><span data-stu-id="3728d-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="3728d-108">Bir satırdaki GÜNCELLEŞTIRME, ekleme veya SILME işlemi (metotlardan birine yapılan bir çağrı ile `Update` ) tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3728d-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="3728d-109">İşlem sırasında bir hata oluştu `Fill` .</span><span class="sxs-lookup"><span data-stu-id="3728d-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="3728d-110">RowUpdating ve RowUpdated</span><span class="sxs-lookup"><span data-stu-id="3728d-110">RowUpdating and RowUpdated</span></span>  

 <span data-ttu-id="3728d-111">`RowUpdating` , öğesinden bir satırdaki herhangi bir güncelleştirme <xref:System.Data.DataSet> veri kaynağında işlenmeden önce tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3728d-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="3728d-112">`RowUpdated` , öğesinden bir satırdaki herhangi bir güncelleştirme `DataSet` veri kaynağında işlendikten sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3728d-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="3728d-113">Sonuç olarak, güncelleştirme `RowUpdating` davranışını yapmadan önce değiştirmek, bir güncelleştirme gerçekleştiğinde, güncelleştirilmiş bir satıra yönelik bir başvuruyu sürdürmek, geçerli güncelleştirmeyi iptal etmek ve ardından bir toplu işlemin daha sonra işlenecek şekilde zamanlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3728d-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="3728d-114">`RowUpdated` , güncelleştirme sırasında oluşan hatalara ve özel durumlara yanıt vermek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3728d-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="3728d-115">Öğesine hata bilgilerini `DataSet` ve yeniden deneme mantığını ve benzerlerini de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3728d-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="3728d-116">Ve <xref:System.Data.Common.RowUpdatingEventArgs> <xref:System.Data.Common.RowUpdatedEventArgs> olaylarına geçirilen bağımsız değişkenler `RowUpdating` `RowUpdated` şunlardır: `Command` `Command` güncelleştirmeyi gerçekleştirmek için kullanılan nesneye başvuran bir özellik; `Row` `DataRow` güncelleştirilmiş bilgileri içeren nesneye başvuran bir özellik; `StatementType` ne tür bir güncelleştirme gerçekleştirilmekte olan bir özellik; `TableMapping` varsa, ve `Status` işlem işlemi.</span><span class="sxs-lookup"><span data-stu-id="3728d-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="3728d-117">`Status`Özelliği, işlem sırasında bir hata oluşup olmadığını ve isterseniz geçerli ve sonuç satırlarıyla eylemleri denetlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3728d-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="3728d-118">Olay gerçekleştiğinde, `Status` özelliği ya da değerine eşittir `Continue` `ErrorsOccurred` .</span><span class="sxs-lookup"><span data-stu-id="3728d-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="3728d-119">Aşağıdaki tabloda, `Status` güncelleştirme sırasında sonraki işlemleri denetlemek için özelliği ayarlayabileceğiniz değerler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3728d-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="3728d-120">Durum</span><span class="sxs-lookup"><span data-stu-id="3728d-120">Status</span></span>|<span data-ttu-id="3728d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3728d-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="3728d-122">Güncelleştirme işlemine devam edin.</span><span class="sxs-lookup"><span data-stu-id="3728d-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="3728d-123">Güncelleştirme işlemini iptal edin ve bir özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3728d-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="3728d-124">Geçerli satırı yoksayın ve güncelleştirme işlemine devam edin.</span><span class="sxs-lookup"><span data-stu-id="3728d-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="3728d-125">Güncelleştirme işlemini iptal edin, ancak özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="3728d-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="3728d-126">`Status`Özelliği olarak ayarlamak `ErrorsOccurred` bir özel durumun oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3728d-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="3728d-127">Özelliği istenen özel duruma ayarlayarak hangi özel durumun oluşturulmuş olduğunu denetleyebilirsiniz `Errors` .</span><span class="sxs-lookup"><span data-stu-id="3728d-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="3728d-128">İçin diğer değerlerden birini kullanmak, `Status` bir özel durumun oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="3728d-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="3728d-129">Ayrıca, `ContinueUpdateOnError` güncelleştirilmiş satırlar için hataları işlemek üzere özelliğini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3728d-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="3728d-130">`DataAdapter.ContinueUpdateOnError`İse `true` , bir satırdaki bir güncelleştirme bir özel durumla sonuçlanmışsa, özel durumun metni `RowError` belirli bir satırın bilgilerine konur ve işleme özel durum oluşturmadan devam eder.</span><span class="sxs-lookup"><span data-stu-id="3728d-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="3728d-131">Bu, bir `Update` `RowUpdated` hata ile karşılaşıldığında hatalara yanıt vermenize olanak sağlayan olaya karşılık olarak hatalara yanıt vermenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3728d-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="3728d-132">Aşağıdaki kod örneği, olay işleyicilerinin nasıl ekleneceğini ve kaldırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3728d-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="3728d-133">`RowUpdating`Olay işleyicisi, bir zaman damgasıyla silinen tüm kayıtların günlüğünü yazar.</span><span class="sxs-lookup"><span data-stu-id="3728d-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="3728d-134">`RowUpdated`Olay işleyicisi `RowError` , içindeki satırın özelliğine hata bilgilerini ekler `DataSet` , özel durumu bastırır ve işleme devam eder (davranışını yansıtma `ContinueUpdateOnError`  =  `true` ).</span><span class="sxs-lookup"><span data-stu-id="3728d-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
' Add handlers.  
AddHandler custAdapter.RowUpdating, New SqlRowUpdatingEventHandler( _  
  AddressOf OnRowUpdating)  
AddHandler custAdapter.RowUpdated, New SqlRowUpdatedEventHandler(  
  AddressOf OnRowUpdated)  
  
' Set DataAdapter command properties, fill DataSet, and modify DataSet.  
  
custAdapter.Update(custDS, "Customers")  
  
' Remove handlers.  
RemoveHandler custAdapter.RowUpdating, _  
  New SqlRowUpdatingEventHandler(AddressOf OnRowUpdating)  
RemoveHandler custAdapter.RowUpdated, _  
  New SqlRowUpdatedEventHandler(AddressOf OnRowUpdated)  
  
Private Shared Sub OnRowUpdating(sender As Object, _  
  args As SqlRowUpdatingEventArgs)  
  If args.StatementType = StatementType.Delete Then  
    Dim tw As System.IO.TextWriter = _  
  System.IO.File.AppendText("Deletes.log")  
    tw.WriteLine( _  
      "{0}: Customer {1} Deleted.", DateTime.Now, args.Row(_  
      "CustomerID", DataRowVersion.Original))  
    tw.Close()  
  End If  
End Sub  
  
Private Shared Sub OnRowUpdated( _  
  sender As Object, args As SqlRowUpdatedEventArgs)  
  If args.Status = UpdateStatus.ErrorsOccurred  
    args.Status = UpdateStatus.SkipCurrentRow  
    args.Row.RowError = args.Errors.Message  
  End If  
End Sub  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
// Add handlers.  
custAdapter.RowUpdating += new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
// Set DataAdapter command properties, fill DataSet, modify DataSet.  
  
custAdapter.Update(custDS, "Customers");  
  
// Remove handlers.  
custAdapter.RowUpdating -= new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated -= new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
protected static void OnRowUpdating(  
  object sender, SqlRowUpdatingEventArgs args)  
{  
  if (args.StatementType == StatementType.Delete)  
  {  
    System.IO.TextWriter tw = System.IO.File.AppendText("Deletes.log");  
    tw.WriteLine(  
      "{0}: Customer {1} Deleted.", DateTime.Now,
       args.Row["CustomerID", DataRowVersion.Original]);  
    tw.Close();  
  }  
}  
  
protected static void OnRowUpdated(  
  object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.Status == UpdateStatus.ErrorsOccurred)  
  {  
    args.Row.RowError = args.Errors.Message;  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="fillerror"></a><span data-ttu-id="3728d-135">FillError</span><span class="sxs-lookup"><span data-stu-id="3728d-135">FillError</span></span>  

 <span data-ttu-id="3728d-136">`DataAdapter` `FillError` İşlem sırasında bir hata oluştuğunda olayı yayınlar `Fill` .</span><span class="sxs-lookup"><span data-stu-id="3728d-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="3728d-137">Bu tür bir hata genellikle, eklenmekte olan satırdaki veriler bir duyarlık kaybı olmadan bir .NET Framework türüne dönüştürülemiyorsa oluşur.</span><span class="sxs-lookup"><span data-stu-id="3728d-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="3728d-138">İşlem sırasında bir hata oluşursa `Fill` , geçerli satır öğesine eklenmez `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="3728d-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="3728d-139">`FillError`Olay, hatayı çözmenize ve satırı eklemenize, ya da dışlanan satırı yoksaymanızı ve işleme devam etmenizi sağlar `Fill` .</span><span class="sxs-lookup"><span data-stu-id="3728d-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="3728d-140">`FillErrorEventArgs`Olaya geçilen, `FillError` hatalara yanıt vermenize ve bunları çözmenize olanak sağlayan çeşitli özellikler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3728d-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="3728d-141">Aşağıdaki tabloda nesnesinin özellikleri gösterilmektedir `FillErrorEventArgs` .</span><span class="sxs-lookup"><span data-stu-id="3728d-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="3728d-142">Özellik</span><span class="sxs-lookup"><span data-stu-id="3728d-142">Property</span></span>|<span data-ttu-id="3728d-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3728d-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="3728d-144">`Exception`Bu oluştu.</span><span class="sxs-lookup"><span data-stu-id="3728d-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="3728d-145">`DataTable`Hata oluştuğunda Doldurulmakta olan nesne.</span><span class="sxs-lookup"><span data-stu-id="3728d-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="3728d-146">Hata oluştuğunda eklenmekte olan satırın değerlerini içeren bir nesne dizisi.</span><span class="sxs-lookup"><span data-stu-id="3728d-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="3728d-147">Dizinin sıralı başvuruları, `Values` eklenmekte olan satır sütunlarının sıralı başvurularına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3728d-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="3728d-148">Örneğin, `Values[0]` satırın ilk sütunu olarak eklenmekte olan değerdir.</span><span class="sxs-lookup"><span data-stu-id="3728d-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="3728d-149">Bir özel durum oluşturulup oluşturulmayacağını seçmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3728d-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="3728d-150">`Continue`Özelliği olarak ayarlamak `false` geçerli `Fill` işlemi durdurur ve bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3728d-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="3728d-151">`Continue` `true` Hataya rağmen işleme devam etmek için ayarlama `Fill` .</span><span class="sxs-lookup"><span data-stu-id="3728d-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="3728d-152">Aşağıdaki kod örneği, olayı için bir olay işleyicisi ekler `FillError` `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="3728d-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="3728d-153">`FillError`Olay kodunda örnek, özel duruma yanıt verme fırsatı sağlayarak duyarlık kaybı için olası olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="3728d-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
```vb  
AddHandler adapter.FillError, New FillErrorEventHandler( _  
  AddressOf FillError)  
  
Dim dataSet As DataSet = New DataSet  
adapter.Fill(dataSet, "ThisTable")  
  
Private Shared Sub FillError(sender As Object, _  
  args As FillErrorEventArgs)  
  If args.Errors.GetType() Is Type.GetType("System.OverflowException") Then  
    ' Code to handle precision loss.  
    ' Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(New Object() _  
      {args.Values(0), args.Values(1), DBNull.Value})  
    ' Set the RowError containing the value for the third column.  
    myRow.RowError = _  
      "OverflowException encountered. Value from data source: " & _  
      args.Values(2)  
    args.Continue = True  
  End If  
End Sub  
```  
  
```csharp  
adapter.FillError += new FillErrorEventHandler(FillError);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "ThisTable");  
  
protected static void FillError(object sender, FillErrorEventArgs args)  
{  
  if (args.Errors.GetType() == typeof(System.OverflowException))  
  {  
    // Code to handle precision loss.  
    //Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(new object[]  
       {args.Values[0], args.Values[1], DBNull.Value});  
    //Set the RowError containing the value for the third column.  
    myRow.RowError =
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3728d-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3728d-154">See also</span></span>

- [<span data-ttu-id="3728d-155">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="3728d-155">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="3728d-156">DataSet Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="3728d-156">Handling DataSet Events</span></span>](./dataset-datatable-dataview/handling-dataset-events.md)
- [<span data-ttu-id="3728d-157">DataTable Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="3728d-157">Handling DataTable Events</span></span>](./dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="3728d-158">Olaylar</span><span class="sxs-lookup"><span data-stu-id="3728d-158">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="3728d-159">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3728d-159">ADO.NET Overview</span></span>](ado-net-overview.md)
