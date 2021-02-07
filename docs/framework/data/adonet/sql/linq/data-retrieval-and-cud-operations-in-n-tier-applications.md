---
description: 'Hakkında daha fazla bilgi edinin: N katmanlı uygulamalarda veri alımı ve CUD Işlemleri (LINQ to SQL)'
title: N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: dbad65e1bd29227f434166dca364946a68256177
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672172"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="b853c-103">N Katmanı Uygulamalarında Veri Alma ve CUD İşlemleri (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="b853c-103">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>

<span data-ttu-id="b853c-104">Müşteriler veya siparişler gibi varlık nesnelerini bir ağ üzerinden bir istemciye serileştirçalıştığınızda, bu varlıklar veri bağlamlarından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="b853c-104">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="b853c-105">Veri bağlamı artık yaptıkları değişiklikleri veya ilişkilerini diğer nesnelerle izlemediğinden.</span><span class="sxs-lookup"><span data-stu-id="b853c-105">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="b853c-106">Bu, istemcilerin yalnızca verileri okuduğu sürece bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="b853c-106">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="b853c-107">Ayrıca, istemcilerin bir veritabanına yeni satırlar eklemesini sağlamak oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="b853c-107">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="b853c-108">Bununla birlikte, uygulamanız, istemcilerin verileri güncelleştirebilmesini veya silmesine gerek duymalıdır, çağrı yapmadan önce varlıkları yeni bir veri bağlamına iliştirmelidir <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b853c-108">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b853c-109">Buna ek olarak, özgün değerlerle iyimser eşzamanlılık denetimi kullanıyorsanız, veritabanını hem özgün varlık hem de varlığı değiştirilmiş olarak sağlamak için bir yol gerekir.</span><span class="sxs-lookup"><span data-stu-id="b853c-109">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="b853c-110">Yöntemler, daha `Attach` sonra varlıkları kullanımdan kaldırıldıktan sonra yeni bir veri bağlamına yerleştirmeye olanak tanımak için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b853c-110">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="b853c-111">Varlıkların yerine ara sunucu nesnelerini serileştirseniz bile [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , verileri veritabanına göndermek için veri erişim katmanında (dal) bir varlık oluşturmanız ve bunu yeni bir ile bağlamanız gerekir <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b853c-111">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b853c-112">varlıkların serileştirilme şekli hakkında tamamen farklıdır.</span><span class="sxs-lookup"><span data-stu-id="b853c-112">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="b853c-113">Windows Communication Foundation (WCF) kullanılarak seri hale getirilebilir sınıflar oluşturmak için Nesne İlişkisel Tasarımcısı ve SQLMetal araçlarının nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: varlıkları seri hale getirme](how-to-make-entities-serializable.md).</span><span class="sxs-lookup"><span data-stu-id="b853c-113">For more information about how to use the Object Relational Designer and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b853c-114">Yalnızca `Attach` Yeni veya serisi kaldırılan varlıklarda Yöntemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="b853c-114">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="b853c-115">Bir varlığın özgün veri bağlamından ayrılması için tek yol, onun serileştirilmesi içindir.</span><span class="sxs-lookup"><span data-stu-id="b853c-115">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="b853c-116">Ayrılmamış bir varlığı yeni bir veri bağlamına iliştirmeye çalışırsanız ve bu varlığın önceki veri bağlamından ertelenmiş yükleyiciler varsa, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b853c-116">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="b853c-117">İki farklı veri bağlamlarından ertelenmiş yükleyicileriyle bir varlık, bu varlıkta ekleme, güncelleştirme ve silme işlemlerini gerçekleştirdiğinizde istenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b853c-117">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="b853c-118">Ertelenmiş yükleyiciler hakkında daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="b853c-118">For more information about deferred loaders, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="b853c-119">Veri alma</span><span class="sxs-lookup"><span data-stu-id="b853c-119">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="b853c-120">İstemci yöntemi çağrısı</span><span class="sxs-lookup"><span data-stu-id="b853c-120">Client Method Call</span></span>  

 <span data-ttu-id="b853c-121">Aşağıdaki örneklerde, bir Windows Forms istemcisinden DAL için örnek yöntem çağrısı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b853c-121">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="b853c-122">Bu örnekte, DAL bir Windows hizmet kitaplığı olarak uygulanır:</span><span class="sxs-lookup"><span data-stu-id="b853c-122">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
