---
title: .NET çalışma zamanı tanımlayıcısı (RID) kataloğu
description: Çalışma zamanı tanımlayıcısı (RID) ve RID 'Lerin .NET 'te nasıl kullanıldığını öğrenin.
ms.date: 01/28/2021
ms.openlocfilehash: 87fbad990fce5431769fa1631be7e079c2eb27a5
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496676"
---
# <a name="net-rid-catalog"></a>.NET RID kataloğu

*Çalışma zamanı tanımlayıcısı* için RID kısadır. RID değerleri, uygulamanın çalıştığı hedef platformları belirlemek için kullanılır.
.NET paketleri tarafından, NuGet paketlerindeki platforma özgü varlıkları göstermek için kullanılırlar. Aşağıdaki değerler, rids örnekleri: `linux-x64` , `ubuntu.14.04-x64` , `win7-x64` veya `osx.10.12-x64` .
Yerel bağımlılıklara sahip paketler için RID, paketin geri yüklenebileceği platformları belirler.

Tek bir RID, `<RuntimeIdentifier>` proje dosyanızın öğesinde ayarlanabilir. Çoklu RID 'Ler, proje dosyasının öğesinde noktalı virgülle ayrılmış bir liste olarak tanımlanabilir `<RuntimeIdentifiers>` . Bunlar ayrıca, `--runtime` aşağıdaki [.net CLI komutlarıyla](./tools/index.md)seçeneği aracılığıyla da kullanılır:

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet store](./tools/dotnet-store.md)

Somut işletim sistemlerini temsil eden RID 'Ler genellikle şu düzene uyar: `[os].[version]-[architecture]-[additional qualifiers]` burada:

- `[os]` işletim/platform sistem adıdır. Örneğin, `ubuntu`.

- `[version]` , bir noktayla ayrılmış () sürüm numarası biçimindeki işletim sistemi sürümüdür `.` . Örneğin, `15.10`.

  - Sürüm, genellikle farklı platform API yüzey alanı ile birlikte işletim sisteminin birden fazla ayrı sürümünü temsil ettiğinden, **Pazarlama sürümü olmamalıdır** .

- `[architecture]` işlemci mimarisidir. Örneğin: `x86` ,, `x64` `arm` veya `arm64` .

- `[additional qualifiers]` farklı platformları daha da birbirinden ayırt edin. Örneğin: `aot`.

## <a name="rid-graph"></a>RID grafiği

RID Graf veya çalışma zamanı geri dönüş grafiği, birbirleriyle uyumlu RID 'lerin bir listesidir. RID 'Ler, [Microsoft. NETCore. Platform](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) paketinde tanımlanır. Desteklenen RID 'lerin listesini, depoda bulunan dosyada [*runtime.js*](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) , RID grafiğinin listesini görebilirsiniz `dotnet/runtime` . Bu dosyada, temel öğe hariç tüm RID 'lerin bir ekstre içerdiğini görebilirsiniz `"#import"` . Bu deyimler, uyumlu RID 'Ler gösterir.

NuGet paketleri geri yüklediğinde, belirtilen çalışma zamanı için tam bir eşleşme bulmaya çalışır.
Tam eşleşme bulunamazsa NuGet, RID grafiğine göre en yakın uyumlu sistemi bulana kadar grafiği geri yönlendirir.

Aşağıdaki örnek, RID için gerçek giriştir `osx.10.12-x64` :

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Yukarıdaki RID, `osx.10.12-x64` içeri aktarmaların belirtir `osx.10.11-x64` . Bu nedenle, NuGet paketleri geri yüklediğinde, pakette tam eşleşmeyi bulmaya çalışır  `osx.10.12-x64` . NuGet belirli çalışma zamanını bulamazsa, örneğin çalışma zamanlarını belirten paketleri geri yükleyebilir `osx.10.11-x64` .

Aşağıdaki örnek, dosyasında *runtime.js*  de tanımlanan biraz daha büyük bir RID grafiğini gösterir:

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

Tüm RID 'Ler sonunda kök RID 'e geri eşlenir `any` .

RID 'Ler hakkında, bunlarla çalışırken göz önünde bulundurmanız gereken bazı noktalar vardır:

