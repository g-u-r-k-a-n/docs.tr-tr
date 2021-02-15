---
description: 'Daha fazla bilgi edinin: Izlenecek yol: COM nesneleriyle devralma uygulama (Visual Basic)'
title: 'İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: dc16990f25126cba52ef3ea457e8c3157c987c60
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438950"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="e2007-103">İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2007-103">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>

<span data-ttu-id="e2007-104">`Public`Visual Basic önceki sürümlerinde oluşturulanlar da dahil olmak üzere COM nesnelerinde sınıflardan Visual Basic sınıfları türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2007-104">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of Visual Basic.</span></span> <span data-ttu-id="e2007-105">COM nesnelerinden devralınan sınıfların özellikleri ve yöntemleri, özellik olarak geçersiz kılınabilir veya aşırı yüklenebilir ve diğer temel sınıfların yöntemlerinin geçersiz kılınabilmesi veya aşırı yüklenmesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2007-105">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="e2007-106">COM nesnelerinden devralma, yeniden derlemek istemediğiniz mevcut bir sınıf kitaplığınız olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2007-106">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>

<span data-ttu-id="e2007-107">Aşağıdaki yordamda, bir sınıfı içeren COM nesnesi oluşturmak için Visual Basic 6,0 ' nin nasıl kullanılacağı gösterilmektedir ve ardından bunu temel sınıf olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="e2007-107">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="e2007-108">Bu kılavuzda kullanılan COM nesnesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e2007-108">To build the COM object that is used in this walkthrough</span></span>

1. <span data-ttu-id="e2007-109">Visual Basic 6,0 ' de, yeni bir ActiveX DLL projesi açın.</span><span class="sxs-lookup"><span data-stu-id="e2007-109">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="e2007-110">Adlı bir proje `Project1` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e2007-110">A project named `Project1` is created.</span></span> <span data-ttu-id="e2007-111">Adında bir sınıfı vardır `Class1` .</span><span class="sxs-lookup"><span data-stu-id="e2007-111">It has a class named `Class1`.</span></span>

2. <span data-ttu-id="e2007-112">**Proje Gezgini**'Nde, **Project1** öğesine sağ tıklayın ve ardından **Project1 özellikleri**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e2007-112">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="e2007-113">**Proje özellikleri** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e2007-113">The **Project Properties** dialog box is displayed.</span></span>

3. <span data-ttu-id="e2007-114">Proje **özellikleri** Iletişim kutusunun **genel** sekmesinde Proje adı alanına yazarak proje adını değiştirin `ComObject1` . </span><span class="sxs-lookup"><span data-stu-id="e2007-114">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>

4. <span data-ttu-id="e2007-115">**Proje Gezgini**'nde, öğesine sağ tıklayın `Class1` ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e2007-115">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="e2007-116">Sınıfının **Özellikler** penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e2007-116">The **Properties** window for the class is displayed.</span></span>

5. <span data-ttu-id="e2007-117">`Name`Özelliğini olarak değiştirin `MathFunctions` .</span><span class="sxs-lookup"><span data-stu-id="e2007-117">Change the `Name` property to `MathFunctions`.</span></span>

6. <span data-ttu-id="e2007-118">**Proje Gezgini**'nde, öğesine sağ tıklayın `MathFunctions` ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e2007-118">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="e2007-119">**Kod Düzenleyicisi** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e2007-119">The **Code Editor** is displayed.</span></span>

7. <span data-ttu-id="e2007-120">Özellik değerini tutacak bir yerel değişken ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e2007-120">Add a local variable to hold the property value:</span></span>

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. <span data-ttu-id="e2007-121">Özellik `Let` ve özellik `Get` özelliği yordamlarını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e2007-121">Add Property `Let` and Property `Get` property procedures:</span></span>

    ```vb
    Public Property Let Prop1(ByVal vData As Integer)
       'Used when assigning a value to the property.
       mvarProp1 = vData
    End Property
    Public Property Get Prop1() As Integer
       'Used when retrieving a property's value.
       Prop1 = mvarProp1
    End Property
    ```

