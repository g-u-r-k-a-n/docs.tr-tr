---
title: dotnet restore komutu
description: Dotnet restore komutuyla bağımlılıkları ve projeye özel araçları nasıl geri yükleyeceğinizi öğrenin.
ms.date: 02/27/2020
ms.openlocfilehash: 14bcf65bb78e6d1d96604c8a10a3ba94fab80db8
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874842"
---
# <a name="dotnet-restore"></a>dotnet restore

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet restore` -Bir projenin bağımlılıklarını ve araçlarını geri yükler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lock-file] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a>Açıklama

Bu `dotnet restore` komut, bağımlılıkları geri yüklemek Için NuGet kullanır ve proje dosyasında belirtilen projeye özgü araçlardır.  Çoğu durumda, `dotnet restore` aşağıdaki komutları çalıştırdığınızda bir NuGet geri yüklemesi gerektiğinde örtük olarak çalıştırıldığı için komutunu açıkça kullanmanız gerekmez:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Bazen, bu komutlarla örtük NuGet geri yüklemesini çalıştırmak kullanışlı olabilir. Örneğin, derleme sistemleri gibi bazı otomatikleştirilmiş sistemlerin, `dotnet restore` ağ kullanımını denetleyebilmeleri için geri yüklemenin ne zaman gerçekleşeceğini denetlemek için açıkça çağrılması gerekir. Örtük NuGet geri yüklemesini engellemek için, `--no-restore` bayrağı, örtük geri yüklemeyi devre dışı bırakmak için bu komutlardan herhangi biriyle kullanabilirsiniz.

### <a name="specify-feeds"></a>Akışları belirt

Bağımlılıkları geri yüklemek için, NuGet paketlerin bulunduğu akışlara ihtiyaç duyuyor. Akışlar genellikle *nuget.config* yapılandırma dosyası aracılığıyla sağlanır. .NET SDK yüklendiğinde varsayılan bir yapılandırma dosyası sağlanır. Ek akışlar belirtmek için aşağıdakilerden birini yapın:

- Proje dizininde kendi *nuget.config* dosyanızı oluşturun. Daha fazla bilgi için bu makalenin ilerleyen kısımlarında [yaygın NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior) ve [nuget.config farklılıkları](#nugetconfig-differences) bölümüne bakın.
- Gibi `dotnet nuget` komutları kullanın [`dotnet nuget add source`](dotnet-nuget-add-source.md) .

*nuget.config* akışlarını seçeneği ile geçersiz kılabilirsiniz `-s` .

Kimliği doğrulanmış akışların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [kimliği doğrulanmış akışlardan paketleri](/nuget/consume-packages/consuming-packages-authenticated-feeds)kullanma.

### <a name="global-packages-folder"></a>Genel paketler klasörü

Bağımlılıklar için, geri yükleme işlemi sırasında bağımsız değişkeni kullanarak geri yüklenen paketlerin nerede yerleştirileceğini belirtebilirsiniz `--packages` . Belirtilmezse, varsayılan NuGet paketi önbelleği kullanılır ve bu, `.nuget/packages` tüm işletim sistemlerindeki kullanıcının giriş dizinindeki dizininde bulunur. Örneğin, Linux üzerinde */home/user1* veya Windows üzerinde *c:\Users\User1* .

### <a name="project-specific-tooling"></a>Projeye özgü araç

Projeye özgü araçlar için, `dotnet restore` önce aracın paketlenmesi gereken paketi geri yükler ve ardından, araç bağımlılıklarını proje dosyasında belirtilen şekilde geri yüklemeye devam eder.

### <a name="nugetconfig-differences"></a>nuget.config farklar

Komutun davranışı, varsa `dotnet restore` *nuget.config* dosyasındaki ayarlardan etkilenir. Örneğin,nuget.configayarlanması, `globalPackagesFolder` geri  yüklenen NuGet paketlerini belirtilen klasöre koyar. Bu seçenek, komutunda seçeneğini belirtmeye yönelik bir alternatiftir `--packages` `dotnet restore` . Daha fazla bilgi için [nuget.config başvurusuna](/nuget/schema/nuget-config-file)bakın.

Yok sayan üç özel ayar vardır `dotnet restore` :

- [Bindingyönlendirmeler](/nuget/schema/nuget-config-file#bindingredirects-section)

  Bağlama yeniden yönlendirmeleri öğelerle çalışmaz `<PackageReference>` ve .net yalnızca `<PackageReference>` NuGet paketleri için öğeleri destekler.

- [çözümden](/nuget/schema/nuget-config-file#solution-section)

  Bu ayar Visual Studio 'ya özeldir ve .NET için uygulanmaz. .NET bir dosya kullanmaz `packages.config` ve bunun yerine `<PackageReference>` NuGet paketleri için öğeleri kullanır.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  Platformlar arası Paket imza doğrulaması desteği .NET 5.0.100 SDK 'sına eklenmiştir.

## <a name="arguments"></a>Bağımsız değişkenler

- **`ROOT`**

  Geri yüklenecek proje dosyasının isteğe bağlı yolu.

## <a name="options"></a>Seçenekler

- **`--configfile <FILE>`**

  Geri yükleme işlemi için kullanılacak NuGet yapılandırma dosyası (*nuget.config*).

- **`--disable-parallel`**

  Paralel olarak birden çok projenin geri yüklenmesini devre dışı bırakır.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, dosyadaki *project.assets.js* silme ile aynıdır.

- **`--force-evaluate`**

  Bir kilit dosyası zaten mevcut olsa bile, geri yüklemeyi tüm bağımlılıklara yeniden değerlendirmeye zorlar.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--ignore-failed-sources`**

  Yalnızca sürüm gereksinimini karşılayan paketler varsa başarısız kaynaklar hakkında uyar.