- Bileşen parçalarını almak için RID ayrıştırmaya çalışmayın.
- Program aracılığıyla RID oluşturma.
- Platform için önceden tanımlanmış olan RID 'leri kullanın.
- RID 'Lerin özel olması gerekir, bu nedenle gerçek RID değerinden herhangi bir şeyi varsaymayın.

## <a name="using-rids"></a>RID 'leri kullanma

RID 'leri kullanabilmeniz için hangi RID 'Lerin mevcut olduğunu bilmeniz gerekir. Yeni değerler platforma düzenli olarak eklenir.
En son ve tüm sürüm için depodaki [runtime.js](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) dosyasına bakın `dotnet/runtime` .

Taşınabilir RID 'Ler, belirli bir sürüme veya işletim sistemi dağıtımına bağlı olmayan RID grafiğine eklenen değerlerdir. Çoğu dağıtım merkezi taşınabilir RID 'lerle eşlendiğinden, özellikle birden çok Linux ile ilgilenirken tercih edilen seçenektir.

Aşağıdaki liste, her bir işletim sistemi için kullanılan en yaygın RID 'lerin küçük bir alt kümesini gösterir.

## <a name="windows-rids"></a>Windows RID 'leri

Yalnızca ortak değerler listelenir. En son ve tüm sürüm için depodaki [runtime.js](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) dosyasına bakın `dotnet/runtime` .

- In
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- Windows 7/Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8.1/Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10/Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

Daha fazla bilgi için bkz. [.net bağımlılıkları ve gereksinimleri](./install/windows.md#dependencies).

## <a name="linux-rids"></a>Linux RID 'leri

Yalnızca ortak değerler listelenir. En son ve tüm sürüm için depodaki [runtime.js](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) dosyasına bakın `dotnet/runtime` . Aşağıda listelenmeyen bir dağıtımı çalıştıran cihazlar taşınabilir RID 'Ler ile çalışabilir. Örneğin, listelenmemiş bir Linux dağıtımını çalıştıran Raspberry PI cihazları ile hedeflenebilir `linux-arm` .

- In
  - `linux-x64` (CentOS, deler, Fedora, Ubuntu ve türetmeler gibi masaüstü dağıtımlarını en iyi şekilde)
  - `linux-musl-x64` (Alp Linux gibi [MUSL](https://wiki.musl-libc.org/projects-using-musl.html) kullanan hafif dağıtımlar)
  - `linux-arm` (Raspbian gibi ARM üzerinde çalışan Linux dağıtımları Raspberry PI model 2 +)
  - `linux-arm64` (Raspberry PI model 3 + üzerinde Ubuntu Server 64-bit gibi 64 bit ARM üzerinde çalışan Linux dağıtımları
- Red Hat Enterprise Linux
  - `rhel-x64` (X sürüm 6 ' dan önce `linux-x64` RHEL için yerine geçti)
  - `rhel.6-x64`
- Tizen
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

Daha fazla bilgi için bkz. [.net bağımlılıkları ve gereksinimleri](./install/linux.md).

## <a name="macos-rids"></a>macOS RIDs

macOS 'Ler eski "OSX" markasını kullanır. Yalnızca ortak değerler listelenir. En son ve tüm sürüm için depodaki [runtime.js](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/src/runtime.json) dosyasına bakın `dotnet/runtime` .

- In
  - `osx-x64` (En düşük işletim sistemi sürümü macOS 10,12 Sierra)
- macOS 10,10 Yosemite
  - `osx.10.10-x64`
- macOS 10,11 El Capitan
  - `osx.10.11-x64`
- macOS 10,12 Sierra
  - `osx.10.12-x64`
- macOS 10,13 High Sierra
  - `osx.10.13-x64`
- macOS 10,14 Mojave
  - `osx.10.14-x64`
- macOS 10,15 Catalina
  - `osx.10.15-x64`
- macOS 11,01 Big Sur
  - `osx.11.0-x64`
  - `osx.11.0-arm64`

Daha fazla bilgi için bkz. [.net bağımlılıkları ve gereksinimleri](./install/macos.md#dependencies).

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı kimlikleri](https://github.com/dotnet/runtime/blob/main/src/libraries/Microsoft.NETCore.Platforms/readme.md)
