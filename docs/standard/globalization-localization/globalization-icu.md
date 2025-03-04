---
description: 'Hakkında daha fazla bilgi edinin: .NET Genelleştirme ve ıCU'
title: Genelleştirme ve ICU
ms.date: 05/21/2020
helpviewer_keywords:
- globalization [.NET], about globalization
- global applications, globalization
- international applications [.NET], globalization
- world-ready applications, globalization
- application development [.NET], globalization
- culture, globalization
- icu, icu on windows, ms-icu
ms.openlocfilehash: 9ff6219a06cb05c743089e56b379de1f98bbc42c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702268"
---
# <a name="net-globalization-and-icu"></a>.NET Genelleştirme ve ıCU

Geçmişte, .NET Genelleştirme API 'Leri farklı platformlarda farklı temel kitaplıklar kullandı. UNIX üzerinde, API 'Ler, [Unicode (ıCU) Için Uluslararası bileşenleri](http://site.icu-project.org/home)kullanıyordu ve Windows 'Ta [Ulusal DIL desteği (NLS)](/windows/win32/intl/national-language-support)kullanırlar. Bu, uygulamaları farklı platformlarda çalıştırırken genelleştirme API 'Leri ile ilgili bazı davranış farklılıklarıyla sonuçlanır. Davranış farklılıkları bu alanlarda önyüklendi:

- Kültürler ve kültür verileri
- Dize büyük harfleri
- Dize sıralama ve arama
- Anahtarları Sırala
- Dize normalleştirme
- Uluslararası etki alanı adları (ıDN) desteği
- Linux üzerinde saat dilimi görünen adı

.NET 5,0 ' den başlayarak, geliştiricilerin platformlar arası farklılıklara engel olmasını sağlayan temel alınan kitaplığın kullanıldığı daha fazla denetimi vardır.

## <a name="icu-on-windows"></a>Windows üzerinde ıCU

Windows 10 Mayıs 2019 güncelleştirmesi ve sonraki sürümleri, işletim sisteminin bir parçası olarak [icu.dll](/windows/win32/intl/international-components-for-unicode--icu-) içerir ve .NET 5,0 ve sonraki sürümler varsayılan olarak ICU kullanır. Windows üzerinde çalışırken, .NET 5,0 ve sonraki sürümler yüklemeye çalışır `icu.dll` ve varsa Genelleştirme uygulamasında bu uygulamayı kullanın. ICU kitaplığı bulunamazsa veya yüklenemezse (örneğin, Windows 'un eski sürümlerinde çalışırken), .NET 5,0 ve üzeri sürümler NLS tabanlı uygulamaya geri döner.

> [!NOTE]
> ICU kullanırken bile,, `CurrentCulture` `CurrentUICulture` ve `CurrentRegion` üyeleri Kullanıcı ayarlarını kabul etmek için Windows Işletim sistemi API 'lerini kullanmaya devam eder.

### <a name="behavioral-differences"></a>Davranış farkları

Uygulamanızı .NET 5 hedefleyecek şekilde yükseltirseniz, Genelleştirme tesislerini kullandığınızı fark etmeseniz bile uygulamanızdaki değişiklikleri görebilirsiniz. Bu bölüm, görebileceğiniz davranış değişikliklerinden birini listeler, ancak diğerleri de vardır.

##### <a name="stringindexof"></a>String. IndexOf

<xref:System.String.IndexOf(System.String)?displayProperty=nameWithType>Bir dizedeki yeni satır karakterinin dizinini bulmak için çağıran aşağıdaki kodu göz önünde bulundurun.

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- Önceki .NET sürümlerinde, kod parçacığı yazdırılır `6` .
- .NET 5,0 ve sonraki sürümlerde Windows 10 ' da 2019 güncelleştirme ve sonraki sürümlerinde, kod parçacığı yazdırılır `-1` .

Kültüre duyarlı arama yerine bir sıralı arama gerçekleştirerek bu kodu onarmak için, <xref:System.String.IndexOf(System.String,System.StringComparison)> aşırı yüklemeyi çağırın ve <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> bağımsız değişken olarak geçirin.

Kod çözümleme kurallarını [CA1307: açıklık ve CA1309 Için StringComparison belirtin](../../../docs/fundamentals/code-analysis/quality-rules/ca1307.md) : kodunuzda bu çağrı sitelerini bulmak Için [sıralı StringComparison](../../../docs/fundamentals/code-analysis/quality-rules/ca1309.md) ' i kullanın.

Daha fazla bilgi için bkz. [.NET 5 + üzerindeki dizeleri karşılaştırırken davranış değişiklikleri](../base-types/string-comparison-net-5-plus.md).

### <a name="use-nls-instead-of-icu"></a>ICU yerine NLS kullanma

NLS yerine ıCU kullanılması, Genelleştirme ile ilgili bazı işlemlerle davranış farklılıkları oluşmasına neden olabilir. Bir geliştirici, NLS 'yi kullanmaya geri dönmek için ıCU uygulamasını devre dışı bırakabilirsiniz. Uygulamalar, aşağıdaki yollarla NLS modunu etkinleştirebilir:

- Proje dosyasında:

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
  </ItemGroup>
  ```

- `runtimeconfig.json` dosyasında:

  ```json
  {
    "runtimeOptions": {
       "configProperties": {
         "System.Globalization.UseNls": true
        }
    }
  }
  ```

- Ortam değişkenini `DOTNET_SYSTEM_GLOBALIZATION_USENLS` değeri veya değerine ayarlayarak `true` `1` .

> [!NOTE]
> Projede veya dosyada ayarlanan bir değer `runtimeconfig.json` , ortam değişkenine göre önceliklidir.

Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma ayarları](../../core/run-time-config/globalization.md#nls).

## <a name="app-local-icu"></a>Uygulama-yerel ıCU

Her bir ıCU sürümü BT hata düzeltmelerinin yanı sıra dünyanın dillerini açıklayan güncelleştirilmiş ortak yerel ayar veri deposu (CLDR) verilerini de getirebilir. ICU sürümleri arasında geçiş yapmak, Genelleştirme ile ilgili işlemlere geldiğinde uygulama davranışını güvenle etkileyebilir. Uygulama geliştiricilerinin tüm dağıtımlarda tutarlılığın sağlanmasına yardımcı olmak için, .NET 5,0 ve sonraki sürümleri, hem Windows hem de UNIX üzerinde uygulamaların kendi ıU kopyalarını taşıması ve kullanması için olanak sağlar.

Uygulamalar, aşağıdaki yollarla bir App-Local ıCU uygulama modunu kabul edebilir:

- Proje dosyasında:

  ```xml
  <ItemGroup>
    <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
  </ItemGroup>
  ```

- `runtimeconfig.json` dosyasında:

  ```json
  {
    "runtimeOptions": {
       "configProperties": {
         "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
       }
    }
  }
  ```

- Ortam değişkenini `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` değeri veya değerine ayarlayarak `<suffix>:<version>` `<version>` .

  `<suffix>`: Genel ıCU paketleme kurallarından sonra, en çok 36 karakterden kısa isteğe bağlı sonek. Özel bir ıU oluştururken, LIB adlarını ve dışarıya aktarılmış sembol adlarını bir sonek içerecek şekilde (örneğin, sonek) oluşturacak şekilde özelleştirebilirsiniz `libicuucmyapp` `myapp` .

  `<version>`: Geçerli bir ıCU sürümü (örneğin, 67,1). Bu sürüm, ikili dosyaları yüklemek ve içe aktarılmış sembolleri almak için kullanılır.

Uygulama yerel anahtarı ayarlandığında ıCU 'yi yüklemek için, .NET <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> birden çok yolu yoklaan yöntemini kullanır. Yöntemi ilk olarak, `NATIVE_DLL_SEARCH_DIRECTORIES` uygulamanın dosyasını temel alan DotNet ana bilgisayar tarafından oluşturulan özellikte kitaplığı bulmayı dener `deps.json` . Daha fazla bilgi için bkz. [Varsayılan yoklama](../../core/dependency-loading/default-probing.md).

Kendi içinde bulunan uygulamalar için, Kullanıcı tarafından özel bir eylem gerekmez, çünkü ıU 'nin uygulama dizininde olduğundan emin olun (kendi içindeki uygulamalar için, çalışma dizini varsayılan olarak ' dir `NATIVE_DLL_SEARCH_DIRECTORIES` ).

ICU 'yi bir NuGet paketi aracılığıyla kullanıyorsanız, bu, çerçeveye bağımlı uygulamalarda kullanılır. NuGet yerel varlıkları çözer ve bu dosyaları `deps.json` dosya ve uygulamanın çıkış dizinine dahil eder `runtimes` . .NET onu buradan yükler.

IU 'nin yerel bir derlemeden kullanıldığı, çerçeveye bağımlı uygulamalar (kendi içinde olmayan) için ek adımlar gerçekleştirmeniz gerekir. .NET SDK 'Sı henüz "gevşek" yerel ikililerinin içine dahil edilecek bir özelliğe sahip değildir `deps.json` ( [Bu SDK sorununa](https://github.com/dotnet/sdk/issues/11373)bakın). Bunun yerine, uygulamanın proje dosyasına ek bilgiler ekleyerek bunu etkinleştirebilirsiniz. Örneğin:

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

Bu, desteklenen çalışma zamanları için tüm ıCU ikilileri için yapılmalıdır. Ayrıca, `NuGetPackageId` öğe grubundaki meta verilerin `RuntimeTargetsCopyLocalItems` projenin gerçekten başvurduğu bir NuGet paketiyle eşleşmesi gerekir.

### <a name="macos-behavior"></a>macOS davranışı

`macOS` , dosyasında Linux yükleyicinden farklı yükleme komutlarından bağımlı dinamik kitaplıkları çözümlemek için farklı bir davranışa sahiptir `match-o` . Linux yükleyicisinde .NET, `libicudata` `libicuuc` `libicui18n` ICU bağımlılık grafiğini karşılamak için, ve (Bu sırada) deneyebilir. Ancak, macOS üzerinde bu çalışmaz. MacOS üzerinde ıCU oluştururken, varsayılan olarak, ' de bu yükleme komutlarıyla bir dinamik kitaplık alacaksınız `libicuuc` . Aşağıdaki kod parçacığında bir örnek gösterilmektedir.

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

Bu komutlar yalnızca ıCU 'nin diğer bileşenleri için bağımlı kitaplıkların adına başvurur. Yükleyici `dlopen` , bu kitaplıkların sistem dizinlerinde olmasını veya `LD_LIBRARY_PATH` env VARS 'i ayarlamayı ya da uygulama düzeyi dizininde ICU 'nin olmasını kapsayan kuralları takip eden bir arama gerçekleştirir. `LD_LIBRARY_PATH`ICU ikililerinin uygulama düzeyi dizininde olmasını veya emin değilseniz, bazı ek işler yapmanız gerekir.

Yükleyici için, gibi bazı yönergeler vardır. Bu, `@loader_path` yükleyiciye bu yük komutuyla aynı dizinde bu bağımlılığı aramasını söyler. Bunu başarmanın iki yolu vardır:

- `install_name_tool -change`

  Aşağıdaki komutları çalıştırın:

  ```bash
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
  install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
  install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
  ```

- İle yüklenen adları oluşturmak için ıCU Patch `@loader_path`

  Oto conf () çalıştırmadan önce `./runConfigureICU` [Bu satırları şu](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) şekilde değiştirin:

  ```
  LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
  ```

## <a name="icu-on-webassembly"></a>WebAssembly üzerinde ıCU

ICU 'nin bir sürümü, özellikle WebAssembly iş yükleri için kullanılabilir. Bu sürüm, masaüstü profilleriyle Genelleştirme uyumluluğu sağlar. ICU veri dosyasının boyutunu 24 MB 'den 1,4 MB 'ye (veya Brotli ile sıkıştırılmışsa ~ 0,3 MB) azaltmak için, bu iş yükünün bir sınırlaması vardır.

Aşağıdaki API 'Ler desteklenmez:

- <xref:System.Globalization.CultureInfo.EnglishName?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.NativeName?displayProperty=nameWithType>
- <xref:System.Globalization.DateTimeFormatInfo.NativeCalendarName?displayProperty=nameWithType>
- <xref:System.Globalization.RegionInfo.NativeName?displayProperty=nameWithType>

Aşağıdaki API 'Ler sınırlamalarla desteklenir:

- <xref:System.String.Normalize(System.Text.NormalizationForm)?displayProperty=nameWithType> ve <xref:System.String.IsNormalized(System.Text.NormalizationForm)?displayProperty=nameWithType> nadiren kullanılan <xref:System.Text.NormalizationForm.FormKC> ve <xref:System.Text.NormalizationForm.FormKD> formları desteklemez.
- <xref:System.Globalization.RegionInfo.CurrencyNativeName?displayProperty=nameWithType> ile aynı değeri döndürür <xref:System.Globalization.RegionInfo.CurrencyEnglishName?displayProperty=nameWithType> .

Ayrıca, desteklenen yerel ayarların bir listesi [DotNet/ICU](https://github.com/dotnet/icu/blob/0f49268ddfd3331ca090f1c51d2baa2f75f6c6c0/icu-filters/optimal.json#L6-L54)deposunda bulunabilir.
