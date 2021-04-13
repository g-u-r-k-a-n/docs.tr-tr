---
title: 'Öğretici: desenler eşleştirme ile derleme algoritmaları'
description: Bu gelişmiş öğreticide, ayrı olarak oluşturulan verileri ve algoritmaları kullanarak işlevsellik oluşturmak için model eşleştirme tekniklerini nasıl kullanabileceğiniz gösterilmektedir.
ms.date: 10/06/2020
ms.technology: csharp-whats-new
ms.custom: contperf-fy21q1
ms.openlocfilehash: 5d132784f591405b906068e2ed0e04347faa5e2c
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255473"
---
# <a name="tutorial-use-pattern-matching-to-build-type-driven-and-data-driven-algorithms"></a><span data-ttu-id="c71a3-103">Öğretici: tür odaklı ve veri odaklı algoritmalar oluşturmak için model eşleştirmeyi kullanın</span><span class="sxs-lookup"><span data-stu-id="c71a3-103">Tutorial: Use pattern matching to build type-driven and data-driven algorithms</span></span>

<span data-ttu-id="c71a3-104">C# 7 temel desenler ile eşleşen özellikleri sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="c71a3-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="c71a3-105">Bu özellikler, C# 8 ve C# 9 ' da yeni ifadelerle ve desenlerle genişletilir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-105">Those features are extended in C# 8 and C# 9 with new expressions and patterns.</span></span> <span data-ttu-id="c71a3-106">Başka kitaplıklarda olabilecek türleri genişletmekle birlikte davranan işlevselliği yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="c71a3-107">Desenler için başka bir kullanım, uygulamanızın genişletilmekte olan türün temel bir özelliği olmayan bir işlev oluşturmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="c71a3-108">Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="c71a3-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="c71a3-109">Model eşleştirmesinin kullanılması gereken durumları tanıyın.</span><span class="sxs-lookup"><span data-stu-id="c71a3-109">Recognize situations where pattern matching should be used.</span></span>
> - <span data-ttu-id="c71a3-110">Türleri ve özellik değerlerini temel alan davranışı uygulamak için kalıp eşleştirme ifadelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c71a3-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> - <span data-ttu-id="c71a3-111">Tüm algoritmalar oluşturmak için model eşleştirmeyi diğer tekniklerle birleştirin.</span><span class="sxs-lookup"><span data-stu-id="c71a3-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c71a3-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c71a3-112">Prerequisites</span></span>

<span data-ttu-id="c71a3-113">Makinenizde C# 9 derleyicisini içeren .NET 5 ' i çalıştıracak şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-113">You'll need to set up your machine to run .NET 5, which includes the C# 9 compiler.</span></span> <span data-ttu-id="c71a3-114">C# 9 derleyicisi, [Visual Studio 2019 sürüm 16,9 Preview 1](https://visualstudio.microsoft.com/vs/preview/) veya [.NET 5,0 SDK](https://dot.net/get-dotnet5)ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-114">The C# 9 compiler is available starting with [Visual Studio 2019 version 16.9 preview 1](https://visualstudio.microsoft.com/vs/preview/) or [.NET 5.0 SDK](https://dot.net/get-dotnet5).</span></span>

<span data-ttu-id="c71a3-115">Bu öğreticide, Visual Studio veya .NET Core CLI dahil olmak üzere C# ve .NET hakkında bilgi sahibi olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="c71a3-116">Model eşleştirme senaryoları</span><span class="sxs-lookup"><span data-stu-id="c71a3-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="c71a3-117">Modern geliştirme genellikle birden çok kaynaktaki verilerin tümleştirilmesine ve bu verilerden tek bir ortak uygulamada bilgi ve Öngörüler sunmaya dahildir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="c71a3-118">Siz ve takımınız gelen verileri temsil eden tüm türler için denetime veya erişime sahip olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="c71a3-119">Klasik nesne odaklı tasarım, uygulamanızda, bu birden çok veri kaynağından her bir veri türünü temsil eden türler oluşturmak için çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="c71a3-120">Daha sonra uygulamanız bu yeni türlerle çalışarak devralma hiyerarşileri oluşturun, sanal yöntemler oluşturur ve soyutlamalar uygular.</span><span class="sxs-lookup"><span data-stu-id="c71a3-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="c71a3-121">Bu teknikler çalışır ve bazen en iyi araçlardır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="c71a3-122">Diğer zamanlarda da daha az kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-122">Other times you can write less code.</span></span> <span data-ttu-id="c71a3-123">Verileri işleyen işlemlerden verileri ayıran teknikleri kullanarak daha fazla şifresiz kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="c71a3-124">Bu öğreticide, tek bir senaryo için çeşitli dış kaynaklardan gelen verileri alan bir uygulama oluşturacaksınız ve keşfedeceğiz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="c71a3-125">**Düzenin** , bu verileri özgün sistemin parçası olmayan yollarla tüketmek ve işlemek için etkili bir yol sağladığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="c71a3-126">Trafiği yönetmek için Tolls ve yoğun zaman fiyatlandırması kullanan bir ana metropol alanı düşünün.</span><span class="sxs-lookup"><span data-stu-id="c71a3-126">Consider a major metropolitan area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="c71a3-127">Türüne göre bir araç için Tolls 'yi hesaplayan bir uygulama yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="c71a3-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="c71a3-128">Daha sonraki geliştirmeler, araç çubuğundaki alan sayısına göre fiyatlandırmaya dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="c71a3-129">Daha fazla geliştirmeler, haftanın saatine ve gününe göre fiyatlandırma ekler.</span><span class="sxs-lookup"><span data-stu-id="c71a3-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="c71a3-130">Bu kısa açıklamadan, bu sistemi modellemek için bir nesne hiyerarşisinde hızlıca taslak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="c71a3-131">Ancak, verileriniz diğer araç kayıt yönetimi sistemleri gibi birden çok kaynaktan geliyor.</span><span class="sxs-lookup"><span data-stu-id="c71a3-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="c71a3-132">Bu sistemler, verileri modellemek için farklı sınıflar sağlar ve kullanabileceğiniz tek bir nesne modeli yoktur.</span><span class="sxs-lookup"><span data-stu-id="c71a3-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="c71a3-133">Bu öğreticide, aşağıdaki kodda gösterildiği gibi bu dış sistemlerden araç verilerini modellemek için bu Basitleştirilmiş sınıfları kullanacaksınız:</span><span class="sxs-lookup"><span data-stu-id="c71a3-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="c71a3-134">Başlangıç kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/main/csharp/tutorials/patterns/start) GitHub deposundan indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/main/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="c71a3-135">Araç sınıflarının farklı sistemlerden olduğunu ve farklı ad alanlarında olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="c71a3-136">Ortak bir temel sınıf yoktur, diğeri `System.Object` yararlanılabilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="c71a3-137">Desen eşleştirme tasarımları</span><span class="sxs-lookup"><span data-stu-id="c71a3-137">Pattern matching designs</span></span>

