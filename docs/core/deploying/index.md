---
title: Uygulama yayımlama
description: .NET uygulaması yayımlama yolları hakkında bilgi edinin. .NET, platforma özgü veya platformlar arası uygulamalar yayımlayabilir. Bir uygulamayı, kendi içinde veya Framework 'e bağımlı olarak yayımlayabilirsiniz. Her mod, bir kullanıcının uygulamanızı nasıl yürüttüğünde etkiler.
ms.date: 02/05/2021
ms.openlocfilehash: ca0fa4ff5e17a3fa4c636604ae81b63ffbbc99f6
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874296"
---
# <a name="net-application-publishing-overview"></a>.NET uygulama yayımlamaya genel bakış

.NET ile oluşturduğunuz uygulamalar iki farklı modda yayımlanabilir ve bu mod, bir kullanıcının uygulamanızı nasıl yürüttüğünde de etkili olur.

Uygulamanızı *kendi içinde* yayımlamak, .NET çalışma zamanı ve kitaplıklarını ve uygulamanızı ve onun bağımlılıklarını içeren bir uygulama oluşturur. Uygulamanın kullanıcıları bu uygulamayı .NET çalışma zamanı yüklü olmayan bir makinede çalıştırabilir.

Uygulamanızı *çerçeveye bağlı* olarak yayımlamak, yalnızca uygulamanızın kendisini ve bağımlılıklarını içeren bir uygulama oluşturur. Uygulamanın kullanıcılarının .NET çalışma zamanını ayrı olarak yüklemesi gerekir.

Her iki yayımlama modu, varsayılan olarak platforma özgü bir yürütülebilir dosya oluşturur. Çerçeveye bağımlı uygulamalar yürütülebilir bir dosya olmadan oluşturulabilir ve bu uygulamalar platformlar arası bir platformdur.

Bir yürütülebilir dosya üretildiğinde, hedef platformu bir çalışma zamanı tanımlayıcısı (RID) ile belirtebilirsiniz. RID 'Ler hakkında daha fazla bilgi için bkz. [.net RID Catalog](../rid-catalog.md).

Aşağıdaki tabloda, bir uygulamayı, SDK sürümü başına çerçeveye bağımlı veya şirket içinde yayımlamak için kullanılan komutlar özetlenmektedir:

