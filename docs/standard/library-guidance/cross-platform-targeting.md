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
# <a name="cross-platform-targeting"></a>Platformlar arası hedefleme

Modern .NET birden çok işletim sistemini ve cihazı destekler. .NET açık kaynaklı kitaplıkların, Azure 'da barındırılan bir ASP.NET Web sitesi mi yoksa Unity 'de bir .NET oyunu mi sundukları gibi çok sayıda geliştirici desteklemesi gerekir.

## <a name="net-and-net-standard-targets"></a>.NET ve .NET Standard hedefleri

.Net ve .NET Standard hedefleri, .NET kitaplığına platformlar arası destek eklemenin en iyi yoludur.

* [.NET Standard](../net-standard.md) , tüm .NET uygulamalarında bulunan .NET API 'lerinin bir belirtimidir. .NET Standard hedefleme, belirli bir .NET Standard sürümünde olan API 'Leri kullanmak için kısıtlanmış kitaplıklar oluşturmanızı sağlar, yani bu .NET Standard sürümünü uygulayan tüm platformlar tarafından kullanılabilir.
* .NET 5, Microsoft 'un etkin bir şekilde geliştirmekte olduğu bir .NET uygulamasıdır. Bu, Windows Masaüstü uygulamaları ve platformlar arası konsol uygulamaları, bulut hizmetleri ve Web siteleri için kullanılabilen, tek bir ürün ve bir dizi özellik ve API 'yi içeren tek bir üründür.

.NET 'in .NET Standard nasıl Karşılaştırıldığı hakkında daha fazla bilgi için bkz. [.NET 5 ve .NET Standard](/dotnet/standard/net-standard#net-5-and-net-standard).

