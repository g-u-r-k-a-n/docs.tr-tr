---
title: DotNet test ve xUnit kullanarak .NET Core 'da birim testi C# kodu
description: C# ve .NET Core 'da birim testi kavramlarını, DotNet test ve xUnit kullanarak örnek çözüm oluşturma adlı etkileşimli bir deneyim aracılığıyla öğrenin.
author: ardalis
ms.author: wiwagn
ms.date: 10/21/2020
ms.openlocfilehash: e1972858be00e8a884efbd66b618ddb9ab77e9ba
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471543"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a><span data-ttu-id="cd59a-103">DotNet test ve xUnit kullanarak .NET Core 'Da birim testi C#</span><span class="sxs-lookup"><span data-stu-id="cd59a-103">Unit testing C# in .NET Core using dotnet test and xUnit</span></span>

<span data-ttu-id="cd59a-104">Bu öğreticide, birim testi projesi ve kaynak kodu projesi içeren bir çözüm oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cd59a-104">This tutorial shows how to build a solution containing a unit test project and source code project.</span></span> <span data-ttu-id="cd59a-105">Önceden oluşturulmuş bir çözümü kullanarak öğreticiyi izlemek için [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span><span class="sxs-lookup"><span data-stu-id="cd59a-105">To follow the tutorial using a pre-built solution, [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/).</span></span> <span data-ttu-id="cd59a-106">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="cd59a-106">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="cd59a-107">Çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd59a-107">Create the solution</span></span>

