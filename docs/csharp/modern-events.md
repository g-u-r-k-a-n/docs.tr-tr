---
title: Güncelleştirilmiş .NET Çekirdek Olay Deseni
description: .NET Core olay deseninin geriye dönük uyumlulukla esnekliği nasıl sağladığını ve async aboneleri ile güvenli olay işlemenin nasıl uygulanacağını öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: c8858158ede761db8a3002beb26e521880f77feb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170442"
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="11ae5-103">Güncelleştirilmiş .NET Çekirdek Olay Deseni</span><span class="sxs-lookup"><span data-stu-id="11ae5-103">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="11ae5-104">Önceki</span><span class="sxs-lookup"><span data-stu-id="11ae5-104">Previous</span></span>](event-pattern.md)

<span data-ttu-id="11ae5-105">Önceki makalede en yaygın olay desenleri tartışıldı.</span><span class="sxs-lookup"><span data-stu-id="11ae5-105">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="11ae5-106">.NET Core daha rahat bir desene sahiptir.</span><span class="sxs-lookup"><span data-stu-id="11ae5-106">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="11ae5-107">Bu sürümde, `EventHandler<TEventArgs>` tanım artık türetilmiş bir sınıf `TEventArgs` `System.EventArgs`olması gereken kısıtlamaya sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="11ae5-107">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="11ae5-108">Bu sizin için esnekliği artırır ve geriye dönük uyumludur.</span><span class="sxs-lookup"><span data-stu-id="11ae5-108">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="11ae5-109">Esneklikle başlayalım.</span><span class="sxs-lookup"><span data-stu-id="11ae5-109">Let's start with the flexibility.</span></span> <span data-ttu-id="11ae5-110">Class System.EventArgs bir yöntem `MemberwiseClone()`sunar: , nesnenin sığ bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="11ae5-110">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="11ae5-111">Bu yöntem, türetilen herhangi bir sınıf için `EventArgs`işlevselliğini uygulamak için yansıma kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="11ae5-111">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="11ae5-112">Bu işlevselliği belirli bir türemiş sınıfta oluşturmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="11ae5-112">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="11ae5-113">Bu, System.EventArgs'dan türeyen bir kısıtlamanın tasarımlarınızı sınırlayan, ancak ek bir fayda sağlamadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="11ae5-113">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="11ae5-114">Aslında, tanımlarını değiştirebilirsiniz `FileFoundArgs` ve `SearchDirectoryArgs` böylece onlar türetilmiştir `EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="11ae5-114">In fact, you can change the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="11ae5-115">Program tam olarak aynı çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="11ae5-115">The program will work exactly the same.</span></span>

<span data-ttu-id="11ae5-116">Bir değişiklik daha `SearchDirectoryArgs` yaparsanız, yapıyı da değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="11ae5-116">You could also change the `SearchDirectoryArgs` to a struct, if you make one more change:</span></span>

```csharp
internal struct SearchDirectoryArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs) : this()
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
```

<span data-ttu-id="11ae5-117">Ek değişiklik, tüm alanları başlarayan açime girmeden önce parametresiz oluşturucuyu çağırmaktır.</span><span class="sxs-lookup"><span data-stu-id="11ae5-117">The additional change is to call the parameterless constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="11ae5-118">Bu ek olmadan, C# kuralları, mülklere atanmadan önce erişildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="11ae5-118">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="11ae5-119">Bir `FileFoundArgs` sınıftan (başvuru türü) bir yapıya (değer türü) değiştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="11ae5-119">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="11ae5-120">Bunun nedeni, iptal etme protokolünün olay bağımsız değişkenlerinin başvuruyla geçirilmesini gerektirmesidir.</span><span class="sxs-lookup"><span data-stu-id="11ae5-120">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="11ae5-121">Aynı değişikliği yaptıysanız, dosya arama sınıfı hiçbir olay abonesi tarafından yapılan değişiklikleri gözlemleyemedi.</span><span class="sxs-lookup"><span data-stu-id="11ae5-121">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="11ae5-122">Yapının yeni bir kopyası her abone için kullanılır ve bu kopya dosya arama nesnesi tarafından görülenkopyadan farklı bir kopya olur.</span><span class="sxs-lookup"><span data-stu-id="11ae5-122">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="11ae5-123">Sonra, bu değişikliğin geriye doğru nasıl uyumlu olabileceğini düşünelim.</span><span class="sxs-lookup"><span data-stu-id="11ae5-123">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="11ae5-124">Kısıtlamanın kaldırılması varolan herhangi bir kodu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="11ae5-124">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="11ae5-125">Varolan tüm olay bağımsız değişken `System.EventArgs`türleri hala.</span><span class="sxs-lookup"><span data-stu-id="11ae5-125">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="11ae5-126">Geriye doğru uyumluluk, neden türetmeye devam `System.EventArgs`edecekleri önemli bir nedendir.</span><span class="sxs-lookup"><span data-stu-id="11ae5-126">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="11ae5-127">Varolan etkinlik aboneleri, klasik deseni izleyen bir etkinliğe abone olacaktır.</span><span class="sxs-lookup"><span data-stu-id="11ae5-127">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="11ae5-128">Benzer mantığı izleyerek, şimdi oluşturulan herhangi bir olay bağımsız değişken türü varolan codebases herhangi bir abone olmaz.</span><span class="sxs-lookup"><span data-stu-id="11ae5-128">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="11ae5-129">Türetilemeyen `System.EventArgs` yeni olay türleri bu kod tabanlarını bozmaz.</span><span class="sxs-lookup"><span data-stu-id="11ae5-129">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="11ae5-130">Async aboneleri ile etkinlikler</span><span class="sxs-lookup"><span data-stu-id="11ae5-130">Events with Async subscribers</span></span>

<span data-ttu-id="11ae5-131">Öğrenmeniz gereken son bir desen var: Async kodu arayan olay abonelerini nasıl doğru yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11ae5-131">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="11ae5-132">Meydan [async](async.md)üzerinde makalede açıklanan ve bekliyor .</span><span class="sxs-lookup"><span data-stu-id="11ae5-132">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="11ae5-133">Async yöntemleri bir boşluk dönüş türü olabilir, ancak bu şiddetle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="11ae5-133">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="11ae5-134">Olay abone kodunuz bir async yöntemi aradığında, bir `async void` yöntem oluşturmaktan başka seçeneğiniz yoktur.</span><span class="sxs-lookup"><span data-stu-id="11ae5-134">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="11ae5-135">Olay işleyiciimzası bunu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="11ae5-135">The event handler signature requires it.</span></span>

<span data-ttu-id="11ae5-136">Bu karşıt rehberliği uzlaştırmanız gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="11ae5-136">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="11ae5-137">Her nasılsa, `async void` güvenli bir yöntem oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="11ae5-137">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="11ae5-138">Uygulamanız gereken örüntünün temelleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="11ae5-138">The basics of the pattern you need to implement are below:</span></span>

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

<span data-ttu-id="11ae5-139">İlk olarak, işleyicinin bir async işleyicisi olarak işaretlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="11ae5-139">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="11ae5-140">Olay işleyicisi temsilci türüne atandığından, geçersiz bir dönüş türüne sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="11ae5-140">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="11ae5-141">Bu, işleyicide gösterilen deseni izlemeniz ve özel durumların async işleyicisinin bağlamından atılmasına izin vermemeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="11ae5-141">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="11ae5-142">Bir görevi döndürmediği için, hatalı durumu girerek hatayı bildirebilecek bir görev yoktur.</span><span class="sxs-lookup"><span data-stu-id="11ae5-142">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="11ae5-143">Yöntem async olduğundan, yöntem sadece özel durum atamaz.</span><span class="sxs-lookup"><span data-stu-id="11ae5-143">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="11ae5-144">(Arama yöntemi yürütmeye devam `async`etti çünkü öyle.) Gerçek çalışma zamanı davranışı farklı ortamlar için farklı tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="11ae5-144">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="11ae5-145">İş parçacığı veya iş parçacığı sahibi işlem sona erdirebilir veya belirsiz bir durumda işlem bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11ae5-145">It may terminate the thread or the process that owns the thread, or leave the process in an indeterminate state.</span></span> <span data-ttu-id="11ae5-146">Tüm bu potansiyel sonuçlar son derece istenmeyen vardır.</span><span class="sxs-lookup"><span data-stu-id="11ae5-146">All of these potential outcomes are highly undesirable.</span></span>

<span data-ttu-id="11ae5-147">Bu nedenle, async Task için bekleme deyimini kendi deneme bloğunuzda tamamlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="11ae5-147">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="11ae5-148">Hatalı bir göreve neden olursa, hatayı günlüğe kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11ae5-148">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="11ae5-149">Uygulamanızın kurtaramadığı bir hataysa, programdan hızlı ve zarif bir şekilde çıkabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="11ae5-149">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="11ae5-150">Bunlar .NET olay deseninin ana güncelleştirmeleridir.</span><span class="sxs-lookup"><span data-stu-id="11ae5-150">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="11ae5-151">Birlikte çalıştığınız kitaplıklarda önceki sürümlerden birçok örnek görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="11ae5-151">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="11ae5-152">Ancak, en son desenlerde ne olduğunu da anlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="11ae5-152">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="11ae5-153">Bu serinin bir sonraki makalesi, `delegates` `events` tasarımlarınızı kullanmak la ayırt etmek arasında ayrım yaptığınızda yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="11ae5-153">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="11ae5-154">Bunlar benzer kavramlardır ve bu makale, programlarınız için en iyi kararı vermenize yardımcı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="11ae5-154">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="11ae5-155">Sonraki</span><span class="sxs-lookup"><span data-stu-id="11ae5-155">Next</span></span>](distinguish-delegates-events.md)