9. <span data-ttu-id="e2007-122">Bir işlev ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e2007-122">Add a function:</span></span>

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. <span data-ttu-id="e2007-123">**Dosya** menüsünde **ComObject1.dllyap** ' a tıklayarak com nesnesini oluşturun ve kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e2007-123">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e2007-124">Ayrıca, Visual Basic ile oluşturulmuş bir sınıfı bir COM nesnesi olarak kullanıma sunabilseniz de, bu, gerçek bir COM nesnesi değildir ve bu kılavuzda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e2007-124">Although you can also expose a class created with Visual Basic as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="e2007-125">Ayrıntılar için bkz. [.NET Framework uygulamalarda com birlikte çalışabilirliği](com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="e2007-125">For details, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>

## <a name="interop-assemblies"></a><span data-ttu-id="e2007-126">Birlikte çalışma derlemeleri</span><span class="sxs-lookup"><span data-stu-id="e2007-126">Interop Assemblies</span></span>

<span data-ttu-id="e2007-127">Aşağıdaki yordamda, yönetilmeyen kod (COM nesnesi gibi) ve Visual Studio 'Nun kullandığı yönetilen kod arasında köprü görevi gören bir birlikte çalışma derlemesi oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e2007-127">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code Visual Studio uses.</span></span> <span data-ttu-id="e2007-128">Visual Basic tarafından oluşturulan birlikte çalışma derlemesi, *birlikte çalışma hazırlama* ve com nesnelerinden gelen ve bunlara geçiş yaparken değerleri eşdeğer veri türlerine döndürme gibi com nesneleriyle çalışma hakkında pek çok ayrıntıyı işler.</span><span class="sxs-lookup"><span data-stu-id="e2007-128">The interop assembly that Visual Basic creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="e2007-129">Visual Basic uygulamasındaki başvuru, gerçek COM nesnesi değil birlikte çalışma derlemesine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="e2007-129">The reference in the Visual Basic application points to the interop assembly, not the actual COM object.</span></span>

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="e2007-130">Visual Basic 2005 ve sonraki sürümlerde bir COM nesnesi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e2007-130">To use a COM object with Visual Basic 2005 and later versions</span></span>

1. <span data-ttu-id="e2007-131">Yeni bir Visual Basic Windows uygulaması projesi açın.</span><span class="sxs-lookup"><span data-stu-id="e2007-131">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="e2007-132">**Proje** menüsünde, **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e2007-132">On the **Project** menu, click **Add Reference**.</span></span>

     <span data-ttu-id="e2007-133">**Başvuru Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e2007-133">The **Add Reference** dialog box is displayed.</span></span>

3. <span data-ttu-id="e2007-134">**Com** sekmesinde, `ComObject1` **bileşen adı** listesine çift tıklayın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e2007-134">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>

4. <span data-ttu-id="e2007-135">**Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e2007-135">On the **Project** menu, click **Add New Item**.</span></span>

     <span data-ttu-id="e2007-136">**Yeni Öğe Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e2007-136">The **Add New Item** dialog box is displayed.</span></span>

5. <span data-ttu-id="e2007-137">**Şablonlar** bölmesinde **sınıf**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e2007-137">In the **Templates** pane, click **Class**.</span></span>

     <span data-ttu-id="e2007-138">Varsayılan dosya adı, `Class1.vb` **ad** alanında görünür.</span><span class="sxs-lookup"><span data-stu-id="e2007-138">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="e2007-139">Bu alanı MathClass. vb olarak değiştirin ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e2007-139">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="e2007-140">Bu, adlı bir sınıf oluşturur `MathClass` ve kodunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e2007-140">This creates a class named `MathClass`, and displays its code.</span></span>

6. <span data-ttu-id="e2007-141">COM sınıfından devralması için aşağıdaki kodu en üst öğesine ekleyin `MathClass` .</span><span class="sxs-lookup"><span data-stu-id="e2007-141">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. <span data-ttu-id="e2007-142">Aşağıdaki kodu öğesine ekleyerek temel sınıfın ortak yöntemini aşırı yükleme `MathClass` :</span><span class="sxs-lookup"><span data-stu-id="e2007-142">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. <span data-ttu-id="e2007-143">Aşağıdaki kodu öğesine ekleyerek devralınan sınıfı genişletin `MathClass` :</span><span class="sxs-lookup"><span data-stu-id="e2007-143">Extend the inherited class by adding the following code to `MathClass`:</span></span>

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

<span data-ttu-id="e2007-144">Yeni sınıf COM nesnesindeki temel sınıfın özelliklerini devralır, bir yöntemi aşırı yükler ve sınıfı genişletmek için yeni bir yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2007-144">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>

