---
description: 'Hakkında daha fazla bilgi edinin: sorgu Işlemlerinde tür Ilişkileri (Visual Basic)'
title: Sorgu İşlemlerinde Tür İlişkileri
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: b6a59308e76afdcf1aaf7084904b9925cd5bef14
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428226"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="85a21-103">LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85a21-103">Type Relationships in Query Operations (Visual Basic)</span></span>

<span data-ttu-id="85a21-104">Language-Integrated Query (LINQ) sorgu işlemlerinde kullanılan değişkenler kesin olarak türdedir ve birbirleriyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85a21-104">Variables used in Language-Integrated Query (LINQ) query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="85a21-105">Güçlü yazma, veri kaynağında, sorgunun kendisinde ve sorgu yürütmesinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="85a21-105">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="85a21-106">Aşağıdaki çizimde, bir LINQ sorgusunu tanımlamak için kullanılan terimler tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="85a21-106">The following illustration identifies terms used to describe a LINQ query.</span></span> <span data-ttu-id="85a21-107">Bir sorgunun kısımları hakkında daha fazla bilgi için bkz. [temel sorgu işlemleri (Visual Basic)](basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="85a21-107">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](basic-query-operations.md).</span></span>

![Öğeleri vurgulanmış bir sözde kod sorgusunu gösteren ekran görüntüsü.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

<span data-ttu-id="85a21-109">Sorgudaki aralık değişkeninin türü, veri kaynağındaki öğelerin türüyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85a21-109">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="85a21-110">Sorgu değişkeninin türü, yan tümcesinde tanımlanan dizi öğesiyle uyumlu olmalıdır `Select` .</span><span class="sxs-lookup"><span data-stu-id="85a21-110">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="85a21-111">Son olarak, dizi öğelerinin türü sorguyu yürüten ifadede kullanılan döngü denetimi değişkeninin türüyle uyumlu olmalıdır `For Each` .</span><span class="sxs-lookup"><span data-stu-id="85a21-111">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="85a21-112">Bu güçlü yazma, derleme zamanında tür hatalarının tanımlanmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="85a21-112">This strong typing facilitates identification of type errors at compile time.</span></span>

<span data-ttu-id="85a21-113">Visual Basic, *örtülü yazma* olarak da bilinen yerel tür çıkarımı uygulayarak güçlü yazma kullanışlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="85a21-113">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="85a21-114">Bu özellik önceki örnekte kullanılır ve LINQ örnekleri ve belgelerinin tamamında kullanıldığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="85a21-114">That feature is used in the previous example, and you will see it used throughout the LINQ samples and documentation.</span></span> <span data-ttu-id="85a21-115">Visual Basic, yerel tür çıkarımı yalnızca `Dim` yan tümce olmadan bir deyimi kullanılarak gerçekleştirilir `As` .</span><span class="sxs-lookup"><span data-stu-id="85a21-115">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="85a21-116">Aşağıdaki örnekte, `city` kesin bir dize olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="85a21-116">In the following example, `city` is strongly typed as a string.</span></span>

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="85a21-117">Yerel tür çıkarımı yalnızca `Option Infer` olarak ayarlandığında kullanılabilir `On` .</span><span class="sxs-lookup"><span data-stu-id="85a21-117">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="85a21-118">Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="85a21-118">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>

<span data-ttu-id="85a21-119">Ancak, bir sorguda yerel tür çıkarımı kullanıyor olsanız bile, veri kaynağı, sorgu değişkeni ve sorgu yürütme döngüsünde değişkenler arasında aynı tür ilişkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="85a21-119">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="85a21-120">LINQ sorguları yazarken veya belgelerde örnek ve kod örnekleriyle çalışırken, bu tür ilişkilerden temel olarak anlaşılmak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="85a21-120">It is useful to have a basic understanding of these type relationships when you are writing LINQ queries, or working with the samples and code examples in the documentation.</span></span>

<span data-ttu-id="85a21-121">Veri kaynağından döndürülen türle eşleşmeyen bir Aralık değişkeni için açık bir tür belirtmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="85a21-121">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="85a21-122">Bir yan tümce kullanarak Aralık değişkeninin türünü belirtebilirsiniz `As` .</span><span class="sxs-lookup"><span data-stu-id="85a21-122">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="85a21-123">Ancak, dönüştürme bir [daraltma dönüştürmesi](../../language-features/data-types/widening-and-narrowing-conversions.md) ise ve olarak ayarlanmışsa bu hata oluşur `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="85a21-123">However, this results in an error if the conversion is a [narrowing conversion](../../language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="85a21-124">Bu nedenle, dönüştürmeyi veri kaynağından alınan değerlerle gerçekleştirmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="85a21-124">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="85a21-125">Yöntemini kullanarak veri kaynağındaki değerleri açık Aralık değişkeni türüne dönüştürebilirsiniz <xref:System.Linq.Enumerable.Cast%2A> .</span><span class="sxs-lookup"><span data-stu-id="85a21-125">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="85a21-126">Yan tümcesindeki seçili değerleri, `Select` Aralık değişkeninin türünden farklı bir açık türe de çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85a21-126">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="85a21-127">Bu noktaları aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="85a21-127">These points are illustrated in the following code.</span></span>

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="85a21-128">Kaynak verilerin tüm öğelerini döndüren sorgular</span><span class="sxs-lookup"><span data-stu-id="85a21-128">Queries That Return Entire Elements of the Source Data</span></span>

<span data-ttu-id="85a21-129">Aşağıdaki örnek, kaynak verilerden seçilen öğelerin dizisini döndüren bir LINQ sorgu işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="85a21-129">The following example shows a LINQ query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="85a21-130">Kaynak, `names` bir dize dizisi içerir ve sorgu çıktısı, ı harfiyle başlayan dizeleri içeren bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="85a21-130">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

<span data-ttu-id="85a21-131">Bu, aşağıdaki koda eşdeğerdir, ancak yazılması çok daha kısadır ve kolaydır.</span><span class="sxs-lookup"><span data-stu-id="85a21-131">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="85a21-132">Sorgularda yerel tür çıkarımı, Visual Basic içinde tercih edilen stildir.</span><span class="sxs-lookup"><span data-stu-id="85a21-132">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

<span data-ttu-id="85a21-133">Aşağıdaki ilişkiler, türlerin örtük olarak mı yoksa açık olarak mı belirlendiği, önceki kod örneklerinde her ikisinde de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="85a21-133">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>

1. <span data-ttu-id="85a21-134">Veri kaynağındaki öğelerin türü, sorgusunda,,,, `names` Aralık değişkeninin türüdür `name` .</span><span class="sxs-lookup"><span data-stu-id="85a21-134">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>

2. <span data-ttu-id="85a21-135">Seçilen nesnenin türü, `name` sorgu değişkeninin türünü belirler `mNames` .</span><span class="sxs-lookup"><span data-stu-id="85a21-135">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="85a21-136">Burada `name` bir dize olduğundan sorgu değişkeni Visual Basic IEnumerable (dize) olur.</span><span class="sxs-lookup"><span data-stu-id="85a21-136">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>

3. <span data-ttu-id="85a21-137">İçinde tanımlanan sorgu, `mNames` `For Each` döngüsünde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="85a21-137">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="85a21-138">Döngü, sorguyu yürütmenin sonucunu yineler.</span><span class="sxs-lookup"><span data-stu-id="85a21-138">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="85a21-139">`mNames`Yürütüldüğünde, bir dize dizisi döndürür, Loop yineleme değişkeni `nm` de bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="85a21-139">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>

## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="85a21-140">Seçili öğelerden bir alan döndüren sorgular</span><span class="sxs-lookup"><span data-stu-id="85a21-140">Queries That Return One Field from Selected Elements</span></span>

<span data-ttu-id="85a21-141">Aşağıdaki örnek, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] veri kaynağından seçilen her bir öğenin yalnızca bir kısmını içeren bir dizi döndüren bir sorgu işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="85a21-141">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="85a21-142">Sorgu, `Customer` veri kaynağı olarak nesneler koleksiyonunu ve yalnızca `Name` sonuç içindeki özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="85a21-142">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="85a21-143">Müşteri adı bir dize olduğundan, sorgu çıktı olarak bir dizi dize üretir.</span><span class="sxs-lookup"><span data-stu-id="85a21-143">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim custNames = From cust In customers
                Where cust.City = "London"
                Select cust.Name

For Each custName In custNames
    Console.WriteLine(custName)
Next
```

<span data-ttu-id="85a21-144">Değişkenler arasındaki ilişkiler, daha basit örnekteki gibi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="85a21-144">The relationships between variables are like those in the simpler example.</span></span>

1. <span data-ttu-id="85a21-145">Veri kaynağındaki öğelerin türü, sorgusunda,,,, `customers` Aralık değişkeninin türüdür `cust` .</span><span class="sxs-lookup"><span data-stu-id="85a21-145">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="85a21-146">Bu örnekte, bu tür olur `Customer` .</span><span class="sxs-lookup"><span data-stu-id="85a21-146">In this example, that type is `Customer`.</span></span>

2. <span data-ttu-id="85a21-147">`Select`İfade, `Name` `Customer` tüm nesne yerine her nesnenin özelliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="85a21-147">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="85a21-148">`Name`Bir dize olduğundan, sorgu değişkeni `custNames` yeniden IEnumerable (dize) olacaktır, değil `Customer` .</span><span class="sxs-lookup"><span data-stu-id="85a21-148">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>

3. <span data-ttu-id="85a21-149">, `custNames` Bir dizi dizeyi temsil ettiğinden, `For Each` döngünün yineleme değişkeni, `custName` bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85a21-149">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>

<span data-ttu-id="85a21-150">Yerel tür çıkarımı olmadan, aşağıdaki örnekte gösterildiği gibi önceki örnek yazmak ve anlamak için daha fazla kullanışsız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="85a21-150">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()
 Dim custNames As IEnumerable(Of String) =
     From cust As Customer In customers
     Where cust.City = "London"
     Select cust.Name

 For Each custName As String In custNames
     Console.WriteLine(custName)
 Next
```

## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="85a21-151">Anonim türler gerektiren sorgular</span><span class="sxs-lookup"><span data-stu-id="85a21-151">Queries That Require Anonymous Types</span></span>

<span data-ttu-id="85a21-152">Aşağıdaki örnekte daha karmaşık bir durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85a21-152">The following example shows a more complex situation.</span></span> <span data-ttu-id="85a21-153">Önceki örnekte, tüm değişkenler için türleri açıkça belirtmek uygun değildi.</span><span class="sxs-lookup"><span data-stu-id="85a21-153">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="85a21-154">Bu örnekte, olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="85a21-154">In this example, it is impossible.</span></span> <span data-ttu-id="85a21-155">Tüm `Customer` öğeleri veri kaynağından veya her öğeden tek bir alandan seçmek yerine, `Select` Bu sorgudaki yan tümce özgün nesnenin iki özelliğini döndürür `Customer` : `Name` ve `City` .</span><span class="sxs-lookup"><span data-stu-id="85a21-155">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="85a21-156">Yan tümcesine yanıt olarak `Select` , derleyici bu iki özelliği içeren anonim bir tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="85a21-156">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="85a21-157">Döngüde yürütmenin sonucu, `nameCityQuery` `For Each` yeni anonim türün örneklerinin bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="85a21-157">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="85a21-158">Anonim türün kullanılabilir bir adı olmadığından, türü `nameCityQuery` veya `custInfo` açıkça belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="85a21-158">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="85a21-159">Diğer bir deyişle, bir anonim tür ile, ' de ' ın yerine kullanılacak tür adı yoktur `String` `IEnumerable(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="85a21-159">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="85a21-160">Daha fazla bilgi için bkz. [anonim türler](../../language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="85a21-160">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim nameCityQuery = From cust In customers
                    Where cust.City = "London"
                    Select cust.Name, cust.City

For Each custInfo In nameCityQuery
    Console.WriteLine(custInfo.Name)
Next
```

<span data-ttu-id="85a21-161">Önceki örnekteki tüm değişkenlerin türlerini belirtmek mümkün olmasa da ilişkiler aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="85a21-161">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>

1. <span data-ttu-id="85a21-162">Veri kaynağındaki öğelerin türü, sorgudaki aralık değişkeninin türüdür.</span><span class="sxs-lookup"><span data-stu-id="85a21-162">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="85a21-163">Bu örnekte, `cust` bir örneğidir `Customer` .</span><span class="sxs-lookup"><span data-stu-id="85a21-163">In this example, `cust` is an instance of `Customer`.</span></span>

2. <span data-ttu-id="85a21-164">`Select`İfade anonim bir tür oluşturduğundan, sorgu değişkeni `nameCityQuery` örtülü olarak anonim bir tür olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85a21-164">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="85a21-165">Anonim bir türün kullanılabilir adı yok ve bu nedenle açıkça belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="85a21-165">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>

3. <span data-ttu-id="85a21-166">Döngüdeki yineleme değişkeninin türü `For Each` 2. adımda oluşturulan anonim türüdür.</span><span class="sxs-lookup"><span data-stu-id="85a21-166">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="85a21-167">Türün kullanılabilir bir adı olmadığından, döngü yineleme değişkeninin türü örtük olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="85a21-167">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>

## <a name="see-also"></a><span data-ttu-id="85a21-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85a21-168">See also</span></span>

- [<span data-ttu-id="85a21-169">Visual Basic'te LINQ'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="85a21-169">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="85a21-170">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="85a21-170">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="85a21-171">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85a21-171">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="85a21-172">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="85a21-172">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="85a21-173">LINQ</span><span class="sxs-lookup"><span data-stu-id="85a21-173">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="85a21-174">Sorgular</span><span class="sxs-lookup"><span data-stu-id="85a21-174">Queries</span></span>](../../../language-reference/queries/index.md)
