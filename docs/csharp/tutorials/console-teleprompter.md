---
title: Konsol Uygulaması
description: Bu öğretici, .NET Core ve bu C# dilin çeşitli özelliklerini öğretir.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 09ce36e7a61f576dc4449976ce676701dc57c9cd
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921130"
---
# <a name="console-app"></a><span data-ttu-id="89929-103">Konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="89929-103">Console app</span></span>

<span data-ttu-id="89929-104">Bu öğretici, .NET Core ve bu C# dilin çeşitli özelliklerini öğretir.</span><span class="sxs-lookup"><span data-stu-id="89929-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="89929-105">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="89929-105">You'll learn:</span></span>

- <span data-ttu-id="89929-106">.NET Core CLI temel kavramları</span><span class="sxs-lookup"><span data-stu-id="89929-106">The basics of the .NET Core CLI</span></span>
- <span data-ttu-id="89929-107">C# Konsol uygulamasının yapısı</span><span class="sxs-lookup"><span data-stu-id="89929-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="89929-108">Konsol g/ç</span><span class="sxs-lookup"><span data-stu-id="89929-108">Console I/O</span></span>
- <span data-ttu-id="89929-109">.NET 'teki dosya g/ç API 'Lerinin temelleri</span><span class="sxs-lookup"><span data-stu-id="89929-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="89929-110">.NET ' te görev tabanlı zaman uyumsuz programlama temelleri</span><span class="sxs-lookup"><span data-stu-id="89929-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="89929-111">Bir metin dosyasını okuyan ve bu metin dosyasının içeriğini konsola yansıtan bir uygulama oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="89929-111">You'll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="89929-112">Konsola giden çıkış, okumayı yüksek sesle eşleştirmeye yönelik olarak ilerleyebileceğiniz bir adım adım olur.</span><span class="sxs-lookup"><span data-stu-id="89929-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="89929-113">' < ' (Küçüktür) veya ' > ' (büyüktür) anahtarlarına basarak hızla hızlandıramaz veya azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89929-113">You can speed up or slow down the pace by pressing the '<' (less than) or '>' (greater than) keys.</span></span>

<span data-ttu-id="89929-114">Bu öğreticide birçok özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="89929-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="89929-115">Bunları birer birer oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="89929-115">Let's build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="89929-116">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="89929-116">Prerequisites</span></span>

