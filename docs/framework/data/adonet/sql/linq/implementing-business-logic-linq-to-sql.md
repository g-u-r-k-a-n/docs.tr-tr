---
title: İş Mantığının Uygulanması (LINQ - SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 51b92549a40d0e5121cc390f5dbdf726cc06404b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174556"
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="848d7-102">İş Mantığının Uygulanması (LINQ - SQL)</span><span class="sxs-lookup"><span data-stu-id="848d7-102">Implementing Business Logic (LINQ to SQL)</span></span>
<span data-ttu-id="848d7-103">Bu konudaki "iş mantığı" terimi, veritabanına eklenmeden, güncellenmeden veya silinmeden önce verilere uyguladığınız özel kuralları veya doğrulama testlerini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="848d7-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="848d7-104">İş mantığı bazen "iş kuralları" veya "etki alanı mantığı" olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="848d7-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="848d7-105">N katmanlı uygulamalarda genellikle mantıksal bir katman olarak tasarlanmıştır, böylece sunu katmanından veya veri erişim katmanından bağımsız olarak değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="848d7-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="848d7-106">İş mantığı, veri tabanındaki verilerin güncelleştirilmesinden, eklenmesinden veya silinmesinden önce veya sonra veri erişim katmanı tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="848d7-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="848d7-107">İş mantığı, alan türünün tablo sütununun türüyle uyumlu olduğundan emin olmak için şema doğrulaması kadar basit olabilir.</span><span class="sxs-lookup"><span data-stu-id="848d7-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="848d7-108">Veya rasgele karmaşık şekillerde etkileşim nesneleri kümesi nden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="848d7-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="848d7-109">Kurallar veritabanında depolanan yordamlar olarak veya bellek nesneleri olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="848d7-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="848d7-110">Ancak iş mantığı uygulanır, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iş mantığını veri erişim kodundan ayırmak için kısmi sınıflar ve kısmi yöntemler kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="848d7-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="848d7-111">LINQ'dan SQL'e İş Mantığınızı Nasıl Çağırır?</span><span class="sxs-lookup"><span data-stu-id="848d7-111">How LINQ to SQL Invokes Your Business Logic</span></span>  
 <span data-ttu-id="848d7-112">Tasarım zamanında, el ile veya Nesne İlişkisel Tasarımcı veya SQLMetal kullanarak bir varlık sınıfı oluşturduğunuzda, kısmi sınıf olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="848d7-112">When you generate an entity class at design time, either manually or by using the Object Relational Designer or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="848d7-113">Bu, ayrı bir kod dosyasında, özel iş mantığınızı içeren varlık sınıfının başka bir bölümünü tanımlayabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="848d7-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="848d7-114">Derleme zamanında, iki bölüm tek bir sınıf halinde birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="848d7-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="848d7-115">Ancak Object Relational Designer veya SQLMetal'i kullanarak varlık sınıflarınızı yeniden oluşturmanız gerekiyorsa, bunu yapabilirsiniz ve sınıfın sizin bölümünüz değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="848d7-115">But if you have to regenerate your entity classes by using the Object Relational Designer or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="848d7-116">Varlıkları tanımlayan kısmi sınıflar ve <xref:System.Data.Linq.DataContext> kısmi yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="848d7-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="848d7-117">Bunlar, bir varlık veya varlık özelliği için herhangi bir güncelleştirme, ekleme veya silme den önce ve sonra iş mantığınızı uygulamak için kullanabileceğiniz genişletilebilirlik noktalarıdır.</span><span class="sxs-lookup"><span data-stu-id="848d7-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="848d7-118">Kısmi yöntemler derleme zamanı olayları olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="848d7-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="848d7-119">Kod oluşturucu bir yöntem imzasını tanımlar ve özellik erişime girenleri, `DataContext` oluşturucuyu ve bazı durumlarda <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağrıldığında perde arkasında yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="848d7-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="848d7-120">Ancak, belirli bir kısmi yöntemi uygulamazsanız, bu yönteme ve tanıma yapılan tüm başvurular derleme zamanında kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="848d7-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="848d7-121">Ayrı kod dosyanıza yazdığınız uygulama tanımında, gereken özel mantığı gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848d7-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="848d7-122">Kısmi sınıfınızın kendisini etki alanı katmanınız olarak kullanabilir veya kısmi yöntemin uygulama tanımından ayrı bir nesneye veya nesneye çağrılayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848d7-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="848d7-123">Her iki şekilde de, iş mantığınız hem veri erişim kodunuzdan hem de sunu katmanı kodunuzdan temiz bir şekilde ayrılır.</span><span class="sxs-lookup"><span data-stu-id="848d7-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="848d7-124">Genişletilebilirlik Noktalarına Daha Yakından Bakış</span><span class="sxs-lookup"><span data-stu-id="848d7-124">A Closer Look at the Extensibility Points</span></span>  
 <span data-ttu-id="848d7-125">Aşağıdaki örnek, iki tabloya sahip sınıf için Nesne `DataContext` İlişkisel Tasarımcısı `Customers` tarafından `Orders`oluşturulan kodun bir bölümünü gösterir: ve .</span><span class="sxs-lookup"><span data-stu-id="848d7-125">The following example shows part of the code generated by the Object Relational Designer for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="848d7-126">Sınıftaki her tablo için Ekle, Güncelleştir ve Sil yöntemlerinin tanımlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="848d7-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 <span data-ttu-id="848d7-127">Kısmi sınıfınızda Ekle, Güncelleştir ve Sil yöntemlerini [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygularsanız, çalışma zamanı çağrıldığında <xref:System.Data.Linq.DataContext.SubmitChanges%2A> kendi varsayılan yöntemleri yerine onları çağırır.</span><span class="sxs-lookup"><span data-stu-id="848d7-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="848d7-128">Bu, oluşturma / okuma / güncelleme / silme işlemleri için varsayılan davranışı geçersiz kılmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="848d7-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="848d7-129">Daha fazla bilgi için [Bkz. Walkthrough: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme.](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)</span><span class="sxs-lookup"><span data-stu-id="848d7-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="848d7-130">Yöntem `OnCreated` sınıf oluşturucu olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="848d7-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 <span data-ttu-id="848d7-131">Varlık sınıfları, varlık oluşturulduğunda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yüklendiğinde ve doğrulandığında (çağrıldığında) `SubmitChanges` çalışma zamanına göre çağrılan üç yönteme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="848d7-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="848d7-132">Varlık sınıfları da her özellik için iki kısmi yöntem vardır, bir özellik ayarlıönce denir ve sonra denir.</span><span class="sxs-lookup"><span data-stu-id="848d7-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="848d7-133">Aşağıdaki kod örneği, sınıf için oluşturulan `Customer` yöntemlerden bazılarını gösterir:</span><span class="sxs-lookup"><span data-stu-id="848d7-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 <span data-ttu-id="848d7-134">Yöntem özelliği için `CustomerID` aşağıdaki örnekte gösterildiği gibi özellik kümesi erişimci denir:</span><span class="sxs-lookup"><span data-stu-id="848d7-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 <span data-ttu-id="848d7-135">Sınıfın sizin bölümünde, yöntemin uygulama tanımını yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="848d7-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="848d7-136">Visual Studio'da, `partial` yazdıktan sonra sınıfın diğer bölümündeki yöntem tanımları için IntelliSense'i görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="848d7-136">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 <span data-ttu-id="848d7-137">Kısmi yöntemler kullanarak uygulamanız için iş mantığı nın nasıl eklenöğretilen hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="848d7-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="848d7-138">Nasıl yapılır: Varlık sınıflarına doğrulama ekleme</span><span class="sxs-lookup"><span data-stu-id="848d7-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="848d7-139">İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="848d7-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 <span data-ttu-id="848d7-140">[Walkthrough: Varlık Sınıflarına Doğrulama Ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="848d7-140">[Walkthrough: Adding Validation to Entity Classes](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="848d7-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="848d7-141">See also</span></span>

- [<span data-ttu-id="848d7-142">Parçalı Sınıflar ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="848d7-142">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="848d7-143">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="848d7-143">Partial Methods</span></span>](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="848d7-144">Visual Studio'daki LINQ to SQL Araçları</span><span class="sxs-lookup"><span data-stu-id="848d7-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="848d7-145">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="848d7-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
