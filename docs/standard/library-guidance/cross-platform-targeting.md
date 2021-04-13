---
title: .NET kitaplıkları için platformlar arası hedefleme
description: Platformlar arası .NET kitaplıkları oluşturmaya yönelik en iyi yöntem önerileri.
ms.date: 04/12/2021
ms.openlocfilehash: c9ea186229ac6f334d19bce7effdeb23ebd602b4
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369718"
---
# <a name="cross-platform-targeting"></a><span data-ttu-id="3b425-103">Platformlar arası hedefleme</span><span class="sxs-lookup"><span data-stu-id="3b425-103">Cross-platform targeting</span></span>

<span data-ttu-id="3b425-104">Modern .NET birden çok işletim sistemini ve cihazı destekler.</span><span class="sxs-lookup"><span data-stu-id="3b425-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="3b425-105">.NET açık kaynaklı kitaplıkların, Azure 'da barındırılan bir ASP.NET Web sitesi mi yoksa Unity 'de bir .NET oyunu mi sundukları gibi çok sayıda geliştirici desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b425-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-and-net-standard-targets"></a><span data-ttu-id="3b425-106">.NET ve .NET Standard hedefleri</span><span class="sxs-lookup"><span data-stu-id="3b425-106">.NET and .NET Standard targets</span></span>

<span data-ttu-id="3b425-107">.Net ve .NET Standard hedefleri, .NET kitaplığına platformlar arası destek eklemenin en iyi yoludur.</span><span class="sxs-lookup"><span data-stu-id="3b425-107">.NET and .NET Standard targets are the best way to add cross-platform support to a .NET library.</span></span>

* <span data-ttu-id="3b425-108">[.NET Standard](../net-standard.md) , tüm .NET uygulamalarında bulunan .NET API 'lerinin bir belirtimidir.</span><span class="sxs-lookup"><span data-stu-id="3b425-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="3b425-109">.NET Standard hedefleme, belirli bir .NET Standard sürümünde olan API 'Leri kullanmak için kısıtlanmış kitaplıklar oluşturmanızı sağlar, yani bu .NET Standard sürümünü uygulayan tüm platformlar tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3b425-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of .NET Standard.</span></span>
* <span data-ttu-id="3b425-110">.NET 5, Microsoft 'un etkin bir şekilde geliştirmekte olduğu bir .NET uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="3b425-110">.NET 5 is an implementation of .NET that Microsoft is actively developing.</span></span> <span data-ttu-id="3b425-111">Bu, Windows Masaüstü uygulamaları ve platformlar arası konsol uygulamaları, bulut hizmetleri ve Web siteleri için kullanılabilen, tek bir ürün ve bir dizi özellik ve API 'yi içeren tek bir üründür.</span><span class="sxs-lookup"><span data-stu-id="3b425-111">It's a single product with a uniform set of capabilities and APIs that can be used for Windows desktop apps and cross-platform console apps, cloud services, and websites.</span></span>

<span data-ttu-id="3b425-112">.NET 'in .NET Standard nasıl Karşılaştırıldığı hakkında daha fazla bilgi için bkz. [.NET 5 ve .NET Standard](/dotnet/standard/net-standard#net-5-and-net-standard).</span><span class="sxs-lookup"><span data-stu-id="3b425-112">For more information about how .NET compares to .NET Standard, see [.NET 5 and .NET Standard](/dotnet/standard/net-standard#net-5-and-net-standard).</span></span>

<span data-ttu-id="3b425-113">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="3b425-113">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="3b425-114">.NET veya .NET Standard hedefleme ve projenizi başarıyla derlemek, kitaplığın tüm platformlarda başarıyla çalışacağını garanti etmez:</span><span class="sxs-lookup"><span data-stu-id="3b425-114">Targeting .NET or .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="3b425-115">Platforma özgü API 'Ler diğer platformlarda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="3b425-115">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="3b425-116">Örneğin, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> Windows 'da başarılı olur ve <xref:System.PlatformNotSupportedException> başka HERHANGI bir işletim sisteminde kullanıldığında throw.</span><span class="sxs-lookup"><span data-stu-id="3b425-116">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="3b425-117">API 'Ler farklı davranabilirler.</span><span class="sxs-lookup"><span data-stu-id="3b425-117">APIs can behave differently.</span></span> <span data-ttu-id="3b425-118">Örneğin, bir uygulama iOS veya UWP üzerinde güncel derleme kullandığında, yansıma API 'Leri farklı performans özelliklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3b425-118">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="3b425-119">.NET ekibi, olası sorunları bulmanıza yardımcı olmak için [bir Roslyn Çözümleyicisi sunmaktadır](../analyzers/api-analyzer.md) .</span><span class="sxs-lookup"><span data-stu-id="3b425-119">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="3b425-120">✔️ bir hedef dahil ile başlayın `netstandard2.0` .</span><span class="sxs-lookup"><span data-stu-id="3b425-120">✔️ DO start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="3b425-121">Genel amaçlı kitaplıkların çoğu .NET Standard 2,0 dışında API 'Lere ihtiyaç mamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b425-121">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="3b425-122">.NET Standard 2,0 tüm modern platformlar tarafından desteklenir ve tek bir hedefle birden çok platformu desteklemek için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="3b425-122">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="3b425-123">`net5.0`modern bir .NET ortamında yeni API 'ler varsa, bir hedef veya daha fazlasını ✔️.</span><span class="sxs-lookup"><span data-stu-id="3b425-123">✔️ DO include a `net5.0` target or later if you require new APIs introduced in a modern .NET.</span></span>