| Tür                                                                                     | SDK 2.1 | SDK 3,1 | SDK 5,0 | Komut |
| ---------------------------------------------------------------------------------------  | ------- | ------- | ------- | ------- |
| geçerli platform için [çerçeveye bağımlı yürütülebilir dosya](#publish-framework-dependent) . |         | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| belirli bir platform için [çerçeveye bağımlı yürütülebilir dosya](#publish-framework-dependent) .  |         | ✔️      | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [çerçeveye bağımlı platformlar arası ikili](#publish-framework-dependent).               | ✔️      | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [kendi kendine içerilen çalıştırılabilir](#publish-self-contained).                                    | ✔️      | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

Daha fazla bilgi için bkz. [.net DotNet Publish komutu](../tools/dotnet-publish.md).

## <a name="produce-an-executable"></a>Yürütülebilir bir dosya oluşturun

Yürütülebilir dosyalar platformlar arası değildir. Bunlar bir işletim sistemine ve CPU mimarisine özgüdür. Uygulamanızı yayımlarken ve yürütülebilir bir dosya oluştururken, uygulamayı [kendi içinde](#publish-self-contained) veya [çerçeveye bağımlı](#publish-framework-dependent)olarak yayımlayabilirsiniz. Bir uygulamayı kendi içinde yayımlamak uygulamayla birlikte .NET çalışma zamanını içerir ve uygulamanın kullanıcıları uygulamayı çalıştırmadan önce .NET yükleme konusunda endişelenmenize gerek kalmaz. Framework 'e bağımlı olarak yayımlanan uygulamalar .NET çalışma zamanı ve kitaplıklarını içermez; yalnızca uygulama ve üçüncü taraf bağımlılıklar dahil edilir.

Aşağıdaki komutlar yürütülebilir bir dosya üretir:

| Tür                                                                                     | SDK 2.1 | SDK 3,1 | SDK 5,0 | Komut |
| ---------------------------------------------------------------------------------------- | ------- | ------- | ------- | ------- |
| geçerli platform için [çerçeveye bağımlı yürütülebilir dosya](#publish-framework-dependent) . |         | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| belirli bir platform için [çerçeveye bağımlı yürütülebilir dosya](#publish-framework-dependent) .  |         | ✔️      | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [kendi kendine içerilen çalıştırılabilir](#publish-self-contained).                                    | ✔️      | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>Platformlar arası ikili oluşturun

Uygulamanızı, bir *DLL* dosyası biçiminde [çerçeveye bağımlı](#publish-framework-dependent)olarak yayımladığınızda platformlar arası ikili dosyalar oluşturulur. *DLL* dosyası projenizden sonra adlandırılır. Örneğin, **word_reader** adlı bir uygulamanız varsa, *word_reader.dll* adlı bir dosya oluşturulur. Bu şekilde yayımlanan uygulamalar `dotnet <filename.dll>` komutla çalışır ve herhangi bir platformda çalıştırılabilir.

Platformlar arası ikili dosyalar, hedeflenen .NET çalışma zamanı zaten yüklü olduğu sürece herhangi bir işletim sisteminde çalıştırılabilir. Hedeflenen .NET çalışma zamanı yüklü değilse, uygulama geri almak üzere yapılandırıldıysa, uygulama daha yeni bir çalışma zamanı kullanılarak çalıştırılabilir. Daha fazla bilgi için bkz. [çerçeveye bağımlı uygulamalar ileri alma](../versions/selection.md#framework-dependent-apps-roll-forward).

Aşağıdaki komut platformlar arası ikili dosya üretir:

| Tür                                                                                 | SDK 2.1 | SDK 3. x | SDK 5,0 | Komut |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- | ------- |
| [çerçeveye bağımlı platformlar arası ikili](#publish-framework-dependent).           | ✔️      | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-framework-dependent"></a>Yayımla çerçevesi-bağımlı

Framework 'e bağımlı olarak yayımlanan uygulamalar platformlar arası ve .NET çalışma zamanı dahil değildir. Uygulamanızın kullanıcısı .NET çalışma zamanını yüklemek için gereklidir.

Bir uygulamayı Framework 'e bağımlı olarak yayımlamak, *DLL* dosyası olarak [platformlar arası bir ikili](#produce-a-cross-platform-binary) dosya ve geçerli platformunuzu hedefleyen [platforma özgü bir yürütülebilir](#produce-an-executable) dosya oluşturur. Yürütülebilir dosya olmadığından, *DLL* platformlar arası bir platformdur. Örneğin, **word_reader** ve hedef pencereleri adlı bir uygulama yayımlarsanız, *word_reader.dll* birlikte *word_reader.exe* yürütülebilir dosyası oluşturulur. Linux veya macOS hedeflenirken, *word_reader.dll* birlikte *word_reader* çalıştırılabilir dosyası oluşturulur. RID 'Ler hakkında daha fazla bilgi için bkz. [.net RID Catalog](../rid-catalog.md).

> [!IMPORTANT]
> .NET SDK 2,1, bir uygulama altyapısına bağımlı yayımladığınızda platforma özgü yürütülebilir dosyalar oluşturmaz.

Uygulamanızın platformlar arası ikili dosyası, `dotnet <filename.dll>` komutla çalıştırılabilir ve herhangi bir platformda çalıştırılabilir. Uygulama platforma özgü uygulamalar içeren bir NuGet paketi kullanıyorsa, tüm platformların bağımlılıkları uygulamayla birlikte yayımlama klasörüne kopyalanır.

Parametreleri komuta geçirerek belirli bir platform için yürütülebilir bir dosya oluşturabilirsiniz `-r <RID> --self-contained false` [`dotnet publish`](../tools/dotnet-publish.md) . `-r`Parametresi atlandığında, geçerli platformunuz için yürütülebilir bir dosya oluşturulur. Hedeflenen platform için platforma özgü bağımlılıklara sahip tüm NuGet paketleri Yayımla klasörüne kopyalanır. Bir Platto 'a özgü yürütülebilir dosya gerekmiyorsa `<UseAppHost>False</UseAppHost>` Proje dosyasında belirtebilirsiniz. Daha fazla bilgi için bkz. [.NET SDK projeleri Için MSBuild başvurusu](../project-sdk/msbuild-props.md#useapphost).

### <a name="advantages"></a>Avantajlar

- **Küçük dağıtım**\
Yalnızca uygulamanız ve bağımlılıkları dağıtılır. .NET çalışma zamanı ve kitaplıkları Kullanıcı tarafından yüklenir ve tüm uygulamalar çalışma zamanını paylaşır.

- **Platformlar arası**\
Uygulamanız ve herhangi bir. AĞ tabanlı kitaplık diğer işletim sistemlerinde çalışır. Uygulamanız için bir hedef platform tanımlamanız gerekmez. .NET dosya biçimi hakkında daha fazla bilgi için bkz. [.NET derleme dosyası biçimi](../../standard/assembly/file-format.md).

- **En son düzeltme eki uygulanmış çalışma zamanını kullanır**\
Uygulama, hedef sistemde yüklü olan en son çalışma zamanını (.NET 'in hedeflenen ana alt ailesi içinde) kullanır. Bu, uygulamanızın .NET çalışma zamanının en son düzeltme eki uygulanmış sürümünü otomatik olarak kullandığı anlamına gelir. Bu varsayılan davranış geçersiz kılınabilir. Daha fazla bilgi için bkz. [çerçeveye bağımlı uygulamalar ileri alma](../versions/selection.md#framework-dependent-apps-roll-forward).

### <a name="disadvantages"></a>Dezavantajlar

- **Çalışma zamanının önceden yüklenmesini gerektirir**\
Uygulamanız yalnızca uygulama hedeflerinizin .NET sürümü konak sisteminde zaten yüklüyse çalıştırılabilir. Uygulama için, belirli bir .NET sürümü gerektiren veya daha yeni bir .NET sürümüne izin veren dağıtım iletme davranışını yapılandırabilirsiniz. Daha fazla bilgi için bkz. [çerçeveye bağımlı uygulamalar ileri alma](../versions/selection.md#framework-dependent-apps-roll-forward).

- **.NET değişebilir**\
.NET çalışma zamanı ve kitaplıklarının uygulamanın çalıştırıldığı makinede güncellenmesi mümkündür. Nadir durumlarda, çoğu uygulamanın yapabileceği .NET kitaplıklarını kullanırsanız, bu durum uygulamanızın davranışını değiştirebilir. Uygulamanızın .NET 'in daha yeni sürümlerini nasıl kullandığını yapılandırabilirsiniz. Daha fazla bilgi için bkz. [çerçeveye bağımlı uygulamalar ileri alma](../versions/selection.md#framework-dependent-apps-roll-forward).

Aşağıdaki dezavantajı yalnızca .NET Core 2,1 SDK için geçerlidir.

- **`dotnet`Uygulamayı başlatmak için komutunu kullanın**\
Kullanıcıların `dotnet <filename.dll>` uygulamanızı başlatması için komutunu çalıştırmaları gerekir. .NET Core 2,1 SDK, Framework 'e bağımlı olan uygulamalar için platforma özel yürütülebilir dosyalar üretmez.

### <a name="examples"></a>Örnekler

Uygulama çoklu platform altyapısına bağımlı yayımlayın. Geçerli platformunuzu hedefleyen bir yürütülebilir dosya *DLL* dosyası ile birlikte oluşturulur.

```dotnet
dotnet publish
```

Uygulama çoklu platform altyapısına bağımlı yayımlayın. Linux 64 bit yürütülebilir dosyası, *DLL* dosyasıyla birlikte oluşturulur. Bu komut .NET Core SDK 2,1 ile çalışmıyor.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>Kendi içinde Yayımla

Uygulamanızı kendi içinde yayımlamak platforma özgü bir yürütülebilir dosya oluşturur. Çıkış yayımlama klasörü, .NET kitaplıkları ve hedef çalışma zamanı dahil olmak üzere uygulamanın tüm bileşenlerini içerir. Uygulama diğer .NET uygulamalarından yalıtılmıştır ve yerel olarak yüklenmiş bir paylaşılan çalışma zamanı kullanmaz. Uygulamanızın kullanıcısı .NET indirmek ve yüklemek için gerekli değildir.

Yürütülebilir ikili dosya belirtilen hedef platform için üretildi. Örneğin, **word_reader** adlı bir uygulamanız varsa ve Windows için kendi kendine içerilen bir yürütülebilir dosyayı yayımlarsanız, bir *word_reader.exe* dosyası oluşturulur. Linux veya macOS için yayımlama, bir *word_reader* dosyası oluşturulur. Hedef platform ve mimari, `-r <RID>` komut parametresiyle belirtilir [`dotnet publish`](../tools/dotnet-publish.md) . RID 'Ler hakkında daha fazla bilgi için bkz. [.net RID Catalog](../rid-catalog.md).

Uygulamanın platforma özgü bağımlılıklar içeren bir NuGet paketi gibi platforma özgü bağımlılıkları varsa, bunlar uygulamayla birlikte Yayımla klasörüne kopyalanır.

### <a name="advantages"></a>Avantajlar

- **Denetim .NET sürümü**\
Uygulamanız ile hangi .NET sürümünün dağıtıldığını kontrol edersiniz.

- **Platforma özgü hedefleme**\
Uygulamanızı her platform için yayımlamanız gerektiğinden uygulamanızın nerede çalışacağını bilirsiniz. .NET yeni bir platform tanısa, bu platformu hedefleyen bir sürüm yayınlayana kadar kullanıcılar uygulamanızı bu platformda çalıştıramıyoruz. Kullanıcılarınızın uygulamanızı yeni platformda çalıştırmadan önce uyumluluk sorunları için uygulamanızı test edebilirsiniz.

### <a name="disadvantages"></a>Dezavantajlar

- **Daha büyük dağıtımlar**\
Uygulamanız .NET çalışma zamanını ve tüm uygulama bağımlılıklarınızı içerdiğinden, gereken indirme boyutu ve sabit disk alanı, [çerçeveye bağlı](#publish-framework-dependent) bir sürümden daha büyük.

  > [!TIP]
  > Linux sistemlerinde dağıtımınızın boyutunu yaklaşık 28 MB ile, .NET [*Genelleştirme sabit modunu*](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md)kullanarak azaltabilirsiniz. Bu, uygulamanızı [sabit kültür](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType)gibi tüm kültürleri işleyecek şekilde zorlar.

  > [!TIP]
  > Dağıtımınızın boyutunu daha fazla azalyabilecek bir [Önizleme kırpma özelliği](trim-self-contained.md) vardır.

- **.NET sürümünü güncelleştirmek daha zordur**\
.NET çalışma zamanı (uygulamanızla birlikte dağıtılır) yalnızca uygulamanızın yeni bir sürümü serbest bırakılarak yükseltilebilir. Ancak .NET, uygulamanızın üzerinde çalıştığı makinedeki çerçeve kitaplığı için gereken kritik güvenlik düzeltme eklerini güncelleştirir. Bu güvenlik düzeltme eki senaryosuna uçtan uca doğrulamadan sorumlusunuz.

### <a name="examples"></a>Örnekler

Kendisini içeren bir uygulama yayımlayın. MacOS 64 bit yürütülebilir dosyası oluşturulur.

```dotnet
dotnet publish -r osx-x64
```

Kendisini içeren bir uygulama yayımlayın. Windows 64 bit yürütülebilir dosyası oluşturulur.

```dotnet
dotnet publish -r win-x64
```

## <a name="publish-with-readytorun-images"></a>ReadyToRun görüntüleriyle yayımlama

ReadyToRun görüntüleriyle yayımlama, uygulamanızın boyutunu artırma maliyetinde uygulamanızın başlama süresini iyileştirir. ReadyToRun ile yayımlamak için, daha fazla ayrıntı için bkz. [readytorun](ready-to-run.md) .

### <a name="advantages"></a>Avantajlar

- **Geliştirilmiş başlangıç zamanı**\
Uygulama JıT 'i çalıştırmaya daha az zaman harcaacaktır.

### <a name="disadvantages"></a>Dezavantajlar

- **Daha büyük boyut**\
Uygulama diskte daha büyük olacaktır.

### <a name="examples"></a>Örnekler

Kendisini içeren ve ReadyToRun uygulama yayımlayın. MacOS 64 bit yürütülebilir dosyası oluşturulur.

```dotnet
dotnet publish -c Release -r osx-x64 -p:PublishReadyToRun=true
```

Kendisini içeren ve ReadyToRun uygulama yayımlayın. Windows 64 bit yürütülebilir dosyası oluşturulur.

```dotnet
dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
```

## <a name="see-also"></a>Ayrıca bkz.

- [.Net CLı ile .NET uygulamaları dağıtma.](deploy-with-cli.md)
- [Visual Studio ile .NET uygulamaları dağıtma.](deploy-with-vs.md)
- [.NET çalışma zamanı tanımlayıcısı (RID) kataloğu.](../rid-catalog.md)
- [Kullanılacak .NET sürümünü seçin.](../versions/selection.md)