```vb  
Private Function GetProdsByCat_Click(ByVal sender As Object, ByVal e _  
    As EventArgs)  
  
    ' Create the WCF client proxy.  
    Dim proxy As New NorthwindServiceReference.Service1Client  
  
    ' Call the method on the service.  
    Dim products As NorthwindServiceReference.Product() = _  
        proxy.GetProductsByCategory(1)  
  
    ' If the database uses original values for concurrency checks,  
    ' the client needs to store them and pass them back to the  
    ' middle tier along with the new values when updating data.  
  
    For Each v As NorthwindClient1.NorthwindServiceReference.Product _  
        In products  
        ' Persist to a List(Of Product) declared at class scope.  
        ' Additional change-tracking logic is the responsibility  
        ' of the presentation tier and/or middle tier.  
        originalProducts.Add(v)  
    Next  
  
    ' (Not shown) Bind the products list to a control  
    ' and/or perform whatever processing is necessary.  
End Function  
```  
  
```csharp  
private void GetProdsByCat_Click(object sender, EventArgs e)  
{  
    // Create the WCF client proxy.  
    NorthwindServiceReference.Service1Client proxy =
    new NorthwindClient.NorthwindServiceReference.Service1Client();  
  
    // Call the method on the service.  
    NorthwindServiceReference.Product[] products =
    proxy.GetProductsByCategory(1);  
  
    // If the database uses original values for concurrency checks,
    // the client needs to store them and pass them back to the
    // middle tier along with the new values when updating data.  
    foreach (var v in products)  
    {  
        // Persist to a list<Product> declared at class scope.  
        // Additional change-tracking logic is the responsibility  
        // of the presentation tier and/or middle tier.  
        originalProducts.Add(v);  
    }  
  
    // (Not shown) Bind the products list to a control  
    // and/or perform whatever processing is necessary.  
    }  
```  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="b853c-123">Orta katman uygulama</span><span class="sxs-lookup"><span data-stu-id="b853c-123">Middle Tier Implementation</span></span>  

 <span data-ttu-id="b853c-124">Aşağıdaki örnek, Orta katmanda arabirim yönteminin bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b853c-124">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="b853c-125">Aşağıda, aklınızda iki ana işaret verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b853c-125">The following are the two main points to note:</span></span>  
  
- <span data-ttu-id="b853c-126">, <xref:System.Data.Linq.DataContext> Yöntem kapsamında bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b853c-126">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
- <span data-ttu-id="b853c-127">Yöntemi, <xref:System.Collections.IEnumerable> gerçek sonuçların bir koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b853c-127">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="b853c-128">Seri hale getirici, sonuçları istemci/sunum katmanına geri göndermek için sorguyu yürütür.</span><span class="sxs-lookup"><span data-stu-id="b853c-128">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="b853c-129">Sorgu sonuçlarına yerel olarak Orta katmanda erişmek için, `ToList` sorgu değişkenine veya öğesini çağırarak yürütmeye zorlayabilirsiniz `ToArray` .</span><span class="sxs-lookup"><span data-stu-id="b853c-129">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="b853c-130">Daha sonra, bu listeyi veya diziyi bir olarak döndürebilirsiniz `IEnumerable` .</span><span class="sxs-lookup"><span data-stu-id="b853c-130">You can then return that list or array as an `IEnumerable`.</span></span>  
  
```vb  
Public Function GetProductsByCategory(ByVal categoryID As Integer) _  
    As IEnumerable(Of Product)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    Dim productQuery = _  
    From prod In db.Products _  
    Where prod.CategoryID = categoryID _  
    Select prod  
  
    Return productQuery.AsEnumerable()  
  
End Function  
```  
  
