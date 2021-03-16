---
title: 'Son değişiklik: CA1416: platform uyumluluğu'
description: Kod Analizi kuralı CA1416 'nin etkinleştirilmesi nedeniyle .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/29/2020
ms.openlocfilehash: fa03e1f0bfa8438b3b2899aaf7c97f42533c7c02
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477551"
---
# <a name="warning-ca1416-platform-compatibility"></a><span data-ttu-id="f08af-103">Uyarı CA1416: platform uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="f08af-103">Warning CA1416: Platform compatibility</span></span>

<span data-ttu-id="f08af-104">.Net Code Analyzer Rule [CA1416](/visualstudio/code-quality/ca1416) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="f08af-104">.NET code analyzer rule [CA1416](/visualstudio/code-quality/ca1416) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="f08af-105">İşletim sistemini doğrulamaktan gelen çağrı sitelerinden platforma özel API 'lere çağrılar için bir derleme uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f08af-105">It produces a build warning for calls to platform-specific APIs from call sites that don't verify the operating system.</span></span>

## <a name="change-description"></a><span data-ttu-id="f08af-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="f08af-106">Change description</span></span>

<span data-ttu-id="f08af-107">.NET 5 ' den başlayarak .NET SDK [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="f08af-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="f08af-108">Bu kuralların bazıları varsayılan olarak [CA1416](/visualstudio/code-quality/ca1416)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="f08af-108">Several of these rules are enabled, by default, including [CA1416](/visualstudio/code-quality/ca1416).</span></span> <span data-ttu-id="f08af-109">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="f08af-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span> <span data-ttu-id="f08af-110">Rule CA1416, platform bağlamının doğrulanmadığı yerlerden platforma özel API 'Ler kullandığınızda size bildirir.</span><span class="sxs-lookup"><span data-stu-id="f08af-110">Rule CA1416 informs you when you're using platform-specific APIs from places where the platform context isn't verified.</span></span>

<span data-ttu-id="f08af-111">[CA1416](/visualstudio/code-quality/ca1416)kuralı, platform uyumluluğu Çözümleyicisi, .NET 5,0 ' de yeni olan diğer özelliklerle birlikte çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f08af-111">Rule [CA1416](/visualstudio/code-quality/ca1416), the platform compatibility analyzer, works hand-in-hand with some other features that are new in .NET 5.0.</span></span> <span data-ttu-id="f08af-112">.NET 5, <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> ve <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> ' de desteklenmeyen platformları belirtmenize olanak sağlayan ve öğesini tanıtır.  </span><span class="sxs-lookup"><span data-stu-id="f08af-112">.NET 5 introduces the <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>, which let you specify the platforms that an API *is* or *isn't* supported on.</span></span> <span data-ttu-id="f08af-113">Bu özniteliklerin yokluğunda, tüm platformlarda desteklenen bir API 'nin olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="f08af-113">In the absence of these attributes, an API is assumed to be supported on all platforms.</span></span> <span data-ttu-id="f08af-114">Bu öznitelikler, çekirdek .NET kitaplıklarında platforma özel API 'lere uygulandı.</span><span class="sxs-lookup"><span data-stu-id="f08af-114">These attributes have been applied to platform-specific APIs in the core .NET libraries.</span></span>

<span data-ttu-id="f08af-115">Kullandıkları API 'Leri hedefleyen projelerde, kural [CA1416](/visualstudio/code-quality/ca1416) platform bağlamının doğrulanmadığı herhangi bir platforma özgü API çağrısını işaretler.</span><span class="sxs-lookup"><span data-stu-id="f08af-115">In projects that target platforms for which APIs that they use aren't available, rule [CA1416](/visualstudio/code-quality/ca1416) flags any platform-specific API call where the platform context isn't verified.</span></span> <span data-ttu-id="f08af-116">Artık ve öznitelikleri ile donatılmış API 'lerin çoğu, <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> <xref:System.PlatformNotSupportedException> Desteklenmeyen bir işletim sisteminde çağrıldığında özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f08af-116">Most of the APIs that are now decorated with the <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> and <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> attributes throw <xref:System.PlatformNotSupportedException> exceptions when they're invoked on an unsupported operating system.</span></span> <span data-ttu-id="f08af-117">Artık bu API 'Lerin platforma özel olarak işaretlendiğinden, kural [CA1416](/visualstudio/code-quality/ca1416) , <xref:System.PlatformNotSupportedException> çağrı sitelerinize işletim sistemi denetimleri ekleyerek çalışma zamanı özel durumlarını engellemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="f08af-117">Now that these APIs are marked as platform-specific, rule [CA1416](/visualstudio/code-quality/ca1416) helps you prevent run-time <xref:System.PlatformNotSupportedException> exceptions by adding OS checks to your call sites.</span></span>

