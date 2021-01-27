---
title: Statik sınıflar ve statik sınıf üyeleri-C# Programlama Kılavuzu
description: Statik sınıflar C# ' de başlatılamaz. Statik bir sınıfın üyelerine sınıf adının kendisini kullanarak erişirsiniz.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: 31de2a7d58d610213bfa4fc0377e1ab7283e111e
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899015"
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a><span data-ttu-id="51cb0-104">Statik Sınıflar ve Statik Sınıf Üyeleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="51cb0-104">Static Classes and Static Class Members (C# Programming Guide)</span></span>

<span data-ttu-id="51cb0-105">[Statik](../../language-reference/keywords/static.md) bir sınıf temelde statik olmayan bir sınıfla aynıdır, ancak bir fark vardır: statik bir sınıf örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="51cb0-105">A [static](../../language-reference/keywords/static.md) class is basically the same as a non-static class, but there is one difference: a static class cannot be instantiated.</span></span> <span data-ttu-id="51cb0-106">Diğer bir deyişle, sınıf türünde bir değişken oluşturmak için [New](../../language-reference/operators/new-operator.md) işlecini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="51cb0-106">In other words, you cannot use the [new](../../language-reference/operators/new-operator.md) operator to create a variable of the class type.</span></span> <span data-ttu-id="51cb0-107">Örnek değişkeni olmadığından, bir statik sınıfın üyelerine sınıf adının kendisini kullanarak erişirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51cb0-107">Because there is no instance variable, you access the members of a static class by using the class name itself.</span></span> <span data-ttu-id="51cb0-108">Örneğin, ortak statik bir yöntemi adlı adlı bir statik sınıfınız varsa `UtilityClass` `MethodA` , yöntemi aşağıdaki örnekte gösterildiği gibi çağırın:</span><span class="sxs-lookup"><span data-stu-id="51cb0-108">For example, if you have a static class that is named `UtilityClass` that has a public static method named `MethodA`, you call the method as shown in the following example:</span></span>  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 <span data-ttu-id="51cb0-109">Statik bir sınıf, yalnızca giriş parametrelerinde çalışan yöntemlerin kümeleri için uygun bir kapsayıcı olarak kullanılabilir ve herhangi bir iç örnek alanı almak veya ayarlamak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="51cb0-109">A static class can be used as a convenient container for sets of methods that just operate on input parameters and do not have to get or set any internal instance fields.</span></span> <span data-ttu-id="51cb0-110">Örneğin, .NET sınıf kitaplığı 'nda statik <xref:System.Math?displayProperty=nameWithType> sınıf, sınıfının belirli bir örneğine özgü verileri depolamak veya almak için herhangi bir gereksinim olmadan matematik işlemleri gerçekleştiren yöntemler içerir <xref:System.Math> .</span><span class="sxs-lookup"><span data-stu-id="51cb0-110">For example, in the .NET Class Library, the static <xref:System.Math?displayProperty=nameWithType> class contains methods that perform mathematical operations, without any requirement to store or retrieve data that is unique to a particular instance of the <xref:System.Math> class.</span></span> <span data-ttu-id="51cb0-111">Diğer bir deyişle, aşağıdaki örnekte gösterildiği gibi sınıf adını ve yöntem adını belirterek sınıfının üyelerini uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="51cb0-111">That is, you apply the members of the class by specifying the class name and the method name, as shown in the following example.</span></span>  
  
```csharp  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
```  
  
 <span data-ttu-id="51cb0-112">Tüm sınıf türlerinde olduğu gibi, bir statik sınıf için tür bilgisi, sınıfa başvuran program yüklendiğinde .NET çalışma zamanı tarafından yüklenir.</span><span class="sxs-lookup"><span data-stu-id="51cb0-112">As is the case with all class types, the type information for a static class is loaded by the .NET runtime when the program that references the class is loaded.</span></span> <span data-ttu-id="51cb0-113">Program, sınıf yüklendiğinde tam olarak belirtemez.</span><span class="sxs-lookup"><span data-stu-id="51cb0-113">The program cannot specify exactly when the class is loaded.</span></span> <span data-ttu-id="51cb0-114">Ancak, yüklenmesi ve alanları başlatılmış olması garantidir ve bu sınıfın, sınıf ilk kez bir kez başvurulmadan önce çağrılan statik Oluşturucusu çağırılır.</span><span class="sxs-lookup"><span data-stu-id="51cb0-114">However, it is guaranteed to be loaded and to have its fields initialized and its static constructor called before the class is referenced for the first time in your program.</span></span> <span data-ttu-id="51cb0-115">Statik bir Oluşturucu yalnızca bir kez çağrılır ve programınızın bulunduğu uygulama etki alanının ömrü boyunca statik bir sınıf bellekte kalır.</span><span class="sxs-lookup"><span data-stu-id="51cb0-115">A static constructor is only called one time, and a static class remains in memory for the lifetime of the application domain in which your program resides.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51cb0-116">Yalnızca tek bir örneğinin oluşturulmasına izin veren statik olmayan bir sınıf oluşturmak için, bkz. [C# ' de](/previous-versions/msp-n-p/ff650316(v=pandp.10))tek bir örnek uygulama.</span><span class="sxs-lookup"><span data-stu-id="51cb0-116">To create a non-static class that allows only one instance of itself to be created, see [Implementing Singleton in C#](/previous-versions/msp-n-p/ff650316(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="51cb0-117">Aşağıdaki liste, bir statik sınıfın ana özelliklerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="51cb0-117">The following list provides the main features of a static class:</span></span>  
  
- <span data-ttu-id="51cb0-118">Yalnızca statik üyeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="51cb0-118">Contains only static members.</span></span>  
  
- <span data-ttu-id="51cb0-119">Örneği oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="51cb0-119">Cannot be instantiated.</span></span>  
  
- <span data-ttu-id="51cb0-120">Mühürlü.</span><span class="sxs-lookup"><span data-stu-id="51cb0-120">Is sealed.</span></span>  
  
- <span data-ttu-id="51cb0-121">[Örnek oluşturucular](./instance-constructors.md)içeremez.</span><span class="sxs-lookup"><span data-stu-id="51cb0-121">Cannot contain [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="51cb0-122">Statik sınıf oluşturmak, bu nedenle temelde yalnızca statik üyeler ve özel bir Oluşturucu içeren bir sınıf oluşturma ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="51cb0-122">Creating a static class is therefore basically the same as creating a class that contains only static members and a private constructor.</span></span> <span data-ttu-id="51cb0-123">Özel Oluşturucu sınıfın oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="51cb0-123">A private constructor prevents the class from being instantiated.</span></span> <span data-ttu-id="51cb0-124">Statik sınıf kullanmanın avantajı, derleyicinin yanlışlıkla hiç örnek üye bulunmadığından emin olmak için denetim yapamamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="51cb0-124">The advantage of using a static class is that the compiler can check to make sure that no instance members are accidentally added.</span></span> <span data-ttu-id="51cb0-125">Derleyici, bu sınıfın örneklerinin oluşturuoluşturulamadığı garantisi alacak.</span><span class="sxs-lookup"><span data-stu-id="51cb0-125">The compiler will guarantee that instances of this class cannot be created.</span></span>  
  
 <span data-ttu-id="51cb0-126">Statik sınıflar mühürlenmiş ve bu nedenle devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="51cb0-126">Static classes are sealed and therefore cannot be inherited.</span></span> <span data-ttu-id="51cb0-127">Dışında herhangi bir sınıftan devralınabilir <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="51cb0-127">They cannot inherit from any class except <xref:System.Object>.</span></span> <span data-ttu-id="51cb0-128">Statik sınıflar bir örnek oluşturucu içeremez.</span><span class="sxs-lookup"><span data-stu-id="51cb0-128">Static classes cannot contain an instance constructor.</span></span> <span data-ttu-id="51cb0-129">Ancak, bir statik Oluşturucu içerebilirler.</span><span class="sxs-lookup"><span data-stu-id="51cb0-129">However, they can contain a static constructor.</span></span> <span data-ttu-id="51cb0-130">Statik olmayan sınıflar Ayrıca, sınıf önemsiz olmayan başlatma gerektiren statik üyeler içeriyorsa statik bir Oluşturucu tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="51cb0-130">Non-static classes should also define a static constructor if the class contains static members that require non-trivial initialization.</span></span> <span data-ttu-id="51cb0-131">Daha fazla bilgi için bkz. [statik oluşturucular](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="51cb0-131">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51cb0-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="51cb0-132">Example</span></span>  

 <span data-ttu-id="51cb0-133">Aşağıda, sıcaklığın Fahrenhayt 'e ve Fahrenhayt 'e kadar olan iki yöntem içeren bir statik sınıfa örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51cb0-133">Here is an example of a static class that contains two methods that convert temperature from Celsius to Fahrenheit and from Fahrenheit to Celsius:</span></span>  
  
 [!code-csharp[TemperatureConverter#1](snippets/static-classes-and-static-class-members/Program.cs#1)]  
  
## <a name="static-members"></a><span data-ttu-id="51cb0-134">Statik Üyeler</span><span class="sxs-lookup"><span data-stu-id="51cb0-134">Static Members</span></span>  

 <span data-ttu-id="51cb0-135">Statik olmayan bir sınıf statik yöntemler, alanlar, özellikler veya olaylar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="51cb0-135">A non-static class can contain static methods, fields, properties, or events.</span></span> <span data-ttu-id="51cb0-136">Statik üye, sınıfın bir örneği oluşturulmasa bile bir sınıf üzerinde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="51cb0-136">The static member is callable on a class even when no instance of the class has been created.</span></span> <span data-ttu-id="51cb0-137">Statik üyeye, örnek adı değil, her zaman sınıf adı tarafından erişilir.</span><span class="sxs-lookup"><span data-stu-id="51cb0-137">The static member is always accessed by the class name, not the instance name.</span></span> <span data-ttu-id="51cb0-138">Statik üyenin yalnızca bir kopyası, sınıfının kaç örneğinin oluşturulduğuna bakılmaksızın vardır.</span><span class="sxs-lookup"><span data-stu-id="51cb0-138">Only one copy of a static member exists, regardless of how many instances of the class are created.</span></span> <span data-ttu-id="51cb0-139">Statik yöntemler ve özellikler, kendi kapsayıcı türündeki statik olmayan alanlara ve olaylara erişemez ve açıkça bir yöntem parametresine geçirilmediği takdirde herhangi bir nesnenin örnek değişkenine erişemez.</span><span class="sxs-lookup"><span data-stu-id="51cb0-139">Static methods and properties cannot access non-static fields and events in their containing type, and they cannot access an instance variable of any object unless it's explicitly passed in a method parameter.</span></span>  
  
 <span data-ttu-id="51cb0-140">Statik olmayan bir sınıfı bazı statik üyelere bildirmek daha tipik bir deyişle, bir sınıfın tamamını statik olarak bildirmek daha normaldir.</span><span class="sxs-lookup"><span data-stu-id="51cb0-140">It is more typical to declare a non-static class with some static members, than to declare an entire class as static.</span></span> <span data-ttu-id="51cb0-141">Statik alanların iki ortak kullanımı, örneği oluşturulmuş nesne sayısının sayısını tutmak veya tüm örnekler arasında paylaşılması gereken bir değeri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51cb0-141">Two common uses of static fields are to keep a count of the number of objects that have been instantiated, or to store a value that must be shared among all instances.</span></span>  
  
 <span data-ttu-id="51cb0-142">Statik yöntemler, sınıfın herhangi bir örneğine değil, sınıfına ait olduğundan aşırı yüklenebilir ancak geçersiz kılınmaz.</span><span class="sxs-lookup"><span data-stu-id="51cb0-142">Static methods can be overloaded but not overridden, because they belong to the class, and not to any instance of the class.</span></span>  
  
 <span data-ttu-id="51cb0-143">Bir alan olarak bildirilemez olsa da `static const` , bir [const](../../language-reference/keywords/const.md) alanı, davranışında temelde statiktir.</span><span class="sxs-lookup"><span data-stu-id="51cb0-143">Although a field cannot be declared as `static const`, a [const](../../language-reference/keywords/const.md) field is essentially static in its behavior.</span></span> <span data-ttu-id="51cb0-144">Tür örneklerine değil, türüne aittir.</span><span class="sxs-lookup"><span data-stu-id="51cb0-144">It belongs to the type, not to instances of the type.</span></span> <span data-ttu-id="51cb0-145">Bu nedenle, `const` alanlara `ClassName.MemberName` statik alanlar için kullanılan aynı gösterim kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="51cb0-145">Therefore, `const` fields can be accessed by using the same `ClassName.MemberName` notation that's used for static fields.</span></span> <span data-ttu-id="51cb0-146">Nesne örneği gerekli değil.</span><span class="sxs-lookup"><span data-stu-id="51cb0-146">No object instance is required.</span></span>  
  
 <span data-ttu-id="51cb0-147">C# statik yerel değişkenleri (yani, yöntem kapsamında belirtilen değişkenleri) desteklemez.</span><span class="sxs-lookup"><span data-stu-id="51cb0-147">C# does not support static local variables (that is, variables that are declared in method scope).</span></span>  
  
 <span data-ttu-id="51cb0-148">`static`Aşağıdaki örnekte gösterildiği gibi, üyenin dönüş türünden önce anahtar sözcüğünü kullanarak statik sınıf üyeleri bildirirsiniz:</span><span class="sxs-lookup"><span data-stu-id="51cb0-148">You declare static class members by using the `static` keyword before the return type of the member, as shown in the following example:</span></span>  
  
 [!code-csharp[AutomobileExample#2](snippets/static-classes-and-static-class-members/Program.cs#2)]  
  
 <span data-ttu-id="51cb0-149">Statik üyeler, statik üyeye ilk kez erişilmeden ve statik oluşturucu bir tane varsa, önce başlatılır.</span><span class="sxs-lookup"><span data-stu-id="51cb0-149">Static members are initialized before the static member is accessed for the first time and before the static constructor, if there is one, is called.</span></span> <span data-ttu-id="51cb0-150">Statik sınıf üyesine erişmek için, aşağıdaki örnekte gösterildiği gibi, üyenin konumunu belirtmek için değişken adı yerine sınıfın adını kullanın:</span><span class="sxs-lookup"><span data-stu-id="51cb0-150">To access a static class member, use the name of the class instead of a variable name to specify the location of the member, as shown in the following example:</span></span>  
  
 [!code-csharp[AccessingStaticMembers#3](snippets/static-classes-and-static-class-members/Program.cs#3)]  
  
 <span data-ttu-id="51cb0-151">Sınıfınız statik alanlar içeriyorsa, sınıfı yüklendiğinde bunları başlatan bir statik Oluşturucu sağlayın.</span><span class="sxs-lookup"><span data-stu-id="51cb0-151">If your class contains static fields, provide a static constructor that initializes them when the class is loaded.</span></span>  
  
 <span data-ttu-id="51cb0-152">Statik bir yönteme yapılan çağrı, Microsoft ara dili (MSIL) içinde bir çağrı yönergesi oluşturur, ancak bir örnek yöntemine yapılan çağrı bir yönerge oluşturur; `callvirt` Bu da null nesne başvurularını denetler.</span><span class="sxs-lookup"><span data-stu-id="51cb0-152">A call to a static method generates a call instruction in Microsoft intermediate language (MSIL), whereas a call to an instance method generates a `callvirt` instruction, which also checks for null object references.</span></span> <span data-ttu-id="51cb0-153">Ancak, ikisi arasındaki performans farkı çoğu zaman önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="51cb0-153">However, most of the time the performance difference between the two is not significant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="51cb0-154">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="51cb0-154">C# Language Specification</span></span>  

<span data-ttu-id="51cb0-155">Daha fazla bilgi için [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [statik sınıflar](~/_csharplang/spec/classes.md#static-classes) ve [statik ve örnek üyeleri](~/_csharplang/spec/classes.md#static-and-instance-members) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="51cb0-155">For more information, see [Static classes](~/_csharplang/spec/classes.md#static-classes) and [Static and instance members](~/_csharplang/spec/classes.md#static-and-instance-members) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="51cb0-156">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="51cb0-156">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="51cb0-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51cb0-157">See also</span></span>

- [<span data-ttu-id="51cb0-158">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="51cb0-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="51cb0-159">static</span><span class="sxs-lookup"><span data-stu-id="51cb0-159">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="51cb0-160">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="51cb0-160">Classes</span></span>](./classes.md)
- [<span data-ttu-id="51cb0-161">sınıfı</span><span class="sxs-lookup"><span data-stu-id="51cb0-161">class</span></span>](../../language-reference/keywords/class.md)
- [<span data-ttu-id="51cb0-162">Statik Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="51cb0-162">Static Constructors</span></span>](./static-constructors.md)
- [<span data-ttu-id="51cb0-163">Örnek Oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="51cb0-163">Instance Constructors</span></span>](./instance-constructors.md)
