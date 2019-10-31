---
title: ​.NET Core 2.1’deki yenilikler
description: .NET Core 2,1 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 603e7ae4ffb9e6a4bb477af9597d6948bd63f55e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100743"
---
# <a name="whats-new-in-net-core-21"></a>​.NET Core 2.1’deki yenilikler

.NET Core 2,1, aşağıdaki alanlarda geliştirmeler ve yeni özellikler içerir:

- [Araçları](#tooling)
- [İleri al](#roll-forward)
- [Dağıtım](#deployment)
- [Windows Uyumluluk Paketi](#windows-compatibility-pack)
- [JıT derleme geliştirmeleri](#jit-compiler-improvements)
- [API değişiklikleri](#api-changes)

## <a name="tooling"></a>Araçlar

.NET Core 2,1 ' de yer alan araç, .NET Core 2,1 SDK (v 2.1.300), aşağıdaki değişiklikleri ve geliştirmeleri içerir:

### <a name="build-performance-improvements"></a>Derleme performansı iyileştirmeleri

.NET Core 2,1 ' nin önemli bir odağında, özellikle Artımlı derlemeler için derleme zamanı performansı geliştiriyoruz. Bu performans geliştirmeleri, `dotnet build` ve Visual Studio 'da derlemeler kullanılarak her iki komut satırı derlemesi için de geçerlidir. İyileşme özgü bazı alanlarda şunlar vardır:

- Paket varlık çözümlemesi için, yalnızca tüm varlıklar yerine bir derleme tarafından kullanılan varlıkları çözümleme.

- Derleme başvurularını önbelleğe alma.

- Tek başına `dotnet build` çağırmaları arasında yayılan süreçler olan uzun süre çalışan SDK yapı sunucularının kullanımı. Her `dotnet build` çalıştırıldığında büyük kod bloklarını JıT ile derleme ihtiyacını ortadan kaldırır. Yapı sunucusu işlemi aşağıdaki komutla otomatik olarak sonlandırılabilir:

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Yeni CLı komutları

Yalnızca .NET Core SDK bir parçası olarak [`DotnetCliToolReference`](../tools/extensibility.md) kullanılarak proje başına kullanılabilen birçok araç vardır. Bu araçlar şunları içerir:

- `dotnet watch`, belirli bir komut kümesini yürütmeden önce bir dosyanın değiştirilmesini bekleyen bir dosya sistem izleyicisi sağlar. Örneğin, aşağıdaki komut, geçerli projeyi otomatik olarak yeniden oluşturur ve her bir dosya değiştiğinde ayrıntılı çıkış üretir:

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   `--verbose` seçeneğinden önce gelen `--` seçeneğine göz önüne alın. Alt `dotnet` işlemine geçirilen bağımsız değişkenlerden `dotnet watch` komutuna doğrudan geçirilen seçenekleri ayırır. Bu olmadan, `--verbose` seçeneği `dotnet build` komutuna değil `dotnet watch` komutu için geçerlidir.
  
   Daha fazla bilgi için bkz. [DotNet Watch kullanarak ASP.NET Core uygulamalar geliştirme](/aspnet/core/tutorials/dotnet-watch).

- `dotnet dev-certs` ASP.NET Core uygulamalarda geliştirme sırasında kullanılan sertifikaları oluşturur ve yönetir.

- `dotnet user-secrets`, ASP.NET Core uygulamalarda Kullanıcı gizli deposundaki gizli dizileri yönetir.

- `dotnet sql-cache`, dağıtılmış önbellek için kullanılacak bir Microsoft SQL Server veritabanında tablo ve dizinler oluşturur.

- `dotnet ef`, Entity Framework Core uygulamalardaki veritabanlarını, <xref:Microsoft.EntityFrameworkCore.DbContext> nesneleri ve geçişleri yönetmeye yönelik bir araçtır. Daha fazla bilgi için bkz. [.NET komut satırı araçlarını EF Core](/ef/core/miscellaneous/cli/dotnet).

### <a name="global-tools"></a>Genel Araçlar

.NET Core 2,1, *genel araçları* destekler-diğer bir deyişle, komut satırından küresel olarak kullanılabilir özel araçlar. .NET Core 'un önceki sürümlerindeki genişletilebilirlik modeli, yalnızca [`DotnetCliToolReference` ' i](../tools/extensibility.md#consuming-per-project-tools)kullanarak her proje için kullanılabilir özel araçları kullanıma sunulmuştur.

Küresel bir araç yüklemek için [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın. Örneğin:

```dotnetcli
dotnet tool install -g dotnetsay
```

Yüklendikten sonra araç, araç adı belirtilerek komut satırından çalıştırılabilir. Daha fazla bilgi için bkz. [.NET Core genel araçlarına genel bakış](../tools/global-tools.md).

### <a name="tool-management-with-the-dotnet-tool-command"></a>`dotnet tool` komutuyla araç yönetimi

.NET Core 2,1 SDK 'da tüm araçlar işlemleri `dotnet tool` komutunu kullanır. Aşağıdaki seçenekler mevcuttur:

- bir araç yüklemek için [`dotnet tool install`](../tools/dotnet-tool-install.md) .

- [`dotnet tool update`](../tools/dotnet-tool-update.md) ' i kaldırmak ve yeniden yüklemek için, etkin bir şekilde güncelleştiren bir araç.

- Şu anda yüklü olan araçları listelemek için [`dotnet tool list`](../tools/dotnet-tool-list.md) .

- yüklü olan araçları kaldırmak için [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) .

## <a name="roll-forward"></a>İleri al

.NET Core 2,0 ile başlayan tüm .NET Core Uygulamaları, bir sistemde yüklü en son alt *sürüme* otomatik olarak ileri doğru iletir.

.NET Core 2,0 ile başlayarak, bir uygulamanın derlenme .NET Core sürümü çalışma zamanında mevcut değilse, uygulama otomatik olarak .NET Core 'un en son yüklenen alt *sürümünde* çalışır. Diğer bir deyişle, bir uygulama .NET Core 2,0 ile derlen, ancak .NET Core 2,0 de ana bilgisayar sisteminde yoksa ancak .NET Core 2,1 ise, uygulama .NET Core 2,1 ile çalışır.

> [!IMPORTANT]
> Bu geri alma davranışı önizleme sürümleri için geçerlidir. Varsayılan olarak, ana yayınlar için de uygulanmaz, ancak bu, aşağıdaki ayarlarla değiştirilebilir.

Bu davranışı, aday paylaşılan çerçeve olmadan geri alma ayarını değiştirerek değiştirebilirsiniz. Kullanılabilir ayarlar şunlardır:

- `0`-ikincil sürüm alma-iletme davranışını devre dışı bırakın. Bu ayarla, .NET Core 2.0.0 için oluşturulmuş bir uygulama .NET Core 2.0.1 'e, ancak .NET Core 2.2.0 veya .NET Core 3.0.0 'e geri alınacaktır.
- `1`-ikincil sürüm alma-iletme davranışını etkinleştirin. Bu ayar için varsayılan değerdir. Bu ayarla, .NET Core 2.0.0 için oluşturulmuş bir uygulama, ne olduğuna bağlı olarak .NET Core 2.0.1 veya .NET Core 2.2.0 'e doğru bir şekilde gönderilir, ancak .NET Core 3.0.0 'e geri almaz.
- `2`-küçük ve ana sürüm alma-iletme davranışını etkinleştirin. Ayarlanırsa, farklı ana sürümler de dikkate alınır, bu nedenle .NET Core 2.0.0 için derlenmiş bir uygulama .NET Core 3.0.0 'e geri alınacaktır.

Bu ayarı, üç şekilde değiştirebilirsiniz:

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` ortam değişkenini istenen değere ayarlayın.

- Aşağıdaki satırı, istenen değeri *. runtimeconfig. JSON* dosyasına ekleyin:

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- [.NET Core CLI araçlarını](../tools/index.md)kullanırken, istenen değeri `run` gibi bir .NET Core komutuna ekleyerek aşağıdaki seçeneği ekleyin:

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

Düzeltme Eki Sürümü ileri, bu ayardan bağımsızdır ve herhangi bir olası küçük veya büyük sürüm ileri doğru uygulandıktan sonra yapılır.

## <a name="deployment"></a>Dağıtım

### <a name="self-contained-application-servicing"></a>Kendi içinde uygulama Bakımı

`dotnet publish` artık hizmet verilen çalışma zamanı sürümü ile bağımsız uygulamalar yayımlar. Bir bağımsız uygulamayı .NET Core 2,1 SDK (v 2.1.300) ile yayımladığınızda, uygulamanız ilgili SDK tarafından bilinen en son hizmet verilen çalışma zamanı sürümünü içerir. En son SDK 'ya yükselttiğinizde, en son .NET Core çalışma zamanı sürümü ile yayımlayabilirsiniz. Bu, .NET Core 1,0 çalışma zamanları ve üzeri için geçerlidir.

Kendi içinde yayımlama, NuGet.org üzerinde çalışma zamanı sürümlerini kullanır. Makinenizde bakım çalışma zamanına sahip olmanız gerekmez.

.NET Core 2,0 SDK 'sını kullanarak, `RuntimeFrameworkVersion` özelliği aracılığıyla farklı bir sürüm belirtilmediği takdirde, kendi içinde bulunan uygulamalar .NET Core 2.0.0 çalışma zamanına yayımlanır. Bu yeni davranışla birlikte, bu özelliği, otomatik olarak kapsanan bir uygulama için daha yüksek bir çalışma zamanı sürümü seçmek üzere ayarlamanıza gerek kalmaz. En kolay yaklaşım .NET Core 2,1 SDK (v 2.1.300) ile her zaman yayımlamaktır.

Daha fazla bilgi için bkz. [kendi kendine içerilen dağıtım çalışma zamanı ileri](../deploying/runtime-patch-selection.md).
## <a name="windows-compatibility-pack"></a>Windows Uyumluluk Paketi

.NET Framework mevcut koddan .NET Core 'a bağlantı oluşturduğunuzda [Windows Uyumluluk Paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)' ni kullanabilirsiniz. .NET Core 'da bulunandan daha fazla 20.000 API erişimi sağlar. Bu API 'Ler <xref:System.Drawing?displayProperty=nameWithType> ad alanı, <xref:System.Diagnostics.EventLog> sınıfı, WMI, performans sayaçları, Windows Hizmetleri ve Windows kayıt defteri türleri ve üyeleri türlerini içerir.

## <a name="jit-compiler-improvements"></a>JıT derleyicisi geliştirmeleri

.NET Core, performansı önemli ölçüde iyileştirebilen *katmanlı derleme* ( *Uyarlamalı iyileştirme*olarak da bilinir) adlı yeni bir JIT Derleyici teknolojisini içerir. Katmanlı derleme, bir katılım ayarıdır.

JıT derleyicisi tarafından gerçekleştirilen önemli görevlerden biri, kod yürütmeyi iyileştiriliyor. Ancak, daha az kullanılan kod yolları için, derleyici en iyi duruma getirilmiş kodu çalıştırmaya kıyasla kodu en iyi duruma getirmek için daha fazla zaman harcayabilir. Katmanlı derleme JıT derlemesinde iki aşama sunar:

- Mümkün olduğunca hızlı bir şekilde kod üreten **ilk katman**.

- Sık çalıştırılan yöntemler için iyileştirilmiş kod üreten **ikinci bir katman**. İkinci derleme katmanı, gelişmiş performans için paralel olarak gerçekleştirilir.

Katmanlı derlemeyi iki şekilde seçebilirsiniz.

- Katmanlı derlemeyi .NET Core 2,1 SDK kullanan tüm projelerde kullanmak için aşağıdaki ortam değişkenini ayarlayın:

  ```console
  COMPlus_TieredCompilation="1"
  ```

- Katmanlı derlemeyi proje başına temelinde kullanmak için, aşağıdaki örnekte gösterildiği gibi, `<TieredCompilation>` özelliğini MSBuild proje dosyasının `<PropertyGroup>` bölümüne ekleyin:

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a>API değişiklikleri

### <a name="spant-and-memoryt"></a>`Span<T>` ve `Memory<T>`

.NET Core 2,1, diziler ve diğer bellek türleriyle çalışmayı çok daha verimli hale getirmek için bazı yeni türler içerir. Yeni türler şunlardır:

- <xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType> ve <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Bu türler olmadan, bu tür öğeleri bir dizinin bir bölümü veya bir bellek arabelleğinin bir bölümü olarak geçirirken, bir yönteme geçirmeden önce verilerin bir kısmının kopyasını oluşturmanız gerekir. Bu türler, ek bellek ayırma ve kopyalama işlemlerine gereksinimi ortadan kaldıran bu verilerin sanal bir görünümünü sağlar.

Aşağıdaki örnek, bir dizi 10 öğenin sanal görünümünü sağlamak için bir <xref:System.Span%601> ve <xref:System.Memory%601> örneğini kullanır.

[!code-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

[!code-vb[Memory\<T>](~/samples/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a>Brotli sıkıştırma

.NET Core 2,1, Brotli sıkıştırma ve açma için destek ekler. Brotli, [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) ' de tanımlanan ve çoğu Web tarayıcısı ve ana Web sunucusu tarafından desteklenen genel amaçlı kayıpsız bir sıkıştırma algoritmasıdır. Stream tabanlı <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> sınıfını veya yüksek performanslı span tabanlı <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> ve <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> sınıflarını kullanabilirsiniz. Aşağıdaki örnek <xref:System.IO.Compression.BrotliStream> sınıfıyla sıkıştırmayı gösterir:

[!code-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

<xref:System.IO.Compression.BrotliStream> davranış <xref:System.IO.Compression.DeflateStream> ve <xref:System.IO.Compression.GZipStream>aynıdır, bu da bu API 'Leri çağıran kodun <xref:System.IO.Compression.BrotliStream>dönüştürülmesini kolaylaştırır.

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Yeni şifreleme API 'Leri ve şifreleme geliştirmeleri

.NET Core 2,1, şifreleme API 'Lerinde çok sayıda geliştirme içerir:

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>, System. Security. Cryptography. Pkcs paketinde kullanılabilir. Uygulama, .NET Framework <xref:System.Security.Cryptography.Pkcs.SignedCms> sınıfıyla aynıdır.

- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> yöntemlerinin yeni aşırı yüklemeleri, çağıranların SHA-1 dışındaki algoritmaları kullanarak sertifika parmak izi değerlerini almasını sağlamak için bir karma algoritma tanımlayıcısı kabul eder.

- Yeni <xref:System.Span%601>tabanlı şifreleme API 'Leri, karma, HMAC, şifreleme rastgele sayı oluşturma, asimetrik imza oluşturma, asimetrik imza işleme ve RSA şifrelemesi için kullanılabilir.

- <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> performansı <xref:System.Span%601>tabanlı bir uygulama kullanılarak yaklaşık %15 oranında geliştirilmiştir.

- Yeni <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> sınıfı iki yeni yöntem içerir:

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>, aynı uzunlukta olan iki giriş için geri dönüş için sabit bir süre sürer. Bu, zamanlama tarafı kanal bilgilerine katkıda bulunmaktan kaçınmak için şifreleme doğrulamasında kullanılması uygun hale getirir.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>, iyileştirelemeyen bir bellek temizleme yordamdır.

- Statik <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> yöntemi rastgele değerlerle bir <xref:System.Span%601> doldurur.

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> artık Linux ve macOS 'ta desteklenmektedir.

- Eliptik Eğri Diffie-Hellman (ECDH) artık <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> sınıf ailesinde kullanılabilir. Yüzey alanı .NET Framework ile aynıdır.

- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> tarafından döndürülen örnek, bir SHA-2 Özeti kullanarak OAEP ile şifreleyebilir veya şifresini çözebilir, ayrıca RSA-PSS kullanarak imzaları oluşturabilir veya doğrulayabilir.

### <a name="sockets-improvements"></a>Yuva geliştirmeleri

.NET Core, daha yüksek düzey ağ API 'Lerinin temelini oluşturan <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> ve bir yeniden yazma <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType> olan yeni bir tür içerir.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, örneğin, <xref:System.Net.Http.HttpClient> uygulamasının temelini oluşturur. .NET Core 'un önceki sürümlerinde, daha üst düzey API 'Ler yerel ağ uygulamalarına dayalıdır.

.NET Core 2,1 ' de tanıtılan yuva uygulamasının çeşitli avantajları vardır:

- Önceki uygulamayla karşılaştırıldığında önemli bir performans geliştirmesi.

- Dağıtım ve hizmeti kolaylaştıran platform bağımlılıklarını eleme.

- Tüm .NET Core platformları genelinde tutarlı davranış.

<xref:System.Net.Http.SocketsHttpHandler>, .NET Core 2,1 ' de varsayılan uygulamasıdır. Ancak, <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemini çağırarak uygulamanızı eski <xref:System.Net.Http.HttpClientHandler> sınıfını kullanacak şekilde yapılandırabilirsiniz:

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

Ayrıca, <xref:System.Net.Http.SocketsHttpHandler>dayalı yuva uygulamalarını kullanmayı devre dışı bırakmak için bir ortam değişkeni de kullanabilirsiniz. Bunu yapmak için `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` `false` ya da 0 olarak ayarlayın.

Windows 'da, bir yerel uygulamaya bağlı <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType> ' ı veya bir sınıfın örneğini <xref:System.Net.Http.HttpClient> oluşturucusuna geçirerek <xref:System.Net.Http.SocketsHttpHandler> sınıfını kullanmayı da seçebilirsiniz.

Linux ve macOS 'ta, işlem başına temelinde yalnızca <xref:System.Net.Http.HttpClient> ' ı yapılandırabilirsiniz. Linux 'ta, eski <xref:System.Net.Http.HttpClient> uygulamasını kullanmak istiyorsanız, [libkıvrık](https://curl.haxx.se/libcurl/) dağıtım yapmanız gerekir. (.NET Core 2,0 ile yüklenir.)

## <a name="see-also"></a>Ayrıca bkz.

- [​.NET Core'daki Yenilikler](index.md)
- [EF Core 2,1 ' deki yeni özellikler](/ef/core/what-is-new/ef-core-2.1)
- [ASP.NET Core 2,1 ' deki yenilikler](/aspnet/core/aspnetcore-2.1)
