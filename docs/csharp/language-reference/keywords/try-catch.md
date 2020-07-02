---
title: try-catch-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
ms.openlocfilehash: 4715a27a94ac86c5e4955c0e8be95c6ee4a28507
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619708"
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="ce77c-102">try-catch (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ce77c-102">try-catch (C# Reference)</span></span>

<span data-ttu-id="ce77c-103">Try-catch deyimleri `try` `catch` , farklı özel durumlar için işleyiciler belirten bir veya daha fazla yan tümce tarafından izlenen bir bloğundan oluşur.</span><span class="sxs-lookup"><span data-stu-id="ce77c-103">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>

<span data-ttu-id="ce77c-104">Bir özel durum oluştuğunda, ortak dil çalışma zamanı (CLR) `catch` Bu özel durumu işleyen ifadeye bakar.</span><span class="sxs-lookup"><span data-stu-id="ce77c-104">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="ce77c-105">Şu anda yürütülmekte olan yöntem böyle bir `catch` blok içermiyorsa, clr geçerli yöntemi çağıran yönteme bakar ve bu şekilde çağrı yığınını alır.</span><span class="sxs-lookup"><span data-stu-id="ce77c-105">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="ce77c-106">Hiçbir `catch` blok bulunamazsa, clr kullanıcıya işlenmeyen bir özel durum iletisi görüntüler ve programın yürütülmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="ce77c-106">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>

<span data-ttu-id="ce77c-107">`try`Blok, özel duruma neden olabilecek korunan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="ce77c-107">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="ce77c-108">Bir özel durum oluşturuluncaya veya başarıyla tamamlanana kadar blok yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ce77c-108">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="ce77c-109">Örneğin, bir nesneyi atama girişimi şu `null` <xref:System.NullReferenceException> özel durumu oluşturur:</span><span class="sxs-lookup"><span data-stu-id="ce77c-109">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

<span data-ttu-id="ce77c-110">`catch`Yan tümcesi herhangi bir tür özel durum yakalamak için bağımsız değişken olmadan kullanılabilmesine rağmen, bu kullanım önerilmez.</span><span class="sxs-lookup"><span data-stu-id="ce77c-110">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="ce77c-111">Genel olarak, yalnızca kurtarmayı bildiğiniz özel durumları yakamalısınız.</span><span class="sxs-lookup"><span data-stu-id="ce77c-111">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="ce77c-112">Bu nedenle, her zaman ' dan türetilmiş bir nesne bağımsız değişkeni belirtmeniz gerekir <xref:System.Exception?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="ce77c-112">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>

```csharp
catch (InvalidCastException e)
{
}
```

<span data-ttu-id="ce77c-113">`catch`Aynı try-catch deyimi içinde birden çok özel yan tümce kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ce77c-113">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="ce77c-114">Bu durumda, yan tümceler sırasıyla `catch` incelenmediği için yan tümcelerinin sırası önemlidir `catch` .</span><span class="sxs-lookup"><span data-stu-id="ce77c-114">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="ce77c-115">Daha az özel durumları daha az spesifik olanlardan önce yakalayın.</span><span class="sxs-lookup"><span data-stu-id="ce77c-115">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="ce77c-116">Daha sonraki bir bloba ulaşılmaması için catch bloklarını sıralarsanız derleyici bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce77c-116">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>

<span data-ttu-id="ce77c-117">`catch`Bağımsız değişkenlerin kullanılması, işlemek istediğiniz özel durumları filtrelemek için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="ce77c-117">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="ce77c-118">Ayrıca, işleme karar vermek için özel durumu daha ayrıntılı bir şekilde inceleyen bir özel durum filtresi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce77c-118">You can also use an exception filter that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="ce77c-119">Özel durum filtresi false döndürürse, işleyici araması devam eder.</span><span class="sxs-lookup"><span data-stu-id="ce77c-119">If the exception filter returns false, then the search for a handler continues.</span></span>

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

<span data-ttu-id="ce77c-120">Özel durum filtreleri yakalamak ve yeniden oluşturmak tercih edilir (aşağıda açıklanmıştır) çünkü filtreler yığından ayrılmaz.</span><span class="sxs-lookup"><span data-stu-id="ce77c-120">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="ce77c-121">Daha sonraki bir işleyici yığının dökümünü alıyorsa, özel durumun ilk olarak oluşturulduğu son yerde değil, ilk olarak nereden geldiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce77c-121">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="ce77c-122">Özel durum filtre ifadelerinin yaygın kullanımı günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ce77c-122">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="ce77c-123">Her zaman bir günlüğe çıkış yapan yanlış değeri döndüren bir filtre oluşturabilirsiniz, bunları işlemek ve yeniden oluşturmak zorunda kalmadan, özel durumları bu şekilde günlüğe kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce77c-123">You can create a filter that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>

<span data-ttu-id="ce77c-124">[Throw](throw.md) deyimleri `catch` , ifadesiyle yakalanan özel durumu yeniden oluşturmak için bir blokta kullanılabilir `catch` .</span><span class="sxs-lookup"><span data-stu-id="ce77c-124">A [throw](throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="ce77c-125">Aşağıdaki örnek, bir özel durumdan kaynak bilgilerini ayıklar <xref:System.IO.IOException> ve ardından ana yöntemin özel durumunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce77c-125">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>

```csharp
catch (FileNotFoundException e)
{
    // FileNotFoundExceptions are handled here.
}
catch (IOException e)
{
    // Extract some information from this exception, and then
    // throw it to the parent method.
    if (e.Source != null)
        Console.WriteLine("IOException source: {0}", e.Source);
    throw;
}
```

<span data-ttu-id="ce77c-126">Bir özel durumu yakalayabilir ve farklı bir özel durum oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce77c-126">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="ce77c-127">Bunu yaptığınızda, aşağıdaki örnekte gösterildiği gibi, iç özel durum olarak yakalandığı özel durumu belirtin.</span><span class="sxs-lookup"><span data-stu-id="ce77c-127">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

<span data-ttu-id="ce77c-128">Ayrıca, aşağıdaki örnekte gösterildiği gibi, belirli bir koşul true olduğunda bir özel durumu yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce77c-128">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    if (e.Data == null)
    {
        throw;
    }
    else
    {
        // Take some action.
    }
}
```

> [!NOTE]
> <span data-ttu-id="ce77c-129">Benzer bir sonucu genellikle temizleyici bir şekilde (Bu belgede daha önce açıklandığı gibi, yığın değiştirilmeyen) almak için bir özel durum filtresi kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ce77c-129">It is also possible to use an exception filter to get a similar result in an often cleaner fashion (as well as not modifying the stack, as explained earlier in this document).</span></span> <span data-ttu-id="ce77c-130">Aşağıdaki örnekte, bir önceki örnek olarak çağıranlar için benzer bir davranış vardır.</span><span class="sxs-lookup"><span data-stu-id="ce77c-130">The following example has a similar behavior for callers as the previous example.</span></span> <span data-ttu-id="ce77c-131">İşlevi, `InvalidCastException` olduğunda çağırana geri dönerek atar `e.Data` `null` .</span><span class="sxs-lookup"><span data-stu-id="ce77c-131">The function throws the `InvalidCastException` back to the caller when `e.Data` is `null`.</span></span>
>
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)
> {
>     // Take some action.
> }
> ```

<span data-ttu-id="ce77c-132">Bir bloğun içinden `try` yalnızca içinde belirtilen değişkenleri başlatın.</span><span class="sxs-lookup"><span data-stu-id="ce77c-132">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="ce77c-133">Aksi takdirde, bloğun yürütülmesi tamamlanmadan önce bir özel durum ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="ce77c-133">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="ce77c-134">Örneğin, aşağıdaki kod örneğinde değişken `n` blok içinde başlatılır `try` .</span><span class="sxs-lookup"><span data-stu-id="ce77c-134">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="ce77c-135">Bu değişkeni ifadesinde bloğunun dışında kullanma girişimi `try` `Write(n)` bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce77c-135">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>

```csharp
static void Main()
{
    int n;
    try
    {
        // Do not initialize this variable here.
        n = 123;
    }
    catch
    {
    }
    // Error: Use of unassigned local variable 'n'.
    Console.Write(n);
}
```

<span data-ttu-id="ce77c-136">Catch hakkında daha fazla bilgi için bkz. [try-catch-finally](try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="ce77c-136">For more information about catch, see [try-catch-finally](try-catch-finally.md).</span></span>

## <a name="exceptions-in-async-methods"></a><span data-ttu-id="ce77c-137">Zaman uyumsuz yöntemlerde özel durumlar</span><span class="sxs-lookup"><span data-stu-id="ce77c-137">Exceptions in async methods</span></span>

<span data-ttu-id="ce77c-138">Zaman uyumsuz bir yöntem, [zaman uyumsuz](async.md) bir değiştirici tarafından işaretlenir ve genellikle bir veya daha fazla await ifadesi ya da deyimi içerir.</span><span class="sxs-lookup"><span data-stu-id="ce77c-138">An async method is marked  by an  [async](async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="ce77c-139">Await ifadesi bir veya ' a [await](../operators/await.md) işlecini uygular <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="ce77c-139">An await expression applies the [await](../operators/await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="ce77c-140">Denetim `await` zaman uyumsuz yöntemde bir ulaştığında, beklenen görev tamamlanana kadar yöntemindeki ilerleme askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="ce77c-140">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="ce77c-141">Görev tamamlandığında, yürütme yöntemi içinde çalışmaya çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="ce77c-141">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="ce77c-142">Daha fazla bilgi için bkz. Async [ve await ile](../../programming-guide/concepts/async/index.md) zaman uyumsuz programlama ve [zaman uyumsuz programlarda denetim akışı](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="ce77c-142">For more information, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md) and [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>

<span data-ttu-id="ce77c-143">Uygulanan tamamlanan görev, `await` görevi döndüren yöntemdeki işlenmeyen bir özel durum nedeniyle hatalı bir durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="ce77c-143">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="ce77c-144">Görevin bekleniyor bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce77c-144">Awaiting the task throws an exception.</span></span> <span data-ttu-id="ce77c-145">Aynı zamanda, döndüren zaman uyumsuz işlem iptal edilirse, bir görev iptal edilmiş durumda da bitebilirler.</span><span class="sxs-lookup"><span data-stu-id="ce77c-145">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="ce77c-146">İptal edilen bir görevin bekleniyor bir oluşturur `OperationCanceledException` .</span><span class="sxs-lookup"><span data-stu-id="ce77c-146">Awaiting a canceled task throws  an `OperationCanceledException`.</span></span> <span data-ttu-id="ce77c-147">Zaman uyumsuz bir işlemi iptal etme hakkında daha fazla bilgi için bkz. [zaman uyumsuz uygulamanızda Ince ayar yapma](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="ce77c-147">For more information about how to cancel an asynchronous process, see [Fine-Tuning Your Async Application](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="ce77c-148">Özel durumu yakalamak için, görevi bir `try` blokta bekleve özel durumu ilişkili blokta yakalayacak `catch` .</span><span class="sxs-lookup"><span data-stu-id="ce77c-148">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="ce77c-149">Örneğin, [zaman uyumsuz yöntem örneği](#async-method-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ce77c-149">For an example, see the [Async method example](#async-method-example) section.</span></span>

<span data-ttu-id="ce77c-150">Beklenen zaman uyumsuz yöntemde birden çok özel durum oluştuğundan, görev hatalı durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="ce77c-150">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="ce77c-151">Örneğin, görev bir çağrısının sonucu olabilir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ce77c-151">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ce77c-152">Böyle bir görevi bekleyettiğinizde, özel durumların yalnızca biri yakalanacaktır ve hangi özel durumun yakalanıp yakalanmayacak olduğunu tahmin edemeyecektir.</span><span class="sxs-lookup"><span data-stu-id="ce77c-152">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="ce77c-153">Bir örnek için, [Task. WhenAll örnek](#taskwhenall-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ce77c-153">For an example, see the [Task.WhenAll example](#taskwhenall-example) section.</span></span>

## <a name="example"></a><span data-ttu-id="ce77c-154">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce77c-154">Example</span></span>

<span data-ttu-id="ce77c-155">Aşağıdaki örnekte, `try` blok bir `ProcessString` özel duruma neden olabilecek metoda bir çağrı içerir.</span><span class="sxs-lookup"><span data-stu-id="ce77c-155">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="ce77c-156">`catch`Yan tümcesi yalnızca ekranda bir ileti görüntüleyen özel durum işleyicisini içerir.</span><span class="sxs-lookup"><span data-stu-id="ce77c-156">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="ce77c-157">`throw`İfade içinden çağrıldığında `ProcessString` , sistem, `catch` ifadeyi arar ve iletiyi görüntüler `Exception caught` .</span><span class="sxs-lookup"><span data-stu-id="ce77c-157">When the `throw` statement is called from inside `ProcessString`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a><span data-ttu-id="ce77c-158">İki catch bloğu örneği</span><span class="sxs-lookup"><span data-stu-id="ce77c-158">Two catch blocks example</span></span>

<span data-ttu-id="ce77c-159">Aşağıdaki örnekte, iki catch bloğu kullanılır ve ilk olarak gelen en özel durum yakalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce77c-159">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>

<span data-ttu-id="ce77c-160">En az özel durumu yakalamak için, içindeki throw ifadesini `ProcessString` aşağıdaki deyimle değiştirebilirsiniz: `throw new Exception()` .</span><span class="sxs-lookup"><span data-stu-id="ce77c-160">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>

<span data-ttu-id="ce77c-161">Örneğe en az özel catch bloğunu yerleştirirseniz, aşağıdaki hata iletisi görüntülenir: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')` .</span><span class="sxs-lookup"><span data-stu-id="ce77c-161">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a><span data-ttu-id="ce77c-162">Async yöntemi örneği</span><span class="sxs-lookup"><span data-stu-id="ce77c-162">Async method example</span></span>

<span data-ttu-id="ce77c-163">Aşağıdaki örnek, zaman uyumsuz metotlar için özel durum işlemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce77c-163">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="ce77c-164">Zaman uyumsuz bir görevin aldığı bir özel durumu yakalamak için, `await` ifadeyi bir blok içine yerleştirin `try` ve özel durumu bir `catch` blokta yakalayın.</span><span class="sxs-lookup"><span data-stu-id="ce77c-164">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>

<span data-ttu-id="ce77c-165">`throw new Exception`Özel durum işlemeyi göstermek için örnekteki satırın açıklamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ce77c-165">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="ce77c-166">Görevin `IsFaulted` özelliği olarak ayarlanır `True` , görevin `Exception.InnerException` özelliği özel duruma ayarlanır ve özel durum `catch` bloğunda yakalanır.</span><span class="sxs-lookup"><span data-stu-id="ce77c-166">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>

<span data-ttu-id="ce77c-167">`throw new OperationCanceledException`Zaman uyumsuz bir işlemi iptal ettiğinizde ne olacağını göstermek için çizginin açıklamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ce77c-167">Uncomment the `throw new OperationCanceledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="ce77c-168">Görevin `IsCanceled` özelliği olarak ayarlanır `true` ve özel durum `catch` bloğunda yakalanır.</span><span class="sxs-lookup"><span data-stu-id="ce77c-168">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="ce77c-169">Bu örnek için geçerli olmayan bazı koşullar altında, görevin `IsFaulted` özelliği olarak ayarlanır `true` ve `IsCanceled` olarak ayarlanır `false` .</span><span class="sxs-lookup"><span data-stu-id="ce77c-169">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a><span data-ttu-id="ce77c-170">Task. WhenAll örneği</span><span class="sxs-lookup"><span data-stu-id="ce77c-170">Task.WhenAll example</span></span>

<span data-ttu-id="ce77c-171">Aşağıdaki örnekte, birden çok görevin birden çok özel durum ile sonuçlanbildiği özel durum işleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ce77c-171">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="ce77c-172">`try`Blok, çağrısı tarafından döndürülen görevi bekler <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ce77c-172">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ce77c-173">Bu görev, WhenAll 'un uygulandığı üç görev tamamlandığında tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ce77c-173">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>

<span data-ttu-id="ce77c-174">Üç görevin her biri özel duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="ce77c-174">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="ce77c-175">`catch`Blok, `Exception.InnerExceptions` tarafından döndürülen görevin özelliğinde bulunan özel durumlar boyunca yinelenir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ce77c-175">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="ce77c-176">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ce77c-176">C# language specification</span></span>

<span data-ttu-id="ce77c-177">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [TRY deyimin](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ce77c-177">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ce77c-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce77c-178">See also</span></span>

- [<span data-ttu-id="ce77c-179">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ce77c-179">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ce77c-180">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ce77c-180">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ce77c-181">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ce77c-181">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ce77c-182">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="ce77c-182">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="ce77c-183">throw</span><span class="sxs-lookup"><span data-stu-id="ce77c-183">throw</span></span>](throw.md)
- [<span data-ttu-id="ce77c-184">try-finally</span><span class="sxs-lookup"><span data-stu-id="ce77c-184">try-finally</span></span>](try-finally.md)
- [<span data-ttu-id="ce77c-185">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ce77c-185">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