<span data-ttu-id="cd59a-108">Bu bölümde, kaynak ve test projelerini içeren bir çözüm oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cd59a-108">In this section, a solution is created that contains the source and test projects.</span></span> <span data-ttu-id="cd59a-109">Tamamlanmış çözüm aşağıdaki dizin yapısına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cd59a-109">The completed solution has the following directory structure:</span></span>

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
```

<span data-ttu-id="cd59a-110">Aşağıdaki yönergeler, test çözümünü oluşturmak için gereken adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd59a-110">The following instructions provide the steps to create the test solution.</span></span> <span data-ttu-id="cd59a-111">Test çözümünü tek bir adımda oluşturmaya yönelik yönergeler için bkz. [Test çözümü oluşturma komutları](#create-test-cmd) .</span><span class="sxs-lookup"><span data-stu-id="cd59a-111">See [Commands to create test solution](#create-test-cmd) for instructions to create the test solution in one step.</span></span>

* <span data-ttu-id="cd59a-112">Bir kabuk penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="cd59a-112">Open a shell window.</span></span>
* <span data-ttu-id="cd59a-113">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="cd59a-113">Run the following command:</span></span>

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  <span data-ttu-id="cd59a-114">Bu [`dotnet new sln`](../tools/dotnet-new.md) komut, *birim-test-using-DotNet-test* dizininde yeni bir çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd59a-114">The [`dotnet new sln`](../tools/dotnet-new.md) command creates a new solution in the *unit-testing-using-dotnet-test* directory.</span></span>
* <span data-ttu-id="cd59a-115">Dizini *birim-test-using-DotNet-test* klasörü ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cd59a-115">Change directory to the *unit-testing-using-dotnet-test* folder.</span></span>
* <span data-ttu-id="cd59a-116">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="cd59a-116">Run the following command:</span></span>

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   <span data-ttu-id="cd59a-117">[`dotnet new classlib`](../tools/dotnet-new.md)Komut, *Primeservice* klasöründe yeni bir sınıf kitaplığı projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd59a-117">The [`dotnet new classlib`](../tools/dotnet-new.md) command creates a new class library project  in the *PrimeService* folder.</span></span> <span data-ttu-id="cd59a-118">Yeni sınıf kitaplığı sınanacak kodu içerecektir.</span><span class="sxs-lookup"><span data-stu-id="cd59a-118">The new class library will contain the code to be tested.</span></span>
* <span data-ttu-id="cd59a-119">*Class1.cs* *olarak yeniden*adlandırın.</span><span class="sxs-lookup"><span data-stu-id="cd59a-119">Rename *Class1.cs* to *PrimeService.cs*.</span></span>
* <span data-ttu-id="cd59a-120">*PrimeService.cs* içindeki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cd59a-120">Replace the code in *PrimeService.cs* with the following code:</span></span>
  
  ```csharp
  using System;

  namespace Prime.Services
  {
      public class PrimeService
      {
          public bool IsPrime(int candidate)
          {
              throw new NotImplementedException("Not implemented.");
          }
      }
  }
  ```

* <span data-ttu-id="cd59a-121">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="cd59a-121">The preceding code:</span></span>
  * <span data-ttu-id="cd59a-122"><xref:System.NotImplementedException>Uygulanmadığını belirten bir ileti içeren bir iletisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd59a-122">Throws a <xref:System.NotImplementedException> with a message indicating it's not implemented.</span></span>
  * <span data-ttu-id="cd59a-123">, Öğreticide daha sonra güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cd59a-123">Is updated later in the tutorial.</span></span>

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* <span data-ttu-id="cd59a-124">*Birim-test-using-DotNet-test* dizini ' nde, sınıf kitaplığı projesini çözüme eklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="cd59a-124">In the *unit-testing-using-dotnet-test* directory, run the following command to add the class library project to the solution:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* <span data-ttu-id="cd59a-125">Aşağıdaki komutu çalıştırarak *Primeservice. Tests* projesini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="cd59a-125">Create the *PrimeService.Tests* project by running the following command:</span></span>

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* <span data-ttu-id="cd59a-126">Yukarıdaki komut:</span><span class="sxs-lookup"><span data-stu-id="cd59a-126">The preceding command:</span></span>
  * <span data-ttu-id="cd59a-127">*Primeservice* . *Tests projesindeki primeservice. Tests* projesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd59a-127">Creates the *PrimeService.Tests* project in the *PrimeService.Tests* directory.</span></span> <span data-ttu-id="cd59a-128">Test projesi, test kitaplığı olarak [xUnit](https://xunit.net/) kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd59a-128">The test project uses [xUnit](https://xunit.net/) as the test library.</span></span>
  * <span data-ttu-id="cd59a-129">, Aşağıdaki öğeleri proje dosyasına ekleyerek Test Çalıştırıcısı 'nı yapılandırır `<PackageReference />` :</span><span class="sxs-lookup"><span data-stu-id="cd59a-129">Configures the test runner by adding the following `<PackageReference />`elements to the project file:</span></span>
    * <span data-ttu-id="cd59a-130">"Microsoft. NET. test. SDK"</span><span class="sxs-lookup"><span data-stu-id="cd59a-130">"Microsoft.NET.Test.Sdk"</span></span>
    * <span data-ttu-id="cd59a-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="cd59a-131">"xunit"</span></span>
    * <span data-ttu-id="cd59a-132">"xUnit. Runner. VisualStudio"</span><span class="sxs-lookup"><span data-stu-id="cd59a-132">"xunit.runner.visualstudio"</span></span>

* <span data-ttu-id="cd59a-133">Aşağıdaki komutu çalıştırarak test projesini çözüm dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cd59a-133">Add the test project to the solution file by running the following command:</span></span>

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* <span data-ttu-id="cd59a-134">`PrimeService`Sınıf kitaplığını, *Primeservice. Tests* projesine bağımlılık olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cd59a-134">Add the `PrimeService` class library as a dependency to the *PrimeService.Tests* project:</span></span>

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a><span data-ttu-id="cd59a-135">Çözüm oluşturma komutları</span><span class="sxs-lookup"><span data-stu-id="cd59a-135">Commands to create the solution</span></span>

<span data-ttu-id="cd59a-136">Bu bölüm, önceki bölümdeki tüm komutları özetler.</span><span class="sxs-lookup"><span data-stu-id="cd59a-136">This section summarizes all the commands in the previous section.</span></span> <span data-ttu-id="cd59a-137">Önceki bölümdeki adımları tamamladığınız takdirde bu bölümü atlayın.</span><span class="sxs-lookup"><span data-stu-id="cd59a-137">Skip this section if you've completed the steps in the previous section.</span></span>

<span data-ttu-id="cd59a-138">Aşağıdaki komutlar, bir Windows makinesinde test çözümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cd59a-138">The following commands create the test solution on a windows machine.</span></span> <span data-ttu-id="cd59a-139">MacOS ve UNIX için, `ren` komutunu `ren` bir dosyayı yeniden adlandırmak üzere işletim sistemi sürümüne güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="cd59a-139">For macOS and Unix, update the `ren` command to the OS version of `ren` to rename a file:</span></span>

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

<span data-ttu-id="cd59a-140">Önceki bölümde " *PrimeService.cs* içindeki kodu aşağıdaki kodla değiştirin" yönergelerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="cd59a-140">Follow the instructions for "Replace the code in *PrimeService.cs* with the following code" in the previous section.</span></span>

## <a name="create-a-test"></a><span data-ttu-id="cd59a-141">Test oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd59a-141">Create a test</span></span>

<span data-ttu-id="cd59a-142">Test odaklı geliştirme (TDD) içinde popüler bir yaklaşım, hedef kodu uygulamadan önce bir test yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="cd59a-142">A popular approach in test driven development (TDD) is to write a test before implementing the target code.</span></span> <span data-ttu-id="cd59a-143">Bu öğretici, TDD yaklaşımını kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd59a-143">This tutorial uses the TDD approach.</span></span> <span data-ttu-id="cd59a-144">`IsPrime`Yöntem çağrılabilir, ancak uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="cd59a-144">The `IsPrime` method is callable, but not implemented.</span></span> <span data-ttu-id="cd59a-145">Test çağrısı `IsPrime` başarısız.</span><span class="sxs-lookup"><span data-stu-id="cd59a-145">A test call to `IsPrime` fails.</span></span> <span data-ttu-id="cd59a-146">TDD ile başarısız olarak bilinen bir test yazılır.</span><span class="sxs-lookup"><span data-stu-id="cd59a-146">With TDD, a test is written that is known to fail.</span></span> <span data-ttu-id="cd59a-147">Hedef kodu test geçişini yapmak için güncellenir.</span><span class="sxs-lookup"><span data-stu-id="cd59a-147">The target code is updated to make the test pass.</span></span> <span data-ttu-id="cd59a-148">Bu yaklaşımı tekrarlayarak, başarısız bir test yazarak ve ardından hedef kodu geçirilecek şekilde güncelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cd59a-148">You keep repeating this approach, writing a failing test and then updating the target code to pass.</span></span>

<span data-ttu-id="cd59a-149">*Primeservice. Tests* projesini güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="cd59a-149">Update the *PrimeService.Tests* project:</span></span>

* <span data-ttu-id="cd59a-150">*Primeservice. Tests/UnitTest1. cs*öğesini silin.</span><span class="sxs-lookup"><span data-stu-id="cd59a-150">Delete *PrimeService.Tests/UnitTest1.cs*.</span></span>
* <span data-ttu-id="cd59a-151">Bir *Primeservice. Tests/PrimeService_IsPrimeShould. cs*  dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cd59a-151">Create a *PrimeService.Tests/PrimeService_IsPrimeShould.cs*  file.</span></span>
* <span data-ttu-id="cd59a-152">*PrimeService_IsPrimeShould. cs* içindeki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cd59a-152">Replace the code in *PrimeService_IsPrimeShould.cs* with the following code:</span></span>

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var primeService = new PrimeService();
            bool result = primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

<span data-ttu-id="cd59a-153">`[Fact]`Özniteliği, Test Çalıştırıcısı tarafından çalıştırılan bir test yöntemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="cd59a-153">The `[Fact]` attribute declares a test method that's run by the test runner.</span></span> <span data-ttu-id="cd59a-154">*Primeservice. Tests* klasöründen çalıştırın `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="cd59a-154">From the *PrimeService.Tests* folder, run `dotnet test`.</span></span> <span data-ttu-id="cd59a-155">[DotNet test](../tools/dotnet-test.md) komutu her iki projeyi de oluşturur ve testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="cd59a-155">The [dotnet test](../tools/dotnet-test.md) command builds both projects and runs the tests.</span></span> <span data-ttu-id="cd59a-156">XUnit Test Çalıştırıcısı, testleri çalıştırmak için program giriş noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="cd59a-156">The xUnit test runner contains the program entry point to run the tests.</span></span> <span data-ttu-id="cd59a-157">`dotnet test` birim test projesini kullanarak Test Çalıştırıcısı başlatır.</span><span class="sxs-lookup"><span data-stu-id="cd59a-157">`dotnet test` starts the test runner using the unit test project.</span></span>

