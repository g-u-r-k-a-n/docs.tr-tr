---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET Core projeleri oluşturur.
no-loc:
- Blazor
- WebAssembly
ms.date: 09/04/2020
ms.openlocfilehash: 2ee06c37cd950f3b9771db2f30fe353435641d67
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400597"
---
# <a name="dotnet-new"></a>dotnet new

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri

## <a name="name"></a>Ad

`dotnet new` -Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {"C#"|"F#"|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a>Açıklama

`dotnet new`Komut bir şablonu temel alan bir .NET Core projesi veya diğer yapılar oluşturur.

Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.

### <a name="implicit-restore"></a>Örtük geri yükleme

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Arguments

- **`TEMPLATE`**

  Komut çağrıldığında örnek oluşturulacak şablon. Her şablonun geçirebilmeniz için özel seçenekleri olabilir. Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).

  `dotnet new --list` `dotnet new -l` Tüm yüklü şablonların listesini görmek için veya çalıştırabilirsiniz. Değer, `TEMPLATE` döndürülen tablodaki **Şablonlar** veya **kısa ad** sütunundaki metinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.

  .NET Core 3,0 SDK ile başlayarak, aşağıdaki koşullarda komutu çağırdığınızda CLı NuGet.org içindeki şablonları arar `dotnet new` :

  - CLı çağrılırken bir şablon eşleşmesi bulamazsa `dotnet new` , bu da kısmi değildir.
  - Şablonun daha yeni bir sürümü kullanılabilir. Bu durumda, proje veya yapıt oluşturulur ancak CLı, şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.

  Aşağıdaki tabloda, .NET Core SDK ile önceden yüklenmiş olan şablonlar gösterilmektedir. Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir. Özel şablon seçeneklerini görmek için kısa ad bağlantısına tıklayın.

