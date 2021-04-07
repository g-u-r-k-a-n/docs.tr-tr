---
title: .NET tanıtımı ve genel bakış
description: Birçok tür uygulama oluşturmaya yönelik ücretsiz, açık kaynaklı bir geliştirme platformu olan .NET hakkında bilgi edinin.
author: tdykstra
ms.date: 11/16/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 7aa84abdf4653960503699ea7cb239279d748c4e
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496702"
---
# <a name="introduction-to-net"></a>.NET’e giriş

.NET, şu gibi birçok tür uygulama oluşturmaya yönelik ücretsiz, açık kaynaklı bir geliştirme platformudur:

* [Web Apps, Web API 'Leri ve mikro hizmetler](/aspnet/core/introduction-to-aspnet-core#recommended-learning-path)
* [Bulutta sunucusuz işlevler](/azure/azure-functions/functions-create-first-function-vs-code?pivots=programming-language-csharp)
* [Bulutta yerel uygulamalar](../architecture/cloud-native/index.md)
* [Mobil uygulamalar](https://dotnet.microsoft.com/learn/xamarin/hello-world-tutorial/intro)
* Masaüstü uygulamaları
  * [Windows WPF](/dotnet/desktop/wpf/)
  * [Windows Forms](/dotnet/desktop/winforms/)
  * [Evrensel Windows Platformu (UWP)](/windows/uwp/get-started/create-a-hello-world-app-xaml-universal)
* [Oyunlar](https://dotnet.microsoft.com/apps/games)
* [Nesnelerin İnterneti (IoT)](../iot/index.yml)
* [Makine öğrenmesi](../machine-learning/index.yml)
* [Konsol uygulamaları](tutorials/with-visual-studio-code.md)
* [Windows Hizmetleri](/aspnet/core/host-and-deploy/windows-service)

[Sınıf kitaplıklarını](../standard/class-libraries.md)kullanarak farklı uygulamalar ve uygulama türleri arasında işlevsellik paylaşabilirsiniz.

.NET ile kodunuz ve proje dosyalarınız, hangi tür bir uygulama oluşturmakta olduğunuzla aynı şekilde görünür. Her uygulamayla aynı çalışma zamanına, API 'ye ve dil özelliklerine erişebilirsiniz.

## <a name="cross-platform"></a>Platformlar arası

Birçok işletim sistemi için aşağıdakiler de dahil olmak üzere .NET uygulamaları oluşturabilirsiniz:

* Windows
* Mac OS
* Linux
* Android
* iOS
* tvOS
* watchOS

Desteklenen İşlemci mimarileri şunları içerir:

* x64
* x86
* ARM32
* ARM64

.NET, işletim sistemi API 'Leri gibi platforma özgü özellikleri kullanmanıza olanak sağlar. Örnekler, Windows üzerinde Windows Forms ve WPF ve Xamarin 'ten her mobil platforma yönelik yerel bağlamalardır.

Daha fazla bilgi için bkz. [desteklenen işletim sistemi yaşam döngüsü ilkesi](https://github.com/dotnet/core/blob/main/os-lifecycle-policy.md) ve [.net RID kataloğu](rid-catalog.md).

## <a name="open-source"></a>Açık kaynak

.NET, [MIT ve Apache 2 lisanslarını](https://github.com/dotnet/runtime/blob/main/LICENSE.TXT)kullanarak açık kaynaktır. .NET, [.net Foundation](https://dotnetfoundation.org/)'ın bir projem.

Daha fazla bilgi için GitHub.com adresindeki [Proje depoları listesine](https://github.com/dotnet/core/blob/main/Documentation/core-repos.md)bakın.

## <a name="support"></a>Destek

.NET, Windows, macOS ve Linux 'ta Microsoft tarafından desteklenir. Her ayın ikinci Salı günü, güvenlik ve kalite açısından düzenli olarak güncelleştirilir.

Microsoft 'un .NET ikili dağıtımları, Azure 'da Microsoft tarafından korunan sunucularda oluşturulup test edilir ve Microsoft mühendislik ve güvenlik uygulamalarını izler.

[Red Hat](https://developers.redhat.com/topics/dotnet/) Red Hat Enterprise Linux (RHEL) üzerinde .net destekler. Red Hat ve Microsoft, .NET Core 'un RHEL üzerinde iyi çalıştığından emin olmak için işbirliği sağlar.

Tizen, Tizen platformlarında [.net destekler](https://developer.tizen.org/development/training/.net-application) .

Daha fazla bilgi için bkz. [.NET Core ve .NET 5 Için yayınlar ve destek](releases-and-support.md).

## <a name="tools-and-productivity"></a>Araçlar ve üretkenlik

.NET size diller, tümleşik geliştirme ortamları (IDEs) ve diğer araçlar sunar.

### <a name="programming-languages"></a>Programlama dilleri

.NET üç programlama dilini destekler:

* [C#](../csharp/index.yml)

  C# ("bkz. diyez") modern, nesne odaklı ve tür açısından güvenli bir programlama dilidir. C#, C ailesinin köklerine sahiptir ve C, C++, Java ve JavaScript programcıları için hemen tanıdık gelecektir.

* [F#](../fsharp/index.yml)

  F # dili işlevsel, nesne yönelimli ve kesinlik temelli programlama modellerini destekler.

* [Visual Basic](../visual-basic/index.yml)

  .NET dilleri arasında Visual Basic sözdizimi, normal insan diline en yakın bir deyişle, daha kolay bilgi edinebilirsiniz. Microsoft 'un yeni özellikler geliştirmekte olduğu C# ve F # ' dan farklı olarak Visual Basic dili kararlı olur. Visual Basic Web Apps için desteklenmez, ancak Web API 'Leri için desteklenir.

.NET dillerinin desteklediği bazı yetenekler şunlardır:

* [Tür güvenliği](../standard/base-types/common-type-system.md)
* Tür çıkarımı- [C#](../csharp/programming-guide/types/index.md#specifying-types-in-variable-declarations), [F #](../fsharp/language-reference/type-inference.md), [Visual Basic](../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
* [Genel türler](../standard/generics.md)
* [Temsilciler](../standard/delegates-lambdas.md)
* [Lambdalar](../standard/delegates-lambdas.md)
* [Ekinlikler](../standard/events/index.md)
* [Özel durumlar](../standard/exceptions/index.md)
* [Öznitelikler](../standard/attributes/index.md)
* [Zaman uyumsuz kod](../standard/async.md)
* [Paralel programlama](../standard/parallel-programming/index.md)
* [Kod çözümleyicileri](../fundamentals/code-analysis/overview.md)

### <a name="ides"></a>IDE

.NET için tümleşik geliştirme ortamları şunları içerir:

* [Visual Studio](https://visualstudio.microsoft.com/vs/)

  Yalnızca Windows üzerinde çalışır. , .NET ile çalışmak için tasarlanan kapsamlı yerleşik işlevlere sahiptir. Topluluk sürümü, öğrenciler, açık kaynak katkı sağlayanlar ve bireyler için ücretsizdir.

* [Visual Studio Code](https://code.visualstudio.com/)

  Windows, macOS ve Linux üzerinde çalışır. Ücretsiz ve açık kaynak. Uzantılar .NET dilleri ile birlikte çalışmak için kullanılabilir.

* [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/)

  Yalnızca macOS 'ta çalışır. İOS, Android ve Web için .NET uygulamaları ve oyunları geliştirme.

* [GitHub Codespaces](https://github.com/features/codespaces)

  Şu anda beta sürümünde olan çevrimiçi bir Visual Studio Code ortamı.

### <a name="sdk-and-runtimes"></a>SDK ve çalışma zamanları

[.NET SDK](sdk.md) , .NET uygulamaları geliştirmeye ve çalıştırmaya yönelik kitaplıkların ve araçların bir kümesidir.

.NET 'i [indirdiğinizde](https://dotnet.microsoft.com/download/dotnet), SDK 'yı veya .NET çalışma zamanı veya ASP.NET Core çalışma zamanı gibi bir *çalışma zamanını* seçebilirsiniz. .NET uygulamalarını çalıştırmaya hazırlamak istediğiniz bir makineye çalışma zamanı yükler. Geliştirme için kullanmak istediğiniz bir makineye SDK 'Yı yükler. SDK 'Yı indirdiğinizde, çalışma zamanlarını otomatik olarak alırsınız.

SDK indirmesi aşağıdaki bileşenleri içerir:

* [.Net CLI](tools/index.md). Yerel geliştirme ve sürekli tümleştirme betikleri için kullanabileceğiniz komut satırı araçları.
* `dotnet` [Sürücü](tools/index.md#driver). Çerçeveye bağımlı uygulamalar çalıştıran bir CLı komutu.
* [Roslyn](https://github.com/dotnet/roslyn) ve [F #](https://github.com/microsoft/visualfsharp) programlama dili derleyicileri.
* [MSBuild](/visualstudio/msbuild/msbuild) derleme altyapısı.
* [.NET çalışma zamanı](#clr). Bir tür sistemi, derleme yükleme, çöp toplayıcı, yerel birlikte çalışma ve diğer temel hizmetleri sağlar.
* [Çalışma zamanı kitaplıkları](#runtime-libraries). Temel veri türleri ve temel yardımcı programlar sağlar.
* ASP.NET Core çalışma zamanı. Web uygulamaları, IoT uygulamaları ve mobil arka uçlar gibi Internet 'e bağlı uygulamalar için temel hizmetler sağlar.
* Masaüstü çalışma zamanı. Windows Forms ve WPF dahil olmak üzere Windows Masaüstü uygulamaları için temel hizmetler sağlar.

Çalışma zamanı indirmesi aşağıdaki bileşenleri içerir:

* İsteğe bağlı olarak, masaüstü veya ASP.NET Core çalışma zamanı.
* [.NET çalışma zamanı](#clr). Bir tür sistemi, derleme yükleme, çöp toplayıcı, yerel birlikte çalışma ve diğer temel hizmetleri sağlar.
* [Çalışma zamanı kitaplıkları](#runtime-libraries). Temel veri türleri ve temel yardımcı programlar sağlar.
* `dotnet` [Sürücü](tools/index.md#driver). Çerçeveye bağımlı uygulamalar çalıştıran bir CLı komutu.

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

* [.NET SDK genel bakış](sdk.md)
* [.NET CLı genel bakış](tools/index.md)
* [DotNet komutu](tools/dotnet.md)

### <a name="project-system-and-msbuild"></a>Proje sistemi ve MSBuild

Bir .NET uygulaması, [MSBuild](/visualstudio/msbuild/msbuild)kullanılarak kaynak koddan oluşturulur. Proje dosyası (*. csproj*, *. fsproj* veya *. vbproj*), Kodu derleyip yayımlamadan sorumlu [hedefleri](/visualstudio/msbuild/msbuild-targets) ve ilişkili [görevleri](/visualstudio/msbuild/msbuild-tasks) belirtir. Standart hedef ve görev koleksiyonlarına başvuran SDK tanımlayıcıları vardır. Bu tanımlayıcıların kullanımı, proje dosyalarını küçük ve ile birlikte çalışmaya devam etmenize yardımcı olur. Örneğin, bir konsol uygulaması için bir proje dosyası aşağıda verilmiştir:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

İşte bir Web uygulaması için:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

Bu örneklerde, `Sdk` öğesinin özniteliği, `Project` Proje oluşturan MSBuild hedefleri ve görevleri kümesini belirtir.  `TargetFramework`Öğesi, uygulamanın bağımlı olduğu .NET sürümünü belirtir. Projeye özgü ek hedefleri ve görevleri eklemek için proje dosyasını düzenleyebilirsiniz.

Daha fazla bilgi için bkz. [.NET Project SDK 'ya genel bakış](project-sdk/overview.md) ve [hedef çerçeveler](../standard/frameworks.md).

### <a name="cicd"></a>CI/CD

MSBuild ve .NET CLı, çeşitli sürekli tümleştirme araçları ve ortamları ile birlikte kullanılabilir:

* [GitHub Actions](https://github.com/features/actions)
* [Azure DevOps](/azure/devops/user-guide/what-is-azure-devops)
* [PASTASı](https://cakebuild.net/)
* [SAHTE](https://fake.build/)

Daha fazla bilgi için bkz. [.NET SDK ve araçlarını sürekli tümleştirme (CI) Ile kullanma](tools/using-ci-with-cli.md)

### <a name="nuget"></a>NuGet

[NuGet](/nuget/what-is-nuget) , .NET için tasarlanan açık kaynaklı bir paket yöneticisidir. Bir NuGet paketi,  `.nupkg` derlenen kod (dll 'ler), bu kodla ilgili diğer dosyalar ve paketin sürüm numarası gibi bilgileri içeren açıklayıcı bir bildirim içeren bir. zip dosyasıdır. Kod içeren geliştiriciler, paket oluşturma ve bunları [NuGet.org](https://nuget.org) veya özel bir ana bilgisayar halinde yayımlamaktır. Paylaşılan kod kullanmak isteyen geliştiriciler, projesine bir paket ekleyin ve ardından Proje kodlarında paketin açığa çıkarılan API 'YI çağırabilir.

Daha fazla bilgi için bkz. [NuGet belgeleri](/nuget/).

### <a name="net-interactive"></a>.NET etkileşimli

.NET etkileşimli, kullanıcıların Web, markın ve Not defterleri üzerinde etkileşimli deneyimler oluşturmalarına olanak tanıyan bir CLı araçları ve API grubudur.

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

* [.NET In-Browser öğreticisi](https://dotnet.microsoft.com/learn/dotnet/in-browser-tutorial/1)
* [Makinenizde Jupyıter ile .NET Not defterleri kullanma](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)
* [.NET etkileşimli belgeleri](https://github.com/dotnet/interactive/blob/main/docs/README.md)

## <a name="execution-models"></a>Yürütme modelleri

.NET uygulamaları, ortak dil çalışma zamanı (CLR) olarak bilinen bir çalışma zamanı ortamında [yönetilen kodu](../standard/managed-code.md) çalıştırır.

### <a name="clr"></a>CLR

.NET [clr](../standard/clr.md) , Windows, MacOS ve Linux desteği içeren platformlar arası bir çalışma zamanı. CLR bellek ayırmayı ve yönetimini işler. CLR aynı zamanda yalnızca uygulamaları yürüten ancak tam zamanında (JıT) derleyici kullanarak kod oluşturan ve derlenen bir sanal makinedir.

Daha fazla bilgi için bkz. [ortak dil çalışma zamanı (CLR) genel bakış](../standard/clr.md).

### <a name="jit-compiler-and-il"></a>JıT derleyicisi ve Il

C# gibi daha üst düzey .NET dilleri, ara dil (IL) olarak adlandırılan donanımdan bağımsız bir yönerge kümesine derler. Bir uygulama çalıştığında, JıT derleyicisi,, işlemcinin anladığı makine koduna Il 'yi dönüştürür. JıT derlemesi, kodun çalıştırılacağı makinede olur.

Uygulamanın yürütülmesi sırasında JıT derlemesi gerçekleşdiğinden, derleme süresi çalışma zamanının bir parçasıdır. Bu nedenle, JıT derleyicileri, kodu en iyi duruma getirmeye harcanan süreyi, sonuçta elde edilen kodun üretediği tasarruflarla dengelemeye yönelik Ancak, bir JıT derleyicisi gerçek donanımı bilir ve geliştiricilerin farklı platformlar için farklı uygulamalar sunmalarını ücretsiz olarak kullanabilir.

.NET JıT derleyicisi *katmanlı derleme* yapabilir, bu da çalışma zamanında bireysel yöntemleri yeniden derleyebileceği anlamına gelir. Bu özellik, sık kullanılan metotlar için kodun yüksek düzeyde ayarlanmış bir sürümünü üretirken hızlı bir şekilde derlenmenize olanak tanır.

Daha fazla bilgi için bkz. [yönetilen yürütme işlemi](../standard/managed-execution-process.md) ve [katmanlı derleme](whats-new/dotnet-core-3-0.md#tiered-compilation).

### <a name="aot-compiler"></a>AOT derleyicisi

.NET iş yüklerinin çoğu için varsayılan deneyim JıT derleyicisidir, ancak .NET iki kez güncel (AOT) derleme derlemesi sunar:

* Bazı senaryolar %100 AOT derlemesini gerektirir. [İOS](/xamarin/ios/)bir örnektir.
* Diğer senaryolarda, bir uygulamanın kodunun çoğu AOT ile derlenir ancak bazıları JıT olarak derlenir. Bazı kod desenleri AOT için (genel türler gibi) kolay değildir. Bu AOT derlemesi bir örnek, [çalıştırmaya hazırlanma](whats-new/dotnet-core-3-0.md#readytorun-images) özellikli Yayımla seçeneğidir. Bu AOT formu, nesnelerin dezavantajları olmadan, AOT 'nin avantajlarını sunmaktadır.

### <a name="automatic-memory-management"></a>Otomatik bellek yönetimi

*Çöp toplayıcı* (GC), uygulamalar için bellek ayırmayı ve serbest bırakma işlemini yönetir. Kodunuz yeni bir nesne oluşturduğunda, CLR [yönetilen yığından](../standard/garbage-collection/fundamentals.md#the-managed-heap)nesne için bellek ayırır. Yönetilen yığında kullanılabilir adres alanı bulunduğu sürece, çalışma zamanı yeni nesneler için bellek ayırmaya devam eder. Yeterli boş adres alanı kaldığı zaman, GC tarafından artık uygulama tarafından kullanılmayan yönetilen yığındaki nesneleri denetler. Daha sonra bu belleği geri kazanır.

GC, *bellek güvenliğini* sağlamaya YARDıMCı olan CLR hizmetlerinden biridir. Bir program, yalnızca ayrılmış belleğe eriştiğinde bellek güvende olur. Örneğin, çalışma zamanı, bir uygulamanın ayrılmamış belleğe bir dizi sınırlarının ötesinde erişmesini sağlar.

Daha fazla bilgi için bkz. [Otomatik bellek yönetimi](../standard/automatic-memory-management.md) ve [çöp toplama temelleri](../standard/garbage-collection/fundamentals.md).

### <a name="working-with-unmanaged-resources"></a>Yönetilmeyen kaynaklarla çalışma

Bazen kodun *yönetilmeyen kaynaklara* başvurması gerekir. Yönetilmeyen kaynaklar, .NET çalışma zamanı tarafından otomatik olarak tutulmayan kaynaklardır. Örneğin, bir dosya tanıtıcısı yönetilmeyen bir kaynaktır. Bir <xref:System.IO.FileStream> nesne yönetilen bir nesnedir, ancak yönetilmeyen bir dosya tanıtıcısına başvurur. Kullanarak işiniz bittiğinde <xref:System.IO.FileStream> dosya tanıtıcısını açıkça serbest bırakmanız gerekir.

.NET ' te, yönetilmeyen kaynaklara başvuran nesneler arabirimini uygular <xref:System.IDisposable> . Nesnesini kullanarak işiniz bittiğinde, <xref:System.IDisposable.Dispose> yönetilmeyen kaynakları serbest bırakmaktan sorumlu olan nesnenin yöntemini çağıracağız. .NET dilleri, `using` yöntemin çağırılmasını sağlayan kullanışlı bir ifade ([C#](../csharp/language-reference/keywords/using.md), [F #](../fsharp/language-reference/resource-management-the-use-keyword.md), [vb](../visual-basic/language-reference/statements/using-statement.md)) sağlar `Dispose` .

Daha fazla bilgi için bkz. [yönetilmeyen kaynakları temizleme](../standard/garbage-collection/unmanaged.md).

## <a name="deployment-models"></a>Dağıtım modelleri

.NET uygulamaları iki farklı modda yayımlanabilir:

* Bir uygulamayı *kendi içinde* yayımlamak, .net [çalışma zamanı](#sdk-and-runtimes) ve [kitaplıklarını](#runtime-libraries)ve uygulamayı ve onun bağımlılıklarını içeren bir yürütülebilir dosya oluşturur. Uygulamanın kullanıcıları bu uygulamayı .NET çalışma zamanı yüklü olmayan bir makinede çalıştırabilir. Kendi içinde bulunan uygulamalar platforma özgüdür ve isteğe bağlı olarak bir [AOT derlemesi](#aot-compiler)formu kullanılarak yayımlanabilir.

* Bir uygulamayı *Framework 'e bağımlı* olarak yayımlamak, yalnızca uygulamanın kendisini ve onun bağımlılıklarını içeren bir yürütülebilir dosya ve ikili dosyalar (*. dll* dosyaları) oluşturur. Uygulamanın kullanıcılarının .NET [çalışma zamanını](#sdk-and-runtimes)ayrı olarak yüklemesi gerekir. Yürütülebilir dosya platforma özgüdür, ancak Framework 'e bağımlı uygulamaların *. dll* dosyaları platformlar arası bir platformdur.

  Çalışma zamanının farklı sürümlerini hedefleyen çerçeveye bağımlı uygulamalar çalıştırmak için çalışma zamanının birden çok sürümünü yan yana yükleyebilirsiniz. Daha fazla bilgi için bkz. [hedef çerçeveler](../standard/frameworks.md).

Yürütülebilir dosyalar, bir [çalışma zamanı tanımlayıcısı (RID)](rid-catalog.md)ile belirttiğiniz belirli hedef platformlar için oluşturulur.

Daha fazla bilgi için bkz. [.NET uygulama yayımlamaya genel bakış](deploying/index.md) ve [.net ve Docker 'a giriş](docker/introduction.md).

## <a name="runtime-libraries"></a>Çalışma zamanı kitaplıkları

.NET, [çalışma zamanı kitaplıkları](../standard/glossary.md#runtime), [çerçeve kitaplıkları](../standard/glossary.md#framework-libraries)veya [temel sınıf kitaplığı (BCL)](../standard/glossary.md#bcl)olarak bilinen bir expante standart sınıf kitaplıkları kümesine sahiptir. Bu kitaplıklar, birçok genel amaçlı ve iş yüküne özgü tür ve yardımcı program işlevselliğine yönelik uygulamalar sağlar.

.NET çalışma zamanı kitaplıklarında tanımlı türlerin bazı örnekleri aşağıda verilmiştir:

* Ve gibi temel türler <xref:System.Boolean?displayProperty=nameWithType> <xref:System.Int32?displayProperty=nameWithType> .
* Ve gibi koleksiyonlar <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> .
* Ve gibi veri türleri <xref:System.Data.DataSet?displayProperty=nameWithType> <xref:System.Data.DataTable?displayProperty=nameWithType> .
* Gibi ağ yardımcı programı türleri <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> .
* Ve gibi [dosya ve akış g/ç](../standard/io/index.md) yardımcı programı türleri <xref:System.IO.FileStream?displayProperty=nameWithType> <xref:System.IO.TextWriter?displayProperty=nameWithType> .
* Ve gibi [serileştirme](../standard/serialization/index.md) yardımcı programı türleri <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .
* , Ve işlem hatları gibi yüksek performanslı <xref:System.Span%601?displayProperty=nameWithType> türler <xref:System.Numerics.Vector?displayProperty=nameWithType> . [](../standard/io/pipelines.md)

Daha fazla bilgi için bkz. [çalışma zamanı kitaplıklarına genel bakış](../standard/runtime-libraries-overview.md). Kitaplıkların kaynak kodu [GitHub DotNet/Runtime deposundadır](https://github.com/dotnet/runtime/tree/main/src/libraries).

### <a name="extensions-to-the-runtime-libraries"></a>Çalışma zamanı kitaplıklarının uzantıları

Yaygın olarak kullanılan bazı uygulama işlevlerinin kitaplıkları çalışma zamanı kitaplıklarına dahil edilmez, ancak aşağıdaki gibi NuGet paketlerinde kullanılabilir hale gelir:

| NuGet paketi | Belgeler |
|---------|---------|
| [Microsoft. Extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) | [Uygulama ömür yönetimi (genel ana bilgisayar)](extensions/generic-host.md) |
| [Microsoft. Extensions. Dependencyınjection](https://www.nuget.org/packages/Microsoft.Extensions.DependencyInjection) | [Bağımlılık ekleme (dı)](extensions/dependency-injection.md)
| [Microsoft.Extensions.Configurlama](https://www.nuget.org/packages/Microsoft.Extensions.Configuration) | [Yapılandırma](extensions/configuration.md) |
| [Microsoft.Extensions.Logging](https://www.nuget.org/packages/Microsoft.Extensions.Logging) | [Günlüğe kaydetme](extensions/logging.md) |
| [Microsoft. Extensions. Options](https://www.nuget.org/packages/Microsoft.Extensions.Options) | [Seçenekler deseni](extensions/options.md) |

Daha fazla bilgi için [GitHub 'daki DotNet/Extensions deposuna](https://github.com/dotnet/extensions)bakın.

## <a name="data-access"></a>Veri erişimi

.NET, bir nesne/Ilişkisel Eşleyici (ORM) ve kodda SQL sorguları yazmak için bir yol sağlar.

### <a name="entity-framework-core"></a>Entity Framework Core

Entity Framework (EF) Core, bir ORM olarak kullanılabilecek [Açık kaynaklı](https://github.com/aspnet/EntityFrameworkCore) ve platformlar arası bir veri erişim teknolojisidir. EF Core, koddaki .NET nesnelerine başvurarak bir veritabanıyla çalışmanıza olanak sağlar. Yazmanız ve test etmeniz gereken veri erişim kodu miktarını azaltır. EF Core birçok veritabanı altyapısını destekler.

Daha fazla bilgi için bkz. [Entity Framework Core](/ef/core/) ve [veritabanı sağlayıcıları](/ef/core/providers/).

### <a name="linq"></a>LINQ

Dil ile tümleşik sorgu (LINQ), veri üzerinde çalışma için bildirim temelli kod yazmanızı sağlar. Veriler birçok biçimde (örneğin, bellek içi nesneler, bir SQL veritabanı veya bir XML belgesi) olabilir, ancak yazdığınız LINQ kodu genellikle veri kaynağı tarafından farklılık gösterir.

Daha fazla bilgi için bkz. [LINQ (dil Ile tümleşik sorgu) genel bakış](../standard/linq/index.md).

## <a name="net-terminology"></a>.NET terminolojisi

.NET belgelerini anlamak için, bazı koşulların kullanımının zaman içinde nasıl değiştiğini öğrenmek yardımcı olabilir.

### <a name="net-core-and-net-5"></a>.NET Core ve .NET 5

2002 ' de, Microsoft, Windows uygulamaları oluşturmaya yönelik bir geliştirme platformu olan [.NET Framework](../framework/get-started/overview.md)yayımlamıştır. Bugün .NET Framework 4,8 sürümüdür ve hala [Microsoft tarafından desteklenmektedir](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework).

2014 ' de, Microsoft .NET Framework için platformlar arası, açık kaynaklı bir ardıl yazmayı başlamıştır. .NET 'in bu yeni uygulamasına, 3,1 sürümüne ulaşıncaya kadar .NET Core adı veriydi. .NET Core 3,1 sonraki sürümü, şu anda önizleme aşamasında olan .NET 5,0 ' dir. Bu .NET ve 4,8 .NET Framework için bu uygulamayla karışmayı önlemek için sürüm numarası atlandı. "Core" adı, artık .NET uygulamasının ana uygulamasının olduğunu açık hale getirmek için bırakıldı.

Bu makale .NET 5 ile ilgilidir, ancak .NET 5 belgelerinin çoğu hala ".NET Core" veya ".NET Framework" başvuruları vardır. Ayrıca, "Core" [ASP.NET Core](/aspnet/core/) ve [Entity Framework Core](/ef/core/)adlarında kalır.

Belgeler ayrıca .NET Standard anlamına gelir. [.NET Standard](../standard/net-standard.md) , .net 'in birden çok uygulaması için sınıf kitaplıkları geliştirmenize olanak sağlayan bir API belirtimidir.

Daha fazla bilgi için bkz. [.net mimari bileşenleri](../standard/components.md).

### <a name="overloaded-terms"></a>Aşırı yüklenmiş terimler

Aynı sözcük farklı bağlamlarda farklı şekillerde kullanıldığından, .NET için bazı terminoloji kafa karıştırıcı olabilir. Daha belirgin örneklerden bazıları aşağıda verilmiştir:

* **çalışma zamanı**

  |Bağlam  |"çalışma zamanı" anlamı |
  |---------|---------|
  | [Ortak Dil Çalışma Zamanı (CLR)](#clr)| Yönetilen programın yürütme ortamı. İşletim sistemi çalışma zamanı ortamının bir parçasıdır ancak .NET çalışma zamanının bir parçası değildir. |
  | [.Net indirme sayfasında .NET çalışma zamanı](https://dotnet.microsoft.com/download/dotnet) | Birlikte, [çerçeveye bağımlı](#deployment-models) uygulamaları çalıştırmaya yönelik destek sağlayan [clr](#clr) ve [çalışma zamanı kitaplıkları](#runtime-libraries). Bu sayfada, ASP.NET Core Server uygulamaları ve Windows Masaüstü uygulamaları için çalışma zamanı seçenekleri de sunulur. |
  | [Çalışma zamanı tanımlayıcısı (RID)](rid-catalog.md) | .NET uygulamasının üzerinde çalıştığı işletim sistemi platformu ve CPU mimarisi. Örneğin: Windows x64, Linux x64. |

* **çerçeve**

  |Bağlam  | "Framework" anlamı |
  |---------|---------------------|
  | .NET Framework | .NET ' in orijinal, yalnızca Windows için uygulanması. "Framework" büyük harfli. |
  | hedef çerçeve | Bir .NET uygulamasının veya kitaplığının dayandığı API 'lerin koleksiyonu. Örnekler: .NET Core 3,1, .NET Standard 2,0 |
  | Hedef çerçeve bilinen adı (tfd)  | TFD, .NET uygulaması veya kitaplığının hedef çerçevesini belirtmek için standartlaştırılmış bir belirteç biçimidir. Örnek: `net462` .NET Framework 4.6.2 için. |
  | çerçeveye bağımlı uygulama | Yalnızca [.net indirme sayfasından](https://dotnet.microsoft.com/download/dotnet)çalışma zamanını yüklediğiniz bir makinede çalışabilen bir uygulama. Bu kullanımdaki "Framework", .NET indirme sayfasından indirdiğinizde "çalışma zamanı" ile aynıdır. |
  | çerçeve kitaplıkları | Bazen [çalışma zamanı kitaplıkları](#runtime-libraries)için bir eş anlamlı olarak kullanılır. |

* **SDK**

  |Bağlam  | "SDK" anlamı |
  |---------|---------------|
  | [.NET indirme sayfasında SDK](#sdk-and-runtimes)  | .NET uygulamaları geliştirmek ve çalıştırmak için indirip yüklediğiniz araç ve kitaplıkların bir koleksiyonu. CLı, MSBuild, .NET çalışma zamanı ve diğer bileşenleri içerir.|
  | [SDK stili proje](#project-system-and-msbuild) | Belirli bir uygulama türü için bir projenin nasıl oluşturulacağını belirten bir MSBuild hedefleri ve görevleri kümesi. Bu anlamda SDK, `Sdk` `Project` bir proje dosyasındaki öğesinin özniteliği kullanılarak belirtilir. |

* **platformunun**

  |Bağlam  | "Platform" anlamı |
  |---------|--------------------|
  | platformlar arası | Bu dönemde, "Platform" Windows, macOS, Linux, iOS ve Android gibi işletim sistemi ve üzerinde çalıştığı donanımlar anlamına gelir. |
  | .NET platformu | Kullanım farklılık gösterir. Başvuru, bir .NET uygulaması (.NET Framework veya .NET 5 gibi) veya tüm uygulamalar dahil olmak üzere .NET 'in aşırı bir kavramı olabilir. |

.NET terminolojisi hakkında daha fazla bilgi için bkz. [.net sözlüğü](../standard/glossary.md).

## <a name="advanced-scenarios"></a>Gelişmiş senaryolar

Aşağıdaki bölümlerde, Gelişmiş senaryolarda yararlı olan bazı .NET özellikleri açıklanmaktadır.

### <a name="native-interop"></a>Yerel birlikte çalışma

Her işletim sistemi, sistem hizmetleri sağlayan bir uygulama programlama arabirimi (API) içerir. .NET, bu API 'Leri çağırmak için çeşitli yollar sağlar.

Yerel API 'lerle birlikte kullanmanın ana yolu, kısa için "Platform Invoke" veya P/Invoke aracılığıyla yapılır. P/Invoke, Linux ve Windows platformları genelinde desteklenir. Windows 'un yalnızca Windows 'un bir yolu, Yönetilen koddaki [COM bileşenleriyle](/cpp/atl/introduction-to-com) birlikte ÇALıŞARAK "com birlikte çalışma" olarak bilinir. P/Invoke altyapısının üzerine kurulmuştur, ancak daha sorunsuz şekilde farklı yollarla çalışmaktadır.

Daha fazla bilgi için bkz. [yerel birlikte çalışabilirlik](../standard/native-interop/index.md).

### <a name="unsafe-code"></a>Güvenli olmayan kod

Dil desteğine bağlı olarak, CLR yerel belleğe erişmenizi ve kod aracılığıyla işaretçi aritmetiği yapmanızı sağlar `unsafe` . Bu işlemler, bazı algoritmalar ve sistem birlikte çalışabilirliği için gereklidir. Güçlü, güvenli olmayan kod kullanımı, sistem API 'Leri ile birlikte çalışmak veya en verimli algoritmayı uygulamak gerekmedikçe önerilmez. Güvenli olmayan kod farklı ortamlarda aynı şekilde yürütülemeyebilir ve ayrıca çöp toplayıcı ve tür güvenliği avantajlarından de yararlanmaya başlayabilir. Güvenli olmayan kodu sınırlamak ve merkezileştirmek ve kodu tamamen test etmeniz önerilir.

Daha fazla bilgi için bkz. [güvenli olmayan kod ve işaretçiler](../csharp/language-reference/unsafe-code.md).

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [.NET öğreticisi seçin](tutorials/index.md)

> [!div class="nextstepaction"]
> [Tarayıcınızda .NET 'i deneyin](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)

> [!div class="nextstepaction"]
> [C turu alın #](../csharp/tour-of-csharp/index.md)

> [!div class="nextstepaction"]
> [F turu alın #](../fsharp/tour.md)