![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

.NET veya .NET Standard hedefleme ve projenizi başarıyla derlemek, kitaplığın tüm platformlarda başarıyla çalışacağını garanti etmez:

1. Platforma özgü API 'Ler diğer platformlarda başarısız olur. Örneğin, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> Windows 'da başarılı olur ve <xref:System.PlatformNotSupportedException> başka HERHANGI bir işletim sisteminde kullanıldığında throw.
2. API 'Ler farklı davranabilirler. Örneğin, bir uygulama iOS veya UWP üzerinde güncel derleme kullandığında, yansıma API 'Leri farklı performans özelliklerine sahiptir.

> [!TIP]
> .NET ekibi, olası sorunları bulmanıza yardımcı olmak için [bir Roslyn Çözümleyicisi sunmaktadır](../analyzers/api-analyzer.md) .

✔️ bir hedef dahil ile başlayın `netstandard2.0` .

> Genel amaçlı kitaplıkların çoğu .NET Standard 2,0 dışında API 'Lere ihtiyaç mamalıdır. .NET Standard 2,0 tüm modern platformlar tarafından desteklenir ve tek bir hedefle birden çok platformu desteklemek için önerilen yoldur.

`net5.0`modern bir .NET ortamında yeni API 'ler varsa, bir hedef veya daha fazlasını ✔️.

> .NET 5 veya üzeri uygulamalar bir hedef kullanabilir, bu `netstandard2.0` nedenle `net5.0` gerekli değildir. `net5.0`Yeni .NET API 'lerini kullanmak istediğinizde açıkça hedefleme eklenmelidir.

❌ Bir hedef dahil kullanmaktan kaçının `netstandard1.x` .

> .NET Standard 1. x, büyük bir paket bağımlılığı grafiği oluşturan ve geliştiricilerin derlerken çok sayıda paket indirmelerine neden olan ayrıntılı bir NuGet paketleri kümesi olarak dağıtılır. Modern .NET uygulamaları 2,0 .NET Standard destekler. Yalnızca daha eski bir platformu hedeflemek istiyorsanız .NET Standard 1. x hedefini hedefleyin.

`netstandard2.0`hedefe ihtiyacınız varsa ✔️ bir hedef içerir `netstandard1.x` .

> 2,0 .NET Standard destekleyen tüm platformlar, daha `netstandard2.0` eski platformlar çalışmaya devam ederken ve hedefi kullanmaya geri dönecektir ve daha küçük bir paket grafiğine sahip olmanın hedefi ve avantajını kullanacaktır `netstandard1.x` .

❌ Kitaplık platforma özgü bir uygulama modeli kullanıyorsa .NET Standard hedefi eklemeyin.

> Örneğin, UWP Denetim araç seti kitaplığı, yalnızca UWP üzerinde kullanılabilen bir uygulama modeline bağlıdır. Uygulama modeline özgü API 'Ler .NET Standard kullanılabilir olmayacaktır.

## <a name="multi-targeting"></a>Çoklu hedefleme

Bazen kitaplıklarınızdan çerçeveye özel API 'Lere erişmeniz gerekir. Çerçeveye özgü API 'Leri çağırmak için en iyi yol, projenizi yalnızca bir yerine birçok [.net hedef](../frameworks.md) çerçevesi için oluşturan Çoklu hedefleme kullanmaktır.

Tüketicilerinizin tek tek çerçeveler için derleme yapmasına gerek kalmadan, bir .NET Standard çıkışına ve bir veya daha fazla çerçeveye özgü çıktıya sahip olmaya çalışmamalısınız. Çoklu hedefleme ile, tüm derlemeler tek bir NuGet paketi içinde paketlenmiştir. Daha sonra tüketiciler aynı pakete başvurabilir ve NuGet uygun uygulamayı seçer. .NET Standard kitaplığınız, NuGet paketinizin çerçeveye özgü bir uygulama sunduğu durumlar dışında her yerde kullanılan geri dönüş Kitaplığı işlevi görür. Çoklu hedefleme, kodunuzda koşullu derleme kullanmanıza ve çerçeveye özgü API 'Leri çağırayapılandırmanıza olanak tanır.

![Birden çok bütünleştirilmiş kod içeren NuGet paketi](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Birden çok bütünleştirilmiş kod içeren NuGet paketi")

✔️ .NET Standard ek olarak .NET uygulamalarını hedeflemeyi düşünün.

> .NET uygulamalarını hedefleme, .NET Standard dışında olan platforma özel API 'Leri aramanızı sağlar.
>
> Bunu yaparken .NET Standard desteğini kaldırmayın. Bunun yerine, uygulama ve teklif yeteneği API 'Lerini oluşturun. Bu şekilde, kitaplığınız her yerde kullanılabilir ve özelliklerin çalışma zamanı ışığını destekler.

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

❌ Kaynak kodunuz tüm hedefler için aynıysa, çok hedeflemeyi ve hedefleme .NET Standard de ÖNLEYIN.

> .NET Standard derlemesi NuGet tarafından otomatik olarak kullanılacaktır. Bağımsız .NET uygulamalarının hedeflenmesi, `*.nupkg` hiçbir avantaj için boyutunu artırır.

✔️ bir hedef sunarken bir hedef eklemeyi düşünün `net461` `netstandard2.0` .

> .NET Framework .NET Standard 2,0 ' in kullanılması .NET Framework 4.7.2 giderilen bazı sorunları içerir. Hala .NET Framework 4.6.1-4.7.1 ' de bulunan geliştiriciler için .NET Framework 4.6.1 için oluşturulmuş bir ikili sunarak deneyimi geliştirebilirsiniz.

✔️, bir NuGet paketi kullanarak kitaplığınızı dağıtır.

> NuGet, geliştirici için en iyi hedefi seçer ve uygun uygulamayı seçmek zorunda kalmalarını sağlar.

✔️ Çoklu hedefleme için proje dosyasının `TargetFrameworks` özelliğini kullanın.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

✔️, UWP ve Xamarin için Çoklu hedefleme proje dosyanızı büyük ölçüde basitleştirirken [MSBuild. SDK. Extras](https://github.com/onovotny/MSBuildSdkExtras) kullanmayı düşünün.

## <a name="older-targets"></a>Daha eski hedefler

.NET, artık yaygın olarak kullanılmayan platformların yanı sıra desteklenen .NET Framework sürümlerinin hedeflenmesini destekler. Kitaplığınızın mümkün olduğunca çok sayıda hedef üzerinde çalışmasını sağlamak için bir değer olsa da, eksik API 'Leri geçici olarak çözmek için önemli ölçüde ek yük eklenebilir. Belirli çerçevelerin daha fazla hedeflenmesini ve bunların erişim ve sınırlamalarını göz önünde bulundurduğumuz düşünülmektedir.

❌ Taşınabilir sınıf kitaplığı (PCL) hedefi eklemeyin. Örneğin, `portable-net45+win8+wpa81+wp8`.

> .NET Standard, platformlar arası .NET kitaplıklarını desteklemeye yönelik modern bir yoldur ve PCLs 'yi değiştirir.

❌ Artık desteklenmeyen .NET platformları için hedefler eklemeyin. Örneğin,, `SL4` `WP` .

>[!div class="step-by-step"]
>[Önceki](get-started.md) 
> [Sonraki](strong-naming.md)
