---
title: "C 'deki koleksiyonlar arasında yineleme #"
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: 15b77fd11c0ff606119425ec7aae8e7127315e82
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240700"
---
# <a name="iterators-c"></a><span data-ttu-id="4ca44-102">Yineleyiciler (C#)</span><span class="sxs-lookup"><span data-stu-id="4ca44-102">Iterators (C#)</span></span>

<span data-ttu-id="4ca44-103">Bir *Yineleyici* , listeler ve diziler gibi koleksiyonlardan dolaşmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca44-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="4ca44-104">Yineleyici yöntemi veya `get` erişimcisi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4ca44-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="4ca44-105">Yineleyici yöntemi, her öğeyi birer birer döndürmek için [yield return](../../language-reference/keywords/yield.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ca44-105">An iterator method uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="4ca44-106">Bir `yield return` ifadeye ulaşıldığında, koddaki geçerli konum hatırlanır.</span><span class="sxs-lookup"><span data-stu-id="4ca44-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="4ca44-107">Bu konumdan, Yineleyici işlevinin bir sonraki çağrılışında yürütme yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="4ca44-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="4ca44-108">Bir [foreach](../../language-reference/keywords/foreach-in.md) ifadesi veya bir LINQ sorgusu kullanarak istemci kodundan bir yineleyici tüketin.</span><span class="sxs-lookup"><span data-stu-id="4ca44-108">You consume an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>

<span data-ttu-id="4ca44-109">Aşağıdaki örnekte, döngünün ilk yinelemesi `foreach` yürütmenin `SomeNumbers` ilk ifadeye ulaşılana kadar yineleyici yönteminde devam etmesine neden olur `yield return` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="4ca44-110">Bu yineleme 3 değerini döndürür ve yineleyici yöntemindeki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="4ca44-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="4ca44-111">Döngünün bir sonraki yinelemesinde, yineleyici yönteminde yürütme kaldığınız yerden devam eder, bir ifadeye ulaştığında yeniden durdurulur `yield return` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="4ca44-112">Bu yineleme 5 değerini döndürür ve yineleyici yöntemindeki geçerli konum yeniden korunur.</span><span class="sxs-lookup"><span data-stu-id="4ca44-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="4ca44-113">Yineleyici yönteminin sonuna ulaşıldığında döngü tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="4ca44-113">The loop completes when the end of the iterator method is reached.</span></span>

```csharp
static void Main()
{
    foreach (int number in SomeNumbers())
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 3 5 8
    Console.ReadKey();
}

public static System.Collections.IEnumerable SomeNumbers()
{
    yield return 3;
    yield return 5;
    yield return 8;
}
```

<span data-ttu-id="4ca44-114">Bir yineleyici yönteminin veya erişimcisinin dönüş türü `get` <xref:System.Collections.IEnumerable> ,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> , veya olabilir <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="4ca44-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="4ca44-115">`yield break`Yinelemeyi sonlandırmak için bir ifade kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ca44-115">You can use a `yield break` statement to end the iteration.</span></span>

> [!NOTE]
> <span data-ttu-id="4ca44-116">Bu konudaki basit Yineleyici örneği hariç tüm örneklerde, [using](../../language-reference/keywords/using-directive.md) `System.Collections` ve ad alanları için using yönergelerini dahil edin `System.Collections.Generic` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-116">For all examples in this topic except the Simple Iterator example, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><span data-ttu-id="4ca44-117">Basit Yineleyici</span><span class="sxs-lookup"><span data-stu-id="4ca44-117">Simple Iterator</span></span>

<span data-ttu-id="4ca44-118">Aşağıdaki örnek, `yield return` [for](../../language-reference/keywords/for.md) döngüsü içindeki tek bir ifadeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4ca44-118">The following example has a single `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="4ca44-119">' De `Main` , `foreach` ifade gövdesinin her yinelemesi bir sonraki ifadeye devam eden Yineleyici işlevine bir çağrı oluşturur `yield return` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-119">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>

```csharp
static void Main()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    // Output: 6 8 10 12 14 16 18
    Console.ReadKey();
}

public static System.Collections.Generic.IEnumerable<int>
    EvenSequence(int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (int number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="creating-a-collection-class"></a><span data-ttu-id="4ca44-120">Koleksiyon sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ca44-120">Creating a Collection Class</span></span>

<span data-ttu-id="4ca44-121">Aşağıdaki örnekte, `DaysOfTheWeek` sınıfı <xref:System.Collections.IEnumerable> bir yöntemi gerektiren arabirimini uygular <xref:System.Collections.IEnumerable.GetEnumerator%2A> .</span><span class="sxs-lookup"><span data-stu-id="4ca44-121">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="4ca44-122">Derleyici, `GetEnumerator` bir döndüren yöntemini dolaylı olarak çağırır <xref:System.Collections.IEnumerator> .</span><span class="sxs-lookup"><span data-stu-id="4ca44-122">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="4ca44-123">`GetEnumerator`Yöntemi, yöntemini kullanarak her bir dizeyi bir kez döndürür `yield return` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-123">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>

```csharp
static void Main()
{
    DaysOfTheWeek days = new DaysOfTheWeek();

    foreach (string day in days)
    {
        Console.Write(day + " ");
    }
    // Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey();
}

public class DaysOfTheWeek : IEnumerable
{
    private string[] days = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };

    public IEnumerator GetEnumerator()
    {
        for (int index = 0; index < days.Length; index++)
        {
            // Yield each day of the week.
            yield return days[index];
        }
    }
}
```

<span data-ttu-id="4ca44-124">Aşağıdaki örnek, `Zoo` hayvanlar koleksiyonunu içeren bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4ca44-124">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="4ca44-125">`foreach`Sınıf örneğine () başvuran ifade, `theZoo` yöntemi örtük olarak çağırır `GetEnumerator` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-125">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="4ca44-126">`foreach` `Birds` Ve özelliklerine başvuran deyimler `Mammals` `AnimalsForType` adlandırılmış yineleyici yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ca44-126">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

```csharp
static void Main()
{
    Zoo theZoo = new Zoo();

    theZoo.AddMammal("Whale");
    theZoo.AddMammal("Rhinoceros");
    theZoo.AddBird("Penguin");
    theZoo.AddBird("Warbler");

    foreach (string name in theZoo)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros Penguin Warbler

    foreach (string name in theZoo.Birds)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Penguin Warbler

    foreach (string name in theZoo.Mammals)
    {
        Console.Write(name + " ");
    }
    Console.WriteLine();
    // Output: Whale Rhinoceros

    Console.ReadKey();
}