> <span data-ttu-id="3b425-124">.NET 5 veya üzeri uygulamalar bir hedef kullanabilir, bu `netstandard2.0` nedenle `net5.0` gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="3b425-124">.NET 5 or later apps can use a `netstandard2.0` target so `net5.0` isn't required.</span></span> <span data-ttu-id="3b425-125">`net5.0`Yeni .NET API 'lerini kullanmak istediğinizde açıkça hedefleme eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="3b425-125">Explicitly targeting `net5.0` should be added when you want to use new .NET APIs.</span></span>

<span data-ttu-id="3b425-126">❌ Bir hedef dahil kullanmaktan kaçının `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="3b425-126">❌ AVOID including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="3b425-127">.NET Standard 1. x, büyük bir paket bağımlılığı grafiği oluşturan ve geliştiricilerin derlerken çok sayıda paket indirmelerine neden olan ayrıntılı bir NuGet paketleri kümesi olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="3b425-127">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="3b425-128">Modern .NET uygulamaları 2,0 .NET Standard destekler.</span><span class="sxs-lookup"><span data-stu-id="3b425-128">Modern .NET implementations support .NET Standard 2.0.</span></span> <span data-ttu-id="3b425-129">Yalnızca daha eski bir platformu hedeflemek istiyorsanız .NET Standard 1. x hedefini hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="3b425-129">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="3b425-130">`netstandard2.0`hedefe ihtiyacınız varsa ✔️ bir hedef içerir `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="3b425-130">✔️ DO include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="3b425-131">2,0 .NET Standard destekleyen tüm platformlar, daha `netstandard2.0` eski platformlar çalışmaya devam ederken ve hedefi kullanmaya geri dönecektir ve daha küçük bir paket grafiğine sahip olmanın hedefi ve avantajını kullanacaktır `netstandard1.x` .</span><span class="sxs-lookup"><span data-stu-id="3b425-131">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="3b425-132">❌ Kitaplık platforma özgü bir uygulama modeli kullanıyorsa .NET Standard hedefi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="3b425-132">❌ DO NOT include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="3b425-133">Örneğin, UWP Denetim araç seti kitaplığı, yalnızca UWP üzerinde kullanılabilen bir uygulama modeline bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b425-133">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="3b425-134">Uygulama modeline özgü API 'Ler .NET Standard kullanılabilir olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="3b425-134">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="3b425-135">Çoklu hedefleme</span><span class="sxs-lookup"><span data-stu-id="3b425-135">Multi-targeting</span></span>

