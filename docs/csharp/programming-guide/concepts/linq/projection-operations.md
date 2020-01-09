---
title: Projeksiyon Işlemleri (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: a2a2ae762d63d5ff26c7018caef1a83558042fb5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346519"
---
# <a name="projection-operations-c"></a><span data-ttu-id="b9be2-102">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b9be2-102">Projection Operations (C#)</span></span>
<span data-ttu-id="b9be2-103">Projeksiyon, bir nesneyi genellikle daha sonra kullanılacak olan özelliklerden oluşan yeni bir forma dönüştürme işlemine başvurur.</span><span class="sxs-lookup"><span data-stu-id="b9be2-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="b9be2-104">Projeksiyonu kullanarak her nesneden oluşturulan yeni bir tür oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9be2-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="b9be2-105">Bir özelliği proje üzerinde bir matematik işlevi de gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9be2-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="b9be2-106">Özgün nesneyi değiştirmeden de proje oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9be2-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="b9be2-107">Yansıtmayı gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b9be2-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9be2-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b9be2-108">Methods</span></span>  
  
|<span data-ttu-id="b9be2-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="b9be2-109">Method Name</span></span>|<span data-ttu-id="b9be2-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9be2-110">Description</span></span>|<span data-ttu-id="b9be2-111">C#Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b9be2-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="b9be2-112">Daha fazla bilgi</span><span class="sxs-lookup"><span data-stu-id="b9be2-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="b9be2-113">Seçim</span><span class="sxs-lookup"><span data-stu-id="b9be2-113">Select</span></span>|<span data-ttu-id="b9be2-114">Bir dönüşüm işlevine dayalı projeler değerleri.</span><span class="sxs-lookup"><span data-stu-id="b9be2-114">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b9be2-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="b9be2-115">SelectMany</span></span>|<span data-ttu-id="b9be2-116">Bir dönüşüm işlevine dayalı ve sonra bunları tek bir sırayla düzleştirir.</span><span class="sxs-lookup"><span data-stu-id="b9be2-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="b9be2-117">Çoklu `from` yan tümceleri kullanma</span><span class="sxs-lookup"><span data-stu-id="b9be2-117">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="b9be2-118">Sorgu Ifadesi söz dizimi örnekleri</span><span class="sxs-lookup"><span data-stu-id="b9be2-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="b9be2-119">Seçim</span><span class="sxs-lookup"><span data-stu-id="b9be2-119">Select</span></span>  
 <span data-ttu-id="b9be2-120">Aşağıdaki örnek, bir dize listesindeki her bir dizeden ilk harfi proje için `select` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9be2-120">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a><span data-ttu-id="b9be2-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="b9be2-121">SelectMany</span></span>  
 <span data-ttu-id="b9be2-122">Aşağıdaki örnek, dizeler listesindeki her bir dizeden her bir sözcüğü projeye eklemek için birden çok `from` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9be2-122">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="b9be2-123">Select SelectMany</span><span class="sxs-lookup"><span data-stu-id="b9be2-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="b9be2-124">`Select()` ve `SelectMany()` her ikisi de, kaynak değerlerinden bir sonuç değeri (veya değerler) üretmeniz.</span><span class="sxs-lookup"><span data-stu-id="b9be2-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="b9be2-125">`Select()` her kaynak değer için bir sonuç değeri üretir.</span><span class="sxs-lookup"><span data-stu-id="b9be2-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="b9be2-126">Bu nedenle, genel sonuç, kaynak koleksiyonuyla aynı sayıda öğeye sahip olan bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="b9be2-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="b9be2-127">Buna karşılık, `SelectMany()` her kaynak değerden birleştirilmiş alt koleksiyonlar içeren tek bir genel sonuç üretir.</span><span class="sxs-lookup"><span data-stu-id="b9be2-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="b9be2-128">`SelectMany()` bir bağımsız değişken olarak geçirilen dönüştürme işlevi, her kaynak değer için sıralanabilir bir değer dizisi döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="b9be2-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="b9be2-129">Bu sıralanabilir sıralar daha sonra `SelectMany()` bir büyük sıra oluşturmak için birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b9be2-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="b9be2-130">Aşağıdaki iki çizimde, bu iki yöntemin eylemleri arasındaki kavramsal fark gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b9be2-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="b9be2-131">Her durumda, seçici (dönüşüm) işlevinin her kaynak değerden çiçekler dizisini seçtiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="b9be2-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="b9be2-132">Bu çizimde `Select()`, kaynak koleksiyon ile aynı sayıda öğeye sahip bir koleksiyonun nasıl döndürdüğü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b9be2-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![Seçme eylemini gösteren grafik&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="b9be2-134">Bu çizimde, `SelectMany()` her bir ara dizideki her bir değeri içeren bir son sonuç değerindeki dizi ara diziyi nasıl birleştiren gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b9be2-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![SelectMany&#40;&#41;eylemini gösteren grafik.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="b9be2-136">Kod Örneği</span><span class="sxs-lookup"><span data-stu-id="b9be2-136">Code Example</span></span>  
 <span data-ttu-id="b9be2-137">Aşağıdaki örnek `Select()` ve `SelectMany()`davranışını karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="b9be2-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="b9be2-138">Kod, kaynak koleksiyondaki her bir çiçek adı listesinden ilk iki öğeyi alarak çiçekler ' ın bir "Buquet" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b9be2-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="b9be2-139">Bu örnekte, dönüşüm işlevinin <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> kullandığı "tek değer" bir değer koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="b9be2-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="b9be2-140">Bu, her bir alt dizideki her bir dizeyi numaralandırmak için ek `foreach` döngüsünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b9be2-140">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********              
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9be2-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9be2-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b9be2-142">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="b9be2-142">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="b9be2-143">select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="b9be2-143">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
- [<span data-ttu-id="b9be2-144">Birden çok kaynaktan nesne koleksiyonları doldurma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b9be2-144">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="b9be2-145">Grupları (LINQ) kullanarak bir dosyayı birden çok dosyaya bölme (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b9be2-145">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