public class Zoo : IEnumerable
{
    // Private members.
    private List<Animal> animals = new List<Animal>();

    // Public methods.
    public void AddMammal(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Mammal });
    }

    public void AddBird(string name)
    {
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Bird });
    }

    public IEnumerator GetEnumerator()
    {
        foreach (Animal theAnimal in animals)
        {
            yield return theAnimal.Name;
        }
    }

    // Public members.
    public IEnumerable Mammals
    {
        get { return AnimalsForType(Animal.TypeEnum.Mammal); }
    }

    public IEnumerable Birds
    {
        get { return AnimalsForType(Animal.TypeEnum.Bird); }
    }

    // Private methods.
    private IEnumerable AnimalsForType(Animal.TypeEnum type)
    {
        foreach (Animal theAnimal in animals)
        {
            if (theAnimal.Type == type)
            {
                yield return theAnimal.Name;
            }
        }
    }

    // Private class.
    private class Animal
    {
        public enum TypeEnum { Bird, Mammal }

        public string Name { get; set; }
        public TypeEnum Type { get; set; }
    }
}
```

## <a name="using-iterators-with-a-generic-list"></a><span data-ttu-id="4ca44-127">Bir genel liste ile yineleyiciler kullanma</span><span class="sxs-lookup"><span data-stu-id="4ca44-127">Using Iterators with a Generic List</span></span>

<span data-ttu-id="4ca44-128">Aşağıdaki örnekte, <xref:System.Collections.Generic.Stack%601> Genel sınıf <xref:System.Collections.Generic.IEnumerable%601> genel arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="4ca44-128">In the following example, the <xref:System.Collections.Generic.Stack%601> generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="4ca44-129"><xref:System.Collections.Generic.Stack%601.Push%2A>Yöntemi, türü bir diziye değerler atar `T` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-129">The <xref:System.Collections.Generic.Stack%601.Push%2A> method assigns values to an array of type `T`.</span></span> <span data-ttu-id="4ca44-130"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>Yöntemi, ifadesini kullanarak dizi değerlerini döndürür `yield return` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-130">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>

<span data-ttu-id="4ca44-131">Genel yöntemin yanı sıra <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> genel olmayan <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemin de uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ca44-131">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="4ca44-132">Bunun nedeni, <xref:System.Collections.Generic.IEnumerable%601> öğesinden devralmasıdır <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="4ca44-132">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="4ca44-133">Genel olmayan uygulama genel uygulamaya erteler.</span><span class="sxs-lookup"><span data-stu-id="4ca44-133">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="4ca44-134">Örnek, aynı veri topluluğunda tekrarların çeşitli yollarını desteklemek için adlandırılmış yineleyiciler kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ca44-134">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="4ca44-135">Bu adlandırılmış yineleyiciler, `TopToBottom` ve `BottomToTop` özellikleridir ve `TopN` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="4ca44-135">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="4ca44-136">`BottomToTop`Özelliği, bir erişimcide yineleyici kullanır `get` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-136">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>

```csharp
static void Main()
{
    Stack<int> theStack = new Stack<int>();

    //  Add items to the stack.
    for (int number = 0; number <= 9; number++)
    {
        theStack.Push(number);
    }

    // Retrieve items from the stack.
    // foreach is allowed because theStack implements IEnumerable<int>.
    foreach (int number in theStack)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    // foreach is allowed, because theStack.TopToBottom returns IEnumerable(Of Integer).
    foreach (int number in theStack.TopToBottom)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    foreach (int number in theStack.BottomToTop)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 0 1 2 3 4 5 6 7 8 9

    foreach (int number in theStack.TopN(7))
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3

    Console.ReadKey();
}