<span data-ttu-id="c71a3-138">Bu öğreticide kullanılan senaryo, düzenin eşleşmesi için uygun olan sorun türlerini vurgular:</span><span class="sxs-lookup"><span data-stu-id="c71a3-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well suited to solve:</span></span>

- <span data-ttu-id="c71a3-139">Çalışmanız gereken nesneler, hedeflerinizle eşleşen bir nesne hiyerarşisinde değildir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="c71a3-140">İlişkisiz sistemlerin parçası olan sınıflarla çalışıyor olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="c71a3-141">Eklemekte olduğunuz işlevsellik, bu sınıfların temel soyutlama kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="c71a3-142">Bir araç tarafından ücretli bir araç, farklı araç türlerine göre *değişir* ancak ücretli bir temel işlev değildir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="c71a3-143">Verilerin *şekli* ve bu verilerdeki *işlemler* birlikte Açıklanmadığında, C# ' deki model eşleştirme özellikleri ile çalışmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="c71a3-144">Temel ücretli hesaplamaları uygulayın</span><span class="sxs-lookup"><span data-stu-id="c71a3-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="c71a3-145">En temel ücretli hesaplama yalnızca araç türüne bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="c71a3-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="c71a3-146">A `Car` $2,00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="c71a3-147">A `Taxi` $3,50 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="c71a3-148">A `Bus` $5,00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="c71a3-149">A `DeliveryTruck` $10,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="c71a3-150">`TollCalculator`Ücretli miktarı almak için yeni bir sınıf oluşturun ve araç türünde kalıp eşleştirmeyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c71a3-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="c71a3-151">Aşağıdaki kod, öğesinin ilk uygulamasını gösterir `TollCalculator` .</span><span class="sxs-lookup"><span data-stu-id="c71a3-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    public class TollCalculator
    {
        public decimal CalculateToll(object vehicle) =>
            vehicle switch
        {
            Car c           => 2.00m,
            Taxi t          => 3.50m,
            Bus b           => 5.00m,
            DeliveryTruck t => 10.00m,
            { }             => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
            null            => throw new ArgumentNullException(nameof(vehicle))
        };
    }
}
```

<span data-ttu-id="c71a3-152">Önceki kod, [ `switch` ](../language-reference/operators/switch-expression.md) [`switch`](../language-reference/keywords/switch.md) [bildirim modelini](../language-reference/operators/patterns.md#declaration-and-type-patterns)test eden bir ifade (deyimiyle aynı değil) kullanır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-152">The preceding code uses a [`switch` expression](../language-reference/operators/switch-expression.md) (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the [declaration pattern](../language-reference/operators/patterns.md#declaration-and-type-patterns).</span></span> <span data-ttu-id="c71a3-153">Bir **switch ifadesi** , `vehicle` Önceki kodda, sonra anahtar sözcüğü gelen değişkenle başlar `switch` .</span><span class="sxs-lookup"><span data-stu-id="c71a3-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="c71a3-154">Ardından, küme ayraçları içindeki tüm **anahtar kolları** gelir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="c71a3-155">`switch`İfade, diğer işlevselliklerindeki deyimini çevreleyen söz dizimini yapar `switch` .</span><span class="sxs-lookup"><span data-stu-id="c71a3-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="c71a3-156">`case`Anahtar sözcüğü atlanır ve her bir ARM 'nin sonucu bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="c71a3-157">Son iki kolonun yeni bir dil özelliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="c71a3-158">`{ }`Durum, önceki bir ARM ile eşleşmeyen null olmayan herhangi bir nesneyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="c71a3-159">Bu ARM, bu yönteme geçirilen hatalı türleri yakalar.</span><span class="sxs-lookup"><span data-stu-id="c71a3-159">This arm catches any incorrect types passed to this method.</span></span> <span data-ttu-id="c71a3-160">`{ }`Durum, her bir araç türü için durumları izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="c71a3-161">Sıra tersine çevrilirse, `{ }` büyük/küçük harf durumuna geçer.</span><span class="sxs-lookup"><span data-stu-id="c71a3-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="c71a3-162">Son olarak, `null` [sabit model](../language-reference/operators/patterns.md#constant-pattern) `null` Bu yönteme ne zaman geçtiğini algılar.</span><span class="sxs-lookup"><span data-stu-id="c71a3-162">Finally, the `null` [constant pattern](../language-reference/operators/patterns.md#constant-pattern) detects when `null` is passed to this method.</span></span> <span data-ttu-id="c71a3-163">`null`Diğer desenler doğru türdeki yalnızca null olmayan bir nesneyle eşleştiğinden, düzen en son olabilir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-163">The `null` pattern can be last because the other patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="c71a3-164">Bu kodu aşağıdaki kodu kullanarak test edebilirsiniz `Program.cs` :</span><span class="sxs-lookup"><span data-stu-id="c71a3-164">You can test this code using the following code in `Program.cs`:</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    class Program
    {
        static void Main(string[] args)
        {
            var tollCalc = new TollCalculator();

            var car = new Car();
            var taxi = new Taxi();
            var bus = new Bus();
            var truck = new DeliveryTruck();

            Console.WriteLine($"The toll for a car is {tollCalc.CalculateToll(car)}");
            Console.WriteLine($"The toll for a taxi is {tollCalc.CalculateToll(taxi)}");
            Console.WriteLine($"The toll for a bus is {tollCalc.CalculateToll(bus)}");
            Console.WriteLine($"The toll for a truck is {tollCalc.CalculateToll(truck)}");

            try
            {
                tollCalc.CalculateToll("this will fail");
            }
            catch (ArgumentException e)
            {
                Console.WriteLine("Caught an argument exception when using the wrong type");
            }
            try
            {
                tollCalc.CalculateToll(null!);
            }
            catch (ArgumentNullException e)
            {
                Console.WriteLine("Caught an argument exception when using null");
            }
        }
    }
}
```

