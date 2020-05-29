---
title: Koleksiyonlar (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 30aa3e34f362f34fc601f90ee61613acd6e4bc68
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201128"
---
# <a name="collections-c"></a><span data-ttu-id="f7abd-102">Koleksiyonlar (C#)</span><span class="sxs-lookup"><span data-stu-id="f7abd-102">Collections (C#)</span></span>

<span data-ttu-id="f7abd-103">Birçok uygulama için ilgili nesne grupları oluşturmak ve yönetmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="f7abd-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="f7abd-104">Nesneleri gruplandırmanın iki yolu vardır: nesne dizileri oluşturarak ve nesne koleksiyonları oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="f7abd-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="f7abd-105">Diziler, kesin olarak belirlenmiş sabit sayıda nesne oluşturmak ve bunlarla çalışmak için en yararlı seçenektir.</span><span class="sxs-lookup"><span data-stu-id="f7abd-105">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="f7abd-106">Diziler hakkında daha fazla bilgi için bkz. [diziler](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="f7abd-106">For information about arrays, see [Arrays](../arrays/index.md).</span></span>

<span data-ttu-id="f7abd-107">Koleksiyonlar, nesne gruplarıyla çalışmak için daha esnek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7abd-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="f7abd-108">Dizilerden farklı olarak, çalıştığınız nesne grubu, uygulama değişikliğinin ihtiyaçlarına göre dinamik olarak büyüyebilir ve küçülebilir.</span><span class="sxs-lookup"><span data-stu-id="f7abd-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="f7abd-109">Bazı koleksiyonlar için, anahtarı kullanarak nesneyi hızlı bir şekilde alabilmeniz için koleksiyona yerleştirdiğiniz herhangi bir nesneye bir anahtar atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7abd-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="f7abd-110">Koleksiyon bir sınıftır, bu nedenle bu koleksiyona öğe ekleyebilmeniz için önce sınıfın bir örneğini bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7abd-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="f7abd-111">Koleksiyonunuz yalnızca bir veri türünün öğelerini içeriyorsa, ad alanındaki sınıflardan birini kullanabilirsiniz <xref:System.Collections.Generic?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f7abd-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f7abd-112">Genel bir koleksiyon, tür güvenliğini, başka bir veri türü eklenememesi için uygular.</span><span class="sxs-lookup"><span data-stu-id="f7abd-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="f7abd-113">Genel koleksiyondan bir öğe aldığınızda, veri türünü belirlememek veya dönüştürmek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7abd-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="f7abd-114">Bu konudaki örnekler için [using](../../language-reference/keywords/using-directive.md) `System.Collections.Generic` ve ad alanları için using yönergelerini içerir `System.Linq` .</span><span class="sxs-lookup"><span data-stu-id="f7abd-114">For the examples in this topic, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

 <span data-ttu-id="f7abd-115">**Bu konuda**</span><span class="sxs-lookup"><span data-stu-id="f7abd-115">**In this topic**</span></span>

- [<span data-ttu-id="f7abd-116">Basit bir koleksiyon kullanma</span><span class="sxs-lookup"><span data-stu-id="f7abd-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)

- [<span data-ttu-id="f7abd-117">Koleksiyon türleri</span><span class="sxs-lookup"><span data-stu-id="f7abd-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)

  - [<span data-ttu-id="f7abd-118">System. Collections. Generic sınıfları</span><span class="sxs-lookup"><span data-stu-id="f7abd-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)

  - [<span data-ttu-id="f7abd-119">System. Collections. eşzamanlı sınıflar</span><span class="sxs-lookup"><span data-stu-id="f7abd-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)

  - [<span data-ttu-id="f7abd-120">System. Collections sınıfları</span><span class="sxs-lookup"><span data-stu-id="f7abd-120">System.Collections Classes</span></span>](#BKMK_Collections)

- [<span data-ttu-id="f7abd-121">Anahtar/değer çiftleri koleksiyonu uygulama</span><span class="sxs-lookup"><span data-stu-id="f7abd-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)

- [<span data-ttu-id="f7abd-122">Koleksiyona erişmek için LINQ kullanma</span><span class="sxs-lookup"><span data-stu-id="f7abd-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)

- [<span data-ttu-id="f7abd-123">Bir koleksiyonu sıralama</span><span class="sxs-lookup"><span data-stu-id="f7abd-123">Sorting a Collection</span></span>](#BKMK_Sorting)

- [<span data-ttu-id="f7abd-124">Özel bir koleksiyon tanımlama</span><span class="sxs-lookup"><span data-stu-id="f7abd-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)

- [<span data-ttu-id="f7abd-125">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="f7abd-125">Iterators</span></span>](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="f7abd-126">Basit bir koleksiyon kullanma</span><span class="sxs-lookup"><span data-stu-id="f7abd-126">Using a Simple Collection</span></span>

<span data-ttu-id="f7abd-127">Bu bölümdeki örneklerde <xref:System.Collections.Generic.List%601> , türü kesin belirlenmiş bir nesne listesiyle çalışmanıza olanak sağlayan genel sınıfı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="f7abd-128">Aşağıdaki örnek, bir dizi dizenin bir listesini oluşturur ve sonra, bir [foreach](../../language-reference/keywords/foreach-in.md) ifadesi kullanarak dizeler arasında yinelenir.</span><span class="sxs-lookup"><span data-stu-id="f7abd-128">The following example creates a list of strings and then iterates through the strings by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

```csharp
// Create a list of strings.
var salmons = new List<string>();
salmons.Add("chinook");
salmons.Add("coho");
salmons.Add("pink");
salmons.Add("sockeye");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="f7abd-129">Bir koleksiyonun içeriği önceden biliniyorsa, koleksiyonu başlatmak için bir *koleksiyon başlatıcısı* kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7abd-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="f7abd-130">Daha fazla bilgi için bkz. [nesne ve koleksiyon başlatıcıları](../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="f7abd-130">For more information, see [Object and Collection Initializers](../classes-and-structs/object-and-collection-initializers.md).</span></span>

<span data-ttu-id="f7abd-131">Aşağıdaki örnek, koleksiyona öğe eklemek için bir koleksiyon başlatıcısı kullanılması dışında, önceki örnekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="f7abd-132">Bir [for](../../language-reference/keywords/for.md) `foreach` koleksiyon aracılığıyla yinelemek için bir for ifadesinin yerine bir for ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7abd-132">You can use a [for](../../language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="f7abd-133">Bunu, koleksiyon öğelerine dizin konumuna erişerek gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7abd-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="f7abd-134">Öğelerin dizini 0 ' dan başlar ve öğe sayısı eksi 1 ' den sona erer.</span><span class="sxs-lookup"><span data-stu-id="f7abd-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="f7abd-135">Aşağıdaki örnek yerine kullanarak bir koleksiyonun öğeleri boyunca yinelenir `for` `foreach` .</span><span class="sxs-lookup"><span data-stu-id="f7abd-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

for (var index = 0; index < salmons.Count; index++)
{
    Console.Write(salmons[index] + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="f7abd-136">Aşağıdaki örnek, kaldırılacak nesneyi belirterek koleksiyondan bir öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-136">The following example removes an element from the collection by specifying the object to remove.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Remove an element from the list by specifying
// the object.
salmons.Remove("coho");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook pink sockeye
```

<span data-ttu-id="f7abd-137">Aşağıdaki örnek, genel bir listeden öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="f7abd-138">Bir ifade yerine `foreach` , azalan düzende yinelenen bir [for](../../language-reference/keywords/for.md) deyimleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-138">Instead of a `foreach` statement, a [for](../../language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="f7abd-139">Bunun nedeni, <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemin kaldırılan bir öğeden sonra öğelerin daha düşük bir dizin değerine sahip olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="f7abd-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

```csharp
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

// Remove odd numbers.
for (var index = numbers.Count - 1; index >= 0; index--)
{
    if (numbers[index] % 2 == 1)
    {
        // Remove the element by specifying
        // the zero-based index in the list.
        numbers.RemoveAt(index);
    }
}

// Iterate through the list.
// A lambda expression is placed in the ForEach method
// of the List(T) object.
numbers.ForEach(
    number => Console.Write(number + " "));
// Output: 0 2 4 6 8
```

<span data-ttu-id="f7abd-140">İçindeki öğe türleri için <xref:System.Collections.Generic.List%601> kendi sınıfınızı de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7abd-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="f7abd-141">Aşağıdaki örnekte, `Galaxy` tarafından kullanılan sınıfı <xref:System.Collections.Generic.List%601> kodda tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

```csharp
private static void IterateThroughList()
{
    var theGalaxies = new List<Galaxy>
        {
            new Galaxy() { Name="Tadpole", MegaLightYears=400},
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},
            new Galaxy() { Name="Milky Way", MegaLightYears=0},
            new Galaxy() { Name="Andromeda", MegaLightYears=3}
        };

    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);
    }

    // Output:
    //  Tadpole  400
    //  Pinwheel  25
    //  Milky Way  0
    //  Andromeda  3
}

public class Galaxy
{
    public string Name { get; set; }
    public int MegaLightYears { get; set; }
}
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a><span data-ttu-id="f7abd-142">Koleksiyon türleri</span><span class="sxs-lookup"><span data-stu-id="f7abd-142">Kinds of Collections</span></span>

<span data-ttu-id="f7abd-143">Birçok ortak koleksiyon .NET Framework tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-143">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="f7abd-144">Her koleksiyon türü belirli bir amaç için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-144">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="f7abd-145">Ortak koleksiyon sınıflarından bazıları bu bölümde açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="f7abd-145">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="f7abd-146"><xref:System.Collections.Generic> sınıflar</span><span class="sxs-lookup"><span data-stu-id="f7abd-146"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="f7abd-147"><xref:System.Collections.Concurrent> sınıflar</span><span class="sxs-lookup"><span data-stu-id="f7abd-147"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="f7abd-148"><xref:System.Collections> sınıflar</span><span class="sxs-lookup"><span data-stu-id="f7abd-148"><xref:System.Collections> classes</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="f7abd-149">System. Collections. Generic sınıfları</span><span class="sxs-lookup"><span data-stu-id="f7abd-149">System.Collections.Generic Classes</span></span>

<span data-ttu-id="f7abd-150">Ad alanındaki sınıflardan birini kullanarak genel bir koleksiyon oluşturabilirsiniz <xref:System.Collections.Generic> .</span><span class="sxs-lookup"><span data-stu-id="f7abd-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="f7abd-151">Genel bir koleksiyon, koleksiyondaki her öğe aynı veri türüne sahip olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="f7abd-152">Genel bir koleksiyon, yalnızca istenen veri türünün eklenmesine izin vererek güçlü yazma uygular.</span><span class="sxs-lookup"><span data-stu-id="f7abd-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="f7abd-153">Aşağıdaki tabloda, ad alanının sık kullanılan sınıflarının bazıları listelenmektedir <xref:System.Collections.Generic?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="f7abd-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="f7abd-154">Sınıf</span><span class="sxs-lookup"><span data-stu-id="f7abd-154">Class</span></span>|<span data-ttu-id="f7abd-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7abd-155">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="f7abd-156">Anahtara göre düzenlenen anahtar/değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7abd-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="f7abd-157">Dizin tarafından erişilebilen nesnelerin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7abd-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="f7abd-158">Listeleri aramak, sıralamak ve değiştirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7abd-158">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="f7abd-159">Nesnelerin ilk, ilk çıkar (FıFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7abd-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="f7abd-160">İlişkili uygulamaya göre anahtara göre sıralanan anahtar/değer çiftleri koleksiyonunu temsil eder <xref:System.Collections.Generic.IComparer%601> .</span><span class="sxs-lookup"><span data-stu-id="f7abd-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="f7abd-161">Nesnelerin son, ilk çıkar (LıFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7abd-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="f7abd-162">Daha fazla bilgi için bkz. [yaygın olarak kullanılan koleksiyon türleri](../../../standard/collections/commonly-used-collection-types.md), [koleksiyon sınıfı seçme](../../../standard/collections/selecting-a-collection-class.md)ve <xref:System.Collections.Generic> .</span><span class="sxs-lookup"><span data-stu-id="f7abd-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="f7abd-163">System. Collections. eşzamanlı sınıflar</span><span class="sxs-lookup"><span data-stu-id="f7abd-163">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="f7abd-164">.NET Framework 4 veya daha yeni bir sürümde, <xref:System.Collections.Concurrent> ad alanındaki koleksiyonlar, koleksiyon öğelerine birden çok iş parçacığından erişmek için verimli iş parçacığı güvenli işlemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7abd-164">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="f7abd-165"><xref:System.Collections.Concurrent> <xref:System.Collections.Generic?displayProperty=nameWithType> <xref:System.Collections?displayProperty=nameWithType> Birden çok iş parçacığının koleksiyona aynı anda eriştiği her seferinde ve ad alanındaki ilgili türler yerine ad alanındaki sınıflar kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="f7abd-166">Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonlar](../../../standard/collections/thread-safe/index.md) ve <xref:System.Collections.Concurrent> .</span><span class="sxs-lookup"><span data-stu-id="f7abd-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="f7abd-167">Ad alanına dahil edilen bazı sınıflar <xref:System.Collections.Concurrent> ,, ve ' dir <xref:System.Collections.Concurrent.BlockingCollection%601> <xref:System.Collections.Concurrent.ConcurrentDictionary%602> <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Concurrent.ConcurrentStack%601> .</span><span class="sxs-lookup"><span data-stu-id="f7abd-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="f7abd-168">System. Collections sınıfları</span><span class="sxs-lookup"><span data-stu-id="f7abd-168">System.Collections Classes</span></span>

<span data-ttu-id="f7abd-169"><xref:System.Collections?displayProperty=nameWithType>Ad alanındaki sınıflar öğeleri özel olarak yazılmış nesneler olarak depolamaz, ancak türünden nesneler olarak depolamaz `Object` .</span><span class="sxs-lookup"><span data-stu-id="f7abd-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="f7abd-170">Mümkün olduğunda, ad alanındaki <xref:System.Collections.Generic?displayProperty=nameWithType> Eski türler yerine ad alanı veya ad alanı içinde genel koleksiyonları kullanmanız gerekir <xref:System.Collections.Concurrent> `System.Collections` .</span><span class="sxs-lookup"><span data-stu-id="f7abd-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="f7abd-171">Aşağıdaki tabloda, ad alanında sık kullanılan sınıfların bazıları listelenmektedir `System.Collections` :</span><span class="sxs-lookup"><span data-stu-id="f7abd-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="f7abd-172">Sınıf</span><span class="sxs-lookup"><span data-stu-id="f7abd-172">Class</span></span>|<span data-ttu-id="f7abd-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7abd-173">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="f7abd-174">Boyutu dinamik olarak gerektiği şekilde arttığı bir nesne dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7abd-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="f7abd-175">Anahtarın karma koduna göre düzenlenmiş anahtar/değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7abd-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="f7abd-176">Nesnelerin ilk, ilk çıkar (FıFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7abd-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="f7abd-177">Nesnelerin son, ilk çıkar (LıFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f7abd-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="f7abd-178"><xref:System.Collections.Specialized>Ad alanı, yalnızca dize toplamaları ve bağlantılı liste ve karma sözlük gibi özelleştirilmiş ve kesin tür belirtilmiş koleksiyon sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7abd-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="f7abd-179">Anahtar/değer çiftleri koleksiyonu uygulama</span><span class="sxs-lookup"><span data-stu-id="f7abd-179">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="f7abd-180"><xref:System.Collections.Generic.Dictionary%602>Genel koleksiyon, her bir öğenin anahtarını kullanarak bir koleksiyondaki öğelere erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7abd-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="f7abd-181">Sözlüğe eklenen her ekleme bir değerden ve ilişkili anahtarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="f7abd-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="f7abd-182">`Dictionary`Sınıfı bir karma tablo olarak uygulandığından, anahtarını kullanarak bir değerin alınması hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="f7abd-183">Aşağıdaki örnek bir koleksiyon oluşturur `Dictionary` ve bir ifade kullanarak sözlükten yinelenir `foreach` .</span><span class="sxs-lookup"><span data-stu-id="f7abd-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>

```csharp
private static void IterateThruDictionary()
{
    Dictionary<string, Element> elements = BuildDictionary();

    foreach (KeyValuePair<string, Element> kvp in elements)
    {
        Element theElement = kvp.Value;

        Console.WriteLine("key: " + kvp.Key);
        Console.WriteLine("values: " + theElement.Symbol + " " +
            theElement.Name + " " + theElement.AtomicNumber);
    }
}

private static Dictionary<string, Element> BuildDictionary()
{
    var elements = new Dictionary<string, Element>();

    AddToDictionary(elements, "K", "Potassium", 19);
    AddToDictionary(elements, "Ca", "Calcium", 20);
    AddToDictionary(elements, "Sc", "Scandium", 21);
    AddToDictionary(elements, "Ti", "Titanium", 22);

    return elements;
}

private static void AddToDictionary(Dictionary<string, Element> elements,
    string symbol, string name, int atomicNumber)
{
    Element theElement = new Element();

    theElement.Symbol = symbol;
    theElement.Name = name;
    theElement.AtomicNumber = atomicNumber;

    elements.Add(key: theElement.Symbol, value: theElement);
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<span data-ttu-id="f7abd-184">Koleksiyonu oluşturmak için bir koleksiyon başlatıcısı kullanmak yerine, `Dictionary` `BuildDictionary` ve `AddToDictionary` yöntemlerini aşağıdaki yöntemle değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7abd-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

```csharp
private static Dictionary<string, Element> BuildDictionary2()
{
    return new Dictionary<string, Element>
    {
        {"K",
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        {"Ca",
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        {"Sc",
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        {"Ti",
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}
```

<span data-ttu-id="f7abd-185">Aşağıdaki örnek, <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> <xref:System.Collections.Generic.Dictionary%602.Item%2A> `Dictionary` bir öğeyi anahtara göre hızlı bir şekilde bulmak için yöntemini ve özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="f7abd-186">`Item`Özelliği, `elements` `elements[symbol]` C# ' de kullanarak koleksiyondaki bir öğeye erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7abd-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>

```csharp
private static void FindInDictionary(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    if (elements.ContainsKey(symbol) == false)
    {
        Console.WriteLine(symbol + " not found");
    }
    else
    {
        Element theElement = elements[symbol];
        Console.WriteLine("found: " + theElement.Name);
    }
}
```

<span data-ttu-id="f7abd-187">Aşağıdaki örnek bunun yerine, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> bir öğeyi anahtara göre hızlı bir şekilde bulmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

```csharp
private static void FindInDictionary2(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    Element theElement = null;
    if (elements.TryGetValue(symbol, out theElement) == false)
        Console.WriteLine(symbol + " not found");
    else
        Console.WriteLine("found: " + theElement.Name);
}
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="f7abd-188">Koleksiyona erişmek için LINQ kullanma</span><span class="sxs-lookup"><span data-stu-id="f7abd-188">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="f7abd-189">LINQ (dil ile tümleşik sorgu), koleksiyonlara erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7abd-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="f7abd-190">LINQ sorguları filtreleme, sıralama ve gruplama özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7abd-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="f7abd-191">Daha fazla bilgi için bkz. [C# ' de LINQ Ile çalışmaya](linq/index.md)başlama.</span><span class="sxs-lookup"><span data-stu-id="f7abd-191">For more information, see [Getting Started with LINQ in C#](linq/index.md).</span></span>

<span data-ttu-id="f7abd-192">Aşağıdaki örnek, genel olarak bir LINQ sorgusu çalıştırır `List` .</span><span class="sxs-lookup"><span data-stu-id="f7abd-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="f7abd-193">LINQ sorgusu, sonuçları içeren farklı bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7abd-193">The LINQ query returns a different collection that contains the results.</span></span>

```csharp
private static void ShowLINQ()
{
    List<Element> elements = BuildList();

    // LINQ Query.
    var subset = from theElement in elements
                 where theElement.AtomicNumber < 22
                 orderby theElement.Name
                 select theElement;

    foreach (Element theElement in subset)
    {
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);
    }

    // Output:
    //  Calcium 20
    //  Potassium 19
    //  Scandium 21
}

private static List<Element> BuildList()
{
    return new List<Element>
    {
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a><span data-ttu-id="f7abd-194">Bir koleksiyonu sıralama</span><span class="sxs-lookup"><span data-stu-id="f7abd-194">Sorting a Collection</span></span>

<span data-ttu-id="f7abd-195">Aşağıdaki örnek bir koleksiyonu sıralamak için bir yordam gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7abd-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="f7abd-196">Örnek, `Car` içinde depolanan sınıfının örneklerini sıralar <xref:System.Collections.Generic.List%601> .</span><span class="sxs-lookup"><span data-stu-id="f7abd-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="f7abd-197">`Car`Sınıfı, <xref:System.IComparable%601> yönteminin uygulanması için arabirimini uygular <xref:System.IComparable%601.CompareTo%2A> .</span><span class="sxs-lookup"><span data-stu-id="f7abd-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="f7abd-198">Yöntemine yapılan her çağrı, <xref:System.IComparable%601.CompareTo%2A> sıralama için kullanılan tek bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="f7abd-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="f7abd-199">Yöntemdeki Kullanıcı tarafından yazılan kod, `CompareTo` geçerli nesnenin her bir karşılaştırması için başka bir nesneyle ilgili bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7abd-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="f7abd-200">Geçerli nesne diğer nesneden daha küçükse döndürülen değer sıfırdan küçük, geçerli nesne diğer nesneden büyükse sıfırdan büyük ve eşitse sıfır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="f7abd-201">Bu, büyük, küçüktür ve eşittir ölçütlerine göre kod içinde tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7abd-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="f7abd-202">Yönteminde, `ListCars` `cars.Sort()` ifade listeyi sıralar.</span><span class="sxs-lookup"><span data-stu-id="f7abd-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="f7abd-203">Öğesinin yöntemine yapılan bu çağrı, <xref:System.Collections.Generic.List%601.Sort%2A> <xref:System.Collections.Generic.List%601> `CompareTo` yönteminin içindeki nesneler için otomatik olarak çağrılmasına neden olur `Car` `List` .</span><span class="sxs-lookup"><span data-stu-id="f7abd-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

```csharp
private static void ListCars()
{
    var cars = new List<Car>
    {
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},
        { new Car() { Name = "car2", Color = "red", Speed = 50}},
        { new Car() { Name = "car3", Color = "green", Speed = 10}},
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},
        { new Car() { Name = "car6", Color = "red", Speed = 60}},
        { new Car() { Name = "car7", Color = "green", Speed = 50}}
    };

    // Sort the cars by color alphabetically, and then by speed
    // in descending order.
    cars.Sort();

    // View all of the cars.
    foreach (Car thisCar in cars)
    {
        Console.Write(thisCar.Color.PadRight(5) + " ");
        Console.Write(thisCar.Speed.ToString() + " ");
        Console.Write(thisCar.Name);
        Console.WriteLine();
    }

    // Output:
    //  blue  50 car4
    //  blue  30 car5
    //  blue  20 car1
    //  green 50 car7
    //  green 10 car3
    //  red   60 car6
    //  red   50 car2
}

public class Car : IComparable<Car>
{
    public string Name { get; set; }
    public int Speed { get; set; }
    public string Color { get; set; }

    public int CompareTo(Car other)
    {
        // A call to this method makes a single comparison that is
        // used for sorting.

        // Determine the relative order of the objects being compared.
        // Sort by color alphabetically, and then by speed in
        // descending order.

        // Compare the colors.
        int compare;
        compare = String.Compare(this.Color, other.Color, true);

        // If the colors are the same, compare the speeds.
        if (compare == 0)
        {
            compare = this.Speed.CompareTo(other.Speed);

            // Use descending order for speed.
            compare = -compare;
        }

        return compare;
    }
}
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a><span data-ttu-id="f7abd-204">Özel bir koleksiyon tanımlama</span><span class="sxs-lookup"><span data-stu-id="f7abd-204">Defining a Custom Collection</span></span>

<span data-ttu-id="f7abd-205">Veya arabirimini uygulayarak bir koleksiyon tanımlayabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="f7abd-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span>

<span data-ttu-id="f7abd-206">Özel bir koleksiyon tanımlamanızı mümkün olsa da, bu konunun önceki kısımlarında yer alan [koleksiyonlar türlerinde](#BKMK_KindsOfCollections) açıklanan .NET Framework dahil edilen koleksiyonları kullanmak genellikle daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="f7abd-206">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this topic.</span></span>

<span data-ttu-id="f7abd-207">Aşağıdaki örnek adlı özel bir koleksiyon sınıfını tanımlar `AllColors` .</span><span class="sxs-lookup"><span data-stu-id="f7abd-207">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="f7abd-208">Bu sınıf, <xref:System.Collections.IEnumerable> yönteminin uygulanması için arabirimini uygular <xref:System.Collections.IEnumerable.GetEnumerator%2A> .</span><span class="sxs-lookup"><span data-stu-id="f7abd-208">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="f7abd-209">`GetEnumerator`Yöntemi, sınıfının bir örneğini döndürür `ColorEnumerator` .</span><span class="sxs-lookup"><span data-stu-id="f7abd-209">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="f7abd-210">`ColorEnumerator`<xref:System.Collections.IEnumerator> <xref:System.Collections.IEnumerator.Current%2A> özelliği, <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi ve yönteminin uygulanması için arabirimini uygular <xref:System.Collections.IEnumerator.Reset%2A> .</span><span class="sxs-lookup"><span data-stu-id="f7abd-210">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

```csharp
private static void ListColors()
{
    var colors = new AllColors();

    foreach (Color theColor in colors)
    {
        Console.Write(theColor.Name + " ");
    }
    Console.WriteLine();
    // Output: red blue green
}

// Collection class.
public class AllColors : System.Collections.IEnumerable
{
    Color[] _colors =
    {
        new Color() { Name = "red" },
        new Color() { Name = "blue" },
        new Color() { Name = "green" }
    };

    public System.Collections.IEnumerator GetEnumerator()
    {
        return new ColorEnumerator(_colors);

        // Instead of creating a custom enumerator, you could
        // use the GetEnumerator of the array.
        //return _colors.GetEnumerator();
    }

    // Custom enumerator.
    private class ColorEnumerator : System.Collections.IEnumerator
    {
        private Color[] _colors;
        private int _position = -1;

        public ColorEnumerator(Color[] colors)
        {
            _colors = colors;
        }

        object System.Collections.IEnumerator.Current
        {
            get
            {
                return _colors[_position];
            }
        }

        bool System.Collections.IEnumerator.MoveNext()
        {
            _position++;
            return (_position < _colors.Length);
        }

        void System.Collections.IEnumerator.Reset()
        {
            _position = -1;
        }
    }
}

// Element class.
public class Color
{
    public string Name { get; set; }
}
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a><span data-ttu-id="f7abd-211">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="f7abd-211">Iterators</span></span>

<span data-ttu-id="f7abd-212">Bir *Yineleyici* , bir koleksiyon üzerinde özel bir yineleme gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-212">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="f7abd-213">Yineleyici bir yöntem veya `get` erişimci olabilir.</span><span class="sxs-lookup"><span data-stu-id="f7abd-213">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="f7abd-214">Bir yineleyici, tek seferde koleksiyonun her bir öğesini döndürmek için bir [yield return](../../language-reference/keywords/yield.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-214">An iterator uses a [yield return](../../language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="f7abd-215">Bir [foreach](../../language-reference/keywords/foreach-in.md) ifadesi kullanarak bir yineleyici çağırın.</span><span class="sxs-lookup"><span data-stu-id="f7abd-215">You call an iterator by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="f7abd-216">Döngünün her yinelemesi `foreach` yineleyiciyi çağırır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-216">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="f7abd-217">`yield return`Yineleyiciden bir ifadeye ulaşıldığında, bir ifade döndürülür ve koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="f7abd-217">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="f7abd-218">Bu konumdan, yineleyici bir sonraki sefer çağrıldığında yürütme yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-218">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="f7abd-219">Daha fazla bilgi için bkz. [yineleyiciler (C#)](./iterators.md).</span><span class="sxs-lookup"><span data-stu-id="f7abd-219">For more information, see [Iterators (C#)](./iterators.md).</span></span>

<span data-ttu-id="f7abd-220">Aşağıdaki örnek bir yineleyici yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-220">The following example uses an iterator method.</span></span> <span data-ttu-id="f7abd-221">Yineleyici yöntemi `yield return` [için bir for](../../language-reference/keywords/for.md) döngüsü içinde olan bir ifade vardır.</span><span class="sxs-lookup"><span data-stu-id="f7abd-221">The iterator method has a `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="f7abd-222">`ListEvenNumbers`Yönteminde, ifade gövdesinin her yinelemesi, `foreach` bir sonraki ifadeye devam eden Yineleyici yöntemine bir çağrı oluşturur `yield return` .</span><span class="sxs-lookup"><span data-stu-id="f7abd-222">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>

```csharp
private static void ListEvenNumbers()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    Console.WriteLine();
    // Output: 6 8 10 12 14 16 18
}

private static IEnumerable<int> EvenSequence(
    int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (var number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="f7abd-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7abd-223">See also</span></span>

- [<span data-ttu-id="f7abd-224">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="f7abd-224">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="f7abd-225">Programlama kavramları (C#)</span><span class="sxs-lookup"><span data-stu-id="f7abd-225">Programming Concepts (C#)</span></span>](./index.md)
- [<span data-ttu-id="f7abd-226">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="f7abd-226">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="f7abd-227">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="f7abd-227">LINQ to Objects (C#)</span></span>](./linq/linq-to-objects.md)
- [<span data-ttu-id="f7abd-228">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f7abd-228">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="f7abd-229">Koleksiyonlar ve veri yapıları</span><span class="sxs-lookup"><span data-stu-id="f7abd-229">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="f7abd-230">Koleksiyon Sınıfı Seçme</span><span class="sxs-lookup"><span data-stu-id="f7abd-230">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="f7abd-231">Koleksiyonlar Içinde karşılaştırmalar ve sıralamalar</span><span class="sxs-lookup"><span data-stu-id="f7abd-231">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="f7abd-232">Genel Koleksiyonlar ne zaman kullanılır?</span><span class="sxs-lookup"><span data-stu-id="f7abd-232">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