## <a name="examples"></a><span data-ttu-id="f08af-118">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f08af-118">Examples</span></span>

- <span data-ttu-id="f08af-119"><xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType>Yöntemi yalnızca Windows 'ta desteklenir ve ile tasarlanmıştır `[SupportedOSPlatform("windows")]` .</span><span class="sxs-lookup"><span data-stu-id="f08af-119">The <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> method is only supported on Windows and is decorated with `[SupportedOSPlatform("windows")]`.</span></span> <span data-ttu-id="f08af-120">Aşağıdaki kod, proje [hedefliyorsa](../../../../standard/frameworks.md) `net5.0` (ancak yoksa) derleme zamanında bir CA1416 uyarısı oluşturur `net5.0-windows` .</span><span class="sxs-lookup"><span data-stu-id="f08af-120">The following code will produce a CA1416 warning at build time if the project [targets](../../../../standard/frameworks.md) `net5.0` (but not `net5.0-windows`).</span></span> <span data-ttu-id="f08af-121">Uyarı oluşmasını önlemek için gerçekleştirebileceğiniz eylemler için bkz. [Önerilen eylem](#recommended-action).</span><span class="sxs-lookup"><span data-stu-id="f08af-121">For actions you can take to avoid the warning, see [Recommended action](#recommended-action).</span></span>

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- <span data-ttu-id="f08af-122"><xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType>Yöntemi tarayıcıda desteklenmez ve ile donatılmış `[UnsupportedOSPlatform("browser")]` .</span><span class="sxs-lookup"><span data-stu-id="f08af-122">The <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> method is not supported in the browser and is decorated with `[UnsupportedOSPlatform("browser")]`.</span></span> <span data-ttu-id="f08af-123">Aşağıdaki kod, proje tarayıcı platformunu destekliyorsa derleme zamanında bir CA1416 uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f08af-123">The following code will produce a CA1416 warning at build time if the project supports the browser platform.</span></span>

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

  > [!TIP]
  >
  > - <span data-ttu-id="f08af-124">Blazor WebAssembly projeleri ve Razor sınıf kitaplığı projeleri otomatik olarak tarayıcı desteği içerir.</span><span class="sxs-lookup"><span data-stu-id="f08af-124">Blazor WebAssembly projects and Razor class library projects include browser support automatically.</span></span>
  > - <span data-ttu-id="f08af-125">Tarayıcınızı projeniz için desteklenen bir platform olarak el ile eklemek için, proje dosyanıza aşağıdaki girişi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f08af-125">To manually add the browser as a supported platform for your project, add the following entry to your project file:</span></span>
  >
  >  ```xml
  >  <ItemGroup>
  >    <SupportedPlatform Include="browser" />
  >  </ItemGroup>
  >  ```

## <a name="version-introduced"></a><span data-ttu-id="f08af-126">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f08af-126">Version introduced</span></span>

<span data-ttu-id="f08af-127">5.0</span><span class="sxs-lookup"><span data-stu-id="f08af-127">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f08af-128">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f08af-128">Recommended action</span></span>

<span data-ttu-id="f08af-129">Platforma özgü API 'Lerin yalnızca kod uygun bir platformda çalışırken çağrıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f08af-129">Ensure that platform-specific APIs are only called when the code is running on an appropriate platform.</span></span> <span data-ttu-id="f08af-130">Geçerli işletim sistemini, sınıfındaki yöntemlerden birini kullanarak (örneğin, `Is<Platform>` <xref:System.OperatingSystem?displayProperty=nameWithType> <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> platforma özgü bir API çağrılmadan önce) kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f08af-130">You can check the current operating system using one of the `Is<Platform>` methods in the <xref:System.OperatingSystem?displayProperty=nameWithType> class, for example, <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType>, before calling a platform-specific API.</span></span>