public class Stack<T> : IEnumerable<T>
{
    private T[] values = new T[100];
    private int top = 0;

    public void Push(T t)
    {
        values[top] = t;
        top++;
    }
    public T Pop()
    {
        top--;
        return values[top];
    }

    // This method implements the GetEnumerator method. It allows
    // an instance of the class to be used in a foreach statement.
    public IEnumerator<T> GetEnumerator()
    {
        for (int index = top - 1; index >= 0; index--)
        {
            yield return values[index];
        }
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }

    public IEnumerable<T> TopToBottom
    {
        get { return this; }
    }

    public IEnumerable<T> BottomToTop
    {
        get
        {
            for (int index = 0; index <= top - 1; index++)
            {
                yield return values[index];
            }
        }
    }

    public IEnumerable<T> TopN(int itemsFromTop)
    {
        // Return less than itemsFromTop if necessary.
        int startIndex = itemsFromTop >= top ? 0 : top - itemsFromTop;

        for (int index = top - 1; index >= startIndex; index--)
        {
            yield return values[index];
        }
    }

}
```

## <a name="syntax-information"></a><span data-ttu-id="4ca44-137">Sözdizimi bilgileri</span><span class="sxs-lookup"><span data-stu-id="4ca44-137">Syntax Information</span></span>

<span data-ttu-id="4ca44-138">Yineleyici bir yöntem veya erişimci olarak gerçekleşebilir `get` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-138">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="4ca44-139">Bir olay, örnek Oluşturucu, statik oluşturucu veya statik sonlandırıcının içinde bir yineleyici gerçekleşemez.</span><span class="sxs-lookup"><span data-stu-id="4ca44-139">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>

<span data-ttu-id="4ca44-140">Deyimdeki ifade türünden, `yield return` Yineleyici tarafından döndürülen için tür bağımsız değişkenine örtük bir dönüştürme bulunmalıdır `IEnumerable<T>` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-140">An implicit conversion must exist from the expression type in the `yield return` statement to the type argument for the `IEnumerable<T>` returned by the iterator.</span></span>

<span data-ttu-id="4ca44-141">C# ' de, yineleyici yöntemi herhangi bir `in` , `ref` veya parametresine sahip olamaz `out` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-141">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>

<span data-ttu-id="4ca44-142">C# dilinde, `yield` ayrılmış bir sözcük değildir ve yalnızca bir `return` veya anahtar sözcüğünden önce kullanıldığında özel anlamı vardır `break` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-142">In C#, `yield` is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="4ca44-143">Teknik Uygulama</span><span class="sxs-lookup"><span data-stu-id="4ca44-143">Technical Implementation</span></span>

<span data-ttu-id="4ca44-144">Bir yineleyici Yöntem olarak yazdığınızda, derleyici onu bir durum makinesi olan bir iç içe geçmiş sınıfa çevirir.</span><span class="sxs-lookup"><span data-stu-id="4ca44-144">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="4ca44-145">Bu sınıf, `foreach` istemci kodundaki döngü devam ettiğinde yineleyicinin konumunu izler.</span><span class="sxs-lookup"><span data-stu-id="4ca44-145">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>

<span data-ttu-id="4ca44-146">Derleyicinin ne yaptığını görmek için, bir yineleyici yöntemi için oluşturulan Microsoft ara dil kodunu görüntülemek için ıldadsm. exe aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ca44-146">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that's generated for an iterator method.</span></span>

<span data-ttu-id="4ca44-147">Bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/builtin-types/struct.md)için Yineleyici oluşturduğunuzda, tüm arabirimini uygulamanız gerekmez <xref:System.Collections.IEnumerator> .</span><span class="sxs-lookup"><span data-stu-id="4ca44-147">When you create an iterator for a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="4ca44-148">Derleyici yineleyiciyi algıladığında, `Current` `MoveNext` veya arabiriminin,, ve yöntemlerini otomatik olarak oluşturur `Dispose` <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="4ca44-148">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="4ca44-149">Döngünün art arda her tekrarında `foreach` (veya doğrudan çağrısının `IEnumerator.MoveNext` ), sonraki Yineleyici kod gövdesi önceki deyimden sonra devam eder `yield return` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-149">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="4ca44-150">Daha sonra `yield return` Yineleyici gövdesinin sonuna ulaşılana kadar veya bir deyime ulaşılana kadar sonraki ifadeye devam eder `yield break` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-150">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>

<span data-ttu-id="4ca44-151">Yineleyiciler <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> yöntemi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="4ca44-151">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4ca44-152">Başlangıçtan itibaren yeniden yinelemek için yeni bir yineleyici edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ca44-152">To reiterate from the start, you must obtain a new iterator.</span></span> <span data-ttu-id="4ca44-153"><xref:System.Collections.IEnumerator.Reset%2A>Yineleyici yöntemi tarafından döndürülen yineleyicinin çağrılması bir oluşturur <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="4ca44-153">Calling <xref:System.Collections.IEnumerator.Reset%2A> on the iterator returned by an iterator method throws a <xref:System.NotSupportedException>.</span></span>

<span data-ttu-id="4ca44-154">Daha fazla bilgi için bkz. [C# dil belirtimi](~/_csharplang/spec/classes.md#iterators).</span><span class="sxs-lookup"><span data-stu-id="4ca44-154">For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).</span></span>

## <a name="use-of-iterators"></a><span data-ttu-id="4ca44-155">Yineleyicilerin kullanımı</span><span class="sxs-lookup"><span data-stu-id="4ca44-155">Use of Iterators</span></span>

<span data-ttu-id="4ca44-156">Yineleyiciler, `foreach` bir liste dizisini doldurmak için karmaşık kod kullanmanız gerektiğinde bir döngünün basitliğini korumanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ca44-156">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="4ca44-157">Bu, aşağıdakileri yapmak istediğinizde yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="4ca44-157">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="4ca44-158">İlk döngü yinelemeden sonra liste sırasını değiştirin `foreach` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-158">Modify the list sequence after the first `foreach` loop iteration.</span></span>

- <span data-ttu-id="4ca44-159">Bir döngünün ilk yinelemesinden önce büyük bir listenin tam olarak yüklenmesini önleyin `foreach` .</span><span class="sxs-lookup"><span data-stu-id="4ca44-159">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="4ca44-160">Tablo satırlarını toplu olarak yüklemek için disk belleğine alınmış bir getirme örneği.</span><span class="sxs-lookup"><span data-stu-id="4ca44-160">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="4ca44-161"><xref:System.IO.DirectoryInfo.EnumerateFiles%2A>.Net ' te yineleyiciler uygulayan yöntemi başka bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="4ca44-161">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators in .NET.</span></span>

- <span data-ttu-id="4ca44-162">Yineleyici içinde listenin oluşturulmasını yalıt.</span><span class="sxs-lookup"><span data-stu-id="4ca44-162">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="4ca44-163">Yineleyici yönteminde, listeyi derleyip her sonucu bir döngüde sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ca44-163">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ca44-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ca44-164">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="4ca44-165">foreach, in</span><span class="sxs-lookup"><span data-stu-id="4ca44-165">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="4ca44-166">yield</span><span class="sxs-lookup"><span data-stu-id="4ca44-166">yield</span></span>](../../language-reference/keywords/yield.md)
- [<span data-ttu-id="4ca44-167">Dizilerle foreach kullanma</span><span class="sxs-lookup"><span data-stu-id="4ca44-167">Using foreach with Arrays</span></span>](../arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="4ca44-168">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="4ca44-168">Generics</span></span>](../generics/index.md)
