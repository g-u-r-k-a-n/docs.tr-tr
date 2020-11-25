---
title: 'Son değişiklik: Microsoft. DotNet. PlatformAbstractions paketi kaldırıldı'
description: Microsoft. DotNet. PlatformAbstractions paketinin kaldırıldığı çekirdek .NET kitaplıklarında .NET 5,0 kırılımı değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 38ffe5e592d01c3bae14fc41becb594283b975a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761525"
---
# <a name="microsoftdotnetplatformabstractions-package-removed"></a>Microsoft. DotNet. PlatformAbstractions paketi kaldırıldı

[Microsoft. DotNet. PlatformAbstractions NuGet paketinin](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) yeni sürümleri üretilmeyecek.

## <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, kitaplığın yeni sürümleri <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> .NET Core 'un yeni sürümleriyle birlikte üretildi. İleri giderek kitaplığa yeni bir işlev eklenmez ve hiçbir yeni ana sürüm yayınlanmayacak. Ancak, kitaplığın var olan sürümleri çalışmaya ve hizmet verilmeye devam edecektir.

<xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName>Kitaplık, System. Namespaces içinde zaten belirlenmiş olan API 'lerle örtüşüyor \* . Ayrıca, bazı <xref:Microsoft.DotNet.PlatformAbstractions> API 'ler, sistemin geri kalanı ile aynı düzeyde scrutine ve uzun süreli desteklenebilirliği ile tasarlanmadı. \* GetVersionEx. Örneğin, <xref:Microsoft.DotNet.PlatformAbstractions> `Platform` geçerli işletim sistemi platformunu anlatmak için sabit listesini kullanır. Bu numaralandırma tasarımı, <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> API tasarlandıkça, yeni platformlar ve gelecek esnekliğe izin vermek için açıkça reddedildi.

Kitaplık tarafından etkinleştirilen senaryolar <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> artık bu olmadan mümkündür. Mevcut sürümler, .NET 5,0 ve üzeri sürümlerde bile çalışmaya devam eder ve önceki .NET Core sürümleriyle birlikte hizmet alınacaktır. Ancak, kitaplığa yeni işlevler eklenmez. Bunun yerine, diğer kitaplıklara ve API 'lere yeni işlevsellik eklenecektir.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

- Gereksinimlerinizi karşılıyorsa Kitaplığın eski sürümlerini kullanmaya devam edebilirsiniz.

- Eski sürümler gereksinimlerinizi karşılamıyorsa, API 'lerin kullanımlarını `PlatformAbstractions` Önerilen değişikliklerle değiştirin.

  | `PlatformAbstractions` 'SINDEKI | Önerilen değiştirme |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> ve <xref:System.Environment.OSVersion?displayProperty=nameWithType> |

  > [!NOTE]
  > Ve için çoğu kullanım `RuntimeEnvironment.OperatingSystem` `RuntimeEnvironment.OperatingSystemVersion` örneği, örneğin, bir kullanıcıya, günlüğe kaydetmeye ve telemetrisine görüntüleme amaçlıdır. Çalışma zamanı kararlarını bir işletim sistemi (OS) sürümüne göre yapmanız önerilmez. <xref:System.Environment.OSVersion?displayProperty=nameWithType> Şimdi Windows ve macOS işletim sistemleri için [doğru sürümü döndürür](environment-osversion-returns-correct-version.md) . Ancak, çoğu UNIX dağıtımı için "işletim sistemi sürümü" olarak kabul edilir. Örneğin, Linux çekirdek sürümü olabilir veya sürüm sürümü olabilir. Birçok UNIX platformu için <xref:System.Environment.OSVersion?displayProperty=nameWithType> ve <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> tarafından döndürülen sürümünü döndürün `uname` . Linux 'un adı ve sürüm bilgilerini almak için önerilen yaklaşım, */etc/OS-Release* dosyasını okumalıdır.

## <a name="affected-apis"></a>Etkilenen API’ler

- `Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner?displayProperty=fullName>
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier()`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- `T:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner`
- `M:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

-->