### <a name="to-test-the-inherited-class"></a><span data-ttu-id="e2007-145">Devralınan sınıfı test etmek için</span><span class="sxs-lookup"><span data-stu-id="e2007-145">To test the inherited class</span></span>

1. <span data-ttu-id="e2007-146">Başlangıç formunuza bir düğme ekleyin ve sonra kodunu görüntülemek için çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e2007-146">Add a button to your startup form, and then double-click it to view its code.</span></span>

2. <span data-ttu-id="e2007-147">Düğmenin `Click` olay işleyicisi yordamında, örneği oluşturmak `MathClass` ve aşırı yüklenmiş yöntemleri çağırmak için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e2007-147">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. <span data-ttu-id="e2007-148">F5 tuşuna basarak projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e2007-148">Run the project by pressing F5.</span></span>

<span data-ttu-id="e2007-149">Formdaki düğmeye tıkladığınızda, `AddNumbers` yöntemi ilk olarak `Short` veri türü numaralarıyla çağırılır ve Visual Basic temel sınıftan uygun yöntemi seçer.</span><span class="sxs-lookup"><span data-stu-id="e2007-149">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and Visual Basic chooses the appropriate method from the base class.</span></span> <span data-ttu-id="e2007-150">İkinci çağrısı, ' `AddNumbers` den aşırı yükleme yöntemine yönlendirilir `MathClass` .</span><span class="sxs-lookup"><span data-stu-id="e2007-150">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="e2007-151">Üçüncü çağrı, `SubtractNumbers` sınıfını genişleten yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="e2007-151">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="e2007-152">Temel sınıftaki özelliği ayarlanır ve değer görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e2007-152">The property in the base class is set, and the value is displayed.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e2007-153">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="e2007-153">Next Steps</span></span>

<span data-ttu-id="e2007-154">Aşırı yüklenmiş `AddNumbers` işlevin, com nesnesinin temel sınıfından devralınan yöntemle aynı veri türüne sahip olduğunu fark etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2007-154">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="e2007-155">Bunun nedeni, temel sınıf yönteminin bağımsız değişkenlerinin ve parametrelerinin Visual Basic 6,0 ' de 16 bit tamsayılar olarak tanımlandığından, ancak Visual Basic sonraki sürümlerinde türünün 16 bit tamsayılar olarak sunulmasıdır `Short` .</span><span class="sxs-lookup"><span data-stu-id="e2007-155">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="e2007-156">Yeni işlev 32 bitlik tamsayılar kabul eder ve temel sınıf işlevini aşırı yükler.</span><span class="sxs-lookup"><span data-stu-id="e2007-156">The new function accepts 32-bit integers, and overloads the base class function.</span></span>

<span data-ttu-id="e2007-157">COM nesneleriyle çalışırken, parametrelerin boyutunu ve veri türlerini doğruladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e2007-157">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="e2007-158">Örneğin, bir bağımsız değişken olarak Visual Basic 6,0 koleksiyon nesnesini kabul eden bir COM nesnesi kullanırken, Visual Basic daha sonraki bir sürümünden koleksiyon sağlayamezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2007-158">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>

<span data-ttu-id="e2007-159">COM sınıflarından devralınan özellikler ve Yöntemler geçersiz kılınabilir, yani bir temel COM sınıfından devralınan bir özelliğin veya yöntemin yerini alan bir yerel özellik veya yöntem bildirebilmeniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e2007-159">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="e2007-160">Devralınan COM özelliklerinin üzerine yazma kuralları, diğer özellikleri ve yöntemleri aşağıdaki özel durumlarla geçersiz kılmak için kurallara benzerdir:</span><span class="sxs-lookup"><span data-stu-id="e2007-160">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>

- <span data-ttu-id="e2007-161">Bir COM sınıfından devralınan herhangi bir özelliği veya yöntemi geçersiz kılarsınız, diğer devralınmış özellikleri ve yöntemleri geçersiz kılmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2007-161">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>

- <span data-ttu-id="e2007-162">Parametreleri kullanan özellikler `ByRef` geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="e2007-162">Properties that use `ByRef` parameters cannot be overridden.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2007-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2007-163">See also</span></span>

- [<span data-ttu-id="e2007-164">.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="e2007-164">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="e2007-165">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="e2007-165">Inherits Statement</span></span>](../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="e2007-166">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e2007-166">Short Data Type</span></span>](../../language-reference/data-types/short-data-type.md)
