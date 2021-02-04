---
ms.openlocfilehash: 15786e6c659a29c5089eee9c8ac365c55b22f7fb
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99531565"
---
| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1,5]              | [1.6]              | [2.0]               | [2.1] |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|---------------------
| .NET                       | 5.0    | 5.0    | 5.0   | 5.0   | 5.0   | 5.0                | 5.0                | 5.0                 | 5.0 |
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2.0                 | 3.0 |
| .NET Framework <sup>1</sup>| 4,5    | 4,5    | 4.5.1 | 4,6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  | Yok<sup>3</sup> |
| Mono                       | 4,6    | 4,6    | 4,6   | 4,6   | 4,6   | 4,6                | 4,6                | 5.4                 | 6.4 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10,14               | 12,16 |
| Xamarin.Mac                | 3.0    | 3.0    | 3.0   | 3.0   | 3.0   | 3.0                | 3.0                | 3.8                 | 5,16 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 | 10.0 |
| Evrensel Windows Platformu | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          | TBD |
| Unity                      | 2018,1 | 2018,1 | 2018,1| 2018,1| 2018,1| 2018,1             |  2018,1            | 2018,1              | TBD |

<sup>1 .NET Framework için listelenen sürümler .NET Core 2,0 SDK ve sonraki araç sürümleri için geçerlidir. Daha eski sürümler .NET Standard 1,5 ve üzeri için farklı bir eşleme kullandı. Visual Studio 2017 ' e veya sonraki bir sürüme yükseltirsiniz, [Visual studio 2015 için .NET Core araçları için araç araçlarını indirebilirsiniz](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md) .</sup>

<sup>2 burada listelenen sürümler, NuGet 'in belirli bir .NET Standard kitaplığının uygulanıp uygulanmadığını belirlemede kullandığı kuralları temsil eder. NuGet, 4.6.1 1,5 ile 2,0 arasındaki destek .NET Standard .NET Framework düşünüyordu. bu sürümler için .NET Framework 4.6.1 projelerinden oluşturulan .NET Standard kitaplıkları kullanan birkaç sorun vardır. Bu tür kitaplıkları kullanması gereken .NET Framework projeleri için, projeyi .NET Framework 4.7.2 veya üstünü hedefleyecek şekilde yükseltmenizi öneririz.</sup>

<sup>3 .NET Framework, .NET Standard 2,1 desteklemez. Daha fazla bilgi için [.NET Standard 2,1 duyurusuna](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/)bakın.</sup>

- Sütunlar .NET Standard sürümlerini temsil eder. Her üst bilgi hücresi, bu .NET Standard sürümünde hangi API 'Lerin eklendiğini gösteren bir belge bağlantıdır.
- Satırlar, farklı .NET uygulamalarını temsil eder.
- Her hücredeki sürüm numarası, bu .NET Standard sürümünü hedeflemek için ihtiyaç duyacağınız *En düşük* uygulama sürümünü gösterir.
- Etkileşimli tablo için [.NET Standard sürümler](https://dotnet.microsoft.com/platform/dotnet-standard#versions)' i inceleyin.

[1.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.0.md
[1.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.1.md
[1.2]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.2.md
[1.3]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.3.md
[1.4]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.4.md
[1,5]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.5.md
[1.6]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.6.md
[2.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md
[2.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.1.md
