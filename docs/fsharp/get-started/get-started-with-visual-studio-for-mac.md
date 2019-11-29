---
title: Mac için Visual Studio ile F# çalışmaya başlama
description: Mac için Visual Studio ile kullanmayı F# öğrenin.
ms.date: 07/03/2018
ms.openlocfilehash: cd45ab9c59cef76e4bf85a93f39d8e2ee063d200
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552364"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="a1a78-103">Mac için Visual Studio ile F# çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="a1a78-103">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="a1a78-104">F#Görsel F# araç Mac için Visual Studio IDE 'de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="a1a78-104">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span> <span data-ttu-id="a1a78-105">[Mac için Visual Studio yüklü](install-fsharp.md#install-f-with-visual-studio-for-mac)olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a1a78-105">Ensure that you have [Visual Studio for Mac installed](install-fsharp.md#install-f-with-visual-studio-for-mac).</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="a1a78-106">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a1a78-106">Creating a console application</span></span>

<span data-ttu-id="a1a78-107">Mac için Visual Studio ' deki en temel projelerden biri konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a1a78-107">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="a1a78-108">Bunun nasıl yapılacağını aşağıda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1a78-108">Here's how to do it.</span></span>  <span data-ttu-id="a1a78-109">Mac için Visual Studio açıldıktan sonra:</span><span class="sxs-lookup"><span data-stu-id="a1a78-109">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="a1a78-110">**Dosya** menüsünde, **yeni çözüm**' ı işaret edin.</span><span class="sxs-lookup"><span data-stu-id="a1a78-110">On the **File** menu, point to **New Solution**.</span></span>

2. <span data-ttu-id="a1a78-111">Yeni proje iletişim kutusunda, konsol uygulaması için 2 farklı şablon vardır.</span><span class="sxs-lookup"><span data-stu-id="a1a78-111">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="a1a78-112">.NET Framework hedefleyen diğer > .NET altında bir tane vardır.</span><span class="sxs-lookup"><span data-stu-id="a1a78-112">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="a1a78-113">Diğer şablon, .NET Core ' u hedefleyen .NET Core-> uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a1a78-113">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="a1a78-114">Her iki şablon da bu makalenin amacına göre çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1a78-114">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="a1a78-115">Konsol uygulaması altında, gerekirse C# olarak F# değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a1a78-115">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="a1a78-116">İleri gitmek için **İleri** düğmesini seçin!</span><span class="sxs-lookup"><span data-stu-id="a1a78-116">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="a1a78-117">Projenize bir ad verin ve uygulama için istediğiniz seçenekleri belirleyin.</span><span class="sxs-lookup"><span data-stu-id="a1a78-117">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="a1a78-118">Ekranın yanındaki Önizleme bölmesi, seçilen seçeneklere göre oluşturulacak dizin yapısını gösterecek şekilde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a1a78-118">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="a1a78-119">**Oluştur**'u tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a1a78-119">Click **Create**.</span></span>  <span data-ttu-id="a1a78-120">Artık Çözüm Gezgini bir F# proje görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1a78-120">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="a1a78-121">Kodunuzu yazma</span><span class="sxs-lookup"><span data-stu-id="a1a78-121">Writing your code</span></span>

<span data-ttu-id="a1a78-122">Önce bazı kodları yazmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="a1a78-122">Let's get started by writing some code first.</span></span>  <span data-ttu-id="a1a78-123">`Program.fs` dosyasının açık olduğundan emin olun ve ardından içeriğini aşağıdakiler ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a1a78-123">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="a1a78-124">Önceki kod örneğinde, `x` adlı bir girişi alan ve kendisini kendisi ile çarparak `square` bir işlev tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a1a78-124">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="a1a78-125">F# [Tür çıkarımı](../language-reference/type-inference.md)kullandığından `x` türünün belirtilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a1a78-125">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="a1a78-126">F# Derleyici, çarpma 'nın geçerli olduğu türleri anlamıştır ve `square` nasıl çağrıldığını temel alarak `x` bir tür atayacaktır.</span><span class="sxs-lookup"><span data-stu-id="a1a78-126">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="a1a78-127">`square`üzerine geldiğinizde, aşağıdakileri görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="a1a78-127">If you hover over `square`, you should see the following:</span></span>

```console
val square: x:int -> int
```

<span data-ttu-id="a1a78-128">İşlevin tür imzası olarak bilinen budur.</span><span class="sxs-lookup"><span data-stu-id="a1a78-128">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="a1a78-129">Şu şekilde okunabilir: "kare x adlı bir tamsayı alan ve tamsayı üreten bir işlevdir".</span><span class="sxs-lookup"><span data-stu-id="a1a78-129">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="a1a78-130">Derleyicinin şu an için `int` türü `square` olduğunu unutmayın. bunun nedeni, çarpma işlemi *Tüm* türler genelinde geneldir, ancak bunun yerine kapalı bir tür kümesinde geneldir.</span><span class="sxs-lookup"><span data-stu-id="a1a78-130">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="a1a78-131">F# Derleyici bu noktada `int` çekildi, ancak `square` `float`gibi farklı bir giriş türüyle çağırırsanız tür imzasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a1a78-131">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="a1a78-132">`main`başka bir işlev, `EntryPoint` özniteliğiyle birlikte düzenlenmiş ve bu, F# derleyicinin program yürütmesinin burada başlaması gerektiğini söylemelidir.</span><span class="sxs-lookup"><span data-stu-id="a1a78-132">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="a1a78-133">Komut satırı bağımsız değişkenlerinin bu işleve geçirilebileceği ve bir tamsayı kodunun döndürüldüğü (genellikle `0`) diğer [C stili programlama dilleri](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B)ile aynı kuralı izler.</span><span class="sxs-lookup"><span data-stu-id="a1a78-133">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="a1a78-134">Bu işlev, `square` işlevini `12`bir bağımsız değişkeniyle çağıracağız.</span><span class="sxs-lookup"><span data-stu-id="a1a78-134">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="a1a78-135">F# Derleyici daha sonra `int -> int` (bir `int` alan ve bir `int`üreten bir işlev) `square` türünü atar.</span><span class="sxs-lookup"><span data-stu-id="a1a78-135">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="a1a78-136">`printfn` çağrısı, C stili programlama dillerine benzer bir biçim dizesi, biçim dizesinde belirtilen parametrelere karşılık gelen parametreler ve sonra sonucu ve yeni bir satırı yazdıran biçimli bir yazdırma işlevidir.</span><span class="sxs-lookup"><span data-stu-id="a1a78-136">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="a1a78-137">Kodunuzu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a1a78-137">Running your code</span></span>

<span data-ttu-id="a1a78-138">Kodu çalıştırabilir ve en üst düzey menüsünde **Çalıştır** ' a tıklayıp **hata ayıklama olmadan başlatabilirsiniz**.</span><span class="sxs-lookup"><span data-stu-id="a1a78-138">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="a1a78-139">Bu işlem, programı hata ayıklamadan çalıştırır ve sonuçları görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1a78-139">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="a1a78-140">Şimdi, Mac için Visual Studio oluşan konsol penceresinde yazdırılmış olan aşağıdakileri görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="a1a78-140">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```console
12 squared is 144!
```

<span data-ttu-id="a1a78-141">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="a1a78-141">Congratulations!</span></span>  <span data-ttu-id="a1a78-142">İlk F# projenizi Mac için Visual Studio oluşturdunuz, bu işlevi çağıran sonuçları yazdırılmış bir F# işlev yazdı ve bazı sonuçları görmek için projeyi çalıştırdık.</span><span class="sxs-lookup"><span data-stu-id="a1a78-142">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="a1a78-143">Etkileşimli F# kullanma</span><span class="sxs-lookup"><span data-stu-id="a1a78-143">Using F# Interactive</span></span>

<span data-ttu-id="a1a78-144">Mac için Visual Studio içinde görsel F# araç oluşturma özelliğinin en iyi özelliklerinden biri F# etkileşimli penceresidir.</span><span class="sxs-lookup"><span data-stu-id="a1a78-144">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="a1a78-145">Bu kodu çağırabileceğiniz ve sonucu etkileşimli olarak görebileceğiniz bir işleme kod göndermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1a78-145">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="a1a78-146">Kullanmaya başlamak için kodunuzda tanımlanan `square` işlevini vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="a1a78-146">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="a1a78-147">Sonra, üst düzey menüsünden **Düzenle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a1a78-147">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="a1a78-148">Sonra **seçimi etkileşimli olarak F# gönder**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a1a78-148">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="a1a78-149">Bu, kodu F# etkileşimli pencerede yürütür.</span><span class="sxs-lookup"><span data-stu-id="a1a78-149">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="a1a78-150">Alternatif olarak, seçime sağ tıklayıp **seçimi etkileşimli öğesine F# gönder**' i seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1a78-150">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="a1a78-151">F# Etkileşimli pencerenin içinde aşağıdaki gibi göründüğünü görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="a1a78-151">You should see the F# Interactive Window appear with the following in it:</span></span>

```console
>

val square : x:int -> int

>
```

<span data-ttu-id="a1a78-152">Bu, daha önce işlevin üzerine gelindiğinde gördüğünüz `square` işlevi için aynı işlev imzasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1a78-152">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="a1a78-153">`square` artık F# etkileşimli işlemde tanımlandığından, farklı değerlerle çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a1a78-153">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="a1a78-154">Bu işlevi yürütür, sonucu yeni bir ada `it`bağlar ve `it`türünü ve değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a1a78-154">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="a1a78-155">`;;`ile her satırı sonlandırabilmeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a1a78-155">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="a1a78-156">Bu, işlev F# çağrın ne zaman tamamlandığını etkileşimli olarak bilir.</span><span class="sxs-lookup"><span data-stu-id="a1a78-156">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="a1a78-157">Etkileşimli ' F# de yeni işlevler de tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a1a78-157">You can also define new functions in F# Interactive:</span></span>

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="a1a78-158">Yukarıdaki `isOdd`yeni bir işlevi tanımlar, bu bir `int` alır ve tek olup olmadığını denetler!</span><span class="sxs-lookup"><span data-stu-id="a1a78-158">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="a1a78-159">Bu işlevi, farklı girişlerle ne döndürdüğünü görmek için çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a1a78-159">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="a1a78-160">İşlev çağrılarının içindeki işlevleri çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a1a78-160">You can call functions within function calls:</span></span>

```console
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="a1a78-161">Ayrıca, değeri iki işlev için ardışık düzen için [Kanal-iletme işlecini](../language-reference/symbol-and-operator-reference/index.md) de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a1a78-161">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="a1a78-162">Kanal iletme operatörü ve daha fazlası sonraki öğreticilerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="a1a78-162">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="a1a78-163">Etkileşimli ile F# yapabileceklerinize yalnızca bir göz atmak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="a1a78-163">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="a1a78-164">Daha fazla bilgi edinmek için [ F#ile etkileşimli programlamaya ](../tutorials/fsharp-interactive/index.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="a1a78-164">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a1a78-165">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a1a78-165">Next steps</span></span>

<span data-ttu-id="a1a78-166">Henüz yapmadıysanız, F# dilin bazı temel özelliklerini kapsayan [turuna F# ](../tour.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="a1a78-166">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="a1a78-167">Bu, bazı özelliklerine F#ilişkin bir genel bakış sağlar ve Mac için Visual Studio kopyalayabilir ve çalıştırmak için örnek kod örnekleri sunar.</span><span class="sxs-lookup"><span data-stu-id="a1a78-167">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="a1a78-168">Ayrıca, [ F# kılavuzda](../index.yml)gösterilen bazı harika dış kaynaklar da mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="a1a78-168">There are also some great external resources you can use, showcased in the [F# Guide](../index.yml).</span></span>

## <a name="see-also"></a><span data-ttu-id="a1a78-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1a78-169">See also</span></span>

- [<span data-ttu-id="a1a78-170">F#Rehberi</span><span class="sxs-lookup"><span data-stu-id="a1a78-170">F# guide</span></span>](../index.yml)
- [<span data-ttu-id="a1a78-171">F# Turu</span><span class="sxs-lookup"><span data-stu-id="a1a78-171">Tour of F#</span></span>](../tour.md)
- [<span data-ttu-id="a1a78-172">F#dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="a1a78-172">F# language reference</span></span>](../language-reference/index.md)
- [<span data-ttu-id="a1a78-173">Tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="a1a78-173">Type inference</span></span>](../language-reference/type-inference.md)
- [<span data-ttu-id="a1a78-174">Sembol ve işleç başvurusu</span><span class="sxs-lookup"><span data-stu-id="a1a78-174">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)
