---
title: Windows 'a .NET yükler
description: Hangi Windows sürümlerini .NET yükleyebileceğinizi öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 1b1f2e383e270e646436f8aa1ce19edd8da262b3
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506759"
---
# <a name="install-net-on-windows"></a>Windows 'a .NET yükler

> [!div class="op_single_selector"]
>
> - [Windows’ta yükleme](windows.md)
> - [macOS’ta yükleme](macos.md)
> - [Linux'ta yükleme](linux.md)

Bu makalede, Windows 'a .NET yüklemeyi öğreneceksiniz. .NET çalışma zamanı ve SDK 'dan oluşur. Çalışma zamanı, .NET uygulamasını çalıştırmak için kullanılır ve uygulama ile birlikte bulunmayabilir veya bulunmayabilir. SDK, .NET uygulamaları ve kitaplıkları oluşturmak için kullanılır. .NET çalışma zamanı her zaman SDK ile birlikte yüklenir.

En son .NET sürümü 5,0 ' dir.

> [!div class="button"]
> [.NET İndir](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>Desteklenen yayınlar

Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Windows sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [Windows 'un yaşam sonuna ulaştığı](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)sürece desteklenene kadar desteklenmeye devam eder.

Windows 10 sürümleri hizmet son tarihleri sürüme göre bölündü. Aşağıdaki tabloda yalnızca **Home** , **Pro** , **Pro eğitim** ve **iş istasyonları için Pro** sürümleri göz önünde bulundurululur. Belirli Ayrıntılar için [Windows yaşam döngüsü olgu sayfasını](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) kontrol edin.

- ✔️, Windows veya .NET Core sürümünün hala desteklendiğini gösterir.
- Bir ❌ Windows veya .NET Core sürümünün bu Windows sürümünde desteklenmediğini belirtir.
- Hem bir Windows sürümü hem de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| İşletim Sistemi                      | .NET Core 2.1 | .NET Core 3,1 | .NET 5 |
|-----------------------------|---------------|---------------|----------------|
| ✔️ Windows 10, sürüm 2004 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ Windows 10, sürüm 1909 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ Windows 10, sürüm 1903 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ Windows 10, sürüm 1809 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌ Windows 10, sürüm 1803 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌ Windows 10, sürüm 1709 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌ Windows 10, sürüm 1703 | ❌ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ❌ Windows 10, sürüm 1607 | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌ Windows 10, sürüm 1511 | ❌ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ❌ Windows 10, sürüm 1507 | ❌ 2,1        | ❌ 3,1        | ❌ 5,0 |

## <a name="unsupported-releases"></a>Desteklenmeyen yayınlar

Aşağıdaki .NET sürümleri ❌ artık desteklenmemektedir. Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:

- 3,0
- 2.2
- 2,0

## <a name="runtime-information"></a>Çalışma zamanı bilgileri

Çalışma zamanı .NET ile oluşturulan uygulamaları çalıştırmak için kullanılır. Uygulama yazarı bir uygulama yayımladığında, çalışma zamanını uygulamayla birlikte dahil edebilirler. Çalışma zamanını içermiyorsa, bu kullanıcı çalışma zamanını yüklemek için kullanıcıya ait olur.

Windows 'a yükleyebileceğiniz üç farklı çalışma zamanı vardır:

*ASP.NET Core çalışma zamanı*\
ASP.NET Core uygulamalar çalıştırır. .NET çalışma zamanı içerir.

*Masaüstü çalışma zamanı*\
.NET WPF ve Windows için masaüstü uygulamaları Windows Forms çalıştırır. .NET çalışma zamanı içerir.

*.NET çalışma zamanı*\
Bu çalışma zamanı, en basit çalışma zamanı ve başka bir çalışma zamanı içermez. .NET uygulamalarıyla en iyi uyumluluk için hem *ASP.NET Core çalışma zamanını* hem de *Masaüstü çalışma zamanını* yüklemenizi öneririz.

> [!div class="button"]
> [.NET çalışma zamanını indirin](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>SDK bilgileri

SDK, .NET uygulamaları ve kitaplıkları derlemek ve yayımlamak için kullanılır. SDK 'nın [yüklenmesi üç çalışma](#runtime-information)zamanını içerir: ASP.NET Core, masaüstü ve .net.

## <a name="dependencies"></a>Bağımlılıklar

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[.NET 5,0](#tab/net50)

Aşağıdaki Windows sürümleri .NET 5,0 ile desteklenir:

> [!NOTE]
> Bir `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                  | Sürüm       | Mimariler   |
|---------------------|---------------|-----------------|
| Windows 10 Istemcisi   | Sürüm 1607 + | x64, x86, ARM64 |
| Windows İstemcisi      | 7 SP1 +, 8,1   | x64, x86        |
| Windows Server      | 2012 R2 +      | x64, x86        |
| Windows Server çekirdeği | 2012 R2 +      | x64, x86        |
| Nano Sunucu         | Sürüm 1809 + | x64             |

.NET 5,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net 5,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).

# <a name="net-core-31"></a>[.NET Core 3,1](#tab/netcore31)

Aşağıdaki Windows sürümleri .NET Core 3,1 ile desteklenir:

> [!NOTE]
> Bir `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                            | Sürüm                        | Mimariler   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows İstemcisi                | 7 SP1 +, 8,1                    | x64, x86        |
| Windows 10 Istemcisi             | Sürüm 1609 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Sunucu                   | Sürüm 1803 +                  | x64, ARM32      |

.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*.NET Core 3,0 şu anda destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:

> [!NOTE]
> Bir `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                            | Sürüm                        | Mimariler   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows İstemcisi                | 7 SP1 +, 8,1                    | x64, x86        |
| Windows 10 Istemcisi             | Sürüm 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Sunucu                   | Sürüm 1803 +                  | x64, ARM32      |

.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*.NET Core 2,2 Şu anda destek dışı. Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:

> [!NOTE]
> Bir `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                            | Sürüm                        | Mimariler   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows İstemcisi                | 7 SP1 +, 8,1                    | x64, x86        |
| Windows 10 Istemcisi             | Sürüm 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Sunucu                   | Sürüm 1803 +                   | x64, ARM32      |

.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:

> [!NOTE]
> Bir `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                            | Sürüm                        | Mimariler   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows İstemcisi                | 7 SP1 +, 8,1                    | x64, x86        |
| Windows 10 Istemcisi             | Sürüm 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Sunucu                   | Sürüm 1803 +                  | x64            |

.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2

Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız ek bağımlılıklar gereklidir:

- ❌ Windows 7 SP1
- ❌ Windows Vista SP 2
- ✔️ Windows 8.1
- ✔️ Windows Server 2008 R2
- ✔️ Windows Server 2012 R2

Aşağıdakileri yükleyerek:

- [Microsoft Visual C++ 2015 yeniden dağıtılabilir güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Aşağıdaki hatalardan birini alırsanız, önceki gereksinimler de gereklidir:

> Bilgisayarınızda *api-ms-win-crt-runtime-l1-1-0.dll* olmadığından program başlatılamıyor. Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.
>
> \- veya
>
> Bilgisayarınızda *api-ms-win-cor-timezone-l1-1-0.dll* olmadığından program başlatılamıyor. Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.
>
> \- veya
>
> Kitaplık *hostfxr.dll* bulundu, ancak *C: \\ \<path_to_app> \\hostfxr.dll* öğesinden yüklenemedi.

## <a name="install-with-powershell-automation"></a>PowerShell otomasyonu ile Install

[DotNet yükleme betikleri](../tools/dotnet-install-script.md) , CI otomasyonu ve çalışma zamanının yönetici olmayan yüklemeleri için kullanılır. Betiği, [DotNet yükleme betiği başvuru sayfasından](../tools/dotnet-install-script.md)indirebilirsiniz.

Komut dosyası, .NET 5,0 olan en son [uzun süreli destek (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) sürümünü yüklemek için varsayılan değerdir. Anahtarı belirterek belirli bir sürümü seçebilirsiniz `Channel` . `Runtime`Çalışma zamanı yüklemek için anahtarı ekleyin. Aksi halde, komut dosyası SDK 'Yı yüklüyor.

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

Anahtarı atlayarak SDK 'Yı yükler `-Runtime` . `-Channel`Bu örnekte anahtar, `Current` desteklenen en son sürümü yükleyecek şekilde olarak ayarlanır.

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a>Visual Studio ile Install

.NET uygulamaları geliştirmek için Visual Studio kullanıyorsanız, aşağıdaki tabloda hedef .NET SDK sürümü temel alınarak gerekli olan en düşük Visual Studio sürümü açıklanmaktadır.

| .NET SDK sürümü      | Visual Studio sürüm                      |
| --------------------- | ------------------------------------------ |
| 5.0                   | Visual Studio 2019 sürüm 16,8 veya üzeri. |
| 3,1                   | Visual Studio 2019 sürüm 16,4 veya üzeri. |
| 3,0                   | Visual Studio 2019 sürüm 16,3 veya üzeri. |
| 2.2                   | Visual Studio 2017 sürüm 15,9 veya üzeri. |
| 2.1                   | Visual Studio 2017 sürüm 15,7 veya üzeri. |

Visual Studio zaten yüklüyse, aşağıdaki adımlarla sürümünüzü kontrol edebilirsiniz.

01. Visual Studio'yu açın.
01. **Help**  >  **Microsoft Visual Studio hakkında** yardım seçeneğini belirleyin.
01. **Hakkında** iletişim kutusunda sürüm numarasını okuyun.

Visual Studio, en son .NET SDK ve çalışma zamanını yükleyebilir.

> [!div class="button"]
> [Visual Studio 'Yu indirin](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>İş yükü seçin

Visual Studio 'Yu yüklerken veya değiştirirken, oluşturmakta olduğunuz uygulamanın türüne bağlı olarak aşağıdaki iş yüklerinden birini veya daha fazlasını seçin:

- **Diğer Toolsets** bölümünde yer alan **.NET Core platformlar arası geliştirme** iş yükü.
- **Web & bulut** bölümündeki **ASP.net ve Web geliştirme** iş yükü.
- **Web & bulut** bölümündeki **Azure geliştirme** iş yükü.
- **Masaüstü & mobil** bölümündeki **.net masaüstü geliştirme** iş yükü.

[![.NET Core iş yüküne sahip Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>Visual Studio Code birlikte yüklemeyi

Visual Studio Code, masaüstünüzde çalışan güçlü ve hafif bir kaynak kod düzenleyicisidir. Visual Studio Code Windows, macOS ve Linux için kullanılabilir.

Visual Studio Code, Visual Studio gibi otomatikleştirilmiş bir .NET Core yükleyicisi ile birlikte gelmediğinden, .NET Core desteği eklemek basittir.

01. [Visual Studio Code indirin ve yükleyin](https://code.visualstudio.com/Download).
01. [.NET Core SDK indirin ve yükleyin](https://dotnet.microsoft.com/download/dotnet-core).
01. [Visual Studio Code marketi 'Nden C# uzantısını yükler](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

## <a name="download-and-manually-install"></a>İndirme ve el ile yükleme

.NET için Windows yükleyicilerine alternatif olarak SDK veya çalışma zamanını indirip el ile yükleyebilirsiniz. El ile yüklemeyi, genellikle sürekli tümleştirme testinin bir parçası olarak gerçekleştirilir. Bir geliştirici veya Kullanıcı için genellikle bir [Yükleyici](https://dotnet.microsoft.com/download/dotnet-core)kullanmak daha iyidir.

Hem .NET SDK hem de .NET çalışma zamanı indirildikten sonra el ile yüklenebilir. .NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez. İlk olarak, aşağıdaki sitelerden birinden SDK veya çalışma zamanı için ikili bir sürüm indirin:

- ✔️ [.net 5,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.NET Core 3,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Tüm .NET Core İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core)

Örneğin, .NET ' i ayıklamak için bir dizin oluşturun `%USERPROFILE%\dotnet` . Ardından, indirilen ZIP dosyasını bu dizine ayıklayın.

Varsayılan olarak, .NET CLı komutları ve uygulamaları bu şekilde .NET kullanmaz ve açıkça bunu kullanmayı tercih etmeniz gerekir. Bunu yapmak için, bir uygulamanın başlatıldığı ortam değişkenlerini değiştirin:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

Bu yaklaşım, farklı konumlara birden çok sürüm yüklemenize olanak sağlar ve ardından uygulamayı o konuma işaret eden ortam değişkenleriyle çalıştırarak uygulamanın kullanması gereken yüklemeyi açıkça seçebilirsiniz.

`DOTNET_MULTILEVEL_LOOKUP`, Olarak ayarlandığında `0` , .net, genel olarak yüklenmiş tüm .NET sürümlerini yoksayar. Uygulamayı çalıştırmak için en iyi çerçeveyi seçerken .NET 'in varsayılan genel yüklemesi konumunu düşünbilmesine izin vermek için bu ortam ayarını kaldırın. Varsayılan değer genellikle `C:\Program Files\dotnet` yükleyicilerin .net yüklemesi ' nin bulunduğu yerdir.

## <a name="docker"></a>Docker

Kapsayıcılar, uygulamanızı ana bilgisayar sisteminin geri kalanından yalıtmak için basit bir yol sağlar. Aynı makinedeki kapsayıcılar yalnızca çekirdeği paylaşır ve uygulamanıza verilen kaynakları kullanır.

.NET, bir Docker kapsayıcısında çalıştırılabilir. Resmi .NET Docker görüntüleri Microsoft Container Registry (MCR) ' de yayımlanır ve [Microsoft .net Docker Hub deposunda](https://hub.docker.com/_/microsoft-dotnet)bulunabilir. Her depo, .NET (SDK veya çalışma zamanı) ve kullanabileceğiniz farklı .NET birleşimlerinin görüntülerini içerir.

Microsoft, belirli senaryolar için uyarlanmış görüntüler sağlar. Örneğin, [ASP.NET Core deposu](https://hub.docker.com/_/microsoft-dotnet-aspnet) üretimde ASP.NET Core uygulamaları çalıştırmak için oluşturulmuş görüntüler sağlar.

Bir Docker kapsayıcısında .NET kullanımı hakkında daha fazla bilgi için bkz. [.net ve Docker](../docker/introduction.md) ve [örneklere](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)giriş.

## <a name="next-steps"></a>Sonraki adımlar

- [.Net 'in zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md?pivots=os-windows).
- [Öğretici: Merhaba Dünya öğreticisi](../tutorials/with-visual-studio.md).
- [Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).
- [Öğretici: bir .NET Core uygulamasını Kapsayıize](../docker/build-container.md)edin.