```csharp  
public IEnumerable<Product> GetProductsByCategory(int categoryID)  
{  
    NorthwindClasses1DataContext db =
    new NorthwindClasses1DataContext(connectionString);  
  
    IEnumerable<Product> productQuery =  
    from prod in db.Products  
    where prod.CategoryID == categoryID  
    select prod;  
  
    return productQuery.AsEnumerable();
}  
```  
  
 <span data-ttu-id="b853c-131">Veri bağlamının bir örneği bir "iş birimi" süresine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b853c-131">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="b853c-132">Gevşek olarak bağlanmış bir ortamda, bir iş birimi genellikle küçük, tek bir çağrı dahil olmak üzere tek bir iyimser işlem olur `SubmitChanges` .</span><span class="sxs-lookup"><span data-stu-id="b853c-132">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="b853c-133">Bu nedenle, veri bağlamı oluşturulup Yöntem kapsamında atılmış olur.</span><span class="sxs-lookup"><span data-stu-id="b853c-133">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="b853c-134">Çalışma birimi iş kuralları mantığına çağrılar içeriyorsa, genellikle `DataContext` örneği bu bütün işlem için tutmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b853c-134">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="b853c-135">Her durumda, `DataContext` örneklerin rastgele işlem sırasında uzun süreler boyunca etkin tutulması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="b853c-135">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="b853c-136">Bu yöntem, ürün nesnelerini döndürür ancak her ürünle ilişkili Order_Detail nesnelerinin toplanmasını sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b853c-136">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="b853c-137"><xref:System.Data.Linq.DataLoadOptions>Bu varsayılan davranışı değiştirmek için nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b853c-137">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="b853c-138">Daha fazla bilgi için bkz. [nasıl yapılır: Ilgili verilerin ne kadar alındığını denetleme](how-to-control-how-much-related-data-is-retrieved.md).</span><span class="sxs-lookup"><span data-stu-id="b853c-138">For more information, see [How to: Control How Much Related Data Is Retrieved](how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="b853c-139">Veri ekleme</span><span class="sxs-lookup"><span data-stu-id="b853c-139">Inserting Data</span></span>  

 <span data-ttu-id="b853c-140">Yeni bir nesne eklemek için sunum katmanı yalnızca orta katman arabirimindeki ilgili yöntemi çağırır ve yeni nesnede eklenecek şekilde geçer.</span><span class="sxs-lookup"><span data-stu-id="b853c-140">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="b853c-141">Bazı durumlarda, istemcinin yalnızca bazı değerleri geçmesi ve ortadaki katmanın tam nesneyi oluşturmasına daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="b853c-141">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="b853c-142">Orta katman uygulama</span><span class="sxs-lookup"><span data-stu-id="b853c-142">Middle Tier Implementation</span></span>  

 <span data-ttu-id="b853c-143">Orta katmanda yeni bir <xref:System.Data.Linq.DataContext> oluşturulur, nesne <xref:System.Data.Linq.DataContext> yöntemi kullanılarak öğesine iliştirilir <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> ve çağrıldığında nesne eklenir <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .</span><span class="sxs-lookup"><span data-stu-id="b853c-143">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="b853c-144">Özel durumlar, geri çağrılar ve hata koşulları diğer Web hizmeti senaryolarında olduğu gibi işlenebilirler.</span><span class="sxs-lookup"><span data-stu-id="b853c-144">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
```vb  
' No call to Attach is necessary for inserts.  
Public Sub InsertOrder(ByVal o As Order)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    db.Orders.InsertOnSubmit(o)  
  
    ' Exception handling not shown.  
    db.SubmitChanges()  
  
End Sub  
```  
  
```csharp  
// No call to Attach is necessary for inserts.  
    public void InsertOrder(Order o)  
    {  
        NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
        db.Orders.InsertOnSubmit(o);  
  
        // Exception handling not shown.  
        db.SubmitChanges();  
    }  
```  
  
## <a name="deleting-data"></a><span data-ttu-id="b853c-145">Veri silme</span><span class="sxs-lookup"><span data-stu-id="b853c-145">Deleting Data</span></span>  

 <span data-ttu-id="b853c-146">Veritabanından varolan bir nesneyi silmek için sunum katmanı, ortadaki katman arabirimindeki ilgili yöntemi çağırır ve Silinecek nesnenin orijinal değerlerini içeren kopyasına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b853c-146">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="b853c-147">Silme işlemleri iyimser eşzamanlılık denetimleri içerir ve Silinecek nesnenin önce yeni veri bağlamına bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b853c-147">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="b853c-148">Bu örnekte, parametresi, `Boolean` `false` nesnesinin zaman damgası (rowversion) olmadığını belirtmek için olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b853c-148">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="b853c-149">Veritabanı tablonuz her kayıt için zaman damgaları üretilemez, eşzamanlılık denetimleri özellikle istemci için çok daha basittir.</span><span class="sxs-lookup"><span data-stu-id="b853c-149">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="b853c-150">Yalnızca orijinal veya değiştirilmiş nesneyi geçirin ve `Boolean` parametresini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="b853c-150">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="b853c-151">Herhangi bir durumda, Orta katmanda genellikle yakalamak gerekir <xref:System.Data.Linq.ChangeConflictException> .</span><span class="sxs-lookup"><span data-stu-id="b853c-151">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="b853c-152">İyimser eşzamanlılık çakışmalarını işleme hakkında daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b853c-152">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="b853c-153">İlişkili tablolarda yabancı anahtar kısıtlamalarına sahip varlıkları silerken, önce koleksiyonlarındaki tüm nesneleri silmeniz gerekir <xref:System.Data.Linq.EntitySet%601> .</span><span class="sxs-lookup"><span data-stu-id="b853c-153">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
```vb  
' Attach is necessary for deletes.  
Public Sub DeleteOrder(ByVal order As Order)  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
  
    db.Orders.Attach(order, False)  
    ' This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order)  
  
    Try  
        ' ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict)  
  
    Catch ex As ChangeConflictException  
        ' Get conflict information, and take actions  
        ' that are appropriate for your application.  
        ' See MSDN Article "How to: Manage Change  
        ' Conflicts (LINQ to SQL).  
  
    End Try  
End Sub  
```  
  
```csharp  
// Attach is necessary for deletes.  
public void DeleteOrder(Order order)  
{  
    NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
  
    db.Orders.Attach(order, false);  
    // This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order);  
    try  
    {  
        // ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict);  
    }  
    catch (ChangeConflictException e)  
    {  
       // Get conflict information, and take actions  
       // that are appropriate for your application.  
       // See MSDN Article How to: Manage Change Conflicts (LINQ to SQL).  
    }  
}  
```  
  
## <a name="updating-data"></a><span data-ttu-id="b853c-154">Veriler güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="b853c-154">Updating Data</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b853c-155">iyimser eşzamanlılık içeren bu senaryolarda güncelleştirmeleri destekler:</span><span class="sxs-lookup"><span data-stu-id="b853c-155">supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
- <span data-ttu-id="b853c-156">Zaman damgaları veya RowVersion numaralarına göre iyimser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="b853c-156">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
- <span data-ttu-id="b853c-157">Varlık özelliklerinin bir alt kümesinin orijinal değerlerini temel alan iyimser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="b853c-157">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
- <span data-ttu-id="b853c-158">Tüm özgün ve değiştirilmiş varlıklar temelinde iyimser eşzamanlılık.</span><span class="sxs-lookup"><span data-stu-id="b853c-158">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="b853c-159">Ayrıca, bir varlıkta bir varlık üzerinde güncelleştirmeler veya silmeler, örneğin bir müşteri ve ilişkili sıralama nesnelerinin bir koleksiyonu gibi işlemleri de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b853c-159">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="b853c-160">İstemcide bir varlık nesneleri ve onların alt () koleksiyonları grafiğinde değişiklikler yaptığınızda `EntitySet` ve iyimser eşzamanlılık denetimleri orijinal değerler gerektirdiğinde, istemci her varlık ve nesne için bu orijinal değerleri sağlamalıdır <xref:System.Data.Linq.EntitySet%601> .</span><span class="sxs-lookup"><span data-stu-id="b853c-160">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="b853c-161">İstemcilerinin tek bir yöntem çağrısında ilgili bir dizi ilgili güncelleştirme, silme ve ekleme yapmasını etkinleştirmek istiyorsanız, istemciye her varlıkta ne tür bir işlemin gerçekleştirileceğini belirten bir yol sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b853c-161">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="b853c-162">Daha sonra, <xref:System.Data.Linq.ITable.Attach%2A> <xref:System.Data.Linq.ITable.InsertOnSubmit%2A> <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A> <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> `Attach` kullanmadan önce her varlık için uygun yöntemi ve sonra, veya (Eklenenler olmadan) yöntemini <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b853c-162">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="b853c-163">Güncelleştirmeleri denemeden önce özgün değerleri elde etmenin bir yolu olarak veritabanından veri alma.</span><span class="sxs-lookup"><span data-stu-id="b853c-163">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="b853c-164">İyimser eşzamanlılık hakkında daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b853c-164">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="b853c-165">İyimser eşzamanlılık değişikliği çakışmalarını çözme hakkında ayrıntılı bilgi için bkz. [nasıl yapılır: değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="b853c-165">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="b853c-166">Aşağıdaki örneklerde her senaryo gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b853c-166">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="b853c-167">Zaman damgalarına sahip iyimser eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="b853c-167">Optimistic concurrency with timestamps</span></span>  
  
```vb  
' Assume that "customer" has been sent by client.  
' Attach with "true" to say this is a modified entity  
' and it can be checked for optimistic concurrency  
' because it has a column that is marked with the  
' "RowVersion" attribute.  
  
db.Customers.Attach(customer, True)  
  
Try  
    ' Optional: Specify a ConflictMode value  
    ' in call to SubmitChanges.  
    db.SubmitChanges()  
Catch ex As ChangeConflictException  
    ' Handle conflict based on options provided.  
    ' See MSDN article "How to: Manage Change  
    ' Conflicts (LINQ to SQL)".  
End Try  
```  
  
```csharp  
// Assume that "customer" has been sent by client.  
// Attach with "true" to say this is a modified entity  
// and it can be checked for optimistic concurrency because  
//  it has a column that is marked with "RowVersion" attribute  
db.Customers.Attach(customer, true)  
try  
{  
    // Optional: Specify a ConflictMode value  
    // in call to SubmitChanges.  
    db.SubmitChanges();  
}  
catch(ChangeConflictException e)  
{  
    // Handle conflict based on options provided  
    // See MSDN article How to: Manage Change Conflicts (LINQ to SQL).  
}  
```  
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="b853c-168">Özgün değerlerin alt kümesiyle</span><span class="sxs-lookup"><span data-stu-id="b853c-168">With Subset of Original Values</span></span>  

 <span data-ttu-id="b853c-169">Bu yaklaşımda istemci, tüm serileştirilmiş nesneyi, değiştirilecek değerlerle birlikte döndürür.</span><span class="sxs-lookup"><span data-stu-id="b853c-169">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
```vb  
Public Sub UpdateProductInventory(ByVal p As Product, ByVal _  
    unitsInStock As Short?, ByVal unitsOnOrder As Short?)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        ' p is the original unmodified product  
        ' that was obtained from the database.  
        ' The client kept a copy and returns it now.  
        db.Products.Attach(p, False)  
  
        ' Now that the original values are in the data context,  
        ' apply the changes.  
        p.UnitsInStock = unitsInStock  
        p.UnitsOnOrder = unitsOnOrder  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle conflict based on options provided.  
            ' See MSDN article "How to: Manage Change Conflicts  
            ' (LINQ to SQL)".  
        End Try  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInventory(Product p, short? unitsInStock, short? unitsOnOrder)  
{  
    using (NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString))  
    {  
        // p is the original unmodified product  
        // that was obtained from the database.  
        // The client kept a copy and returns it now.  
        db.Products.Attach(p, false);  
  
        // Now that the original values are in the data context, apply the changes.  
        p.UnitsInStock = unitsInStock;  
        p.UnitsOnOrder = unitsOnOrder;  
        try  
        {  
             // Optional: Specify a ConflictMode value  
             // in call to SubmitChanges.  
             db.SubmitChanges();  
        }  
        catch (ChangeConflictException e)  
        {  
            // Handle conflict based on provided options.  
            // See MSDN article How to: Manage Change Conflicts  
            // (LINQ to SQL).  
        }  
    }  
}  
```  
  
### <a name="with-complete-entities"></a><span data-ttu-id="b853c-170">Tüm varlıklarla</span><span class="sxs-lookup"><span data-stu-id="b853c-170">With Complete Entities</span></span>  
  
```vb  
Public Sub UpdateProductInfo(ByVal newProd As Product, ByVal _  
    originalProd As Product)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        db.Products.Attach(newProd, originalProd)  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle potential change conflicgt in whatever way  
            ' is appropriate for your application.  
            ' For more information, see the MSDN article  
            ' "How to: Manage Change Conflicts (LINQ to  
            ' SQL)".  
        End Try  
  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInfo(Product newProd, Product originalProd)  
{  
     using (NorthwindClasses1DataContext db = new  
        NorthwindClasses1DataContext(connectionString))  
     {  
         db.Products.Attach(newProd, originalProd);  
         try  
         {  
               // Optional: Specify a ConflictMode value  
               // in call to SubmitChanges.  
               db.SubmitChanges();  
         }  
        catch (ChangeConflictException e)  
        {  
            // Handle potential change conflict in whatever way  
            // is appropriate for your application.  
            // For more information, see the MSDN article  
            // How to: Manage Change Conflicts (LINQ to SQL)/  
        }
    }  
}  
```  
  
 <span data-ttu-id="b853c-171">Bir koleksiyonu güncelleştirmek için yerine çağırın <xref:System.Data.Linq.ITable.AttachAll%2A> `Attach` .</span><span class="sxs-lookup"><span data-stu-id="b853c-171">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="b853c-172">Beklenen varlık üyeleri</span><span class="sxs-lookup"><span data-stu-id="b853c-172">Expected Entity Members</span></span>  

 <span data-ttu-id="b853c-173">Daha önce belirtildiği gibi, yöntemleri çağırmadan önce yalnızca belirli varlık nesnesi üyelerinin ayarlanması gerekir `Attach` .</span><span class="sxs-lookup"><span data-stu-id="b853c-173">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="b853c-174">Ayarlanması gereken varlık üyelerinin aşağıdaki kriterleri yerine getirilmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="b853c-174">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
- <span data-ttu-id="b853c-175">Varlığın kimliğinin bir parçası olun.</span><span class="sxs-lookup"><span data-stu-id="b853c-175">Be part of the entity’s identity.</span></span>  
  
- <span data-ttu-id="b853c-176">Değiştirilmesi bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="b853c-176">Be expected to be modified.</span></span>  
  
- <span data-ttu-id="b853c-177">Bir zaman damgası olun veya <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özniteliği bir öğe olarak ayarlanır `Never` .</span><span class="sxs-lookup"><span data-stu-id="b853c-177">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="b853c-178">Bir tablo, iyimser eşzamanlılık denetimi için zaman damgası veya sürüm numarası kullanıyorsa, bu üyeleri çağırmadan önce ayarlamanız gerekir <xref:System.Data.Linq.ITable.Attach%2A> .</span><span class="sxs-lookup"><span data-stu-id="b853c-178">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="b853c-179"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>Bu sütun özniteliğinde özelliği true olarak ayarlandığında, bir üye iyimser eşzamanlılık denetimi için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b853c-179">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="b853c-180">İstenen tüm güncelleştirmeler yalnızca sürüm numarası veya zaman damgası değerleri veritabanında aynı ise gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b853c-180">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="b853c-181">Üye, olarak ayarlı olmadığı sürece iyimser eşzamanlılık denetiminde de kullanılır <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> `Never` .</span><span class="sxs-lookup"><span data-stu-id="b853c-181">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="b853c-182">Varsayılan değer, `Always` başka bir değer belirtilmemişse olur.</span><span class="sxs-lookup"><span data-stu-id="b853c-182">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="b853c-183">Bu gerekli üyelerin herhangi biri eksikse, <xref:System.Data.Linq.ChangeConflictException> <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("satır bulunamadı veya değiştirildi") sırasında bir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b853c-183">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="b853c-184">Durum</span><span class="sxs-lookup"><span data-stu-id="b853c-184">State</span></span>  

 <span data-ttu-id="b853c-185">Bir varlık nesnesi örneğe eklendikten sonra <xref:System.Data.Linq.DataContext> , nesne durumunda olduğu kabul edilir `PossiblyModified` .</span><span class="sxs-lookup"><span data-stu-id="b853c-185">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="b853c-186">Eklenmiş bir nesneyi kabul etmeye zorlamak için üç yol vardır `Modified` .</span><span class="sxs-lookup"><span data-stu-id="b853c-186">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1. <span data-ttu-id="b853c-187">Bunu değiştirilmemiş olarak ekleyin ve ardından alanları doğrudan değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b853c-187">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2. <span data-ttu-id="b853c-188"><xref:System.Data.Linq.Table%601.Attach%2A>Geçerli ve orijinal nesne örneklerini alan aşırı yüklemeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b853c-188">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="b853c-189">Bu değişiklik izleyicisini eski ve yeni değerlerle sağlar, böylece hangi alanların değiştirildiğini otomatik olarak bilir.</span><span class="sxs-lookup"><span data-stu-id="b853c-189">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3. <span data-ttu-id="b853c-190"><xref:System.Data.Linq.Table%601.Attach%2A>İkinci bir Boole parametresi alan aşırı yüklemeye ekleyin (true olarak ayarlanır).</span><span class="sxs-lookup"><span data-stu-id="b853c-190">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="b853c-191">Bu, değişiklik izleyicide herhangi bir özgün değer sağlamak zorunda kalmadan değiştirilen nesneyi kabul edecek şekilde söyleyecektir.</span><span class="sxs-lookup"><span data-stu-id="b853c-191">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="b853c-192">Bu yaklaşımda, nesnenin bir sürüm/zaman damgası alanı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b853c-192">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="b853c-193">Daha fazla bilgi için bkz. [nesne durumları ve değişiklik izleme](object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="b853c-193">For more information, see [Object States and Change-Tracking](object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="b853c-194">Bir varlık nesnesi, iliştirilmekte olan nesneyle aynı kimliğe sahip KIMLIK önbelleğinde zaten gerçekleşirse, bir <xref:System.Data.Linq.DuplicateKeyException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b853c-194">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="b853c-195">Bir nesne kümesiyle birlikte eklediğinizde `IEnumerable` , <xref:System.Data.Linq.DuplicateKeyException> zaten varolan bir anahtar olduğunda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b853c-195">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="b853c-196">Kalan nesneler ekli değil.</span><span class="sxs-lookup"><span data-stu-id="b853c-196">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b853c-197">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b853c-197">See also</span></span>

- [<span data-ttu-id="b853c-198">LINQ to SQL ile N Katmanı ve Uzak Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="b853c-198">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="b853c-199">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="b853c-199">Background Information</span></span>](background-information.md)
