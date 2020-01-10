---
title: DotNet test ve NUnit ile .NET Core 'da birim testi Visual Basic
description: .NET Core 'daki birim testi kavramlarını, NUnit kullanarak örnek Visual Basic çözüm oluşturma adlı etkileşimli bir deneyim aracılığıyla öğrenin.
author: rprouse
ms.date: 10/04/2018
ms.openlocfilehash: 8f05d25a0add76f5c552f5b9ac1eb310c3d6407a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715402"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a>DotNet test ve NUnit kullanarak .NET Core kitaplıkları Visual Basic birim testi

Bu öğreticide, birim testi kavramlarını öğrenmek için bir örnek çözüm oluşturma adım adım yönergeler sunarak etkileşimli bir deneyim sağlanır. Önceden oluşturulmuş bir çözüm kullanarak öğreticiyi izlemeyi tercih ediyorsanız, başlamadan önce [örnek kodu görüntüleyin veya indirin](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) . İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Prerequisites

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri.
- Tercih ettiğiniz bir metin veya kod düzenleyicisi.

## <a name="creating-the-source-project"></a>Kaynak proje oluşturma

Bir kabuk penceresi açın. Çözümü tutmak için *birim-test-vb-NUnit* adlı bir dizin oluşturun. Bu yeni dizin içinde, sınıf kitaplığı ve test projesi için yeni bir çözüm dosyası oluşturmak üzere aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet new sln
```

Ardından, bir *Primeservice* dizini oluşturun. Aşağıdaki ana hat şu ana kadar dosya yapısını gösterir:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

Kaynak projeyi oluşturmak için *Primeservice* 'i geçerli dizin yapın ve şu komutu çalıştırın:

```dotnetcli
dotnet new classlib -lang VB
```

*Class1. vb* ' i *primeservice. vb*olarak yeniden adlandırın. `PrimeService` sınıfının başarısız bir uygulamasını oluşturursunuz:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

Dizini *birim-test-vb-using-MSTest* dizinine geri çevirin. Çözüme Sınıf Kitaplığı projesini eklemek için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a>Test projesi oluşturma

Ardından, *Primeservice. Tests* dizinini oluşturun. Aşağıdaki ana hat dizin yapısını gösterir:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

*Primeservice. test* dizinini geçerli dizini yapın ve aşağıdaki komutu kullanarak yeni bir proje oluşturun:

```dotnetcli
dotnet new nunit -lang VB
```

[DotNet New](../tools/dotnet-new.md) komutu, test kitaplığı olarak NUnit kullanan bir test projesi oluşturur. Oluşturulan şablon, *Primeservicetests. vbproj* dosyasında Test Çalıştırıcısı 'nı yapılandırır:

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

Test projesi, birim testlerini oluşturmak ve çalıştırmak için diğer paketlerin kullanılmasını gerektirir. önceki adımda `dotnet new` NUnit ve NUnit test bağdaştırıcısı eklenmiştir. Şimdi, `PrimeService` sınıf kitaplığını projeye başka bir bağımlılık olarak ekleyin. [`dotnet add reference`](../tools/dotnet-add-reference.md) komutunu kullanın:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

GitHub 'daki [örnekler deposunda](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) dosyanın tamamını görebilirsiniz.

Aşağıdaki son çözüm düzenine sahipsiniz:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

*Birim-test-vb-NUnit* dizininde aşağıdaki komutu yürütün:

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a>İlk test oluşturma

Başarısız bir test yazdığınızda, geçişi yapıp işlemi tekrarlayabilirsiniz. *Primeservice. Tests* dizininde, *UnitTest1. vb* dosyasını *PrimeService_IsPrimeShould. vb* olarak yeniden adlandırın ve tüm içeriğini aşağıdaki kodla değiştirin:

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`<TestFixture>` özniteliği, testleri içeren bir sınıfı gösterir. `<Test>` özniteliği, Test Çalıştırıcısı tarafından çalıştırılan bir yöntemi gösterir. *Birim-test-vb-NUnit*' den testleri ve sınıf kitaplığını oluşturmak için [`dotnet test`](../tools/dotnet-test.md) yürütün ve ardından testleri çalıştırın. NUnit Test Çalıştırıcısı, testlerinizi çalıştırmak için program giriş noktasını içerir. `dotnet test`, oluşturduğunuz birim test projesini kullanarak Test Çalıştırıcısı başlatır.

Testiniz başarısız oluyor. Uygulamayı henüz oluşturmadınız. Aşağıdaki `PrimeService` sınıfında en basit kodu yazarak bu test geçişini yapın:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

*Birim-test-vb-NUnit* dizininde `dotnet test` yeniden çalıştırın. `dotnet test` komutu, `PrimeService` projesi için bir derleme ve sonra `PrimeService.Tests` projesi için çalışır. Her iki proje de oluşturulduktan sonra bu tek testi çalıştırır. Geçirir.

## <a name="adding-more-features"></a>Daha fazla özellik ekleme

Artık bir test geçişi yapmış olduğunuza göre daha fazla yazma zamanı vardır. Asal sayıların diğer birkaç basit durumu vardır: 0,-1. Bu servis taleplerini `<Test>` özniteliğiyle yeni testler olarak ekleyebilirsiniz, ancak bu hızlı bir şekilde sıkıcı olur. Benzer testlerin bir paketini yazmanızı sağlayan başka xUnit öznitelikleri vardır.  Bir `<TestCase>` özniteliği, aynı kodu çalıştıran ancak farklı giriş bağımsız değişkenlerine sahip olan bir test paketini temsil eder. Bu girişlerin değerlerini belirtmek için `<TestCase>` özniteliğini kullanabilirsiniz.

Yeni testler oluşturmak yerine, bu iki özniteliği, en düşük asal sayı olan iki değerden küçük olan birkaç değeri test eden bir dizi testi oluşturacak şekilde uygulayın:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

`dotnet test`çalıştırın, bu testlerin ikisi de başarısız olur. Tüm testlerin geçişini yapmak için *PrimeServices.cs* dosyasındaki `Main` yönteminin başındaki `if` yan tümcesini değiştirin:

```vb
if candidate < 2
```

Ana kitaplıkta daha fazla test, daha fazla yer ve daha fazla kod ekleyerek yinelemek için devam edin. [Testlerin tamamlanmış sürümüne](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) ve [kitaplığın tüm uygulamasına](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb)sahipsiniz.

Bu kitaplık için küçük bir kitaplık ve birim testleri kümesi oluşturdunuz. Çözümü, yeni paket ve test eklemek normal iş akışının bir parçası olacak şekilde öğrendiniz. Uygulamanın hedeflerini çözme konusunda zaman ve çaba harcamanızı en iyi şekilde gördünüz.