<span data-ttu-id="cd59a-158">Test başarısız oldu, çünkü `IsPrime` uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="cd59a-158">The test fails because `IsPrime` hasn't been implemented.</span></span> <span data-ttu-id="cd59a-159">TDD yaklaşımını kullanarak, bu testin başarılı olması için yalnızca yeterli kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="cd59a-159">Using the TDD approach, write only enough code so this test passes.</span></span> <span data-ttu-id="cd59a-160">`IsPrime`Aşağıdaki kodla güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="cd59a-160">Update `IsPrime` with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

<span data-ttu-id="cd59a-161">Şu komutu çalıştırın: `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="cd59a-161">Run `dotnet test`.</span></span> <span data-ttu-id="cd59a-162">Test geçirilir.</span><span class="sxs-lookup"><span data-stu-id="cd59a-162">The test passes.</span></span>

### <a name="add-more-tests"></a><span data-ttu-id="cd59a-163">Daha fazla test ekleyin</span><span class="sxs-lookup"><span data-stu-id="cd59a-163">Add more tests</span></span>

<span data-ttu-id="cd59a-164">0 ve-1 için asal sayı testleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cd59a-164">Add prime number tests for 0 and -1.</span></span> <span data-ttu-id="cd59a-165">Önceki testi kopyalayabilir ve aşağıdaki kodu 0 ve-1 kullanacak şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cd59a-165">You could copy the preceding test and change the following code to use 0 and -1:</span></span>

```csharp
var primeService = new PrimeService();
bool result = primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