- <span data-ttu-id="89929-117">Makinenizi .NET Core çalıştıracak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="89929-117">Set up your machine to run .NET Core.</span></span> <span data-ttu-id="89929-118">Yükleme yönergelerini [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89929-118">You can find the installation instructions on the [.NET Core downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="89929-119">Bu uygulamayı Windows, Linux, macOS veya Docker kapsayıcısında çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89929-119">You can run this application on Windows, Linux, macOS, or in a Docker container.</span></span>

- <span data-ttu-id="89929-120">En sevdiğiniz kod düzenleyicinizi yükler.</span><span class="sxs-lookup"><span data-stu-id="89929-120">Install your favorite code editor.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="89929-121">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="89929-121">Create the app</span></span>

<span data-ttu-id="89929-122">İlk adım yeni bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="89929-122">The first step is to create a new application.</span></span> <span data-ttu-id="89929-123">Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89929-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="89929-124">Geçerli dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89929-124">Make that the current directory.</span></span> <span data-ttu-id="89929-125">Komut istemine komut `dotnet new console` yazın.</span><span class="sxs-lookup"><span data-stu-id="89929-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="89929-126">Bu, temel bir "Merhaba Dünya" uygulaması için başlangıç dosyalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89929-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="89929-127">Değişiklik yapmaya başlamadan önce, basit Merhaba Dünya uygulamasını çalıştırmak için adımları ilerlim.</span><span class="sxs-lookup"><span data-stu-id="89929-127">Before you start making modifications, let's go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="89929-128">Uygulamayı oluşturduktan sonra komut istemine `dotnet restore` yazın.</span><span class="sxs-lookup"><span data-stu-id="89929-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="89929-129">Bu komut NuGet paketi geri yükleme işlemini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="89929-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="89929-130">NuGet bir .NET paket yöneticisidir.</span><span class="sxs-lookup"><span data-stu-id="89929-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="89929-131">Bu komut, projeniz için eksik bağımlılıkları indirir.</span><span class="sxs-lookup"><span data-stu-id="89929-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="89929-132">Bu yeni bir proje olduğundan, bağımlılıklardan hiçbiri yerinde değildir, bu nedenle ilk çalıştırma .NET Core çerçevesini indirir.</span><span class="sxs-lookup"><span data-stu-id="89929-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="89929-133">Bu ilk adımdan sonra, yalnızca yeni bağımlı paketler eklediğinizde `dotnet restore` çalıştırmanız veya bağımlılıklarınızın herhangi birinin sürümlerini güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89929-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="89929-134">Paketleri geri yükledikten sonra `dotnet build`çalıştırırsınız.</span><span class="sxs-lookup"><span data-stu-id="89929-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="89929-135">Bu, yapı altyapısını yürütür ve uygulamanızı çalıştırılabilir olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89929-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="89929-136">Son olarak, uygulamanızı çalıştırmak için `dotnet run` yürütün.</span><span class="sxs-lookup"><span data-stu-id="89929-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="89929-137">Basit Merhaba Dünya uygulama kodu Program.cs ' de bulunur.</span><span class="sxs-lookup"><span data-stu-id="89929-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="89929-138">Bu dosyayı en sevdiğiniz metin düzenleyicinizle açın.</span><span class="sxs-lookup"><span data-stu-id="89929-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="89929-139">İlk değişikliklerimizi yapmak bizim için çalışıyoruz.</span><span class="sxs-lookup"><span data-stu-id="89929-139">We're about to make our first changes.</span></span> <span data-ttu-id="89929-140">Dosyanın en üstünde, bkz. using deyimleri:</span><span class="sxs-lookup"><span data-stu-id="89929-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="89929-141">Bu ifade, derleyiciye `System` ad alanındaki herhangi bir türün kapsam içinde olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="89929-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="89929-142">Kullandığınız diğer nesne yönelimli diller gibi, C# türleri düzenlemek için ad alanlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="89929-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="89929-143">Bu Merhaba Dünya program farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="89929-143">This Hello World program is no different.</span></span> <span data-ttu-id="89929-144">Programın adı ile geçerli dizinin adına bağlı olarak ad alanı içinde bulunduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89929-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="89929-145">Bu öğretici için ad alanının adını `TeleprompterConsole`olarak değiştirelim:</span><span class="sxs-lookup"><span data-stu-id="89929-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="89929-146">Dosyayı okuma ve Yankılandırın</span><span class="sxs-lookup"><span data-stu-id="89929-146">Reading and Echoing the File</span></span>

<span data-ttu-id="89929-147">Eklenecek ilk özellik, bir metin dosyasını okuma ve bu metnin tümünü konsola görüntüleme olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="89929-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="89929-148">İlk olarak bir metin dosyası ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="89929-148">First, let's add a text file.</span></span> <span data-ttu-id="89929-149">Bu [örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) için GitHub deposundan [samplequotes. txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) dosyasını proje dizininize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="89929-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="89929-150">Bu, uygulamanız için komut dosyası olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="89929-150">This will serve as the script for your application.</span></span> <span data-ttu-id="89929-151">Bu konu için örnek uygulamanın nasıl indirileceği hakkında bilgi isterseniz, [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) konusundaki yönergelere bakın.</span><span class="sxs-lookup"><span data-stu-id="89929-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="89929-152">Sonra, `Program` Sınıfınıza aşağıdaki yöntemi ekleyin (`Main` yönteminin hemen altına):</span><span class="sxs-lookup"><span data-stu-id="89929-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

<span data-ttu-id="89929-153">Bu yöntem iki yeni ad alanından türler kullanır.</span><span class="sxs-lookup"><span data-stu-id="89929-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="89929-154">Bu derleme için, dosyanın en üstüne aşağıdaki iki satırı eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="89929-154">For this to compile you'll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="89929-155"><xref:System.Collections.Generic.IEnumerable%601> arabirimi <xref:System.Collections.Generic> ad alanında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="89929-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="89929-156"><xref:System.IO.File> sınıfı, <xref:System.IO> ad alanında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="89929-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="89929-157">Bu yöntem, *yineleyici yöntemi*olarak adlandırılan C# özel bir yöntem türüdür.</span><span class="sxs-lookup"><span data-stu-id="89929-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="89929-158">Numaralandırıcı yöntemleri değerlendirilen dizileri döndürür geç.</span><span class="sxs-lookup"><span data-stu-id="89929-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="89929-159">Bu, dizideki her öğe, diziyi kullanan kod tarafından istenerek oluşturulduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="89929-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="89929-160">Numaralandırıcı yöntemleri bir veya daha fazla [`yield return`](../language-reference/keywords/yield.md) deyimi içeren yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="89929-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="89929-161">`ReadFrom` yöntemi tarafından döndürülen nesne, dizideki her bir öğeyi oluşturmak için kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="89929-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="89929-162">Bu örnekte, kaynak dosyadaki bir sonraki metin satırını okumayı ve bu dizeyi döndürmeyle ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="89929-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="89929-163">Çağıran kod, sıradaki bir sonraki öğeyi her istediğinde, kod dosyadaki metnin bir sonraki satırını okur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="89929-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="89929-164">Dosya tamamen okunmadığında, dizi daha fazla öğe olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89929-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="89929-165">Size yeni olabilecek iki C# farklı sözdizimi öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="89929-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="89929-166">Bu yöntemdeki [`using`](../language-reference/keywords/using-statement.md) ifadesinin kaynağı temizleme işlemini yönetir.</span><span class="sxs-lookup"><span data-stu-id="89929-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="89929-167">`using` bildiriminde (`reader`, bu örnekte) başlatılan değişken <xref:System.IDisposable> arabirimini gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="89929-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="89929-168">Bu arabirim, kaynak yayınlanacaksa çağrılması gereken tek bir yöntemi `Dispose`tanımlar.</span><span class="sxs-lookup"><span data-stu-id="89929-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="89929-169">, Yürütme `using` deyimin kapanış ayracına ulaştığında derleyici bu çağrıyı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89929-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="89929-170">Derleyici tarafından oluşturulan kod, using ifadesiyle tanımlanan bloktaki koddan bir özel durum oluşsa bile kaynağın serbest bırakılacağını sağlar.</span><span class="sxs-lookup"><span data-stu-id="89929-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="89929-171">`reader` değişkeni `var` anahtar sözcüğü kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="89929-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="89929-172">[`var`](../language-reference/keywords/var.md) *örtük olarak yazılmış bir yerel değişkeni*tanımlar.</span><span class="sxs-lookup"><span data-stu-id="89929-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="89929-173">Bu, değişkenin türü değişkene atanan nesnenin derleme zamanı türü tarafından belirlendiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="89929-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="89929-174">Burada, bir <xref:System.IO.StreamReader> nesnesi olan <xref:System.IO.File.OpenText(System.String)> yönteminin dönüş değeridir.</span><span class="sxs-lookup"><span data-stu-id="89929-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="89929-175">Şimdi de `Main` yönteminde dosyayı okumak için kodu dolduralım:</span><span class="sxs-lookup"><span data-stu-id="89929-175">Now, let's fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="89929-176">Programı çalıştırın (`dotnet run`kullanarak) ve konsolda yazdırılan her satırı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89929-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="89929-177">Gecikme ve biçimlendirme çıktısı ekleme</span><span class="sxs-lookup"><span data-stu-id="89929-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="89929-178">Ne kadar hızlı görüntülendikleriniz çok yüksek.</span><span class="sxs-lookup"><span data-stu-id="89929-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="89929-179">Şimdi çıktıdaki gecikmeleri eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89929-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="89929-180">Başladığınızda, zaman uyumsuz işleme sağlayan çekirdek koddan bazılarını oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="89929-180">As you start, you'll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="89929-181">Bununla birlikte, bu ilk adımlar birkaç tane kenar deseninden daha izlenecek.</span><span class="sxs-lookup"><span data-stu-id="89929-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="89929-182">Siz kodu eklerken yorumlara desenler görüntülenir ve kod sonraki adımlarda güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="89929-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="89929-183">Bu bölümde iki adım vardır.</span><span class="sxs-lookup"><span data-stu-id="89929-183">There are two steps to this section.</span></span> <span data-ttu-id="89929-184">İlk olarak, yineleyici yöntemini tüm satırlar yerine tek bir sözcük döndürecek şekilde güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="89929-184">First, you'll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="89929-185">Bu değişiklikler bu değişikliklerle yapılır.</span><span class="sxs-lookup"><span data-stu-id="89929-185">That's done with these modifications.</span></span> <span data-ttu-id="89929-186">`yield return line;` ifadesini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="89929-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="89929-187">Ardından, dosyanın satırlarını nasıl kullanacağınızı değiştirmeniz ve her bir kelime yazıldıktan sonra bir gecikme eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89929-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="89929-188">`Main` yöntemindeki `Console.WriteLine(line)` ifadesini aşağıdaki blokla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="89929-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

<span data-ttu-id="89929-189"><xref:System.Threading.Tasks.Task> sınıfı <xref:System.Threading.Tasks> ad alanında olduğundan, bu `using` ifadesini dosyanın en üstüne eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="89929-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="89929-190">Örneği çalıştırın ve çıktıyı denetleyin.</span><span class="sxs-lookup"><span data-stu-id="89929-190">Run the sample, and check the output.</span></span> <span data-ttu-id="89929-191">Şimdi, her bir sözcük yazdırılır ve ardından 200 ms gecikme gelir.</span><span class="sxs-lookup"><span data-stu-id="89929-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="89929-192">Ancak, görüntülenen çıktıda bazı sorunlar gösterilmektedir çünkü kaynak metin dosyasında satır sonu olmadan 80 ' ten fazla karakter içeren birkaç satır vardır.</span><span class="sxs-lookup"><span data-stu-id="89929-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="89929-193">Bu, kaydırma sırasında okunması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="89929-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="89929-194">Bu, düzeltilmesi kolay bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="89929-194">That's easy to fix.</span></span> <span data-ttu-id="89929-195">Her satırın uzunluğunu takip edersiniz ve satır uzunluğu belirli bir eşiğe ulaştığında yeni bir satır oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="89929-195">You'll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="89929-196">Satır uzunluğunu tutan `ReadFrom` yönteminde `words` bildiriminden sonra yerel bir değişken bildirin:</span><span class="sxs-lookup"><span data-stu-id="89929-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="89929-197">Sonra, `yield return word + " ";` deyiminden sonra aşağıdaki kodu ekleyin (kapatma küme ayracından önce):</span><span class="sxs-lookup"><span data-stu-id="89929-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="89929-198">Örneği çalıştırın, daha önceden yapılandırılmış hızda sesli okuyabileceksiniz.</span><span class="sxs-lookup"><span data-stu-id="89929-198">Run the sample, and you'll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="89929-199">Zaman uyumsuz görevler</span><span class="sxs-lookup"><span data-stu-id="89929-199">Async Tasks</span></span>

<span data-ttu-id="89929-200">Bu son adımda, çıktıyı zaman uyumsuz olarak bir görevde yazacak şekilde, Ayrıca metin görüntüsünü hızlandırmak veya yavaşlatacak şekilde Kullanıcı girişini okumak için başka bir görevi çalıştırırken, metin görüntülemeyi tamamen durdurmak için kodu ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="89929-200">In this final step, you'll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display, or stop the text display altogether.</span></span> <span data-ttu-id="89929-201">Bunun içinde ve sonunda birkaç adım vardır, ihtiyacınız olan tüm güncelleştirmelere sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="89929-201">This has a few steps in it and by the end, you'll have all the updates that you need.</span></span> <span data-ttu-id="89929-202">İlk adım, dosyayı okuyup görüntülemesi için oluşturduğunuz kodu temsil eden zaman uyumsuz <xref:System.Threading.Tasks.Task> döndüren bir yöntem oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="89929-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you've created so far to read and display the file.</span></span>

<span data-ttu-id="89929-203">Bu yöntemi `Program` sınıfa ekleyin (`Main` yönteminizin gövdesinden alınır):</span><span class="sxs-lookup"><span data-stu-id="89929-203">Add this method to your `Program` class (it's taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="89929-204">İki değişiklik fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="89929-204">You'll notice two changes.</span></span> <span data-ttu-id="89929-205">İlk olarak, yöntemin gövdesinde, bir görevin bitmesini zaman uyumlu olarak beklemek <xref:System.Threading.Tasks.Task.Wait> yerine, bu sürüm `await` anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="89929-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="89929-206">Bunu yapmak için yöntem imzasına `async` değiştiricisini eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89929-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="89929-207">Bu yöntem bir `Task`döndürür.</span><span class="sxs-lookup"><span data-stu-id="89929-207">This method returns a `Task`.</span></span> <span data-ttu-id="89929-208">`Task` nesnesi döndüren bir dönüş deyimi olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="89929-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="89929-209">Bunun yerine, `Task` nesnesi, `await` işlecini kullandığınızda derleyicinin oluşturduğu kodla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="89929-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="89929-210">Bu yöntemin, bir `await`ulaştığında döndürdüğünü düşünün.</span><span class="sxs-lookup"><span data-stu-id="89929-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="89929-211">Döndürülen `Task`, çalışmanın tamamlanmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89929-211">The returned `Task` indicates that the work has not completed.</span></span> <span data-ttu-id="89929-212">Yöntemi, beklenen görev tamamlandığında devam eder.</span><span class="sxs-lookup"><span data-stu-id="89929-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="89929-213">Tamamlanmayı yürütüldüğünde, döndürülen `Task` tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89929-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="89929-214">Çağıran kod, ne zaman tamamlandığını öğrenmek için döndürülen `Task` izleyebilir.</span><span class="sxs-lookup"><span data-stu-id="89929-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="89929-215">`Main` yönteminde bu yeni yöntemi çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="89929-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="89929-216">Burada `Main`, kod zaman uyumlu olarak bekler.</span><span class="sxs-lookup"><span data-stu-id="89929-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="89929-217">Mümkün olduğunca zaman uyumlu bekleme yerine `await` işlecini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="89929-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="89929-218">Ancak, bir konsol uygulamasının `Main` yönteminde `await` işlecini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="89929-218">But, in a console application's `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="89929-219">Bu, uygulamanın tüm görevler tamamlanmadan çıkılması ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="89929-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="89929-220">C# 7,1 veya sonraki bir sürümü kullanıyorsanız, [`async` `Main` yöntemiyle](../whats-new/csharp-7-1.md#async-main)konsol uygulamaları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89929-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="89929-221">Sonra, konsolundan okumak için ikinci zaman uyumsuz yöntemi yazmanız ve ' < ' (küçüktür), ' > ' (büyüktür) ve ' x ' veya ' x ' tuşlarından daha fazla bilgi almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="89929-221">Next, you need to write the second asynchronous method to read from the Console and watch for the '<' (less than), '>' (greater than) and 'X' or 'x' keys.</span></span> <span data-ttu-id="89929-222">Bu görev için eklediğiniz yöntem aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="89929-222">Here's the method you add for that task:</span></span>

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
            {
                break;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="89929-223">Bu, konsolundan bir anahtar okuyan bir <xref:System.Action> temsilcisini temsil eden bir lambda ifadesi oluşturur ve Kullanıcı ' < ' (küçüktür) veya ' > ' (büyüktür) tuşlarından sonra gelen gecikmeyi temsil eden yerel bir değişkeni değiştirir.</span><span class="sxs-lookup"><span data-stu-id="89929-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the '<' (less than) or '>' (greater than) keys.</span></span> <span data-ttu-id="89929-224">Temsilci yöntemi, Kullanıcı ' X ' veya ' x ' tuşlarına bastığında sona erdiğinde, kullanıcının metin görüntüsünü istediğiniz zaman durdurmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="89929-224">The delegate method finishes when user presses the 'X' or 'x'  keys, which allow the user to stop the text display at any time.</span></span> <span data-ttu-id="89929-225">Bu yöntem, engellemek için <xref:System.Console.ReadKey> kullanır ve kullanıcının bir tuşa basması için bekleyin.</span><span class="sxs-lookup"><span data-stu-id="89929-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="89929-226">Bu özelliği bitirebilmeniz için, bu görevlerin her ikisini de (`GetInput` ve `ShowTeleprompter`) Başlatan yeni bir `async Task` döndürme yöntemi oluşturmanız ve ayrıca bu iki görev arasındaki paylaşılan verileri de yönetmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="89929-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="89929-227">Bu iki görev arasında paylaşılan verileri işleyebilen bir sınıf oluşturmak zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="89929-227">It's time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="89929-228">Bu sınıf iki genel özellik içerir: gecikme ve bir bayrak, dosyanın tamamen okunduğunu göstermek için `Done`:</span><span class="sxs-lookup"><span data-stu-id="89929-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            DelayInMilliseconds = newDelay;
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

<span data-ttu-id="89929-229">Bu sınıfı yeni bir dosyaya yerleştirin ve bu sınıfı yukarıda gösterildiği gibi `TeleprompterConsole` ad alanına iliştirin.</span><span class="sxs-lookup"><span data-stu-id="89929-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="89929-230">Ayrıca, kapsayan sınıf veya ad alanı adları olmadan `Min` ve `Max` yöntemlerine başvurabilmeniz için `using static` bir ifade eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89929-230">You'll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="89929-231">[`using static`](../language-reference/keywords/using-static.md) bir ifade, bir sınıftan yöntemleri içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="89929-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="89929-232">Bu, bir ad alanından tüm sınıfları içeri aktarmış olan bu noktaya kadar kullanılan `using` deyimlerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="89929-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="89929-233">Sonra, yeni `config` nesnesini kullanmak için `ShowTeleprompter` ve `GetInput` yöntemlerini güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89929-233">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="89929-234">Her iki görevi başlatmak ve ilk görev tamamlandığında çıkış yapmak için `async` yöntemi döndüren bir son `Task` yazın:</span><span class="sxs-lookup"><span data-stu-id="89929-234">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="89929-235">Burada yeni bir yöntem <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="89929-235">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="89929-236">Bu, bağımsız değişken listesindeki görevlerden herhangi biri tamamlandıktan hemen sonra sona erbir `Task` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="89929-236">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="89929-237">Sonra, gecikme için `config` nesnesini kullanmak üzere hem `ShowTeleprompter` hem de `GetInput` yöntemlerini güncelleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="89929-237">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
                config.SetDone();
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="89929-238">`ShowTeleprompter` yeni sürümü `TeleprompterConfig` sınıfında yeni bir yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="89929-238">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="89929-239">Şimdi, `ShowTeleprompter`yerine `RunTeleprompter` çağırmak için `Main` güncelleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="89929-239">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="89929-240">Sonuç</span><span class="sxs-lookup"><span data-stu-id="89929-240">Conclusion</span></span>

<span data-ttu-id="89929-241">Bu öğreticide, C# dil etrafındaki ve konsol uygulamalarında çalışmaya yönelik .NET Core kitaplıklarının çeşitli özellikleri gösterildi.</span><span class="sxs-lookup"><span data-stu-id="89929-241">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span> <span data-ttu-id="89929-242">Bu bilgiyi, dil ve burada tanıtılan sınıflar hakkında daha fazla bilgi için oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89929-242">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="89929-243">Dosya ve konsol g/ç ile ilgili temel bilgileri, görev tabanlı zaman uyumsuz programlamayı engellemeyi ve engellenmemiş kullanımı, C# dilin bir turu ve programların nasıl C# düzenlendiğini ve .NET Core CLI olduğunu gördünüz.</span><span class="sxs-lookup"><span data-stu-id="89929-243">You've seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized, and the .NET Core CLI.</span></span>

<span data-ttu-id="89929-244">Dosya g/ç hakkında daha fazla bilgi için bkz. [dosya ve akış g/ç](../../standard/io/index.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="89929-244">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="89929-245">Bu öğreticide kullanılan zaman uyumsuz programlama modeli hakkında daha fazla bilgi için [görev tabanlı zaman uyumsuz programlama](../..//standard/parallel-programming/task-based-asynchronous-programming.md) konusuna ve [zaman uyumsuz programlama](../async.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="89929-245">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