- **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya). .NET Core 2.1.400 'dan beri.

- **`--lock-file-path <LOCK_FILE_PATH>`**

  Proje kilit dosyasının yazıldığı çıkış konumu. Bu, varsayılan olarak *PROJECT_ROOT\packages.lock.js*.

- **`--locked-mode`**

  Proje kilit dosyası güncelleştirilmeye izin verme.

- **`--no-cache`**

  HTTP isteklerinin önbelleğe alınamadı belirtir.

- **`--no-dependencies`**

  Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.

- **`--packages <PACKAGES_DIRECTORY>`**

  Geri yüklenen paketlerin dizinini belirtir.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Paket geri yüklemesi için bir çalışma zamanı belirtir. Bu, `<RuntimeIdentifiers>` *. csproj* dosyasındaki etiketinde açıkça listelenmeyen çalışma zamanları paketlerini geri yüklemek için kullanılır. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). Bu seçeneği birden çok kez belirterek birden çok grup belirtin.

- **`-s|--source <SOURCE>`**

  Geri yükleme işlemi sırasında kullanılacak NuGet paket kaynağının URI 'sini belirtir. Bu ayar *nuget.config* dosyalarında belirtilen tüm kaynakları geçersiz kılar. Bu seçenek birden çok kez belirtilerek birden çok kaynak sağlanarak sağlayabilirsiniz.

- **`--use-lock-file`**

  Proje kilitleme dosyasının oluşturulup geri yükleme ile kullanılmasını sağlar.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . Varsayılan değer `minimal` olarak belirlenmiştir.

## <a name="examples"></a>Örnekler

- Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükle:

  ```dotnetcli
  dotnet restore
  ```

- Verilen yolda bulunan projenin bağımlılıklarını ve araçlarını geri yükleyin `app1` :

  ```dotnetcli
  dotnet restore ./projects/app1/app1.csproj
  ```

- Kaynak olarak belirtilen dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- Kaynak olarak girilen iki dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- Geçerli dizindeki proje için bağımlılıkları ve araçları ayrıntılı çıktıyı gösteren geri yükleyin:

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