<span data-ttu-id="cd59a-166">Yalnızca bir parametre değiştiğinde test kodu kopyalama, kod yineleme ve test blobunun sonuçlarını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="cd59a-166">Copying test code when only a parameter changes results in code duplication and test bloat.</span></span> <span data-ttu-id="cd59a-167">Aşağıdaki xUnit öznitelikleri benzer testlerin bir paketini yazmayı etkinleştirir:</span><span class="sxs-lookup"><span data-stu-id="cd59a-167">The following xUnit attributes enable writing a suite of similar tests:</span></span>

- <span data-ttu-id="cd59a-168">`[Theory]` aynı kodu çalıştıran, ancak farklı giriş bağımsız değişkenlerine sahip olan testlerin paketini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cd59a-168">`[Theory]` represents a suite of tests that execute the same code but have different input arguments.</span></span>
- <span data-ttu-id="cd59a-169">`[InlineData]` öznitelik, bu girişlerin değerlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cd59a-169">`[InlineData]` attribute specifies values for those inputs.</span></span>

<span data-ttu-id="cd59a-170">Yeni test oluşturmak yerine, tek bir teorisi oluşturmak için önceki xUnit özniteliklerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="cd59a-170">Rather than creating new tests, apply the preceding xUnit attributes to create a single theory.</span></span> <span data-ttu-id="cd59a-171">Aşağıdaki kodu değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cd59a-171">Replace the following code:</span></span>

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var primeService = new PrimeService();
    bool result = primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

<span data-ttu-id="cd59a-172">aşağıdaki kodla:</span><span class="sxs-lookup"><span data-stu-id="cd59a-172">with the following code:</span></span>

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

<span data-ttu-id="cd59a-173">Önceki kodda, `[Theory]` `[InlineData]` ikiden küçük olan birkaç değeri test etmeyi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="cd59a-173">In the preceding code, `[Theory]` and `[InlineData]` enable testing several values less than two.</span></span> <span data-ttu-id="cd59a-174">İki, en küçük asal sayıdır.</span><span class="sxs-lookup"><span data-stu-id="cd59a-174">Two is the smallest prime number.</span></span>

<span data-ttu-id="cd59a-175">Çalıştırılan `dotnet test` testlerin ikisi de başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="cd59a-175">Run `dotnet test`, two of the tests fail.</span></span> <span data-ttu-id="cd59a-176">Tüm testlerin geçişini yapmak için `IsPrime` yöntemini aşağıdaki kodla güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="cd59a-176">To make all of the tests pass, update the `IsPrime` method with the following code:</span></span>

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

<span data-ttu-id="cd59a-177">TDD yaklaşımını izleyerek, daha fazla başarısız test ekleyin ve ardından hedef kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="cd59a-177">Following the TDD approach, add more failing tests, then update the target code.</span></span> <span data-ttu-id="cd59a-178">[Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs)bakın.</span><span class="sxs-lookup"><span data-stu-id="cd59a-178">See the [finished version of the tests](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) and the [complete implementation of the library](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).</span></span>

<span data-ttu-id="cd59a-179">Tamamlanan `IsPrime` Yöntem, test açısından etkili bir algoritma değildir.</span><span class="sxs-lookup"><span data-stu-id="cd59a-179">The completed `IsPrime` method is not an efficient algorithm for testing primality.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="cd59a-180">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="cd59a-180">Additional resources</span></span>

- [<span data-ttu-id="cd59a-181">xUnit.net resmi site</span><span class="sxs-lookup"><span data-stu-id="cd59a-181">xUnit.net official site</span></span>](https://xunit.net)
- [<span data-ttu-id="cd59a-182">ASP.NET Core 'de test denetleyicisi mantığı</span><span class="sxs-lookup"><span data-stu-id="cd59a-182">Testing controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
