---
ms.openlocfilehash: 8c8e87c885c99d28aa9a7a5d5a2b48c80d40d7db
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032170"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor

ZIP arşivi, merkezi dizinde ve yerel üstbilgide Sıkıştırılmış boyut ve sıkıştırılmamış boyut listesini de listeler.  Giriş verilerinin kendisi de boyutunu gösterir.  .NET Core 2,2 ve önceki sürümlerinde, bu değerler hiçbir şekilde tutarlılık denetimi yapılmadı. .NET Core 3,0 ' den itibaren artık kullanıma sunulmuştur.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> Yerel üst bilgi ZIP dosyasının orta üst bilgisiyle kabul etmese bile başarılı olur. Verilerin uzunluğu, merkezi Dizin/yerel üst bilgisinde listelenen sıkıştırılmamış dosya boyutunu aşsa bile, sıkıştırılan akışın sonuna ulaşılana kadar veriler açılır.

.NET Core 3,0 ' den itibaren <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> Yöntem, yerel üst bilgi ve orta üstbilginin bir girdinin sıkıştırılmış ve sıkıştırılmamış boyutlarında kabul ettiğini denetler.  Aksi takdirde, <xref:System.IO.InvalidDataException> Bu, arşiv 'in yerel üst bilgisi ve/veya ZIP dosyasının merkezi diziniyle uyumlu olmayan veri tanımlayıcısı liste boyutlarıdır. Bir girişi okurken, sıkıştırması açılmış veriler üst bilgide listelenen sıkıştırılmamış dosya boyutuna kesilir.

Bu değişiklik, <xref:System.IO.Compression.ZipArchiveEntry> verilerin boyutunu doğru bir şekilde temsil ettiğinden ve yalnızca o miktarda veri okunduğunuzdan emin olmak için yapılmıştır.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Bu sorunları gösteren herhangi bir ZIP arşivini yeniden paketleyin.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
