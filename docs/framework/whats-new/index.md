---
title: .NET Framework’teki yenilikler
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
ms.openlocfilehash: 4c5c7ffcab118978baf1b2f7602f39291452d1e6
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740417"
---
# <a name="whats-new-in-the-net-framework"></a>.NET Framework’teki yenilikler

Bu makalede, .NET Framework aşağıdaki sürümlerindeki temel yeni özellikler ve geliştirmeler özetlenmektedir:

- [.NET Framework 4,8](#v48)
- [.NET Framework 4.7.2](#v472)
- [.NET Framework 4.7.1](#v471)
- [.NET Framework 4,7](#v47)
- [.NET Framework 4.6.2](#v462)
- [.NET Framework 4.6.1](#v461)
- [.NET 2015 ve .NET Framework 4,6](#v46)
- [.NET Framework 4.5.2](#v452)
- [.NET Framework 4.5.1](#v451)
- [.NET Framework 4.5](#v45)

Bu makale, her yeni özellik hakkında kapsamlı bilgi sağlamaz ve değişikliğe tabidir. .NET Framework hakkında genel bilgi için [bkz. Başlarken](../get-started/index.md). Desteklenen platformlar için bkz. [sistem gereksinimleri](../get-started/system-requirements.md). İndirme bağlantıları ve yükleme yönergeleri için bkz. [Yükleme Kılavuzu](../install/guide-for-developers.md).

> [!NOTE]
> .NET Framework ekibi, platform desteğini genişletmek ve sabit koleksiyonlar ve SıMD özellikli vektör türleri gibi yeni işlevsellik tanıtmak için NuGet ile bant dışı özellikleri de serbest bırakır. Daha fazla bilgi için bkz. [Ek sınıf kitaplıkları ve API 'ler](../additional-apis/index.md) ve [.NET Framework ve bant dışı yayınlar](../get-started/the-net-framework-and-out-of-band-releases.md).
> .NET Framework için [NuGet paketlerinin tüm listesini](https://www.nuget.org/profiles/dotnetframework) görüntüleyin.

<a name="v48" />

## <a name="introducing-net-framework-48"></a>.NET Framework 4,8 tanıtımı

.NET Framework 4,8, çok kararlı bir ürünün geri kalanında birçok yeni düzeltme ve birkaç yeni özellik ekleyerek .NET Framework 4. x ' in önceki sürümlerinde oluşturulur.

### <a name="downloading-and-installing-net-framework-48"></a>.NET Framework 4,8 indiriliyor ve yükleniyor

.NET Framework 4,8 ' i şu konumlardan indirebilirsiniz:

- [.NET Framework 4,8 Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=2085155)

- [NET Framework 4,8 çevrimdışı yükleyicisi](https://go.microsoft.com/fwlink/?linkid=2088631)

.NET Framework 4,8, Windows 10, Windows 8.1, Windows 7 SP1 ve Windows Server 2008 R2 SP1 ile başlayan karşılık gelen sunucu platformları üzerine yüklenebilir. Web yükleyicisini veya çevrimdışı yükleyiciyi kullanarak .NET Framework 4,8 ' ü yükleyebilirsiniz. Çoğu kullanıcı için önerilen yöntem web yükleyicisini kullanmaktır.

[.NET Framework 4,8 Geliştirici paketini](https://go.microsoft.com/fwlink/?LinkId=2085167)yükleyerek Visual Studio 2012 veya sonraki sürümlerde .NET Framework 4,8 ' i hedefleyebilirsiniz.

### <a name="whats-new-in-net-framework-48"></a>.NET Framework 4,8 ' deki yenilikler

.NET Framework 4,8 aşağıdaki alanlarda yeni özellikler sunar:

- [Temel sınıflar](#core48)
- [Windows Communication Foundation (WCF)](#wcf48)
- [Windows Presentation Foundation (WPF)](#wpf48)
- [Ortak dil çalışma zamanı](#clr48)

Bir uygulamanın yardımcı teknoloji kullanıcıları için uygun bir deneyim sağlamasına izin veren iyileştirilmiş erişilebilirlik, .NET Framework 4,8 ' nin önemli bir odağında devam etmektedir. .NET Framework 4,8 ' deki erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için [.NET Framework erişilebilirlik](whats-new-in-accessibility.md)yenilikleri bölümüne bakın.

<a name="core48" />

#### <a name="base-classes"></a>Temel sınıflar

**Şifrelemeye göre daha az FIPS etkisi**. .NET Framework önceki sürümlerinde, <xref:System.Security.Cryptography.SHA256Managed> gibi yönetilen şifreleme sağlayıcısı sınıfları, Sistem şifreleme kitaplıkları "FIPS modunda" yapılandırıldığında bir <xref:System.Security.Cryptography.CryptographicException> oluşturur. Bu özel durumlar, Sistem şifreleme kitaplıklarının aksine, şifreleme sağlayıcısı sınıflarının yönetilen sürümlerinin FIPS (Federal bilgi Işleme standartları) 140-2 sertifikası olmadığı için oluşturulur. Bazı geliştiricilerin geliştirme makineleri FIPS modunda olduğundan, özel durumlar genellikle üretim sistemlerinde oluşturulur.

.NET Framework 4,8 ' i hedefleyen uygulamalarda varsayılan olarak, aşağıdaki yönetilen şifreleme sınıfları artık bu durumda bir <xref:System.Security.Cryptography.CryptographicException> oluşturmaz:

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

Bunun yerine, bu sınıflar şifreleme işlemlerini bir sistem şifreleme kitaplığına yönlendirir. Bu değişiklik, geliştirici ortamları ve üretim ortamları arasındaki kafa karıştırıcı bir farkı etkili bir şekilde kaldırır ve yerel bileşenlerin ve yönetilen bileşenlerin aynı şifreleme ilkesi altında çalışmasını sağlar. Bu özel durumlara bağımlı uygulamalar, AppContext anahtar `Switch.System.Security.Cryptography.UseLegacyFipsThrow` `true`olarak ayarlayarak önceki davranışı geri yükleyebilir. Daha fazla bilgi için bkz. [yönetilen şifreleme SıNıFLARı FIPS modunda Cryptographyıexception](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode)oluşturmaz.

**ZLib 'in güncelleştirilmiş sürümünün kullanımı**

.NET Framework 4,5 ' den başlayarak, clrcompression. dll derlemesi, söndür algoritma için bir uygulama sağlamak üzere veri sıkıştırma için yerel bir dış kitaplık olan [zlib](https://www.zlib.net)'i kullanır. .NET Framework 4,8, clrcompression. dll, çeşitli temel geliştirmeler ve düzeltmeler içeren ZLib sürüm 1.2.11 kullanacak şekilde güncelleştirilir.

<a name="wcf48" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

**ServiceHealthBehavior 'a giriş**

Sistem durumu uç noktaları, Hizmetleri sistem durumlarına göre yönetmek için Orchestration araçları tarafından yaygın olarak kullanılır. Sistem durumu denetimleri, bir hizmetin kullanılabilirliği ve performansı hakkında bildirimler izlemek ve bu bildirimleri sağlamak için izleme araçları tarafından da kullanılabilir.

**Servicehealthbehavior** , <xref:System.ServiceModel.Description.IServiceBehavior>GENIŞLETEN bir WCF hizmeti davranışıdır.  <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> koleksiyonuna eklendiğinde, bir hizmet davranışı şunları yapar:

- HTTP yanıt kodlarıyla hizmet sistem durumu döndürür. Bir HTTP/GET Health araştırma isteği için HTTP durum kodunu bir sorgu dizesinde belirtebilirsiniz.

- Hizmet durumu hakkında bilgi yayımlar. Hizmet durumu, kısıtlama sayısı ve kapasite dahil olmak üzere hizmete özgü ayrıntılar `?health` sorgu dizesiyle bir HTTP/GET isteği kullanılarak görüntülenebilir. Bu tür bilgilere erişim kolaylığı, hatalı bir WCF hizmeti sorunlarını giderirken önemlidir.

Sistem durumu uç noktasını açığa çıkarmak ve WCF hizmeti durum bilgilerini yayımlamak için iki yol vardır:

- Kod üzerinden. Örneğin:

  ```csharp
  ServiceHost host = new ServiceHost(typeof(Service1),
                     new Uri("http://contoso:81/Service1"));
  ServiceHealthBehavior healthBehavior =
      host.Description.Behaviors.Find<ServiceHealthBehavior>();
  healthBehavior ??= new ServiceHealthBehavior();
  host.Description.Behaviors.Add(healthBehavior);
  ```

  ```vb
  Dim host As New ServiceHost(GetType(Service1),
              New Uri("http://contoso:81/Service1"))
  Dim healthBehavior As ServiceHealthBehavior =
     host.Description.Behaviors.Find(Of ServiceHealthBehavior)()
  If healthBehavior Is Nothing Then
     healthBehavior = New ServiceHealthBehavior()
  End If
  host.Description.Behaviors.Add(healthBehavior)
  ```

- Bir yapılandırma dosyası kullanarak. Örneğin:

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

Hizmetin sistem durumu, `OnServiceFailure`, `OnDispatcherFailure`, `OnListenerFailure`, `OnThrottlePercentExceeded`) gibi sorgu parametreleri kullanılarak sorgulanabilir ve her sorgu parametresi için bir HTTP yanıt kodu belirtilebilir. Bir sorgu parametresi için HTTP yanıt kodu atlanırsa, varsayılan olarak bir 503 HTTP yanıt kodu kullanılır. Örneğin:

- OnServiceFailure: `https://contoso:81/Service1?health&OnServiceFailure=450`

  ServiceHost olduğunda bir 450 HTTP yanıt durum kodu döndürülür. [durum](xref:System.ServiceModel.Channels.CommunicationObject.State) <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>'den büyük.
Sorgu parametreleri ve örnekleri:

- OnDispatcherFailure: `https://contoso:81/Service1?health&OnDispatcherFailure=455`

  Bir 455 HTTP yanıt durum kodu, kanal sevkiyatlarından birinin durumu <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>daha büyükse döndürülür.

- OnListenerFailure: `https://contoso:81/Service1?health&OnListenerFailure=465`

  Kanal dinleyicilerinin herhangi birinin durumu <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>daha büyükse, 465 HTTP yanıt durum kodu döndürülür.

- Onthrottleyüztexcebaşında: `https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`

  Yanıtı tetikleyen {1 – 100} yüzdesini ve {200 – 599} HTTP yanıt kodunu belirtir. Bu örnekte:

  - Yüzde 95 ' den büyükse, bir 500 HTTP yanıt kodu döndürülür.

  - Yüzde veya 70 ile 95 arasında bir değer döndürülürse, 350 döndürülür.

  - Aksi takdirde, 200 döndürülür.

Hizmet sistem durumu, `https://contoso:81/Service1?health&Xml`gibi bir sorgu dizesi belirterek, `https://contoso:81/Service1?health` veya XML gibi bir sorgu dizesi belirterek HTML içinde görüntülenebilir. `https://contoso:81/Service1?health&NoContent` gibi bir sorgu dizesi boş bir HTML sayfası döndürüyor.

<a name="wpf48" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Yüksek DPı geliştirmeleri**

.NET Framework 4,8 ' de WPF, Monitor v2 DPı tanıma ve karma mod DPı ölçeklendirme için destek ekler. Yüksek DPı geliştirmesi hakkında daha fazla bilgi için bkz. [Windows üzerinde yüksek DPI masaüstü uygulaması geliştirme](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) .

.NET Framework 4,8, karma mod DPı ölçeklendirmesini (Windows 10 Nisan 2018 ' den başlayarak) destekleyen platformlar üzerindeki yüksek DPı WPF uygulamalarında barındırılan HWNDs ve Windows Forms birlikte çalışabilirlik desteğini geliştirir. Barındırılan HWNDs veya Windows Forms denetimleri [Setthreaddpihostingbehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) ve [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext)çağırarak karışık modlu DPI ölçekli pencereler olarak oluşturulduysa, her bir Monitor v2 WPF uygulamasında barındırılabilir ve uygun şekilde boyutlandırılabilir ve ölçeklenirler. Bu tür barındırılan içerikler yerel DPı 'de işlenmez; Bunun yerine, işletim sistemi barındırılan içeriği uygun boyuta ölçeklendirir. Monitör başına v2 DPı tanıma moduna yönelik destek Ayrıca, WPF denetimlerinin yüksek DPı uygulamasındaki yerel bir pencerede barındırılmasına (yani, üstü olarak) olanak tanır.

Karma mod yüksek DPı ölçeklendirme desteğini etkinleştirmek için aşağıdaki [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarlarını uygulama yapılandırma dosyasına ayarlayabilirsiniz:

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48" />

#### <a name="common-language-runtime"></a>Ortak dil çalışma zamanı

.NET Framework 4,8 ' deki çalışma zamanı aşağıdaki değişiklikleri ve geliştirmeleri içerir:

**JIT derleyicisi geliştirmeleri**. .NET Framework 4,8 ' deki tam zamanında (JıT) derleyici .NET Core 2,1 ' de JıT derleyicisine dayanır. .NET Core 2,1 JıT derleyicisi üzerinde yapılan en iyileştirmelerin ve tüm hata düzeltmelerinin çoğu, .NET Framework 4,8 JıT derleyicisine dahildir.

**Ngen geliştirmeleri**. Çalışma zamanı, [Yerel Görüntü Oluşturucu](../tools/ngen-exe-native-image-generator.md) (NGen) görüntüleri için bellek yönetimini iyileştirmiştir, bu sayede Ngen görüntülerinden eşlenen verilerin bellekte yerleşik olmaması sağlanır. Bu, yürütülecek belleği değiştirerek bu yüzey alanını rastgele kodu yürütmeye çalışacak saldırılara karşı azaltır.

**Tüm derlemeler Için kötü amaçlı yazılımdan koruma taraması**. .NET Framework önceki sürümlerinde, çalışma zamanı, Windows Defender ya da üçüncü taraf kötü amaçlı yazılımdan koruma yazılımı kullanarak diskten yüklenen tüm derlemeleri tarar. Ancak, <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> yöntemi gibi diğer kaynaklardan yüklenen derlemeler taranmaz ve olası algılanabilecek kötü amaçlı yazılımları içerebilir. Windows 10 ' da çalışan .NET Framework 4,8 ' den itibaren, çalışma zamanı [kötü amaçlı yazılımdan koruma taraması arabirimini (AMSı)](/windows/desktop/AMSI/antimalware-scan-interface-portal)uygulayan kötü amaçlı yazılımdan koruma çözümleri tarafından bir taramayı tetikler

<a name="v472" />

## <a name="whats-new-in-net-framework-472"></a>.NET Framework 4.7.2 yenilikleri

.NET Framework 4.7.2, aşağıdaki alanlardaki yeni özellikler içerir:

- [Temel sınıflar](#core-472)
- [ASP.NET](#asp-net472)
- [Ağ](#net472)
- [SQL](#sql472)
- [WPF](#wpf472)
- [ClickOnce](#clickonce)

.NET Framework 4.7.2 ' ye odaklanmaya devam etmek, bir uygulamanın yardımcı teknoloji kullanıcıları için uygun bir deneyim sağlamasına olanak tanıyan bir uygulamadır. .NET Framework 4.7.2 ' deki erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için [.NET Framework erişilebilirlik](whats-new-in-accessibility.md)yenilikleri bölümüne bakın.

<a name="core-472" />

#### <a name="base-classes"></a>Temel sınıflar

.NET Framework 4.7.2, çok sayıda şifreleme geliştirmesi, ZIP arşivleri için daha iyi açma desteği ve ek koleksiyon API 'Leri sunar.

**Yeni RSA aşırı yüklemeleri. Ve DSA oluştur. Oluşturma**

<xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> yöntemleri, yeni bir <xref:System.Security.Cryptography.DSA> veya <xref:System.Security.Cryptography.RSA> anahtar örneği oluşturulurken anahtar parametreleri sunmanıza olanak tanır. Bunlar, aşağıdaki gibi bir kod değiştirmenizi sağlar:

```csharp
// Before .NET Framework 4.7.2
using (RSA rsa = RSA.Create())
{
   rsa.ImportParameters(rsaParameters);
   // Other code to execute using the RSA instance.
}
```

```vb
' Before .NET Framework 4.7.2
Using rsa = RSA.Create()
   rsa.ImportParameters(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
```

Şu şekilde kodla:

```csharp
// Starting with .NET Framework 4.7.2
using (RSA rsa = RSA.Create(rsaParameters))
{
   // Other code to execute using the rsa instance.
}
```

```vb
' Starting with .NET Framework 4.7.2
Using rsa = RSA.Create(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
```

<xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> yöntemleri, belirli bir anahtar boyutuyla yeni <xref:System.Security.Cryptography.DSA> veya <xref:System.Security.Cryptography.RSA> anahtarları oluşturmanıza olanak sağlar. Örneğin:

```csharp
using (DSA dsa = DSA.Create(2048))
{
   // Other code to execute using the dsa instance.
}
```

```vb
Using dsa = DSA.Create(2048)
   ' Other code to execute using the dsa instance.
End Using
```

**Rfc2898DeriveBytes oluşturucular bir karma algoritma adı kabul eder**

<xref:System.Security.Cryptography.Rfc2898DeriveBytes> sınıfı, anahtarları türetmede kullanılacak HMAC algoritmasını tanımlayan bir <xref:System.Security.Cryptography.HashAlgorithmName> parametresine sahip üç yeni oluşturucuya sahiptir. Geliştiriciler, SHA-1 kullanmak yerine, aşağıdaki örnekte gösterildiği gibi SHA-256 gibi bir SHA-2 tabanlı HMAC kullanmalıdır:

```csharp
private static byte[] DeriveKey(string password, out int iterations, out byte[] salt,
                                out HashAlgorithmName algorithm)
{
   iterations = 100000;
   algorithm = HashAlgorithmName.SHA256;

   const int SaltSize = 32;
   const int DerivedValueSize = 32;

   using (Rfc2898DeriveBytes pbkdf2 = new Rfc2898DeriveBytes(password, SaltSize,
                                                             iterations, algorithm))
   {
      salt = pbkdf2.Salt;
      return pbkdf2.GetBytes(DerivedValueSize);
   }
}
```

```vb
Private Shared Function DeriveKey(password As String, ByRef iterations As Integer,
                                  ByRef salt AS Byte(), ByRef algorithm As HashAlgorithmName) As Byte()
   iterations = 100000
   algorithm = HashAlgorithmName.SHA256

   Const SaltSize As Integer = 32
   Const  DerivedValueSize As Integer = 32

   Using pbkdf2 = New Rfc2898DeriveBytes(password, SaltSize, iterations, algorithm)
      salt = pbkdf2.Salt
      Return pbkdf2.GetBytes(DerivedValueSize)
   End Using
End Function
```

**Kısa ömürlü anahtarlar için destek**

PFX içeri aktarma isteğe bağlı olarak, sabit sürücüyü atlayarak özel anahtarları doğrudan bellekten yükleyebilir. Yeni <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> bayrağı bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> oluşturucuda veya <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> yönteminin aşırı yüklerinden birinde belirtildiğinde, özel anahtarlar kısa ömürlü anahtarlar olarak yüklenir. Bu, anahtarların diskte görünmesini önler. Ancak

- Anahtarlar diske kalıcı olmadığından, bu bayrağıyla yüklenen sertifikalar bir X509Store eklemek için iyi aday değildir.

- Bu şekilde yüklenen anahtarlar neredeyse her zaman Windows CNG aracılığıyla yüklenir. Bu nedenle, çağıranlar, CERT gibi uzantı yöntemlerini çağırarak özel anahtara erişmelidir [. GetRSAPrivateKey ()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A). <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> özelliği çalışmıyor.

- Eski <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> özelliği sertifikalarla çalışmadıklarından, geliştiricilerin kısa ömürlü anahtarlara geçmeden önce ciddi testler gerçekleştirmesi gerekir.

**PKCS # 10 sertifika imzalama istekleri ve X. 509.440 ortak anahtar sertifikalarının programlı bir şekilde oluşturulması**

.NET Framework 4.7.2 ' den itibaren, iş yükleri sertifika imzalama istekleri (CSR) oluşturabilir ve bu da sertifika isteği oluşturma 'nın var olan araç halinde hazırlanmasını sağlar. Bu, genellikle test senaryolarında yararlı olur.

Daha fazla bilgi ve kod örnekleri için [.net blogda](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/)"PKCS # 10 sertifika imzalama Isteklerinin ve X. 509.440 ortak anahtar sertifikalarının programlı oluşturulması" başlığına bakın.

**Yeni SignerInfo üyeleri**

.NET Framework 4.7.2 ile başlayarak, <xref:System.Security.Cryptography.Pkcs.SignerInfo> sınıfı imza hakkında daha fazla bilgi sunar. İmzalayan tarafından kullanılan imza algoritmasını belirleyebilmek için <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> özelliğinin değerini alabilirsiniz. <xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType>, bu imzalayan için şifreleme imzasının bir kopyasını almak üzere çağrılabilir.

**CryptoStream atıldıktan sonra sarmalanmış bir akışın açılmasını bırakma**

.NET Framework 4.7.2 ile başlayarak, <xref:System.Security.Cryptography.CryptoStream> sınıfının sarmalanmış akışı kapatmadığından <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> izin veren ek bir Oluşturucusu vardır. <xref:System.Security.Cryptography.CryptoStream> örneği atıldıktan sonra kaydırılmış akışı açık bırakmak için, yeni <xref:System.Security.Cryptography.CryptoStream> oluşturucusunu aşağıdaki gibi çağırın:

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

**DeflateStream 'de değişiklikleri açma**

.NET Framework 4.7.2 ' den itibaren, <xref:System.IO.Compression.DeflateStream> sınıfında açma işlemlerinin uygulanması, varsayılan olarak yerel Windows API 'Lerini kullanacak şekilde değiştirilmiştir. Genellikle bu, önemli ölçüde performans geliştirmesine neden olur.

Windows API 'Leri kullanarak açma desteği, .NET Framework 4.7.2 ' i hedefleyen uygulamalar için varsayılan olarak etkinleştirilmiştir. .NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4.7.2 altında çalışan uygulamalar, uygulama yapılandırma dosyasına aşağıdaki [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ekleyerek bu davranışı kabul edebilir:

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

**Ek koleksiyon API 'Leri**

.NET Framework 4.7.2, <xref:System.Collections.Generic.SortedSet%601> ve <xref:System.Collections.Generic.HashSet%601> türlerine bir dizi yeni API ekler. Bu güncelleştirmeler şunlardır:

- diğer koleksiyon türlerinde kullanılan try modelini bu iki türe genişleten `TryGetValue` yöntemleri. Yöntemler şunlardır:

  - [Genel bool HashSet\<T >. TryGetValue (T equalValue, out gerçek değeri)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [Genel bool SortedSet\<T >. TryGetValue (T equalValue, out gerçek değeri)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- bir koleksiyonu <xref:System.Collections.Generic.HashSet%601>dönüştüren uzantı yöntemleri `Enumerable.To*`:

  - [genel statik diyez kümesi\<TSource > ToHashSet\<TSource > (Bu IEnumerable\<TSource > kaynağı)](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [ortak statik diyez kümesi\<TSource > ToHashSet\<TSource > (Bu IEnumerable\<TSource > Source, IEqualityComparer\<TSource > Comparer)](xref:System.Linq.Enumerable.ToHashSet%2A)

- Daha önce <xref:System.Collections.Generic.HashSet%601> boyutunu bildiğiniz sırada bir performans avantajı veren koleksiyonun kapasitesini ayarlamanıza olanak sağlayan yeni <xref:System.Collections.Generic.HashSet%601> oluşturucular:

  - [Genel diyez kümesi (int kapasitesi)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))
  - [ortak diyez kümesi (int kapasitesi, IEqualityComparer\<T > Comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))

<xref:System.Collections.Concurrent.ConcurrentDictionary%602> sınıfı, sözlükten bir değer almak veya bulunamadıysanız eklemek ve sözlüğe bir değer eklemek ya da zaten varsa güncelleştirmek için <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> yöntemlerinin yeni aşırı yüklerini içerir.

```csharp
public TValue AddOrUpdate<TArg>(TKey key, Func<TKey, TArg, TValue> addValueFactory, Func<TKey, TValue, TArg, TValue> updateValueFactory, TArg factoryArgument)

public TValue GetOrAdd<TArg>(TKey key, Func<TKey, TArg, TValue> valueFactory, TArg factoryArgument)
```

```vb
Public AddOrUpdate(Of TArg)(key As TKey, addValueFactory As Func(Of TKey, TArg, TValue), updateValueFactory As Func(Of TKey, TValue, TArg, TValue), factoryArgument As TArg) As TValue

Public GetOrAdd(Of TArg)(key As TKey, valueFactory As Func(Of TKey, TArg, TValue), factoryArgument As TArg) As TValue
```

<a name="asp-net472" />

#### <a name="aspnet"></a>ASP.NET

**Web Forms bağımlılık ekleme desteği**

[Bağımlılık ekleme (dı)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) nesneleri ve bağımlılıklarını ayırır, böylece bir bağımlılık değiştiği için nesnenin kodunun artık değişmesi gerekmez. .NET Framework 4.7.2 hedefleyen ASP.NET uygulamaları geliştirirken şunları yapabilirsiniz:

- [İşleyiciler ve modüller](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [sayfa örnekleri](xref:System.Web.UI.Page)ve ASP.NET Web uygulaması projelerinin [kullanıcı denetimlerinde](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) , ayarlayıcı tabanlı, arabirim tabanlı ve Oluşturucu tabanlı ekleme kullanın.

- [İşleyiciler ve modüller](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [sayfa örnekleri](xref:System.Web.UI.Page)ve ASP.NET Web sitesi projelerinin [kullanıcı denetimlerinde](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) , ayarlayıcı tabanlı ve arabirim tabanlı ekleme kullanın.

- Farklı bağımlılık ekleme çerçeveleri takın.

**Aynı site tanımlama bilgileri için destek**

[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) , bir tarayıcının bir siteler arası istekle birlikte tanımlama bilgisi göndermesini engeller. .NET Framework 4.7.2, değeri <xref:System.Web.SameSiteMode?displayProperty=nameWithType> numaralandırma üyesi olan bir <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> özelliği ekler. Değeri <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> veya <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>ise, ASP.NET, set-Cookie başlığına `SameSite` özniteliğini ekler. SameSite desteği <xref:System.Web.HttpCookie> nesneler için, <xref:System.Web.Security.FormsAuthentication> ve <xref:System.Web.SessionState> tanımlama bilgilerine de uygulanır.

<xref:System.Web.HttpCookie> nesne için SameSite ' i aşağıdaki gibi ayarlayabilirsiniz:

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

Ayrıca, Web. config dosyasını değiştirerek, uygulama düzeyinde SameSite tanımlama bilgilerini de yapılandırabilirsiniz:

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

Web yapılandırma dosyasını değiştirerek <xref:System.Web.Security.FormsAuthentication> ve <xref:System.Web.SessionState> tanımlama bilgileri için SameSite ekleyebilirsiniz:

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   <authentication />
   <sessionState cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472" />

#### <a name="networking"></a>Ağ Oluşturma

**HttpClientHandler özelliklerinin uygulanması**

.NET Framework 4.7.1 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> sınıfına sekiz özellik ekledi. Ancak, ikisi bir <xref:System.PlatformNotSupportedException>oluşturdu. .NET Framework 4.7.2 artık bu özellikler için bir uygulama sağlar. Özellikler şunlardır:

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />

#### <a name="sqlclient"></a>SQLClient

**Azure Active Directory evrensel kimlik doğrulaması ve Multi-Factor Authentication desteği**

Büyüyen uyumluluk ve güvenlik talepleri birçok müşterinin Multi-Factor Authentication (MFA) kullanmasını gerektirir. Ayrıca, geçerli en iyi uygulamalar Kullanıcı parolalarını doğrudan bağlantı dizelerine dahil etmekten kaçınarak. Bu değişiklikleri desteklemek için, 4.7.2 ve [Azure AD kimlik doğrulamasını](/azure/sql-database/sql-database-aad-authentication-configure)desteklemek üzere mevcut "Authentication" anahtar sözcüğü için yeni bir değer ekleyerek [SQLClient bağlantı dizelerini](xref:System.Data.SqlClient.SqlConnection.ConnectionString) Active Directory ".NET Framework genişletir. Yeni etkileşimli Yöntem, yerel ve Federal Azure AD kullanıcılarını ve Azure AD Konuk kullanıcılarını destekler. Bu yöntem kullanıldığında, Azure AD tarafından uygulanan MFA kimlik doğrulaması SQL veritabanları için desteklenir. Ayrıca, kimlik doğrulama işlemi, en iyi güvenlik uygulamalarına uyacak şekilde bir Kullanıcı parolası ister.

.NET Framework önceki sürümlerinde SQL bağlantısı yalnızca <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> ve <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> seçeneklerini destekliyordu. Bunların her ikisi de, MFA 'yı desteklemeyen, etkileşimli olmayan [adal protokolünün](/azure/active-directory/develop/active-directory-authentication-libraries)bir parçasıdır. Yeni <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> seçeneğiyle, SQL bağlantısı MFA 'yı ve mevcut kimlik doğrulama yöntemlerini (parola ve tümleşik kimlik doğrulaması) destekler, böylece kullanıcılar bağlantı dizesinde kalıcı parolalar olmadan Kullanıcı parolalarını etkileşimli olarak girebilir.

Daha fazla bilgi ve örnek için [.net blogdaki](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/)"SQL--Azure AD Universal ve Multi-Factor Authentication support" başlığına bakın.

**Always Encrypted sürüm 2 için destek**

NET Framework 4.7.2, şifreleme tabanlı Always Encrypted destekler. Always Encrypted orijinal sürümü, şifreleme anahtarlarının istemciden hiçbir şekilde ayrılmayacağı istemci tarafı bir şifreleme teknolojisidir. Encde tabanlı Always Encrypted, istemci isteğe bağlı olarak, SQL Server bir parçası olarak kabul edilebilir ancak SQL Server kodu ile oynanamaz güvenli bir hesaplama varlığı olan güvenli bir kuşya şifreleme anahtarlarını gönderebilir. Kuşatma tabanlı Always Encrypted desteklemek için .NET Framework 4.7.2, <xref:System.Data.SqlClient> ad alanına aşağıdaki türleri ve üyeleri ekler:

- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, şifreleme tabanlı Always Encrypted URI 'sini belirtir.

- Tüm kuşve sağlayıcılarının türetildiği soyut bir sınıf olan <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>.

- <xref:System.Data.SqlClient.SqlEnclaveSession>, belirli bir şifreleme oturumunun durumunu kapsülleyen.

- <xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, belirli bir kanıtlama protokolünü yürütmek için gereken bilgileri almak üzere SQL Server tarafından kullanılan kanıtlama parametrelerini sağlayan.

Uygulama yapılandırma dosyası daha sonra, şifreleme sağlayıcısı için işlevselliği sağlayan soyut <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> sınıfının somut bir uygulamasını belirtir. Örneğin:

```xml
<configuration>
  <configSections>
    <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/> 
  </configSections>
  <SqlColumnEncryptionEnclaveProviders>
    <providers>
      <add name="Azure" type="Microsoft.SqlServer.Management.AlwaysEncrypted.AzureEnclaveProvider,MyApp"/>
      <add name="HGS" type="Microsoft.SqlServer.Management.AlwaysEncrypted.HGSEnclaveProvider,MyApp" />
    </providers>
  </SqlColumnEncryptionEnclaveProviders >
</configuration>
```

Şifreleme tabanlı Always Encrypted temel akışı:

1. Kullanıcı, SQL Server şifreli bir bağlantı oluşturur ve bu, şifreleme tabanlı Always Encrypted destekler. Sürücü, doğru kuşağa bağlandığından emin olmak için kanıtlama hizmetiyle iletişim kurar.

1. Şifreleme onaylandıktan sonra, sürücü, SQL Server barındırılan güvenli şifreleme ile güvenli bir kanal oluşturur.

1. Sürücü, SQL bağlantısı süresi boyunca güvenli şifreleme ile istemci tarafından yetkilendirilmiş şifreleme anahtarlarını paylaşır.

<a name="wpf472" />

#### <a name="windows-presentation-foundation"></a>Windows Presentation Foundation

**Kaynağa göre Resourcesözlükler bulma**

.NET Framework 4.7.2 ile başlayarak bir tanılama Yardımcısı, belirli bir kaynak URI 'sinden oluşturulmuş <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> bulabilir. (Bu özellik, üretim uygulamalarına göre değil, tanılama yardımcıları tarafından kullanılır.) Visual Studio "Düzenle ve devam et" özelliği gibi bir tanılama Yardımcısı, kullanıcının, değişikliklerin çalışan uygulamaya uygulanmasını sağlamak için bir ResourceDictionary 'yi düzenlemesine olanak tanır. Bunu elde eden bir adım, çalışan uygulamanın düzenlenmekte olan sözlükten oluşturduğu tüm Resourcesözlüklerini bulmasıdır. Örneğin, bir uygulama, içeriği belirli bir kaynak URI 'den kopyalanmış bir ResourceDictionary bildirebilir:

```xml
<ResourceDictionary Source="MyRD.xaml">
```

*Myrd. xaml* içindeki özgün biçimlendirmeyi düzenleyen bir tanılama Yardımcısı, sözlüğü bulmak için yeni özelliği kullanabilir. Özelliği, <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>yeni bir statik yöntem tarafından uygulanır. Tanılama Yardımcısı, aşağıdaki kodda gösterildiği gibi özgün biçimlendirmeyi tanımlayan mutlak bir URI kullanarak yeni yöntemi çağırır:

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

 <xref:System.Windows.Diagnostics.VisualDiagnostics> etkinleştirilmediği ve [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) ortam değişkeni ayarlanmadığı takdirde yöntem boş bir sıralanabilir değer döndürür.

**ResourceDictionary sahiplerini bulma**

.NET Framework 4.7.2 ile başlayarak bir tanılama Yardımcısı, belirli bir <xref:Windows.UI.Xaml.ResourceDictionary>sahiplerini bulabilir. (Özelliği, üretim uygulamalarına göre değil, tanılama yardımcıları tarafından kullanılır.) Bir <xref:Windows.UI.Xaml.ResourceDictionary>her değişiklik yapıldığında WPF, değişiklikten etkilenebilecek tüm [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) başvurularını otomatik olarak bulur.

Visual Studio 'nun "Düzenle ve devam et" özelliği gibi bir tanılama Yardımcısı, bu, [StaticResource](../wpf/advanced/staticresource-markup-extension.md) başvurularını işlemek için bunu genişletmek isteyebilir. Bu işlemin ilk adımı, sözlüğün sahiplerini bulledir; diğer bir deyişle, `Resources` özelliği sözlüğüne başvuran tüm nesneleri bulmak için (doğrudan veya <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> özelliği aracılığıyla dolaylı olarak). <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> sınıfında uygulanan üç yeni statik yöntem, bir `Resources` özelliğine sahip olan temel türlerin her biri için, bu adımı destekler:

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

 <xref:System.Windows.Diagnostics.VisualDiagnostics> etkinleştirilmediği ve [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) ortam değişkeni ayarlanmadığı takdirde bu yöntemler boş bir sıralanabilir değer döndürür.

**StaticResource başvurularını bulma**

Bir tanılama Yardımcısı, bir [StaticResource](../wpf/advanced/staticresource-markup-extension.md) başvurusu çözümlendiğinde artık bildirim alabilir. (Özelliği, üretim uygulamalarına göre değil, tanılama yardımcıları tarafından kullanılır.) Visual Studio "Düzenle ve devam et" özelliği gibi bir tanılama Yardımcısı, bir <xref:Windows.UI.Xaml.ResourceDictionary> değiştiğinde bir kaynağın tüm kullanımlarını güncelleştirmek isteyebilir. WPF bunu, [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) başvuruları için otomatik olarak yapar, ancak bu şekilde bu, [StaticResource](../wpf/advanced/staticresource-markup-extension.md) başvuruları için bunu yapmaz. .NET Framework 4.7.2 ile başlayarak, tanılama Yardımcısı bu bildirimleri statik kaynak kullanımlarını bulmak için kullanabilir.

Bildirim, yeni <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> olayı tarafından uygulanır:

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

Bu olay, çalışma zamanı bir [StaticResource](../wpf/advanced/staticresource-markup-extension.md) başvurusunu her çözdüğünde tetiklenir. <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> bağımsız değişkenleri çözümlemeyi betimleyen ve bu, [StaticResource](../wpf/advanced/staticresource-markup-extension.md) başvurusunu barındıran nesne ve özelliği ve çözüm için kullanılan <xref:Windows.UI.Xaml.ResourceDictionary> ve anahtarı belirtir:

```csharp
public class StaticResourceResolvedEventArgs : EventArgs
{
   public Object TargetObject { get; }

   public Object TargetProperty { get; }

   public ResourceDictionary ResourceDictionary { get; }

   public object ResourceKey { get; }
}
```

```vb
Public Class StaticResourceResolvedEventArgs : Inherits EventArgs
   Public ReadOnly Property TargetObject As Object
   Public ReadOnly Property TargetProperty As Object
   Public ReadOnly Property ResourceDictionary As ResourceDictionary
   Public ReadOnly Property ResourceKey As Object
End Class
```

 <xref:System.Windows.Diagnostics.VisualDiagnostics> etkinleştirilmediği ve [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) ortam değişkeni ayarlanmadığı müddetçe olay oluşturulmaz (ve `add` erişimcisi yok sayılır).

#### <a name="clickonce"></a>ClickOnce

Windows Forms, Windows Presentation Foundation (WPF) ve Office için Visual Studio Araçları (VSTO) için HDPı kullanan uygulamalar ClickOnce kullanılarak dağıtılabilir. Uygulama bildiriminde aşağıdaki giriş bulunursa, dağıtım .NET Framework 4.7.2 altında başarılı olur:

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

Windows Forms uygulama için, uygulama bildirimi yerine uygulama yapılandırma dosyasında DPı tanımayı ayarlamaya yönelik önceki geçici çözüm, artık ClickOnce dağıtımının başarılı olması için gerekli değildir.

<a name="v471" />

## <a name="whats-new-in-net-framework-471"></a>.NET Framework 4.7.1 yenilikleri

.NET Framework 4.7.1, aşağıdaki alanlardaki yeni özellikler içerir:

- [Temel sınıflar](#core471)
- [Ortak dil çalışma zamanı (CLR)](#clr)
- [Ağ](#net471)
- [ASP.NET](#asp-net471)

Ayrıca, .NET Framework 4.7.1 ' deki önemli bir odak, bir uygulamanın yardımcı teknoloji kullanıcıları için uygun bir deneyim sağlamasına izin veren gelişmiş erişilebilirliğe sahiptir. .NET Framework 4.7.1 ' deki erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için [.NET Framework erişilebilirlik](whats-new-in-accessibility.md)yenilikleri bölümüne bakın.

<a name="core471" />

#### <a name="base-classes"></a>Temel sınıflar

**.NET Standard 2,0 desteği**

[.NET Standard](../../standard/net-standard.md) , standart sürümünü destekleyen her bir .NET uygulamasında kullanılabilir olması gereken bir API kümesini tanımlar. .NET Framework 4.7.1, .NET Standard 2,0 ' yi tam olarak destekler ve .NET Standard 2,0 ' de tanımlanan [200 API 'leri](https://github.com/dotnet/standard/blob/master/netstandard/src/ApiCompatBaseline.net461.txt) ekler ve .NET Framework 4.6.1, 4.6.2 ve 4,7. (.NET Framework bu sürümlerinin yalnızca hedef sistemde ek .NET Standard destek dosyaları da dağıtılmışsa .NET Standard 2,0 desteklediğine unutmayın.) Daha fazla bilgi için, [.NET Framework 4.7.1 çalışma zamanı ve derleyici özellikleri blog gönderisinde](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) "BCL-.NET Standard 2,0 desteği" ne bakın.

**Yapılandırma oluşturucuları için destek**

Yapılandırma üreticileri, geliştiricilerin uygulamalar için yapılandırma ayarlarını çalışma zamanında dinamik olarak eklemesine ve oluşturmalarına olanak tanır. Özel yapılandırma oluşturucuları, bir yapılandırma bölümünde var olan verileri değiştirmek veya tamamen sıfırdan bir yapılandırma bölümü oluşturmak için kullanılabilir. Yapılandırma oluşturucuları olmadan,. config dosyaları statiktir ve ayarları bir uygulama başlatılmadan önce bir süre tanımlanır.

Özel bir yapılandırma Oluşturucu oluşturmak için, oluşturucuyu soyut <xref:System.Configuration.ConfigurationBuilder> sınıfından türetirsiniz ve <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> ve <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>geçersiz kılarsınız. Ayrıca, Oluşturucularınızı. config dosyanızda tanımlarsınız. Daha fazla bilgi için, [.NET Framework 4.7.1 ASP.net ve yapılandırma özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisinin "yapılandırma oluşturucuları" bölümüne bakın.

**Çalışma zamanı özellik algılama**

<xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> sınıfı, derleme zamanında veya çalışma zamanında, belirli bir .NET uygulamasında önceden tanımlanmış bir özelliğin desteklenip desteklenmediğini belirlemede bir mekanizma sağlar. Derleme zamanında bir derleyici, özelliğin desteklenip desteklenmediğini anlamak için belirtilen alanın mevcut olup olmadığını denetleyebilir. varsa, bu özellikten faydalanan kodu yayabilir. Çalışma zamanında bir uygulama, çalışma zamanında kodu göndermeden önce <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> metodunu çağırabilir. Daha fazla bilgi için bkz. [çalışma zamanı tarafından desteklenen özellikleri anlatmak için yardımcı yöntemi ekleme](https://github.com/dotnet/corefx/issues/17116).

**Değer tanımlama grubu türleri seri hale getirilebilir**

.NET Framework 4.7.1 ile başlayarak, <xref:System.ValueTuple?displayProperty=nameWithType> ve ilişkili genel türleri, ikili Serileştirmeye izin veren [seri hale getirilebilir](xref:System.SerializableAttribute)olarak işaretlenir. Bu, <xref:System.Tuple%603> ve <xref:System.Tuple%604>gibi kayıt düzeni türlerinin değer tanımlama grubu türlerine daha kolay olmasını sağlamalıdır. Daha fazla bilgi için, [.NET Framework 4.7.1 çalışma zamanı ve derleyici özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisinde "derleyici--ValueTuple" seri hale getirilebilir "başlığına bakın.

**Salt okuma başvuruları desteği**

.NET Framework 4.7.1 <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>ekler. Bu öznitelik, salt okuma başvuru dönüş türleri veya parametreleri olan üyeleri işaretlemek için dil derleyicileri tarafından kullanılır. Daha fazla bilgi için, [.NET Framework 4.7.1 çalışma zamanı ve derleyici özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisinde "derleyici--ReadOnlyReferences desteği" bölümüne bakın. Başvuru dönüş değerleri hakkında daha fazla bilgi için bkz. [ref Return Values ve refC# Locals (Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) ve [ref Return values (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).

<a name="clr" />

#### <a name="common-language-runtime-clr"></a>Ortak dil çalışma zamanı (CLR)

**Çöp toplama performansı iyileştirmeleri**

.NET Framework 4.7.1 'teki çöp toplama (GC) değişiklikleri, özellikle büyük nesne yığını (LOH) ayırmaları için genel performansı geliştirir. .NET Framework 4.7.1 ' de, arka plan GC, SOH 'yi ortaya çıkaran zaman, LOH ayırmalarının oluşmasına izin veren küçük nesne yığını (SOH) ve LOH ayırmaları için ayrı kilitler kullanılır. Sonuç olarak, çok sayıda LOH ayırması yapan uygulamalar, ayırma Kilidi çakışması ve gelişmiş performans konusunda bir azalma görmeniz gerekir. Daha fazla bilgi için, [.NET Framework 4.7.1 çalışma zamanı ve derleyici özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisindeki "çalışma zamanı--GC performansı iyileştirmeleri" bölümüne bakın.

<a name="net471"/>

#### <a name="networking"></a>Ağ Oluşturma

**Message. HashAlgorithm için SHA-2 desteği**

.NET Framework 4,7 ve önceki sürümlerde, <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> özelliği yalnızca <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> ve <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> değerlerini destekliyordu. .NET Framework 4.7.1 ile başlayarak, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>ve <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> de desteklenir. Bu değerin gerçekten kullanılıp kullanılmadığını, <xref:System.Messaging.Message> örneğinin kendisi karma olmadığından ve yalnızca MSMQ 'ya değer geçirdiğinden MSMQ 'ya bağlıdır. Daha fazla bilgi için, [.NET Framework 4.7.1 ASP.net ve yapılandırma özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisinin "Message. HASHALGORITHM için SHA-2 desteği" bölümüne bakın.

<a name="asp-net471" />

#### <a name="aspnet"></a>ASP.NET

**ASP.NET uygulamalarındaki yürütme adımları**

ASP.NET, 23 olay içeren önceden tanımlanmış bir işlem hattındaki istekleri işler. ASP.NET, her olay işleyicisini yürütme adımı olarak yürütür. ASP.NET ' nin .NET Framework 4,7 ' e kadar olan sürümlerinde, yerel ve yönetilen iş parçacıkları arasında geçiş yapmak nedeniyle ASP.NET yürütme bağlamını akamaz. Bunun yerine, ASP.NET yalnızca <xref:System.Web.HttpContext>akar. .NET Framework 4.7.1 ile başlayarak, <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> Yöntemi ayrıca modüllerin çevresel verileri geri yüklemesine olanak tanır. Bu özellik, izleme, profil oluşturma, tanılama veya işlemlerle ilgili kitaplıklara, örneğin, uygulamanın yürütme akışı hakkında endişeleri hedefleder. Daha fazla bilgi için, [.NET Framework 4.7.1 ASP.net ve yapılandırma özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisine "ASP.net Execution Step Feature" bölümüne bakın.

**ASP.NET HttpCookie ayrıştırma**

.NET Framework 4.7.1, bir dizeden <xref:System.Web.HttpCookie> nesne oluşturmak için standartlaştırılmış bir yol sağlayan ve son kullanma tarihi ve yolu gibi tanımlama bilgisi değerlerini doğru şekilde atayan yeni bir <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>yöntem içerir. Daha fazla bilgi için, [.NET Framework 4.7.1 ASP.net ve yapılandırma özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisine "ASP.net HttpCookie ayrıştırma" konusuna bakın.

**ASP.NET Forms kimlik doğrulama kimlik bilgileri için SHA-2 karma seçenekleri**

.NET Framework 4,7 ve önceki sürümlerde, ASP.NET izin verilen geliştiricilerin, Kullanıcı kimlik bilgilerini MD5 veya SHA1 kullanarak yapılandırma dosyalarında karma parolalara depolamasına olanak sağlar. .NET Framework 4.7.1 ile başlayarak, ASP.NET, SHA256, SHA384 ve SHA512 olur gibi yeni güvenli SHA-2 karma seçeneklerini de destekler. SHA1 varsayılan olarak kalır ve varsayılan olmayan bir karma algoritması Web yapılandırma dosyasında tanımlanabilir. Örneğin:

```xml
<system.web>
    <authentication mode="Forms">
        <forms loginUrl="~/login.aspx">
          <credentials passwordFormat="SHA512">
            <user name="jdoe" password="6D003E98EA1C7F04ABF8FCB375388907B7F3EE06F278DB966BE960E7CBBD103DF30CA6D61F7E7FD981B2E4E3A64D43C836A4BEDCA165C33B163E6BCDC538A664" />
          </credentials>
        </forms>
    </authentication>
</system.web>
```

<a name="v47" />

## <a name="whats-new-in-net-framework-47"></a>.NET Framework 4,7 ' deki yenilikler

.NET Framework 4,7, aşağıdaki alanlardaki yeni özellikler içerir:

- [Temel sınıflar](#Core47)
- [Ağ](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

.NET Framework 4,7 ' ye eklenen yeni API 'lerin bir listesi için bkz. GitHub 'da [.NET Framework 4,7 API değişiklikleri](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) . .NET Framework 4,7 ' deki Özellik geliştirmeleri ve hata düzeltmeleri listesi için GitHub 'da [.NET Framework 4,7 değişiklik listesine](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) bakın.  Daha fazla bilgi için bkz. .NET blogu 'nda [.NET Framework 4,7 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) .

<a name="Core47" />

#### <a name="base-classes"></a>Temel sınıflar

.NET Framework 4,7 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>tarafından Serileştirmeyi geliştirir:

**Eliptik eğri şifrelemesi (ECC) Ile gelişmiş işlevsellik***

.NET Framework 4,7 ' de, bir nesnenin zaten oluşturulmuş bir anahtarı göstermesini sağlamak için <xref:System.Security.Cryptography.ECDsa> ve <xref:System.Security.Cryptography.ECDiffieHellman> sınıflarına `ImportParameters(ECParameters)` yöntemler eklenmiştir. Açık eğri parametreleri kullanılarak anahtarı dışarı aktarmak için bir `ExportParameters(Boolean)` yöntemi de eklenmiştir.

.NET Framework 4,7 ayrıca ek eğriler (Brainpool eğrisi paketi dahil) için destek de ekler ve yeni <xref:System.Security.Cryptography.ECDsa.Create%2A> ve <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> Factory yöntemleriyle oluşturma kolaylığı için önceden tanımlanmış tanımlar ekledi.

GitHub 'da [4,7 .NET Framework şifreleme geliştirmesi örneği](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) görebilirsiniz.

**DataContractJsonSerializer tarafından denetim karakterleri için daha iyi destek**

.NET Framework 4,7 ' de, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ECMAScript 6 standardı ile uyum içinde denetim karakterlerini seri hale getirir. Bu davranış, .NET Framework 4,7 ' i hedefleyen uygulamalar için varsayılan olarak etkindir ve .NET Framework 4,7 altında çalışan ancak .NET Framework önceki bir sürümünü hedefleyen uygulamalar için bir kabul etme özelliğidir. Daha fazla bilgi için bkz. [.NET Framework 4,7 ' de yeniden hedefleme değişiklikleri](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="net47" />

#### <a name="networking"></a>Ağ Oluşturma

.NET Framework 4,7, ağla ilgili aşağıdaki özelliği ekler:

**TLS protokolleri Için varsayılan işletim sistemi desteği***

HTTP, FTP ve SMTP gibi <xref:System.Net.Security.SslStream?displayProperty=nameWithType> ve yukarı yığın bileşenleri tarafından kullanılan TLS yığını, geliştiricilerin işletim sistemi tarafından desteklenen varsayılan TLS protokollerini kullanmasına izin verir. Geliştiricilerin artık bir TLS sürümüne sabit kod olmaması gerekir.

<a name="ASP-NET47" />

#### <a name="aspnet"></a>ASP.NET

.NET Framework 4,7 ' de, ASP.NET aşağıdaki yeni özellikleri içerir:

**Nesne önbelleği genişletilebilirliği**

ASP.NET, .NET Framework 4,7 ' den başlayarak, geliştiricilerin bellek içi nesne önbelleğe alma ve bellek izleme için varsayılan ASP.NET uygulamalarını değiştirmesine izin veren yeni bir API kümesi ekler. ASP.NET uygulamasının yeterli olmaması halinde geliştiriciler artık aşağıdaki üç bileşenden birini değiştirebilir:

- **Nesne önbelleği deposu**. Yeni önbellek sağlayıcıları yapılandırma bölümünü kullanarak, geliştiriciler yeni **ICacheStoreProvider** arabirimini kullanarak bir ASP.NET uygulaması için nesne önbelleğinin yeni uygulamalarını yükleyebilir.

- **Bellek izleme**. ASP.NET ' deki varsayılan bellek İzleyicisi, uygulamaları, işlem için yapılandırılmış özel bayt sınırına yakın bir şekilde çalıştığında veya makinenin toplam kullanılabilir fiziksel RAM üzerinde azaldığını bildirir. Bu limitlerin yakınında, bildirimler tetiklenir. Bazı uygulamalar için bildirimler, yararlı yeniden eylemlere izin vermek üzere yapılandırılan sınırlara çok yakın şekilde harekete geçirilir. Geliştiriciler artık <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> özelliğini kullanarak varsayılan değerini değiştirmek için kendi bellek izleyicilerini yazabilir.

- **Bellek sınırı yeniden eylemleri**. ASP.NET, varsayılan olarak, nesne önbelleğini kırpmaya çalışır ve özel bayt işlem sınırı yakınında <xref:System.GC.Collect%2A?displayProperty=nameWithType> düzenli aralıklarla çağırır. Bazı uygulamalarda, <xref:System.GC.Collect%2A?displayProperty=nameWithType> çağrılarının sıklığı veya kırpılan önbellek miktarı verimsiz olur. Geliştiriciler artık **ıgözlemci** uygulamalarını uygulamanın bellek izleyicisine abone olarak varsayılan davranışı değiştirebilir veya tamamlayabilir.

<a name="wcf47" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WCF) aşağıdaki özellikleri ve değişiklikleri ekler:

**Varsayılan ileti güvenlik ayarlarını TLS 1,1 veya TLS 1,2 olarak yapılandırma olanağı**

WCF, .NET Framework 4,7 ' den itibaren, varsayılan ileti güvenlik protokolü olarak SSL 3,0 ve TSL 1,0 ' ye ek olarak TSL 1,1 veya TLS 1,2 yapılandırmanızı sağlar. Bu bir kabul etme ayarıdır; etkinleştirmek için, uygulama yapılandırma dosyanıza aşağıdaki girişi eklemeniz gerekir:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

**WCF uygulamalarının ve WCF serileştirmenin güvenilirliği geliştirildi**

WCF, yarış koşullarını ortadan kaldıran bir dizi kod değişikliği içerir, böylece performansı ve serileştirme seçeneklerinin güvenilirliğini geliştirir. Bu güncelleştirmeler şunlardır:

- **SocketConnection. BeginRead** ve **SocketConnection. Read**çağrılarına zaman uyumsuz ve zaman uyumlu kod karıştırma için daha iyi destek.
- **Sharedconnectionlistener** ve **DuplexChannelBinder**ile bağlantı iptal edildiğinde iyileştirilmiş güvenilirlik.
- <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> yöntemi çağrılırken serileştirme işlemlerinin geliştirilmiş güvenilirliği.
- **Channeleşitleyici. removewaiter** yöntemi çağırarak bir garson kaldırılırken güvenilirlik artırıldı.

<a name="wf47" />

#### <a name="windows-forms"></a>Windows Forms

.NET Framework 4,7 ' de, Windows Forms yüksek DPı izleyicileri desteğini geliştirir.

**Yüksek DPı desteği**

.NET Framework 4,7 ' i hedefleyen uygulamalarla başlayarak, .NET Framework Windows Forms uygulamalar için yüksek DPı ve dinamik DPı desteği sunar. Yüksek DPı desteği, yüksek DPı izleyicilerinde form ve denetimlerin düzen ve görünümünü geliştirir. Dinamik DPı, Kullanıcı DPı 'yi değiştirdiğinde form ve denetimlerin yerleşimini ve görünümünü değiştirir ve çalışan bir uygulamanın ölçek faktörünü görüntüler.

Yüksek DPı desteği, uygulama yapılandırma dosyanızda [\<System. Windows. Forms. ConfigurationSection >](../configure-apps/file-schema/winforms/index.md) bölümü tanımlayarak yapılandırdığınız bir katılım özelliğidir. Windows Forms uygulamanıza yüksek DPı desteği ve dinamik DPı desteği ekleme hakkında daha fazla bilgi için, bkz. [Windows Forms yüksek DPI desteği](../winforms/high-dpi-support-in-windows-forms.md).

<a name="WPF47" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

.NET Framework 4,7 ' de WPF aşağıdaki geliştirmeleri içerir:

**Windows WM_POINTER iletilerine dayalı bir dokunmatik/Stilus yığını desteği**

Artık Windows mürekkep hizmetleri platformu (WıSS) yerine [WM_POINTER iletilerine](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) dayalı bir dokunmatik/Stilus yığını kullanma seçeneğiniz vardır. Bu, .NET Framework bir katılım özelliğidir. Daha fazla bilgi için bkz. [.NET Framework 4,7 ' de yeniden hedefleme değişiklikleri](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

**WPF yazdırma API 'Leri için yeni uygulama**

WPF 'nin <xref:System.Printing.PrintQueue?displayProperty=nameWithType> sınıfında bulunan yazdırma API 'Leri, kullanım dışı olan [XPS yazdırma API](/windows/desktop/printdocs/xps-printing)'Si yerine Windows [yazdırma belgesi paketi API](/windows/desktop/printdocs/tailored-app-printing-api) 'sini çağırır. Bu değişikliğin uygulama uyumluluğuna etkisi için [.NET Framework 4,7 ' deki yeniden hedefleme değişiklikleri](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md)bölümüne bakın.

<a name="v462" />

## <a name="whats-new-in-net-framework-462"></a>.NET Framework 4.6.2 yenilikleri

.NET Framework 4.6.2, aşağıdaki alanlardaki yeni özellikler içerir:

- [ASP.NET](#ASPNET462)

- [Karakter kategorileri](#Strings)

- [Şifreleme](#Crypto462)

- [SqlClient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#clickonce-1)

- [Windows Forms ve WPF uygulamalarını UWP uygulamalarına dönüştürme](#UWPConvert)

- [Hata ayıklama geliştirmeleri](#Debug462)

.NET Framework 4.6.2 'e eklenen yeni API 'lerin bir listesi için bkz. GitHub 'da [.NET Framework 4.6.2 API değişiklikleri](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) . .NET Framework 4.6.2 ' deki Özellik geliştirmeleri ve hata düzeltmeleri listesi için bkz. GitHub 'da [değişiklikler listesi .NET Framework 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) . Daha fazla bilgi için bkz. .NET blogda [.NET Framework 4.6.2 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) .

<a name="ASPNET462" />

### <a name="aspnet"></a>ASP.NET

.NET Framework 4.6.2, ASP.NET aşağıdaki geliştirmeleri içerir:

**Veri ek açıklama Doğrulayıcıları 'nda yerelleştirilmiş hata iletileri için geliştirilmiş destek**

Veri ek açıklama Doğrulayıcıları bir sınıf özelliğine bir veya daha fazla öznitelik ekleyerek doğrulama gerçekleştirmenize olanak tanır. Özniteliğin <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> öğesi, doğrulama başarısız olursa hata iletisinin metnini tanımlar. .NET Framework 4.6.2 ile başlayarak, ASP.NET hata iletilerini yerelleştirmenizi kolaylaştırır. Şu durumlarda hata iletileri yerelleştirilecektir:

1. <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType>, doğrulama özniteliğinde verilmiştir.

2. Kaynak dosyası App_LocalResources klasöründe depolanır.

3. Yerelleştirilmiş kaynaklar dosyasının adı `DataAnnotation.Localization.{`*adı*`}.resx`, burada *ad* *languageCode*`-`*ülke/RegionCode* veya *languageCode*biçiminde bir kültür adıdır.

4. Kaynağın anahtar adı, <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> özniteliğe atanan dizedir ve değeri yerelleştirilmiş hata iletisidir.

Örneğin, aşağıdaki Data Annotation özniteliği geçersiz bir derecelendirme için varsayılan kültürün hata iletisini tanımlar.

```csharp
public class RatingInfo
{
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]
   [Display(Name = "Your Rating")]
   public int Rating { get; set; }
}
```

```vb
Public Class RatingInfo
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>
   <Display(Name = "Your Rating")>
   Public Property Rating As Integer = 1
End Class
```

Ardından, anahtar hata iletisi dizesi olan ve değeri yerelleştirilmiş hata iletisi olan DataAnnotation. yerelleştirme. fr. resx olan bir kaynak dosyası oluşturabilirsiniz. Dosyanın `App.LocalResources` klasöründe bulunması gerekir. Örneğin, aşağıdaki anahtar ve değeri yerelleştirilmiş Fransızca (fr) dil hata iletisinde verilmiştir:

| Name                                 | Değer                                     |
| ------------------------------------ | ----------------------------------------- |
| Derecelendirme 1 ile 10 arasında olmalıdır. | La Note DoIt être, diğer 1 et 10. |

 Ayrıca, veri ek açıklaması yerelleştirme genişletilebilir. Geliştiriciler, yerelleştirme dizesini kaynak dosyasında dışında bir yerde depolamak için <xref:System.Web.Globalization.IStringLocalizerProvider> arabirimini uygulayarak kendi dize yerelleştirici sağlayıcısını ekleyebilir.

 **Oturum durumu depo sağlayıcıları ile zaman uyumsuz destek**

 ASP.NET artık oturum durumu depolama sağlayıcılarıyla birlikte görev döndüren yöntemlerin kullanılmasına izin veriyor, böylece ASP.NET uygulamalarının zaman uyumsuz olarak ölçeklenebilirlik avantajlarını almasına izin verir. ASP.NET <xref:System.Web.IHttpModule> 'ten devralan ve geliştiricilerin kendi oturum durumu modülünü ve zaman uyumsuz oturum depolama sağlayıcılarını uygulamasına olanak tanıyan <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, oturum durumu depolama sağlayıcılarıyla zaman uyumsuz işlemleri destekler. Arabirim aşağıdaki gibi tanımlanır:

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

```vb
Public Interface ISessionStateModule : Inherits IHttpModule
   Sub ReleaseSessionState(context As HttpContext)
   Function ReleaseSessionStateAsync(context As HttpContext) As Task
End Interface
```

 Ayrıca, <xref:System.Web.SessionState.SessionStateUtility> sınıfı, zaman uyumsuz işlemleri desteklemek için kullanılabilen iki yeni yöntem içerir, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> ve <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>.

 **Çıkış önbelleği sağlayıcıları için zaman uyumsuz destek**

 .NET Framework 4.6.2 ile başlayarak, zaman uyumsuz olarak ölçeklenebilirlik avantajları sağlamak için, görev döndüren yöntemler çıkış önbelleği sağlayıcılarıyla birlikte kullanılabilir.  Bu yöntemleri uygulayan sağlayıcılar, bir Web sunucusundaki iş parçacığı engellemeyi azaltır ve bir ASP.NET hizmetinin ölçeklenebilirliğini geliştirir.

 Zaman uyumsuz çıkış önbelleği sağlayıcılarını desteklemek için aşağıdaki API 'Ler eklenmiştir:

- <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> devralan ve geliştiricilerin zaman uyumsuz çıkış önbelleği sağlayıcısı uygulamasına izin veren <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> sınıfı.

- Çıkış önbelleğini yapılandırmak için yardımcı yöntemler sağlayan <xref:System.Web.Caching.OutputCacheUtility> sınıfı.

- <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> sınıfında 18 yeni yöntem. Bunlara <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>ve <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>dahildir.

- 2 <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> sınıfında yeni Yöntemler: <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> ve <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.

- 2 <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> sınıfında yeni Yöntemler: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> ve <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.

- 2 <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> sınıfında yeni Yöntemler: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> ve <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.

- <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> sınıfında <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> yöntemi.

- <xref:System.Web.Caching.CacheDependency>, <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> yöntemi.

<a name="Strings" />

### <a name="character-categories"></a>Karakter kategorileri

.NET Framework 4.6.2 karakterler [Unicode standardı, sürüm 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/)temel alınarak sınıflandırılır. .NET Framework 4,6 ve .NET Framework 4.6.1, karakterler Unicode 6,3 karakter kategorilerine göre sınıflandırıldı.

Unicode 8,0 desteği, <xref:System.Globalization.CharUnicodeInfo> sınıfı ve kendisine bağımlı tür ve yöntemlere göre karakterlerin sınıflandırmasıyla sınırlıdır. Bunlara <xref:System.Globalization.StringInfo> sınıfı, aşırı yüklenmiş <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> yöntemi ve .NET Framework normal ifade altyapısı tarafından tanınan [karakter sınıfları](../../standard/base-types/character-classes-in-regular-expressions.md) dahildir.  Karakter ve dize karşılaştırma ve sıralama bu değişiklikten etkilenmez ve temel alınan işletim sistemine veya Windows 7 sistemlerinde, .NET Framework tarafından belirtilen karakter verilerinde kullanılmaya devam eder.

Unicode 6,0 ' den Unicode 7,0 ' e karakter kategorilerindeki değişiklikler için bkz. Unicode [Standart, sürüm 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) , Unicode konsorsiyum Web sitesi. Unicode 7,0 ' den Unicode 8,0 ' e yapılan değişiklikler için bkz. Unicode [Standart, sürüm 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) , Unicode konsorsiyum Web sitesi.

<a name="Crypto462" />

### <a name="cryptography"></a>Şifreleme

**FIPS 186-3 DSA içeren x509 sertifikaları desteği**

.NET Framework 4.6.2, anahtarları FIPS 186-2 1024 bit sınırını aşan DSA (dijital Imza algoritması) x509 sertifikaları için destek ekler.

.NET Framework 4.6.2, FIPS 186-3 'in daha büyük anahtar boyutlarını desteklemeye ek olarak, karma algoritmaların SHA-2 ailesiyle (SHA256, SHA384 ve SHA512 olur) imzaları hesaplama olanağı sağlar. FIPS 186-3 desteği yeni <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> sınıfı tarafından sağlanmaktadır.

.NET Framework 4,6 ' deki <xref:System.Security.Cryptography.RSA> sınıfında son değişiklikler ve .NET Framework 4.6.1 ' deki <xref:System.Security.Cryptography.ECDsa> sınıfı ile birlikte, <xref:System.Security.Cryptography.DSA> 4.6.2 içindeki .NET Framework soyut temel sınıf, çağıranların atama olmadan bu işlevselliği kullanmasına izin vermek için ek yöntemlere sahiptir. Aşağıdaki örnekte gösterildiği gibi, verileri imzalamak için <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> uzantısı yöntemini çağırabilirsiniz.

```csharp
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPrivateKey())
    {
        return dsa.SignData(data, HashAlgorithmName.SHA384);
    }
}
```

```vb
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()
    Using DSA As DSA = cert.GetDSAPrivateKey()
        Return DSA.SignData(data, HashAlgorithmName.SHA384)
    End Using
End Function
```

Aşağıdaki örnekte gösterildiği gibi imzalı verileri doğrulamak için <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> uzantısı yöntemini çağırabilirsiniz.

```csharp
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPublicKey())
    {
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);
    }
}
```

```vb
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean
    Using dsa As DSA = cert.GetDSAPublicKey()
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)
    End Using
End Function
```

**Ecdıfıehellman anahtar türetme yordamlarına yönelik girişler için daha fazla açıklık**

.NET Framework 3,5, üç farklı anahtar türetme Işlevi (KDF) yordamlarına sahip Eliptik Eğri Diffie-Hellman anahtar anlaşması için destek eklendi. Yordamlarına yapılan girişler ve yordamlar, <xref:System.Security.Cryptography.ECDiffieHellmanCng> nesnesindeki özellikler aracılığıyla yapılandırılmıştır. Ancak her bir yordam her giriş özelliğini okumadığından, geliştiricinin geçmişte karışıklık için çok fazla yer vardır.

.NET Framework 4.6.2 ' de bunu ele almak için, bu KDF yordamlarını ve bunların girişlerini daha net bir şekilde temsil etmek üzere <xref:System.Security.Cryptography.ECDiffieHellman> temel sınıfına aşağıdaki üç yöntem eklenmiştir:

|Ecdıfıfiehellman yöntemi|Açıklama|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Formülü kullanarak önemli malzemeleri türetiliyor<br /><br /> Karma (SecretPrepend &#124; &#124; *x* &#124; &#124; SecretAppend)<br /><br /> Karma (secretPrepend Orelo *x* Orelo secretAppend)<br /><br /> Burada *x* , EC Diffie-Hellman algoritmasının hesaplanan sonucudur.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Formülü kullanarak önemli malzemeleri türetiliyor<br /><br /> HMAC (HmacKey, SecretPrepend &#124; &#124; *x* &#124; &#124; SecretAppend)<br /><br /> HMAC (hmacKey, secretPrepend Orelo *x* Orellsecretappend)<br /><br /> Burada *x* , EC Diffie-Hellman algoritmasının hesaplanan sonucudur.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|TLS sözde rastgele işlevi (PRF) türetme algoritmasını kullanarak önemli malzemeleri türetiliyor.|

**Kalıcı anahtar simetrik şifreleme desteği**

Windows şifreleme kitaplığı (CNG), kalıcı simetrik anahtarları depolama ve donanımla depolanan simetrik anahtarları kullanma desteği eklendi ve .NET Framework 4.6.2 geliştiricilerin bu özelliği kullanmasını mümkün hale getirir.  Anahtar adları ve anahtar sağlayıcılarının kavramı uygulamaya özgü olduğundan, bu özelliğin kullanılması tercih edilen fabrika yaklaşımı (örneğin, `Aes.Create`çağırma) yerine somut uygulama türleri oluşturucusunun kullanılmasını gerektirir.

AES (<xref:System.Security.Cryptography.AesCng>) ve 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algoritmaları için kalıcı anahtar simetrik şifreleme desteği vardır. Örneğin:

```csharp
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)
{
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))
    {
        aes.IV = iv;

        // Using the zero-argument overload is required to make use of the persisted key
        using (ICryptoTransform encryptor = aes.CreateEncryptor())
        {
            if (!encryptor.CanTransformMultipleBlocks)
            {
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");
            }

            return encryptor.TransformFinalBlock(data, 0, data.Length);
        }
    }
}
```

```vb
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)
        Aes.IV = iv

        ' Using the zero-argument overload Is required to make use of the persisted key
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()
            If Not encryptor.CanTransformMultipleBlocks Then
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

**SHA-2 karma için SignedXml desteği**

.NET Framework 4.6.2, RSA-SHA256, RSA-SHA384 ve RSA-SHA512 olur PKCS # 1 imza yöntemlerine, SHA256, SHA384 ve SHA512 olur başvuru Özet algoritmalarına yönelik <xref:System.Security.Cryptography.Xml.SignedXml> sınıfına destek ekler.

URI sabitlerinin tümü <xref:System.Security.Cryptography.Xml.SignedXml>açıktır:

|SignedXml alanı|Sabit|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Bu algoritmalara yönelik destek eklemek için <xref:System.Security.Cryptography.CryptoConfig> özel bir <xref:System.Security.Cryptography.SignatureDescription> işleyicisini kaydetmiş olan programlar geçmişte oldukları gibi çalışmaya devam eder, ancak artık platform Varsayılanları olduğundan, <xref:System.Security.Cryptography.CryptoConfig> kaydı artık gerekli değildir.

<a name="SQLClient" />

### <a name="sqlclient"></a>SqlClient

SQL Server için .NET Framework Veri Sağlayıcısı (<xref:System.Data.SqlClient?displayProperty=nameWithType>) .NET Framework 4.6.2 aşağıdaki yeni özellikleri içerir:

**Azure SQL veritabanları ile bağlantı havuzu oluşturma ve zaman aşımları**

Bağlantı havuzu etkinleştirildiğinde ve bir zaman aşımı ya da başka bir oturum açma hatası oluştuğunda, bir özel durum önbelleğe alınır ve sonraki 5 saniye 1 dakikaya kadar sonraki bağlantı denemelerde önbelleğe alınan özel durum oluşturulur.  Daha ayrıntılı bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../data/adonet/sql-server-connection-pooling.md).

Bağlantı girişimleri genellikle hızla kurtarılan geçici hatalarla başarısız olduğundan, bu davranış Azure SQL veritabanlarına bağlanırken istenmez. Bağlantı yeniden deneme deneyimini daha iyi en iyi hale getirebilmesi için, Azure SQL veritabanlarına bağlantı başarısız olduğunda bağlantı havuzu engelleme süresi davranışı kaldırılır.

Yeni `PoolBlockingPeriod` anahtar sözcüğünün eklenmesi, uygulamanız için en uygun engelleme dönemini seçmenize olanak sağlar. Değerlere şunlar dahildir:

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

Azure SQL veritabanına bağlanan bir uygulama için bağlantı havuzu engelleme süresi devre dışıdır ve başka bir SQL Server örneğine bağlanan bir uygulama için bağlantı havuzu engelleme süresi etkindir. Varsayılan değer budur. Sunucu uç noktası adı aşağıdakilerden biriyle sonlanıyorsa, Azure SQL veritabanı olarak kabul edilir:

- .database.windows.net

- .database.chinacloudapi.cn

- .database.usgovcloudapi.net

- .database.cloudapi.de

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

Bağlantı havuzu engelleme dönemi her zaman etkindir.

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

Bağlantı havuzu engelleme süresi her zaman devre dışıdır.

**Always Encrypted geliştirmeleri**

SQLClient Always Encrypted için iki geliştirme sunar:

- Şifrelenmiş veritabanı sütunlarına karşı parametreli sorguların performansını artırmak için, sorgu parametrelerinin şifreleme meta verileri artık önbelleğe alınır. <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> özelliği `true` (varsayılan değer) olarak ayarlandığında, aynı sorgu birden çok kez çağrılırsa, istemci parametre meta verilerini sunucudan yalnızca bir kez alır.

- Anahtar önbelleğindeki sütun şifreleme anahtarı girdileri artık yapılandırılabilir bir zaman aralığından sonra çıkarılmakta ve <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> özelliği kullanılarak ayarlanır.

<a name="WCF" />

### <a name="windows-communication-foundation"></a>Windows Communication Foundation

.NET Framework 4.6.2, aşağıdaki alanlarda Windows Communication Foundation geliştirilmiştir:

**CNG kullanılarak depolanan sertifikalar için WCF Aktarım güvenliği desteği**

WCF Aktarım güvenliği, Windows şifreleme kitaplığı (CNG) kullanılarak depolanan sertifikaları destekler. .NET Framework 4.6.2, bu destek, en fazla 32 bit uzunluğunda olmayan bir ortak anahtarla sertifikaların kullanılmasıyla sınırlandırılmıştır. Bir uygulama .NET Framework 4.6.2 hedefliyorsa, bu özellik varsayılan olarak açık olur.

.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 üzerinde çalışan uygulamalar için, bu özellik App. config veya Web. config dosyasının [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki satırı eklenerek etkinleştirilebilir.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

Bu, aşağıdakiler gibi kodla programlı olarak da yapılabilir:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

**DataContractJsonSerializer sınıfına göre birden çok gün ışığından yararlanma zaman ayarlama kuralı için daha iyi destek**

Müşteriler, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sınıfının tek bir saat dilimi için birden çok ayarlama kuralını destekleyip desteklemediğini tespit etmek için bir uygulama yapılandırma ayarı kullanabilir. Bu onaya bağlı bir özelliktir. Etkinleştirmek için App. config dosyanıza aşağıdaki ayarı ekleyin:

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Bu özellik etkinleştirildiğinde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nesnesi tarih ve saat verilerinin serisini kaldırmak için <xref:System.TimeZone> türü yerine <xref:System.TimeZoneInfo> türünü kullanır. <xref:System.TimeZoneInfo>, geçmişteki saat dilimi verileriyle çalışmayı olanaklı kılan birden çok ayarlama kuralını destekler;   <xref:System.TimeZone>.

<xref:System.TimeZoneInfo> yapısı ve saat dilimi ayarlamaları hakkında daha fazla bilgi için bkz. [saat dilimine genel bakış](../../standard/datetime/time-zone-overview.md).

**NetNamedPipeBinding en iyi eşleşme**

WCF, istemci uygulamalarında, istedikleri uygulamayla en iyi şekilde eşleşen URI 'yi dinleyen hizmete her zaman bağlanabildiğini sağlayan yeni bir uygulama ayarına sahiptir. Bu uygulama ayarı `false` (varsayılan) olarak ayarlandığında, <xref:System.ServiceModel.NetNamedPipeBinding> kullanan istemciler, istenen URI 'nin bir alt dizesi olan bir URI üzerinde dinleme yapan bir hizmete bağlanmaya çalışmak için mümkündür.

Örneğin, bir istemci `net.pipe://localhost/Service1`dinlemeye bir hizmete bağlanmaya çalışır, ancak bu makinede yönetici ayrıcalığıyla çalışan farklı bir hizmet `net.pipe://localhost`dinler. Bu uygulama ayarı `false`olarak ayarlandığında, istemci yanlış hizmete bağlanmaya çalışır. Uygulama ayarını `true`olarak ayarladıktan sonra istemci her zaman en iyi eşleşen hizmete bağlanır.

> [!NOTE]
> <xref:System.ServiceModel.NetNamedPipeBinding> kullanan istemciler, tam bitiş noktası adresi yerine hizmetin temel adresine (varsa) göre hizmetleri bulur. Bu ayarın her zaman çalıştığından emin olmak için, hizmetin benzersiz bir temel adres kullanması gerekir.

Bu değişikliği etkinleştirmek için, istemci uygulamanızın App. config veya Web. config dosyasına aşağıdaki uygulama ayarını ekleyin:

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

**SSL 3,0 varsayılan bir protokol değil**

SSL 3,0, aktarım güvenliği ile NetTcp kullanırken güvenli bir bağlantı anlaşması için kullanılan varsayılan protokol değildir. Çoğu durumda, TLS 1,0, NetTcp protokol listesine eklendiğinden, var olan uygulamalara hiçbir etkisi olmaz. Tüm mevcut istemciler, en az TLS 1,0 kullanarak bir bağlantı anlaşması yapabilmelidir. Ssl3 gerekliyse, anlaşmalı protokoller listesine eklemek için aşağıdaki yapılandırma mekanizmalarından birini kullanın.

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> özelliği

- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> özelliği

- [\<netTcpBinding >](../configure-apps/file-schema/wcf/nettcpbinding.md) bölümünün [\<taşıma >](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) bölümü

- [\<customBinding >](../configure-apps/file-schema/wcf/custombinding.md) bölümünün [\<sslstreamsecurity >](../configure-apps/file-schema/wcf/sslstreamsecurity.md) bölümü

<a name="WPF462" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

.NET Framework 4.6.2, aşağıdaki alanlarda Windows Presentation Foundation geliştirilmiştir:

**Grup sıralaması**

Verileri gruplamak için bir <xref:System.Windows.Data.CollectionView> nesnesi kullanan bir uygulama, artık grupların nasıl sıralanacağını açıkça bildirebilirler. Açık sıralama, bir uygulama grupları dinamik olarak eklediğinde ya da kaldırırken veya gruplandırmada yer alan öğe özelliklerinin değerini değiştirdiğinde oluşan sezgisel olmayan sıralama sorununa yöneliktir. Ayrıca, gruplama özelliklerinin karşılaştırmalarını tam koleksiyonun sıralamasını grupların sıralaması olarak taşıyarak Grup oluşturma işleminin performansını da artırır.

Grup sıralamasını desteklemek için, yeni <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> ve <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> özellikleri <xref:System.ComponentModel.GroupDescription> nesnesi tarafından üretilen grup koleksiyonunun nasıl sıralanacağını anlatmaktadır. Bu, benzer <xref:System.Windows.Data.ListCollectionView> özelliklerinin veri öğelerinin nasıl sıralanacağını betimleyen yönteme benzerdir.

<xref:System.Windows.Data.PropertyGroupDescription> sınıfının iki yeni statik özelliği <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> ve <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, en yaygın durumlarda kullanılabilir.

Örneğin, aşağıdaki XAML verileri yaş ile gruplandırır, yaş gruplarını artan düzende sıralar ve her yaş grubundaki öğeleri son ada göre gruplandırır.

```xaml
<GroupDescriptions>
     <PropertyGroupDescription
         PropertyName="Age"
         CustomSort=
              "{x:Static PropertyGroupDescription.CompareNamesAscending}"/>
     </PropertyGroupDescription>
</GroupDescriptions>

<SortDescriptions>
     <SortDescription PropertyName="LastName"/>
</SortDescriptions>
```

**Yazılım klavye desteği**

Yumuşak klavye desteği, bir WPF uygulamalarında, dokunma girişi metin girişi yapan bir denetim tarafından alındığında, otomatik olarak Windows 10 ' da yeni yazılım klavyesini çağırarak ve yok ederek, bir WPF uygulamalarında odak izlemeye izin verebilir.

.NET Framework önceki sürümlerinde, WPF uygulamaları WPF kalem/dokunma hareketi desteğini devre dışı bırakmadan odak izlemeyi kabul edemez.  Sonuç olarak, WPF uygulamalarının tam WPF dokunma desteği arasında seçim yapmanız veya Windows fare yükseltmesine güvenmelidir.

**Monitör başına DPı**

WPF uygulamaları için yüksek DPı ve hibrit DPı ortamlarının en son kullanımını desteklemek için, .NET Framework 4.6.2 ' deki WPF, izleme başına tanımayı sağlar. WPF uygulamanızın monitör başına DPı kullanan bir duruma gelmesini sağlama hakkında daha fazla bilgi için bkz. GitHub 'da [örnekler ve Geliştirici Kılavuzu](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) .

.NET Framework önceki sürümlerinde, WPF uygulamaları sistem DPı farkındaylardır. Diğer bir deyişle, uygulamanın kullanıcı arabirimi, uygulamanın işlendiği izleyicinin DPı değerine bağlı olarak, işletim sistemi tarafından uygun şekilde ölçeklendirilir.

.NET Framework 4.6.2 altında çalışan uygulamalar için, uygulama yapılandırma dosyanızın [\<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki şekilde bir yapılandırma AÇıKLAMASı ekleyerek WPF uygulamalarında MONITÖR başına DPI değişikliklerini devre dışı bırakabilirsiniz:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462" />

### <a name="windows-workflow-foundation-wf"></a>{1&gt;Windows Workflow Foundation (WF)&lt;1}

.NET Framework 4.6.2, Windows Workflow Foundation aşağıdaki alanda geliştirilmiştir:

**Yeniden barındırılan C# WF tasarımcısında Ifadeler ve IntelliSense desteği**

WF, 4,5 .NET Framework başlayarak hem Visual Studio C# tasarımcısında hem de kod iş akışlarında ifadeleri destekler. Yeniden barındırılan İş Akışı Tasarımcısı, bir WF 'nin Visual Studio dışında bir uygulamada olmasını İş Akışı Tasarımcısı sağlayan bir temel özelliktir (örneğin, WPF).  Windows Workflow Foundation, yeniden barındırılan İş Akışı Tasarımcısı ifadeleri C# ve IntelliSense 'i destekleme yeteneği sağlar. Daha fazla bilgi için [Windows Workflow Foundation bloguna](https://blogs.msdn.microsoft.com/workflowteam/2016/07/20/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer/)bakın.

.NET Framework 4.6.2 ' den önceki .NET Framework sürümlerindeki `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`, bir müşteri, Visual Studio 'dan bir iş akışı projesi yeniden oluştururken WF Tasarımcısı IntelliSense bozulur. Proje derlemesi başarılı olsa da, iş akışı türleri tasarımcıda bulunmadı ve eksik iş akışı türleri için IntelliSense uyarıları **hata listesi** penceresinde görünür. .NET Framework 4.6.2 Bu sorunu giderir ve IntelliSense 'i kullanılabilir hale getirir.

**İş akışı Izleme olan iş akışı v1 uygulamaları artık FIPS modunda çalıştırılır**

FIPS uyumluluk modu etkin olan makineler artık iş akışı izleme ile iş akışı sürüm 1 stilinde bir uygulamayı başarıyla çalıştırabiliyor. Bu senaryoyu etkinleştirmek için App. config dosyanızda aşağıdaki değişikliği yapmanız gerekir:

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

Bu senaryo etkinleştirilmemişse, uygulamayı çalıştırmak iletiyle birlikte bir özel durum oluşturmaya devam eder, "Bu uygulama Windows platformu FIPS tarafından doğrulanan şifreleme algoritmalarının bir parçası değil."

**Visual Studio ile dinamik güncelleştirme kullanılırken iş akışı geliştirmeleri İş Akışı Tasarımcısı**

İş Akışı Tasarımcısı, FlowChart etkinlik Tasarımcısı ve diğer Iş akışı etkinliği tasarımcıları artık <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> yöntemi çağrıldıktan sonra kaydedilmiş iş akışlarını başarıyla yükler ve görüntüler. .NET Framework 4.6.2 önce .NET Framework sürümlerinde, <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> çağrıldıktan sonra kaydedilmiş bir iş akışı için Visual Studio 'da bir XAML dosyası yüklemek aşağıdaki sorunlara neden olabilir:

- İş Akışı Tasarımcısı XAML dosyasını doğru bir şekilde yükleyemez (<xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> satırın sonunda olduğunda).

- Akış çizelgesi etkinlik Tasarımcısı veya diğer Iş akışı etkinliği tasarımcıları, eklenen özellik değerlerinin aksine tüm nesneleri varsayılan konumlarında görüntüleyebilir.

<a name="clickonce-1" />

### <a name="clickonce"></a>ClickOnce

ClickOnce, zaten desteklediği 1,0 protokolüne ek olarak TLS 1,1 ve TLS 1,2 ' yi destekleyecek şekilde güncelleştirilmiştir. ClickOnce hangi protokolün gerekli olduğunu otomatik olarak algılar; TLS 1,1 ve 1,2 desteğini etkinleştirmek için ClickOnce uygulaması içinde ek adım gerekmez.

<a name="UWPConvert" />

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Windows Forms ve WPF uygulamalarını UWP uygulamalarına dönüştürme

Windows artık WPF ve Windows Forms uygulamalar dahil olmak üzere var olan Windows masaüstü uygulamalarını Evrensel Windows Platformu (UWP) uygulamasına getirmeye yönelik yetenekler sunmaktadır. Bu teknoloji, mevcut kod tabanınızı UWP 'ye kademeli olarak geçirmenize olanak tanıyarak bir köprü görevi görür ve böylece uygulamanızı tüm Windows 10 cihazlarına taşıyabilirsiniz.

Dönüştürülmüş masaüstü uygulamaları, UWP API 'Lerinin, canlı kutucuk ve bildirimler gibi özellikleri etkinleştirmek için erişilebilir hale getiren UWP uygulamalarının uygulama kimliğiyle benzer bir uygulama kimliği elde edebilir. Uygulama, daha önce olduğu gibi davranmaya devam eder ve tam güven uygulaması olarak çalışır. Uygulama dönüştürüldükten sonra, bir uyarlamalı Kullanıcı arabirimi eklemek için mevcut tam güven işlemine bir uygulama kapsayıcısı işlemi eklenebilir. Tüm işlevler uygulama kapsayıcısı işlemine taşındığında, tam güven işlemi kaldırılabilir ve yeni UWP uygulaması tüm Windows 10 cihazlarında kullanılabilir hale getirilebilir.

<a name="Debug462" />

### <a name="debugging-improvements"></a>Hata ayıklama geliştirmeleri

*Yönetilmeyen hata ayıklama API 'si* , bir <xref:System.NullReferenceException> oluşturulduğunda ek analizler gerçekleştirmek için .NET Framework geliştirilmiştir. böylece, tek bir kaynak kodu satırındaki hangi değişkenin `null`olduğunu tespit etmek mümkündür.   Bu senaryoyu desteklemek için, yönetilmeyen hata ayıklama API 'sine aşağıdaki API 'Ler eklenmiştir.

- Yönetilen değişkenlerin yerel evlerini açığa çıkaran [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ıcordebugvariablehome](../unmanaged-api/debugging/icordebugvariablehome-interface.md)ve [ıcordebugvariablehomeenum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) arabirimleri. Bu, bir <xref:System.NullReferenceException> gerçekleştiğinde hata ayıklayıcıların bazı kod akışı analizini yapmasına ve `null`yerel konuma karşılık gelen yönetilen değişkeni belirlemede geriye doğru çalışabilmesine olanak sağlar.

- [ICorDebugType2:: GetTypeId](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) yöntemi ıcordebugtype için [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md)bir eşleme sağlar ve bu da hata ayıklayıcının ICorDebugType örneği olmadan bir [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) almasına olanak tanır. [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) mevcut API 'ler, daha sonra türün sınıf yerleşimini belirlemede kullanılabilir.

<a name="v461" />

## <a name="whats-new-in-net-framework-461"></a>.NET Framework 4.6.1 yenilikleri

.NET Framework 4.6.1, aşağıdaki alanlardaki yeni özellikler içerir:

- [Şifreleme](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profil Oluşturma](#Profile461)

- [NGen](#NGEN461)

.NET Framework 4.6.1 hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [.NET Framework 4.6.1 listesi](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-changes.md)

- [4.6.1 'de uygulama uyumluluğu](../migration-guide/application-compatibility.md)

- [.NET Framework API farkı](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (GitHub üzerinde)

<a name="Crypto" />

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Şifreleme: ECDSA içeren x509 sertifikaları için destek

.NET Framework 4,6, x509 sertifikaları için RSACng desteğini ekledi. .NET Framework 4.6.1 ECDSA (Eliptik Eğri dijital Imza algoritması) x509 sertifikaları için destek ekler.

ECDSA, daha iyi performans sağlar ve RSA 'dan daha güvenli bir şifreleme algoritmasıdır ve Aktarım Katmanı Güvenliği (TLS) performansının ve ölçeklenebilirliğinin sorun olduğu durumlarda mükemmel bir seçimdir. .NET Framework uygulama, çağrıları mevcut Windows işlevlerine kaydırır.

Aşağıdaki örnek kod, .NET Framework 4.6.1 eklenen ECDSA x509 sertifikaları için yeni desteği kullanarak bir bayt akışı için imza oluşturmanın ne kadar kolay olduğunu gösterir.

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

Bu, .NET Framework 4,6 ' de imza oluşturmak için gereken koda işaretlenmiş bir kontrast sunar.

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461" />

### <a name="adonet"></a>ADO.NET

ADO.NET 'e aşağıdakiler eklenmiştir:

**Donanım korumalı anahtarlar için Always Encrypted desteği**

ADO.NET artık Always Encrypted sütunlu ana anahtarların donanım güvenlik modüllerinde (HSM 'ler) yerel olarak depolanmasını desteklemektedir. Bu destek sayesinde müşteriler, özel sütun ana anahtar deposu sağlayıcıları yazmak ve bunları uygulamalara kaydetmek zorunda kalmadan HSM 'lerde depolanan Asimetrik Anahtarlarla faydalanabilir.

Müşterilerin HSM 'de depolanan sütun ana anahtarlarıyla korunan Always Encrypted verilerine erişmek için, uygulama sunucularına veya istemci bilgisayarlara HSM satıcı tarafından sunulan CSP sağlayıcısını veya CNG anahtar deposu sağlayıcılarını yüklemeleri gerekir.

**AlwaysOn <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> bağlantı davranışı geliştirildi**

SqlClient artık otomatik olarak bir AlwaysOn kullanılabilirlik grubuna (AG) daha hızlı bağlantılar sağlar. Uygulamanızın farklı bir alt ağda bir AlwaysOn kullanılabilirlik grubuna (AG) bağlanıp bağlanmadığını saydam bir şekilde algılar ve geçerli etkin sunucuyu hızlıca bulup sunucuya bağlantı sağlar. Bu sürümden önce, bir uygulamanın bir AlwaysOn kullanılabilirlik grubuna bağlanmakta olduğunu göstermek için bağlantı dizesini `"MultisubnetFailover=true"` içerecek şekilde ayarlaması gerekiyordu. Bağlantı anahtar sözcüğünü `true`olarak ayarlamadan, bir uygulama bir AlwaysOn kullanılabilirlik grubuna bağlanılırken bir zaman aşımı yaşar. Bu sürümde, bir uygulamanın artık `true` <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> *ayarlaması gerekmez.* Always on kullanılabilirlik grupları için SqlClient desteği hakkında daha fazla bilgi için bkz. [yüksek kullanılabilirlik Için SqlClient desteği, olağanüstü durum kurtarma](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

<a name="WPF461" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Windows Presentation Foundation birkaç iyileştirme ve değişiklik içerir.

**İyileştirilmiş performans**

Dokunma olaylarının tetiklendiği gecikme .NET Framework 4.6.1 düzeltildi. Ayrıca, bir <xref:System.Windows.Controls.RichTextBox> denetimine yazmak hızlı giriş sırasında işleme iş parçacığını artık erişemez.

**Yazım denetimi geliştirmeleri**

WPF 'deki yazım denetleyicisi, Windows 8.1 ve sonraki sürümlerinde, yazım denetimi ek dilleri için işletim sistemi desteğinden yararlanmak üzere güncelleştirilmiştir.  Windows 8.1 öncesindeki Windows sürümlerindeki işlevlerde değişiklik yoktur.

.NET Framework önceki sürümlerinde olduğu gibi, aşağıdaki sırayla bilgi arayarak <xref:System.Windows.Controls.TextBox> denetim Ora <xref:System.Windows.Controls.RichTextBox> bloğunun dili algılanır:

- varsa `xml:lang`.

- Geçerli giriş dili.

- Geçerli iş parçacığı kültürü.

WPF dil desteği hakkında daha fazla bilgi için, [.NET Framework 4.6.1 özellikleri hakkında WPF blog](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/)gönderisi bölümüne bakın.

**Kullanıcı başına özel sözlükler için ek destek**

WPF .NET Framework 4.6.1 içinde, genel olarak kaydedilen özel sözlükleri tanır. Bu özellik, denetimleri her denetim için kaydetme özelliğine ek olarak kullanılabilir.

WPF 'nin önceki sürümlerinde özel sözlükler dışlanan kelimeleri ve otomatik düzeltme listelerini tanımıyor. Windows 8.1 ve Windows 10 ' da `%AppData%\Microsoft\Spelling\<language tag>` dizin altına yerleştirilebilecek dosyaların kullanımı ile desteklenir.  Bu dosyalar için aşağıdaki kurallar geçerlidir:

- Dosyalar. dic uzantılarına sahip olmalıdır (eklenen kelimeler için),. exc (dışlanan kelimeler için) veya. ACL (otomatik düzeltme için).

- Dosyalar, bayt sırası Işareti (BOM) ile başlayan UTF-16 LE düz metin olmalıdır.

- Her satır bir sözcükten (eklenen ve dışlanan sözcük listelerinde) ya da dikey çubukla ("&#124;") (otomatik düzeltme sözcük listesinde) ayrılmış sözcükler içeren bir otomatik düzeltme çiftinden oluşmalıdır.

- Bu dosyalar salt okunurdur ve sistem tarafından değiştirilmez.

> [!NOTE]
> Bu yeni dosya biçimleri WPF yazım denetimi API 'Leri tarafından doğrudan desteklenmez ve uygulamalarda WPF 'ye sağlanan özel sözlüklerin. Lex dosyalarını kullanmaya devam etmesi gerekir.

**Örnekler**

[Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples) GitHub deposunda birçok WPF örneği vardır. Bize bir çekme isteği göndererek veya bir [GitHub sorunu](https://github.com/Microsoft/WPF-Samples/issues)açarak örneklerimizi geliştirmemize yardımcı olun.

**DirectX uzantıları**

WPF, DX10 ve DX11 içeriğiyle birlikte çalışabilmeyi kolaylaştıran yeni <xref:System.Windows.Interop.D3DImage> uygulamaları sağlayan bir [NuGet paketi](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) içerir. Bu paketin kodu açık kaynaklıdır ve [GitHub 'da](https://github.com/Microsoft/WPFDXInterop)kullanılabilir.

<a name="WWF461" />

### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation: Işlemler

<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> yöntemi artık işlemi yükseltmek için MSDTC dışında bir dağıtılmış işlem yöneticisi kullanabilir. Bunu, yeni <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> aşırı yüküne bir GUID işlem Promoter tanımlayıcısı belirterek yapabilirsiniz. Bu işlem başarılı olursa, işlemin özelliklerine yerleştirilmiş sınırlamalar vardır. MSDTC olmayan bir işlem promosyonu kaydedildikten sonra, bu yöntemler MSDTC 'ye yükseltme gerektirdiğinden aşağıdaki yöntemler bir <xref:System.Transactions.TransactionPromotionException> oluşturur:

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

MSDTC olmayan bir işlem Promoter kaydedildikten sonra, tanımladığı protokoller kullanılarak gelecekteki dayanıklı kayıtlar için kullanılmalıdır. İşlem Promoter 'ın <xref:System.Guid>, <xref:System.Transactions.Transaction.PromoterType%2A> özelliği kullanılarak elde edilebilir. İşlem yükseltildiğinde, işlem Promoter, yükseltilen belirteci temsil eden bir <xref:System.Byte> dizisi sağlar. Bir uygulama, <xref:System.Transactions.Transaction.GetPromotedToken%2A> yöntemiyle MSDTC olmayan bir yükseltilen işlem için yükseltilen belirteci elde edebilir.

Yeni <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> aşırı yüklemesinin kullanıcıları, yükseltme işleminin başarıyla tamamlanabilmesi için belirli bir çağrı sırasını izlemelidir. Bu kurallar yöntemin belgelerinde belgelenmiştir.

<a name="Profile461" />

### <a name="profiling"></a>Profil Oluşturma

Yönetilmeyen profil oluşturma API 'SI aşağıdaki şekilde geliştirilmiştir:

- [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) arabirimindeki pdb 'leri 'e erişmek için daha iyi destek.

  ASP.NET Core, derleme işlemleri için Roslyn tarafından bellek içinde derlenmesi çok daha yaygın hale geliyor. Profil oluşturma araçları kuran geliştiriciler için bu, geçmişte diskte serileştirilmiş olan pdb 'leri artık mevcut olmayabilir. Profil Oluşturucu araçları genellikle kodu, kod kapsamı veya satır içi performans analizi gibi görevler için kaynak satırlara eşlemek için pdb 'leri kullanır. [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) arabirimi artık iki yeni yöntem Içerir: [ICorProfilerInfo7:: GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) ve [ICorProfilerInfo7:: ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), bu Profiler araçlarının yenı API 'leri kullanarak bellek içi pdb verilerine erişimi sağlamak için, bir profil oluşturucu bellek içi pdb 'nin içeriğini bayt dizisi olarak edinebilir ve sonra işleyebilir veya diske serileştirmez.

- ICorProfiler arabirimiyle daha iyi izleme.

  Dinamik izleme için `ICorProfiler` API 'Leri yeniden JIT işlevini kullanan profil oluşturucular artık bazı meta verileri değiştirebilir. Daha önce böyle araçlar, herhangi bir zamanda Il 'yi işaretleyebilir, ancak meta veriler yalnızca modül yükleme sırasında değiştirilebilir. Il meta verilere başvurduğundan, bu, yapılabilecek izleme türlerini sınırlandırıyor. Modül yüklendikten sonra yeni `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`ve `UserString` kayıtları ekleyerek meta veri düzenlemelerinin bir alt kümesini desteklemek üzere [ICorProfilerInfo7:: ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) metodunu ekleyerek bu limitlerden bazılarını yükseltilmemiş sunuyoruz. Bu değişiklik, mümkün olan çok daha geniş bir izleme sağlar.

<a name="NGEN461" />

### <a name="native-image-generator-ngen-pdbs"></a>Yerel Görüntü Oluşturucu (NGEN) pdb 'leri

Çapraz makine olay izleme, müşterilerin A makinesinde bir programı profilini oluşturmasını ve B makinesi üzerinde kaynak satırı eşleme ile profil oluşturma verilerine bakmaya olanak sağlar. .NET Framework önceki sürümlerini kullanarak, Kullanıcı profili oluşturulan tüm modülleri ve yerel görüntüleri profili oluşturulmuş Kaynak-yerel eşlemeyi oluşturmak için Il PDB 'sini içeren analiz makinesine makine. Bu işlem, dosyalar görece küçük olduğunda (örneğin, telefon uygulamaları için), dosyalar masaüstü sistemlerinde çok büyük olabilir ve kopyalamak için önemli bir zaman gerekebilir.

Ngen pdb 'leri ile NGen, Il PDB 'ye bağımlılık olmadan IL-yerel eşlemeyi içeren bir PDB oluşturabilir. Makineler arası olay izleme senaryolarımızda, A makinesi tarafından oluşturulan yerel görüntü PDB 'sini B makinesine kopyalamak ve Il PDB 'nin kaynaktan Il eşlemesini ve yerel görüntü PDB 'nin Il-to-to-Native eşlemesini okumak için [hata ayıklama arabirimi erişim API 'lerini](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) kullanmak için gereklidir. Her iki eşlemeyi de birleştirmek, kaynaktan yerel eşleme sağlar. Yerel görüntü PDB tüm modüllerden ve yerel görüntülerden çok daha küçük olduğundan, A makinesinden B makinesine kopyalama işlemi çok daha hızlıdır.

<a name="v46" />

## <a name="whats-new-in-net-2015"></a>.NET 2015 ' deki yenilikler

.NET 2015, 4,6 ve .NET Core .NET Framework sunmaktadır. Bazı yeni özellikler için geçerlidir ve diğer özellikler .NET Framework 4,6 veya .NET Core 'a özgüdür.

- **ASP.NET Core**

  .NET 2015, modern bulut tabanlı uygulamalar oluşturmak için yalın bir .NET uygulaması olan ASP.NET Core içerir. ASP.NET Core modüler olduğundan, yalnızca uygulamanızda gerekli olan özellikleri ekleyebilirsiniz. IIS 'de veya özel bir işlemde barındırılabilecek ve aynı sunucuda .NET Framework farklı sürümleriyle uygulamalar çalıştırabilirsiniz. Bulut dağıtımı için tasarlanan yeni bir ortam yapılandırma sistemi içerir.

  MVC, Web API 'SI ve Web sayfaları, MVC 6 adlı tek bir çerçevede birleştirilmiştir. Visual Studio 2015 veya sonraki sürümlerde araçlar aracılığıyla ASP.NET Core uygulamalar derleyebilirsiniz. Mevcut uygulamalarınız yeni .NET Framework çalışacaktır; Ancak, MVC 6 veya SignalR 3 kullanan bir uygulama oluşturmak için Visual Studio 2015 veya sonraki sürümlerde proje sistemini kullanmanız gerekir.

  Bilgi için bkz. [ASP.NET Core](/aspnet/core/).

- **ASP.NET güncelleştirmeleri**

  - **Zaman uyumsuz yanıt Temizleme için görev tabanlı API**

    ASP.NET artık, zaman uyumsuz yanıt Temizleme için basit bir görev tabanlı API sağlıyor <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, bu da yanıtların, dilinizin `async/await` desteği kullanılarak zaman uyumsuz olarak temizlenmesini sağlar.

  - **Model bağlama, görev döndüren yöntemleri destekler**

    .NET Framework 4,5 ' de ASP.NET, Web Forms sayfalarındaki ve Kullanıcı denetimlerindeki CRUD tabanlı veri işlemlerine Genişletilebilir, kod odaklı bir yaklaşım uygulayan model bağlama özelliğini ekledi. Model bağlama sistemi artık <xref:System.Threading.Tasks.Task>döndüren model bağlama yöntemlerini desteklemektedir. Bu özellik, Web Forms geliştiricilerin, Entity Framework dahil olmak üzere daha yeni sürümleri kullanırken veri bağlama sistemi sayesinde, zaman uyumsuz olan ölçeklenebilirlik avantajlarını elde etmesine olanak tanır.

    Zaman uyumsuz model bağlama `aspnet:EnableAsyncModelBinding` yapılandırma ayarı tarafından denetlenir.

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    Uygulamalar üzerinde .NET Framework 4,6 ' i hedefleyin, varsayılan olarak `true`. .NET Framework önceki bir sürümünü hedefleyen .NET Framework 4,6 üzerinde çalışan uygulamalarda, varsayılan olarak `false`. Yapılandırma ayarı `true`olarak ayarlanarak etkinleştirilebilir.

  - **HTTP/2 desteği (Windows 10)**

    [Http/2](https://www.wikipedia.org/wiki/HTTP/2) , çok daha iyi bağlantı kullanımı (istemci ve sunucu arasında daha az gidiş dönüş) sağlayan yenı bir http Protokolü sürümüdür ve bu sayede kullanıcılar için daha düşük gecikme süresi Web sayfası yüklemesi oluşur.  Web sayfaları (hizmetler 'in aksine) HTTP/2 ' den en iyi şekilde faydalanır çünkü protokol, tek bir deneyimin bir parçası olarak istenen birden çok yapıtı için iyileştirmiştir. .NET Framework 4,6 ' de ASP.NET 'e HTTP/2 desteği eklenmiştir. Ağ işlevselliği birden çok katmanda mevcut olduğundan, Windows 'da, IIS 'de ve ASP.NET ' de HTTP/2 ' yi etkinleştirmek için yeni özellikler gerekiyordu. ASP.NET ile HTTP/2 kullanmak için Windows 10 ' da çalıştırıyor olmanız gerekir.

    HTTP/2 Ayrıca, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> API kullanan Windows 10 Evrensel Windows Platformu (UWP) uygulamaları için varsayılan olarak desteklenir.

    ASP.NET uygulamalarında [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) özelliğini kullanmanın bir yolunu sağlamak için <xref:System.Web.HttpResponse> sınıfına <xref:System.Web.HttpResponse.PushPromise%28System.String%29> ve <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>olmak üzere iki aşırı yüklemeye sahip yeni bir yöntem eklenmiştir.

    > [!NOTE]
    > ASP.NET Core HTTP/2 ' yi desteklese de, anında PROMISE özelliği için destek henüz eklenmemiş.

    Tarayıcı ve Web sunucusu (Windows üzerinde IIS) tüm işleri çalışır. Kullanıcılarınız için herhangi bir ağır kaldırma yapmanız gerekmez.

    [Büyük tarayıcıların çoğu http/2 ' yi desteklediğinden](https://www.wikipedia.org/wiki/HTTP/2), sunucunuz bunu destekliyorsa, kullanıcılarınızın http/2 desteğinden faydalanır olması olasıdır.

  - **Belirteç bağlama protokolü desteği**

    Microsoft ve Google, [belirteç bağlama protokolü](https://github.com/TokenBinding/Internet-Drafts)olarak adlandırılan kimlik doğrulamaya yönelik yeni bir yaklaşım üzerinde işbirliği yapmış. Şirket içi, kimlik doğrulama belirteçlerinin (tarayıcı önbelleğinizin) çalınabileceği ve güvenli kaynaklara (örn. banka hesabınız) parolanızı veya diğer ayrıcalıklı bilgilere ihtiyaç duymadan erişmek üzere dolandırıcıların de kullanılabilir olmasını sağlar. Bu sorunu hafifletmek için yeni protokol amaçlar.

    Belirteç bağlama protokolü Windows 10 ' da bir tarayıcı özelliği olarak uygulanır. ASP.NET uygulamalar protokolde yer alacak ve kimlik doğrulama belirteçlerinin yasal olması için doğrulanacak. İstemci ve sunucu uygulamaları, protokol tarafından belirtilen uçtan uca korumayı oluştururlar.

  - **Rastgele dize karma algoritmaları**

    .NET Framework 4,5, [rastgele bir dize karma algoritması](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)sunmuştur. Ancak, ASP.NET tarafından, kararlı bir karma koda bağımlı bazı ASP.NET özellikleri nedeniyle desteklenmez. .NET Framework 4,6 ' de, rastgele dize karma algoritmaları artık desteklenmektedir. Bu özelliği etkinleştirmek için `aspnet:UseRandomizedStringHashAlgorithm` config ayarını kullanın.

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- **ADO.NET**

  ADO .NET artık SQL Server 2016 Community Technology Preview 2 ' de (CTP2) sunulan Always Encrypted özelliğini desteklemektedir. Always Encrypted, SQL Server şifrelenmiş veriler üzerinde işlemler gerçekleştirebilir ve tüm şifreleme anahtarının en iyisi, sunucuda değil, müşterinin güvenilir ortamındaki uygulamayla birlikte bulunur. Always Encrypted, müşteri verilerinin güvenliğini sağlar, böylece DBAs düz metin verilerine erişemez. Verilerin şifrelenmesi ve şifresinin çözülmesi, sürücü düzeyinde saydam bir şekilde gerçekleşir ve mevcut uygulamalarda yapılması gereken değişiklikleri en aza indirir. Ayrıntılar için bkz. [Always Encrypted (veritabanı altyapısı)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) ve [Always Encrypted (istemci geliştirme)](/sql/relational-databases/security/encryption/always-encrypted-client-development).

- **yönetilen kod için 64 bit JıT derleyicisi**

  .NET Framework 4,6, 64 bit JıT derleyicisinin yeni bir sürümünü (özgün olarak kod adı RyuJIT) sunar. Yeni 64 bit derleyicisi, eski 64 bit JıT derleyicisi üzerinde önemli performans iyileştirmeleri sağlar. Yeni 64 bit derleyici, .NET Framework 4,6 üzerinde çalışan 64 bit süreçler için etkinleştirilmiştir. Uygulamanız 64 bit ya da AnyCPU olarak derlenirse ve bir 64-bit işletim sisteminde çalışıyorsa, 64 bitlik bir işlemde çalışır. Yeni derleyiciye geçişi mümkün olduğunca saydam hale getirmek için dikkatli olunurken, davranıştaki değişiklikler mümkündür. Yeni JıT derleyicisini kullanırken karşılaşılan sorunları doğrudan öğrenmek istiyoruz. Yeni 64-bit JıT derleyicisi ile ilgili olabilecek bir sorunla karşılaşırsanız lütfen [Microsoft Connect](https://connect.microsoft.com/) üzerinden bizimle iletişim kurun.

  Yeni 64-bit JıT derleyicisi Ayrıca, <xref:System.Numerics> ad alanındaki SıMD özellikli türlerle birlikte kullanıldığında, iyi performans iyileştirmeleri sağlayan donanım SıMD hızlandırma özelliklerini de içerir.

- **Derleme yükleyici geliştirmeleri**

  Derleme yükleyici artık, ilgili NGEN resmi yüklendikten sonra IL derlemeleri yüklemelerini kaldırarak belleği daha verimli bir şekilde kullanıyor. Bu değişiklik, başta büyük 32 bit uygulamalar (Visual Studio gibi) için faydalı olan sanal belleği azaltır ve fiziksel bellek alanından tasarruf eder.

- **Temel sınıf kitaplığı değişiklikleri**

  Temel senaryoları etkinleştirmek için .NET Framework 4,6 ' ye birçok yeni API eklenmiştir. Bunlar aşağıdaki değişiklikleri ve eklemeleri içerir:

  - **IReadOnlyCollection\<T > uygulamalar**

    Ek koleksiyonlar, <xref:System.Collections.Generic.Queue%601> ve <xref:System.Collections.Generic.Stack%601>gibi <xref:System.Collections.Generic.IReadOnlyCollection%601> uygular.

  - **CultureInfo. CurrentCulture ve CultureInfo. CurrentUICulture**

    <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özellikleri artık salt okuma yerine salt yazılır. Bu özelliklere yeni bir <xref:System.Globalization.CultureInfo> nesnesi atarsanız, `Thread.CurrentThread.CurrentCulture` özelliği tarafından tanımlanan geçerli iş parçacığı kültürü ve `Thread.CurrentThread.CurrentUICulture` özellikleri tarafından tanımlanan geçerli UI iş parçacığı kültürü de değişir.

  - **Çöp toplama geliştirmeleri (GC)**

    <xref:System.GC> sınıfı artık kritik bir yolun yürütülmesi sırasında çöp toplamaya izin vermemeyi sağlayan <xref:System.GC.TryStartNoGCRegion%2A> ve <xref:System.GC.EndNoGCRegion%2A> yöntemleri içerir.

    <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> yönteminin yeni bir aşırı yüklemesi, hem küçük nesne yığını hem de büyük nesne yığınının birlikte kullanılıp kullanılmadığını ve yalnızca swemi olduğunu denetlemenize olanak tanır.

  - **SıMD özellikli türler**

    <xref:System.Numerics> ad alanı artık <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>ve <xref:System.Numerics.Vector4>gibi birçok SıMD özellikli tür içerir.

    Yeni 64-bit JıT derleyicisi Ayrıca donanım SıMD hızlandırma özellikleri de içerdiğinden, yeni 64 bit JıT derleyicisi ile SıMD özellikli türler kullanılırken özellikle önemli performans iyileştirmeleri vardır.

  - **Şifreleme güncelleştirmeleri**

    <xref:System.Security.Cryptography?displayProperty=nameWithType> API 'SI, [WINDOWS CNG şifreleme API 'lerini](/windows/desktop/SecCNG/cng-reference)destekleyecek şekilde güncelleştiriliyor. Önceki .NET Framework sürümleri, <xref:System.Security.Cryptography?displayProperty=nameWithType> uygulamanın temeli olarak [Windows şifreleme API 'lerinin önceki bir sürümünde](/windows/desktop/SecCrypto/cryptography-portal) tamamıyla güvendi. Belirli uygulama kategorileri için önemli olan [modern şifreleme algoritmalarını](/windows/desktop/SecCNG/cng-features#suite-b-support)DESTEKLEDIĞINDEN CNG API 'sini desteklemeye yönelik isteklerdir.

    .NET Framework 4,6, Windows CNG şifreleme API 'Lerini desteklemek için aşağıdaki yeni geliştirmeleri içerir:

    - X509 sertifikaları, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` ve `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`için, mümkün olduğunda CAPı tabanlı bir uygulama yerine, CNG tabanlı bir uygulama döndüren bir genişletme yöntemleri kümesi. (Bazı smartcards, vb. için hala CAPı gerekir ve API geri dönüşü işler).

    - RSA algoritmasının CNG uygulamasını sağlayan <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> sınıfı.

    - Yaygın eylemlerin artık atama gerektirmemesi için RSA API geliştirmeleri. Örneğin, <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> nesne kullanarak verileri şifrelemek, .NET Framework önceki sürümlerinde aşağıdakiler gibi bir kod gerektirir.

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      .NET Framework 4,6 ' deki yeni şifreleme API 'Lerini kullanan kod, dönüştürmeyi önlemek için aşağıdaki şekilde yeniden yazılabilir.

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - **Tarih ve saatleri Unix zamanına veya bu saatten dönüştürmeye yönelik destek**

    <xref:System.DateTimeOffset> yapısına, tarih ve saat değerlerini UNIX zamanından veya buradan dönüştürmeyi desteklemek için aşağıdaki yeni yöntemler eklenmiştir:

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - **Uyumluluk anahtarları**

    Yeni <xref:System.AppContext> sınıfı, kitaplık yazıcılarının kullanıcılarına yönelik yeni işlevler için Tekdüzen bir geri alma mekanizması sağlamasını sağlayan yeni bir uyumluluk özelliği ekler. Bir kapatma isteğini iletmek için bileşenler arasında gevşek olarak bağlanmış bir sözleşme oluşturur. Bu özellik, genellikle mevcut işlevlere bir değişiklik yapıldığında önemlidir. Buna karşılık, yeni işlevsellik için zaten örtük bir katılım vardır.

    <xref:System.AppContext>, kitaplıklar uyumluluk anahtarlarını tanımlar ve kullanıma sunar, ancak bunlara bağlı olan kod bu anahtarları kitaplık davranışını etkileyecek şekilde ayarlayabilir. Varsayılan olarak, kitaplıklar yeni işlevselliği sağlar ve yalnızca, anahtar ayarlanmışsa (yani, önceki işlevleri sağlar) değiştirir.

    Bir uygulama (veya bir kitaplık), bağımlı bir kitaplığın tanımladığı bir anahtarın (her zaman bir <xref:System.Boolean> değeri) değerini bildirebilir. Anahtar her zaman örtük `false`. Anahtarın `true` için ayarlanması etkinleştirilir. Anahtarın `false` olarak ayarlanması, yeni davranışı sağlar.

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    Kitaplığın, bir tüketicinin anahtar değerini bildirdiğinden ve daha sonra uygun şekilde davrandığından emin olması gerekir.

    ```csharp
    if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow))
    {
        // This is the case where the switch value was not set by the application.
        // The library can choose to get the value of shouldThrow by other means.
        // If no overrides nor default values are specified, the value should be 'false'.
        // A false value implies the latest behavior.
    }

    // The library can use the value of shouldThrow to throw exceptions or not.
    if (shouldThrow)
    {
        // old code
    }
    else
    {
        // new code
    }
    ```

    ```vb
    If Not AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", shouldThrow) Then
        ' This is the case where the switch value was not set by the application.
        ' The library can choose to get the value of shouldThrow by other means.
        ' If no overrides nor default values are specified, the value should be 'false'.
        ' A false value implies the latest behavior.
    End If

    ' The library can use the value of shouldThrow to throw exceptions or not.
    If shouldThrow Then
        ' old code
    Else
        ' new code
    End If
    ```

    Bir kitaplık tarafından kullanıma sunulan resmi bir sözleşme olduklarından, anahtarlar için tutarlı bir biçim kullanmak faydalıdır. Aşağıda iki belirgin biçim verilmiştir.

    - *Anahtar*. *ad alanı*. *SwitchName*

    - *Anahtar*. *kitaplığı*. *SwitchName*

  - **Görev tabanlı zaman uyumsuz düzende yapılan değişiklikler (TAP)**

    .NET Framework 4,6 ' i hedefleyen uygulamalar için <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneleri çağıran iş parçacığının kültür ve Kullanıcı Arabirimi kültürünü devralınır. .NET Framework önceki sürümlerini hedefleyen veya .NET Framework belirli bir sürümünü hedefmayan uygulamaların davranışı etkilenmemiştir. Daha fazla bilgi için, <xref:System.Globalization.CultureInfo> sınıfı konusunun "Kültür ve görev tabanlı zaman uyumsuz işlemler" bölümüne bakın.

    <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> sınıfı, bir `async` yöntemi gibi belirli bir zaman uyumsuz Denetim akışında yerel olan çevresel verileri temsil etmenize olanak tanır. İş parçacıkları arasında veri kalıcı hale getirmek için kullanılabilir. Ayrıca, <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> özelliği açıkça değiştiği veya iş parçacığı bir bağlam geçişi ile karşılaştığından, ortam verilerinin her ne zaman değiştiğini belirten bir geri çağırma yöntemi tanımlayabilirsiniz.

    <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>ve <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, görev tabanlı zaman uyumsuz düzene (dokunarak) belirli bir durumda Tamamlanan görevleri döndürmek için eklenmiştir.

    <xref:System.IO.Pipes.NamedPipeClientStream> sınıfı artık yeni <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>zaman uyumsuz iletişimi desteklemektedir. yöntemidir.

  - **EventSource şimdi olay günlüğüne yazmayı destekliyor**

    Artık, makinede oluşturulan mevcut ETW oturumlarına ek olarak yönetim veya işletimsel iletileri olay günlüğüne kaydetmek için <xref:System.Diagnostics.Tracing.EventSource> sınıfını kullanabilirsiniz. Geçmişte, bu işlevsellik için Microsoft. Diagnostics. Tracing. EventSource NuGet paketini kullanmanız gerekiyordu. Bu işlevsellik artık 4,6 .NET Framework yerleşik olarak sunulmuştur.

    Hem NuGet paketi hem de .NET Framework 4,6 aşağıdaki özelliklerle güncelleştirilmiştir:

    - **Dinamik olaylar**

      Olay yöntemi oluşturmadan "anında" tanımlanan olaylara izin verir.

    - **Zengin yük**

      Özel olarak öznitelikli sınıfların ve dizilerin yanı sıra yük olarak geçirilecek ilkel türler sağlar

    - **Etkinlik izleme**

      , Şu anda etkin olan tüm etkinlikleri temsil eden bir KIMLIK ile aralarında olayları etiketlemek için başlatma ve durdurma olaylarına neden olur.

    Bu özellikleri desteklemek için, <xref:System.Diagnostics.Tracing.EventSource> sınıfına aşırı yüklenmiş <xref:System.Diagnostics.Tracing.EventSource.Write%2A> yöntemi eklenmiştir.

- **Windows Presentation Foundation (WPF)**

  - **HDPı geliştirmeleri**

    WPF 'de HDPı desteği artık .NET Framework 4,6 ' de daha iyidir. Kenarlıkların bulunduğu denetimlerde kırpma örneklerini azaltmak için yerleşim yuvarlama sırasında değişiklikler yapılmıştır. Varsayılan olarak, bu özellik yalnızca <xref:System.Runtime.Versioning.TargetFrameworkAttribute> .NET 4,6 olarak ayarlandıysa etkindir.  Framework 'ün önceki sürümlerini hedefleyen ancak .NET Framework 4,6 üzerinde çalışan uygulamalar, App. config dosyasının [\<runtime >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki satırı ekleyerek yeni davranışı kabul edebilir:

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    Farklı DPı ayarlarına (çok DPı Kurulum) sahip birden çok izleyiciden oluşan WPF pencereleri, artık Blacked-Out bölgeleri olmadan tamamen işlenir. Bu yeni davranışı devre dışı bırakmak için App. config dosyasının `<appSettings>` bölümüne aşağıdaki satırı ekleyerek bu davranışı iptal edebilirsiniz:

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>'ye DPı ayarı temelinde sağ imleci otomatik olarak yükleme desteği eklenmiştir.

  - **Dokunmatik daha iyidir**

    İletişim [üzerindeki müşteri raporları, .NET Framework](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) 4,6 ' de öngörülemeyen davranış üretir. Windows Mağazası uygulamaları ve WPF uygulamaları için çift dokunma eşiği artık Windows 8.1 ve üzeri sürümlerde aynıdır.

  - **Saydam alt pencere desteği**

    .NET Framework 4,6 ' de WPF, Windows 8.1 ve üzeri sürümlerde saydam alt pencereleri destekler. Bu, üst düzey Windows 'larınızı dikdörtgen olmayan ve şeffaf alt pencereler oluşturmanıza olanak sağlar. <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> özelliğini `true`olarak ayarlayarak bu özelliği etkinleştirebilirsiniz.

- **Windows Communication Foundation (WCF)**

  - **SSL desteği**

    WCF, aktarım güvenliği ve istemci kimlik doğrulamasıyla NetTcp kullanılırken SSL 3,0 ve TLS 1,0 özelliklerine ek olarak SSL sürüm TLS 1,1 ve TLS 1,2 ' yi desteklemektedir. Artık hangi protokolün kullanılacağını seçebilir veya eski daha az güvenli protokollerin devre dışı bırakılması mümkündür. Bu, <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> özelliği ayarlanarak veya bir yapılandırma dosyasına aşağıdakiler eklenerek yapılabilir.

    ```xml
    <netTcpBinding>
        <binding>
          <security mode= "None|Transport|Message|TransportWithMessageCredential" >
              <transport clientCredentialType="None|Windows|Certificate"
                        protectionLevel="None|Sign|EncryptAndSign"
                        sslProtocols="Ssl3|Tls1|Tls11|Tls12">
                </transport>
          </security>
        </binding>
    </netTcpBinding>
    ```

  - **Farklı HTTP bağlantıları kullanarak ileti gönderme**

    WCF artık kullanıcıların, farklı temel HTTP bağlantıları kullanılarak belirli iletilerin gönderilmesini sağlamasına izin veriyor. Bunu yapmak için iki yol vardır:

    - **Bağlantı grubu adı ön eki kullanma**

      Kullanıcılar, WCF 'nin bağlantı grubu adı için önek olarak kullanacağı bir dize belirtebilir. Farklı ön ekleri olan iki ileti, farklı temel HTTP bağlantıları kullanılarak gönderilir. İletinin <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> özelliğine bir anahtar/değer çifti ekleyerek ön eki ayarlarsınız. Anahtar "HttpTransportConnectionGroupNamePrefix"; değer, istenen önekidir.

    - **Farklı kanal fabrikaları kullanma**

      Kullanıcılar ayrıca, farklı kanal fabrikaları tarafından oluşturulan kanallar kullanılarak gönderilen iletilerin farklı temel HTTP bağlantıları kullanmasını sağlayan bir özelliği etkinleştirebilir. Bu özelliği etkinleştirmek için, kullanıcıların aşağıdaki `appSetting` `true`olarak ayarlaması gerekir:

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- **Windows Workflow Foundation (WWF)**

  Artık, isteği zaman aşımından önce bekleyen bir "protokol dışı" yer işareti olduğunda, bir iş akışı hizmetinin bir sıra dışı işlem isteğine açık olacağı saniye sayısını belirtebilirsiniz. "Protokol dışı" yer işareti, bekleyen alma etkinlikleriyle ilgili olmayan bir yer işaretidir. Bazı etkinlikler, kendi uygulamalarında protokol olmayan yer işaretleri oluşturur, bu nedenle protokol olmayan bir yer işaretinin mevcut olduğu açık olmayabilir. Bu durum ve seçim dahildir. Bu nedenle, bir durum makinesi ile uygulanan veya bir çekme etkinliği içeren bir iş akışı hizmetiniz varsa, muhtemelen protokol olmayan yer işaretlerine sahip olursunuz. Uygulama. config dosyanızın `appSettings` bölümüne aşağıdakine benzer bir satır ekleyerek aralığı belirtirsiniz:

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  Varsayılan değer 60 saniyedir. `value` 0 olarak ayarlandıysa, aşağıdaki gibi görünen metin ile bir hata vererek sıra dışı istekler anında reddedilir:

  ```console
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  Bu, bir sıra dışı işlem iletisi alındığında ve protokol olmayan yer işaretleri yoksa aldığınız mesajdır.

  `FilterResumeTimeoutInSeconds` öğesinin değeri sıfır değilse, protokol olmayan yer işaretleri vardır ve zaman aşımı aralığı sona erdiğinde, işlem zaman aşımı iletisiyle başarısız olur.

- **İşlemler**

  Artık <xref:System.Transactions.TransactionException> ' den türetilen bir özel durumun oluşturulmasına neden olan işlem için dağıtılmış işlem tanımlayıcıyı ekleyebilirsiniz. Bunu, App. config dosyanızın `appSettings` bölümüne aşağıdaki anahtarı ekleyerek yapabilirsiniz:

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  Varsayılan değer `false` şeklindedir.

- **Ağ**

  - **Yuva yeniden kullanımı**

    Windows 10, giden TCP bağlantıları için yerel bağlantı noktalarını yeniden kullanarak makine kaynaklarından daha iyi şekilde yararlanmasına yönelik yeni bir yüksek ölçeklenebilirlik ağ algoritması içerir. .NET Framework 4,6 yeni algoritmayı destekleyerek, .NET uygulamalarının yeni davranıştan yararlanmasını sağlar. Önceki Windows sürümlerinde, bir hizmetin ölçeklenebilirliğini, yük altında bağlantı noktası tükenmesi olmasına neden olarak sınırlayan yapay bir eşzamanlı bağlantı sınırı (genellikle 16.384) vardı.

    .NET Framework 4,6 ' de, bağlantı noktası yeniden kullanımını etkinleştirmek için iki yeni API eklenmiştir. Bu, eşzamanlı bağlantılarda 64K sınırını etkili bir şekilde kaldırır:

    - <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> numaralandırma değeri.

    - <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> özelliği.

    Varsayılan olarak, `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` kayıt defteri anahtarının `HWRPortReuseOnSocketBind` değeri 0x1 olarak ayarlanmadığı müddetçe <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> özelliği `false`. HTTP bağlantılarında yerel bağlantı noktası yeniden kullanımını etkinleştirmek için <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> özelliğini `true`olarak ayarlayın. Bu, <xref:System.Net.Http.HttpClient> ve <xref:System.Net.HttpWebRequest> giden tüm giden TCP yuvası bağlantılarının, yerel bağlantı noktası yeniden kullanımını sağlayan yeni bir Windows 10 yuva seçeneği [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options)kullanmasına neden olur.

    Yalnızca bir yuva uygulaması yazan geliştiriciler, bağlama sırasında giden yuvaların yerel bağlantı noktalarını yeniden kullanabilmesi için <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> gibi bir yöntemi çağırırken <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> seçeneğini belirtebilir.

  - **Uluslararası etki alanı adları ve puni kodu desteği**

    Uluslararası etki alanı adlarını ve zayıf kodu daha iyi desteklemek için <xref:System.Uri> sınıfına <xref:System.Uri.IdnHost%2A>yeni bir özellik eklenmiştir.

- **Windows Forms Denetimlerinde yeniden boyutlandırma.**

  Bu özellik .NET Framework 4,6 ' de <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.ToolStripSplitButton> türlerini ve bir <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> çizerken kullanılan <xref:System.Drawing.Design.UITypeEditor>özelliği tarafından belirtilen dikdörtgeni içerecek şekilde genişletildi.

  Bu onaya bağlı bir özelliktir. Etkinleştirmek için, uygulama yapılandırma (App. config) dosyasında `EnableWindowsFormsHighDpiAutoResizing` öğesini `true` olarak ayarlayın:

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Kod sayfası kodlamaları için destek**

  .NET Core öncelikle Unicode kodlamaları destekler ve varsayılan olarak, kod sayfası kodlamaları için sınırlı destek sağlar. Kod sayfası kodlamalarını <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> yöntemiyle kaydederek .NET Framework, ancak .NET Core 'ta desteklenmeyen kod sayfası kodlamaları için destek ekleyebilirsiniz. Daha fazla bilgi için bkz. <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Native**

  .NET Core 'u C# hedefleyen ve veya Visual Basic yazılan Windows 10 için Windows uygulamaları, uygulamaları Il yerine yerel koda derleyen yeni bir teknolojiden yararlanabilir. Daha hızlı başlatma ve yürütme süreleriyle nitelenen uygulamalar oluşturur. Daha fazla bilgi için bkz. [.NET Native uygulamalar derleme](../net-native/index.md). Hem JıT derleme hem de NGEN 'ten farklı olan .NET Native genel bir bakış için ve kodunuz için ne anlama geldiğini, bkz. [.NET Native ve derleme](../net-native/net-native-and-compilation.md).

  Uygulamalarınız, Visual Studio 2015 veya sonraki bir sürümü ile derlerken varsayılan olarak yerel koda derlenir. Daha fazla bilgi için bkz. [.NET Native kullanmaya](../net-native/getting-started-with-net-native.md)başlama.

  .NET Native uygulamalarında hata ayıklamayı desteklemek için, yönetilmeyen hata ayıklama API 'sine bir dizi yeni arabirim ve listeleme eklenmiştir. Daha fazla bilgi için bkz. [hata ayıklama (YÖNETILMEYEN API Başvurusu)](../unmanaged-api/debugging/index.md) konusu.

- **Açık kaynaklı .NET Framework paketleri**

  Sabit koleksiyonlar, [SIMD API 'leri](https://www.nuget.org/packages/Microsoft.Bcl.Simd)ve <xref:System.Net.Http> ad alanında bulunan gibi ağ API 'leri gibi .NET Core paketleri artık [GitHub](https://github.com/)'da açık kaynak paketleri olarak kullanılabilir. Koda erişmek için [GitHub 'da .net](https://github.com/dotnet/runtime)bölümüne bakın. Daha fazla bilgi ve bu paketlere katkıda bulunma hakkında daha fazla bilgi için bkz. GitHub 'da [.NET Core ve açık kaynak](../get-started/net-core-and-open-source.md), [.net giriş sayfası](https://github.com/dotnet/home).

<a name="v452" />

## <a name="whats-new-in-net-framework-452"></a>.NET Framework 4.5.2 yenilikleri

- **ASP.NET uygulamaları için yeni API 'Ler.** Yeni <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> ve <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> yöntemleri, yanıt, istemci uygulamasına boşaltılmakta olduğu için yanıt üst bilgilerini ve durum kodunu incelemenizi ve değiştirmenizi sağlar. <xref:System.Web.HttpApplication.PreSendRequestHeaders> ve <xref:System.Web.HttpApplication.PreSendRequestContent> olayları yerine bu yöntemleri kullanmayı düşünün; daha verimli ve güvenilir.

  <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> yöntemi, küçük arka plan iş öğelerini zamanlamanıza olanak sağlar. ASP.NET bu öğeleri izler ve tüm arka plan iş öğeleri tamamlanana kadar IIS 'nin çalışan işlemini aniden sonlandırmasını önler. Bu yöntem, ASP.NET tarafından yönetilen bir uygulama etki alanı dışında çağrılamaz.

  Yeni <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> ve <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> özellikleri, yanıt üstbilgilerinin yazılıp yazılmadığını belirten Boolean değerler döndürür. Bu özellikleri, <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> gibi API 'lere yapılan çağrıların (üstbilgiler yazılmışsa özel durumlar oluşturur) başarılı olacağını doğrulamak için kullanabilirsiniz.

- **Windows Forms Denetimlerinde yeniden boyutlandırma.** Bu özellik genişletildi. Artık, aşağıdaki ek denetimlerin bileşenlerini yeniden boyutlandırmak için sistem DPı ayarını kullanabilirsiniz (örneğin, Birleşik giriş kutularındaki aşağı açılan ok):

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  Bu onaya bağlı bir özelliktir. Etkinleştirmek için, uygulama yapılandırma (App. config) dosyasında `EnableWindowsFormsHighDpiAutoResizing` öğesini `true` olarak ayarlayın:

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Yeni iş akışı özelliği.** <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> yöntemi kullanan bir kaynak yöneticisi (ve bu nedenle <xref:System.Transactions.IPromotableSinglePhaseNotification> arabirimini uygulamak), aşağıdakileri istemek için yeni <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> yöntemini kullanabilir:

  - İşlemi bir Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) işlemine yükseltin.

  - <xref:System.Transactions.IPromotableSinglePhaseNotification>, tek aşamalı işlemeleri destekleyen dayanıklı bir kayıt olan <xref:System.Transactions.ISinglePhaseNotification>ile değiştirin.

  Bu, aynı uygulama etki alanı içinde yapılabilir ve yükseltmeyi gerçekleştirmek üzere MSDTC ile etkileşimde bulunmak için ek yönetilmeyen kod gerektirmez. Yeni yöntem yalnızca, <xref:System.Transactions?displayProperty=nameWithType> 'ten promotable kaydı tarafından uygulanan <xref:System.Transactions.IPromotableSinglePhaseNotification>`Promote` yöntemine bekleyen bir çağrı olduğunda çağrılabilir.

- **Profil oluşturma geliştirmeleri.** Aşağıdaki yeni yönetilmeyen profil oluşturma API 'Leri daha sağlam profil oluşturma sağlar:

  - [COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [COR_PRF_HIGH_MONITOR Sabit Listesi](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [GetAssemblyReferences Yöntemi](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [GetEventMask2 Yöntemi](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [SetEventMask2 Yöntemi](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [AddAssemblyReference Yöntemi](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  Önceki `ICorProfiler` uygulamalar bağımlı derlemelerin geç yüklenmesini destekliyordu. Yeni profil oluşturma API 'Leri, uygulama tam olarak başlatıldıktan sonra yüklenmesi yerine, profil oluşturucu tarafından doğrudan yüklenebilir olarak eklenen bağımlı derlemeler gerektirir. Bu değişiklik, mevcut `ICorProfiler` API 'Leri kullanıcılarını etkilemez.

- **Hata ayıklama geliştirmeleri.** Aşağıdaki yeni yönetilmeyen hata ayıklama API 'Leri, bir profil Oluşturucu ile daha iyi tümleştirme sağlar. Artık Profiler tarafından yerleştirilen meta verilere, Ayrıca, döküm hata ayıklaması sırasında derleyici ReJIT istekleri tarafından oluşturulan yerel değişkenlere ve koda erişebilirsiniz.

  - [SetWriteableMetadataUpdateMode Yöntemi](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [EnumerateLocalVariablesEx Yöntemi](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [GetLocalVariableEx Yöntemi](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [GetCodeEx Yöntemi](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [GetActiveReJitRequestILCode Yöntemi](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [GetInstrumentedILMap Yöntemi](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Olay izleme değişiklikleri.** .NET Framework 4.5.2, daha büyük bir yüzey alanı için işlem dışı, Windows için olay Izleme (ETW) tabanlı etkinlik izleme imkanı sunar. Bu, gelişmiş güç yönetimi (APM) satıcılarının, iş parçacıkları arasındaki bireysel isteklerin ve etkinliklerin maliyetlerini doğru bir şekilde izleyen hafif araçlar sağlamasına olanak sağlar.  Bu olaylar yalnızca ETW denetleyicileri etkinleştirilse tetiklenir; Bu nedenle, değişiklikler önceden yazılmış ETW kodunu veya ETW devre dışı ile çalışan kodu etkilemez.

- **Bir işlemi yükseltme ve dayanıklı bir kayda dönüştürme**

  <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType>, .NET Framework 4.5.2 ve 4,6 ' ye eklenen yeni bir API 'dir:

  ```csharp
  [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
  public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                            IPromotableSinglePhaseNotification promotableNotification,
                                            ISinglePhaseNotification enlistmentNotification,
                                            EnlistmentOptions enlistmentOptions)
  ```

  ```vb
  <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")>
  public Function PromoteAndEnlistDurable(resourceManagerIdentifier As Guid,
                                          promotableNotification As IPromotableSinglePhaseNotification,
                                          enlistmentNotification As ISinglePhaseNotification,
                                          enlistmentOptions As EnlistmentOptions) As Enlistment
  ```

  Yöntemi, <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> yöntemine yanıt olarak <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> tarafından daha önce oluşturulmuş bir kayıt tarafından kullanılabilir. İşlemi bir MSDTC işlemine yükseltmek ve promotable listesini dayanıklı bir listeye "dönüştürmek" için `System.Transactions` sorar. Bu yöntem başarıyla tamamlandıktan sonra, <xref:System.Transactions.IPromotableSinglePhaseNotification> arabirimine artık `System.Transactions`tarafından başvurulmayacak ve gelecekteki tüm bildirimler belirtilen <xref:System.Transactions.ISinglePhaseNotification> arabirimine gönderilir. Söz konusu kayıt, işlem günlüğü ve kurtarmayı destekleyen dayanıklı bir liste olarak davranmalıdır. Ayrıntılar için <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> bakın. Ayrıca, kayıt <xref:System.Transactions.ISinglePhaseNotification>desteklemelidir.  Bu yöntem, *yalnızca* bir <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> çağrısı işlenirken çağrılabilir. Böyle değilse, bir <xref:System.Transactions.TransactionException> özel durumu oluşturulur.

<a name="v451" />

## <a name="whats-new-in-net-framework-451"></a>.NET Framework 4.5.1 yenilikleri

**Nisan 2014 güncelleştirmeleri**:

- [Visual Studio 2013 güncelleştirme 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) , bu senaryoları desteklemek Için taşınabilir sınıf kitaplığı şablonlarına yönelik güncelleştirmeleri içerir:

  - Windows 8.1, Windows Phone 8,1 ve Windows Phone Silverlight 8,1 ' i hedefleyen taşınabilir kitaplıklarda Windows Çalışma Zamanı API 'Leri kullanabilirsiniz.

  - Windows 8.1 veya Windows Phone 8,1 ' i hedefliyorsanız taşınabilir kitaplıklara XAML (Windows. UI. XAML türleri) ekleyebilirsiniz. Şu XAML şablonları desteklenir: boş sayfa, kaynak sözlüğü, şablonlu denetim ve Kullanıcı denetimi.

  - Windows 8.1 ve Windows Phone 8,1 ' i hedefleyen Mağaza uygulamalarında kullanılmak üzere taşınabilir bir Windows Çalışma Zamanı bileşeni (. winmd dosyası) oluşturabilirsiniz.

  - Bir Windows Mağazası veya Windows Phone depolama sınıfı kitaplığını taşınabilir bir sınıf kitaplığı gibi yeniden hedefleyebilirsiniz.

  Bu değişiklikler hakkında daha fazla bilgi için bkz. [taşınabilir sınıf kitaplığı](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

- .NET Framework içerik kümesi artık, Windows uygulamaları oluşturmaya ve dağıtmaya yönelik bir ön derleme teknolojisi olan .NET Native belgelerini içerir. .NET Native uygulamalarınızı, daha iyi performans için, ara dil (IL) yerine yerel koda doğrudan derler. Ayrıntılar için bkz. [.NET Native uygulamalar derleme](../net-native/index.md).

- [.NET Framework başvuru kaynağı](https://referencesource.microsoft.com/) yeni bir gözatma deneyimi ve gelişmiş işlevsellik sağlar. Artık .NET Framework kaynak koduna göz atabilir, çevrimdışı görüntüleme [başvurusunu indirebilir](https://referencesource.microsoft.com/download.html) ve hata ayıklama sırasında kaynaklarda (yayama ve güncelleştirmeler dahil) ilerme yapabilirsiniz. Daha fazla bilgi için bkz. [.net başvuru kaynağı için yeni bir görünüm](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/)olan blog girişi.

.NET Framework 4.5.1 ' deki temel sınıflardaki yeni özellikler ve geliştirmeler şunları içerir:

- Derlemeler için otomatik bağlama yeniden yönlendirme. Visual Studio 2013 başlayarak, .NET Framework 4.5.1 hedefleyen bir uygulama derlerken, uygulamanız veya bileşenleri aynı derlemenin birden çok sürümüne başvurduğu zaman bağlama yeniden yönlendirmeleri uygulama yapılandırma dosyasına eklenebilir. Ayrıca, .NET Framework eski sürümlerini hedefleyen projeler için bu özelliği etkinleştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: otomatik bağlama yeniden yönlendirmeyi etkinleştirme ve devre dışı bırakma](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

- Geliştiricilerin sunucu ve bulut uygulamalarının performansını geliştirmesine yardımcı olmak için tanılama bilgilerini toplama özelliği. Daha fazla bilgi için <xref:System.Diagnostics.Tracing.EventSource> sınıfındaki <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> ve <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> yöntemlerine bakın.

- Çöp toplama sırasında büyük nesne yığınını (LOH) açık bir şekilde sıkıştırabilme. Daha fazla bilgi için <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> özelliğine bakın.

- .NET Framework güncelleştirmesinden sonra ASP.NET uygulama askıya alma, çok çekirdekli JıT geliştirmeleri ve daha hızlı uygulama başlatma gibi ek performans geliştirmeleri. Ayrıntılar için bkz. [.NET Framework 4.5.1 ilanı](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) ve [ASP.net App Suspend](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) blog gönderisi.

Windows Forms iyileştirmeleri şunlardır:

- Windows Forms Denetimlerinde yeniden boyutlandırma. Denetim bileşenlerini (örneğin, bir özellik kılavuzunda görünen simgeler) uygulamanızın uygulama yapılandırma dosyasında (App. config) bir girdiyle değiştirerek yeniden boyutlandırmak için sistem DPı ayarını kullanabilirsiniz. Bu özellik şu anda aşağıdaki Windows Forms Denetimlerinde desteklenmektedir:

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  - <xref:System.Windows.Forms.DataGridView> bazı yönleri (desteklenen ek denetimler için bkz. [4.5.2 sürümündeki yeni özellikler](#v452) )

  Bu özelliği etkinleştirmek için yapılandırma dosyasına (App. config) yeni bir \<appSettings > öğesi ekleyin ve `EnableWindowsFormsHighDpiAutoResizing` öğesini `true`olarak ayarlayın:

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

Visual Studio 2013 .NET Framework uygulamalarınızın hata ayıklaması sırasında iyileştirmeler şunlardır:

- Visual Studio hata ayıklayıcısındaki değerleri döndürün. Visual Studio 2013 yönetilen bir uygulamada hata ayıklarken, oto 'Lar penceresi yöntemlerin dönüş türlerini ve değerlerini görüntüler. Bu bilgiler Masaüstü, Windows Mağazası ve Windows Phone uygulamaları için kullanılabilir. Daha fazla bilgi için bkz. [Yöntem çağrılarının dönüş değerlerini inceleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).

- 64 bit uygulamalar için Düzenle ve devam et. Visual Studio 2013 Masaüstü, Windows Mağazası ve Windows Phone 64 bitlik yönetilen uygulamalar için Düzenle ve devam et özelliğini destekler. Mevcut sınırlamalar hem 32-bit hem de 64-bit uygulamalar için geçerli kalır ( [desteklenen kod değişikliklerininC#](/visualstudio/debugger/supported-code-changes-csharp) son bölümüne bakın () makalesinin).

- Zaman uyumsuz olarak algılayan hata ayıklama. Visual Studio 2013, zaman uyumsuz uygulamalarda hata ayıklamayı kolaylaştırmak için, çağrı yığını zaman uyumsuz programlamayı desteklemek için derleyiciler tarafından belirtilen altyapı kodunu gizler ve ayrıca mantıksal program yürütmeyi daha fazla takip edebilmeniz için mantıksal üst çerçevelerde zincirler NET. Bir Görevler penceresi, paralel görevler penceresinin yerini alır ve belirli bir kesme noktasıyla ilgili görevleri görüntüler ve ayrıca, şu anda etkin olan veya uygulamada zamanlanan diğer görevleri görüntüler. Bu özellik hakkında bilgi edinmek için, [.NET Framework 4.5.1 duyurusunun](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/)"zaman uyumsuz algılayan hata ayıklama" bölümünde bulabilirsiniz.

- Windows Çalışma Zamanı bileşenleri için daha iyi özel durum desteği. Windows 8.1, Windows Mağazası uygulamalarından kaynaklanan özel durumlar, özel duruma neden olan hata hakkındaki bilgileri, dil sınırları boyunca korur. Bu özellik hakkında bilgi edinmek için [.NET Framework 4.5.1 duyurusunun](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/)"Windows Mağazası uygulama geliştirme" bölümünde bulabilirsiniz.

Visual Studio 2013 başlayarak, Windows 8. x mağaza uygulamalarını ve masaüstü uygulamalarını en iyi duruma getirmek için [yönetilen profil temelli Iyileştirme aracı 'nı (Mpgo. exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) kullanabilirsiniz.

ASP.NET 4.5.1 içindeki yeni özellikler için bkz. [Visual Studio 2013 Sürüm notları ASP.NET and Web Tools](/aspnet/visual-studio/overview/2013/release-notes).

<a name="v45" />

## <a name="whats-new-in-net-framework-45"></a>{1&gt;{2&gt;.NET Framework 4.5'teki Yenilikler&lt;2}&lt;1}

### <a name="base-classes"></a>Temel sınıflar

- Dağıtım sırasında .NET Framework 4 uygulamalarını algılayıp kapatarak sistem yeniden başlatmaları azaltma özelliği. Bkz. [.NET Framework 4,5 yüklemeleri sırasında sistem yeniden başlatmaları azaltma](../deployment/reducing-system-restarts.md).

- 64-bit platformlarda 2 gigabayttan (GB) daha büyük diziler için destek. Bu özellik uygulama yapılandırma dosyasında etkinleştirilebilir. Nesne boyutu ve dizi boyutu üzerindeki diğer kısıtlamaları da listeleyen [\<gcAllowVeryLargeObjects > öğesine](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)bakın.

- Sunucular için arka plan atık toplama ile daha iyi performans. .NET Framework 4,5 ' de sunucu çöp toplama kullandığınızda, arka plan atık toplama otomatik olarak etkinleştirilir. [Çöp toplama temelleri](../../standard/garbage-collection/fundamentals.md) konusunun arka plan sunucusu çöp toplama bölümüne bakın.

- Arka plan tam zamanında (JıT) derleme, isteğe bağlı olarak, uygulama performansını artırmak için çok çekirdekli işlemcilerde kullanılabilir. Bkz. <xref:System.Runtime.ProfileOptimization>.

- Normal ifade altyapısının zaman aşımına uğramadan önce normal ifadeyi çözmeyi ne kadar süreyle deneyeceğini sınırlayabilme olanağı. <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> özelliğine bakın.

- Bir uygulama etki alanı için varsayılan kültürü tanımlama özelliği. <xref:System.Globalization.CultureInfo> sınıfına bakın.

- Unicode (UTF-16) kodlaması için konsol desteği. <xref:System.Console> sınıfına bakın.

- Kültürel dize sıralaması ve karşılaştırma verilerinin sürümü oluşturma desteği. <xref:System.Globalization.SortVersion> sınıfına bakın.

- Kaynakları alırken daha iyi performans. Bkz. [kaynakları paketleme ve dağıtma](../resources/packaging-and-deploying-resources-in-desktop-apps.md).

- Sıkıştırılmış bir dosyanın boyutunu azaltmak için ZIP sıkıştırma geliştirmeleri. Bkz. <xref:System.IO.Compression?displayProperty=nameWithType> ad alanı.

- <xref:System.Reflection.Context.CustomReflectionContext> sınıfı aracılığıyla varsayılan yansıma davranışını geçersiz kılmak için yansıma bağlamını özelleştirme özelliği.

- Windows 8 ' de <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> sınıfı kullanıldığında, uygulamalar (ıDNA) standardında uluslararası etki alanı adlarının 2008 sürümü için destek.

- Windows 8 ' de .NET Framework kullanıldığında, Unicode 6,0 uygulayan işletim sistemine dize karşılaştırması temsili. Diğer platformlarda çalışırken .NET Framework, Unicode 5. x uygulayan kendi dize karşılaştırma verilerini içerir. <xref:System.Globalization.SortVersion> sınıfının <xref:System.String> sınıfına ve açıklamalar bölümüne bakın.

- Her uygulama etki alanı temelinde dizeler için karma kodları hesaplama özelliği. Bkz. [\<UseRandomizedStringHashAlgorithm > öğesi](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- <xref:System.Type> ve <xref:System.Reflection.TypeInfo> sınıfları arasında bölünmüş tür yansıtma desteği. Bkz. [Windows Mağazası uygulamaları için .NET Framework yansıtma](../reflection-and-codedom/reflection-for-windows-store-apps.md).

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

.NET Framework 4,5 ' de, Managed Extensibility Framework (MEF) aşağıdaki yeni özellikleri sağlar:

- Genel türler için destek.

- Öznitelikler yerine adlandırma kurallarına göre parçalar oluşturmanıza olanak sağlayan kural tabanlı programlama modeli.

- Birden çok kapsam.

- Windows 8. x Mağazası uygulamaları oluştururken kullanabileceğiniz MEF alt kümesi. Bu alt küme NuGet galerisinden [indirilebilir bir paket](https://www.nuget.org/packages/Microsoft.Composition) olarak kullanılabilir. Paketi yüklemek için, projenizi Visual Studio 'da açın, **Proje** menüsünden **NuGet Paketlerini Yönet** ' i seçin ve `Microsoft.Composition` paketini çevrimiçi olarak arayın.

Daha fazla bilgi için bkz. [Managed Extensibility Framework (MEF)](../mef/index.md).

### <a name="asynchronous-file-operations"></a>Zaman uyumsuz dosya işlemleri

.NET Framework 4,5 ' de, C# ve Visual Basic dillerine yeni zaman uyumsuz özellikler eklenmiştir. Bu özellikler, zaman uyumsuz işlemleri gerçekleştirmek için görev tabanlı bir model ekler. Bu yeni modeli kullanmak için g/ç sınıflarında zaman uyumsuz yöntemleri kullanın. Bkz. [zaman uyumsuz dosya g/ç](../../standard/io/asynchronous-file-i-o.md).

<a name="tools" />

### <a name="tools"></a>Araçları

.NET Framework 4,5, kaynak dosya Oluşturucu (Resgen. exe), bir. resources .NET Framework dosyasındaki Windows 8. x Mağaza uygulamalarında kullanılmak üzere bir. resw dosyası oluşturmanıza olanak sağlar. Daha fazla bilgi için bkz. [Resgen. exe (kaynak dosya Oluşturucu)](../tools/resgen-exe-resource-file-generator.md).

Yönetilen profil temelli Iyileştirme (Mpgo. exe), yerel görüntü derlemelerini iyileştirerek uygulama başlangıç süresini, bellek kullanımını (çalışma kümesi boyutu) ve aktarım hızını iyileştirmenize olanak sağlar. Komut satırı aracı, yerel görüntü uygulama derlemeleri için profil verileri oluşturur. Bkz. [Mpgo. exe (yönetilen profil temelli Iyileştirme aracı)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Visual Studio 2013 başlayarak, Mpgo. exe ' yi kullanarak Windows 8. x mağaza uygulamalarını ve masaüstü uygulamalarını en iyi duruma getirebilirsiniz.

<a name="parallel" />

### <a name="parallel-computing"></a>Paralel bilgi işlem

.NET Framework 4,5, paralel bilgi işlem için çeşitli yeni özellikler ve iyileştirmeler sağlar. Bunlar, geliştirilmiş performans, artırılmış denetim, zaman uyumsuz programlama için geliştirilmiş destek, yeni bir veri akışı kitaplığı ve paralel hata ayıklama ve performans analizi için geliştirilmiş destek içerir. .Net blogu ile paralel programlamada [.net 4,5 ' de paralellik Için nasıl yeni](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) bir giriş olduğuna bakın.

<a name="web" />

### <a name="web"></a>Web

Web Forms, WebSocket desteği, zaman uyumsuz işleyiciler, performans geliştirmeleri ve diğer birçok özellik için ASP.NET 4,5 ve 4.5.1 model bağlama ekleyin. Daha fazla bilgi için aşağıdaki kaynaklara bakın:

- [ASP.NET 4,5 ve Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))

- [Visual Studio 2013 için ASP.NET and Web Tools Sürüm Notları](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking-a-namenetworking-"></a>Ağ <a name="networking" />

.NET Framework 4,5, HTTP uygulamaları için yeni bir programlama arabirimi sağlar. Daha fazla bilgi için bkz. yeni <xref:System.Net.Http?displayProperty=nameWithType> ve <xref:System.Net.Http.Headers?displayProperty=nameWithType> ad alanları.

Ayrıca, mevcut <xref:System.Net.HttpListener> ve ilgili sınıfları kullanarak bir WebSocket bağlantısı kabul etmek ve bunlarla etkileşim kurmak için yeni bir programlama arabirimi de mevcuttur. Daha fazla bilgi için bkz. yeni <xref:System.Net.WebSockets> ad alanı ve <xref:System.Net.HttpListener> sınıfı.

Ayrıca, 4,5 .NET Framework aşağıdaki ağ geliştirmelerini içerir:

- RFC uyumlu URI desteği. Daha fazla bilgi için bkz. <xref:System.Uri> ve ilgili sınıflar.

- Uluslararası etki alanı adı (ıDN) ayrıştırma desteği. Daha fazla bilgi için bkz. <xref:System.Uri> ve ilgili sınıflar.

- E-posta adresi uluslararası duruma getirme (EAı) desteği. Daha fazla bilgi için <xref:System.Net.Mail> ad alanına bakın.

- Geliştirilmiş IPv6 desteği. Daha fazla bilgi için <xref:System.Net.NetworkInformation> ad alanına bakın.

- Çift modlu yuva desteği. Daha fazla bilgi için bkz. <xref:System.Net.Sockets.Socket> ve <xref:System.Net.Sockets.TcpListener> sınıfları.

<a name="client" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

.NET Framework 4,5 ' de, Windows Presentation Foundation (WPF) aşağıdaki alanlarda değişiklikler ve iyileştirmeler içerir:

- Hızlı erişim araç çubuğu, uygulama menüsü ve sekmeler barındıran bir şerit kullanıcı arabirimi uygulamanıza olanak sağlayan yeni <xref:System.Windows.Controls.Ribbon.Ribbon> denetimi.

- Zaman uyumlu ve zaman uyumsuz veri doğrulamayı destekleyen yeni <xref:System.ComponentModel.INotifyDataErrorInfo> arabirimi.

- <xref:System.Windows.Controls.VirtualizingPanel> ve <xref:System.Windows.Threading.Dispatcher> sınıflarına yönelik yeni özellikler.

- Büyük düzeyde gruplandırılmış verilerin görüntülenirken ve Kullanıcı arabirimi olmayan iş parçacıklarında koleksiyonlara erişerek gelişmiş performans.

- Statik özelliklere veri bağlama, <xref:System.Reflection.ICustomTypeProvider> arabirimini uygulayan özel türlere veri bağlama ve veri bağlama bilgilerinin bir bağlama ifadesinden alınması.

- Değerler değiştiğinde verileri yeniden konumlandırma (canlı şekillendirme).

- Bir öğe kapsayıcısının veri bağlamının bağlantısının kesilmesi olup olmadığını denetleme özelliği.

- Özellik değişiklikleri ve veri kaynağı güncelleştirmeleri arasında geçmesi gereken süre miktarını ayarlama yeteneği.

- Zayıf olay desenleri uygulama desteği geliştirildi. Ayrıca, olaylar artık işaretleme uzantılarını kabul edebilir.

<a name="windows_communication_foundation" />

### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

.NET Framework 4,5 ' de, Windows Communication Foundation (WCF) uygulamaları yazmayı ve bakımını daha kolay hale getirmek için aşağıdaki özellikler eklenmiştir:

- Oluşturulan yapılandırma dosyalarının basitleştirmesi.

- Sözleşmenin ilk geliştirmesi için destek.

- ASP.NET uyumluluk modunu daha kolay bir şekilde yapılandırma özelliği.

- Varsayılan taşıma özelliği değerlerindeki değişiklikler, bunları ayarlamak için sahip olma olasılığını azaltır.

- XML sözlüğü okuyucuları için kotaları el ile yapılandırmak zorunda olma olasılığını azaltmak için <xref:System.Xml.XmlDictionaryReaderQuotas> sınıfına yönelik güncelleştirmeler.

- Visual Studio tarafından derleme sürecinin bir parçası olarak WCF yapılandırma dosyalarının doğrulanması, böylece uygulamanızı çalıştırmadan önce yapılandırma hatalarını tespit edebilirsiniz.

- Yeni zaman uyumsuz akış desteği.

- Internet Information Services (IIS) ile HTTPS üzerinden bir uç nokta açığa çıkarmak daha kolay hale getirmek için yeni HTTPS protokol eşlemesi.

- Hizmet URL 'sine `?singleWSDL` ekleyerek tek bir WSDL belgesinde meta veri oluşturma yeteneği.

- TCP aktarımına benzer performans özellikleriyle 80 ve 443 bağlantı noktaları üzerinden doğru çift yönlü iletişimi etkinleştirmek için WebSockets desteği.

- Kodda hizmetleri yapılandırmaya yönelik destek.

- XML Düzenleyici araç ipuçları.

- önbelleğe alma desteği <xref:System.ServiceModel.ChannelFactory>.

- İkili kodlayıcı sıkıştırma desteği.

- Geliştiricilerin "yangın ve unut" iletilerini kullanan hizmetler yazmasını sağlayan bir UDP taşıması desteği. İstemci, hizmete bir ileti gönderir ve hizmetten yanıt vermez.

- HTTP taşıma ve aktarım güvenliği kullanılırken, tek bir WCF uç noktasında birden çok kimlik doğrulama modunu destekleme özelliği.

- Uluslararası etki alanı adları (IDNs) kullanan WCF Hizmetleri için destek.

Daha fazla bilgi için bkz. [Windows Communication Foundation](../wcf/whats-new.md)yenilikleri.

<a name="windows_workflow_foundation" />

### <a name="windows-workflow-foundation-wf"></a>{1&gt;Windows Workflow Foundation (WF)&lt;1}

.NET Framework 4,5 ' de aşağıdakiler de dahil olmak üzere Windows Workflow Foundation (WF) birkaç yeni özellik eklenmiştir:

- İlk olarak .NET Framework 4.0.1 ([.NET Framework 4 platformu güncelleştirme 1](https://blogs.msdn.microsoft.com/endpoint/2011/04/18/microsoft-net-framework-4-platform-update-1/)) bir parçası olarak sunulan durum makinesi iş akışları. Bu güncelleştirme, geliştiricilerin durum makinesi iş akışları oluşturmalarına olanak tanıyan birkaç yeni sınıf ve etkinlik içeriyordu. Bu sınıflar ve Etkinlikler 4,5 .NET Framework şunlar için güncelleştirildi:

  - Durumlar üzerinde kesme noktaları ayarlama yeteneği.

  - İş akışı tasarımcısında geçişleri kopyalama ve yapıştırma özelliği.

  - Paylaşılan tetikleyici geçişi oluşturma için tasarımcı desteği.

  - <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>ve <xref:System.Activities.Statements.Transition>dahil olmak üzere durum makine iş akışları oluşturma etkinlikleri.

- Aşağıdakiler gibi gelişmiş İş Akışı Tasarımcısı Özellikler:

  - Visual Studio 'da **hızlı bul** ve **dosyalardaki bul**dahil olmak üzere gelişmiş iş akışı arama özellikleri.

  - Bir kapsayıcı etkinliğine ikinci bir alt etkinlik eklendiğinde ve her iki etkinliği de sıralı etkinliğe dahil etmek için otomatik olarak bir dizi etkinliği oluşturma özelliği.

  - Kaydırma çubukları kullanılmadan bir iş akışının görünür bölümünün değiştirilmesini sağlayan kaydırma desteği.

  - Bir ağaç stili ana hat görünümündeki bir iş akışının bileşenlerini gösteren ve **Belge anahat** görünümünde bir bileşen seçmenize olanak sağlayan yeni bir **Belge anahat** görünümü.

  - Etkinliklere ek açıklamalar ekleme özelliği.

  - İş akışı tasarımcısını kullanarak etkinlik temsilcilerini tanımlama ve kullanma yeteneği.

  - Durum makinesi ve akış çizelgesi iş akışlarında etkinlikler ve geçişler için otomatik bağlan ve otomatik ekle.

- Bir iş akışı için Görünüm durumu bilgilerini XAML dosyasındaki tek bir öğede depolamak için, Görünüm durumu bilgisini kolayca bulup düzenleyebilmenizi sağlayabilirsiniz.

- Alt etkinliklerin kalıcı olmasını önleyen bir NoPersistScope kapsayıcı etkinliği.

- İfadeler için C# destek:

  - Visual Basic kullanan iş akışı projeleri Visual Basic ifadelerini kullanır ve C# iş akışı projeleri ifadeleri kullanır. C#

  - C#Visual Studio 2010 ' de oluşturulan ve Visual Basic ifadelerine sahip iş akışı projeleri, ifadeler kullanan C# C# iş akışı projeleriyle uyumludur.

- Sürüm oluşturma geliştirmeleri:

  - Kalıcı bir iş akışı örneği ve onun iş akışı tanımı arasında eşleme sağlayan yeni <xref:System.Activities.WorkflowIdentity> sınıfı.

  - <xref:System.ServiceModel.Activities.WorkflowServiceHost>dahil olmak üzere aynı ana bilgisayarda birden çok iş akışı sürümünün yan yana yürütülmesi.

  - Dinamik güncelleştirmede, kalıcı bir iş akışı örneğinin tanımını değiştirme özelliği.

- Sözleşme-ilk iş akışı hizmeti geliştirme, mevcut bir hizmet sözleşmesiyle eşleşecek şekilde otomatik olarak etkinlik oluşturma desteği sağlar.

Daha fazla bilgi için bkz. [Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md)yenilikleri.

<a name="tailored" />

### <a name="net-for-windows-8x-store-apps"></a>Windows 8.x Mağazası uygulamaları için .NET

Windows 8. x Mağazası uygulamaları belirli form faktörleri için tasarlanmıştır ve Windows işletim sisteminin gücünden yararlanır. Veya Visual Basic kullanarak C# Windows için Windows 8. x Mağazası uygulamaları oluşturmak üzere 4,5 veya 4.5.1 .NET Framework bir alt kümesi mevcuttur. Bu alt küme, Windows 8. x Mağazası uygulamaları için .NET olarak adlandırılır ve [genel bakışta](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))ele alınmıştır.

### <a name="portable-class-libraries-a-nameportable-"></a>Taşınabilir sınıf kitaplıkları <a name="portable" />

Visual Studio 2012 ' deki (ve sonraki sürümlerde) taşınabilir sınıf kitaplığı projesi, birden çok .NET Framework platformda çalışan yönetilen derlemeler yazmanızı ve oluşturmanızı sağlar. Taşınabilir bir sınıf kitaplığı projesi kullanarak, hedeflenecek platformları (Windows Phone ve Windows 8. x Mağazası uygulamaları için .NET) seçersiniz. Projenizdeki kullanılabilir türler ve Üyeler, bu platformlar genelinde ortak türler ve üyelerle otomatik olarak kısıtlıdır. Daha fazla bilgi için bkz. [taşınabilir sınıf kitaplığı](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework ve Bant Dışı Yayınlar](../get-started/the-net-framework-and-out-of-band-releases.md)
- [.NET Framework erişilebilirlik yenilikleri](whats-new-in-accessibility.md)
- [Visual Studio 2017'deki yenilikler](/visualstudio/ide/whats-new-visual-studio-2017)
- [Visual Studio 2019 ' deki yenilikler](/visualstudio/ide/whats-new-visual-studio-2019)
- [ASP.NET](/aspnet)
- [Visual Studio C++ 'daki yenilikler](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