<span data-ttu-id="3b425-136">Bazen kitaplıklarınızdan çerçeveye özel API 'Lere erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b425-136">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="3b425-137">Çerçeveye özgü API 'Leri çağırmak için en iyi yol, projenizi yalnızca bir yerine birçok [.net hedef](../frameworks.md) çerçevesi için oluşturan Çoklu hedefleme kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3b425-137">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="3b425-138">Tüketicilerinizin tek tek çerçeveler için derleme yapmasına gerek kalmadan, bir .NET Standard çıkışına ve bir veya daha fazla çerçeveye özgü çıktıya sahip olmaya çalışmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="3b425-138">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="3b425-139">Çoklu hedefleme ile, tüm derlemeler tek bir NuGet paketi içinde paketlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="3b425-139">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="3b425-140">Daha sonra tüketiciler aynı pakete başvurabilir ve NuGet uygun uygulamayı seçer.</span><span class="sxs-lookup"><span data-stu-id="3b425-140">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="3b425-141">.NET Standard kitaplığınız, NuGet paketinizin çerçeveye özgü bir uygulama sunduğu durumlar dışında her yerde kullanılan geri dönüş Kitaplığı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="3b425-141">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="3b425-142">Çoklu hedefleme, kodunuzda koşullu derleme kullanmanıza ve çerçeveye özgü API 'Leri çağırayapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3b425-142">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="3b425-143">![Birden çok bütünleştirilmiş kod içeren NuGet paketi](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Birden çok bütünleştirilmiş kod içeren NuGet paketi")</span><span class="sxs-lookup"><span data-stu-id="3b425-143">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="3b425-144">✔️ .NET Standard ek olarak .NET uygulamalarını hedeflemeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="3b425-144">✔️ CONSIDER targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="3b425-145">.NET uygulamalarını hedefleme, .NET Standard dışında olan platforma özel API 'Leri aramanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b425-145">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="3b425-146">Bunu yaparken .NET Standard desteğini kaldırmayın.</span><span class="sxs-lookup"><span data-stu-id="3b425-146">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="3b425-147">Bunun yerine, uygulama ve teklif yeteneği API 'Lerini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3b425-147">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="3b425-148">Bu şekilde, kitaplığınız her yerde kullanılabilir ve özelliklerin çalışma zamanı ışığını destekler.</span><span class="sxs-lookup"><span data-stu-id="3b425-148">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

```csharp
public static class GpsLocation
{
    // This project uses multi-targeting to expose device-specific APIs to .NET Standard.
    public static async Task<(double latitude, double longitude)> GetCoordinatesAsync()
    {
#if NET461
        return CallDotNetFramworkApi();
#elif WINDOWS_UWP
        return CallUwpApi();
#else
        throw new PlatformNotSupportedException();
#endif
    }

    // Allows callers to check without having to catch PlatformNotSupportedException
    // or replicating the OS check.
    public static bool IsSupported
    {
        get
        {
#if NET461 || WINDOWS_UWP
            return true;
#else
            return false;
#endif
        }
    }
}
```

<span data-ttu-id="3b425-149">❌ Kaynak kodunuz tüm hedefler için aynıysa, çok hedeflemeyi ve hedefleme .NET Standard de ÖNLEYIN.</span><span class="sxs-lookup"><span data-stu-id="3b425-149">❌ AVOID multi-targeting as well as targeting .NET Standard, if your source code is the same for all targets.</span></span>

> <span data-ttu-id="3b425-150">.NET Standard derlemesi NuGet tarafından otomatik olarak kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="3b425-150">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="3b425-151">Bağımsız .NET uygulamalarının hedeflenmesi, `*.nupkg` hiçbir avantaj için boyutunu artırır.</span><span class="sxs-lookup"><span data-stu-id="3b425-151">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="3b425-152">✔️ bir hedef sunarken bir hedef eklemeyi düşünün `net461` `netstandard2.0` .</span><span class="sxs-lookup"><span data-stu-id="3b425-152">✔️ CONSIDER adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span>

> <span data-ttu-id="3b425-153">.NET Framework .NET Standard 2,0 ' in kullanılması .NET Framework 4.7.2 giderilen bazı sorunları içerir.</span><span class="sxs-lookup"><span data-stu-id="3b425-153">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="3b425-154">Hala .NET Framework 4.6.1-4.7.1 ' de bulunan geliştiriciler için .NET Framework 4.6.1 için oluşturulmuş bir ikili sunarak deneyimi geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b425-154">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="3b425-155">✔️, bir NuGet paketi kullanarak kitaplığınızı dağıtır.</span><span class="sxs-lookup"><span data-stu-id="3b425-155">✔️ DO distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="3b425-156">NuGet, geliştirici için en iyi hedefi seçer ve uygun uygulamayı seçmek zorunda kalmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b425-156">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="3b425-157">✔️ Çoklu hedefleme için proje dosyasının `TargetFrameworks` özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3b425-157">✔️ DO use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="3b425-158">✔️, UWP ve Xamarin için Çoklu hedefleme proje dosyanızı büyük ölçüde basitleştirirken [MSBuild. SDK. Extras](https://github.com/onovotny/MSBuildSdkExtras) kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="3b425-158">✔️ CONSIDER using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="3b425-159">Daha eski hedefler</span><span class="sxs-lookup"><span data-stu-id="3b425-159">Older targets</span></span>

<span data-ttu-id="3b425-160">.NET, artık yaygın olarak kullanılmayan platformların yanı sıra desteklenen .NET Framework sürümlerinin hedeflenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="3b425-160">.NET supports targeting versions of .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="3b425-161">Kitaplığınızın mümkün olduğunca çok sayıda hedef üzerinde çalışmasını sağlamak için bir değer olsa da, eksik API 'Leri geçici olarak çözmek için önemli ölçüde ek yük eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3b425-161">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="3b425-162">Belirli çerçevelerin daha fazla hedeflenmesini ve bunların erişim ve sınırlamalarını göz önünde bulundurduğumuz düşünülmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b425-162">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="3b425-163">❌ Taşınabilir sınıf kitaplığı (PCL) hedefi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="3b425-163">❌ DO NOT include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="3b425-164">Örneğin, `portable-net45+win8+wpa81+wp8`.</span><span class="sxs-lookup"><span data-stu-id="3b425-164">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="3b425-165">.NET Standard, platformlar arası .NET kitaplıklarını desteklemeye yönelik modern bir yoldur ve PCLs 'yi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3b425-165">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="3b425-166">❌ Artık desteklenmeyen .NET platformları için hedefler eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="3b425-166">❌ DO NOT include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="3b425-167">Örneğin,, `SL4` `WP` .</span><span class="sxs-lookup"><span data-stu-id="3b425-167">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3b425-168">[Önceki](get-started.md) 
> [Sonraki](strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="3b425-168">[Previous](get-started.md)
[Next](strong-naming.md)</span></span>
