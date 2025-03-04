---
title: dotnet publish komutu
description: Dotnet publish komutu bir dizine .NET projesi veya çözümü yayımlar.
ms.date: 02/03/2021
ms.openlocfilehash: 64f300c415d8810badca99878e4243b37f32d86d
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873425"
---
# <a name="dotnet-publish"></a>dotnet publish

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet publish` -Uygulamayı ve bağımlılıklarını barındırma sistemine dağıtım için bir klasöre yayımlar.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a>Açıklama

`dotnet publish` uygulamayı derler, proje dosyasında belirtilen bağımlılıklarını okur ve elde edilen dosya kümesini bir dizine yayınlar. Çıktı aşağıdaki varlıkları içerir:

- *DLL* uzantılı bir derlemede ara DIL (IL) kodu.
- Projenin tüm bağımlılıklarını içeren bir *.deps.js* dosyası.
- Bir dosyada, uygulamanın beklediği paylaşılan çalışma zamanını belirten bir *.runtimeconfig.js* ve çalışma zamanına yönelik diğer yapılandırma seçenekleri (örneğin, çöp toplama türü).
- NuGet önbelleğinden çıkış klasörüne kopyalanmış olan uygulamanın bağımlılıkları.

`dotnet publish`Komutun çıktısı, yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtıma yöneliktir. Uygulamayı dağıtıma hazırlamak için tek resmi olarak desteklenen bir yoldur. Projenin belirttiği dağıtımın türüne bağlı olarak, barındırma sisteminde .NET paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir. Daha fazla bilgi için bkz. .net [CLI ile .NET uygulamalarını yayımlama](../deploying/deploy-with-cli.md).

### <a name="implicit-restore"></a>Örtük geri yükleme

[!INCLUDE[dotnet restore note](../../../includes/dotnet-restore-note.md)]

### <a name="msbuild"></a>MSBuild

`dotnet publish`Komutu, hedefi çağıran MSBuild 'i çağırır `Publish` . Öğesine geçirilen parametreler `dotnet publish` MSBuild 'e geçirilir. `-c`Ve `-o` parametreleri `Configuration` sırasıyla MSBuild ve özellikler ile eşlenir `PublishDir` .

`dotnet publish`Komut, `-p` özellikleri ayarlama ve bir günlükçü tanımlama gibi MSBuild seçeneklerini kabul eder `-l` . Örneğin, şu biçimi kullanarak bir MSBuild özelliği ayarlayabilirsiniz: `-p:<NAME>=<VALUE>` .

Ayrıca, bir *. pubxml* dosyasına (.net Core 3,1 SDK sürümünden itibaren kullanılabilir) başvurarak, yayınla ilgili özellikleri de ayarlayabilirsiniz. Örnek:

```dotnetcli
dotnet publish -p:PublishProfile=FolderProfile
```

Önceki örnekte, *\<project_folder> /Properties/publishprofiles* klasöründe bulunan *folderprofile. pubxml* dosyası kullanılmaktadır. Özelliği ayarlarken bir yol ve dosya uzantısı belirtirseniz `PublishProfile` , bunlar yoksayılır. MSBuild varsayılan olarak *Properties/PublishProfiles* klasörüne bakar ve *pubxml* dosya uzantısını varsayar. Uzantısı dahil yolunu ve dosya adını belirtmek için özelliği `PublishProfileFullPath` yerine özelliği ayarlayın `PublishProfile` .

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

- [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference)
- [ASP.NET Core uygulama dağıtımı için Visual Studio yayımlama profilleri (. pubxml)](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)

## <a name="arguments"></a>Bağımsız değişkenler

- **`PROJECT|SOLUTION`**

  Yayımlanacak proje veya çözüm.

  * `PROJECT` bir C#, F # veya Visual Basic proje dosyasının yolu ve dosya adı ya da C#, F # veya Visual Basic proje dosyası içeren bir dizinin yoludur. Dizin belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır.

  * `SOLUTION` , bir çözüm dosyasının (*. sln* uzantısının) yolu ve dosya adı veya çözüm dosyası içeren bir dizinin yoludur. Dizin belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır. .NET Core 3,0 SDK 'dan beri kullanılabilir.

## <a name="options"></a>Seçenekler

- **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılandır `Debug` , ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.

- **`-f|--framework <FRAMEWORK>`**

  Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar. Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, dosyadaki *project.assets.js* silme ile aynıdır.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir. Örneğin, kimlik doğrulamasını tamamlamaya yönelik. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir. Bildirim dosyası, [ `dotnet store` komutun](dotnet-store.md)çıktısının bir parçasıdır. Birden çok bildirim belirtmek için `--manifest` her bildirim için bir seçenek ekleyin.

- **`--no-build`**

  Yayımlamadan önce projeyi oluşturmaz. Ayrıca bayrağı örtülü olarak ayarlar `--no-restore` .

- **`--no-dependencies`**

  Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.

- **`--nologo`**

  Başlangıç başlığını veya telif hakkı iletisini görüntülemez. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--no-restore`**

  Komutu çalıştırılırken örtük geri yükleme yürütülmez.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Çıkış dizini için yolu belirtir.
  
  Belirtilmemişse, çerçeveye bağlı bir yürütülebilir dosya ve platformlar arası ikili dosyalar için *[project_file_folder]/bin/[Configuration]/[Framework]/Publish/* varsayılan değeri. Bu, kendi içinde bulunan yürütülebilir dosya için *[project_file_folder]/bin/[yapılandırma]/[Framework]/[Runtime]/Publish/* varsayılan değerini alır.

  Bir Web projesinde, çıkış klasörü proje klasöründe ise, birbirini izleyen `dotnet publish` Komutlar iç içe geçmiş çıkış klasörlerine neden olur. Örneğin, proje klasörü *projem ise* ve yayımlama çıkış klasörü *myprojem/Publish* ise ve `dotnet publish` iki kez çalıştırırsanız ikinci çalıştırma, *MyProject/Publish/Publish* içindeki *. config* ve *. JSON* dosyaları gibi içerik dosyalarını koyar. Yayımlama klasörlerinin iç içe geçirilmesi önlemek için, proje **klasörünün altında olmayan** bir yayımlama klasörü belirtin veya Yayımla klasörünü projeden dışlayın. *Publishoutput* adlı bir yayımlama klasörünü dışlamak için, `PropertyGroup` *. csproj* dosyasındaki bir öğeye aşağıdaki öğeyi ekleyin:

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - .NET Core 3. x SDK ve üzeri

    Bir projeyi yayımlarken göreli bir yol belirtirseniz, oluşturulan çıkış dizini proje dosyası konumuna değil geçerli çalışma dizinine göre belirlenir.

    Bir çözüm yayımlarken göreli bir yol belirtirseniz, tüm projelere ait tüm çıktılar geçerli çalışma dizinine göre belirtilen klasöre gider. Yayımla çıkışını her proje için ayrı klasörlere gitmesini sağlamak için, seçeneği yerine MSBuild özelliğini kullanarak göreli bir yol belirtin `PublishDir` `--output` . Örneğin, `dotnet publish -p:PublishDir=.\publish` her proje için yayımlama çıkışını `publish` Proje dosyasını içeren klasörün altındaki bir klasöre gönderir.

  - .NET Core 2. x SDK

    Bir projeyi yayımlarken göreli bir yol belirtirseniz, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.

    Bir çözüm yayımlarken göreli bir yol belirtirseniz, her projenin çıktısı proje dosyası konumuna göre ayrı bir klasöre gider. Bir çözüm yayımlarken mutlak bir yol belirtirseniz, tüm projeler için tüm yayımlama çıkışları belirtilen klasöre gider.

- **`-p:PublishReadyToRun=true`**

  Uygulama derlemelerini ReadyToRun (R2R) biçimi olarak derler. R2R, bir süre öncesi (AOT) derleme biçimidir. Daha fazla bilgi için bkz. [Readytorun görüntüleri](../deploying/ready-to-run.md). .NET Core 3,0 SDK 'dan beri kullanılabilir.

  Çalışma zamanı hatalarının oluşmasına neden olabilecek eksik bağımlılıklarla ilgili uyarıları görmek için kullanın `-p:PublishReadyToRunShowWarnings=true` .

  Bu seçeneği, komut satırı yerine bir yayımlama profilinde belirtmenizi öneririz. Daha fazla bilgi için bkz. [MSBuild](#msbuild).

- **`-p:PublishSingleFile=true`**

  Uygulamayı platforma özgü bir tek dosya yürütülebilir dosyasına paketler. Yürütülebilir dosya kendiliğinden ayıklanıyor ve uygulamayı çalıştırmak için gerekli tüm bağımlılıkları (yerel dahil) içerir. Uygulama ilk kez çalıştırıldığında uygulama adı ve derleme tanımlayıcısı temelinde bir dizine çıkarılır. Uygulama yeniden çalıştırıldığında başlatma daha hızlıdır. Yeni bir sürüm kullanılmadığı takdirde uygulamanın kendisi ikinci kez ayıklanmasına gerek yoktur. .NET Core 3,0 SDK 'dan beri kullanılabilir.

  Tek dosya yayınlama hakkında daha fazla bilgi için bkz. [tek dosya paketcisi tasarım belgesi](https://github.com/dotnet/designs/blob/main/accepted/2020/single-file/design.md).

  Bu seçeneği, komut satırı yerine bir yayımlama profilinde belirtmenizi öneririz. Daha fazla bilgi için bkz. [MSBuild](#msbuild).

- **`-p:PublishTrimmed=true`**

  Bağımsız bir yürütülebilir dosya yayımlarken uygulamanın dağıtım boyutunu azaltmak için kullanılmayan kitaplıkları kırpar. Daha fazla bilgi için bkz. [kendi kendine kapsanan dağıtımları ve yürütülebilir dosyaları kırpma](../deploying/trim-self-contained.md). Bir önizleme özelliği olarak .NET Core 3,0 SDK sürümünden itibaren kullanılabilir.

  Bu seçeneği, komut satırı yerine bir yayımlama profilinde belirtmenizi öneririz. Daha fazla bilgi için bkz. [MSBuild](#msbuild).

- **`--self-contained [true|false]`**

  .NET çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez. Varsayılan olarak, `true` bir çalışma zamanı tanımlayıcısı belirtilirse ve proje yürütülebilir bir projem ise (kitaplık projesi değil). Daha fazla bilgi için bkz. .net [uygulama yayımlama](../deploying/index.md) ve .net [CLI Ile .NET uygulamaları yayımlama](../deploying/deploy-with-cli.md).

  Bu seçenek veya belirtilmeden kullanılırsa, `true` `false` varsayılan olur `true` . Bu durumda, çözüm veya proje bağımsız değişkenini hemen sonra yerleştirmeyin `--self-contained` , çünkü `true` veya `false` Bu konumda beklenmez.

- **`--no-self-contained`**

  İle eşdeğerdir `--self-contained false` . .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Uygulamayı belirli bir çalışma zamanı için yayımlar. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). Daha fazla bilgi için bkz. .net [uygulama yayımlama](../deploying/index.md) ve .net [CLI Ile .NET uygulamaları yayımlama](../deploying/deploy-with-cli.md).

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . Varsayılan değer `minimal` olarak belirlenmiştir.

- **`--version-suffix <VERSION_SUFFIX>`**

  Proje dosyasının sürüm alanındaki yıldız işaretini () değiştirecek olan sürüm sonekini tanımlar `*` .

## <a name="examples"></a>Örnekler

- Geçerli dizinde proje için [çerçeveye bağımlı platformlar arası ikili](../deploying/index.md#produce-a-cross-platform-binary) oluşturun:

  ```dotnetcli
  dotnet publish
  ```

  .NET Core 3,0 SDK ile başlayarak bu örnek ayrıca geçerli platform için [çerçeveye bağlı bir yürütülebilir dosya](../deploying/index.md#publish-framework-dependent) oluşturur.

- Belirli bir çalışma zamanı için geçerli dizindeki proje için [kendi kendine içerilen bir yürütülebilir dosya](../deploying/index.md#publish-self-contained) oluşturun:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  RID proje dosyasında olmalıdır.

- Belirli bir platform için geçerli dizindeki proje için [çerçeveye bağlı bir yürütülebilir dosya](../deploying/index.md#publish-framework-dependent) oluşturun:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  RID proje dosyasında olmalıdır. Bu örnek .NET Core 3,0 SDK ve sonraki sürümleri için geçerlidir.

- Projeyi, belirli bir çalışma zamanı ve hedef çerçeve için geçerli dizinde yayımlayın:

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Belirtilen proje dosyasını Yayımla:

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Geçerli uygulamayı yayımlayın ancak projeden projeye (P2P) başvurularını geri yüklemeyin, ancak geri yükleme işlemi sırasında yalnızca kök proje:

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET uygulama yayımlamaya genel bakış](../deploying/index.md)
- [.Net CLı ile .NET uygulamaları yayımlama](../deploying/deploy-with-cli.md)
- [Hedef çerçeveler](../../standard/frameworks.md)
- [Çalışma Zamanı Tanımlayıcısı (RID) kataloğu](../rid-catalog.md)
- [MacOS Catalina Notarle çalışma](../install/macos-notarization-issues.md)
- [Yayımlanan bir uygulamanın dizin yapısı](/aspnet/core/hosting/directory-structure)
- [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference)
- [ASP.NET Core uygulama dağıtımı için Visual Studio yayımlama profilleri (. pubxml)](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)
- [Illınk. Tasks](../deploying/trim-self-contained.md)