<span data-ttu-id="f08af-131">`Is<Platform>`Bir deyimin koşulunda yöntemlerden birini kullanabilirsiniz `if` :</span><span class="sxs-lookup"><span data-stu-id="f08af-131">You can use one of the `Is<Platform>` methods in the condition of an `if` statement:</span></span>

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

<span data-ttu-id="f08af-132">Ya da çalışma zamanında ek bir deyimin ek yükünü istemiyorsanız `if` , şunu çağırın <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="f08af-132">Or, if you don't want the overhead of an additional `if` statement at run time, call <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> instead:</span></span>

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="f08af-133">Bir kitaplık yazıyorsanız, API 'nizi platforma özel olarak işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f08af-133">If you're authoring a library, you can mark your API as platform-specific.</span></span> <span data-ttu-id="f08af-134">Bu durumda, gereksinimlerin denetim yükü çağıranlarınızın üzerine düşer.</span><span class="sxs-lookup"><span data-stu-id="f08af-134">In this case, the burden of checking requirements falls on your callers.</span></span> <span data-ttu-id="f08af-135">Belirli yöntemleri veya türleri ya da tüm derlemeyi işaretleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f08af-135">You can mark specific methods or types or an entire assembly.</span></span>

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="f08af-136">Tüm çağrı sitelerinizi onarmak istemiyorsanız, uyarıyı bastırmak için aşağıdaki seçeneklerden birini belirleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f08af-136">If you don't want to fix all your call sites, you can choose one of the following options to suppress the warning:</span></span>

- <span data-ttu-id="f08af-137">Kural CA1416 ' ı bastırmak için, `#pragma` veya [**disableduyarılar**](../../../../csharp/language-reference/compiler-options/errors-warnings.md#disabledwarnings) derleyici bayrağını kullanarak ya da [kuralın önem derecesini](../../../../fundamentals/code-analysis/configuration-options.md#severity-level) `none` bir. editorconfig dosyasında olarak ayarlayarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f08af-137">To suppress rule CA1416, you can do so using `#pragma` or the [**DisabledWarnings**](../../../../csharp/language-reference/compiler-options/errors-warnings.md#disabledwarnings) compiler flag, or by [setting the rule's severity](../../../../fundamentals/code-analysis/configuration-options.md#severity-level) to `none` in an .editorconfig file.</span></span>

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- <span data-ttu-id="f08af-138">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f08af-138">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="f08af-139">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="f08af-139">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f08af-140">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f08af-140">Affected APIs</span></span>

<span data-ttu-id="f08af-141">Windows platformu için:</span><span class="sxs-lookup"><span data-stu-id="f08af-141">For Windows platform:</span></span>

- <span data-ttu-id="f08af-142">Üzerinde listelenen tüm API 'Ler <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> .</span><span class="sxs-lookup"><span data-stu-id="f08af-142">All APIs listed at <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md>.</span></span>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

<span data-ttu-id="f08af-143">Blazor WebAssembly platformu için:</span><span class="sxs-lookup"><span data-stu-id="f08af-143">For Blazor WebAssembly platform:</span></span>

- <span data-ttu-id="f08af-144">Üzerinde listelenen tüm API 'Ler <https://github.com/dotnet/runtime/issues/41087> .</span><span class="sxs-lookup"><span data-stu-id="f08af-144">All APIs listed at <https://github.com/dotnet/runtime/issues/41087>.</span></span>

<!--

### Affected APIs

- ``

### Category

- Code analysis
- Core .NET libraries

-->

## <a name="see-also"></a><span data-ttu-id="f08af-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f08af-145">See also</span></span>

- [<span data-ttu-id="f08af-146">CA1416: Platform uyumluluğunu doğrula</span><span class="sxs-lookup"><span data-stu-id="f08af-146">CA1416: Validate platform compatibility</span></span>](/visualstudio/code-quality/ca1416)
- [<span data-ttu-id="f08af-147">.NET API Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="f08af-147">.NET API analyzer</span></span>](../../../../standard/analyzers/api-analyzer.md)
