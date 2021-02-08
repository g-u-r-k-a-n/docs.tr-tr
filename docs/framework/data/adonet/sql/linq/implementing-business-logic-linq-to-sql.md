---
description: 'Daha fazla bilgi edinin: Iş mantığını uygulama (LINQ to SQL)'
title: Iş mantığını uygulama (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 3f2b7085db3832f37da7520c8f75b6bc120125f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803886"
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="38211-103">Iş mantığını uygulama (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="38211-103">Implementing Business Logic (LINQ to SQL)</span></span>

<span data-ttu-id="38211-104">Bu konudaki "iş mantığı" terimi, verileri eklenmeden, yapılandırmadan veya veritabanından silinmeden önce, veri için uyguladığınız özel kurallara veya doğrulama testlerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="38211-104">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="38211-105">İş mantığı bazen "iş kuralları" veya "etki alanı mantığı" olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="38211-105">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="38211-106">N katmanlı uygulamalarda, genellikle, sunu katmanından veya veri erişim katmanından bağımsız olarak değiştirilebilecek şekilde mantıksal katman olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="38211-106">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="38211-107">İş mantığı, veritabanındaki verilerin güncelleştirilmesi, eklenmesi veya silinmesinden önce veya sonra veri erişim katmanı tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="38211-107">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="38211-108">Alan türünün tablo sütununun türüyle uyumlu olduğundan emin olmak için, iş mantığı bir şema doğrulaması kadar basit olabilir.</span><span class="sxs-lookup"><span data-stu-id="38211-108">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="38211-109">Ya da rastgele karmaşık yollarla etkileşim kuran bir nesne kümesinden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="38211-109">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="38211-110">Kurallar, veritabanında saklı yordamlar olarak veya bellek içi nesneler olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="38211-110">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="38211-111">Ancak iş mantığı uygulanır, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veri erişim kodundan iş mantığını ayırmak için kısmi sınıflar ve kısmi Yöntemler kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="38211-111">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="38211-112">LINQ to SQL Iş mantığınızı nasıl çağırır</span><span class="sxs-lookup"><span data-stu-id="38211-112">How LINQ to SQL Invokes Your Business Logic</span></span>  

 <span data-ttu-id="38211-113">Tasarım zamanında, el ile veya Nesne İlişkisel Tasarımcısı ya da SQLMetal kullanarak bir varlık sınıfı oluşturduğunuzda, bu, kısmi bir sınıf olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="38211-113">When you generate an entity class at design time, either manually or by using the Object Relational Designer or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="38211-114">Bu, ayrı bir kod dosyasında özel iş mantığınızı içeren varlık sınıfının başka bir bölümünü tanımlayabilmeniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="38211-114">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="38211-115">Derleme zamanında, iki bölüm tek bir sınıfta birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="38211-115">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="38211-116">Ancak Nesne İlişkisel Tasarımcısı veya SQLMetal kullanarak varlık sınıflarınızı yeniden oluşturmanız gerekiyorsa, bunu yapabilirsiniz ve sınıfının bir kısmı değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="38211-116">But if you have to regenerate your entity classes by using the Object Relational Designer or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="38211-117">Varlıkları tanımlayan kısmi sınıflar ve <xref:System.Data.Linq.DataContext> kısmi yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="38211-117">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="38211-118">Bunlar bir varlık veya varlık özelliği için herhangi bir güncelleştirme, ekleme veya silme işleminden önce ve sonra iş mantığınızı uygulamak için kullanabileceğiniz genişletilebilirlik noktalardır.</span><span class="sxs-lookup"><span data-stu-id="38211-118">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="38211-119">Kısmi Yöntemler, derleme zamanı olayları olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="38211-119">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="38211-120">Kod Oluşturucu bir yöntem imzasını tanımlar ve Get ve set özellik erişimcileri, `DataContext` Oluşturucu ve bazı durumlarda, çağrıldığında bu yöntemleri çağırır <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .</span><span class="sxs-lookup"><span data-stu-id="38211-120">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="38211-121">Ancak, belirli bir kısmi yöntemi gerçekleştirmeyin, bu durumda ona yapılan tüm başvurular ve tanım derleme sırasında kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="38211-121">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="38211-122">Ayrı kod dosyanızda yazdığınız uygulama tanımında, gerekli olan her türlü özel mantığı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38211-122">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="38211-123">Kısmi sınıfınızı kendi etki alanı katmanınız olarak kullanabilir veya kısmi yöntemin uygulama tanımınızdan ayrı bir nesneye veya nesnelere çağrı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38211-123">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="38211-124">Her iki durumda da, iş mantığınız hem veri erişim kodunuzdan hem de sunum katmanı kodunuzda düzgün bir şekilde ayrılır.</span><span class="sxs-lookup"><span data-stu-id="38211-124">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="38211-125">Genişletilebilirlik noktalarına daha yakından bakış</span><span class="sxs-lookup"><span data-stu-id="38211-125">A Closer Look at the Extensibility Points</span></span>  

 <span data-ttu-id="38211-126">Aşağıdaki örnek, iki tablo içeren sınıf için Nesne İlişkisel Tasarımcısı tarafından oluşturulan kodun bir parçasını gösterir `DataContext` : `Customers` ve `Orders` .</span><span class="sxs-lookup"><span data-stu-id="38211-126">The following example shows part of the code generated by the Object Relational Designer for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="38211-127">INSERT, Update ve DELETE yöntemlerinin sınıftaki her tablo için tanımlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="38211-127">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
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
  
 <span data-ttu-id="38211-128">Kısmi sınıfınıza INSERT, Update ve DELETE yöntemlerini uygularsanız, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çağrıldığında çalışma zamanı bunları kendi varsayılan yöntemleri yerine çağırır <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .</span><span class="sxs-lookup"><span data-stu-id="38211-128">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="38211-129">Bu, oluşturma/okuma/güncelleştirme/silme işlemleri için varsayılan davranışı geçersiz kılmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="38211-129">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="38211-130">Daha fazla bilgi için bkz. [Izlenecek yol: varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span><span class="sxs-lookup"><span data-stu-id="38211-130">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="38211-131">`OnCreated`Yöntemi sınıf oluşturucusunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="38211-131">The `OnCreated` method is called in the class constructor.</span></span>  
  
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
  
 <span data-ttu-id="38211-132">Varlık sınıflarının, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlık oluşturulduğunda, yüklendiğinde ve doğrulandığında (çağrıldığında) çalışma zamanı tarafından çağrılan üç yöntemi vardır `SubmitChanges` .</span><span class="sxs-lookup"><span data-stu-id="38211-132">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="38211-133">Varlık sınıflarının her bir özellik için iki kısmi yöntemi vardır, bir özellik ayarlanmadan önce çağırılır ve öğesinden sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="38211-133">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="38211-134">Aşağıdaki kod örneği, sınıfı için oluşturulan yöntemlerin bazılarını göstermektedir `Customer` :</span><span class="sxs-lookup"><span data-stu-id="38211-134">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
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
  
 <span data-ttu-id="38211-135">Yöntemleri, özelliği için aşağıdaki örnekte gösterildiği gibi özellik kümesi erişimcisinde çağrılır `CustomerID` :</span><span class="sxs-lookup"><span data-stu-id="38211-135">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
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
  
 <span data-ttu-id="38211-136">Sınıfının bölümünde, yönteminin bir uygulama tanımını yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="38211-136">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="38211-137">Visual Studio 'da, yazdıktan sonra `partial` sınıfının diğer bölümünde yöntem tanımları Için IntelliSense 'i görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="38211-137">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
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
  
 <span data-ttu-id="38211-138">Kısmi yöntemler kullanarak uygulamanıza iş mantığı ekleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="38211-138">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="38211-139">Nasıl yapılır: Varlık sınıflarına doğrulama ekleme</span><span class="sxs-lookup"><span data-stu-id="38211-139">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="38211-140">İzlenecek yol: Varlık sınıflarının ekleme, güncelleştirme ve silme davranışını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="38211-140">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 <span data-ttu-id="38211-141">[İzlenecek yol: varlık sınıflarına doğrulama ekleme](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="38211-141">[Walkthrough: Adding Validation to Entity Classes](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38211-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38211-142">See also</span></span>

- [<span data-ttu-id="38211-143">Parçalı Sınıflar ve Yöntemler</span><span class="sxs-lookup"><span data-stu-id="38211-143">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="38211-144">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="38211-144">Partial Methods</span></span>](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="38211-145">Visual Studio'daki LINQ to SQL Araçları</span><span class="sxs-lookup"><span data-stu-id="38211-145">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="38211-146">SqlMetal.exe (kod üretme aracı)</span><span class="sxs-lookup"><span data-stu-id="38211-146">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