| Şablonlar                                    | Kısa ad                      | Dil     | Etiketler                                  | Sunulan özellikler |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| Konsol Uygulaması                          | [konsola](#console)             | [C#], F #, VB | Ortak/konsol                        | 1,0        |
| Sınıf kitaplığı                                | [projesinin](#classlib)           | [C#], F #, VB | Ortak/Kitaplık                        | 1,0        |
| WPF uygulaması                              | [WPF](#wpf)                     | [C#], VB     | Ortak/WPF                            | 3,0 (VB için 5,0)|
| WPF sınıf kitaplığı                            | [wpflib](#wpf)                  | [C#], VB     | Ortak/WPF                            | 3,0 (VB için 5,0)|
| WPF Özel Denetim Kitaplığı                   | [wpfcustomcontrollib](#wpf)     | [C#], VB     | Ortak/WPF                            | 3,0 (VB için 5,0)|
| WPF Kullanıcı denetimi kitaplığı                     | [wpfusercontrollib](#wpf)       | [C#], VB     | Ortak/WPF                            | 3,0 (VB için 5,0)|
| Windows Forms (WinForms) uygulaması         | [WinForms](#winforms)           | [C#], VB     | Ortak/WinForms                       | 3,0 (VB için 5,0)|
| Windows Forms (WinForms) sınıf kitaplığı       | [winformslib](#winforms)        | [C#], VB     | Ortak/WinForms                       | 3,0 (VB için 5,0)|
| Çalışan hizmeti                               | [ından](#web-others)           | Þ         | Ortak/çalışan/Web                     | 3,0        |
| Birim testi projesi                            | ['i](#test)                 | [C#], F #, VB | Test/MSTest                           | 1,0        |
| NUnit 3 test projesi                         | [NUnit](#nunit)                 | [C#], F #, VB | Test/NUnit                            | 2.1.400    |
| NUnit 3 test öğesi                            | `nunit-test`                    | [C#], F #, VB | Test/NUnit                            | 2.2        |
| xUnit test projesi                           | [xUnit](#test)                  | [C#], F #, VB | Test/xUnit                            | 1,0        |
| Razor bileşeni                              | `razorcomponent`                | Þ         | Web/ASP. NET                           | 3,0        |
| Razor sayfası                                   | [sayfasında](#page)                   | Þ         | Web/ASP. NET                           | 2,0        |
| MVC Viewıtemts                              | [viewıtems 'lar](#namespace)       | Þ         | Web/ASP. NET                           | 2,0        |
| MVC ViewStart                                | `viewstart`                     | Þ         | Web/ASP. NET                           | 2,0        |
| Blazor Sunucu uygulaması                            | [blazorserver](#blazorserver)   | Þ         | WebBlazor                            | 3,0        |
| BlazorWebAssemblyUygulama                       | [blazorwasm](#blazorwasm)       | Þ         | WebBlazor/WebAssembly                | 3.1.300    |
| ASP.NET Core boş                           | [Web](#web)                     | [C#], F #     | Web/boş                             | 1,0        |
| ASP.NET Core Web uygulaması (Model-View-Controller) | [MVC](#web-options)             | [C#], F #     | Web/MVC                               | 1,0        |
| ASP.NET Core Web uygulaması                         | [WEBAPP, Razor](#web-options)   | Þ         | Web/MVC/Razor Pages                   | 2,2, 2,0   |
| Angular ile ASP.NET Core                    | [Angular](#spa)                 | Þ         | Web/MVC/SPA                           | 2,0        |
| React.js ASP.NET Core                   | [tıkla](#spa)                   | Þ         | Web/MVC/SPA                           | 2,0        |
| React.js ve Redux ile ASP.NET Core         | [reactredux](#reactredux)       | Þ         | Web/MVC/SPA                           | 2,0        |
| Razor sınıf kitaplığı                          | [razorclasslib](#razorclasslib) | Þ         | Web/Razor/kitaplık/Razor sınıfı kitaplığı | 2.1        |
| ASP.NET Core Web API'si                         | [WebApi](#webapi)               | [C#], F #     | Web/WebAPI                            | 1,0        |
| ASP.NET Core gRPC hizmeti                    | [GRPC](#web-others)             | Þ         | Web/gRPC                              | 3,0        |
| DotNet gitignore dosyası                        | `gitignore`                     |              | Config                                | 3,0        |
| Dosya üzerinde global.js                             | [globaljson](#globaljson)       |              | Config                                | 2,0        |
| NuGet yapılandırması                                 | `nugetconfig`                   |              | Config                                | 1,0        |
| DotNet yerel araç bildirim dosyası              | `tool-manifest`                 |              | Config                                | 3,0        |
| Web yapılandırması                                   | `webconfig`                     |              | Config                                | 1,0        |
| Çözüm dosyası                                | `sln`                           |              | Çözüm                              | 1,0        |
| Protokol arabelleği dosyası                         | [Proto](#namespace)             |              | Web/gRPC                              | 3,0        |

## <a name="options"></a>Seçenekler

- **`--dry-run`**

  Bir şablon oluşturulmasına neden olacaksa, verilen komutun çalıştırılması durumunda ne olacağını gösteren bir Özet görüntüler. .NET Core 2,2 SDK 'dan beri kullanılabilir.

- **`--force`**

  Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar. Seçilen şablon çıkış dizinindeki mevcut dosyaları geçersiz kılacağından bu gereklidir.

- **`-h|--help`**

  Komut için yardım yazdırır. `dotnet new`Komutun kendisi veya herhangi bir şablon için çağrılabilir. Örneğin, `dotnet new mvc --help`.

- **`-i|--install <PATH|NUGET_ID>`**

  Veya tarafından belirtilen bir şablon paketini `PATH` kurar `NUGET_ID` . Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde belirtmeniz gerekir `<package-name>::<package-version>` . Varsayılan olarak, `dotnet new` \* en son kararlı paket sürümünü temsil eden sürüm için geçirir. [Örnekler](#examples) bölümündeki bir örneğe bakın.
  
  Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklüyse, şablon belirtilen sürüme veya sürüm belirtilmemişse en son kararlı sürüme güncelleştirilir.

  Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).

- **`-l|--list`**

  Belirtilen adı içeren şablonları listeler. Ad belirtilmemişse, tüm şablonları listeler.

- **`-lang|--language {C#|F#|VB}`**

  Oluşturulacak şablonun dili. Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar). Bazı şablonlar için geçerli değildir.

  > [!NOTE]
  > Bazı kabuklar `#` özel bir karakter olarak yorumlanır. Bu durumlarda, dil parametre değerini tırnak içine alın. Örneğin, `dotnet new console -lang "F#"`.

- **`-n|--name <OUTPUT_NAME>`**

  Oluşturulan çıkışın adı. Ad belirtilmemişse, geçerli dizinin adı kullanılır.

- **`--nuget-source <SOURCE>`**

  Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir. .NET Core 2,1 SDK 'dan beri kullanılabilir.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Oluşturulan çıkışın yerleştirileceği konum. Geçerli dizin varsayılandır.

- **`--type <TYPE>`**

  Şablonları kullanılabilir türlerine göre filtreler. Önceden tanımlanmış değerler `project` ve ' dir `item` .

- **`-u|--uninstall [PATH|NUGET_ID]`**

  Veya belirtilen bir şablon paketini kaldırır `PATH` `NUGET_ID` . `<PATH|NUGET_ID>`Değer belirtilmediğinde, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir. Belirtirken `NUGET_ID` , sürüm numarasını eklemeyin.

  Bu seçeneğe bir parametre belirtmezseniz, komut, yüklü şablonları ve bunlarla ilgili ayrıntıları listeler.

  > [!NOTE]
  > Bir şablonu kullanarak kaldırmak için `PATH` , yolu tam olarak nitelemeniz gerekir. Örneğin, *C:/Users/ \<USER> /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.
  > Şablon yolunuzda son Sonlandırıcı Dizin eğik çizgisi eklemeyin.

- **`--update-apply`**

  Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmelerin olup olmadığını denetler ve bunları kurar. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--update-check`**

  Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmeler olup olmadığını denetler. .NET Core 3,0 SDK 'dan beri kullanılabilir.

## <a name="template-options"></a>Şablon seçenekleri

Her proje şablonunda ek seçenekler bulunabilir. Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:

### <a name="console"></a>console

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. .NET Core 3,0 SDK 'dan beri kullanılabilir.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  `LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar. Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın. F # için desteklenmez. .NET Core 2,2 SDK 'dan beri kullanılabilir.

  Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Belirtilmişse, proje oluşturma sırasında örtük geri yükleme yürütmez. .NET Core 2,2 SDK 'dan beri kullanılabilir.

**_

### <a name="classlib"></a>projesinin

- _ *`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: `netcoreapp<version>` bir .NET Core sınıf kitaplığı oluşturmak veya `netstandard<version>` bir .NET Standard sınıf kitaplığı oluşturmak için. `netstandard2.0` varsayılan değerdir.

- **`--langVersion <VERSION_NUMBER>`**

  `LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar. Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın. F # için desteklenmez. .NET Core 2,2 SDK 'dan beri kullanılabilir.

  Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**_

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a> WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib

- _ *`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. `netcoreapp3.1` varsayılan değerdir. .NET Core 3,1 SDK 'dan beri kullanılabilir.

- **`--langVersion <VERSION_NUMBER>`**

  `LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar. Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.

  Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**_

### <a name="winforms-winformslib"></a><a name="winforms"></a> WinForms, winformslib

- _ *`--langVersion <VERSION_NUMBER>`**

  `LangVersion`Oluşturulan proje dosyasındaki özelliği ayarlar. Örneğin, `--langVersion 7.3` C# 7,3 kullanmak için kullanın.

  Varsayılan C# sürümlerinin listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**_

### <a name="worker-grpc"></a><a name="web-others"></a> çalışan, GRPC

- _ *`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. `netcoreapp3.1` varsayılan değerdir. .NET Core 3,1 SDK 'dan beri kullanılabilir.

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *launchSettings.js* dışlar.

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**_

### <a name="mstest-xunit"></a><a name="test"></a> MSTest, xUnit

- _ *`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. .NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  [DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**_

### <a name="nunit"></a>NUnit

- _ *`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |
  | 2.2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  [DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**_

### <a name="page"></a>sayfasında

- _ *`-na|--namespace <NAMESPACE_NAME>`**

  Oluşturulan kod için ad alanı. `MyApp.Namespace` varsayılan değerdir.

- **`-np|--no-pagemodel`**

  PageModel olmadan sayfayı oluşturur.

**_

### <a name="viewimports-proto"></a><a name="namespace"></a> viewıtemler, Proto

- _ *`-na|--namespace <NAMESPACE_NAME>`**

  Oluşturulan kod için ad alanı. `MyApp.Namespace` varsayılan değerdir.

**_

### <a name="blazorserver"></a>blazorserver

- _ *`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

  - `None` -Kimlik doğrulaması yok (varsayılan).
  - `Individual` -Bireysel kimlik doğrulama.
  - `IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.
  - `SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.
  - `MultiOrg` -Birden çok kiracı için kuruluş kimlik doğrulaması.
  - `Windows` -Windows kimlik doğrulaması.

- **`--aad-b2c-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C`Kimlik doğrulamasıyla kullanın. `https://login.microsoftonline.com/tfp/` varsayılan değerdir.

- **`-ssp|--susi-policy-id <ID>`**

  Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C`Kimlik doğrulamasıyla kullanın.

- **`-rp|--reset-password-policy-id <ID>`**

  Bu proje için parola sıfırlama ilkesi KIMLIĞI. `IndividualB2C`Kimlik doğrulamasıyla kullanın.

- **`-ep|--edit-profile-policy-id <ID>`**

  Bu proje için profil ilke KIMLIĞINI Düzenle. `IndividualB2C`Kimlik doğrulamasıyla kullanın.

- **`--aad-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory örneği. `SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın. `https://login.microsoftonline.com/` varsayılan değerdir.

- **`--client-id <ID>`**

  Bu projenin Istemci KIMLIĞI. `IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın. `11111111-1111-1111-11111111111111111` varsayılan değerdir.

- **`--domain <DOMAIN>`**

  Dizin kiracının etki alanı. `SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın. `qualified.domain.name` varsayılan değerdir.

- **`--tenant-id <ID>`**

  Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg`Kimlik doğrulamasıyla kullanın. `22222222-2222-2222-2222-222222222222` varsayılan değerdir.

- **`--callback-path <PATH>`**

  Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu. `SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın. `/signin-oidc` varsayılan değerdir.

- **`-r|--org-read-access`**

  Bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *launchSettings.js* dışlar.

- **`--no-https`**

  HTTPS 'yi kapatır. Bu seçenek yalnızca,, `Individual` , `IndividualB2C` `SingleOrg` veya için kullanılmıyorsa geçerlidir `MultiOrg` `--auth` .

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**_

### <a name="blazorwasm"></a>blazorwasm

- _ *`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 5.0         | `net5.0`        |
  | 3,1         | `netcoreapp3.1` |

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

- **`-ho|--hosted`**

  Uygulama için bir ASP.NET Core Konağı içerir Blazor WebAssembly .

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

  - `None` -Kimlik doğrulaması yok (varsayılan).
  - `Individual` -Bireysel kimlik doğrulama.
  - `IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.
  - `SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.

- **`--authority <AUTHORITY>`**

  OıDC sağlayıcısı yetkilisi. `Individual`Kimlik doğrulamasıyla kullanın. `https://login.microsoftonline.com/` varsayılan değerdir.

- **`--aad-b2c-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C`Kimlik doğrulamasıyla kullanın. `https://aadB2CInstance.b2clogin.com/` varsayılan değerdir.

- **`-ssp|--susi-policy-id <ID>`**

  Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C`Kimlik doğrulamasıyla kullanın.

- **`--aad-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory örneği. `SingleOrg`Kimlik doğrulamasıyla kullanın. `https://login.microsoftonline.com/` varsayılan değerdir.

- **`--client-id <ID>`**

  Bu projenin Istemci KIMLIĞI. `IndividualB2C` `SingleOrg` `Individual` Tek başına senaryolarda, veya ile kimlik doğrulaması kullanın. `33333333-3333-3333-33333333333333333` varsayılan değerdir.

- **`--domain <DOMAIN>`**

  Dizin kiracının etki alanı. `SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın. `qualified.domain.name` varsayılan değerdir.

- **`--app-id-uri <URI>`**

  Çağırmak istediğiniz sunucu API 'SI için uygulama KIMLIĞI URI 'Si. `SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın. `api.id.uri` varsayılan değerdir.

- **`--api-client-id <ID>`**

  Sunucunun barındırdığı API 'nin Istemci KIMLIĞI. `SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın. `11111111-1111-1111-11111111111111111` varsayılan değerdir.

- **`-s|--default-scope <SCOPE>`**

  İstemcinin bir erişim belirteci sağlamasını istemesi gereken API kapsamı. `SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın. `user_impersonation` varsayılan değerdir.

- **`--tenant-id <ID>`**

  Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg`Kimlik doğrulamasıyla kullanın. `22222222-2222-2222-2222-222222222222` varsayılan değerdir.

- **`-r|--org-read-access`**

  Bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *launchSettings.js* dışlar.

- **`-p|--pwa`**

  yüklemeyi ve çevrimdışı kullanımı destekleyen bir aşamalı Web uygulaması (PWA) üretir.

- **`--no-https`**

  HTTPS 'yi kapatır. Bu seçenek yalnızca,, `Individual` `IndividualB2C` veya için kullanılmıyorsa geçerlidir `SingleOrg` `--auth` .

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.

- **`--called-api-url <URL>`**

  Web uygulamasından çağrılacak API 'nin URL 'SI. Yalnızca `SingleOrg` `IndividualB2C` ASP.NET Core bir ana bilgisayar olmadan veya kimlik doğrulaması için geçerlidir. `https://graph.microsoft.com/v1.0/me` varsayılan değerdir.

- **`--calls-graph`**

  Web uygulamasının Microsoft Graph çağırıyorsa belirtir. Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.

- **`--called-api-scopes <SCOPES>`**

  Web uygulamasından API 'yi çağırmak için istenen kapsamlar. Yalnızca `SingleOrg` `IndividualB2C` ASP.NET Core bir ana bilgisayar olmadan veya kimlik doğrulaması için geçerlidir. Varsayılan değer: `user.read`.

**_

### <a name="web"></a>web

- _ *`--exclude-launch-settings`**

  Oluşturulan şablondan *launchSettings.js* dışlar.

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

- **`--no-https`**

  HTTPS 'yi kapatır.

**_

### <a name="mvc-webapp"></a><a name="web-options"></a> MVC, WebApp

- _ *`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

  - `None` -Kimlik doğrulaması yok (varsayılan).
  - `Individual` -Bireysel kimlik doğrulama.
  - `IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.
  - `SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.
  - `MultiOrg` -Birden çok kiracı için kuruluş kimlik doğrulaması.
  - `Windows` -Windows kimlik doğrulaması.

- **`--aad-b2c-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C`Kimlik doğrulamasıyla kullanın. `https://login.microsoftonline.com/tfp/` varsayılan değerdir.

- **`-ssp|--susi-policy-id <ID>`**

  Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C`Kimlik doğrulamasıyla kullanın.

- **`-rp|--reset-password-policy-id <ID>`**

  Bu proje için parola sıfırlama ilkesi KIMLIĞI. `IndividualB2C`Kimlik doğrulamasıyla kullanın.

- **`-ep|--edit-profile-policy-id <ID>`**

  Bu proje için profil ilke KIMLIĞINI Düzenle. `IndividualB2C`Kimlik doğrulamasıyla kullanın.

- **`--aad-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory örneği. `SingleOrg`Veya `MultiOrg` kimlik doğrulamasıyla kullanın. `https://login.microsoftonline.com/` varsayılan değerdir.

- **`--client-id <ID>`**

  Bu projenin Istemci KIMLIĞI. `IndividualB2C`, `SingleOrg` Veya `MultiOrg` kimlik doğrulamasıyla kullanın. `11111111-1111-1111-11111111111111111` varsayılan değerdir.

- **`--domain <DOMAIN>`**

  Dizin kiracının etki alanı. `SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın. `qualified.domain.name` varsayılan değerdir.

- **`--tenant-id <ID>`**

  Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg`Kimlik doğrulamasıyla kullanın. `22222222-2222-2222-2222-222222222222` varsayılan değerdir.

- **`--callback-path <PATH>`**

  Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu. `SingleOrg`Veya `IndividualB2C` kimlik doğrulamasıyla kullanın. `/signin-oidc` varsayılan değerdir.

- **`-r|--org-read-access`**

  Bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *launchSettings.js* dışlar.

- **`--no-https`**

  HTTPS 'yi kapatır. Bu seçenek yalnızca,,, veya kullanılmıyorsa geçerlidir `Individual` `IndividualB2C` `SingleOrg` `MultiOrg` .

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. .NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

- **`--use-browserlink`**

  Projedeki BrowserLink öğesini içerir. Seçenek .NET Core 2,2 ve 3,1 SDK sürümünde kullanılamaz.

- **`-rrc|--razor-runtime-compilation`**

  Projenin hata ayıklama yapılarında [Razor çalışma zamanı derlemesini](/aspnet/core/mvc/views/view-compilation#runtime-compilation) kullanmak üzere yapılandırılıp yapılandırılmadığını belirler. .NET Core 3.1.201 SDK 'dan beri kullanılabilir seçeneği.

**_

### <a name="angular-react"></a><a name="spa"></a> Angular, tepki verme

- _ *`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulaması türü. .NET Core 3,0 SDK 'dan beri kullanılabilir.
  
  Olası değerler şunlardır:

  - `None` -Kimlik doğrulaması yok (varsayılan).
  - `Individual` -Bireysel kimlik doğrulama.

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *launchSettings.js* dışlar.

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

- **`--no-https`**

  HTTPS 'yi kapatır. Bu seçenek yalnızca kimlik doğrulaması ise geçerlidir `None` .

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

**_

### <a name="reactredux"></a>reactredux

- _ *`--exclude-launch-settings`**

  Oluşturulan şablondan *launchSettings.js* dışlar.

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

- **`--no-https`**

  HTTPS 'yi kapatır.

**_

### <a name="razorclasslib"></a>razorclasslib

- _ *`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

- **`-s|--support-pages-and-views`**

  , Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve görünümleri eklenmesini destekler. .NET Core 3,0 SDK 'dan beri kullanılabilir.

**_
  
### <a name="webapi"></a>WebApi

- _ *`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

  - `None` -Kimlik doğrulaması yok (varsayılan).
  - `IndividualB2C` -Azure AD B2C ile bireysel kimlik doğrulama.
  - `SingleOrg` -Tek bir kiracı için kuruluş kimlik doğrulaması.
  - `Windows` -Windows kimlik doğrulaması.

- **`--aad-b2c-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C`Kimlik doğrulamasıyla kullanın. `https://login.microsoftonline.com/tfp/` varsayılan değerdir.

- **`-ssp|--susi-policy-id <ID>`**

  Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C`Kimlik doğrulamasıyla kullanın.

- **`--aad-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory örneği. `SingleOrg`Kimlik doğrulamasıyla kullanın. `https://login.microsoftonline.com/` varsayılan değerdir.

- **`--client-id <ID>`**

  Bu projenin Istemci KIMLIĞI. `IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın. `11111111-1111-1111-11111111111111111` varsayılan değerdir.

- **`--domain <DOMAIN>`**

  Dizin kiracının etki alanı. `IndividualB2C`Veya `SingleOrg` kimlik doğrulamasıyla kullanın. `qualified.domain.name` varsayılan değerdir.

- **`--tenant-id <ID>`**

  Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg`Kimlik doğrulamasıyla kullanın. `22222222-2222-2222-2222-222222222222` varsayılan değerdir.

- **`-r|--org-read-access`**

  Bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *launchSettings.js* dışlar.

- **`--no-https`**

  HTTPS 'yi kapatır. `app.UseHsts` ve `app.UseHttpsRedirection` öğesine eklenmez `Startup.Configure` . Bu seçenek yalnızca `IndividualB2C` `SingleOrg` kimlik doğrulaması için kullanılmıyorsa geçerlidir.

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca `IndividualB2C` kimlik doğrulaması için geçerlidir.

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3,1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**_

### <a name="globaljson"></a>globaljson

- _ *`--sdk-version <VERSION_NUMBER>`**

  *global.json* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.

***

## <a name="examples"></a>Örnekler

- Şablon adını belirterek bir C# konsol uygulaması projesi oluşturun:

  ```dotnetcli
  dotnet new "Console Application"
  ```

- Geçerli dizinde bir F # konsol uygulaması projesi oluşturun:

  ```dotnetcli
  dotnet new console -lang "F#"
  ```

- Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun:

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- Geçerli dizinde kimlik doğrulaması olmadan yeni bir ASP.NET Core C# MVC projesi oluşturun:

  ```dotnetcli
  dotnet new mvc -au None
  ```

- Yeni bir xUnit projesi oluştur:

  ```dotnetcli
  dotnet new xunit
  ```

- Tek sayfalı uygulama (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:

  ```dotnetcli
  dotnet new spa -l
  ```

- *We* alt dizeniz ile eşleşen tüm şablonları listeleyin. Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.

  ```dotnetcli
  dotnet new we -l
  ```

- Şablonla *eşleşen şablonu* çağırma girişimi. Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.

  ```dotnetcli
  dotnet new ng
  ```

- ASP.NET Core için SPA şablonlarının 2,0 sürümünü yükler:

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- Yüklü şablonları ve bunlarla ilgili ayrıntıları, bunları kaldırma dahil olmak üzere listeleyin:

  ```dotnetcli
  dotnet new -u
  ```

- SDK sürümünü 3.1.101 olarak ayarlamak için geçerli dizinde bir *global.js* oluşturun:

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet New için özel şablonlar](custom-templates.md)
- [Dotnet new için özel şablon oluşturma](../tutorials/cli-templates-create-item-template.md)
- [DotNet/DotNet-şablon-örnek GitHub deposu](https://github.com/dotnet/dotnet-template-samples)
- [DotNet New için kullanılabilir şablonlar](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