<span data-ttu-id="c71a3-165">Bu kod, başlatıcı projesine dahil edilmiştir, ancak açıklama eklenir. Açıklamaları kaldırın ve ne yazdığınızı test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="c71a3-166">Desenlerin kodun ve verilerin ayrı olduğu algoritmalar oluşturmanıza nasıl yardımcı olduğunu görmeyi başlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="c71a3-167">`switch`İfade, türü sınar ve sonuçlara göre farklı değerler üretir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="c71a3-168">Bu yalnızca başlangıç amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="c71a3-169">İskan fiyatlandırması Ekle</span><span class="sxs-lookup"><span data-stu-id="c71a3-169">Add occupancy pricing</span></span>

<span data-ttu-id="c71a3-170">Ücretli yetkili, en yüksek kapasiteden gezilerin gezmelerini teşvik etmek istiyor.</span><span class="sxs-lookup"><span data-stu-id="c71a3-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="c71a3-171">Araçlar daha az pastlar olduğunda daha fazla ücret ödemelerine ve daha düşük fiyatlandırma sunarak tam bir şekilde teşvik etmeye karar vermiştir:</span><span class="sxs-lookup"><span data-stu-id="c71a3-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="c71a3-172">Otomobiller ve Tax, hiçbir Pasca, ek $0,50 ödeyebilir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="c71a3-173">Otomobiller ve Tax, iki pasa, $0,50 indirimi alır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-173">Cars and taxis with two passengers get a $0.50 discount.</span></span>
- <span data-ttu-id="c71a3-174">Üç veya daha fazla Pascal ile otomobiller ve Tax, $1,00 indirimi alır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="c71a3-175">%50 ' den küçük veri yolları, fazladan $2,00 oranında ödeyin.</span><span class="sxs-lookup"><span data-stu-id="c71a3-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="c71a3-176">%90 ' den fazla tam veri yolları $1,00 indirimi elde edin.</span><span class="sxs-lookup"><span data-stu-id="c71a3-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="c71a3-177">Bu kurallar, aynı anahtar ifadesinde bir [özellik düzeniyle](../language-reference/operators/patterns.md#property-pattern) kullanılarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-177">These rules can be implemented using a [property pattern](../language-reference/operators/patterns.md#property-pattern) in the same switch expression.</span></span> <span data-ttu-id="c71a3-178">Özellik deseninin bir özellik değeri bir sabit değerle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-178">A property pattern compares a property value to a constant value.</span></span> <span data-ttu-id="c71a3-179">Özellik deseninin türü belirlendikten sonra nesnenin özellikleri incelenir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-179">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="c71a3-180">Bir için tek durum `Car` dört farklı durumda genişler:</span><span class="sxs-lookup"><span data-stu-id="c71a3-180">The single case for a `Car` expands to four different cases:</span></span>

```csharp
vehicle switch
{
    Car {Passengers: 0}        => 2.00m + 0.50m,
    Car {Passengers: 1}        => 2.0m,
    Car {Passengers: 2}        => 2.0m - 0.50m,
    Car c                      => 2.00m - 1.0m,

    // ...
};
```

<span data-ttu-id="c71a3-181">İlk üç durum türü bir olarak test `Car` edin, sonra özelliğin değerini kontrol edin `Passengers` .</span><span class="sxs-lookup"><span data-stu-id="c71a3-181">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="c71a3-182">Her ikisi de eşleşiyorsa, bu ifade değerlendirilir ve döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c71a3-182">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="c71a3-183">Ayrıca, taxiçin de benzer bir şekilde durum da genişletebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c71a3-183">You would also expand the cases for taxis in a similar manner:</span></span>

```csharp
vehicle switch
{
    // ...

    Taxi {Fares: 0}  => 3.50m + 1.00m,
    Taxi {Fares: 1}  => 3.50m,
    Taxi {Fares: 2}  => 3.50m - 0.50m,
    Taxi t           => 3.50m - 1.00m,

    // ...
};
```

<span data-ttu-id="c71a3-184">Ardından, aşağıdaki örnekte gösterildiği gibi, veri yolları için durumları genişleterek sahiplik kurallarını uygulayın:</span><span class="sxs-lookup"><span data-stu-id="c71a3-184">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

```csharp
vehicle switch
{
    // ...

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    // ...
};
```

<span data-ttu-id="c71a3-185">Ücretli yetkili, teslim kamyonları içindeki pastıcılar sayısıyla ilgilenmez.</span><span class="sxs-lookup"><span data-stu-id="c71a3-185">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="c71a3-186">Bunun yerine, aşağıdaki gibi, kamyonlar ağırlık sınıfına göre ücretli miktarı ayarlar:</span><span class="sxs-lookup"><span data-stu-id="c71a3-186">Instead, they adjust the toll amount based on the weight class of the trucks as follows:</span></span>

- <span data-ttu-id="c71a3-187">5000 lbs üzerinde structuralks, fazladan $5,00 ücretlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-187">Trucks over 5000 lbs are charged an extra $5.00.</span></span>
- <span data-ttu-id="c71a3-188">3000 lbs kapsamında hafif bir $2,00 indirimi verilir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-188">Light trucks under 3000 lbs are given a $2.00 discount.</span></span>

<span data-ttu-id="c71a3-189">Bu kural aşağıdaki kodla uygulanır:</span><span class="sxs-lookup"><span data-stu-id="c71a3-189">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="c71a3-190">Yukarıdaki kod, `when` anahtar ARM 'nin yan tümcesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-190">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="c71a3-191">`when`Bir özellikte eşitlik dışındaki koşulları test etmek için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c71a3-191">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="c71a3-192">İşiniz bittiğinde, aşağıdaki kod gibi görünen bir yönteme sahip olacaksınız:</span><span class="sxs-lookup"><span data-stu-id="c71a3-192">When you've finished, you'll have a method that looks much like the following code:</span></span>

```csharp
vehicle switch
{
    Car {Passengers: 0}        => 2.00m + 0.50m,
    Car {Passengers: 1}        => 2.0m,
    Car {Passengers: 2}        => 2.0m - 0.50m,
    Car c                      => 2.00m - 1.0m,

    Taxi {Fares: 0}  => 3.50m + 1.00m,
    Taxi {Fares: 1}  => 3.50m,
    Taxi {Fares: 2}  => 3.50m - 0.50m,
    Taxi t           => 3.50m - 1.00m,

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,

    { }     => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
    null    => throw new ArgumentNullException(nameof(vehicle))
};
```

<span data-ttu-id="c71a3-193">Bu anahtar kolları çoğu **özyinelemeli desenlere** örnektir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-193">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="c71a3-194">Örneğin, `Car { Passengers: 1}` bir özellik deseninin içinde sabit bir model gösterir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-194">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="c71a3-195">İç içe geçmiş anahtarlar kullanarak bu kodu daha az tekrarlı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-195">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="c71a3-196">`Car`Ve `Taxi` her ikisi de önceki örneklerde dört farklı kollu bir sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-196">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="c71a3-197">Her iki durumda da, bir sabit düzende akışlara yönelik bir bildirim stili oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-197">In both cases, you can create a declaration pattern that feeds into a constant pattern.</span></span> <span data-ttu-id="c71a3-198">Bu teknik aşağıdaki kodda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c71a3-198">This technique is shown in the following code:</span></span>

```csharp
public decimal CalculateToll(object vehicle) =>
    vehicle switch
    {
        Car c => c.Passengers switch
        {
            0 => 2.00m + 0.5m,
            1 => 2.0m,
            2 => 2.0m - 0.5m,
            _ => 2.00m - 1.0m
        },

        Taxi t => t.Fares switch
        {
            0 => 3.50m + 1.00m,
            1 => 3.50m,
            2 => 3.50m - 0.50m,
            _ => 3.50m - 1.00m
        },

        Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
        Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
        Bus b => 5.00m,

        DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
        DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
        DeliveryTruck t => 10.00m,

        { }  => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
        null => throw new ArgumentNullException(nameof(vehicle))
    };
```

<span data-ttu-id="c71a3-199">Önceki örnekte, özyinelemeli bir ifade kullanmak, `Car` `Taxi` özellik değerini test eden alt kolları içeren ve kolları yinelediğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-199">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="c71a3-200">Bu `Bus` Özellikler, ve `DeliveryTruck` kolları için kullanılmaz, çünkü bu Koller özellik için aralıkları test etmez, ayrık değerler değildir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-200">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="c71a3-201">Tepe fiyatlandırması Ekle</span><span class="sxs-lookup"><span data-stu-id="c71a3-201">Add peak pricing</span></span>

<span data-ttu-id="c71a3-202">Son özellik için, ücretli yetkili zamana duyarlı tepe fiyatlandırması eklemek istemektedir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-202">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="c71a3-203">Sabah ve akşam aceleniz saatlerinde, Tolls iki katına çıkar.</span><span class="sxs-lookup"><span data-stu-id="c71a3-203">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="c71a3-204">Bu kural yalnızca bir yönde trafiği etkiler: sabah şehrine gelen ve akşam aceleniz Hour 'daki çıkış.</span><span class="sxs-lookup"><span data-stu-id="c71a3-204">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="c71a3-205">İş gününde diğer saatlerde, Tolls %50 oranında artar.</span><span class="sxs-lookup"><span data-stu-id="c71a3-205">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="c71a3-206">Geç gece ve erken sabah, Tolls %25 oranında azaltılır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-206">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="c71a3-207">Hafta sonu sırasında, zamandan bağımsız olarak normal fiyat olur.</span><span class="sxs-lookup"><span data-stu-id="c71a3-207">During the weekend, it's the normal rate, regardless of the time.</span></span> <span data-ttu-id="c71a3-208">`if` `else` Bu ve deyimlerini aşağıdaki kodu kullanarak ifade etmek için bir seriler ve deyimler kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c71a3-208">You could use a series if `if` and `else` statements to express this using the following code:</span></span>

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#SnippetPremiumWithoutPattern)]

<span data-ttu-id="c71a3-209">Yukarıdaki kod doğru çalışır, ancak okunabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-209">The preceding code does work correctly, but isn't readable.</span></span> <span data-ttu-id="c71a3-210">Kod hakkında sebebini sağlamak için tüm giriş durumları ve iç içe geçmiş deyimlerini kullanarak zincirleyebilirsiniz `if` .</span><span class="sxs-lookup"><span data-stu-id="c71a3-210">You have to chain through all the input cases and the nested `if` statements to reason about the code.</span></span> <span data-ttu-id="c71a3-211">Bunun yerine, bu özellik için model eşleştirmeyi kullanacaksınız, ancak diğer tekniklerle tümleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-211">Instead, you'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="c71a3-212">Tüm yön, hafta günü ve saat birleşimleri için hesap oluşturacak tek bir kalıp eşleştirme ifadesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-212">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="c71a3-213">Sonuç karmaşık bir ifade olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-213">The result would be a complicated expression.</span></span> <span data-ttu-id="c71a3-214">Okunması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-214">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="c71a3-215">Bu, doğruluğu garanti etmelerini zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-215">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="c71a3-216">Bunun yerine, öz 'in tüm bu durumları açıkladığı bir dizi değer oluşturmak için bu yöntemleri birleştirin.</span><span class="sxs-lookup"><span data-stu-id="c71a3-216">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="c71a3-217">Ardından, ücretli bir çarpanı hesaplamak için model eşleştirmeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c71a3-217">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="c71a3-218">Kayıt düzeni üç farklı koşul içerir:</span><span class="sxs-lookup"><span data-stu-id="c71a3-218">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="c71a3-219">Gün, bir hafta içi veya bir hafta sonu olabilir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-219">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="c71a3-220">Ücretli sürenin toplanacağı zaman bandı.</span><span class="sxs-lookup"><span data-stu-id="c71a3-220">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="c71a3-221">Yön City veya City 'den</span><span class="sxs-lookup"><span data-stu-id="c71a3-221">The direction is into the city or out of the city</span></span>

<span data-ttu-id="c71a3-222">Aşağıdaki tabloda, giriş değerleri ve en yüksek fiyatlandırma çarpanı birleşimleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c71a3-222">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="c71a3-223">Gün</span><span class="sxs-lookup"><span data-stu-id="c71a3-223">Day</span></span>        | <span data-ttu-id="c71a3-224">Saat</span><span class="sxs-lookup"><span data-stu-id="c71a3-224">Time</span></span>         | <span data-ttu-id="c71a3-225">Yön</span><span class="sxs-lookup"><span data-stu-id="c71a3-225">Direction</span></span> | <span data-ttu-id="c71a3-226">Premium</span><span class="sxs-lookup"><span data-stu-id="c71a3-226">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="c71a3-227">Weekday</span><span class="sxs-lookup"><span data-stu-id="c71a3-227">Weekday</span></span>    | <span data-ttu-id="c71a3-228">sabah aceleniz</span><span class="sxs-lookup"><span data-stu-id="c71a3-228">morning rush</span></span> | <span data-ttu-id="c71a3-229">gelen</span><span class="sxs-lookup"><span data-stu-id="c71a3-229">inbound</span></span>   | <span data-ttu-id="c71a3-230">x 2,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-230">x 2.00</span></span>  |
| <span data-ttu-id="c71a3-231">Weekday</span><span class="sxs-lookup"><span data-stu-id="c71a3-231">Weekday</span></span>    | <span data-ttu-id="c71a3-232">sabah aceleniz</span><span class="sxs-lookup"><span data-stu-id="c71a3-232">morning rush</span></span> | <span data-ttu-id="c71a3-233">giden</span><span class="sxs-lookup"><span data-stu-id="c71a3-233">outbound</span></span>  | <span data-ttu-id="c71a3-234">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-234">x 1.00</span></span>  |
| <span data-ttu-id="c71a3-235">Weekday</span><span class="sxs-lookup"><span data-stu-id="c71a3-235">Weekday</span></span>    | <span data-ttu-id="c71a3-236">saati</span><span class="sxs-lookup"><span data-stu-id="c71a3-236">daytime</span></span>      | <span data-ttu-id="c71a3-237">gelen</span><span class="sxs-lookup"><span data-stu-id="c71a3-237">inbound</span></span>   | <span data-ttu-id="c71a3-238">x 1,50</span><span class="sxs-lookup"><span data-stu-id="c71a3-238">x 1.50</span></span>  |
| <span data-ttu-id="c71a3-239">Weekday</span><span class="sxs-lookup"><span data-stu-id="c71a3-239">Weekday</span></span>    | <span data-ttu-id="c71a3-240">saati</span><span class="sxs-lookup"><span data-stu-id="c71a3-240">daytime</span></span>      | <span data-ttu-id="c71a3-241">giden</span><span class="sxs-lookup"><span data-stu-id="c71a3-241">outbound</span></span>  | <span data-ttu-id="c71a3-242">x 1,50</span><span class="sxs-lookup"><span data-stu-id="c71a3-242">x 1.50</span></span>  |
| <span data-ttu-id="c71a3-243">Weekday</span><span class="sxs-lookup"><span data-stu-id="c71a3-243">Weekday</span></span>    | <span data-ttu-id="c71a3-244">akşam aceleniz</span><span class="sxs-lookup"><span data-stu-id="c71a3-244">evening rush</span></span> | <span data-ttu-id="c71a3-245">gelen</span><span class="sxs-lookup"><span data-stu-id="c71a3-245">inbound</span></span>   | <span data-ttu-id="c71a3-246">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-246">x 1.00</span></span>  |
| <span data-ttu-id="c71a3-247">Weekday</span><span class="sxs-lookup"><span data-stu-id="c71a3-247">Weekday</span></span>    | <span data-ttu-id="c71a3-248">akşam aceleniz</span><span class="sxs-lookup"><span data-stu-id="c71a3-248">evening rush</span></span> | <span data-ttu-id="c71a3-249">giden</span><span class="sxs-lookup"><span data-stu-id="c71a3-249">outbound</span></span>  | <span data-ttu-id="c71a3-250">x 2,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-250">x 2.00</span></span>  |
| <span data-ttu-id="c71a3-251">Weekday</span><span class="sxs-lookup"><span data-stu-id="c71a3-251">Weekday</span></span>    | <span data-ttu-id="c71a3-252">gece</span><span class="sxs-lookup"><span data-stu-id="c71a3-252">overnight</span></span>    | <span data-ttu-id="c71a3-253">gelen</span><span class="sxs-lookup"><span data-stu-id="c71a3-253">inbound</span></span>   | <span data-ttu-id="c71a3-254">x 0,75</span><span class="sxs-lookup"><span data-stu-id="c71a3-254">x 0.75</span></span>  |
| <span data-ttu-id="c71a3-255">Weekday</span><span class="sxs-lookup"><span data-stu-id="c71a3-255">Weekday</span></span>    | <span data-ttu-id="c71a3-256">gece</span><span class="sxs-lookup"><span data-stu-id="c71a3-256">overnight</span></span>    | <span data-ttu-id="c71a3-257">giden</span><span class="sxs-lookup"><span data-stu-id="c71a3-257">outbound</span></span>  | <span data-ttu-id="c71a3-258">x 0,75</span><span class="sxs-lookup"><span data-stu-id="c71a3-258">x 0.75</span></span>  |
| <span data-ttu-id="c71a3-259">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="c71a3-259">Weekend</span></span>    | <span data-ttu-id="c71a3-260">sabah aceleniz</span><span class="sxs-lookup"><span data-stu-id="c71a3-260">morning rush</span></span> | <span data-ttu-id="c71a3-261">gelen</span><span class="sxs-lookup"><span data-stu-id="c71a3-261">inbound</span></span>   | <span data-ttu-id="c71a3-262">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-262">x 1.00</span></span>  |
| <span data-ttu-id="c71a3-263">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="c71a3-263">Weekend</span></span>    | <span data-ttu-id="c71a3-264">sabah aceleniz</span><span class="sxs-lookup"><span data-stu-id="c71a3-264">morning rush</span></span> | <span data-ttu-id="c71a3-265">giden</span><span class="sxs-lookup"><span data-stu-id="c71a3-265">outbound</span></span>  | <span data-ttu-id="c71a3-266">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-266">x 1.00</span></span>  |
| <span data-ttu-id="c71a3-267">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="c71a3-267">Weekend</span></span>    | <span data-ttu-id="c71a3-268">saati</span><span class="sxs-lookup"><span data-stu-id="c71a3-268">daytime</span></span>      | <span data-ttu-id="c71a3-269">gelen</span><span class="sxs-lookup"><span data-stu-id="c71a3-269">inbound</span></span>   | <span data-ttu-id="c71a3-270">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-270">x 1.00</span></span>  |
| <span data-ttu-id="c71a3-271">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="c71a3-271">Weekend</span></span>    | <span data-ttu-id="c71a3-272">saati</span><span class="sxs-lookup"><span data-stu-id="c71a3-272">daytime</span></span>      | <span data-ttu-id="c71a3-273">giden</span><span class="sxs-lookup"><span data-stu-id="c71a3-273">outbound</span></span>  | <span data-ttu-id="c71a3-274">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-274">x 1.00</span></span>  |
| <span data-ttu-id="c71a3-275">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="c71a3-275">Weekend</span></span>    | <span data-ttu-id="c71a3-276">akşam aceleniz</span><span class="sxs-lookup"><span data-stu-id="c71a3-276">evening rush</span></span> | <span data-ttu-id="c71a3-277">gelen</span><span class="sxs-lookup"><span data-stu-id="c71a3-277">inbound</span></span>   | <span data-ttu-id="c71a3-278">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-278">x 1.00</span></span>  |
| <span data-ttu-id="c71a3-279">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="c71a3-279">Weekend</span></span>    | <span data-ttu-id="c71a3-280">akşam aceleniz</span><span class="sxs-lookup"><span data-stu-id="c71a3-280">evening rush</span></span> | <span data-ttu-id="c71a3-281">giden</span><span class="sxs-lookup"><span data-stu-id="c71a3-281">outbound</span></span>  | <span data-ttu-id="c71a3-282">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-282">x 1.00</span></span>  |
| <span data-ttu-id="c71a3-283">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="c71a3-283">Weekend</span></span>    | <span data-ttu-id="c71a3-284">gece</span><span class="sxs-lookup"><span data-stu-id="c71a3-284">overnight</span></span>    | <span data-ttu-id="c71a3-285">gelen</span><span class="sxs-lookup"><span data-stu-id="c71a3-285">inbound</span></span>   | <span data-ttu-id="c71a3-286">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-286">x 1.00</span></span>  |
| <span data-ttu-id="c71a3-287">Hafta Sonu</span><span class="sxs-lookup"><span data-stu-id="c71a3-287">Weekend</span></span>    | <span data-ttu-id="c71a3-288">gece</span><span class="sxs-lookup"><span data-stu-id="c71a3-288">overnight</span></span>    | <span data-ttu-id="c71a3-289">giden</span><span class="sxs-lookup"><span data-stu-id="c71a3-289">outbound</span></span>  | <span data-ttu-id="c71a3-290">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c71a3-290">x 1.00</span></span>  |

<span data-ttu-id="c71a3-291">Üç değişkenin 16 farklı birleşimi vardır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-291">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="c71a3-292">Bazı koşulları birleştirerek son anahtar ifadesini basitleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-292">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="c71a3-293">Tolls 'yi toplayan sistem, <xref:System.DateTime> ücretli olarak toplanan zaman için bir yapı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-293">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="c71a3-294">Yukarıdaki tablodan değişkenleri oluşturan üye yöntemleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c71a3-294">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="c71a3-295">Aşağıdaki işlev bir bir <xref:System.DateTime> hafta sonu veya haftanın gününü temsil edip etmediğini ifade etmek için bir model eşleştirme anahtar ifadesi kullanır:</span><span class="sxs-lookup"><span data-stu-id="c71a3-295">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

```csharp
private static bool IsWeekDay(DateTime timeOfToll) =>
    timeOfToll.DayOfWeek switch
    {
        DayOfWeek.Monday    => true,
        DayOfWeek.Tuesday   => true,
        DayOfWeek.Wednesday => true,
        DayOfWeek.Thursday  => true,
        DayOfWeek.Friday    => true,
        DayOfWeek.Saturday  => false,
        DayOfWeek.Sunday    => false
    };
```

<span data-ttu-id="c71a3-296">Bu yöntem doğrudur, ancak repetitious.</span><span class="sxs-lookup"><span data-stu-id="c71a3-296">That method is correct, but it's repetitious.</span></span> <span data-ttu-id="c71a3-297">Aşağıdaki kodda gösterildiği gibi basitleşebilir:</span><span class="sxs-lookup"><span data-stu-id="c71a3-297">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="c71a3-298">Sonra, zaman bloklara zaman kategorize etmek için benzer bir işlev ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c71a3-298">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="c71a3-299">`enum`Her zaman aralığını ayrı bir değere dönüştürmek için bir özel ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c71a3-299">You add a private `enum` to convert each range of time to a discrete value.</span></span> <span data-ttu-id="c71a3-300">Ardından, `GetTimeBand` yöntemi, C# 9,0 ' de eklenen [ilişkisel desenleri](../language-reference/operators/patterns.md#relational-patterns)ve birlikte bulunan [ `or` desenleri](../language-reference/operators/patterns.md#logical-patterns)kullanır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-300">Then, the `GetTimeBand` method uses [relational patterns](../language-reference/operators/patterns.md#relational-patterns), and [conjunctive `or` patterns](../language-reference/operators/patterns.md#logical-patterns), both added in C# 9.0.</span></span> <span data-ttu-id="c71a3-301">İlişkisel bir model,,, veya kullanarak sayısal bir değeri test etmenizi sağlar `<` `>` `<=` `>=` .</span><span class="sxs-lookup"><span data-stu-id="c71a3-301">A relational pattern lets you test a numeric value using `<`, `>`, `<=`, or `>=`.</span></span> <span data-ttu-id="c71a3-302">Bir `or` ifadenin bir veya daha fazla desenle eşleşmesi durumunda desen test eder.</span><span class="sxs-lookup"><span data-stu-id="c71a3-302">The `or` pattern tests if an expression matches one or more patterns.</span></span> <span data-ttu-id="c71a3-303">Ayrıca `and` , bir ifadenin iki ayrı desenle eşleştiğinden emin olmak için bir desen ve bir `not` ifadenin bir desenle eşleşmediğini test etmek için bir desen de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-303">You can also use an `and` pattern to ensure that an expression matches two distinct patterns, and a `not` pattern to test that an expression doesn't match a pattern.</span></span>

<span data-ttu-id="c71a3-304">Bu yöntemleri oluşturduktan sonra, `switch` fiyatlandırma Premium 'u hesaplamak için **demet düzenine** sahip başka bir ifadeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-304">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="c71a3-305">`switch`Tüm 16 kollu bir ifade oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c71a3-305">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="c71a3-306">Yukarıdaki kod işe yarar, ancak basitleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-306">The above code works, but it can be simplified.</span></span> <span data-ttu-id="c71a3-307">Hafta sonu için sekiz kombinasyonun hepsi de aynı ücretli bir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-307">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="c71a3-308">Tüm sekiz değerini aşağıdaki satırla değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c71a3-308">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="c71a3-309">Hem gelen hem de giden trafik, hafta içi gündüz ve gece saatlerinde aynı katkılar.</span><span class="sxs-lookup"><span data-stu-id="c71a3-309">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="c71a3-310">Bu dört anahtar kolları aşağıdaki iki satır ile değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="c71a3-310">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="c71a3-311">Kod, bu iki değişiklikten sonra aşağıdaki kod gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="c71a3-311">The code should look like the following code after those two changes:</span></span>

```csharp
public decimal PeakTimePremium(DateTime timeOfToll, bool inbound) =>
    (IsWeekDay(timeOfToll), GetTimeBand(timeOfToll), inbound) switch
    {
        (true, TimeBand.MorningRush, true)  => 2.00m,
        (true, TimeBand.MorningRush, false) => 1.00m,
        (true, TimeBand.Daytime,     _)     => 1.50m,
        (true, TimeBand.EveningRush, true)  => 1.00m,
        (true, TimeBand.EveningRush, false) => 2.00m,
        (true, TimeBand.Overnight,   _)     => 0.75m,
        (false, _,                   _)     => 1.00m,
    };
```

<span data-ttu-id="c71a3-312">Son olarak, normal fiyatı ödeyerek iki aceleniz saatlik saati kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-312">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="c71a3-313">Bu kolları kaldırdıktan sonra, `false` `_` son anahtar ARM içindeki ' ı bir at () ile değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-313">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="c71a3-314">Aşağıdaki tamamlanmış yönteme sahip olacaksınız:</span><span class="sxs-lookup"><span data-stu-id="c71a3-314">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="c71a3-315">Bu örnek, düzen eşleştirmesinin avantajlarından birini vurgular: düzen dalları sırayla değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-315">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="c71a3-316">Daha önceki bir dalın daha sonraki durumlardan birini işleyeceği şekilde yeniden ayarlarsanız, derleyici ulaşılamaz kod hakkında sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-316">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="c71a3-317">Bu dil kuralları, önceki basitleştirmeleri kodun değiştirmiyordu güvenle daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-317">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="c71a3-318">Model eşleştirme bazı kod türlerini daha okunaklı hale getirir ve sınıflarınıza kod ekleyemadığınızda nesne odaklı teknikler için bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="c71a3-318">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="c71a3-319">Bulut, verilerin ve işlevlerin canlı olmasına neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="c71a3-319">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="c71a3-320">Verilerin *şekli* ve üzerindeki *işlemler* birlikte açıklanmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-320">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="c71a3-321">Bu öğreticide, var olan verileri özgün işlevinden tamamen farklı şekillerde kullandınız.</span><span class="sxs-lookup"><span data-stu-id="c71a3-321">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="c71a3-322">Model eşleştirme, bunları genişletmemiş olsanız bile, bu türlerin üzerine geçen işlevselliği yazma olanağını vermiştir.</span><span class="sxs-lookup"><span data-stu-id="c71a3-322">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c71a3-323">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c71a3-323">Next steps</span></span>

<span data-ttu-id="c71a3-324">Tamamlanan kodu [DotNet/Samples](https://github.com/dotnet/samples/tree/main/csharp/tutorials/patterns/finished) GitHub deposundan indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-324">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/main/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="c71a3-325">Kendi hiyerarşinizdeki desenleri keşfedebilir ve bu tekniği düzenli kodlama etkinliklerinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c71a3-325">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="c71a3-326">Bu teknikleri öğrenirken, sorun yaklaşımı ve yeni işlevler oluşturmak için kullanabileceğiniz başka bir yol sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c71a3-326">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>

## <a name="see-also"></a><span data-ttu-id="c71a3-327">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c71a3-327">See also</span></span>

- [<span data-ttu-id="c71a3-328">Desenler</span><span class="sxs-lookup"><span data-stu-id="c71a3-328">Patterns</span></span>](../language-reference/operators/patterns.md)
- [<span data-ttu-id="c71a3-329">`switch` ifadesini</span><span class="sxs-lookup"><span data-stu-id="c71a3-329">`switch` expression</span></span>](../language-reference/operators/switch-expression.md)
