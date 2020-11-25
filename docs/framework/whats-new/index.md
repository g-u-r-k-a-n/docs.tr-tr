---
title: .NET Framework yenilikleri
description: Çeşitli .NET Framework sürümlerindeki yenilikleri görün. Her sürümdeki önemli yeni özellik ve geliştirmelerin özetini okuyun.
ms.date: 10/21/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
ms.openlocfilehash: 3421afee304125413f4fcade6b20df990e922f58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704805"
---
# <a name="whats-new-in-net-framework"></a><span data-ttu-id="66a64-104">.NET Framework yenilikleri</span><span class="sxs-lookup"><span data-stu-id="66a64-104">What's new in .NET Framework</span></span>

[!INCLUDE [net-framework-future](../../../includes/net-framework-future.md)]

<span data-ttu-id="66a64-105">Bu makalede, aşağıdaki .NET Framework sürümlerindeki temel yeni özellikler ve geliştirmeler özetlenmektedir:</span><span class="sxs-lookup"><span data-stu-id="66a64-105">This article summarizes key new features and improvements in the following versions of .NET Framework:</span></span>

- [<span data-ttu-id="66a64-106"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="66a64-106">.NET Framework 4.8</span></span>](#v48)
- [<span data-ttu-id="66a64-107">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="66a64-107">.NET Framework 4.7.2</span></span>](#v472)
- [<span data-ttu-id="66a64-108">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="66a64-108">.NET Framework 4.7.1</span></span>](#v471)
- [<span data-ttu-id="66a64-109">.NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="66a64-109">.NET Framework 4.7</span></span>](#v47)
- [<span data-ttu-id="66a64-110">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="66a64-110">.NET Framework 4.6.2</span></span>](#v462)
- [<span data-ttu-id="66a64-111">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="66a64-111">.NET Framework 4.6.1</span></span>](#v461)
- [<span data-ttu-id="66a64-112">.NET 2015 ve .NET Framework 4,6</span><span class="sxs-lookup"><span data-stu-id="66a64-112">.NET 2015 and .NET Framework 4.6</span></span>](#v46)
- [<span data-ttu-id="66a64-113">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="66a64-113">.NET Framework 4.5.2</span></span>](#v452)
- [<span data-ttu-id="66a64-114">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="66a64-114">.NET Framework 4.5.1</span></span>](#v451)
- [<span data-ttu-id="66a64-115">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="66a64-115">.NET Framework 4.5</span></span>](#v45)

<span data-ttu-id="66a64-116">Bu makale, her yeni özellik hakkında kapsamlı bilgi sağlamaz ve değişikliğe tabidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-116">This article does not provide comprehensive information about each new feature and is subject to change.</span></span> <span data-ttu-id="66a64-117">.NET Framework hakkında genel bilgi için [bkz. Başlarken](../get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-117">For general information about .NET Framework, see [Getting Started](../get-started/index.md).</span></span> <span data-ttu-id="66a64-118">Desteklenen platformlar için bkz. [sistem gereksinimleri](../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-118">For supported platforms, see [System Requirements](../get-started/system-requirements.md).</span></span> <span data-ttu-id="66a64-119">İndirme bağlantıları ve yükleme yönergeleri için bkz. [Yükleme Kılavuzu](../install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-119">For download links and installation instructions, see [Installation Guide](../install/guide-for-developers.md).</span></span>

> [!NOTE]
> <span data-ttu-id="66a64-120">.NET Framework ekibi, platform desteğini genişletmek ve sabit koleksiyonlar ve SıMD özellikli vektör türleri gibi yeni işlevsellik tanıtmak için NuGet kullanarak bant dışı özellikleri de serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="66a64-120">The .NET Framework team also releases features out of band, using NuGet, to expand platform support and introduce new functionality, such as immutable collections and SIMD-enabled vector types.</span></span> <span data-ttu-id="66a64-121">Daha fazla bilgi için bkz. [Ek sınıf kitaplıkları ve API 'ler](../additional-apis/index.md) ve [.NET Framework ve bant dışı yayınlar](../get-started/the-net-framework-and-out-of-band-releases.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-121">For more information, see [Additional Class Libraries and APIs](../additional-apis/index.md) and [.NET Framework and Out-of-Band Releases](../get-started/the-net-framework-and-out-of-band-releases.md).</span></span>
> <span data-ttu-id="66a64-122">.NET Framework için [NuGet paketlerinin tüm listesini](https://www.nuget.org/profiles/dotnetframework) görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="66a64-122">See a [complete list of NuGet packages](https://www.nuget.org/profiles/dotnetframework) for .NET Framework.</span></span>

<a name="v48"></a>

## <a name="introducing-net-framework-48"></a><span data-ttu-id="66a64-123">.NET Framework 4,8 tanıtımı</span><span class="sxs-lookup"><span data-stu-id="66a64-123">Introducing .NET Framework 4.8</span></span>

<span data-ttu-id="66a64-124">.NET Framework 4,8, çok kararlı bir ürün kaldığında birçok yeni düzeltme ve birkaç yeni özellik ekleyerek .NET Framework 4. x ' in önceki sürümlerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="66a64-124">.NET Framework 4.8 builds on previous versions of .NET Framework 4.x by adding many new fixes and several new features while remaining a very stable product.</span></span>

### <a name="download-and-install-net-framework-48"></a><span data-ttu-id="66a64-125">.NET Framework 4,8 indirin ve yükleyin</span><span class="sxs-lookup"><span data-stu-id="66a64-125">Download and install .NET Framework 4.8</span></span>

<span data-ttu-id="66a64-126">.NET Framework 4,8 ' i şu konumlardan indirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66a64-126">You can download .NET Framework 4.8 from the following locations:</span></span>

- [<span data-ttu-id="66a64-127">.NET Framework 4,8 Web Yükleyicisi</span><span class="sxs-lookup"><span data-stu-id="66a64-127">.NET Framework 4.8 Web Installer</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

- [<span data-ttu-id="66a64-128">NET Framework 4,8 çevrimdışı yükleyicisi</span><span class="sxs-lookup"><span data-stu-id="66a64-128">NET Framework 4.8 Offline Installer</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

<span data-ttu-id="66a64-129">.NET Framework 4,8, Windows 10, Windows 8.1, Windows 7 SP1 ve Windows Server 2008 R2 SP1 ile başlayan karşılık gelen sunucu platformları üzerine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-129">.NET Framework 4.8 can be installed on Windows 10, Windows 8.1, Windows 7 SP1, and the corresponding server platforms starting with Windows Server 2008 R2 SP1.</span></span> <span data-ttu-id="66a64-130">Web yükleyicisini veya çevrimdışı yükleyiciyi kullanarak .NET Framework 4,8 ' ü yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-130">You can install .NET Framework 4.8 by using either the web installer or the offline installer.</span></span> <span data-ttu-id="66a64-131">Çoğu kullanıcı için önerilen yöntem web yükleyicisini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="66a64-131">The recommended way for most users is to use the web installer.</span></span>

<span data-ttu-id="66a64-132">[.NET Framework 4,8 Geliştirici paketini](https://go.microsoft.com/fwlink/?LinkId=2085167)yükleyerek Visual Studio 2012 veya sonraki sürümlerde .NET Framework 4,8 ' i hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-132">You can target .NET Framework 4.8 in Visual Studio 2012 or later by installing the [.NET Framework 4.8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).</span></span>

### <a name="whats-new-in-net-framework-48"></a><span data-ttu-id="66a64-133">.NET Framework 4,8 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="66a64-133">What's new in .NET Framework 4.8</span></span>

<span data-ttu-id="66a64-134">.NET Framework 4,8 aşağıdaki alanlarda yeni özellikler sunar:</span><span class="sxs-lookup"><span data-stu-id="66a64-134">.NET Framework 4.8 introduces new features in the following areas:</span></span>

- [<span data-ttu-id="66a64-135">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="66a64-135">Base classes</span></span>](#core48)
- [<span data-ttu-id="66a64-136">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="66a64-136">Windows Communication Foundation (WCF)</span></span>](#wcf48)
- [<span data-ttu-id="66a64-137">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="66a64-137">Windows Presentation Foundation (WPF)</span></span>](#wpf48)
- [<span data-ttu-id="66a64-138">Ortak dil çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="66a64-138">Common language runtime</span></span>](#clr48)

<span data-ttu-id="66a64-139">Bir uygulamanın yardımcı teknoloji kullanıcıları için uygun bir deneyim sağlamasına izin veren iyileştirilmiş erişilebilirlik, .NET Framework 4,8 ' nin önemli bir odağında devam etmektedir.</span><span class="sxs-lookup"><span data-stu-id="66a64-139">Improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology, continues to be a major focus of .NET Framework 4.8.</span></span> <span data-ttu-id="66a64-140">.NET Framework 4,8 ' deki erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için, bkz. [.NET Framework erişilebilirlik 'Teki yenilikler](whats-new-in-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-140">For information on accessibility improvements in .NET Framework 4.8, see [What's new in accessibility in .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core48"></a>

#### <a name="base-classes"></a><span data-ttu-id="66a64-141">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="66a64-141">Base classes</span></span>

<span data-ttu-id="66a64-142">**Şifrelemeye göre daha az FIPS etkisi**.</span><span class="sxs-lookup"><span data-stu-id="66a64-142">**Reduced FIPS impact on Cryptography**.</span></span> <span data-ttu-id="66a64-143">.NET Framework önceki sürümlerinde, <xref:System.Security.Cryptography.SHA256Managed> <xref:System.Security.Cryptography.CryptographicException> Sistem şifreleme KITAPLıKLARı "FIPS modunda" yapılandırıldığında bir oluşturma gibi yönetilen şifreleme sağlayıcısı sınıfları.</span><span class="sxs-lookup"><span data-stu-id="66a64-143">In previous versions of .NET Framework, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in "FIPS mode".</span></span> <span data-ttu-id="66a64-144">Bu özel durumlar, Sistem şifreleme kitaplıklarının aksine, şifreleme sağlayıcısı sınıflarının yönetilen sürümlerinin FIPS (Federal bilgi Işleme standartları) 140-2 sertifikası olmadığı için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="66a64-144">These exceptions are thrown because the managed versions of the cryptographic provider classes, unlike the system cryptographic libraries, have not undergone FIPS (Federal Information Processing Standards) 140-2 certification.</span></span> <span data-ttu-id="66a64-145">Bazı geliştiricilerin geliştirme makineleri FIPS modunda olduğundan, özel durumlar genellikle üretim sistemlerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="66a64-145">Because few developers have their development machines in FIPS mode, the exceptions are commonly thrown in production systems.</span></span>

<span data-ttu-id="66a64-146">Varsayılan olarak, .NET Framework 4,8 ' i hedefleyen uygulamalarda aşağıdaki yönetilen şifreleme sınıfları artık bu durumda bir oluşturmaz <xref:System.Security.Cryptography.CryptographicException> :</span><span class="sxs-lookup"><span data-stu-id="66a64-146">By default in applications that target .NET Framework 4.8, the following managed cryptography classes no longer throw a <xref:System.Security.Cryptography.CryptographicException> in this case:</span></span>

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

<span data-ttu-id="66a64-147">Bunun yerine, bu sınıflar şifreleme işlemlerini bir sistem şifreleme kitaplığına yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-147">Instead, these classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="66a64-148">Bu değişiklik, geliştirici ortamları ve üretim ortamları arasındaki kafa karıştırıcı bir farkı etkili bir şekilde kaldırır ve yerel bileşenlerin ve yönetilen bileşenlerin aynı şifreleme ilkesi altında çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-148">This change effectively removes a potentially confusing difference between developer environments and production environments and makes native components and managed components operate under the same cryptographic policy.</span></span> <span data-ttu-id="66a64-149">Bu özel durumlara bağımlı uygulamalar, AppContext anahtarını olarak ayarlayarak önceki davranışı geri yükleyebilir `Switch.System.Security.Cryptography.UseLegacyFipsThrow` `true` .</span><span class="sxs-lookup"><span data-stu-id="66a64-149">Applications that depend on these exceptions can restore the previous behavior by setting the AppContext switch `Switch.System.Security.Cryptography.UseLegacyFipsThrow` to `true`.</span></span> <span data-ttu-id="66a64-150">Daha fazla bilgi için bkz. [yönetilen şifreleme SıNıFLARı FIPS modunda Cryptographyıexception](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode)oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="66a64-150">For more information, see [Managed cryptography classes do not throw a CryptographyException in FIPS mode](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).</span></span>

<span data-ttu-id="66a64-151">**ZLib 'in güncelleştirilmiş sürümünün kullanımı**</span><span class="sxs-lookup"><span data-stu-id="66a64-151">**Use of updated version of ZLib**</span></span>

<span data-ttu-id="66a64-152">.NET Framework 4,5 ' den başlayarak, clrcompression.dll derlemesi, söndür algoritma için bir uygulama sağlamak üzere veri sıkıştırma için yerel bir dış kitaplık olan [zlib](https://www.zlib.net)'i kullanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-152">Starting with .NET Framework 4.5, the clrcompression.dll assembly uses [ZLib](https://www.zlib.net), a native external library for data compression, in order to provide an implementation for the deflate algorithm.</span></span> <span data-ttu-id="66a64-153">clrcompression.dll .NET Framework 4,8 sürümü, çeşitli temel geliştirmeler ve düzeltmeler içeren ZLib sürüm 1.2.11 kullanacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-153">The .NET Framework 4.8 version of clrcompression.dll is updated to use ZLib Version 1.2.11, which includes several key improvements and fixes.</span></span>

<a name="wcf48"></a>

#### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="66a64-154">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="66a64-154">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="66a64-155">**ServiceHealthBehavior 'a giriş**</span><span class="sxs-lookup"><span data-stu-id="66a64-155">**Introduction of ServiceHealthBehavior**</span></span>

<span data-ttu-id="66a64-156">Sistem durumu uç noktaları, Hizmetleri sistem durumlarına göre yönetmek için Orchestration araçları tarafından yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66a64-156">Health endpoints are widely used by orchestration tools to manage services based on their health status.</span></span> <span data-ttu-id="66a64-157">Sistem durumu denetimleri, bir hizmetin kullanılabilirliği ve performansı hakkında bildirimler izlemek ve bu bildirimleri sağlamak için izleme araçları tarafından da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-157">Health checks can also be used by monitoring tools to track and provide notifications about the availability and performance of a service.</span></span>

<span data-ttu-id="66a64-158">**Servicehealthbehavior** , GENIŞLETEN bir WCF hizmeti davranışıdır <xref:System.ServiceModel.Description.IServiceBehavior> .</span><span class="sxs-lookup"><span data-stu-id="66a64-158">**ServiceHealthBehavior** is a WCF service behavior that extends <xref:System.ServiceModel.Description.IServiceBehavior>.</span></span>  <span data-ttu-id="66a64-159"><xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType>Koleksiyona eklendiğinde, bir hizmet davranışı şunları yapar:</span><span class="sxs-lookup"><span data-stu-id="66a64-159">When added to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> collection, a service behavior does the following:</span></span>

- <span data-ttu-id="66a64-160">HTTP yanıt kodlarıyla hizmet sistem durumu döndürür.</span><span class="sxs-lookup"><span data-stu-id="66a64-160">Returns service health status with HTTP response codes.</span></span> <span data-ttu-id="66a64-161">Bir HTTP/GET Health araştırma isteği için HTTP durum kodunu bir sorgu dizesinde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-161">You can specify in a query string the HTTP status code for a HTTP/GET health probe request.</span></span>

- <span data-ttu-id="66a64-162">Hizmet durumu hakkında bilgi yayımlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-162">Publishes information about service health.</span></span> <span data-ttu-id="66a64-163">Hizmet durumu, kısıtlama sayısı ve kapasite dahil olmak üzere hizmete özgü ayrıntılar, sorgu dizesiyle bir HTTP/GET isteği kullanılarak görüntülenebilir `?health` .</span><span class="sxs-lookup"><span data-stu-id="66a64-163">Service-specific details, including service state, throttle counts, and capacity can be displayed by using an HTTP/GET request with the `?health` query string.</span></span> <span data-ttu-id="66a64-164">Bu tür bilgilere erişim kolaylığı, hatalı bir WCF hizmeti sorunlarını giderirken önemlidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-164">Ease of access to such information is important when troubleshooting a misbehaving WCF service.</span></span>

<span data-ttu-id="66a64-165">Sistem durumu uç noktasını açığa çıkarmak ve WCF hizmeti durum bilgilerini yayımlamak için iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="66a64-165">There are two ways to expose the health endpoint and publish WCF service health information:</span></span>

- <span data-ttu-id="66a64-166">Kod üzerinden.</span><span class="sxs-lookup"><span data-stu-id="66a64-166">Through code.</span></span> <span data-ttu-id="66a64-167">Örnek:</span><span class="sxs-lookup"><span data-stu-id="66a64-167">For example:</span></span>

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

- <span data-ttu-id="66a64-168">Bir yapılandırma dosyası kullanarak.</span><span class="sxs-lookup"><span data-stu-id="66a64-168">By using a configuration file.</span></span> <span data-ttu-id="66a64-169">Örnek:</span><span class="sxs-lookup"><span data-stu-id="66a64-169">For example:</span></span>

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

<span data-ttu-id="66a64-170">Hizmetin sistem durumu,,,, gibi sorgu parametreleri kullanılarak sorgulanabilir `OnServiceFailure` `OnDispatcherFailure` `OnListenerFailure` `OnThrottlePercentExceeded` ve her sorgu parametresi için bir http yanıt kodu belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-170">A service's health status can be queried by using query parameters such as `OnServiceFailure`, `OnDispatcherFailure`, `OnListenerFailure`, `OnThrottlePercentExceeded`), and an HTTP response code can be specified for each query parameter.</span></span> <span data-ttu-id="66a64-171">Bir sorgu parametresi için HTTP yanıt kodu atlanırsa, varsayılan olarak bir 503 HTTP yanıt kodu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66a64-171">If the HTTP response code is omitted for a query parameter, a 503 HTTP response code is used by default.</span></span> <span data-ttu-id="66a64-172">Örnek:</span><span class="sxs-lookup"><span data-stu-id="66a64-172">For example:</span></span>

- <span data-ttu-id="66a64-173">OnServiceFailure: `https://contoso:81/Service1?health&OnServiceFailure=450`</span><span class="sxs-lookup"><span data-stu-id="66a64-173">OnServiceFailure: `https://contoso:81/Service1?health&OnServiceFailure=450`</span></span>

  <span data-ttu-id="66a64-174">[ServiceHost. State](xref:System.ServiceModel.Channels.CommunicationObject.State) değerinden büyük olduğunda BIR 450 http yanıt durum kodu döndürülür <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-174">A 450 HTTP response status code is returned when [ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="66a64-175">Sorgu parametreleri ve örnekleri:</span><span class="sxs-lookup"><span data-stu-id="66a64-175">Query parameters and examples:</span></span>

- <span data-ttu-id="66a64-176">OnDispatcherFailure: `https://contoso:81/Service1?health&OnDispatcherFailure=455`</span><span class="sxs-lookup"><span data-stu-id="66a64-176">OnDispatcherFailure: `https://contoso:81/Service1?health&OnDispatcherFailure=455`</span></span>

  <span data-ttu-id="66a64-177">Bir 455 HTTP yanıt durum kodu, kanal sevkiyatlarından birinin durumu değerinden büyükse döndürülür <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-177">A 455 HTTP response status code is returned when the state of any of the channel dispatchers is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="66a64-178">OnListenerFailure: `https://contoso:81/Service1?health&OnListenerFailure=465`</span><span class="sxs-lookup"><span data-stu-id="66a64-178">OnListenerFailure: `https://contoso:81/Service1?health&OnListenerFailure=465`</span></span>

  <span data-ttu-id="66a64-179">Kanal dinleyicilerinin herhangi birinin durumu şundan büyükse, 465 HTTP yanıt durum kodu döndürülür <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-179">A 465 HTTP response status code is returned when the state of any of the channel listeners is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="66a64-180">Onthrottleyüztexcebaşında: `https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`</span><span class="sxs-lookup"><span data-stu-id="66a64-180">OnThrottlePercentExceeded: `https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`</span></span>

  <span data-ttu-id="66a64-181">Yanıtı tetikleyen {1 – 100} yüzdesini ve {200 – 599} HTTP yanıt kodunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="66a64-181">Specifies the percentage {1 – 100} that triggers the response and its HTTP response code {200 – 599}.</span></span> <span data-ttu-id="66a64-182">Bu örnekte:</span><span class="sxs-lookup"><span data-stu-id="66a64-182">In this example:</span></span>

  - <span data-ttu-id="66a64-183">Yüzde 95 ' den büyükse, bir 500 HTTP yanıt kodu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="66a64-183">If the percentage is greater than 95, a 500 HTTP response code is returned.</span></span>

  - <span data-ttu-id="66a64-184">Yüzde veya 70 ile 95 arasında bir değer döndürülürse, 350 döndürülür.</span><span class="sxs-lookup"><span data-stu-id="66a64-184">If the percentage or between 70 and 95, 350 is returned.</span></span>

  - <span data-ttu-id="66a64-185">Aksi takdirde, 200 döndürülür.</span><span class="sxs-lookup"><span data-stu-id="66a64-185">Otherwise, 200 is returned.</span></span>

<span data-ttu-id="66a64-186">Hizmet sistem durumu, `https://contoso:81/Service1?health` gibi bir sorgu dizesi belirterek, XML içinde veya gibi bir sorgu dizesi BELIRTEREK HTML içinde görüntülenebilir `https://contoso:81/Service1?health&Xml` .</span><span class="sxs-lookup"><span data-stu-id="66a64-186">The service health status can be displayed either in HTML by specifying a query string like `https://contoso:81/Service1?health` or in XML by specifying a query string like `https://contoso:81/Service1?health&Xml`.</span></span> <span data-ttu-id="66a64-187">Gibi bir sorgu dizesi `https://contoso:81/Service1?health&NoContent` boş BIR HTML sayfası döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="66a64-187">A query string like `https://contoso:81/Service1?health&NoContent` returns an empty HTML page.</span></span>

<a name="wpf48"></a>

#### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="66a64-188">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="66a64-188">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="66a64-189">**Yüksek DPı geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="66a64-189">**High DPI enhancements**</span></span>

<span data-ttu-id="66a64-190">.NET Framework 4,8 ' de WPF, Per-Monitor v2 DPı tanıma ve Mixed-Mode DPı ölçeklendirme desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-190">In .NET Framework 4.8, WPF adds support for Per-Monitor V2 DPI Awareness and Mixed-Mode DPI scaling.</span></span> <span data-ttu-id="66a64-191">Yüksek DPı geliştirmesi hakkında daha fazla bilgi için bkz. [Windows üzerinde yüksek DPI masaüstü uygulaması geliştirme](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) .</span><span class="sxs-lookup"><span data-stu-id="66a64-191">See [High DPI Desktop Application Development on Windows](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) for additional information about high DPI development.</span></span>

<span data-ttu-id="66a64-192">.NET Framework 4,8, Mixed-Mode DPı ölçeklendirmesini destekleyen platformlar üzerinde (Windows 10 Nisan 2018 güncelleştirmesi ile başlayarak) yüksek DPı kullanan WPF uygulamalarında barındırılan HWNDs ve Windows Forms birlikte çalışabilirlik desteğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-192">.NET Framework 4.8 improves support for hosted HWNDs and Windows Forms interoperation in High-DPI WPF applications on platforms that support Mixed-Mode DPI scaling (starting with Windows 10 April 2018 Update).</span></span> <span data-ttu-id="66a64-193">Barındırılan HWNDs veya Windows Forms denetimleri [Setthreaddpihostingbehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) ve [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext)çağırarak DPI ölçekli pencereler Mixed-Mode olarak oluşturulduysa, bir Per-Monitor v2 WPF uygulamasında barındırılabilir ve uygun şekilde boyutlandırılabilir ve ölçeklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="66a64-193">When hosted HWNDs or Windows Forms controls are created as Mixed-Mode DPI-scaled windows by calling [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) and [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), they can be hosted in a Per-Monitor V2 WPF application and are sized and scaled appropriately.</span></span> <span data-ttu-id="66a64-194">Bu tür barındırılan içerikler yerel DPı 'de işlenmez; Bunun yerine, işletim sistemi barındırılan içeriği uygun boyuta ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-194">Such hosted content is not rendered at the native DPI; instead, the operating system scales the hosted content to the appropriate size.</span></span> <span data-ttu-id="66a64-195">Per-Monitor v2 DPı tanıma moduna yönelik destek Ayrıca, WPF denetimlerinin yüksek DPı uygulamasındaki yerel bir pencerede barındırılmasına (yani, üst öğe) olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-195">The support for Per-Monitor v2 DPI awareness mode also allows WPF controls to be hosted (i.e., parented) in a native window in a high-DPI application.</span></span>

<span data-ttu-id="66a64-196">Mixed-Mode yüksek DPı ölçeklendirme desteğini etkinleştirmek için aşağıdaki [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarlarını uygulama yapılandırma dosyasına ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66a64-196">To enable support for Mixed-Mode High DPI scaling, you can set the following [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches the application configuration file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48"></a>

#### <a name="common-language-runtime"></a><span data-ttu-id="66a64-197">Ortak dil çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="66a64-197">Common language runtime</span></span>

<span data-ttu-id="66a64-198">.NET Framework 4,8 ' deki çalışma zamanı aşağıdaki değişiklikleri ve geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-198">The runtime in .NET Framework 4.8 includes the following changes and improvements:</span></span>

<span data-ttu-id="66a64-199">**JIT derleyicisi geliştirmeleri**.</span><span class="sxs-lookup"><span data-stu-id="66a64-199">**Improvements to the JIT compiler**.</span></span> <span data-ttu-id="66a64-200">.NET Framework 4,8 ' deki tam zamanında (JıT) derleyici .NET Core 2,1 ' de JıT derleyicisine dayanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-200">The Just-in-time (JIT) compiler in .NET Framework 4.8 is based on the JIT compiler in .NET Core 2.1.</span></span> <span data-ttu-id="66a64-201">.NET Core 2,1 JıT derleyicisi üzerinde yapılan en iyileştirmelerin ve tüm hata düzeltmelerinin çoğu, .NET Framework 4,8 JıT derleyicisine dahildir.</span><span class="sxs-lookup"><span data-stu-id="66a64-201">Many of the optimizations and all of the bug fixes made to the .NET Core 2.1 JIT compiler are included in the .NET Framework 4.8 JIT compiler.</span></span>

<span data-ttu-id="66a64-202">**Ngen geliştirmeleri**.</span><span class="sxs-lookup"><span data-stu-id="66a64-202">**NGEN improvements**.</span></span> <span data-ttu-id="66a64-203">Çalışma zamanı, [Yerel Görüntü Oluşturucu](../tools/ngen-exe-native-image-generator.md) (NGen) görüntüleri için bellek yönetimini iyileştirmiştir, bu sayede Ngen görüntülerinden eşlenen verilerin bellekte yerleşik olmaması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-203">The runtime has improved its memory management for [Native Image Generator](../tools/ngen-exe-native-image-generator.md) (NGEN) images so that data mapped from NGEN images are not memory-resident.</span></span> <span data-ttu-id="66a64-204">Bu, yürütülecek belleği değiştirerek bu yüzey alanını rastgele kodu yürütmeye çalışacak saldırılara karşı azaltır.</span><span class="sxs-lookup"><span data-stu-id="66a64-204">This reduces the surface area available to attacks that attempt to execute arbitrary code by modifying memory that will be executed.</span></span>

<span data-ttu-id="66a64-205">**Tüm derlemeler Için kötü amaçlı yazılımdan koruma taraması**.</span><span class="sxs-lookup"><span data-stu-id="66a64-205">**Antimalware scanning for all assemblies**.</span></span> <span data-ttu-id="66a64-206">Önceki .NET Framework sürümlerinde, çalışma zamanı Windows Defender ya da üçüncü taraf kötü amaçlı yazılımdan koruma yazılımı kullanarak diskten yüklenen tüm derlemeleri tarar.</span><span class="sxs-lookup"><span data-stu-id="66a64-206">In previous versions of .NET Framework, the runtime scans all assemblies loaded from disk using either Windows Defender or third-party antimalware software.</span></span> <span data-ttu-id="66a64-207">Ancak, yöntemi gibi diğer kaynaklardan yüklenen derlemeler <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> taranmaz ve olası algılanabilecek kötü amaçlı yazılımları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-207">However, assemblies loaded from other sources, such as by the <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> method, are not scanned and can potentially contain undetected malware.</span></span> <span data-ttu-id="66a64-208">Windows 10 ' da çalışan .NET Framework 4,8 ' den itibaren, çalışma zamanı [kötü amaçlı yazılımdan koruma taraması arabirimini (AMSı)](/windows/desktop/AMSI/antimalware-scan-interface-portal)uygulayan kötü amaçlı yazılımdan koruma çözümleri tarafından bir taramayı tetikler</span><span class="sxs-lookup"><span data-stu-id="66a64-208">Starting with .NET Framework 4.8 running on Windows 10, the runtime triggers a scan by antimalware solutions that implement the [Antimalware Scan Interface (AMSI)](/windows/desktop/AMSI/antimalware-scan-interface-portal).</span></span>

<a name="v472"></a>

## <a name="whats-new-in-net-framework-472"></a><span data-ttu-id="66a64-209">.NET Framework 4.7.2 yenilikleri</span><span class="sxs-lookup"><span data-stu-id="66a64-209">What's new in .NET Framework 4.7.2</span></span>

<span data-ttu-id="66a64-210">.NET Framework 4.7.2, aşağıdaki alanlardaki yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-210">.NET Framework 4.7.2 includes new features in the following areas:</span></span>

- [<span data-ttu-id="66a64-211">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="66a64-211">Base classes</span></span>](#core-472)
- [<span data-ttu-id="66a64-212">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66a64-212">ASP.NET</span></span>](#asp-net472)
- [<span data-ttu-id="66a64-213">Ağ</span><span class="sxs-lookup"><span data-stu-id="66a64-213">Networking</span></span>](#net472)
- [<span data-ttu-id="66a64-214">SQL</span><span class="sxs-lookup"><span data-stu-id="66a64-214">SQL</span></span>](#sql472)
- [<span data-ttu-id="66a64-215">WPF</span><span class="sxs-lookup"><span data-stu-id="66a64-215">WPF</span></span>](#wpf472)
- [<span data-ttu-id="66a64-216">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="66a64-216">ClickOnce</span></span>](#clickonce)

<span data-ttu-id="66a64-217">.NET Framework 4.7.2 ' ye odaklanmaya devam etmek, bir uygulamanın yardımcı teknoloji kullanıcıları için uygun bir deneyim sağlamasına olanak tanıyan bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="66a64-217">A continuing focus in .NET Framework 4.7.2 is improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="66a64-218">.NET Framework 4.7.2 ' deki erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için, bkz. [Erişilebilirlik 'deki yenilikler .NET Framework](whats-new-in-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-218">For information on accessibility improvements in .NET Framework 4.7.2, see [What's new in accessibility in .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core-472"></a>

#### <a name="base-classes"></a><span data-ttu-id="66a64-219">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="66a64-219">Base classes</span></span>

<span data-ttu-id="66a64-220">.NET Framework 4.7.2, çok sayıda şifreleme geliştirmesi, ZIP arşivleri için daha iyi açma desteği ve ek koleksiyon API 'Leri sunar.</span><span class="sxs-lookup"><span data-stu-id="66a64-220">.NET Framework 4.7.2 features a large number of cryptographic enhancements, better decompression support for ZIP archives, and additional collection APIs.</span></span>

<span data-ttu-id="66a64-221">**Yeni RSA aşırı yüklemeleri. Ve DSA oluştur. Oluşturma**</span><span class="sxs-lookup"><span data-stu-id="66a64-221">**New overloads of RSA.Create and DSA.Create**</span></span>

<span data-ttu-id="66a64-222"><xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType>Ve <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> yöntemleri, yeni veya anahtar örneği oluşturulurken anahtar parametreleri vermenizi sağlar <xref:System.Security.Cryptography.DSA> <xref:System.Security.Cryptography.RSA> .</span><span class="sxs-lookup"><span data-stu-id="66a64-222">The <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> and <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> methods let you supply key parameters when instantiating a new <xref:System.Security.Cryptography.DSA> or <xref:System.Security.Cryptography.RSA> key.</span></span> <span data-ttu-id="66a64-223">Bunlar, aşağıdaki gibi bir kod değiştirmenizi sağlar:</span><span class="sxs-lookup"><span data-stu-id="66a64-223">They allow you to replace code like the following:</span></span>

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

<span data-ttu-id="66a64-224">Şu şekilde kodla:</span><span class="sxs-lookup"><span data-stu-id="66a64-224">with code like this:</span></span>

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

<span data-ttu-id="66a64-225"><xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType>Ve <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> yöntemleri, <xref:System.Security.Cryptography.DSA> <xref:System.Security.Cryptography.RSA> belirli bir anahtar boyutuyla yeni veya anahtarlar oluşturmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-225">The <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> and <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> methods let you generate new <xref:System.Security.Cryptography.DSA> or <xref:System.Security.Cryptography.RSA> keys with a specific key size.</span></span> <span data-ttu-id="66a64-226">Örnek:</span><span class="sxs-lookup"><span data-stu-id="66a64-226">For example:</span></span>

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

<span data-ttu-id="66a64-227">**Rfc2898DeriveBytes oluşturucular bir karma algoritma adı kabul eder**</span><span class="sxs-lookup"><span data-stu-id="66a64-227">**Rfc2898DeriveBytes constructors accept a hash algorithm name**</span></span>

<span data-ttu-id="66a64-228"><xref:System.Security.Cryptography.Rfc2898DeriveBytes>Sınıfında, <xref:System.Security.Cryptography.HashAlgorithmName> anahtarları TÜRETMEDE kullanılacak HMAC algoritmasını tanımlayan bir parametreye sahip üç yeni Oluşturucu vardır.</span><span class="sxs-lookup"><span data-stu-id="66a64-228">The <xref:System.Security.Cryptography.Rfc2898DeriveBytes> class has three new constructors with a <xref:System.Security.Cryptography.HashAlgorithmName> parameter that identifies the HMAC algorithm to use when deriving keys.</span></span> <span data-ttu-id="66a64-229">Geliştiriciler, SHA-1 kullanmak yerine, aşağıdaki örnekte gösterildiği gibi SHA-256 gibi bir SHA-2 tabanlı HMAC kullanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="66a64-229">Instead of using SHA-1, developers should use a SHA-2-based HMAC like SHA-256, as shown in the following example:</span></span>

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

<span data-ttu-id="66a64-230">**Kısa ömürlü anahtarlar için destek**</span><span class="sxs-lookup"><span data-stu-id="66a64-230">**Support for ephemeral keys**</span></span>

<span data-ttu-id="66a64-231">PFX içeri aktarma isteğe bağlı olarak, sabit sürücüyü atlayarak özel anahtarları doğrudan bellekten yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-231">PFX import can optionally load private keys directly from memory, bypassing the hard drive.</span></span> <span data-ttu-id="66a64-232">Yeni <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> bayrak bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> oluşturucuda veya metodun aşırı yüklerinden birinde belirtildiğinde <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> , özel anahtarlar kısa ömürlü anahtarlar olarak yüklenecektir.</span><span class="sxs-lookup"><span data-stu-id="66a64-232">When the new <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> flag is specified in an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> constructor or one of the overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> method, the private keys will be loaded as ephemeral keys.</span></span> <span data-ttu-id="66a64-233">Bu, anahtarların diskte görünmesini önler.</span><span class="sxs-lookup"><span data-stu-id="66a64-233">This prevents the keys from being visible on the disk.</span></span> <span data-ttu-id="66a64-234">Ancak</span><span class="sxs-lookup"><span data-stu-id="66a64-234">However:</span></span>

- <span data-ttu-id="66a64-235">Anahtarlar diske kalıcı olmadığından, bu bayrağıyla yüklenen sertifikalar bir X509Store eklemek için iyi aday değildir.</span><span class="sxs-lookup"><span data-stu-id="66a64-235">Since the keys are not persisted to disk, certificates loaded with this flag are not good candidates to add to an X509Store.</span></span>

- <span data-ttu-id="66a64-236">Bu şekilde yüklenen anahtarlar neredeyse her zaman Windows CNG aracılığıyla yüklenir.</span><span class="sxs-lookup"><span data-stu-id="66a64-236">Keys loaded in this manner are almost always loaded via Windows CNG.</span></span> <span data-ttu-id="66a64-237">Bu nedenle, çağıranlar, CERT gibi uzantı yöntemlerini çağırarak özel anahtara erişmelidir [. GetRSAPrivateKey ()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A).</span><span class="sxs-lookup"><span data-stu-id="66a64-237">Therefore, callers must access the private key by calling extension methods, such as [cert.GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A).</span></span> <span data-ttu-id="66a64-238"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>Özellik çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="66a64-238">The <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> property does not function.</span></span>

- <span data-ttu-id="66a64-239">Eski <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> özellik sertifikalarla çalışmadıklarından, geliştiricilerin kısa ömürlü anahtarlara geçmeden önce ciddi testler gerçekleştirmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="66a64-239">Since the legacy <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> property does not work with certificates, developers should perform rigorous testing before switching to ephemeral keys.</span></span>

<span data-ttu-id="66a64-240">**PKCS # 10 sertifika imzalama istekleri ve X. 509.440 ortak anahtar sertifikalarının programlı bir şekilde oluşturulması**</span><span class="sxs-lookup"><span data-stu-id="66a64-240">**Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates**</span></span>

<span data-ttu-id="66a64-241">.NET Framework 4.7.2 ' den itibaren, iş yükleri sertifika imzalama istekleri (CSR) oluşturabilir ve bu da sertifika isteği oluşturma 'nın var olan araç halinde hazırlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-241">Starting with .NET Framework 4.7.2, workloads can generate certificate signing requests (CSRs), which allows certificate request generation to be staged into existing tooling.</span></span> <span data-ttu-id="66a64-242">Bu, genellikle test senaryolarında yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="66a64-242">This is frequently useful in test scenarios.</span></span>

<span data-ttu-id="66a64-243">Daha fazla bilgi ve kod örnekleri için [.net blogda](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/)"PKCS # 10 sertifika imzalama Isteklerinin ve X. 509.440 ortak anahtar sertifikalarının programlı oluşturulması" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-243">For more information and code examples, see "Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates" in the [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span></span>

<span data-ttu-id="66a64-244">**Yeni SignerInfo üyeleri**</span><span class="sxs-lookup"><span data-stu-id="66a64-244">**New SignerInfo members**</span></span>

<span data-ttu-id="66a64-245">.NET Framework 4.7.2 ile başlayarak, <xref:System.Security.Cryptography.Pkcs.SignerInfo> sınıfı imza hakkında daha fazla bilgi sunar.</span><span class="sxs-lookup"><span data-stu-id="66a64-245">Starting with .NET Framework 4.7.2, the <xref:System.Security.Cryptography.Pkcs.SignerInfo> class exposes more information about the signature.</span></span> <span data-ttu-id="66a64-246"><xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName>İmzalayan tarafından kullanılan imza algoritmasını belirleyebilmek için özelliğinin değerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-246">You can retrieve the value of the <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> property to determine the signature algorithm used by the signer.</span></span> <span data-ttu-id="66a64-247"><xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> , bu imzalayan için şifreleme imzasının bir kopyasını almak üzere çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-247"><xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> can be called to get a copy of the cryptographic signature for this signer.</span></span>

<span data-ttu-id="66a64-248">**CryptoStream atıldıktan sonra sarmalanmış bir akışın açılmasını bırakma**</span><span class="sxs-lookup"><span data-stu-id="66a64-248">**Leaving a wrapped stream open after CryptoStream is disposed**</span></span>

<span data-ttu-id="66a64-249">.NET Framework 4.7.2 ile başlayarak, <xref:System.Security.Cryptography.CryptoStream> sınıfı <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> sarmalanmış akışı kapatmayan ek bir oluşturucuya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="66a64-249">Starting with .NET Framework 4.7.2, the <xref:System.Security.Cryptography.CryptoStream> class has an additional constructor that allows <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> to not close the wrapped stream.</span></span> <span data-ttu-id="66a64-250">Örnek atıldıktan sonra sarmalanmış akışı açık bırakmak için <xref:System.Security.Cryptography.CryptoStream> Yeni <xref:System.Security.Cryptography.CryptoStream> oluşturucuyu aşağıdaki gibi çağırın:</span><span class="sxs-lookup"><span data-stu-id="66a64-250">To leave the wrapped stream open after the <xref:System.Security.Cryptography.CryptoStream> instance is disposed, call the new <xref:System.Security.Cryptography.CryptoStream> constructor as follows:</span></span>

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

<span data-ttu-id="66a64-251">**DeflateStream 'de değişiklikleri açma**</span><span class="sxs-lookup"><span data-stu-id="66a64-251">**Decompression changes in DeflateStream**</span></span>

<span data-ttu-id="66a64-252">.NET Framework 4.7.2 ile başlayarak, sınıftaki açma işlemlerinin uygulanması, <xref:System.IO.Compression.DeflateStream> Varsayılan olarak yerel Windows API 'lerini kullanacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-252">Starting with .NET Framework 4.7.2, the implementation of decompression operations in the <xref:System.IO.Compression.DeflateStream> class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="66a64-253">Genellikle bu, önemli ölçüde performans geliştirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="66a64-253">Typically, this results in a substantial performance improvement.</span></span>

<span data-ttu-id="66a64-254">Windows API 'Leri kullanarak açma desteği, .NET Framework 4.7.2 ' i hedefleyen uygulamalar için varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-254">Support for decompression by using Windows APIs is enabled by default for applications that target .NET Framework 4.7.2.</span></span> <span data-ttu-id="66a64-255">.NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4.7.2 altında çalışan uygulamalar, uygulama yapılandırma dosyasına aşağıdaki [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ekleyerek bu davranışı kabul edebilir:</span><span class="sxs-lookup"><span data-stu-id="66a64-255">Applications that target earlier versions of .NET Framework but are running under .NET Framework 4.7.2 can opt into this behavior by adding the following [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

<span data-ttu-id="66a64-256">**Ek koleksiyon API 'Leri**</span><span class="sxs-lookup"><span data-stu-id="66a64-256">**Additional collection APIs**</span></span>

<span data-ttu-id="66a64-257">.NET Framework 4.7.2, ve türlerine bir dizi yeni API ekler <xref:System.Collections.Generic.SortedSet%601> <xref:System.Collections.Generic.HashSet%601> .</span><span class="sxs-lookup"><span data-stu-id="66a64-257">.NET Framework 4.7.2 adds a number of new APIs to the <xref:System.Collections.Generic.SortedSet%601> and <xref:System.Collections.Generic.HashSet%601> types.</span></span> <span data-ttu-id="66a64-258">Bunlar:</span><span class="sxs-lookup"><span data-stu-id="66a64-258">These include:</span></span>

- <span data-ttu-id="66a64-259">`TryGetValue` diğer koleksiyon türlerinde kullanılan try modelini bu iki türe genişleten Yöntemler.</span><span class="sxs-lookup"><span data-stu-id="66a64-259">`TryGetValue` methods, which extend the try pattern used in other collection types to these two types.</span></span> <span data-ttu-id="66a64-260">Yöntemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="66a64-260">The methods are:</span></span>

  - [<span data-ttu-id="66a64-261">Genel bool diyez kümesi \<T> . TryGetValue (T equalValue, out gerçek değeri)</span><span class="sxs-lookup"><span data-stu-id="66a64-261">public bool HashSet\<T>.TryGetValue(T equalValue, out T actualValue)</span></span>](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [<span data-ttu-id="66a64-262">Genel bool SortedSet \<T> . TryGetValue (T equalValue, out gerçek değeri)</span><span class="sxs-lookup"><span data-stu-id="66a64-262">public bool SortedSet\<T>.TryGetValue(T equalValue, out T actualValue)</span></span>](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- <span data-ttu-id="66a64-263">`Enumerable.To*` Uzantı yöntemleri, bir koleksiyonu öğesine dönüştürür <xref:System.Collections.Generic.HashSet%601> :</span><span class="sxs-lookup"><span data-stu-id="66a64-263">`Enumerable.To*` extension methods, which convert a collection to a <xref:System.Collections.Generic.HashSet%601>:</span></span>

  - [<span data-ttu-id="66a64-264">ortak static HashSet \<TSource> tohashset \<TSource> (Bu IEnumerable \<TSource> kaynağı)</span><span class="sxs-lookup"><span data-stu-id="66a64-264">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source)</span></span>](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [<span data-ttu-id="66a64-265">ortak statik HashSet \<TSource> tohashset \<TSource> (Bu IEnumerable \<TSource> kaynağı, IEqualityComparer \<TSource> karşılaştırıcısı)</span><span class="sxs-lookup"><span data-stu-id="66a64-265">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source, IEqualityComparer\<TSource> comparer)</span></span>](xref:System.Linq.Enumerable.ToHashSet%2A)

- <span data-ttu-id="66a64-266"><xref:System.Collections.Generic.HashSet%601>Koleksiyonun kapasitesini ayarlamanıza olanak tanıyan yeni oluşturucular, daha önce boyutunu bildiğiniz bir performans avantajı verir <xref:System.Collections.Generic.HashSet%601> :</span><span class="sxs-lookup"><span data-stu-id="66a64-266">New <xref:System.Collections.Generic.HashSet%601> constructors that let you set the collection's capacity, which yields a performance benefit when you know the size of the <xref:System.Collections.Generic.HashSet%601> in advance:</span></span>

  - <span data-ttu-id="66a64-267">[Genel diyez kümesi (int kapasitesi)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="66a64-267">[public HashSet(int capacity)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))</span></span>
  - <span data-ttu-id="66a64-268">[ortak diyez kümesi (int kapasitesi, IEqualityComparer \<T> Comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))</span><span class="sxs-lookup"><span data-stu-id="66a64-268">[public HashSet(int capacity, IEqualityComparer\<T> comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))</span></span>

<span data-ttu-id="66a64-269"><xref:System.Collections.Concurrent.ConcurrentDictionary%602>Sınıfı, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> sözlükten bir değer almak veya bulunamadıysanız eklemek ve sözlüğe bir değer eklemek ya da zaten varsa güncelleştirmek için ve yöntemlerinin yeni aşırı yüklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-269">The <xref:System.Collections.Concurrent.ConcurrentDictionary%602> class includes new overloads of the <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> methods to retrieve a value from the dictionary or to add it if it is not found, and to add a value to the dictionary or to update it if it already exists.</span></span>

```csharp
public TValue AddOrUpdate<TArg>(TKey key, Func<TKey, TArg, TValue> addValueFactory, Func<TKey, TValue, TArg, TValue> updateValueFactory, TArg factoryArgument)

public TValue GetOrAdd<TArg>(TKey key, Func<TKey, TArg, TValue> valueFactory, TArg factoryArgument)
```

```vb
Public AddOrUpdate(Of TArg)(key As TKey, addValueFactory As Func(Of TKey, TArg, TValue), updateValueFactory As Func(Of TKey, TValue, TArg, TValue), factoryArgument As TArg) As TValue

Public GetOrAdd(Of TArg)(key As TKey, valueFactory As Func(Of TKey, TArg, TValue), factoryArgument As TArg) As TValue
```

<a name="asp-net472"></a>

#### <a name="aspnet"></a><span data-ttu-id="66a64-270">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66a64-270">ASP.NET</span></span>

<span data-ttu-id="66a64-271">**Web Forms bağımlılık ekleme desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-271">**Support for dependency injection in Web Forms**</span></span>

<span data-ttu-id="66a64-272">[Bağımlılık ekleme (dı)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) nesneleri ve bağımlılıklarını ayırır, böylece bir bağımlılık değiştiği için nesnenin kodunun artık değişmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="66a64-272">[Dependency injection (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) decouples objects and their dependencies so that an object's code no longer needs to be changed just because a dependency has changed.</span></span> <span data-ttu-id="66a64-273">.NET Framework 4.7.2 hedefleyen ASP.NET uygulamaları geliştirirken şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66a64-273">When developing ASP.NET applications that target .NET Framework 4.7.2, you can:</span></span>

- <span data-ttu-id="66a64-274">[İşleyiciler ve modüller](/previous-versions/aspnet/bb398986(v=vs.100)), [sayfa örnekleri](xref:System.Web.UI.Page)ve ASP.NET Web uygulaması projelerinin [kullanıcı denetimlerinde](/previous-versions/aspnet/y6wb1a0e(v=vs.100)) , ayarlayıcı tabanlı, arabirim tabanlı ve Oluşturucu tabanlı ekleme kullanın.</span><span class="sxs-lookup"><span data-stu-id="66a64-274">Use setter-based, interface-based, and constructor-based injection in [handlers and modules](/previous-versions/aspnet/bb398986(v=vs.100)), [Page instances](xref:System.Web.UI.Page), and [user controls](/previous-versions/aspnet/y6wb1a0e(v=vs.100)) of ASP.NET web application projects.</span></span>

- <span data-ttu-id="66a64-275">[İşleyiciler ve modüller](/previous-versions/aspnet/bb398986(v=vs.100)), [sayfa örnekleri](xref:System.Web.UI.Page)ve ASP.NET Web sitesi projelerinin [kullanıcı denetimlerinde](/previous-versions/aspnet/y6wb1a0e(v=vs.100)) , ayarlayıcı tabanlı ve arabirim tabanlı ekleme kullanın.</span><span class="sxs-lookup"><span data-stu-id="66a64-275">Use setter-based and interface-based injection in [handlers and modules](/previous-versions/aspnet/bb398986(v=vs.100)), [Page instances](xref:System.Web.UI.Page), and [user controls](/previous-versions/aspnet/y6wb1a0e(v=vs.100)) of ASP.NET web site projects.</span></span>

- <span data-ttu-id="66a64-276">Farklı bağımlılık ekleme çerçeveleri takın.</span><span class="sxs-lookup"><span data-stu-id="66a64-276">Plug in different dependency injection frameworks.</span></span>

<span data-ttu-id="66a64-277">**Aynı site tanımlama bilgileri için destek**</span><span class="sxs-lookup"><span data-stu-id="66a64-277">**Support for same-site cookies**</span></span>

<span data-ttu-id="66a64-278">[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) , bir tarayıcının bir siteler arası istekle birlikte tanımlama bilgisi göndermesini engeller.</span><span class="sxs-lookup"><span data-stu-id="66a64-278">[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) prevents a browser from sending a cookie along with a cross-site request.</span></span> <span data-ttu-id="66a64-279">.NET Framework 4.7.2 <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> , değeri bir numaralandırma üyesi olan bir özellik ekler <xref:System.Web.SameSiteMode?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-279">.NET Framework 4.7.2 adds a <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> property whose value is a <xref:System.Web.SameSiteMode?displayProperty=nameWithType> enumeration member.</span></span> <span data-ttu-id="66a64-280">Eğer değeri veya ise <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType> , ASP.net `SameSite` özniteliğini set-Cookie başlığına ekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-280">If its value is <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> or <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET adds the `SameSite` attribute to the set-cookie header.</span></span> <span data-ttu-id="66a64-281">SameSite desteğinin <xref:System.Web.HttpCookie> , <xref:System.Web.Security.FormsAuthentication> ve için ve tanımlama bilgilerinin yanı sıra nesneler için de geçerlidir <xref:System.Web.SessionState> .</span><span class="sxs-lookup"><span data-stu-id="66a64-281">SameSite support applies to <xref:System.Web.HttpCookie> objects, as well as to <xref:System.Web.Security.FormsAuthentication> and <xref:System.Web.SessionState> cookies.</span></span>

<span data-ttu-id="66a64-282">Bir nesne için SameSite öğesini <xref:System.Web.HttpCookie> aşağıdaki gibi ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66a64-282">You can set SameSite for an <xref:System.Web.HttpCookie> object as follows:</span></span>

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

<span data-ttu-id="66a64-283">Ayrıca, web.config dosyasını değiştirerek, uygulama düzeyinde de SameSite tanımlama bilgilerini yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66a64-283">You can also configure SameSite cookies at the application level by modifying the web.config file:</span></span>

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

<span data-ttu-id="66a64-284"><xref:System.Web.Security.FormsAuthentication> <xref:System.Web.SessionState> Web yapılandırma dosyasını değiştirerek, ve tanımlama bilgilerini Için SameSite ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66a64-284">You can add SameSite for <xref:System.Web.Security.FormsAuthentication> and <xref:System.Web.SessionState> cookies by modifying the web config file:</span></span>

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   </authentication>
   <sessionState cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472"></a>

#### <a name="networking"></a><span data-ttu-id="66a64-285">Ağ</span><span class="sxs-lookup"><span data-stu-id="66a64-285">Networking</span></span>

<span data-ttu-id="66a64-286">**HttpClientHandler özelliklerinin uygulanması**</span><span class="sxs-lookup"><span data-stu-id="66a64-286">**Implementation of HttpClientHandler properties**</span></span>

<span data-ttu-id="66a64-287">.NET Framework 4.7.1, sınıfa sekiz özellik ekledi <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-287">.NET Framework 4.7.1 added eight properties to the <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="66a64-288">Ancak, iki olarak bir oluşturdu <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="66a64-288">However, two threw a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="66a64-289">.NET Framework 4.7.2 artık bu özellikler için bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-289">.NET Framework 4.7.2 now provides an implementation for these properties.</span></span> <span data-ttu-id="66a64-290">Özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="66a64-290">The properties are:</span></span>

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472"></a>

#### <a name="sqlclient"></a><span data-ttu-id="66a64-291">SQLClient</span><span class="sxs-lookup"><span data-stu-id="66a64-291">SQLClient</span></span>

<span data-ttu-id="66a64-292">**Azure Active Directory evrensel kimlik doğrulaması ve Multi-Factor Authentication desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-292">**Support for Azure Active Directory Universal Authentication and Multi-Factor authentication**</span></span>

<span data-ttu-id="66a64-293">Büyüyen uyumluluk ve güvenlik talepleri birçok müşterinin Multi-Factor Authentication (MFA) kullanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-293">Growing compliance and security demands require that many customers use multi-factor authentication (MFA).</span></span> <span data-ttu-id="66a64-294">Ayrıca, geçerli en iyi uygulamalar Kullanıcı parolalarını doğrudan bağlantı dizelerine dahil etmekten kaçınarak.</span><span class="sxs-lookup"><span data-stu-id="66a64-294">In addition, current best practices discourage including user passwords directly in connection strings.</span></span> <span data-ttu-id="66a64-295">Bu değişiklikleri desteklemek için, 4.7.2 ve [Azure AD kimlik doğrulamasını](/azure/sql-database/sql-database-aad-authentication-configure)desteklemek üzere mevcut "Authentication" anahtar sözcüğü için yeni bir değer ekleyerek [SQLClient bağlantı dizelerini](xref:System.Data.SqlClient.SqlConnection.ConnectionString) Active Directory ".NET Framework genişletir.</span><span class="sxs-lookup"><span data-stu-id="66a64-295">To support these changes, .NET Framework 4.7.2 extends [SQLClient connection strings](xref:System.Data.SqlClient.SqlConnection.ConnectionString) by adding a new value, "Active Directory Interactive", for the existing "Authentication" keyword to support MFA and [Azure AD Authentication](/azure/sql-database/sql-database-aad-authentication-configure).</span></span> <span data-ttu-id="66a64-296">Yeni etkileşimli Yöntem, yerel ve Federal Azure AD kullanıcılarını ve Azure AD Konuk kullanıcılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-296">The new interactive method supports native and federated Azure AD users as well as Azure AD guest users.</span></span> <span data-ttu-id="66a64-297">Bu yöntem kullanıldığında, Azure AD tarafından uygulanan MFA kimlik doğrulaması SQL veritabanları için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="66a64-297">When this method is used, the MFA authentication imposed by Azure AD is supported for SQL databases.</span></span> <span data-ttu-id="66a64-298">Ayrıca, kimlik doğrulama işlemi, en iyi güvenlik uygulamalarına uyacak şekilde bir Kullanıcı parolası ister.</span><span class="sxs-lookup"><span data-stu-id="66a64-298">In addition, the authentication process requests a user password to adhere to security best practices.</span></span>

<span data-ttu-id="66a64-299">Önceki .NET Framework sürümlerinde SQL bağlantısı yalnızca <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> ve seçeneklerini destekliyordu <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-299">In previous versions of .NET Framework, SQL connectivity supported only the <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> and <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> options.</span></span> <span data-ttu-id="66a64-300">Bunların her ikisi de, MFA 'yı desteklemeyen, etkileşimli olmayan [adal protokolünün](/azure/active-directory/develop/active-directory-authentication-libraries)bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-300">Both of these are part of the non-interactive [ADAL protocol](/azure/active-directory/develop/active-directory-authentication-libraries), which does not support MFA.</span></span> <span data-ttu-id="66a64-301">Yeni <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> seçenekle, SQL BAĞLANTıSı MFA 'yı ve mevcut kimlik doğrulama yöntemlerini (parola ve tümleşik kimlik doğrulaması) destekler, böylece kullanıcılar bağlantı dizesinde kalıcı parolalar olmadan Kullanıcı parolalarını etkileşimli olarak girebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-301">With the new <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> option, SQL connectivity supports MFA as well as existing authentication methods (password and integrated authentication), which allows users to enter user passwords interactively without persisting passwords in the connection string.</span></span>

<span data-ttu-id="66a64-302">Daha fazla bilgi ve örnek için [.net blogdaki](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/)"SQL--Azure AD Universal ve Multi-Factor Authentication support" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-302">For more information and an example, see "SQL -- Azure AD Universal and Multi-factor Authentication Support" in the [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span></span>

<span data-ttu-id="66a64-303">**Always Encrypted sürüm 2 için destek**</span><span class="sxs-lookup"><span data-stu-id="66a64-303">**Support for Always Encrypted version 2**</span></span>

<span data-ttu-id="66a64-304">NET Framework 4.7.2, şifreleme tabanlı Always Encrypted destekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-304">NET Framework 4.7.2 adds supports for enclave-based Always Encrypted.</span></span> <span data-ttu-id="66a64-305">Always Encrypted orijinal sürümü, şifreleme anahtarlarının istemciden hiçbir şekilde ayrılmayacağı istemci tarafı bir şifreleme teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-305">The original version of Always Encrypted is a client-side encryption technology in which encryption keys never leave the client.</span></span> <span data-ttu-id="66a64-306">Encde tabanlı Always Encrypted, istemci isteğe bağlı olarak, SQL Server bir parçası olarak kabul edilebilir ancak SQL Server kodu ile oynanamaz güvenli bir hesaplama varlığı olan güvenli bir kuşya şifreleme anahtarlarını gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-306">In enclave-based Always Encrypted, the client can optionally send the encryption keys to a secure enclave, which is a secure computational entity that can be considered part of SQL Server but that SQL Server code cannot tamper with.</span></span> <span data-ttu-id="66a64-307">.NET Framework 4.7.2, şifreleme tabanlı Always Encrypted desteklemek için aşağıdaki türleri ve üyeleri <xref:System.Data.SqlClient> ad alanına ekler:</span><span class="sxs-lookup"><span data-stu-id="66a64-307">To support enclave-based Always Encrypted, .NET Framework 4.7.2 adds the following types and members to the <xref:System.Data.SqlClient> namespace:</span></span>

- <span data-ttu-id="66a64-308"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, şifreleme tabanlı Always Encrypted URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="66a64-308"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, which specifies the Uri for enclave-based Always Encrypted.</span></span>

- <span data-ttu-id="66a64-309"><xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>Bu, tüm kuşve sağlayıcılarının türetildiği soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="66a64-309"><xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, which is an abstract class from which all enclave providers are derived.</span></span>

- <span data-ttu-id="66a64-310"><xref:System.Data.SqlClient.SqlEnclaveSession>, belirli bir şifreleme oturumunun durumunu kapsülleyen.</span><span class="sxs-lookup"><span data-stu-id="66a64-310"><xref:System.Data.SqlClient.SqlEnclaveSession>, which encapsulates the state for a given enclave session.</span></span>

- <span data-ttu-id="66a64-311"><xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, belirli bir kanıtlama protokolünü yürütmek için gereken bilgileri almak üzere SQL Server tarafından kullanılan kanıtlama parametrelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-311"><xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, which provides the attestation parameters used by SQL Server to get information required to execute a particular Attestation Protocol.</span></span>

<span data-ttu-id="66a64-312">Uygulama yapılandırma dosyası daha sonra, <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> şifreleme sağlayıcısı için işlevselliği sağlayan soyut sınıfın somut bir uygulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="66a64-312">The application configuration file then specifies a concrete implementation of the abstract <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> class that provides the functionality for the enclave provider.</span></span> <span data-ttu-id="66a64-313">Örnek:</span><span class="sxs-lookup"><span data-stu-id="66a64-313">For example:</span></span>

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

<span data-ttu-id="66a64-314">Şifreleme tabanlı Always Encrypted temel akışı:</span><span class="sxs-lookup"><span data-stu-id="66a64-314">The basic flow of enclave-based Always Encrypted is:</span></span>

1. <span data-ttu-id="66a64-315">Kullanıcı, SQL Server şifreli bir bağlantı oluşturur ve bu, şifreleme tabanlı Always Encrypted destekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-315">The user creates an AlwaysEncrypted connection to SQL Server that supported enclave-based Always Encrypted.</span></span> <span data-ttu-id="66a64-316">Sürücü, doğru kuşağa bağlandığından emin olmak için kanıtlama hizmetiyle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="66a64-316">The driver contacts the attestation service to ensure that it is connecting to right enclave.</span></span>

1. <span data-ttu-id="66a64-317">Şifreleme onaylandıktan sonra, sürücü, SQL Server barındırılan güvenli şifreleme ile güvenli bir kanal oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66a64-317">Once the enclave has been attested, the driver establishes a secure channel with the secure enclave hosted on SQL Server.</span></span>

1. <span data-ttu-id="66a64-318">Sürücü, SQL bağlantısı süresi boyunca güvenli şifreleme ile istemci tarafından yetkilendirilmiş şifreleme anahtarlarını paylaşır.</span><span class="sxs-lookup"><span data-stu-id="66a64-318">The driver shares encryption keys authorized by the client with the secure enclave for the duration of the SQL connection.</span></span>

<a name="wpf472"></a>

#### <a name="windows-presentation-foundation"></a><span data-ttu-id="66a64-319">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="66a64-319">Windows Presentation Foundation</span></span>

<span data-ttu-id="66a64-320">**Kaynağa göre Resourcesözlükler bulma**</span><span class="sxs-lookup"><span data-stu-id="66a64-320">**Finding ResourceDictionaries by Source**</span></span>

<span data-ttu-id="66a64-321">.NET Framework 4.7.2 ile başlayarak bir tanılama Yardımcısı, <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> belirli bir kaynak URI 'sinden oluşturulmuş olan öğesini bulabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-321">Starting with .NET Framework 4.7.2, a diagnostic assistant can locate the <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> that have been created from a given source Uri.</span></span> <span data-ttu-id="66a64-322">(Bu özellik, üretim uygulamalarına göre değil, tanılama yardımcıları tarafından kullanılır.) Visual Studio "Düzenle ve devam et" özelliği gibi bir tanılama Yardımcısı, kullanıcının, değişikliklerin çalışan uygulamaya uygulanmasını sağlamak için bir ResourceDictionary 'yi düzenlemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-322">(This feature is for use by diagnostic assistants, not by production applications.) A diagnostic assistant such as Visual Studio's "Edit-and-Continue" facility lets its user edit a ResourceDictionary with the intent that the changes be applied to the running application.</span></span> <span data-ttu-id="66a64-323">Bunu elde eden bir adım, çalışan uygulamanın düzenlenmekte olan sözlükten oluşturduğu tüm Resourcesözlüklerini bulmasıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-323">One step in achieving this is finding all the ResourceDictionaries that the running application has created from the dictionary that's being edited.</span></span> <span data-ttu-id="66a64-324">Örneğin, bir uygulama, içeriği belirli bir kaynak URI 'den kopyalanmış bir ResourceDictionary bildirebilir:</span><span class="sxs-lookup"><span data-stu-id="66a64-324">For example, an application can declare a ResourceDictionary whose content is copied from a given source URI:</span></span>

```xml
<ResourceDictionary Source="MyRD.xaml" />
```

<span data-ttu-id="66a64-325">*Myrd. xaml* içindeki özgün biçimlendirmeyi düzenleyen bir tanılama Yardımcısı, sözlüğü bulmak için yeni özelliği kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-325">A diagnostic assistant that edits the original markup in *MyRD.xaml* can use the new feature to locate the dictionary.</span></span> <span data-ttu-id="66a64-326">Özelliği, yeni bir statik yöntem tarafından uygulanır <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-326">The feature is implemented by a new static method, <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="66a64-327">Tanılama Yardımcısı, aşağıdaki kodda gösterildiği gibi özgün biçimlendirmeyi tanımlayan mutlak bir URI kullanarak yeni yöntemi çağırır:</span><span class="sxs-lookup"><span data-stu-id="66a64-327">The diagnostic assistant calls the new method using an absolute Uri that identifies the original markup, as illustrated by the following code:</span></span>

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

<span data-ttu-id="66a64-328"><xref:System.Windows.Diagnostics.VisualDiagnostics>Etkin olmadığı ve ortam değişkeni ayarlanmadığı için yöntem boş bir sıralanabilir değer döndürür [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) .</span><span class="sxs-lookup"><span data-stu-id="66a64-328">The method returns an empty enumerable unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

<span data-ttu-id="66a64-329">**ResourceDictionary sahiplerini bulma**</span><span class="sxs-lookup"><span data-stu-id="66a64-329">**Finding ResourceDictionary owners**</span></span>

<span data-ttu-id="66a64-330">.NET Framework 4.7.2 ile başlayarak, bir tanılama Yardımcısı belirli bir ' ın sahibini bulabilir <xref:Windows.UI.Xaml.ResourceDictionary> .</span><span class="sxs-lookup"><span data-stu-id="66a64-330">Starting with .NET Framework 4.7.2, a diagnostic assistant can locate the owners of a given <xref:Windows.UI.Xaml.ResourceDictionary>.</span></span> <span data-ttu-id="66a64-331">(Özelliği, üretim uygulamalarına göre değil, tanılama yardımcıları tarafından kullanılır.) Bir değişiklik her yapıldığında <xref:Windows.UI.Xaml.ResourceDictionary> WPF, değişiklikten etkilenebilecek tüm [DynamicResource](/dotnet/desktop/wpf/advanced/dynamicresource-markup-extension) başvurularını otomatik olarak bulur.</span><span class="sxs-lookup"><span data-stu-id="66a64-331">(The feature is for use by diagnostic assistants and not by production applications.) Whenever a change is made to a <xref:Windows.UI.Xaml.ResourceDictionary>, WPF automatically finds all [DynamicResource](/dotnet/desktop/wpf/advanced/dynamicresource-markup-extension) references that might be affected by the change.</span></span>

<span data-ttu-id="66a64-332">Visual Studio "Düzenle ve devam et" özelliği gibi bir tanılama Yardımcısı, bu, [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) başvurularını işlemek için bunu genişletmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-332">A diagnostic assistant such as Visual Studio's "Edit-and-Continue" facility may want to extend this to handle [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) references.</span></span> <span data-ttu-id="66a64-333">Bu işlemin ilk adımı, sözlüğün sahiplerini bulledir; diğer bir deyişle, özelliği sözlüğüne başvuran tüm nesneleri bulmak için `Resources` (doğrudan veya dolaylı olarak <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> özelliği aracılığıyla).</span><span class="sxs-lookup"><span data-stu-id="66a64-333">The first step in this process is to find the owners of the dictionary; that is, to find all the objects whose `Resources` property refers to the dictionary (either directly, or indirectly via the <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="66a64-334">Sınıfına uygulanan üç yeni statik yöntem <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> , bir özelliği olan temel türlerin her biri için, `Resources` Bu adımı destekler:</span><span class="sxs-lookup"><span data-stu-id="66a64-334">Three new static methods implemented on the <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> class, one for each of the base types that has a `Resources` property, support this step:</span></span>

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

<span data-ttu-id="66a64-335"><xref:System.Windows.Diagnostics.VisualDiagnostics>Etkin olmadığı ve ortam değişkeni ayarlanmadığı için bu yöntemler boş bir sıralanabilir değer döndürür [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) .</span><span class="sxs-lookup"><span data-stu-id="66a64-335">These methods return an empty enumerable unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

<span data-ttu-id="66a64-336">**StaticResource başvurularını bulma**</span><span class="sxs-lookup"><span data-stu-id="66a64-336">**Finding StaticResource references**</span></span>

<span data-ttu-id="66a64-337">Bir tanılama Yardımcısı, bir [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) başvurusu çözümlendiğinde artık bildirim alabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-337">A diagnostic assistant can now receive a notification whenever a [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) reference is resolved.</span></span> <span data-ttu-id="66a64-338">(Özelliği, üretim uygulamalarına göre değil, tanılama yardımcıları tarafından kullanılır.) Visual Studio "Düzenle ve devam et" özelliği gibi bir tanılama Yardımcısı, bir değişiklik içindeki değeri bir kaynağın tüm kullanımlarını güncelleştirmek isteyebilir <xref:Windows.UI.Xaml.ResourceDictionary> .</span><span class="sxs-lookup"><span data-stu-id="66a64-338">(The feature is for use by diagnostic assistants, not by production applications.) A diagnostic assistant such as Visual Studio's "Edit-and-Continue" facility may want to update all uses of a resource when its value in a <xref:Windows.UI.Xaml.ResourceDictionary> changes.</span></span> <span data-ttu-id="66a64-339">WPF bunu, [DynamicResource](/dotnet/desktop/wpf/advanced/dynamicresource-markup-extension) başvuruları için otomatik olarak yapar, ancak bu şekilde bu, [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) başvuruları için bunu yapmaz.</span><span class="sxs-lookup"><span data-stu-id="66a64-339">WPF does this automatically for [DynamicResource](/dotnet/desktop/wpf/advanced/dynamicresource-markup-extension) references, but it intentionally does not do so for [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) references.</span></span> <span data-ttu-id="66a64-340">.NET Framework 4.7.2 ile başlayarak, tanılama Yardımcısı bu bildirimleri statik kaynak kullanımlarını bulmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-340">Starting with .NET Framework 4.7.2, the diagnostic assistant can use these notifications to locate those uses of the static resource.</span></span>

<span data-ttu-id="66a64-341">Bildirim, yeni olay tarafından uygulanır <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="66a64-341">The notification is implemented by the new <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> event:</span></span>

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

<span data-ttu-id="66a64-342">Bu olay, çalışma zamanı bir [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) başvurusunu her çözdüğünde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="66a64-342">This event is raised whenever the runtime resolves a [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) reference.</span></span> <span data-ttu-id="66a64-343"><xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs>Bağımsız değişkenler, çözümü betimleyen ve bu, [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) başvurusunu barındıran nesne ve özelliği ve <xref:Windows.UI.Xaml.ResourceDictionary> çözüm için kullanılan anahtarı belirtir:</span><span class="sxs-lookup"><span data-stu-id="66a64-343">The <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> arguments describe the resolution, and indicate the object and property that host the [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) reference and the <xref:Windows.UI.Xaml.ResourceDictionary> and key used for the resolution:</span></span>

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

<span data-ttu-id="66a64-344">`add` <xref:System.Windows.Diagnostics.VisualDiagnostics> Etkin olmadığı ve ortam değişkeni ayarlanmadığı takdirde olay oluşturulmaz (ve erişimcisi yok sayılır) [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) .</span><span class="sxs-lookup"><span data-stu-id="66a64-344">The event is not raised (and its `add` accessor is ignored) unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

#### <a name="clickonce"></a><span data-ttu-id="66a64-345">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="66a64-345">ClickOnce</span></span>

<span data-ttu-id="66a64-346">Windows Forms, Windows Presentation Foundation (WPF) ve Office için Visual Studio Araçları (VSTO) için HDPı kullanan uygulamalar ClickOnce kullanılarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-346">HDPI-aware applications for Windows Forms, Windows Presentation Foundation (WPF), and Visual Studio Tools for Office (VSTO) can all be deployed by using ClickOnce.</span></span> <span data-ttu-id="66a64-347">Uygulama bildiriminde aşağıdaki giriş bulunursa, dağıtım .NET Framework 4.7.2 altında başarılı olur:</span><span class="sxs-lookup"><span data-stu-id="66a64-347">If the following entry is found in the application manifest, deployment will succeed under .NET Framework 4.7.2:</span></span>

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

<span data-ttu-id="66a64-348">Windows Forms uygulama için, uygulama bildirimi yerine uygulama yapılandırma dosyasında DPı tanımayı ayarlamaya yönelik önceki geçici çözüm, artık ClickOnce dağıtımının başarılı olması için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="66a64-348">For Windows Forms application, the previous workaround of setting DPI awareness in the application configuration file rather than the application manifest is no longer necessary for ClickOnce deployment to succeed.</span></span>

<a name="v471"></a>

## <a name="whats-new-in-net-framework-471"></a><span data-ttu-id="66a64-349">.NET Framework 4.7.1 yenilikleri</span><span class="sxs-lookup"><span data-stu-id="66a64-349">What's new in .NET Framework 4.7.1</span></span>

<span data-ttu-id="66a64-350">.NET Framework 4.7.1, aşağıdaki alanlardaki yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-350">.NET Framework 4.7.1 includes new features in the following areas:</span></span>

- [<span data-ttu-id="66a64-351">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="66a64-351">Base classes</span></span>](#core471)
- [<span data-ttu-id="66a64-352">Ortak dil çalışma zamanı (CLR)</span><span class="sxs-lookup"><span data-stu-id="66a64-352">Common language runtime (CLR)</span></span>](#clr)
- [<span data-ttu-id="66a64-353">Ağ</span><span class="sxs-lookup"><span data-stu-id="66a64-353">Networking</span></span>](#net471)
- [<span data-ttu-id="66a64-354">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66a64-354">ASP.NET</span></span>](#asp-net471)

<span data-ttu-id="66a64-355">Ayrıca, .NET Framework 4.7.1 ' deki önemli bir odak, bir uygulamanın yardımcı teknoloji kullanıcıları için uygun bir deneyim sağlamasına izin veren gelişmiş erişilebilirliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="66a64-355">In addition, a major focus in .NET Framework 4.7.1 is improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="66a64-356">.NET Framework 4.7.1 ' deki erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için, bkz. [Erişilebilirlik 'deki yenilikler .NET Framework](whats-new-in-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-356">For information on accessibility improvements in .NET Framework 4.7.1, see [What's new in accessibility in .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core471"></a>

#### <a name="base-classes"></a><span data-ttu-id="66a64-357">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="66a64-357">Base classes</span></span>

<span data-ttu-id="66a64-358">**.NET Standard 2,0 desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-358">**Support for .NET Standard 2.0**</span></span>

<span data-ttu-id="66a64-359">[.NET Standard](../../standard/net-standard.md) , standart sürümünü destekleyen her bir .NET uygulamasında kullanılabilir olması gereken bir API kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-359">[.NET Standard](../../standard/net-standard.md) defines a set of APIs that must be available on each .NET implementation that supports that version of the standard.</span></span> <span data-ttu-id="66a64-360">.NET Framework 4.7.1, .NET Standard 2,0 ' yi tam olarak destekler ve .NET Standard 2,0 ' de tanımlanan [200 API 'leri](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) ekler ve .NET Framework 4.6.1, 4.6.2 ve 4,7.</span><span class="sxs-lookup"><span data-stu-id="66a64-360">.NET Framework 4.7.1 fully supports .NET Standard 2.0 and adds [about 200 APIs](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) that are defined in .NET Standard 2.0 and are missing from .NET Framework 4.6.1, 4.6.2, and 4.7.</span></span> <span data-ttu-id="66a64-361">(Bu .NET Framework sürümlerinin yalnızca hedef sistemde ek .NET Standard destek dosyaları da dağıtılmışsa .NET Standard 2,0 desteklediğine unutmayın.) Daha fazla bilgi için, [.NET Framework 4.7.1 çalışma zamanı ve derleyici özellikleri blog gönderisinde](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) "BCL-.NET Standard 2,0 desteği" ne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-361">(Note that these versions of .NET Framework support .NET Standard 2.0 only if additional .NET Standard support files are also deployed on the target system.) For more information, see "BCL - .NET Standard 2.0 Support" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<span data-ttu-id="66a64-362">**Yapılandırma oluşturucuları için destek**</span><span class="sxs-lookup"><span data-stu-id="66a64-362">**Support for configuration builders**</span></span>

<span data-ttu-id="66a64-363">Yapılandırma üreticileri, geliştiricilerin uygulamalar için yapılandırma ayarlarını çalışma zamanında dinamik olarak eklemesine ve oluşturmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-363">Configuration builders allow developers to inject and build configuration settings for applications dynamically at run time.</span></span> <span data-ttu-id="66a64-364">Özel yapılandırma oluşturucuları, bir yapılandırma bölümünde var olan verileri değiştirmek veya tamamen sıfırdan bir yapılandırma bölümü oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-364">Custom configuration builders can be used to modify existing data in a configuration section or to build a configuration section entirely from scratch.</span></span> <span data-ttu-id="66a64-365">Yapılandırma oluşturucuları olmadan,. config dosyaları statiktir ve ayarları bir uygulama başlatılmadan önce bir süre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-365">Without configuration builders, .config files are static, and their settings are defined some time before an application is launched.</span></span>

<span data-ttu-id="66a64-366">Özel bir yapılandırma Oluşturucu oluşturmak için, oluşturucuyu soyut sınıftan türetirsiniz <xref:System.Configuration.ConfigurationBuilder> ve <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> ve ' ı geçersiz kılarsınız <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-366">To create a custom configuration builder, you derive your builder from the abstract <xref:System.Configuration.ConfigurationBuilder> class and override its <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> and <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="66a64-367">Ayrıca, Oluşturucularınızı. config dosyanızda tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="66a64-367">You also define your builders in your .config file.</span></span> <span data-ttu-id="66a64-368">Daha fazla bilgi için, [.NET Framework 4.7.1 ASP.net ve yapılandırma özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisinin "yapılandırma oluşturucuları" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-368">For more information, see the "Configuration Builders" section in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="66a64-369">**Çalışma zamanı özellik algılama**</span><span class="sxs-lookup"><span data-stu-id="66a64-369">**Run-time feature detection**</span></span>

<span data-ttu-id="66a64-370"><xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType>Sınıfı, derleme zamanında veya çalışma zamanında, belirli bir .NET uygulamasında önceden tanımlanmış bir özelliğin desteklenip desteklenmediğini belirlemede bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-370">The <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> class provides a mechanism for determine whether a predefined feature is supported on a given .NET implementation at compile time or run time.</span></span> <span data-ttu-id="66a64-371">Derleme zamanında bir derleyici, özelliğin desteklenip desteklenmediğini anlamak için belirtilen alanın mevcut olup olmadığını denetleyebilir. varsa, bu özellikten faydalanan kodu yayabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-371">At compile time, a compiler can check whether a specified field exists to determine whether the feature is supported; if so, it can emit code that takes advantage of that feature.</span></span> <span data-ttu-id="66a64-372">Çalışma zamanında bir uygulama, <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> çalışma zamanında kodu göndermeden önce yöntemini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-372">At run time, an application can call the <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> method before emitting code at runtime.</span></span> <span data-ttu-id="66a64-373">Daha fazla bilgi için bkz. [çalışma zamanı tarafından desteklenen özellikleri anlatmak için yardımcı yöntemi ekleme](https://github.com/dotnet/corefx/issues/17116).</span><span class="sxs-lookup"><span data-stu-id="66a64-373">For more information, see [Add helper method to describe features supported by the runtime](https://github.com/dotnet/corefx/issues/17116).</span></span>

<span data-ttu-id="66a64-374">**Değer tanımlama grubu türleri seri hale getirilebilir**</span><span class="sxs-lookup"><span data-stu-id="66a64-374">**Value tuple types are serializable**</span></span>

<span data-ttu-id="66a64-375">.NET Framework 4.7.1 ile başlayarak <xref:System.ValueTuple?displayProperty=nameWithType> ve ilişkili genel türleri, ikili Serileştirmeye izin veren [seri hale getirilebilir](xref:System.SerializableAttribute)olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="66a64-375">Starting with .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> and its associated generic types are marked as [Serializable](xref:System.SerializableAttribute), which allows binary serialization.</span></span> <span data-ttu-id="66a64-376">Bu, ve gibi demet türlerinin <xref:System.Tuple%603> <xref:System.Tuple%604> değer tanımlama grubu türlerine daha kolay olmasını sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-376">This should make migrating Tuple types, such as <xref:System.Tuple%603> and <xref:System.Tuple%604>, to value tuple types easier.</span></span> <span data-ttu-id="66a64-377">Daha fazla bilgi için, [.NET Framework 4.7.1 çalışma zamanı ve derleyici özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisinde "derleyici--ValueTuple" seri hale getirilebilir "başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-377">For more information, see "Compiler -- ValueTuple is Serializable" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<span data-ttu-id="66a64-378">**Salt okuma başvuruları desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-378">**Support for read-only references**</span></span>

<span data-ttu-id="66a64-379">.NET Framework 4.7.1, öğesini ekler <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-379">.NET Framework 4.7.1 adds the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="66a64-380">Bu öznitelik, salt okuma başvuru dönüş türleri veya parametreleri olan üyeleri işaretlemek için dil derleyicileri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66a64-380">This attribute is used by language compilers to mark members that have read-only ref return types or parameters.</span></span> <span data-ttu-id="66a64-381">Daha fazla bilgi için, [.NET Framework 4.7.1 çalışma zamanı ve derleyici özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisinde "derleyici--ReadOnlyReferences desteği" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-381">For more information, see "Compiler -- Support for ReadOnlyReferences" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span> <span data-ttu-id="66a64-382">Başvuru dönüş değerleri hakkında daha fazla bilgi için bkz. [ref Return Values ve ref Locals (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) ve [ref return values (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-382">For information on ref return values, see [Ref return values and ref locals (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) and [Ref return values (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).</span></span>

<a name="clr"></a>

#### <a name="common-language-runtime-clr"></a><span data-ttu-id="66a64-383">Ortak dil çalışma zamanı (CLR)</span><span class="sxs-lookup"><span data-stu-id="66a64-383">Common language runtime (CLR)</span></span>

<span data-ttu-id="66a64-384">**Çöp toplama performansı iyileştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="66a64-384">**Garbage collection performance improvements**</span></span>

<span data-ttu-id="66a64-385">.NET Framework 4.7.1 'teki çöp toplama (GC) değişiklikleri, özellikle büyük nesne yığını (LOH) ayırmaları için genel performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-385">Changes to garbage collection (GC) in .NET Framework 4.7.1 improve overall performance, especially for large object heap (LOH) allocations.</span></span> <span data-ttu-id="66a64-386">.NET Framework 4.7.1 ' de, arka plan GC, SOH 'yi ortaya çıkaran zaman, LOH ayırmalarının oluşmasına izin veren küçük nesne yığını (SOH) ve LOH ayırmaları için ayrı kilitler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="66a64-386">In .NET Framework 4.7.1, separate locks are used for small object heap (SOH) and LOH allocations, which allows LOH allocations to occur when background GC is sweeping the SOH.</span></span> <span data-ttu-id="66a64-387">Sonuç olarak, çok sayıda LOH ayırması yapan uygulamalar, ayırma Kilidi çakışması ve gelişmiş performans konusunda bir azalma görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="66a64-387">As a result, applications that make a large number of LOH allocations should see a reduction in allocation lock contention and improved performance.</span></span> <span data-ttu-id="66a64-388">Daha fazla bilgi için, [.NET Framework 4.7.1 çalışma zamanı ve derleyici özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisindeki "çalışma zamanı--GC performansı iyileştirmeleri" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-388">For more information, see the "Runtime -- GC Performance Improvements" section in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<a name="net471"/>

#### <a name="networking"></a><span data-ttu-id="66a64-389">Ağ</span><span class="sxs-lookup"><span data-stu-id="66a64-389">Networking</span></span>

<span data-ttu-id="66a64-390">**Message. HashAlgorithm için SHA-2 desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-390">**SHA-2 support for Message.HashAlgorithm**</span></span>

<span data-ttu-id="66a64-391">.NET Framework 4,7 ve önceki sürümlerde, <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> özelliği <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> yalnızca ve değerlerini destekler <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-391">In .NET Framework 4.7 and earlier versions, the <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> property supported values of <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> and <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> only.</span></span> <span data-ttu-id="66a64-392">.NET Framework 4.7.1,, ve ile başlayarak <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType> <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType> <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="66a64-392">Starting with .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, and <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> are also supported.</span></span> <span data-ttu-id="66a64-393">Değerin <xref:System.Messaging.Message> kendisi karma olmadığından ve yalnızca MSMQ 'ya değer geçirdiğinden, bu değerin gerçekten kullanılıp kullanılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="66a64-393">Whether this value is actually used depends on MSMQ, since the <xref:System.Messaging.Message> instance itself does no hashing but simply passes on values to MSMQ.</span></span> <span data-ttu-id="66a64-394">Daha fazla bilgi için, [.NET Framework 4.7.1 ASP.net ve yapılandırma özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisinin "Message. HASHALGORITHM için SHA-2 desteği" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-394">For more information, see the "SHA-2 support for Message.HashAlgorithm" section in the [.NET Framework 4.7.1 ASP.NET and Configuration features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<a name="asp-net471"></a>

#### <a name="aspnet"></a><span data-ttu-id="66a64-395">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66a64-395">ASP.NET</span></span>

<span data-ttu-id="66a64-396">**ASP.NET uygulamalarındaki yürütme adımları**</span><span class="sxs-lookup"><span data-stu-id="66a64-396">**Execution steps in ASP.NET applications**</span></span>

<span data-ttu-id="66a64-397">ASP.NET, 23 olay içeren önceden tanımlanmış bir işlem hattındaki istekleri işler.</span><span class="sxs-lookup"><span data-stu-id="66a64-397">ASP.NET processes requests in a predefined pipeline that includes 23 events.</span></span> <span data-ttu-id="66a64-398">ASP.NET, her olay işleyicisini yürütme adımı olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="66a64-398">ASP.NET executes each event handler as an execution step.</span></span> <span data-ttu-id="66a64-399">ASP.NET ' nin .NET Framework 4,7 ' e kadar olan sürümlerinde, yerel ve yönetilen iş parçacıkları arasında geçiş yapmak nedeniyle ASP.NET yürütme bağlamını akamaz.</span><span class="sxs-lookup"><span data-stu-id="66a64-399">In versions of ASP.NET up to .NET Framework 4.7, ASP.NET can't flow the execution context due to switching between native and managed threads.</span></span> <span data-ttu-id="66a64-400">Bunun yerine, ASP.NET yalnızca öğesini seçmeli olarak akar <xref:System.Web.HttpContext> .</span><span class="sxs-lookup"><span data-stu-id="66a64-400">Instead, ASP.NET selectively flows only the <xref:System.Web.HttpContext>.</span></span> <span data-ttu-id="66a64-401">Yöntemi, .NET Framework 4.7.1 ile başlayarak, <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> Ayrıca modüllerin çevresel verileri geri yüklemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-401">Starting with .NET Framework 4.7.1, the <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> method also allows modules to restore ambient data.</span></span> <span data-ttu-id="66a64-402">Bu özellik, izleme, profil oluşturma, tanılama veya işlemlerle ilgili kitaplıklara, örneğin, uygulamanın yürütme akışı hakkında endişeleri hedefleder.</span><span class="sxs-lookup"><span data-stu-id="66a64-402">This feature is targeted at libraries concerned with tracing, profiling, diagnostics, or transactions, for example, that care about the execution flow of the application.</span></span> <span data-ttu-id="66a64-403">Daha fazla bilgi için, [.NET Framework 4.7.1 ASP.net ve yapılandırma özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisine "ASP.net Execution Step Feature" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-403">For more information, see the "ASP.NET Execution Step Feature" in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="66a64-404">**ASP.NET HttpCookie ayrıştırma**</span><span class="sxs-lookup"><span data-stu-id="66a64-404">**ASP.NET HttpCookie parsing**</span></span>

<span data-ttu-id="66a64-405">.NET Framework 4.7.1, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType> bir dizeden bir nesne oluşturmak için standartlaştırılmış bir yol sağlayan <xref:System.Web.HttpCookie> ve sona erme tarihi ve yolu gibi tanımlama bilgisi değerlerini doğru şekilde atayan yeni bir yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-405">.NET Framework 4.7.1 includes a new method, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, that provides a standardized way to create an <xref:System.Web.HttpCookie> object from a string and accurately assign cookie values such as expiration date and path.</span></span> <span data-ttu-id="66a64-406">Daha fazla bilgi için, [.NET Framework 4.7.1 ASP.net ve yapılandırma özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisine "ASP.net HttpCookie ayrıştırma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-406">For more information, see "ASP.NET HttpCookie parsing" in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="66a64-407">**ASP.NET Forms kimlik doğrulama kimlik bilgileri için SHA-2 karma seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="66a64-407">**SHA-2 hash options for ASP.NET forms authentication credentials**</span></span>

<span data-ttu-id="66a64-408">.NET Framework 4,7 ve önceki sürümlerde, ASP.NET izin verilen geliştiricilerin, Kullanıcı kimlik bilgilerini MD5 veya SHA1 kullanarak yapılandırma dosyalarında karma parolalara depolamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-408">In .NET Framework 4.7 and earlier versions, ASP.NET allowed developers to store user credentials with hashed passwords in configuration files using either MD5 or SHA1.</span></span> <span data-ttu-id="66a64-409">.NET Framework 4.7.1 ile başlayarak, ASP.NET, SHA256, SHA384 ve SHA512 olur gibi yeni güvenli SHA-2 karma seçeneklerini de destekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-409">Starting with .NET Framework 4.7.1, ASP.NET also supports new secure SHA-2 hash options such as SHA256, SHA384, and SHA512.</span></span> <span data-ttu-id="66a64-410">SHA1 varsayılan olarak kalır ve varsayılan olmayan bir karma algoritması Web yapılandırma dosyasında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-410">SHA1 remains the default, and a non-default hash algorithm can be defined in the web configuration file.</span></span> <span data-ttu-id="66a64-411">Örnek:</span><span class="sxs-lookup"><span data-stu-id="66a64-411">For example:</span></span>

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

<a name="v47"></a>

## <a name="whats-new-in-net-framework-47"></a><span data-ttu-id="66a64-412">.NET Framework 4,7 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="66a64-412">What's new in .NET Framework 4.7</span></span>

<span data-ttu-id="66a64-413">.NET Framework 4,7, aşağıdaki alanlardaki yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-413">.NET Framework 4.7 includes new features in the following areas:</span></span>

- [<span data-ttu-id="66a64-414">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="66a64-414">Base classes</span></span>](#Core47)
- [<span data-ttu-id="66a64-415">Ağ</span><span class="sxs-lookup"><span data-stu-id="66a64-415">Networking</span></span>](#net47)
- [<span data-ttu-id="66a64-416">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66a64-416">ASP.NET</span></span>](#ASP-NET47)
- [<span data-ttu-id="66a64-417">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="66a64-417">Windows Communication Foundation (WCF)</span></span>](#wcf47)
- [<span data-ttu-id="66a64-418">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66a64-418">Windows Forms</span></span>](#wf47)
- [<span data-ttu-id="66a64-419">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="66a64-419">Windows Presentation Foundation (WPF)</span></span>](#WPF47)

<span data-ttu-id="66a64-420">.NET Framework 4,7 ' ye eklenen yeni API 'lerin bir listesi için bkz. GitHub 'da [.NET Framework 4,7 API değişiklikleri](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) .</span><span class="sxs-lookup"><span data-stu-id="66a64-420">For a list of new APIs added to .NET Framework 4.7, see [.NET Framework 4.7 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) on GitHub.</span></span> <span data-ttu-id="66a64-421">.NET Framework 4,7 ' deki Özellik geliştirmeleri ve hata düzeltmeleri listesi için GitHub 'da [.NET Framework 4,7 değişiklik listesine](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-421">For a list of feature improvements and bug fixes in .NET Framework 4.7, see [.NET Framework 4.7 List of Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) on GitHub.</span></span> <span data-ttu-id="66a64-422">Daha fazla bilgi için bkz. .NET blogda [.NET Framework 4,7 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) .</span><span class="sxs-lookup"><span data-stu-id="66a64-422">For more information, see [Announcing .NET Framework 4.7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) in the .NET blog.</span></span>

<a name="Core47"></a>

#### <a name="base-classes"></a><span data-ttu-id="66a64-423">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="66a64-423">Base classes</span></span>

<span data-ttu-id="66a64-424">.NET Framework 4,7 tarafından serileştirme şunu geliştirir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> :</span><span class="sxs-lookup"><span data-stu-id="66a64-424">.NET Framework 4.7 improves serialization by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>

<span data-ttu-id="66a64-425">**Eliptik eğri şifrelemesi (ECC) Ile gelişmiş işlevsellik**</span><span class="sxs-lookup"><span data-stu-id="66a64-425">**Enhanced functionality with Elliptic Curve Cryptography (ECC)** _</span></span>

<span data-ttu-id="66a64-426">.NET Framework 4,7 ' de, `ImportParameters(ECParameters)` <xref:System.Security.Cryptography.ECDsa> <xref:System.Security.Cryptography.ECDiffieHellman> bir nesnenin zaten oluşturulmuş bir anahtarı göstermesini sağlamak için ve sınıflarına yöntemler eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-426">In .NET Framework 4.7, `ImportParameters(ECParameters)` methods were added to the <xref:System.Security.Cryptography.ECDsa> and <xref:System.Security.Cryptography.ECDiffieHellman> classes to allow for an object to represent an already-established key.</span></span> <span data-ttu-id="66a64-427">`ExportParameters(Boolean)`Açık eğri parametreleri kullanılarak anahtarı dışarı aktarmak için bir yöntem de eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-427">An `ExportParameters(Boolean)` method was also added for exporting the key using explicit curve parameters.</span></span>

<span data-ttu-id="66a64-428">.NET Framework 4,7 ayrıca ek eğriler (Brainpool eğrisi paketi dahil) için destek de ekler ve yeni <xref:System.Security.Cryptography.ECDsa.Create%2A> ve fabrika yöntemleriyle oluşturma kolaylığı için önceden tanımlanmış tanımlar ekledi <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> .</span><span class="sxs-lookup"><span data-stu-id="66a64-428">.NET Framework 4.7 also adds support for additional curves (including the Brainpool curve suite), and has added predefined definitions for ease-of-creation through the new <xref:System.Security.Cryptography.ECDsa.Create%2A> and <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> factory methods.</span></span>

<span data-ttu-id="66a64-429">GitHub 'da [4,7 .NET Framework şifreleme geliştirmesi örneği](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-429">You can see an [example of .NET Framework 4.7 cryptography improvements](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) on GitHub.</span></span>

<span data-ttu-id="66a64-430">_ *DataContractJsonSerializer tarafından denetim karakterleri Için daha iyi destek*\*</span><span class="sxs-lookup"><span data-stu-id="66a64-430">_ *Better support for control characters by the DataContractJsonSerializer*\*</span></span>

<span data-ttu-id="66a64-431">.NET Framework 4,7 ' de, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sınıf ECMAScript 6 standardı ile uyum içindeki denetim karakterlerini seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-431">In .NET Framework 4.7, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> class serializes control characters in conformity with the ECMAScript 6 standard.</span></span> <span data-ttu-id="66a64-432">Bu davranış, .NET Framework 4,7 ' i hedefleyen uygulamalar için varsayılan olarak etkindir ve .NET Framework 4,7 altında çalışan ve .NET Framework önceki bir sürümünü hedefleyen uygulamalar için bir kabul etme özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-432">This behavior is enabled by default for applications that target .NET Framework 4.7, and is an opt-in feature for applications that are running under .NET Framework 4.7 but target a previous version of .NET Framework.</span></span> <span data-ttu-id="66a64-433">Daha fazla bilgi için [uygulama uyumluluğu](../migration-guide/application-compatibility.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-433">For more information, see the [Application compatibility](../migration-guide/application-compatibility.md) section.</span></span>

<a name="net47"></a>

#### <a name="networking"></a><span data-ttu-id="66a64-434">Ağ</span><span class="sxs-lookup"><span data-stu-id="66a64-434">Networking</span></span>

<span data-ttu-id="66a64-435">.NET Framework 4,7, ağla ilgili aşağıdaki özelliği ekler:</span><span class="sxs-lookup"><span data-stu-id="66a64-435">.NET Framework 4.7 adds the following network-related feature:</span></span>

<span data-ttu-id="66a64-436">**TLS protokolleri Için varsayılan işletim sistemi desteği** _</span><span class="sxs-lookup"><span data-stu-id="66a64-436">**Default operating system support for TLS protocols** _</span></span>

<span data-ttu-id="66a64-437"><xref:System.Net.Security.SslStream?displayProperty=nameWithType>Ve http, FTP ve SMTP gibi yukarı yığın bileşenleri tarafından kullanılan TLS yığını, geliştiricilerin işletim sistemi tarafından desteklenen varsayılan TLS protokollerini kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="66a64-437">The TLS stack, which is used by <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and up-stack components such as HTTP, FTP, and SMTP, allows developers to use the default TLS protocols supported by the operating system.</span></span> <span data-ttu-id="66a64-438">Geliştiricilerin artık bir TLS sürümüne sabit kod olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="66a64-438">Developers need no longer hard-code a TLS version.</span></span>

<a name="ASP-NET47"></a>

#### <a name="aspnet"></a><span data-ttu-id="66a64-439">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66a64-439">ASP.NET</span></span>

<span data-ttu-id="66a64-440">.NET Framework 4,7 ' de, ASP.NET aşağıdaki yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-440">In .NET Framework 4.7, ASP.NET includes the following new features:</span></span>

<span data-ttu-id="66a64-441">_ *Nesne önbelleği genişletilebilirliği*\*</span><span class="sxs-lookup"><span data-stu-id="66a64-441">_ *Object Cache Extensibility*\*</span></span>

<span data-ttu-id="66a64-442">ASP.NET, .NET Framework 4,7 ' den başlayarak, geliştiricilerin bellek içi nesne önbelleğe alma ve bellek izleme için varsayılan ASP.NET uygulamalarını değiştirmesine izin veren yeni bir API kümesi ekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-442">Starting with .NET Framework 4.7, ASP.NET adds a new set of APIs that allow developers to replace the default ASP.NET implementations for in-memory object caching and memory monitoring.</span></span> <span data-ttu-id="66a64-443">ASP.NET uygulamasının yeterli olmaması halinde geliştiriciler artık aşağıdaki üç bileşenden birini değiştirebilir:</span><span class="sxs-lookup"><span data-stu-id="66a64-443">Developers can now replace any of the following three components if the ASP.NET implementation is not adequate:</span></span>

- <span data-ttu-id="66a64-444">**Nesne önbelleği deposu**.</span><span class="sxs-lookup"><span data-stu-id="66a64-444">**Object Cache Store**.</span></span> <span data-ttu-id="66a64-445">Yeni önbellek sağlayıcıları yapılandırma bölümünü kullanarak, geliştiriciler yeni **ICacheStoreProvider** arabirimini kullanarak bir ASP.NET uygulaması için nesne önbelleğinin yeni uygulamalarını yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-445">By using the new cache providers configuration section, developers can plug in new implementations of an object cache for an ASP.NET application by using the new **ICacheStoreProvider** interface.</span></span>

- <span data-ttu-id="66a64-446">**Bellek izleme**.</span><span class="sxs-lookup"><span data-stu-id="66a64-446">**Memory monitoring**.</span></span> <span data-ttu-id="66a64-447">ASP.NET ' deki varsayılan bellek İzleyicisi, uygulamaları, işlem için yapılandırılmış özel bayt sınırına yakın bir şekilde çalıştığında veya makinenin toplam kullanılabilir fiziksel RAM üzerinde azaldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-447">The default memory monitor in ASP.NET notifies applications when they are running close to the configured private bytes limit for the process, or when the machine is low on total available physical RAM.</span></span> <span data-ttu-id="66a64-448">Bu limitlerin yakınında, bildirimler tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="66a64-448">When these limits are near, notifications are fired.</span></span> <span data-ttu-id="66a64-449">Bazı uygulamalar için bildirimler, yararlı yeniden eylemlere izin vermek üzere yapılandırılan sınırlara çok yakın şekilde harekete geçirilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-449">For some applications, notifications are fired too close to the configured limits to allow for useful reactions.</span></span> <span data-ttu-id="66a64-450">Geliştiriciler artık özelliğini kullanarak varsayılan değerini değiştirmek için kendi bellek izleyicilerini yazabilir <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-450">Developers can now write their own memory monitors to replace the default by using the <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="66a64-451">**Bellek sınırı yeniden eylemleri**.</span><span class="sxs-lookup"><span data-stu-id="66a64-451">**Memory Limit Reactions**.</span></span> <span data-ttu-id="66a64-452">Varsayılan olarak, ASP.NET, nesne önbelleğini kırpmaya çalışır ve <xref:System.GC.Collect%2A?displayProperty=nameWithType> özel bayt işlem sınırı yakınında düzenli olarak çağrı gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-452">By default, ASP.NET attempts to trim the object cache and periodically call <xref:System.GC.Collect%2A?displayProperty=nameWithType> when the private byte process limit is near.</span></span> <span data-ttu-id="66a64-453">Bazı uygulamalarda, çağrı sıklığı <xref:System.GC.Collect%2A?displayProperty=nameWithType> veya kırpılan önbellek miktarı verimsiz olur.</span><span class="sxs-lookup"><span data-stu-id="66a64-453">For some applications, the frequency of calls to <xref:System.GC.Collect%2A?displayProperty=nameWithType> or the amount of cache that is trimmed are inefficient.</span></span> <span data-ttu-id="66a64-454">Geliştiriciler artık **ıgözlemci** uygulamalarını uygulamanın bellek izleyicisine abone olarak varsayılan davranışı değiştirebilir veya tamamlayabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-454">Developers can now replace or supplement the default behavior by subscribing **IObserver** implementations to the application's memory monitor.</span></span>

<a name="wcf47"></a>

#### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="66a64-455">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="66a64-455">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="66a64-456">Windows Communication Foundation (WCF) aşağıdaki özellikleri ve değişiklikleri ekler:</span><span class="sxs-lookup"><span data-stu-id="66a64-456">Windows Communication Foundation (WCF) adds the following features and changes:</span></span>

<span data-ttu-id="66a64-457">**Varsayılan ileti güvenlik ayarlarını TLS 1,1 veya TLS 1,2 olarak yapılandırma olanağı**</span><span class="sxs-lookup"><span data-stu-id="66a64-457">**Ability to configure the default message security settings to TLS 1.1 or TLS 1.2**</span></span>

<span data-ttu-id="66a64-458">WCF, .NET Framework 4,7 ' den itibaren varsayılan ileti güvenlik protokolü olarak SSL 3,0 ve TLS 1,0 ' ye ek olarak TLS 1,1 veya TLS 1,2 yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-458">Starting with .NET Framework 4.7, WCF allows you to configure TLS 1.1 or TLS 1.2 in addition to SSL 3.0 and TLS 1.0 as the default message security protocol.</span></span> <span data-ttu-id="66a64-459">Bu bir kabul etme ayarıdır; etkinleştirmek için, uygulama yapılandırma dosyanıza aşağıdaki girişi eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="66a64-459">This is an opt-in setting; to enable it, you must add the following entry to your application configuration file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

<span data-ttu-id="66a64-460">**WCF uygulamalarının ve WCF serileştirmenin güvenilirliği geliştirildi**</span><span class="sxs-lookup"><span data-stu-id="66a64-460">**Improved reliability of WCF applications and WCF serialization**</span></span>

<span data-ttu-id="66a64-461">WCF, yarış koşullarını ortadan kaldıran bir dizi kod değişikliği içerir, böylece performansı ve serileştirme seçeneklerinin güvenilirliğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-461">WCF includes a number of code changes that eliminate race conditions, thereby improving performance and the reliability of serialization options.</span></span> <span data-ttu-id="66a64-462">Bunlar:</span><span class="sxs-lookup"><span data-stu-id="66a64-462">These include:</span></span>

- <span data-ttu-id="66a64-463">**SocketConnection. BeginRead** ve **SocketConnection. Read** çağrılarına zaman uyumsuz ve zaman uyumlu kod karıştırma için daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="66a64-463">Better support for mixing asynchronous and synchronous code in calls to **SocketConnection.BeginRead** and **SocketConnection.Read**.</span></span>
- <span data-ttu-id="66a64-464">**Sharedconnectionlistener** ve **DuplexChannelBinder** ile bağlantı iptal edildiğinde iyileştirilmiş güvenilirlik.</span><span class="sxs-lookup"><span data-stu-id="66a64-464">Improved reliability when aborting a connection with **SharedConnectionListener** and **DuplexChannelBinder**.</span></span>
- <span data-ttu-id="66a64-465">Yöntemi çağırırken serileştirme işlemlerinin güvenilirliği geliştirildi <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-465">Improved reliability of serialization operations when calling the <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> method.</span></span>
- <span data-ttu-id="66a64-466">**Channeleşitleyici. removewaiter** yöntemi çağırarak bir garson kaldırılırken güvenilirlik artırıldı.</span><span class="sxs-lookup"><span data-stu-id="66a64-466">Improved reliability when removing a waiter by calling the **ChannelSynchronizer.RemoveWaiter** method.</span></span>

<a name="wf47"></a>

#### <a name="windows-forms"></a><span data-ttu-id="66a64-467">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="66a64-467">Windows Forms</span></span>

<span data-ttu-id="66a64-468">.NET Framework 4,7 ' de, Windows Forms yüksek DPı izleyicileri desteğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-468">In .NET Framework 4.7, Windows Forms improves support for high DPI monitors.</span></span>

<span data-ttu-id="66a64-469">**Yüksek DPı desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-469">**High DPI support**</span></span>

<span data-ttu-id="66a64-470">.NET Framework 4,7 ' i hedefleyen uygulamalarla başlayarak Windows Forms uygulamalar için yüksek DPı ve dinamik DPı desteği .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66a64-470">Starting with applications that target .NET Framework 4.7, .NET Framework features high DPI and dynamic DPI support for Windows Forms applications.</span></span> <span data-ttu-id="66a64-471">Yüksek DPı desteği, yüksek DPı izleyicilerinde form ve denetimlerin düzen ve görünümünü geliştirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-471">High DPI support improves the layout and appearance of forms and controls on high DPI monitors.</span></span> <span data-ttu-id="66a64-472">Dinamik DPı, Kullanıcı DPı 'yi değiştirdiğinde form ve denetimlerin yerleşimini ve görünümünü değiştirir ve çalışan bir uygulamanın ölçek faktörünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="66a64-472">Dynamic DPI changes the layout and appearance of forms and controls when the user changes the DPI or display scale factor of a running application.</span></span>

<span data-ttu-id="66a64-473">Yüksek DPı desteği, uygulama yapılandırma dosyanızda bir bölümü tanımlayarak yapılandırdığınız bir katılım özelliğidir [\<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) .</span><span class="sxs-lookup"><span data-stu-id="66a64-473">High DPI support is an opt-in feature that you configure by defining a [\<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) section in your application configuration file.</span></span> <span data-ttu-id="66a64-474">Windows Forms uygulamanıza yüksek DPı desteği ve dinamik DPı desteği ekleme hakkında daha fazla bilgi için, bkz. [Windows Forms yüksek DPI desteği](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms).</span><span class="sxs-lookup"><span data-stu-id="66a64-474">For more information on adding high DPI support and dynamic DPI support to your Windows Forms application, see [High DPI Support in Windows Forms](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms).</span></span>

<a name="WPF47"></a>

#### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="66a64-475">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="66a64-475">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="66a64-476">.NET Framework 4,7 ' de WPF aşağıdaki geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-476">In .NET Framework 4.7, WPF includes the following enhancements:</span></span>

<span data-ttu-id="66a64-477">**Windows WM_POINTER iletilerine dayalı bir dokunmatik/Stilus yığını desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-477">**Support for a touch/stylus stack based on Windows WM_POINTER messages**</span></span>

<span data-ttu-id="66a64-478">Artık Windows mürekkep hizmetleri platformu (WıSS) yerine [WM_POINTER iletilerine](/previous-versions/windows/desktop/InputMsg/messages) dayalı bir dokunmatik/Stilus yığını kullanma seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="66a64-478">You now have the option of using a touch/stylus stack based on [WM_POINTER messages](/previous-versions/windows/desktop/InputMsg/messages) instead of the Windows Ink Services Platform (WISP).</span></span> <span data-ttu-id="66a64-479">Bu, .NET Framework bir katılım özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-479">This is an opt-in feature in .NET Framework.</span></span> <span data-ttu-id="66a64-480">Daha fazla bilgi için [uygulama uyumluluğu](../migration-guide/application-compatibility.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-480">For more information, see the [Application compatibility](../migration-guide/application-compatibility.md) section.</span></span>

<span data-ttu-id="66a64-481">**WPF yazdırma API 'Leri için yeni uygulama**</span><span class="sxs-lookup"><span data-stu-id="66a64-481">**New implementation for WPF printing APIs**</span></span>

<span data-ttu-id="66a64-482">WPF 'nin sınıftaki yazdırma API 'Leri <xref:System.Printing.PrintQueue?displayProperty=nameWithType> , kullanım dışı olan [XPS yazdırma API](/windows/desktop/printdocs/xps-printing)'Si yerine Windows [yazdırma belgesi paketi API](/windows/desktop/printdocs/tailored-app-printing-api) 'sini çağırır.</span><span class="sxs-lookup"><span data-stu-id="66a64-482">WPF's printing APIs in the <xref:System.Printing.PrintQueue?displayProperty=nameWithType> class call the Windows [Print Document Package API](/windows/desktop/printdocs/tailored-app-printing-api) instead of the deprecated [XPS Print API](/windows/desktop/printdocs/xps-printing).</span></span> <span data-ttu-id="66a64-483">Bu değişikliğin uygulama uyumluluğuna etkisi için [uygulama uyumluluğu](../migration-guide/application-compatibility.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-483">For the impact of this change on application compatibility, see the [Application compatibility](../migration-guide/application-compatibility.md) section.</span></span>

<a name="v462"></a>

## <a name="whats-new-in-net-framework-462"></a><span data-ttu-id="66a64-484">.NET Framework 4.6.2 yenilikleri</span><span class="sxs-lookup"><span data-stu-id="66a64-484">What's new in .NET Framework 4.6.2</span></span>

<span data-ttu-id="66a64-485">.NET Framework 4.6.2, aşağıdaki alanlardaki yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-485">.NET Framework 4.6.2 includes new features in the following areas:</span></span>

- [<span data-ttu-id="66a64-486">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66a64-486">ASP.NET</span></span>](#ASPNET462)

- [<span data-ttu-id="66a64-487">Karakter kategorileri</span><span class="sxs-lookup"><span data-stu-id="66a64-487">Character categories</span></span>](#Strings)

- [<span data-ttu-id="66a64-488">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="66a64-488">Cryptography</span></span>](#Crypto462)

- [<span data-ttu-id="66a64-489">SqlClient</span><span class="sxs-lookup"><span data-stu-id="66a64-489">SqlClient</span></span>](#SQLClient)

- [<span data-ttu-id="66a64-490">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="66a64-490">Windows Communication Foundation</span></span>](#WCF)

- [<span data-ttu-id="66a64-491">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="66a64-491">Windows Presentation Foundation (WPF)</span></span>](#WPF462)

- [<span data-ttu-id="66a64-492">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="66a64-492">Windows Workflow Foundation (WF)</span></span>](#WF462)

- [<span data-ttu-id="66a64-493">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="66a64-493">ClickOnce</span></span>](#clickonce-1)

- [<span data-ttu-id="66a64-494">Windows Forms ve WPF uygulamalarını UWP uygulamalarına dönüştürme</span><span class="sxs-lookup"><span data-stu-id="66a64-494">Converting Windows Forms and WPF apps to UWP apps</span></span>](#UWPConvert)

- [<span data-ttu-id="66a64-495">Hata ayıklama geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="66a64-495">Debugging improvements</span></span>](#Debug462)

<span data-ttu-id="66a64-496">.NET Framework 4.6.2 'e eklenen yeni API 'lerin bir listesi için bkz. GitHub 'da [.NET Framework 4.6.2 API değişiklikleri](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) .</span><span class="sxs-lookup"><span data-stu-id="66a64-496">For a list of new APIs added to .NET Framework 4.6.2, see [.NET Framework 4.6.2 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) on GitHub.</span></span> <span data-ttu-id="66a64-497">.NET Framework 4.6.2 ' deki Özellik geliştirmeleri ve hata düzeltmeleri listesi için bkz. GitHub 'da [değişiklikler listesi .NET Framework 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) .</span><span class="sxs-lookup"><span data-stu-id="66a64-497">For a list of feature improvements and bug fixes in .NET Framework 4.6.2, see [.NET Framework 4.6.2 List of Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) on GitHub.</span></span> <span data-ttu-id="66a64-498">Daha fazla bilgi için bkz. .NET blogda [.NET Framework 4.6.2 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) .</span><span class="sxs-lookup"><span data-stu-id="66a64-498">For more information, see [Announcing .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) in the .NET blog.</span></span>

<a name="ASPNET462"></a>

### <a name="aspnet"></a><span data-ttu-id="66a64-499">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66a64-499">ASP.NET</span></span>

<span data-ttu-id="66a64-500">.NET Framework 4.6.2, ASP.NET aşağıdaki geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-500">In  .NET Framework 4.6.2, ASP.NET includes the following enhancements:</span></span>

<span data-ttu-id="66a64-501">**Veri ek açıklama Doğrulayıcıları 'nda yerelleştirilmiş hata iletileri için geliştirilmiş destek**</span><span class="sxs-lookup"><span data-stu-id="66a64-501">**Improved support for localized error messages in data annotation validators**</span></span>

<span data-ttu-id="66a64-502">Veri ek açıklama Doğrulayıcıları bir sınıf özelliğine bir veya daha fazla öznitelik ekleyerek doğrulama gerçekleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-502">Data annotation validators enable you to perform validation by adding one or more attributes to a class property.</span></span> <span data-ttu-id="66a64-503">Özniteliğin öğesi, <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> doğrulama başarısız olursa hata iletisinin metnini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-503">The attribute's <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> element defines the text of the error message if validation fails.</span></span> <span data-ttu-id="66a64-504">.NET Framework 4.6.2 ile başlayarak, ASP.NET hata iletilerini yerelleştirmenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="66a64-504">Starting with .NET Framework 4.6.2, ASP.NET makes it easy to localize error messages.</span></span> <span data-ttu-id="66a64-505">Şu durumlarda hata iletileri yerelleştirilecektir:</span><span class="sxs-lookup"><span data-stu-id="66a64-505">Error messages will be localized if:</span></span>

1. <span data-ttu-id="66a64-506">, <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> Doğrulama özniteliğinde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-506">The <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> is provided in the validation attribute.</span></span>

2. <span data-ttu-id="66a64-507">Kaynak dosyası App_LocalResources klasöründe depolanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-507">The resource file is stored in the App_LocalResources folder.</span></span>

3. <span data-ttu-id="66a64-508">Yerelleştirilmiş kaynaklar dosyasının adı `DataAnnotation.Localization.{` *name* `}.resx` , *adı* *languageCode* `-` *Country/RegionCode* veya *languageCode* biçiminde bir kültür adı olduğunda, form adına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="66a64-508">The name of the localized resources file has the form `DataAnnotation.Localization.{`*name*`}.resx`, where *name* is a culture name in the format *languageCode*`-`*country/regionCode* or *languageCode*.</span></span>

4. <span data-ttu-id="66a64-509">Kaynağın anahtar adı özniteliğe atanan dizedir <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> ve değeri yerelleştirilmiş hata iletisidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-509">The key name of the resource is the string assigned to the <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> attribute,  and its value is the localized error message.</span></span>

<span data-ttu-id="66a64-510">Örneğin, aşağıdaki Data Annotation özniteliği geçersiz bir derecelendirme için varsayılan kültürün hata iletisini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-510">For example, the following data annotation attribute defines the default culture's error message for an invalid rating.</span></span>

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

<span data-ttu-id="66a64-511">Ardından, anahtar hata iletisi dizesi olan ve değeri yerelleştirilmiş hata iletisi olan DataAnnotation. yerelleştirme. fr. resx olan bir kaynak dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-511">You can then create a resource file, DataAnnotation.Localization.fr.resx, whose key is the error message string and whose value is the localized error message.</span></span> <span data-ttu-id="66a64-512">Dosyanın klasörde bulunması gerekir `App.LocalResources` .</span><span class="sxs-lookup"><span data-stu-id="66a64-512">The file must be found in the `App.LocalResources` folder.</span></span> <span data-ttu-id="66a64-513">Örneğin, aşağıdaki anahtar ve değeri yerelleştirilmiş Fransızca (fr) dil hata iletisinde verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="66a64-513">For example, the following is the key and its value in a localized French (fr) language error message:</span></span>

| <span data-ttu-id="66a64-514">Name</span><span class="sxs-lookup"><span data-stu-id="66a64-514">Name</span></span>                                 | <span data-ttu-id="66a64-515">Değer</span><span class="sxs-lookup"><span data-stu-id="66a64-515">Value</span></span>                                     |
| ------------------------------------ | ----------------------------------------- |
| <span data-ttu-id="66a64-516">Derecelendirme 1 ile 10 arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-516">The rating must be between 1 and 10.</span></span> | <span data-ttu-id="66a64-517">La Note DoIt être, diğer 1 et 10.</span><span class="sxs-lookup"><span data-stu-id="66a64-517">La note doit être comprise entre 1 et 10.</span></span> |

 <span data-ttu-id="66a64-518">Ayrıca, veri ek açıklaması yerelleştirme genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-518">In addition, data annotation localization is extensible.</span></span> <span data-ttu-id="66a64-519">Geliştiriciler, <xref:System.Web.Globalization.IStringLocalizerProvider> Yerelleştirme dizesini kaynak dosyasında dışında bir yerde depolamak için arabirimini uygulayarak kendi dize yerelleştirici sağlayıcısını ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-519">Developers can plug in their own string localizer provider by implementing the <xref:System.Web.Globalization.IStringLocalizerProvider> interface to store localization string somewhere other than in a resource file.</span></span>

 <span data-ttu-id="66a64-520">**Oturum durumu depo sağlayıcıları ile zaman uyumsuz destek**</span><span class="sxs-lookup"><span data-stu-id="66a64-520">**Async support with session-state store providers**</span></span>

 <span data-ttu-id="66a64-521">ASP.NET artık oturum durumu depolama sağlayıcılarıyla birlikte görev döndüren yöntemlerin kullanılmasına izin veriyor, böylece ASP.NET uygulamalarının zaman uyumsuz olarak ölçeklenebilirlik avantajlarını almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="66a64-521">ASP.NET now allows task-returning methods to be used with session-state store providers, thereby allowing ASP.NET apps to get the scalability benefits of async.</span></span> <span data-ttu-id="66a64-522">ASP.NET, oturum durumu depolama sağlayıcılarıyla zaman uyumsuz işlemleri desteklemek için, ' den devralan yeni bir arabirim içerir <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType> <xref:System.Web.IHttpModule> ve geliştiricilerin kendi oturum durumu modülünü ve zaman uyumsuz oturum depolama sağlayıcılarını uygulamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-522">To supports asynchronous operations with session state store providers, ASP.NET includes  a new interface, <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, which inherits from <xref:System.Web.IHttpModule> and allows developers to implement their own session-state module and async session store providers.</span></span> <span data-ttu-id="66a64-523">Arabirim aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="66a64-523">The interface is defined as follows:</span></span>

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

 <span data-ttu-id="66a64-524">Ayrıca, sınıfı, <xref:System.Web.SessionState.SessionStateUtility> <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A> zaman uyumsuz işlemleri desteklemek için kullanılabilen iki yeni yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-524">In addition, the <xref:System.Web.SessionState.SessionStateUtility> class includes two new methods, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> and <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, that can be used to support asynchronous operations.</span></span>

 <span data-ttu-id="66a64-525">**Çıkış önbelleği sağlayıcıları için zaman uyumsuz destek**</span><span class="sxs-lookup"><span data-stu-id="66a64-525">**Async support for output-cache providers**</span></span>

 <span data-ttu-id="66a64-526">.NET Framework 4.6.2 ile başlayarak, zaman uyumsuz olarak ölçeklenebilirlik avantajları sağlamak için, görev döndüren yöntemler çıkış önbelleği sağlayıcılarıyla birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-526">Starting with .NET Framework 4.6.2, task-returning methods can be used with output-cache providers to provide the scalability benefits of async.</span></span>  <span data-ttu-id="66a64-527">Bu yöntemleri uygulayan sağlayıcılar, bir Web sunucusundaki iş parçacığı engellemeyi azaltır ve bir ASP.NET hizmetinin ölçeklenebilirliğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-527">Providers that implement these methods reduce thread-blocking on a web server and improve the scalability of an ASP.NET service.</span></span>

 <span data-ttu-id="66a64-528">Zaman uyumsuz çıkış önbelleği sağlayıcılarını desteklemek için aşağıdaki API 'Ler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="66a64-528">The following APIs have been added to support asynchronous output-cache providers:</span></span>

- <span data-ttu-id="66a64-529"><xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType>' Den devralan <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> ve geliştiricilerin zaman uyumsuz çıkış önbelleği sağlayıcısı uygulamasına izin veren sınıfı.</span><span class="sxs-lookup"><span data-stu-id="66a64-529">The <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> class, which inherits from <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> and allows developers to implement an asynchronous output-cache provider.</span></span>

- <span data-ttu-id="66a64-530"><xref:System.Web.Caching.OutputCacheUtility>Çıktı önbelleğini yapılandırmak için yardımcı yöntemler sağlayan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="66a64-530">The <xref:System.Web.Caching.OutputCacheUtility> class, which provides helper methods for configuring the output cache.</span></span>

- <span data-ttu-id="66a64-531">, sınıfında 18 yeni yöntem <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-531">18 new methods in the <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="66a64-532">Bunlar,,,,, <xref:System.Web.HttpCachePolicy.GetCacheability%2A> <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A> <xref:System.Web.HttpCachePolicy.GetETag%2A> <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A> <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> , <xref:System.Web.HttpCachePolicy.GetNoStore%2A> , <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A> , <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A> , <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A> , <xref:System.Web.HttpCachePolicy.GetRevalidation%2A> , <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A> , <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A> , <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A> , ve içerir <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A> .</span><span class="sxs-lookup"><span data-stu-id="66a64-532">These include <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, and <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.</span></span>

- <span data-ttu-id="66a64-533">sınıfında 2 yeni yöntem <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> :  <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> ve <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A> .</span><span class="sxs-lookup"><span data-stu-id="66a64-533">2 new methods in the <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> class:  <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> and <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.</span></span>

- <span data-ttu-id="66a64-534">sınıfında 2 yeni yöntem <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> : <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> ve <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A> .</span><span class="sxs-lookup"><span data-stu-id="66a64-534">2 new methods in the <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> class: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> and <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.</span></span>

- <span data-ttu-id="66a64-535">sınıfında 2 yeni yöntem <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> : <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> ve <xref:System.Web.HttpCacheVaryByParams.SetParams%2A> .</span><span class="sxs-lookup"><span data-stu-id="66a64-535">2 new methods in the <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> class: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> and <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.</span></span>

- <span data-ttu-id="66a64-536"><xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType>Sınıfında, <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="66a64-536">In the <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> class, the <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> method.</span></span>

- <span data-ttu-id="66a64-537">İçinde <xref:System.Web.Caching.CacheDependency> , <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="66a64-537">In the <xref:System.Web.Caching.CacheDependency>, the <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> method.</span></span>

<a name="Strings"></a>

### <a name="character-categories"></a><span data-ttu-id="66a64-538">Karakter kategorileri</span><span class="sxs-lookup"><span data-stu-id="66a64-538">Character categories</span></span>

<span data-ttu-id="66a64-539">.NET Framework 4.6.2 içindeki karakterler [Unicode standardı, sürüm 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/)temel alınarak sınıflandırılır.</span><span class="sxs-lookup"><span data-stu-id="66a64-539">Characters in .NET Framework 4.6.2 are classified based on the [Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span></span> <span data-ttu-id="66a64-540">.NET Framework 4,6 ve .NET Framework 4.6.1, karakterler Unicode 6,3 karakter kategorilerine göre sınıflandırıldı.</span><span class="sxs-lookup"><span data-stu-id="66a64-540">In .NET Framework 4.6 and .NET Framework 4.6.1, characters were classified based on Unicode 6.3 character categories.</span></span>

<span data-ttu-id="66a64-541">Unicode 8,0 desteği, <xref:System.Globalization.CharUnicodeInfo> sınıf ve ona bağlı tür ve yöntemlere göre karakterlerin sınıflandırmasıyla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-541">Support for Unicode 8.0 is limited to the classification of characters by the <xref:System.Globalization.CharUnicodeInfo> class and to types and methods that rely on it.</span></span> <span data-ttu-id="66a64-542">Bunlar <xref:System.Globalization.StringInfo> sınıfı, aşırı yüklenmiş <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> yöntemi ve .NET Framework normal ifade altyapısı tarafından tanınan [karakter sınıflarını](../../standard/base-types/character-classes-in-regular-expressions.md) içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-542">These include the <xref:System.Globalization.StringInfo> class, the overloaded <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> method, and the [character classes](../../standard/base-types/character-classes-in-regular-expressions.md) recognized by the .NET Framework regular expression engine.</span></span>  <span data-ttu-id="66a64-543">Karakter ve dize karşılaştırma ve sıralama bu değişiklikten etkilenmez ve temel alınan işletim sistemine veya Windows 7 sistemlerinde, .NET Framework tarafından belirtilen karakter verilerinde kullanılmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="66a64-543">Character and string comparison and sorting is unaffected by this change and continues to rely on the underlying operating system or, on Windows 7 systems, on character data provided by .NET Framework.</span></span>

<span data-ttu-id="66a64-544">Unicode 6,0 ' den Unicode 7,0 ' e karakter kategorilerindeki değişiklikler için bkz. Unicode [Standart, sürüm 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) , Unicode konsorsiyum Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="66a64-544">For changes in character categories from Unicode 6.0 to Unicode 7.0, see [The Unicode Standard, Version 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) at The Unicode Consortium website.</span></span> <span data-ttu-id="66a64-545">Unicode 7,0 ' den Unicode 8,0 ' e yapılan değişiklikler için bkz. Unicode [Standart, sürüm 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) , Unicode konsorsiyum Web sitesi.</span><span class="sxs-lookup"><span data-stu-id="66a64-545">For changes from Unicode 7.0 to Unicode 8.0, see [The Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) at The Unicode Consortium website.</span></span>

<a name="Crypto462"></a>

### <a name="cryptography"></a><span data-ttu-id="66a64-546">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="66a64-546">Cryptography</span></span>

<span data-ttu-id="66a64-547">**FIPS 186-3 DSA içeren x509 sertifikaları desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-547">**Support for X509 certificates containing FIPS 186-3 DSA**</span></span>

<span data-ttu-id="66a64-548">.NET Framework 4.6.2, anahtarları FIPS 186-2 1024 bit sınırını aşan DSA (dijital Imza algoritması) x509 sertifikaları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-548">.NET Framework 4.6.2 adds support for DSA (Digital Signature Algorithm) X509 certificates whose keys exceed the FIPS 186-2 1024-bit limit.</span></span>

<span data-ttu-id="66a64-549">.NET Framework 4.6.2, FIPS 186-3 ' nin daha büyük anahtar boyutlarını desteklemeye ek olarak, karma algoritmaların SHA-2 ailesiyle (SHA256, SHA384 ve SHA512 olur) imzaları hesaplama olanağı tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-549">In addition to supporting the larger key sizes of FIPS 186-3, .NET Framework 4.6.2 allows computing signatures with the SHA-2 family of hash algorithms (SHA256, SHA384, and SHA512).</span></span> <span data-ttu-id="66a64-550">FIPS 186-3 desteği yeni sınıf tarafından sağlanmaktadır <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-550">FIPS 186-3 support is provided by the new <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="66a64-551">.NET Framework 4,6 ' deki ve .NET Framework 4.6.1 ' deki sınıf üzerinde yapılan son değişikliklerle birlikte <xref:System.Security.Cryptography.RSA> <xref:System.Security.Cryptography.ECDsa> , <xref:System.Security.Cryptography.DSA> .NET Framework 4.6.2 içindeki soyut temel sınıf, çağıranların atama olmadan bu işlevselliği kullanmasına izin vermek için ek yöntemlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="66a64-551">In keeping with recent changes to the <xref:System.Security.Cryptography.RSA> class in .NET Framework 4.6 and the <xref:System.Security.Cryptography.ECDsa> class in .NET Framework 4.6.1, the <xref:System.Security.Cryptography.DSA> abstract base class in .NET Framework 4.6.2 has additional methods to allow callers to use this functionality without casting.</span></span> <span data-ttu-id="66a64-552"><xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, verileri imzalamak için uzantı yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-552">You can call the <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> extension method to sign data, as the following example shows.</span></span>

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

<span data-ttu-id="66a64-553">Ve <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi imzalı verileri doğrulamak için genişletme yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-553">And you can call the <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> extension method to verify signed data, as the following example shows.</span></span>

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

<span data-ttu-id="66a64-554">**Ecdıfıehellman anahtar türetme yordamlarına yönelik girişler için daha fazla açıklık**</span><span class="sxs-lookup"><span data-stu-id="66a64-554">**Increased clarity for inputs to ECDiffieHellman key derivation routines**</span></span>

<span data-ttu-id="66a64-555">.NET Framework 3,5, eliptik eğri Diffie-Hellman üç farklı anahtar türetme Işlevi (KDF) yordamlarına sahip anahtar anlaşması için destek ekledi.</span><span class="sxs-lookup"><span data-stu-id="66a64-555">.NET Framework 3.5 added support for Elliptic Curve Diffie-Hellman Key Agreement with three different Key Derivation Function (KDF) routines.</span></span> <span data-ttu-id="66a64-556">Yordamlarına yapılan girişler ve yordamlar, nesne üzerindeki özellikler aracılığıyla yapılandırılmıştır <xref:System.Security.Cryptography.ECDiffieHellmanCng> .</span><span class="sxs-lookup"><span data-stu-id="66a64-556">The inputs to the routines, and the routines themselves, were configured via properties on the <xref:System.Security.Cryptography.ECDiffieHellmanCng> object.</span></span> <span data-ttu-id="66a64-557">Ancak her bir yordam her giriş özelliğini okumadığından, geliştiricinin geçmişte karışıklık için çok fazla yer vardır.</span><span class="sxs-lookup"><span data-stu-id="66a64-557">But since not every routine read every input property, there was ample room for confusion on the past of the developer.</span></span>

<span data-ttu-id="66a64-558">.NET Framework 4.6.2 ' de bunu ele almak için temel sınıfa aşağıdaki üç yöntem eklenmiştir  <xref:System.Security.Cryptography.ECDiffieHellman> ve bu KDF yordamlarını ve bunların girişlerini daha net bir şekilde temsil eder:</span><span class="sxs-lookup"><span data-stu-id="66a64-558">To address this in .NET Framework 4.6.2, the following three methods have been added to the  <xref:System.Security.Cryptography.ECDiffieHellman> base class to more clearly represent these KDF routines and their inputs:</span></span>

|<span data-ttu-id="66a64-559">Ecdıfıfiehellman yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a64-559">ECDiffieHellman method</span></span>|<span data-ttu-id="66a64-560">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66a64-560">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="66a64-561">Formülü kullanarak önemli malzemeleri türetiliyor</span><span class="sxs-lookup"><span data-stu-id="66a64-561">Derives key material using the formula</span></span><br /><br /> <span data-ttu-id="66a64-562">Karma (secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span><span class="sxs-lookup"><span data-stu-id="66a64-562">HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span></span><br /><br /> <span data-ttu-id="66a64-563">Karma (secretPrepend Orelo *x* Orelo secretAppend)</span><span class="sxs-lookup"><span data-stu-id="66a64-563">HASH(secretPrepend OrElse *x* OrElse secretAppend)</span></span><br /><br /> <span data-ttu-id="66a64-564">Burada *x* , EC Diffie-Hellman algoritmasının hesaplanan sonucudur.</span><span class="sxs-lookup"><span data-stu-id="66a64-564">where *x* is the computed result of the EC Diffie-Hellman algorithm.</span></span>|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="66a64-565">Formülü kullanarak önemli malzemeleri türetiliyor</span><span class="sxs-lookup"><span data-stu-id="66a64-565">Derives key material using the formula</span></span><br /><br /> <span data-ttu-id="66a64-566">HMAC (hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span><span class="sxs-lookup"><span data-stu-id="66a64-566">HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span></span><br /><br /> <span data-ttu-id="66a64-567">HMAC (hmacKey, secretPrepend Orelo *x* Orellsecretappend)</span><span class="sxs-lookup"><span data-stu-id="66a64-567">HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)</span></span><br /><br /> <span data-ttu-id="66a64-568">Burada *x* , EC Diffie-Hellman algoritmasının hesaplanan sonucudur.</span><span class="sxs-lookup"><span data-stu-id="66a64-568">where *x* is the computed result of the EC Diffie-Hellman algorithm.</span></span>|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="66a64-569">TLS sözde rastgele işlevi (PRF) türetme algoritmasını kullanarak önemli malzemeleri türetiliyor.</span><span class="sxs-lookup"><span data-stu-id="66a64-569">Derives key material using the TLS pseudo-random function (PRF) derivation algorithm.</span></span>|

<span data-ttu-id="66a64-570">**Kalıcı anahtar simetrik şifreleme desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-570">**Support for persisted-key symmetric encryption**</span></span>

<span data-ttu-id="66a64-571">Windows şifreleme kitaplığı (CNG), kalıcı simetrik anahtarları depolama ve donanımla depolanan simetrik anahtarları kullanma desteği eklendi ve geliştiricilerin bu özelliği kullanmasını olanaklı hale 4.6.2 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66a64-571">The Windows cryptography library (CNG) added support for storing persisted symmetric keys and using hardware-stored symmetric keys, and .NET Framework 4.6.2 made it possible for developers to make use of this feature.</span></span>  <span data-ttu-id="66a64-572">Anahtar adları ve anahtar sağlayıcılarının kavramı uygulamaya özgü olduğundan, bu özelliğin kullanılması tercih edilen fabrika yaklaşımı (çağırma gibi) yerine somut uygulama türleri oluşturucusunun kullanılmasını gerektirir `Aes.Create` .</span><span class="sxs-lookup"><span data-stu-id="66a64-572">Since the notion of key names and key providers is implementation-specific, using this feature requires utilizing the constructor of the concrete implementation types instead of the preferred factory approach (such as calling `Aes.Create`).</span></span>

<span data-ttu-id="66a64-573">AES ( <xref:System.Security.Cryptography.AesCng> ) ve 3DES () algoritmaları için kalıcı anahtar simetrik şifreleme desteği var <xref:System.Security.Cryptography.TripleDESCng> .</span><span class="sxs-lookup"><span data-stu-id="66a64-573">Persisted-key symmetric encryption support exists for the AES (<xref:System.Security.Cryptography.AesCng>) and 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algorithms.</span></span> <span data-ttu-id="66a64-574">Örnek:</span><span class="sxs-lookup"><span data-stu-id="66a64-574">For example:</span></span>

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
                throw new InvalidOperationException("This is a sample, this case wasn't handled...");
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
                Throw New InvalidOperationException("This is a sample, this case wasn't handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

<span data-ttu-id="66a64-575">**SHA-2 karma için SignedXml desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-575">**SignedXml support for SHA-2 hashing**</span></span>

<span data-ttu-id="66a64-576">.NET Framework 4.6.2, <xref:System.Security.Cryptography.Xml.SignedXml> RSA-SHA256, RSA-SHA384 ve RSA-SHA512 olur PKCS # 1 imza yöntemlerine ve SHA256, SHA384 ve SHA512 olur başvuru Özet algoritmalarına yönelik destek ekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-576">.NET Framework 4.6.2 adds support to  the <xref:System.Security.Cryptography.Xml.SignedXml> class for RSA-SHA256, RSA-SHA384, and RSA-SHA512 PKCS#1 signature methods, and SHA256, SHA384, and SHA512 reference digest algorithms.</span></span>

<span data-ttu-id="66a64-577">URI sabitlerinin tümü üzerine açıktır <xref:System.Security.Cryptography.Xml.SignedXml> :</span><span class="sxs-lookup"><span data-stu-id="66a64-577">The URI constants are all exposed on <xref:System.Security.Cryptography.Xml.SignedXml>:</span></span>

|<span data-ttu-id="66a64-578">SignedXml alanı</span><span class="sxs-lookup"><span data-stu-id="66a64-578">SignedXml field</span></span>|<span data-ttu-id="66a64-579">Sabit</span><span class="sxs-lookup"><span data-stu-id="66a64-579">Constant</span></span>|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|<span data-ttu-id="66a64-580">"http://www.w3.org/2001/04/xmlenc#sha256"</span><span class="sxs-lookup"><span data-stu-id="66a64-580">"http://www.w3.org/2001/04/xmlenc#sha256"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|<span data-ttu-id="66a64-581">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"</span><span class="sxs-lookup"><span data-stu-id="66a64-581">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|<span data-ttu-id="66a64-582">"http://www.w3.org/2001/04/xmldsig-more#sha384"</span><span class="sxs-lookup"><span data-stu-id="66a64-582">"http://www.w3.org/2001/04/xmldsig-more#sha384"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|<span data-ttu-id="66a64-583">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"</span><span class="sxs-lookup"><span data-stu-id="66a64-583">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|<span data-ttu-id="66a64-584">"http://www.w3.org/2001/04/xmlenc#sha512"</span><span class="sxs-lookup"><span data-stu-id="66a64-584">"http://www.w3.org/2001/04/xmlenc#sha512"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|<span data-ttu-id="66a64-585">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"</span><span class="sxs-lookup"><span data-stu-id="66a64-585">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"</span></span>|

 <span data-ttu-id="66a64-586"><xref:System.Security.Cryptography.SignatureDescription> <xref:System.Security.Cryptography.CryptoConfig> Bu algoritmalara yönelik destek eklemek için özel bir işleyici kaydetmiş olan programlar geçmişte olduğu gibi çalışmaya devam eder, ancak artık platform Varsayılanları olduğundan, <xref:System.Security.Cryptography.CryptoConfig> kayıt artık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="66a64-586">Any programs that have registered a custom <xref:System.Security.Cryptography.SignatureDescription> handler into <xref:System.Security.Cryptography.CryptoConfig> to add support for these algorithms will continue to function as they did in the past, but since there are now platform defaults, the <xref:System.Security.Cryptography.CryptoConfig> registration is no longer necessary.</span></span>

<a name="SQLClient"></a>

### <a name="sqlclient"></a><span data-ttu-id="66a64-587">SqlClient</span><span class="sxs-lookup"><span data-stu-id="66a64-587">SqlClient</span></span>

<span data-ttu-id="66a64-588">SQL Server () için .NET Framework Veri Sağlayıcısı <xref:System.Data.SqlClient?displayProperty=nameWithType> , .NET Framework 4.6.2 ' de aşağıdaki yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-588">.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) includes the following new features in .NET Framework 4.6.2:</span></span>

<span data-ttu-id="66a64-589">**Azure SQL veritabanları ile bağlantı havuzu oluşturma ve zaman aşımları**</span><span class="sxs-lookup"><span data-stu-id="66a64-589">**Connection pooling and timeouts with Azure SQL databases**</span></span>

<span data-ttu-id="66a64-590">Bağlantı havuzu etkinleştirildiğinde ve bir zaman aşımı ya da başka bir oturum açma hatası oluştuğunda, bir özel durum önbelleğe alınır ve sonraki 5 saniye 1 dakikaya kadar sonraki bağlantı denemelerde önbelleğe alınan özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="66a64-590">When connection pooling is enabled and a timeout or other login error occurs, an exception is cached, and the cached exception is thrown on any subsequent connection attempt for the next 5 seconds to 1 minute.</span></span> <span data-ttu-id="66a64-591">Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-591">For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span>

<span data-ttu-id="66a64-592">Bağlantı girişimleri genellikle hızla kurtarılan geçici hatalarla başarısız olduğundan, bu davranış Azure SQL veritabanlarına bağlanırken istenmez.</span><span class="sxs-lookup"><span data-stu-id="66a64-592">This behavior is not desirable when connecting to Azure SQL Databases, since connection attempts can fail with transient errors that are typically recovered quickly.</span></span> <span data-ttu-id="66a64-593">Bağlantı yeniden deneme deneyimini daha iyi en iyi hale getirebilmesi için, Azure SQL veritabanlarına bağlantı başarısız olduğunda bağlantı havuzu engelleme süresi davranışı kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="66a64-593">To better optimize the connection retry experience, the connection pool blocking period behavior is removed when connections to Azure SQL Databases fail.</span></span>

<span data-ttu-id="66a64-594">Yeni anahtar sözcüğünün eklenmesi, `PoolBlockingPeriod` uygulamanız için en uygun engelleme dönemini seçmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-594">The addition of the new `PoolBlockingPeriod` keyword lets you select the blocking period best suited for your app.</span></span> <span data-ttu-id="66a64-595">Değerlere şunlar dahildir:</span><span class="sxs-lookup"><span data-stu-id="66a64-595">Values include:</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

<span data-ttu-id="66a64-596">Azure SQL veritabanına bağlanan bir uygulama için bağlantı havuzu engelleme süresi devre dışıdır ve başka bir SQL Server örneğine bağlanan bir uygulama için bağlantı havuzu engelleme süresi etkindir.</span><span class="sxs-lookup"><span data-stu-id="66a64-596">The connection pool blocking period for an application that connects to an Azure SQL Database is disabled, and the connection pool blocking period for an application that connects to any other SQL Server instance is enabled.</span></span> <span data-ttu-id="66a64-597">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="66a64-597">This is the default value.</span></span> <span data-ttu-id="66a64-598">Sunucu uç noktası adı aşağıdakilerden biriyle sonlanıyorsa, Azure SQL veritabanı olarak kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="66a64-598">If the Server endpoint name ends with any of the following, they are considered Azure SQL Databases:</span></span>

- <span data-ttu-id="66a64-599">. database.windows.net</span><span class="sxs-lookup"><span data-stu-id="66a64-599">.database.windows.net</span></span>

- <span data-ttu-id="66a64-600">. database.chinacloudapi.cn</span><span class="sxs-lookup"><span data-stu-id="66a64-600">.database.chinacloudapi.cn</span></span>

- <span data-ttu-id="66a64-601">. database.usgovcloudapi.net</span><span class="sxs-lookup"><span data-stu-id="66a64-601">.database.usgovcloudapi.net</span></span>

- <span data-ttu-id="66a64-602">. database.cloudapi.de</span><span class="sxs-lookup"><span data-stu-id="66a64-602">.database.cloudapi.de</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

<span data-ttu-id="66a64-603">Bağlantı havuzu engelleme dönemi her zaman etkindir.</span><span class="sxs-lookup"><span data-stu-id="66a64-603">The connection pool blocking period is always enabled.</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

<span data-ttu-id="66a64-604">Bağlantı havuzu engelleme süresi her zaman devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-604">The connection pool blocking period is always disabled.</span></span>

<span data-ttu-id="66a64-605">**Always Encrypted geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="66a64-605">**Enhancements for Always Encrypted**</span></span>

<span data-ttu-id="66a64-606">SQLClient Always Encrypted için iki geliştirme sunar:</span><span class="sxs-lookup"><span data-stu-id="66a64-606">SQLClient introduces two enhancements for Always Encrypted:</span></span>

- <span data-ttu-id="66a64-607">Şifrelenmiş veritabanı sütunlarına karşı parametreli sorguların performansını artırmak için, sorgu parametrelerinin şifreleme meta verileri artık önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="66a64-607">To improve performance of parameterized queries against encrypted database columns, encryption metadata for query parameters is now cached.</span></span> <span data-ttu-id="66a64-608"><xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType>Özelliği olarak ayarlanmış `true` (varsayılan değer olan), aynı sorgu birden çok kez çağrılırsa, istemci parametre meta verilerini sunucudan yalnızca bir kez alır.</span><span class="sxs-lookup"><span data-stu-id="66a64-608">With the <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> property set to `true` (which is the default value), if the same query is called multiple times, the client retrieves parameter metadata from the server only once.</span></span>

- <span data-ttu-id="66a64-609">Anahtar önbelleğindeki sütun şifreleme anahtarı girdileri artık yapılandırılabilir bir zaman aralığından sonra çıkarıldıktan sonra özelliği kullanılarak ayarlanır <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-609">Column encryption key entries in the key cache are now evicted after a configurable time interval, set using the <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> property.</span></span>

<a name="WCF"></a>

### <a name="windows-communication-foundation"></a><span data-ttu-id="66a64-610">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="66a64-610">Windows Communication Foundation</span></span>

<span data-ttu-id="66a64-611">.NET Framework 4.6.2 ' de, aşağıdaki alanlarda Windows Communication Foundation geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="66a64-611">In .NET Framework 4.6.2, Windows Communication Foundation has been enhanced in the following areas:</span></span>

<span data-ttu-id="66a64-612">**CNG kullanılarak depolanan sertifikalar için WCF Aktarım güvenliği desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-612">**WCF transport security support for certificates stored using CNG**</span></span>

<span data-ttu-id="66a64-613">WCF Aktarım güvenliği, Windows şifreleme kitaplığı (CNG) kullanılarak depolanan sertifikaları destekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-613">WCF transport security supports certificates stored using the Windows cryptography library (CNG).</span></span> <span data-ttu-id="66a64-614">.NET Framework 4.6.2, bu destek, en fazla 32 bit uzunluğunda olmayan bir ortak anahtarla sertifikaların kullanılmasıyla sınırlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="66a64-614">In .NET Framework 4.6.2, this support is limited to using certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="66a64-615">Bir uygulama .NET Framework 4.6.2 hedefliyorsa, bu özellik varsayılan olarak açık olur.</span><span class="sxs-lookup"><span data-stu-id="66a64-615">When an application targets .NET Framework 4.6.2, this feature is on by default.</span></span>

<span data-ttu-id="66a64-616">.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 üzerinde çalışan uygulamalar için, bu özellik, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) app.config veya web.config dosyanın bölümüne aşağıdaki satırı eklenerek etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-616">For applications that target .NET Framework 4.6.1 and earlier but are running on .NET Framework 4.6.2, this feature can be enabled by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app.config or web.config file.</span></span>

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

<span data-ttu-id="66a64-617">Bu, aşağıdakiler gibi kodla programlı olarak da yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="66a64-617">This can also be done programmatically with code like the following:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="66a64-618">**DataContractJsonSerializer sınıfına göre birden çok gün ışığından yararlanma zaman ayarlama kuralı için daha iyi destek**</span><span class="sxs-lookup"><span data-stu-id="66a64-618">**Better support for multiple daylight saving time adjustment rules by the DataContractJsonSerializer class**</span></span>

<span data-ttu-id="66a64-619">Müşteriler, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sınıfın tek bir saat dilimi için birden çok ayarlama kuralını destekleyip desteklemediğini tespit etmek için bir uygulama yapılandırma ayarı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-619">Customers can use an application configuration setting to determine whether the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> class supports multiple adjustment rules for a single time zone.</span></span> <span data-ttu-id="66a64-620">Bu bir katılım özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-620">This is an opt-in feature.</span></span> <span data-ttu-id="66a64-621">Etkinleştirmek için app.config dosyanıza aşağıdaki ayarı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="66a64-621">To enable it, add the following setting to your app.config file:</span></span>

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

<span data-ttu-id="66a64-622">Bu özellik etkinleştirildiğinde bir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nesne, <xref:System.TimeZoneInfo> <xref:System.TimeZone> Tarih ve saat verilerinin serisini kaldırmak için türü yerine türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-622">When this feature is enabled, a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object uses the <xref:System.TimeZoneInfo> type instead of the <xref:System.TimeZone> type to deserialize date and time data.</span></span> <span data-ttu-id="66a64-623"><xref:System.TimeZoneInfo> , geçmişteki saat dilimi verileriyle çalışmayı olanaklı kılan birden çok ayarlama kuralını destekler;   <xref:System.TimeZone> değildir.</span><span class="sxs-lookup"><span data-stu-id="66a64-623"><xref:System.TimeZoneInfo> supports multiple adjustment rules, which makes it possible to work with historic time zone data;   <xref:System.TimeZone> does not.</span></span>

<span data-ttu-id="66a64-624"><xref:System.TimeZoneInfo>Yapı ve saat dilimi ayarlamaları hakkında daha fazla bilgi için bkz. [saat dilimine genel bakış](../../standard/datetime/time-zone-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-624">For more information on the <xref:System.TimeZoneInfo> structure and time zone adjustments, see [Time Zone Overview](../../standard/datetime/time-zone-overview.md).</span></span>

<span data-ttu-id="66a64-625">**NetNamedPipeBinding en iyi eşleşme**</span><span class="sxs-lookup"><span data-stu-id="66a64-625">**NetNamedPipeBinding best match**</span></span>

<span data-ttu-id="66a64-626">WCF, istemci uygulamalarında, istedikleri uygulamayla en iyi şekilde eşleşen URI 'yi dinleyen hizmete her zaman bağlanabildiğini sağlayan yeni bir uygulama ayarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="66a64-626">WCF has a new app setting that can be set on client applications to ensure they always connect to the service listening on the URI that best matches the one that they request.</span></span> <span data-ttu-id="66a64-627">Bu uygulama ayarı `false` (varsayılan) olarak ayarlandığında, kullanan istemciler, <xref:System.ServiceModel.NetNamedPipeBinding> istenen URI 'nin bir alt dizesi olan bir URI üzerinde dinleme yapan bir hizmete bağlanmayı denemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="66a64-627">With this app setting set to `false` (the default), it is possible for clients using <xref:System.ServiceModel.NetNamedPipeBinding> to attempt to connect to a service listening on a URI that is a substring of the requested URI.</span></span>

<span data-ttu-id="66a64-628">Örneğin, bir istemci ' de dinleme yapan bir hizmete bağlanmaya çalışır `net.pipe://localhost/Service1` , ancak bu makinede yönetici ayrıcalığıyla çalışan farklı bir hizmet dinlemektedir `net.pipe://localhost` .</span><span class="sxs-lookup"><span data-stu-id="66a64-628">For example, a client tries to connect to a service listening at `net.pipe://localhost/Service1`, but a different service on that machine running with administrator privilege is listening at `net.pipe://localhost`.</span></span> <span data-ttu-id="66a64-629">Bu uygulama ayarı olarak ayarlandığında `false` , istemci yanlış hizmete bağlanmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="66a64-629">With this app setting set to `false`, the client would attempt to connect to the wrong service.</span></span> <span data-ttu-id="66a64-630">Uygulama ayarı olarak ayarlandıktan sonra `true` istemci her zaman en iyi eşleşen hizmete bağlanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-630">After setting the app setting to `true`, the client will always connect to the best matching service.</span></span>

> [!NOTE]
> <span data-ttu-id="66a64-631">İstemci, <xref:System.ServiceModel.NetNamedPipeBinding> tam bitiş noktası adresi yerine hizmetin temel adresine (varsa) göre bulma hizmetlerini kullanan istemcilerdir.</span><span class="sxs-lookup"><span data-stu-id="66a64-631">Clients using <xref:System.ServiceModel.NetNamedPipeBinding> find services based on the service's base address (if it exists) rather than the full endpoint address.</span></span> <span data-ttu-id="66a64-632">Bu ayarın her zaman çalıştığından emin olmak için, hizmetin benzersiz bir temel adres kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="66a64-632">To ensure this setting always works the service should use a unique base address.</span></span>

<span data-ttu-id="66a64-633">Bu değişikliği etkinleştirmek için, istemci uygulamanızın App.config veya Web.config dosyasına aşağıdaki uygulama ayarını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="66a64-633">To enable this change, add the following app setting to your client application's App.config or Web.config file:</span></span>

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="66a64-634">**SSL 3,0 varsayılan bir protokol değil**</span><span class="sxs-lookup"><span data-stu-id="66a64-634">**SSL 3.0 is not a default protocol**</span></span>

<span data-ttu-id="66a64-635">SSL 3,0, aktarım güvenliği ile NetTcp kullanırken güvenli bir bağlantı anlaşması için kullanılan varsayılan protokol değildir.</span><span class="sxs-lookup"><span data-stu-id="66a64-635">When using NetTcp with transport security and a credential type of certificate, SSL 3.0 is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="66a64-636">Çoğu durumda, TLS 1,0, NetTcp protokol listesine eklendiğinden, var olan uygulamalara hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="66a64-636">In most cases, there should be no impact to existing apps, because TLS 1.0 is included in the protocol list for NetTcp.</span></span> <span data-ttu-id="66a64-637">Tüm mevcut istemciler, en az TLS 1,0 kullanarak bir bağlantı anlaşması yapabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-637">All existing clients should be able to negotiate a connection using at least TLS 1.0.</span></span> <span data-ttu-id="66a64-638">Ssl3 gerekliyse, anlaşmalı protokoller listesine eklemek için aşağıdaki yapılandırma mekanizmalarından birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="66a64-638">If Ssl3 is required, use one of the following configuration mechanisms to add it to the list of negotiated protocols.</span></span>

- <span data-ttu-id="66a64-639"><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType>Özelliği</span><span class="sxs-lookup"><span data-stu-id="66a64-639">The <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> property</span></span>

- <span data-ttu-id="66a64-640"><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType>Özelliği</span><span class="sxs-lookup"><span data-stu-id="66a64-640">The <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property</span></span>

- <span data-ttu-id="66a64-641">[\<transport>](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md) Bölümünün bölümü</span><span class="sxs-lookup"><span data-stu-id="66a64-641">The [\<transport>](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) section of the [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md) section</span></span>

- <span data-ttu-id="66a64-642">[\<sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md) [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) Bölümünün bölümü</span><span class="sxs-lookup"><span data-stu-id="66a64-642">The [\<sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md) section of the [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) section</span></span>

<a name="WPF462"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="66a64-643">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="66a64-643">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="66a64-644">.NET Framework 4.6.2 ' de, aşağıdaki alanlarda Windows Presentation Foundation geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="66a64-644">In .NET Framework 4.6.2, Windows Presentation Foundation has been enhanced in the following areas:</span></span>

<span data-ttu-id="66a64-645">**Grup sıralaması**</span><span class="sxs-lookup"><span data-stu-id="66a64-645">**Group sorting**</span></span>

<span data-ttu-id="66a64-646"><xref:System.Windows.Data.CollectionView>Verileri gruplamak için bir nesne kullanan bir uygulama artık grupların nasıl sıralanacağını açıkça bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-646">An application that uses a <xref:System.Windows.Data.CollectionView> object to group data can now explicitly declare how to  sort the groups.</span></span> <span data-ttu-id="66a64-647">Açık sıralama, bir uygulama grupları dinamik olarak eklediğinde ya da kaldırırken veya gruplandırmada yer alan öğe özelliklerinin değerini değiştirdiğinde oluşan sezgisel olmayan sıralama sorununa yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="66a64-647">Explicit sorting addresses the problem of non-intuitive ordering that occurs when an app dynamically adds or removes groups, or when it changes the value of item properties involved in grouping.</span></span> <span data-ttu-id="66a64-648">Ayrıca, gruplama özelliklerinin karşılaştırmalarını tam koleksiyonun sıralamasını grupların sıralaması olarak taşıyarak Grup oluşturma işleminin performansını da artırır.</span><span class="sxs-lookup"><span data-stu-id="66a64-648">It can also improve the performance of the group creation process by moving comparisons of the grouping properties from the sort of the full collection to the sort of the groups.</span></span>

<span data-ttu-id="66a64-649">Grup sıralamasını desteklemek için, New <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> ve <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> Properties, nesne tarafından üretilen grupların koleksiyonunun nasıl sıralanacağını anlatmaktadır <xref:System.ComponentModel.GroupDescription> .</span><span class="sxs-lookup"><span data-stu-id="66a64-649">To support group sorting, the new <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> and <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> properties describe how to sort the collection of groups produced by the <xref:System.ComponentModel.GroupDescription> object.</span></span> <span data-ttu-id="66a64-650">Bu, aynı adlı <xref:System.Windows.Data.ListCollectionView> özelliklerin veri öğelerinin nasıl sıralanacağını betimleyen yönteme benzerdir.</span><span class="sxs-lookup"><span data-stu-id="66a64-650">This is analogous to the way the identically named <xref:System.Windows.Data.ListCollectionView> properties describe how to sort the data items.</span></span>

<span data-ttu-id="66a64-651">Sınıfının iki yeni statik özelliği <xref:System.Windows.Data.PropertyGroupDescription>  <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> ve <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A> en sık karşılaşılan durumlar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-651">Two new static properties of the <xref:System.Windows.Data.PropertyGroupDescription> class,  <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> and <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, can be used for the most common cases.</span></span>

<span data-ttu-id="66a64-652">Örneğin, aşağıdaki XAML verileri yaş ile gruplandırır, yaş gruplarını artan düzende sıralar ve her yaş grubundaki öğeleri son ada göre gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="66a64-652">For example, the following XAML groups data by age, sort the age groups in ascending order, and group the items within each age group by last name.</span></span>

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

<span data-ttu-id="66a64-653">**Dokunmatik klavye desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-653">**Touch keyboard support**</span></span>

<span data-ttu-id="66a64-654">Dokunmatik klavye desteği, dokunma girişi metin girişi yapan bir denetim tarafından alındığında, Windows 10 ' da dokunmatik klavyeyi otomatik olarak çağırarak ve yok ederek, WPF uygulamalarında odak izlemeye izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-654">Touch keyboard support enables focus tracking in WPF applications by automatically invoking and dismissing the touch Keyboard in Windows 10 when the touch input is received by a control that can take textual input.</span></span>

<span data-ttu-id="66a64-655">.NET Framework önceki sürümlerinde, WPF uygulamaları WPF kalem/dokunma hareketi desteğini devre dışı bırakmadan odak izlemeyi kabul edemiyor.</span><span class="sxs-lookup"><span data-stu-id="66a64-655">In previous versions of .NET Framework, WPF applications can't opt into the focus tracking without disabling WPF pen/touch gesture support.</span></span> <span data-ttu-id="66a64-656">Sonuç olarak, WPF uygulamalarının tam WPF dokunma desteği arasında seçim yapmanız veya Windows fare yükseltmesine güvenmelidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-656">As a result, WPF applications must choose between full WPF touch support or rely on Windows mouse promotion.</span></span>

<span data-ttu-id="66a64-657">**Monitör başına DPı**</span><span class="sxs-lookup"><span data-stu-id="66a64-657">**Per-monitor DPI**</span></span>

<span data-ttu-id="66a64-658">WPF uygulamaları için yüksek DPı ve hibrit DPı ortamlarının en son kullanımını desteklemek için, .NET Framework 4.6.2 ' deki WPF, izleme başına tanımayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-658">To support the recent proliferation of high-DPI and hybrid-DPI environments for WPF apps, WPF in .NET Framework 4.6.2 enables per-monitor awareness.</span></span> <span data-ttu-id="66a64-659">WPF uygulamanızın monitör başına DPı kullanan bir duruma gelmesini sağlama hakkında daha fazla bilgi için bkz. GitHub 'da [örnekler ve Geliştirici Kılavuzu](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) .</span><span class="sxs-lookup"><span data-stu-id="66a64-659">See the [samples and developer guide](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) on GitHub for more information about how to enable your WPF app to become per-monitor DPI aware.</span></span>

<span data-ttu-id="66a64-660">.NET Framework önceki sürümlerinde, WPF uygulamaları sistem DPı özellikli.</span><span class="sxs-lookup"><span data-stu-id="66a64-660">In previous versions of .NET Framework, WPF apps are system-DPI aware.</span></span> <span data-ttu-id="66a64-661">Diğer bir deyişle, uygulamanın kullanıcı arabirimi, uygulamanın işlendiği izleyicinin DPı değerine bağlı olarak, işletim sistemi tarafından uygun şekilde ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-661">In other words, the application's UI is scaled by the OS as appropriate, depending on the DPI of the monitor on which the app is rendered.</span></span>

<span data-ttu-id="66a64-662">.NET Framework 4.6.2 altında çalışan uygulamalar için, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) aşağıdaki gibi, uygulama yapılandırma dosyanızın bölümüne bir yapılandırma açıklaması ekleyerek WPF uygulamalarında monitör BAŞıNA DPI değişikliklerini devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66a64-662">For apps running under .NET Framework 4.6.2, you can disable per-monitor DPI changes in WPF apps by adding a configuration statement to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file, as follows:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462"></a>

### <a name="windows-workflow-foundation-wf"></a><span data-ttu-id="66a64-663">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="66a64-663">Windows Workflow Foundation (WF)</span></span>

<span data-ttu-id="66a64-664">.NET Framework 4.6.2 ' de, aşağıdaki alanda Windows Workflow Foundation geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="66a64-664">In .NET Framework 4.6.2, Windows Workflow Foundation has been enhanced in the following area:</span></span>

<span data-ttu-id="66a64-665">**Yeniden barındırılan WF tasarımcısında C# ifadeleri ve IntelliSense desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-665">**Support for C# expressions and IntelliSense in the Rehosted WF Designer**</span></span>

<span data-ttu-id="66a64-666">WF .NET Framework 4,5 ' den başlayarak hem Visual Studio tasarımcısında hem de kod iş akışlarında C# ifadelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-666">Starting with .NET Framework 4.5, WF supports C# expressions in both the Visual Studio Designer and in code workflows.</span></span> <span data-ttu-id="66a64-667">Yeniden barındırılan İş Akışı Tasarımcısı, bir WF 'nin Visual Studio dışında bir uygulamada olmasını İş Akışı Tasarımcısı sağlayan bir temel özelliktir (örneğin, WPF).</span><span class="sxs-lookup"><span data-stu-id="66a64-667">The Rehosted Workflow Designer is a key feature of WF that allows for the Workflow Designer to be in an application outside Visual Studio (for example, in WPF).</span></span>  <span data-ttu-id="66a64-668">Windows Workflow Foundation, yeniden barındırılan İş Akışı Tasarımcısı C# ifadelerini ve IntelliSense 'i destekleme yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-668">Windows Workflow Foundation provides the ability to support C# expressions and IntelliSense in the Rehosted Workflow Designer.</span></span> <span data-ttu-id="66a64-669">Daha fazla bilgi için [Windows Workflow Foundation bloguna](/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer)bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-669">For more information, see the [Windows Workflow Foundation blog](/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer).</span></span>

<span data-ttu-id="66a64-670">`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` 4.6.2 ' den önceki .NET Framework sürümlerinde, bir müşteri, Visual Studio 'dan bir iş akışı projesi yeniden oluştururken WF Tasarımcısı IntelliSense bozulur.</span><span class="sxs-lookup"><span data-stu-id="66a64-670">`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` In versions of the .NET Framework prior to 4.6.2, WF Designer IntelliSense is broken when a customer rebuilds a workflow project from Visual Studio.</span></span> <span data-ttu-id="66a64-671">Proje derlemesi başarılı olsa da, iş akışı türleri tasarımcıda bulunmadı ve eksik iş akışı türleri için IntelliSense uyarıları **hata listesi** penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="66a64-671">While the project build is successful, the workflow types are not found on the designer, and warnings from IntelliSense for the missing workflow types appear in the **Error List** window.</span></span> <span data-ttu-id="66a64-672">.NET Framework 4.6.2 Bu sorunu giderir ve IntelliSense 'i kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-672">.NET Framework 4.6.2 addresses this issue and makes IntelliSense available.</span></span>

<span data-ttu-id="66a64-673">**İş akışı Izleme olan iş akışı v1 uygulamaları artık FIPS modunda çalıştırılır**</span><span class="sxs-lookup"><span data-stu-id="66a64-673">**Workflow V1 applications with Workflow Tracking on now run under FIPS-mode**</span></span>

<span data-ttu-id="66a64-674">FIPS uyumluluk modu etkin olan makineler artık iş akışı izleme ile iş akışı sürüm 1 stilinde bir uygulamayı başarıyla çalıştırabiliyor.</span><span class="sxs-lookup"><span data-stu-id="66a64-674">Machines with FIPS Compliance Mode enabled can now successfully run a workflow Version 1-style application with Workflow tracking on.</span></span> <span data-ttu-id="66a64-675">Bu senaryoyu etkinleştirmek için app.config dosyanızda aşağıdaki değişikliği yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="66a64-675">To enable this scenario, you must make the following change to your app.config file:</span></span>

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

<span data-ttu-id="66a64-676">Bu senaryo etkinleştirilmemişse, uygulamayı çalıştırmak iletiyle birlikte bir özel durum oluşturmaya devam eder, "Bu uygulama Windows platformu FIPS tarafından doğrulanan şifreleme algoritmalarının bir parçası değil."</span><span class="sxs-lookup"><span data-stu-id="66a64-676">If this scenario is not enabled, running the application continues to generate an exception with the message, "This implementation is not part of the Windows Platform FIPS validated cryptographic algorithms."</span></span>

<span data-ttu-id="66a64-677">**Visual Studio ile dinamik güncelleştirme kullanılırken iş akışı geliştirmeleri İş Akışı Tasarımcısı**</span><span class="sxs-lookup"><span data-stu-id="66a64-677">**Workflow Improvements when using Dynamic Update with Visual Studio Workflow Designer**</span></span>

<span data-ttu-id="66a64-678">İş Akışı Tasarımcısı, akış çizelgesi etkinlik Tasarımcısı ve diğer Iş akışı etkinliği tasarımcıları artık yöntemi çağırdıktan sonra kaydedilmiş iş akışlarını başarıyla yükleyip görüntüler <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-678">The Workflow Designer, FlowChart Activity Designer, and other Workflow Activity Designers now successfully load and display workflows that have been saved after calling  the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="66a64-679">.NET Framework 4.6.2 önce .NET Framework sürümlerinde, çağrıldıktan sonra kaydedilmiş bir iş akışı için Visual Studio 'da bir XAML dosyası yüklemek <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> aşağıdaki sorunlara neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="66a64-679">In versions of the .NET Framework before .NET Framework 4.6.2, loading a XAML file in Visual Studio for a workflow that has been saved after calling <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> can result in the following issues:</span></span>

- <span data-ttu-id="66a64-680">İş Akışı Tasarımcısı XAML dosyasını doğru bir şekilde yükleyemez ( <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> satırın sonunda olduğunda).</span><span class="sxs-lookup"><span data-stu-id="66a64-680">The Workflow Designer can't load the XAML file correctly (when the <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> is at the end of the line).</span></span>

- <span data-ttu-id="66a64-681">Akış çizelgesi etkinlik Tasarımcısı veya diğer Iş akışı etkinliği tasarımcıları, eklenen özellik değerlerinin aksine tüm nesneleri varsayılan konumlarında görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-681">Flowchart Activity Designer or other Workflow Activity Designers may display all objects in their default locations as opposed to attached property values.</span></span>

<a name="clickonce-1"></a>

### <a name="clickonce"></a><span data-ttu-id="66a64-682">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="66a64-682">ClickOnce</span></span>

<span data-ttu-id="66a64-683">ClickOnce, zaten desteklediği 1,0 protokolüne ek olarak TLS 1,1 ve TLS 1,2 ' yi destekleyecek şekilde güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-683">ClickOnce has been updated to support TLS 1.1 and TLS 1.2 in addition to the 1.0 protocol, which it already supports.</span></span> <span data-ttu-id="66a64-684">ClickOnce hangi protokolün gerekli olduğunu otomatik olarak algılar; TLS 1,1 ve 1,2 desteğini etkinleştirmek için ClickOnce uygulaması içinde ek adım gerekmez.</span><span class="sxs-lookup"><span data-stu-id="66a64-684">ClickOnce automatically detects which protocol is required; no extra steps within the ClickOnce application are required to enable TLS 1.1 and 1.2 support.</span></span>

<a name="UWPConvert"></a>

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a><span data-ttu-id="66a64-685">Windows Forms ve WPF uygulamalarını UWP uygulamalarına dönüştürme</span><span class="sxs-lookup"><span data-stu-id="66a64-685">Converting Windows Forms and WPF apps to  UWP apps</span></span>

<span data-ttu-id="66a64-686">Windows artık WPF ve Windows Forms uygulamalar dahil olmak üzere var olan Windows masaüstü uygulamalarını Evrensel Windows Platformu (UWP) uygulamasına getirmeye yönelik yetenekler sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="66a64-686">Windows now offers capabilities to bring existing Windows desktop apps, including WPF and Windows Forms apps, to the Universal Windows Platform (UWP).</span></span> <span data-ttu-id="66a64-687">Bu teknoloji, mevcut kod tabanınızı UWP 'ye kademeli olarak geçirmenize olanak tanıyarak bir köprü görevi görür ve böylece uygulamanızı tüm Windows 10 cihazlarına taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-687">This technology acts as a bridge by enabling you to gradually migrate your existing code base to UWP, thereby bringing your app to all Windows 10 devices.</span></span>

<span data-ttu-id="66a64-688">Dönüştürülmüş masaüstü uygulamaları, UWP API 'Lerinin, canlı kutucuk ve bildirimler gibi özellikleri etkinleştirmek için erişilebilir hale getiren UWP uygulamalarının uygulama kimliğiyle benzer bir uygulama kimliği elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-688">Converted desktop apps gain an app identity similar to the app identity of UWP apps, which makes UWP APIs accessible to enable features such as Live Tiles and notifications.</span></span> <span data-ttu-id="66a64-689">Uygulama, daha önce olduğu gibi davranmaya devam eder ve tam güven uygulaması olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="66a64-689">The app continues to behave as before and runs as a full trust app.</span></span> <span data-ttu-id="66a64-690">Uygulama dönüştürüldükten sonra, bir uyarlamalı Kullanıcı arabirimi eklemek için mevcut tam güven işlemine bir uygulama kapsayıcısı işlemi eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-690">Once the app is converted, an app container process can be added to the existing full trust process to add an adaptive user interface.</span></span> <span data-ttu-id="66a64-691">Tüm işlevler uygulama kapsayıcısı işlemine taşındığında, tam güven işlemi kaldırılabilir ve yeni UWP uygulaması tüm Windows 10 cihazlarında kullanılabilir hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-691">When all functionality is moved to the app container process, the full trust process can be removed and the new UWP app can be made available to all Windows 10 devices.</span></span>

<a name="Debug462"></a>

### <a name="debugging-improvements"></a><span data-ttu-id="66a64-692">Hata ayıklama geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="66a64-692">Debugging improvements</span></span>

<span data-ttu-id="66a64-693">*Yönetilmeyen hata ayıklama API 'si* , bir <xref:System.NullReferenceException> kaynak kodunun tek bir satırındaki hangi değişkenin olduğunu belirleyebilmek mümkün olduğunda ek analizler gerçekleştirmek için .NET Framework 4.6.2 ' de geliştirilmiştir `null` .</span><span class="sxs-lookup"><span data-stu-id="66a64-693">The *unmanaged debugging API* has been enhanced in .NET Framework 4.6.2 to perform additional analysis when a <xref:System.NullReferenceException> is thrown so that it is possible to determine which variable in a single line of source code is `null`.</span></span>   <span data-ttu-id="66a64-694">Bu senaryoyu desteklemek için, yönetilmeyen hata ayıklama API 'sine aşağıdaki API 'Ler eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-694">To support this scenario, the following APIs have been added to the unmanaged debugging API.</span></span>

- <span data-ttu-id="66a64-695">Yönetilen değişkenlerin yerel evlerini açığa çıkaran [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ıcordebugvariablehome](../unmanaged-api/debugging/icordebugvariablehome-interface.md)ve [ıcordebugvariablehomeenum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="66a64-695">The [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md), and [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interfaces, which expose the native homes of managed variables.</span></span> <span data-ttu-id="66a64-696">Bu, hata ayıklayıcıların bir durum oluştuğunda bazı kod akışı analizlerini yapmasına  <xref:System.NullReferenceException> ve geri doğru çalışarak yerel konuma karşılık gelen yönetilen değişkeni belirlemesine olanak sağlar `null` .</span><span class="sxs-lookup"><span data-stu-id="66a64-696">This enables debuggers to do some code flow analysis when a  <xref:System.NullReferenceException> occurs and to work backwards to determine the managed variable that corresponds to the native location that was `null`.</span></span>

- <span data-ttu-id="66a64-697">[ICorDebugType2:: GetTypeId](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) yöntemi ıcordebugtype için [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md)bir eşleme sağlar ve bu da hata ayıklayıcının ICorDebugType örneği olmadan bir [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) almasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-697">The [ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method provides a mapping for ICorDebugType to [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), which allows the debugger to obtain a [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) without an instance of the ICorDebugType.</span></span> <span data-ttu-id="66a64-698">[COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) mevcut API 'ler, daha sonra türün sınıf yerleşimini belirlemede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-698">Existing APIs on [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) can then be used to determine the class layout of the type.</span></span>

<a name="v461"></a>

## <a name="whats-new-in-net-framework-461"></a><span data-ttu-id="66a64-699">.NET Framework 4.6.1 yenilikleri</span><span class="sxs-lookup"><span data-stu-id="66a64-699">What's new in .NET Framework 4.6.1</span></span>

<span data-ttu-id="66a64-700">.NET Framework 4.6.1, aşağıdaki alanlardaki yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-700">.NET Framework 4.6.1 includes new features in the following areas:</span></span>

- [<span data-ttu-id="66a64-701">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="66a64-701">Cryptography</span></span>](#Crypto)

- [<span data-ttu-id="66a64-702">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="66a64-702">ADO.NET</span></span>](#ADO.NET461)

- [<span data-ttu-id="66a64-703">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="66a64-703">Windows Presentation Foundation (WPF)</span></span>](#WPF461)

- [<span data-ttu-id="66a64-704">Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="66a64-704">Windows Workflow Foundation</span></span>](#WWF461)

- [<span data-ttu-id="66a64-705">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="66a64-705">Profiling</span></span>](#Profile461)

- [<span data-ttu-id="66a64-706">NGen</span><span class="sxs-lookup"><span data-stu-id="66a64-706">NGen</span></span>](#NGEN461)

<span data-ttu-id="66a64-707">.NET Framework 4.6.1 hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="66a64-707">For more information on .NET Framework 4.6.1, see the following topics:</span></span>

- [<span data-ttu-id="66a64-708">.NET Framework 4.6.1 listesi</span><span class="sxs-lookup"><span data-stu-id="66a64-708">.NET Framework 4.6.1 list of changes</span></span>](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-changes.md)

- [<span data-ttu-id="66a64-709">4.6.1 'de uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="66a64-709">Application Compatibility in 4.6.1</span></span>](../migration-guide/application-compatibility.md)

- <span data-ttu-id="66a64-710">[.NET Framework API farkı](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (GitHub üzerinde)</span><span class="sxs-lookup"><span data-stu-id="66a64-710">[.NET Framework API diff](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (on GitHub)</span></span>

<a name="Crypto"></a>

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a><span data-ttu-id="66a64-711">Şifreleme: ECDSA içeren x509 sertifikaları için destek</span><span class="sxs-lookup"><span data-stu-id="66a64-711">Cryptography: Support for X509 certificates containing ECDSA</span></span>

<span data-ttu-id="66a64-712">.NET Framework 4,6, x509 sertifikaları için RSACng desteğini ekledi.</span><span class="sxs-lookup"><span data-stu-id="66a64-712">.NET Framework 4.6 added RSACng support for X509 certificates.</span></span> <span data-ttu-id="66a64-713">.NET Framework 4.6.1 ECDSA (Eliptik Eğri dijital Imza algoritması) x509 sertifikaları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-713">.NET Framework 4.6.1 adds support for ECDSA (Elliptic Curve Digital Signature Algorithm) X509 certificates.</span></span>

<span data-ttu-id="66a64-714">ECDSA, daha iyi performans sağlar ve RSA 'dan daha güvenli bir şifreleme algoritmasıdır ve Aktarım Katmanı Güvenliği (TLS) performansının ve ölçeklenebilirliğinin sorun olduğu durumlarda mükemmel bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="66a64-714">ECDSA offers better performance and is a more secure cryptography algorithm than RSA, providing an excellent choice where Transport Layer Security (TLS) performance and scalability is a concern.</span></span> <span data-ttu-id="66a64-715">.NET Framework uygulama, çağrıları mevcut Windows işlevlerine kaydırır.</span><span class="sxs-lookup"><span data-stu-id="66a64-715">The .NET Framework implementation wraps calls into existing Windows functionality.</span></span>

<span data-ttu-id="66a64-716">Aşağıdaki örnek kod, .NET Framework 4.6.1 ' ye dahil edilen ECDSA x509 sertifikaları için yeni desteği kullanarak bir bayt akışı için imza oluşturmanın ne kadar kolay olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="66a64-716">The following example code shows how easy it is to generate a signature for a byte stream by using the new  support for ECDSA  X509 certificates included in .NET Framework 4.6.1.</span></span>

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

<span data-ttu-id="66a64-717">Bu, .NET Framework 4,6 ' de imza oluşturmak için gereken koda işaretlenmiş bir kontrast sunar.</span><span class="sxs-lookup"><span data-stu-id="66a64-717">This offers a marked contrast to the code needed to generate a signature in .NET Framework 4.6.</span></span>

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461"></a>

### <a name="adonet"></a><span data-ttu-id="66a64-718">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="66a64-718">ADO.NET</span></span>

<span data-ttu-id="66a64-719">ADO.NET 'e aşağıdakiler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="66a64-719">The following have been added to ADO.NET:</span></span>

<span data-ttu-id="66a64-720">**Donanım korumalı anahtarlar için Always Encrypted desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-720">**Always Encrypted support for hardware protected keys**</span></span>

<span data-ttu-id="66a64-721">ADO.NET artık Always Encrypted sütunlu ana anahtarların donanım güvenlik modüllerinde (HSM 'ler) yerel olarak depolanmasını desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="66a64-721">ADO.NET now supports storing Always Encrypted column master keys natively in Hardware Security Modules (HSMs).</span></span> <span data-ttu-id="66a64-722">Bu destek sayesinde müşteriler, özel sütun ana anahtar deposu sağlayıcıları yazmak ve bunları uygulamalara kaydetmek zorunda kalmadan HSM 'lerde depolanan Asimetrik Anahtarlarla faydalanabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-722">With this support, customers can leverage asymmetric keys stored in HSMs without having to write custom column master key store providers and registering them in applications.</span></span>

<span data-ttu-id="66a64-723">Müşterilerin HSM 'de depolanan sütun ana anahtarlarıyla korunan Always Encrypted verilerine erişmek için, uygulama sunucularına veya istemci bilgisayarlara HSM satıcı tarafından sunulan CSP sağlayıcısını veya CNG anahtar deposu sağlayıcılarını yüklemeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="66a64-723">Customers need to install the HSM vendor-provided CSP provider or CNG key store providers on the app servers or client computers in order to access Always Encrypted data protected with column master keys stored in a HSM.</span></span>

<span data-ttu-id="66a64-724">**<xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>AlwaysOn için geliştirilmiş bağlantı davranışı**</span><span class="sxs-lookup"><span data-stu-id="66a64-724">**Improved <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> connection behavior for AlwaysOn**</span></span>

<span data-ttu-id="66a64-725">SqlClient artık otomatik olarak bir AlwaysOn kullanılabilirlik grubuna (AG) daha hızlı bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-725">SqlClient now automatically provides faster connections to an AlwaysOn Availability Group (AG).</span></span> <span data-ttu-id="66a64-726">Uygulamanızın farklı bir alt ağda bir AlwaysOn kullanılabilirlik grubuna (AG) bağlanıp bağlanmadığını saydam bir şekilde algılar ve geçerli etkin sunucuyu hızlıca bulup sunucuya bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-726">It transparently detects whether your application is connecting to an AlwaysOn availability group (AG) on a different subnet and quickly discovers the current active server and provides a connection to the server.</span></span> <span data-ttu-id="66a64-727">Bu sürümden önce, bir uygulamanın `"MultisubnetFailover=true"` bir AlwaysOn kullanılabilirlik grubuna bağlanmakta olduğunu göstermek için bağlantı dizesini içerecek şekilde ayarlaması gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="66a64-727">Prior to this release, an application had to set the connection string to include `"MultisubnetFailover=true"` to indicate that it was connecting to an AlwaysOn Availability Group.</span></span> <span data-ttu-id="66a64-728">Bağlantı anahtar sözcüğünü öğesine ayarlamadan `true` , bir uygulama bir AlwaysOn kullanılabilirlik grubuna bağlanılırken zaman aşımı ile karşılaşabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-728">Without setting the connection keyword to `true`, an application might experience a timeout while connecting to an AlwaysOn Availability Group.</span></span> <span data-ttu-id="66a64-729">Bu sürümle, bir uygulamanın artık olarak *ayarlanması gerekmez* <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="66a64-729">With this release, an application does *not* need to set <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> to `true` anymore.</span></span> <span data-ttu-id="66a64-730">Always on kullanılabilirlik grupları için SqlClient desteği hakkında daha fazla bilgi için bkz. [yüksek kullanılabilirlik Için SqlClient desteği, olağanüstü durum kurtarma](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-730">For more information about SqlClient support for Always On Availability Groups, see [SqlClient Support for High Availability, Disaster Recovery](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).</span></span>

<a name="WPF461"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="66a64-731">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="66a64-731">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="66a64-732">Windows Presentation Foundation birkaç iyileştirme ve değişiklik içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-732">Windows Presentation Foundation includes a number of improvements and changes.</span></span>

<span data-ttu-id="66a64-733">**İyileştirilmiş performans**</span><span class="sxs-lookup"><span data-stu-id="66a64-733">**Improved performance**</span></span>

<span data-ttu-id="66a64-734">Dokunma olaylarının tetiklendiği gecikme .NET Framework 4.6.1 içinde düzeltildi.</span><span class="sxs-lookup"><span data-stu-id="66a64-734">The delay in firing touch events has been fixed in .NET Framework 4.6.1.</span></span> <span data-ttu-id="66a64-735">Ayrıca, bir <xref:System.Windows.Controls.RichTextBox> denetime yazmak hızlı giriş sırasında işleme iş parçacığını artık erişemez.</span><span class="sxs-lookup"><span data-stu-id="66a64-735">In addition, typing in a <xref:System.Windows.Controls.RichTextBox> control no longer ties up the render thread during fast input.</span></span>

<span data-ttu-id="66a64-736">**Yazım denetimi geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="66a64-736">**Spell checking improvements**</span></span>

<span data-ttu-id="66a64-737">WPF 'deki yazım denetleyicisi, Windows 8.1 ve sonraki sürümlerinde, yazım denetimi ek dilleri için işletim sistemi desteğinden yararlanmak üzere güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-737">The spell checker in WPF has been updated on Windows 8.1 and later versions to leverage operating system support for spell-checking additional languages.</span></span>  <span data-ttu-id="66a64-738">Windows 8.1 öncesindeki Windows sürümlerindeki işlevlerde değişiklik yoktur.</span><span class="sxs-lookup"><span data-stu-id="66a64-738">There is no change in functionality on Windows versions prior to Windows 8.1.</span></span>

<span data-ttu-id="66a64-739">.NET Framework önceki sürümlerinde olduğu gibi, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> aşağıdaki sırayla bilgi arayarak denetim Ora bloğunun dili algılanır:</span><span class="sxs-lookup"><span data-stu-id="66a64-739">As in previous versions of .NET Framework, the language for a <xref:System.Windows.Controls.TextBox> control ora <xref:System.Windows.Controls.RichTextBox> block is detected by looking for information in the following order:</span></span>

- <span data-ttu-id="66a64-740">`xml:lang`varsa.</span><span class="sxs-lookup"><span data-stu-id="66a64-740">`xml:lang`, if it is present.</span></span>

- <span data-ttu-id="66a64-741">Geçerli giriş dili.</span><span class="sxs-lookup"><span data-stu-id="66a64-741">Current input language.</span></span>

- <span data-ttu-id="66a64-742">Geçerli iş parçacığı kültürü.</span><span class="sxs-lookup"><span data-stu-id="66a64-742">Current thread culture.</span></span>

<span data-ttu-id="66a64-743">WPF dil desteği hakkında daha fazla bilgi için, [.NET Framework 4.6.1 özellikleri hakkında WPF blog](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/)gönderisi bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-743">For more information on language support in WPF, see the [WPF blog post on .NET Framework 4.6.1 features](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/).</span></span>

<span data-ttu-id="66a64-744">**Kullanıcı başına özel sözlükler için ek destek**</span><span class="sxs-lookup"><span data-stu-id="66a64-744">**Additional support for per-user custom dictionaries**</span></span>

<span data-ttu-id="66a64-745">WPF .NET Framework 4.6.1 içinde, genel olarak kaydedilen özel sözlükleri tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-745">In .NET Framework 4.6.1, WPF recognizes custom dictionaries that are registered globally.</span></span> <span data-ttu-id="66a64-746">Bu özellik, denetimleri her denetim için kaydetme özelliğine ek olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-746">This capability is available in addition to the ability to register them per-control.</span></span>

<span data-ttu-id="66a64-747">WPF 'nin önceki sürümlerinde özel sözlükler dışlanan kelimeleri ve otomatik düzeltme listelerini tanımıyor.</span><span class="sxs-lookup"><span data-stu-id="66a64-747">In previous versions of WPF, custom dictionaries did not recognize Excluded Words and AutoCorrect lists.</span></span> <span data-ttu-id="66a64-748">Windows 8.1 ve Windows 10 ' da, dizin altına yerleştirilebilecek dosyaların kullanımı ile desteklenir `%AppData%\Microsoft\Spelling\<language tag>` .</span><span class="sxs-lookup"><span data-stu-id="66a64-748">They are supported on Windows 8.1 and Windows 10 through the use of files that can be placed under the `%AppData%\Microsoft\Spelling\<language tag>` directory.</span></span>  <span data-ttu-id="66a64-749">Bu dosyalar için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="66a64-749">The following rules apply to these files:</span></span>

- <span data-ttu-id="66a64-750">Dosyalar. dic uzantılarına sahip olmalıdır (eklenen kelimeler için),. exc (dışlanan kelimeler için) veya. ACL (otomatik düzeltme için).</span><span class="sxs-lookup"><span data-stu-id="66a64-750">The files should have extensions of .dic (for added words), .exc (for excluded words), or .acl (for AutoCorrect).</span></span>

- <span data-ttu-id="66a64-751">Dosyalar, bayt sırası Işareti (BOM) ile başlayan UTF-16 LE düz metin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-751">The files should be UTF-16 LE plaintext that starts with the Byte Order Mark (BOM).</span></span>

- <span data-ttu-id="66a64-752">Her satır bir sözcükten (eklenen ve dışlanan sözcük listelerinde) ya da dikey çubukla ("&#124;") (otomatik düzeltme sözcük listesinde) ayrılmış sözcükler içeren bir otomatik düzeltme çiftinden oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-752">Each line should consist of a word (in the added and excluded word lists), or an autocorrect pair with the words separated by a vertical bar ("&#124;") (in the AutoCorrect word list).</span></span>

- <span data-ttu-id="66a64-753">Bu dosyalar salt okunurdur ve sistem tarafından değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="66a64-753">These files are considered read-only and are not modified by the system.</span></span>

> [!NOTE]
> <span data-ttu-id="66a64-754">Bu yeni dosya biçimleri WPF yazım denetimi API 'Leri tarafından doğrudan desteklenmez ve uygulamalarda WPF 'ye sağlanan özel sözlüklerin. Lex dosyalarını kullanmaya devam etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="66a64-754">These new file-formats are not directly supported by the WPF spell checking APIs, and the custom dictionaries supplied to WPF in applications should continue to use .lex files.</span></span>

<span data-ttu-id="66a64-755">**Örnekler**</span><span class="sxs-lookup"><span data-stu-id="66a64-755">**Samples**</span></span>

<span data-ttu-id="66a64-756">[Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples) GitHub deposunda birçok WPF örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="66a64-756">There are a number of WPF samples on the [Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples) GitHub repository.</span></span> <span data-ttu-id="66a64-757">Bize bir çekme isteği göndererek veya bir [GitHub sorunu](https://github.com/Microsoft/WPF-Samples/issues)açarak örneklerimizi geliştirmemize yardımcı olun.</span><span class="sxs-lookup"><span data-stu-id="66a64-757">Help us improve our samples by sending us a pull-request or opening a [GitHub issue](https://github.com/Microsoft/WPF-Samples/issues).</span></span>

<span data-ttu-id="66a64-758">**DirectX uzantıları**</span><span class="sxs-lookup"><span data-stu-id="66a64-758">**DirectX extensions**</span></span>

<span data-ttu-id="66a64-759">WPF, DX10 ve DX11 içeriğiyle birlikte çalışabilmeyi kolaylaştıran yeni uygulamaları sağlayan bir [NuGet paketi](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) içerir <xref:System.Windows.Interop.D3DImage> .</span><span class="sxs-lookup"><span data-stu-id="66a64-759">WPF includes a [NuGet package](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) that provides new implementations of <xref:System.Windows.Interop.D3DImage> that make it easy for you to interoperate with DX10 and Dx11 content.</span></span> <span data-ttu-id="66a64-760">Bu paketin kodu açık kaynaklıdır ve [GitHub 'da](https://github.com/Microsoft/WPFDXInterop)kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-760">The code for this package has been open sourced and is available [on GitHub](https://github.com/Microsoft/WPFDXInterop).</span></span>

<a name="WWF461"></a>

### <a name="windows-workflow-foundation-transactions"></a><span data-ttu-id="66a64-761">Windows Workflow Foundation: Işlemler</span><span class="sxs-lookup"><span data-stu-id="66a64-761">Windows Workflow Foundation: Transactions</span></span>

<span data-ttu-id="66a64-762"><xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType>Yöntemi artık işlemi yükseltmek IÇIN MSDTC dışında bir dağıtılmış işlem yöneticisi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-762">The <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> method can now use a distributed transaction manager other than MSDTC to promote the transaction.</span></span> <span data-ttu-id="66a64-763">Yeni aşırı yüklemeye bir GUID işlem Promoter tanımlayıcısı belirterek bunu yapabilirsiniz <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-763">You do this by specifying a GUID transaction promoter identifier to the  new <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> overload .</span></span> <span data-ttu-id="66a64-764">Bu işlem başarılı olursa, işlemin özelliklerine yerleştirilmiş sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="66a64-764">If this operation is successful, there are limitations placed on the capabilities of the transaction.</span></span> <span data-ttu-id="66a64-765">MSDTC olmayan bir işlem promosyonu kaydedildikten sonra, <xref:System.Transactions.TransactionPromotionException> Bu yöntemler MSDTC 'ye yükseltme gerektirdiğinden aşağıdaki yöntemler bir oluşturur:</span><span class="sxs-lookup"><span data-stu-id="66a64-765">Once a non-MSDTC transaction promoter is enlisted, the following methods throw a <xref:System.Transactions.TransactionPromotionException> because these methods require promotion to MSDTC:</span></span>

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

<span data-ttu-id="66a64-766">MSDTC olmayan bir işlem Promoter kaydedildikten sonra, tanımladığı protokoller kullanılarak gelecekteki dayanıklı kayıtlar için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-766">Once a non-MSDTC transaction promoter is enlisted, it must be used for future durable enlistments by using protocols that it defines.</span></span> <span data-ttu-id="66a64-767"><xref:System.Guid>İşlem Promoter, özelliği kullanılarak elde edilebilir <xref:System.Transactions.Transaction.PromoterType%2A> .</span><span class="sxs-lookup"><span data-stu-id="66a64-767">The <xref:System.Guid> of the transaction promoter can be obtained by using the <xref:System.Transactions.Transaction.PromoterType%2A> property.</span></span> <span data-ttu-id="66a64-768">İşlem yükseltildiğinde, işlem Promoter <xref:System.Byte> yükseltilen belirteci temsil eden bir dizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-768">When the transaction promotes, the transaction promoter provides a <xref:System.Byte> array that represents the promoted token.</span></span> <span data-ttu-id="66a64-769">Bir uygulama, yöntemi ile MSDTC olmayan bir yükseltilen işlem için yükseltilen belirteci elde edebilir <xref:System.Transactions.Transaction.GetPromotedToken%2A> .</span><span class="sxs-lookup"><span data-stu-id="66a64-769">An application can obtain the promoted token for a non-MSDTC promoted transaction with the <xref:System.Transactions.Transaction.GetPromotedToken%2A> method.</span></span>

<span data-ttu-id="66a64-770"><xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType>Yükseltme işleminin başarıyla tamamlanabilmesi için yeni aşırı yükleme kullanıcıları belirli bir çağrı sırasını izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-770">Users of the new <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> overload must follow a specific call sequence in order for the promotion operation to complete successfully.</span></span> <span data-ttu-id="66a64-771">Bu kurallar yöntemin belgelerinde belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-771">These rules are documented in the method's documentation.</span></span>

<a name="Profile461"></a>

### <a name="profiling"></a><span data-ttu-id="66a64-772">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="66a64-772">Profiling</span></span>

<span data-ttu-id="66a64-773">Yönetilmeyen profil oluşturma API 'SI aşağıdaki şekilde geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="66a64-773">The unmanaged profiling API has been enhanced as follows:</span></span>

- <span data-ttu-id="66a64-774">[ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) arabirimindeki pdb 'leri 'e erişmek için daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="66a64-774">Better support for accessing PDBs in the [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface.</span></span>

  <span data-ttu-id="66a64-775">ASP.NET Core, derleme işlemleri için Roslyn tarafından bellek içinde derlenmesi çok daha yaygın hale geliyor.</span><span class="sxs-lookup"><span data-stu-id="66a64-775">In ASP.NET Core, it is becoming much more common for assemblies to be compiled in-memory by Roslyn.</span></span> <span data-ttu-id="66a64-776">Profil oluşturma araçları kuran geliştiriciler için bu, geçmişte diskte serileştirilmiş olan pdb 'leri artık mevcut olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-776">For developers making profiling tools, this means that PDBs that historically were serialized on disk may no longer be present.</span></span> <span data-ttu-id="66a64-777">Profil Oluşturucu araçları genellikle kodu, kod kapsamı veya satır içi performans analizi gibi görevler için kaynak satırlara eşlemek için pdb 'leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-777">Profiler tools often use PDBs to map code back to source lines for tasks such as code coverage or line-by-line performance analysis.</span></span> <span data-ttu-id="66a64-778">[ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) arabirimi artık iki yeni yöntem Içerir: [ICorProfilerInfo7:: GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) ve [ICorProfilerInfo7:: ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), bu Profiler araçlarının yenı API 'leri kullanarak bellek içi pdb verilerine erişimi sağlamak için, bir profil oluşturucu bellek içi pdb 'nin içeriğini bayt dizisi olarak edinebilir ve sonra işleyebilir veya diske serileştirmez.</span><span class="sxs-lookup"><span data-stu-id="66a64-778">The [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface now includes two new methods, [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) and [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), to provide these profiler tools with access to the in-memory PDB data, By using the new APIs, a profiler can obtain the contents of an in-memory PDB as a byte array and then process it or serialize it to disk.</span></span>

- <span data-ttu-id="66a64-779">ICorProfiler arabirimiyle daha iyi izleme.</span><span class="sxs-lookup"><span data-stu-id="66a64-779">Better instrumentation with the ICorProfiler interface.</span></span>

  <span data-ttu-id="66a64-780">`ICorProfiler`Dinamik izleme API 'leri Için yeniden JIT işlevselliği kullanan profil oluşturucular artık bazı meta verileri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-780">Profilers that are using the `ICorProfiler` APIs ReJit functionality for dynamic instrumentation can now modify some metadata.</span></span> <span data-ttu-id="66a64-781">Daha önce böyle araçlar, herhangi bir zamanda Il 'yi işaretleyebilir, ancak meta veriler yalnızca modül yükleme sırasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-781">Previously such tools could instrument IL at any time, but metadata could only be modified at module load time.</span></span> <span data-ttu-id="66a64-782">Il meta verilere başvurduğundan, bu, yapılabilecek izleme türlerini sınırlandırıyor.</span><span class="sxs-lookup"><span data-stu-id="66a64-782">Because IL refers to metadata, this limited the kinds of instrumentation that could be done.</span></span> <span data-ttu-id="66a64-783">Modül yüklendikten sonra, özellikle yeni,,,,, ve kayıtları ekleyerek, meta veri düzenlemelerinin bir alt kümesini desteklemek için [ICorProfilerInfo7:: ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) metodunu ekleyerek bu limitlerin bazılarını yükseltilmemiş sunuyoruz `AssemblyRef` `TypeRef` `TypeSpec` `MemberRef` `MemberSpec` `UserString` .</span><span class="sxs-lookup"><span data-stu-id="66a64-783">We have lifted some of those limits by adding the [ICorProfilerInfo7::ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) method to support a subset of metadata edits after the module loads, in particular by adding new `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, and `UserString` records.</span></span> <span data-ttu-id="66a64-784">Bu değişiklik, mümkün olan çok daha geniş bir izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-784">This change makes a much broader range of on-the-fly instrumentation possible.</span></span>

<a name="NGEN461"></a>

### <a name="native-image-generator-ngen-pdbs"></a><span data-ttu-id="66a64-785">Yerel Görüntü Oluşturucu (NGEN) pdb 'leri</span><span class="sxs-lookup"><span data-stu-id="66a64-785">Native Image Generator (NGEN) PDBs</span></span>

<span data-ttu-id="66a64-786">Çapraz makine olay izleme, müşterilerin makine A 'daki bir programı oluşturmalarına ve B makinesi üzerinde kaynak satır eşleme ile profil oluşturma verilerine bakmaya olanak sağlar. önceki .NET Framework sürümlerini kullanarak, Kullanıcı profili oluşturulan makineden tüm modülleri ve yerel görüntüleri, kaynak-yerel eşlemeyi oluşturmak için Il PDB 'yi içeren analiz makinesine kopyalayabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-786">Cross-machine event tracing allows customers to profile a program on Machine A and look at the profiling data with source line mapping on Machine B. Using previous versions of .NET Framework, the user would copy all the modules and native images from the profiled machine to the analysis machine that contains the IL PDB to create the source-to-native mapping.</span></span> <span data-ttu-id="66a64-787">Bu işlem, dosyalar görece küçük olduğunda (örneğin, telefon uygulamaları için), dosyalar masaüstü sistemlerinde çok büyük olabilir ve kopyalamak için önemli bir zaman gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-787">While this process may work well when the files are relatively small, such as for phone applications, the files can be very large on desktop systems and require significant time to copy.</span></span>

<span data-ttu-id="66a64-788">Ngen pdb 'leri ile NGen, Il PDB 'ye bağımlılık olmadan IL-yerel eşlemeyi içeren bir PDB oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-788">With Ngen PDBs, NGen can create a PDB that contains the IL-to-native mapping without a dependency on the IL PDB.</span></span> <span data-ttu-id="66a64-789">Makineler arası olay izleme senaryolarımızda, A makinesi tarafından oluşturulan yerel görüntü PDB 'sini B makinesine kopyalamak ve Il PDB 'nin kaynaktan Il eşlemesini ve yerel görüntü PDB 'nin Il-to-to-Native eşlemesini okumak için [hata ayıklama arabirimi erişim API 'lerini](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) kullanmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-789">In our cross-machine event tracing scenario, all that is needed is to copy the native image PDB that is generated by Machine A to Machine B and to use [Debug Interface Access APIs](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) to read the IL PDB's source-to-IL mapping and the native image PDB's IL-to-native mapping.</span></span> <span data-ttu-id="66a64-790">Her iki eşlemeyi de birleştirmek, kaynaktan yerel eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-790">Combining both mappings provides a source-to-native mapping.</span></span> <span data-ttu-id="66a64-791">Yerel görüntü PDB tüm modüllerden ve yerel görüntülerden çok daha küçük olduğundan, A makinesinden B makinesine kopyalama işlemi çok daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-791">Since the native image PDB is much smaller than all the modules and native images, the process of copying from Machine A to Machine B is much faster.</span></span>

<a name="v46"></a>

## <a name="whats-new-in-net-2015"></a><span data-ttu-id="66a64-792">.NET 2015 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="66a64-792">What's new in .NET 2015</span></span>

<span data-ttu-id="66a64-793">.NET 2015, .NET Framework 4,6 ve .NET Core ' u sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="66a64-793">.NET 2015 introduces .NET Framework 4.6 and .NET Core.</span></span> <span data-ttu-id="66a64-794">Bazı yeni özellikler için geçerlidir ve diğer özellikler .NET Framework 4,6 veya .NET Core 'a özgüdür.</span><span class="sxs-lookup"><span data-stu-id="66a64-794">Some new features apply to both, and other features are specific to .NET Framework 4.6 or .NET Core.</span></span>

- <span data-ttu-id="66a64-795">**ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="66a64-795">**ASP.NET Core**</span></span>

  <span data-ttu-id="66a64-796">.NET 2015, modern bulut tabanlı uygulamalar oluşturmak için yalın bir .NET uygulaması olan ASP.NET Core içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-796">.NET 2015 includes ASP.NET Core, which is a lean .NET implementation for building modern cloud-based apps.</span></span> <span data-ttu-id="66a64-797">ASP.NET Core modüler olduğundan, yalnızca uygulamanızda gerekli olan özellikleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-797">ASP.NET Core is modular so you can include only those features that are needed in your application.</span></span> <span data-ttu-id="66a64-798">IIS 'de veya özel bir işlemde barındırılabilecek ve aynı sunucuda .NET Framework farklı sürümleriyle uygulamalar çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-798">It can be hosted on IIS or self-hosted in a custom process, and you can run apps with different versions of the .NET Framework on the same server.</span></span> <span data-ttu-id="66a64-799">Bulut dağıtımı için tasarlanan yeni bir ortam yapılandırma sistemi içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-799">It includes a new environment configuration system that is designed for cloud deployment.</span></span>

  <span data-ttu-id="66a64-800">MVC, Web API 'SI ve Web sayfaları, MVC 6 adlı tek bir çerçevede birleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-800">MVC, Web API, and Web Pages are unified into a single framework called MVC 6.</span></span> <span data-ttu-id="66a64-801">Visual Studio 2015 veya sonraki sürümlerde araçlar aracılığıyla ASP.NET Core uygulamalar derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-801">You build ASP.NET Core apps through tools in Visual Studio 2015 or later.</span></span> <span data-ttu-id="66a64-802">Mevcut uygulamalarınız yeni .NET Framework çalışacaktır; Ancak, MVC 6 veya SignalR 3 kullanan bir uygulama oluşturmak için Visual Studio 2015 veya sonraki sürümlerde proje sistemini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="66a64-802">Your existing applications will work on the new .NET Framework; however to build an app that uses MVC 6 or SignalR 3, you must use the project system in Visual Studio 2015 or later.</span></span>

  <span data-ttu-id="66a64-803">Bilgi için bkz. [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="66a64-803">For information, see [ASP.NET Core](/aspnet/core/).</span></span>

- <span data-ttu-id="66a64-804">**ASP.NET güncelleştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="66a64-804">**ASP.NET Updates**</span></span>

  - <span data-ttu-id="66a64-805">**Zaman uyumsuz yanıt Temizleme için görev tabanlı API**</span><span class="sxs-lookup"><span data-stu-id="66a64-805">**Task-based API for Asynchronous Response Flushing**</span></span>

    <span data-ttu-id="66a64-806">ASP.NET artık zaman uyumsuz yanıt Temizleme için basit bir görev tabanlı API sağlıyor, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType> Bu da yanıtların, dilinizin desteği kullanılarak zaman uyumsuz olarak temizlenmesini sağlar `async/await` .</span><span class="sxs-lookup"><span data-stu-id="66a64-806">ASP.NET now provides a simple task-based API for asynchronous response flushing, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, that allows responses to be flushed asynchronously by using your language's `async/await` support.</span></span>

  - <span data-ttu-id="66a64-807">**Model bağlama, görev döndüren yöntemleri destekler**</span><span class="sxs-lookup"><span data-stu-id="66a64-807">**Model binding supports task-returning methods**</span></span>

    <span data-ttu-id="66a64-808">.NET Framework 4,5 ' de ASP.NET, Web Forms sayfalarındaki ve Kullanıcı denetimlerindeki CRUD tabanlı veri işlemlerine Genişletilebilir, kod odaklı bir yaklaşım uygulayan model bağlama özelliğini ekledi.</span><span class="sxs-lookup"><span data-stu-id="66a64-808">In .NET Framework 4.5, ASP.NET added the Model Binding feature that enabled an extensible, code-focused approach to CRUD-based data operations in Web Forms pages and user controls.</span></span> <span data-ttu-id="66a64-809">Model bağlama sistemi artık ' i destekleyen <xref:System.Threading.Tasks.Task> model bağlama yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="66a64-809">The Model Binding system now supports <xref:System.Threading.Tasks.Task>-returning model binding methods.</span></span> <span data-ttu-id="66a64-810">Bu özellik, Web Forms geliştiricilerin, Entity Framework dahil olmak üzere daha yeni sürümleri kullanırken veri bağlama sistemi sayesinde, zaman uyumsuz olan ölçeklenebilirlik avantajlarını elde etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-810">This feature allows Web Forms developers to get the scalability benefits of async with the ease of the data-binding system when using newer versions of ORMs, including the Entity Framework.</span></span>

    <span data-ttu-id="66a64-811">Zaman uyumsuz model bağlama `aspnet:EnableAsyncModelBinding` yapılandırma ayarı tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="66a64-811">Async model binding is controlled by the `aspnet:EnableAsyncModelBinding` configuration setting.</span></span>

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    <span data-ttu-id="66a64-812">Hedef .NET Framework 4,6 ' de, varsayılan olarak olur `true` .</span><span class="sxs-lookup"><span data-stu-id="66a64-812">On apps the target .NET Framework 4.6, it defaults to `true`.</span></span> <span data-ttu-id="66a64-813">.NET Framework önceki bir sürümünü hedefleyen .NET Framework 4,6 üzerinde çalışan uygulamalarda `false` Varsayılan olarak olur.</span><span class="sxs-lookup"><span data-stu-id="66a64-813">On apps running on .NET Framework 4.6 that target an earlier version of .NET Framework, it is `false` by default.</span></span> <span data-ttu-id="66a64-814">Yapılandırma ayarı olarak ayarlanarak etkinleştirilebilir `true` .</span><span class="sxs-lookup"><span data-stu-id="66a64-814">It can be enabled by setting the configuration setting to `true`.</span></span>

  - <span data-ttu-id="66a64-815">**HTTP/2 desteği (Windows 10)**</span><span class="sxs-lookup"><span data-stu-id="66a64-815">**HTTP/2 Support (Windows 10)**</span></span>

    <span data-ttu-id="66a64-816">[Http/2](https://www.wikipedia.org/wiki/HTTP/2) , çok daha iyi bağlantı kullanımı (istemci ve sunucu arasında daha az gidiş dönüş) sağlayan yenı bir http Protokolü sürümüdür ve bu sayede kullanıcılar için daha düşük gecikme süresi Web sayfası yüklemesi oluşur.</span><span class="sxs-lookup"><span data-stu-id="66a64-816">[HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) is a new version of the HTTP protocol that provides much better connection utilization (fewer round-trips between client and server), resulting in lower latency web page loading for users.</span></span>  <span data-ttu-id="66a64-817">Web sayfaları (hizmetler 'in aksine) HTTP/2 ' den en iyi şekilde faydalanır çünkü protokol, tek bir deneyimin bir parçası olarak istenen birden çok yapıtı için iyileştirmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-817">Web pages (as opposed to services) benefit the most from HTTP/2, since the protocol optimizes for multiple artifacts being requested as part of a single experience.</span></span> <span data-ttu-id="66a64-818">.NET Framework 4,6 ' de ASP.NET 'e HTTP/2 desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-818">HTTP/2 support has been added to ASP.NET in .NET Framework 4.6.</span></span> <span data-ttu-id="66a64-819">Ağ işlevselliği birden çok katmanda mevcut olduğundan, Windows 'da, IIS 'de ve ASP.NET ' de HTTP/2 ' yi etkinleştirmek için yeni özellikler gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="66a64-819">Because networking functionality exists at multiple layers, new features were required in Windows, in IIS, and in ASP.NET to enable HTTP/2.</span></span> <span data-ttu-id="66a64-820">ASP.NET ile HTTP/2 kullanmak için Windows 10 ' da çalıştırıyor olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="66a64-820">You must be running on Windows 10 to use HTTP/2 with ASP.NET.</span></span>

    <span data-ttu-id="66a64-821">HTTP/2 Ayrıca API kullanan Windows 10 Evrensel Windows Platformu (UWP) uygulamaları için varsayılan olarak desteklenir <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-821">HTTP/2 is also supported and on by default for Windows 10 Universal Windows Platform (UWP) apps that use the <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> API.</span></span>

    <span data-ttu-id="66a64-822">ASP.NET uygulamalarında [PUSH_PROMISE](https://httpwg.github.io/http2-spec/#PUSH_PROMISE) özelliğini kullanmanın bir yolunu sağlamak için, iki aşırı yüklemeye sahip yeni bir yöntem <xref:System.Web.HttpResponse.PushPromise%28System.String%29> ve <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29> , <xref:System.Web.HttpResponse> sınıfına eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-822">In order to provide a way to use the [PUSH_PROMISE](https://httpwg.github.io/http2-spec/#PUSH_PROMISE) feature in ASP.NET applications, a new method with two overloads, <xref:System.Web.HttpResponse.PushPromise%28System.String%29> and <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, has been added to the <xref:System.Web.HttpResponse> class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="66a64-823">ASP.NET Core HTTP/2 ' yi desteklese de, anında PROMISE özelliği için destek henüz eklenmemiş.</span><span class="sxs-lookup"><span data-stu-id="66a64-823">While ASP.NET Core supports HTTP/2, support for the PUSH PROMISE feature has not yet been added.</span></span>

    <span data-ttu-id="66a64-824">Tarayıcı ve Web sunucusu (Windows üzerinde IIS) tüm işleri çalışır.</span><span class="sxs-lookup"><span data-stu-id="66a64-824">The browser and the web server (IIS on Windows) do all the work.</span></span> <span data-ttu-id="66a64-825">Kullanıcılarınız için herhangi bir ağır kaldırma yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="66a64-825">You don't have to do any heavy-lifting for your users.</span></span>

    <span data-ttu-id="66a64-826">[Büyük tarayıcıların çoğu http/2 ' yi desteklediğinden](https://www.wikipedia.org/wiki/HTTP/2), sunucunuz bunu destekliyorsa, kullanıcılarınızın http/2 desteğinden faydalanır olması olasıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-826">Most of the [major browsers support HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), so it's likely that your users will benefit from HTTP/2 support if your server supports it.</span></span>

  - <span data-ttu-id="66a64-827">**Belirteç bağlama protokolü desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-827">**Support for the Token Binding Protocol**</span></span>

    <span data-ttu-id="66a64-828">Microsoft ve Google, [belirteç bağlama protokolü](https://github.com/TokenBinding/Internet-Drafts)olarak adlandırılan kimlik doğrulamaya yönelik yeni bir yaklaşım üzerinde işbirliği yapmış.</span><span class="sxs-lookup"><span data-stu-id="66a64-828">Microsoft and Google have been collaborating on a new approach to authentication, called the [Token Binding Protocol](https://github.com/TokenBinding/Internet-Drafts).</span></span> <span data-ttu-id="66a64-829">Şirket içi, kimlik doğrulama belirteçlerinin (tarayıcı önbelleğinizin) çalınabileceği ve güvenli kaynaklara (örneğin, banka hesabınızda) parola veya herhangi bir ayrıcalıklı bilgi gerekmeden erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-829">The premise is that authentication tokens (in your browser cache) can be stolen and used by criminals to access otherwise secure resources (for example, your bank account) without requiring your password or any other privileged knowledge.</span></span> <span data-ttu-id="66a64-830">Bu sorunu hafifletmek için yeni protokol amaçlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-830">The new protocol aims to mitigate this problem.</span></span>

    <span data-ttu-id="66a64-831">Belirteç bağlama protokolü Windows 10 ' da bir tarayıcı özelliği olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-831">The Token Binding Protocol will be implemented in Windows 10 as a browser feature.</span></span> <span data-ttu-id="66a64-832">ASP.NET uygulamalar protokolde yer alacak ve kimlik doğrulama belirteçlerinin yasal olması için doğrulanacak.</span><span class="sxs-lookup"><span data-stu-id="66a64-832">ASP.NET apps will participate in the protocol, so that authentication tokens are validated to be legitimate.</span></span> <span data-ttu-id="66a64-833">İstemci ve sunucu uygulamaları, protokol tarafından belirtilen uçtan uca korumayı oluştururlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-833">The client and the server implementations establish the end-to-end protection specified by the protocol.</span></span>

  - <span data-ttu-id="66a64-834">**Rastgele dize karma algoritmaları**</span><span class="sxs-lookup"><span data-stu-id="66a64-834">**Randomized string hash algorithms**</span></span>

    <span data-ttu-id="66a64-835">.NET Framework 4,5, [rastgele bir dize karma algoritması](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="66a64-835">.NET Framework 4.5 introduced a [randomized string hash algorithm](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span></span> <span data-ttu-id="66a64-836">Ancak, ASP.NET tarafından, kararlı bir karma koda bağımlı bazı ASP.NET özellikleri nedeniyle desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="66a64-836">However, it was not supported by ASP.NET because of some ASP.NET features depended on a stable hash code.</span></span> <span data-ttu-id="66a64-837">.NET Framework 4,6 ' de, rastgele dize karma algoritmaları artık desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="66a64-837">In .NET Framework 4.6, randomized string hash algorithms are now supported.</span></span> <span data-ttu-id="66a64-838">Bu özelliği etkinleştirmek için `aspnet:UseRandomizedStringHashAlgorithm` yapılandırma ayarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="66a64-838">To enable this feature, use the `aspnet:UseRandomizedStringHashAlgorithm` config setting.</span></span>

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- <span data-ttu-id="66a64-839">**ADO.NET**</span><span class="sxs-lookup"><span data-stu-id="66a64-839">**ADO.NET**</span></span>

  <span data-ttu-id="66a64-840">ADO .NET artık SQL Server 2016 Community Technology Preview 2 ' de (CTP2) sunulan Always Encrypted özelliğini desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="66a64-840">ADO .NET now supports the Always Encrypted feature available in SQL Server 2016 Community Technology Preview 2 (CTP2).</span></span> <span data-ttu-id="66a64-841">Always Encrypted, SQL Server şifrelenmiş veriler üzerinde işlemler gerçekleştirebilir ve tüm şifreleme anahtarının en iyisi, sunucuda değil, müşterinin güvenilir ortamındaki uygulamayla birlikte bulunur.</span><span class="sxs-lookup"><span data-stu-id="66a64-841">With Always Encrypted, SQL Server can perform operations on encrypted data, and best of all the encryption key resides with the application inside the customer's trusted environment and not on the server.</span></span> <span data-ttu-id="66a64-842">Always Encrypted, müşteri verilerinin güvenliğini sağlar, böylece DBAs düz metin verilerine erişemez.</span><span class="sxs-lookup"><span data-stu-id="66a64-842">Always Encrypted secures customer data so DBAs do not have access to plain text data.</span></span> <span data-ttu-id="66a64-843">Verilerin şifrelenmesi ve şifresinin çözülmesi, sürücü düzeyinde saydam bir şekilde gerçekleşir ve mevcut uygulamalarda yapılması gereken değişiklikleri en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-843">Encryption and decryption of data happens transparently at the driver level, minimizing changes that have to be made to existing applications.</span></span> <span data-ttu-id="66a64-844">Ayrıntılar için bkz. [Always Encrypted (veritabanı altyapısı)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) ve [Always Encrypted (istemci geliştirme)](/sql/relational-databases/security/encryption/always-encrypted-client-development).</span><span class="sxs-lookup"><span data-stu-id="66a64-844">For details, see [Always Encrypted (Database Engine)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) and [Always Encrypted (client development)](/sql/relational-databases/security/encryption/always-encrypted-client-development).</span></span>

- <span data-ttu-id="66a64-845">**yönetilen kod için 64 bit JıT derleyicisi**</span><span class="sxs-lookup"><span data-stu-id="66a64-845">**64-bit JIT Compiler for managed code**</span></span>

  <span data-ttu-id="66a64-846">.NET Framework 4,6, 64 bit JıT derleyicisinin yeni bir sürümünü (özgün olarak kod adı RyuJIT) sunar.</span><span class="sxs-lookup"><span data-stu-id="66a64-846">.NET Framework 4.6 features a new version of the 64-bit JIT compiler (originally code-named RyuJIT).</span></span> <span data-ttu-id="66a64-847">Yeni 64 bit derleyicisi, eski 64 bit JıT derleyicisi üzerinde önemli performans iyileştirmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-847">The new 64-bit compiler provides significant performance improvements over the older 64-bit JIT compiler.</span></span> <span data-ttu-id="66a64-848">Yeni 64 bit derleyici, .NET Framework 4,6 üzerinde çalışan 64 bit süreçler için etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-848">The new 64-bit compiler is enabled for 64-bit processes running on top of .NET Framework 4.6.</span></span> <span data-ttu-id="66a64-849">Uygulamanız 64 bit ya da AnyCPU olarak derlenirse ve bir 64-bit işletim sisteminde çalışıyorsa, 64 bitlik bir işlemde çalışır.</span><span class="sxs-lookup"><span data-stu-id="66a64-849">Your app will run in a 64-bit process if it is compiled as 64-bit or AnyCPU and is running on a 64-bit operating system.</span></span> <span data-ttu-id="66a64-850">Yeni derleyiciye geçişi mümkün olduğunca saydam hale getirmek için dikkatli olunurken, davranıştaki değişiklikler mümkündür.</span><span class="sxs-lookup"><span data-stu-id="66a64-850">While care has been taken to make the transition to the new compiler as transparent as possible, changes in behavior are possible.</span></span>

  <span data-ttu-id="66a64-851">Yeni 64-bit JıT derleyicisi Ayrıca, ad alanındaki SıMD özellikli türlerle birlikte kullanıldığında <xref:System.Numerics> , iyi performans iyileştirmeleri elde eden donanım SIMD hızlandırma özelliklerini de içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-851">The new 64-bit JIT compiler also includes hardware SIMD acceleration features when coupled with SIMD-enabled types in the <xref:System.Numerics> namespace, which can yield good performance improvements.</span></span>

- <span data-ttu-id="66a64-852">**Derleme yükleyici geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="66a64-852">**Assembly loader improvements**</span></span>

  <span data-ttu-id="66a64-853">Derleme yükleyicisi artık, ilgili bir NGEN görüntüsü yüklendikten sonra Il derlemelerini kaldırarak belleği daha verimli bir şekilde kullanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="66a64-853">The assembly loader now uses memory more efficiently by unloading IL assemblies after a corresponding NGEN image is loaded.</span></span> <span data-ttu-id="66a64-854">Bu değişiklik, özellikle büyük 32 bitlik uygulamalar (Visual Studio gibi) için yararlı olan sanal belleği azaltır ve fiziksel belleği da kaydeder.</span><span class="sxs-lookup"><span data-stu-id="66a64-854">This change decreases virtual memory, which is particularly beneficial for large 32-bit apps (such as Visual Studio), and also saves physical memory.</span></span>

- <span data-ttu-id="66a64-855">**Temel sınıf kitaplığı değişiklikleri**</span><span class="sxs-lookup"><span data-stu-id="66a64-855">**Base class library changes**</span></span>

  <span data-ttu-id="66a64-856">Temel senaryoları etkinleştirmek için .NET Framework 4,6 ' ye birçok yeni API eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-856">Many new APIs have been added around to .NET Framework 4.6 to enable key scenarios.</span></span> <span data-ttu-id="66a64-857">Bunlar aşağıdaki değişiklikleri ve eklemeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-857">These include the following changes and additions:</span></span>

  - <span data-ttu-id="66a64-858">**IReadOnlyCollection \<T> uygulamaları**</span><span class="sxs-lookup"><span data-stu-id="66a64-858">**IReadOnlyCollection\<T> implementations**</span></span>

    <span data-ttu-id="66a64-859">, Ve gibi ek koleksiyonlar uygular <xref:System.Collections.Generic.IReadOnlyCollection%601> <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Generic.Stack%601> .</span><span class="sxs-lookup"><span data-stu-id="66a64-859">Additional collections implement <xref:System.Collections.Generic.IReadOnlyCollection%601> such as <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601>.</span></span>

  - <span data-ttu-id="66a64-860">**CultureInfo. CurrentCulture ve CultureInfo. CurrentUICulture**</span><span class="sxs-lookup"><span data-stu-id="66a64-860">**CultureInfo.CurrentCulture and CultureInfo.CurrentUICulture**</span></span>

    <span data-ttu-id="66a64-861"><xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>Ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özellikleri artık salt okuma yerine salt yazılır.</span><span class="sxs-lookup"><span data-stu-id="66a64-861">The <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> properties are now read-write rather than read-only.</span></span> <span data-ttu-id="66a64-862"><xref:System.Globalization.CultureInfo>Bu özelliklere yeni bir nesne atarsanız, özelliği tarafından tanımlanan geçerli iş parçacığı kültürü `Thread.CurrentThread.CurrentCulture` ve özellikler tarafından tanımlanan geçerli UI iş parçacığı kültürü `Thread.CurrentThread.CurrentUICulture` de değişir.</span><span class="sxs-lookup"><span data-stu-id="66a64-862">If you assign a new <xref:System.Globalization.CultureInfo> object to these properties, the current thread culture defined by the `Thread.CurrentThread.CurrentCulture` property and the current UI thread culture defined by the `Thread.CurrentThread.CurrentUICulture` properties also change.</span></span>

  - <span data-ttu-id="66a64-863">**Çöp toplama geliştirmeleri (GC)**</span><span class="sxs-lookup"><span data-stu-id="66a64-863">**Enhancements to garbage collection (GC)**</span></span>

    <span data-ttu-id="66a64-864"><xref:System.GC>Sınıfı artık, <xref:System.GC.TryStartNoGCRegion%2A> <xref:System.GC.EndNoGCRegion%2A> önemli bir yolun yürütülmesi sırasında çöp toplamaya izin vermemeyi sağlayan yöntemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-864">The <xref:System.GC> class now includes <xref:System.GC.TryStartNoGCRegion%2A> and <xref:System.GC.EndNoGCRegion%2A> methods that allow you to disallow garbage collection during the execution of a critical path.</span></span>

    <span data-ttu-id="66a64-865">Yönteminin yeni bir aşırı yüklemesi, <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> hem küçük nesne yığını hem de büyük nesne yığınının birlikte ve yalnızca swemi yoksa yalnızca swemi olduğunu denetlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-865">A new overload of the <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> method allows you to control whether both the small object heap and the large object heap are swept and compacted or swept only.</span></span>

  - <span data-ttu-id="66a64-866">**SIMD özellikli türler**</span><span class="sxs-lookup"><span data-stu-id="66a64-866">**SIMD-enabled types**</span></span>

    <span data-ttu-id="66a64-867"><xref:System.Numerics>Ad alanı artık,,,,, ve gibi birçok SIMD özellikli türü <xref:System.Numerics.Matrix3x2> içerir <xref:System.Numerics.Matrix4x4> <xref:System.Numerics.Plane> <xref:System.Numerics.Quaternion> <xref:System.Numerics.Vector2> <xref:System.Numerics.Vector3> <xref:System.Numerics.Vector4> .</span><span class="sxs-lookup"><span data-stu-id="66a64-867">The <xref:System.Numerics> namespace now includes a number of SIMD-enabled types, such as <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4>.</span></span>

    <span data-ttu-id="66a64-868">Yeni 64-bit JıT derleyicisi Ayrıca donanım SıMD hızlandırma özellikleri de içerdiğinden, yeni 64 bit JıT derleyicisi ile SıMD özellikli türler kullanılırken özellikle önemli performans iyileştirmeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="66a64-868">Because the new 64-bit JIT compiler also includes hardware SIMD acceleration features, there are especially significant performance improvements when using the SIMD-enabled types with the new 64-bit JIT compiler.</span></span>

  - <span data-ttu-id="66a64-869">**Şifreleme güncelleştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="66a64-869">**Cryptography updates**</span></span>

    <span data-ttu-id="66a64-870"><xref:System.Security.Cryptography?displayProperty=nameWithType>API, [Windows CNG şifreleme API 'lerini](/windows/desktop/SecCNG/cng-reference)destekleyecek şekilde güncelleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="66a64-870">The <xref:System.Security.Cryptography?displayProperty=nameWithType> API is being updated to support the [Windows CNG cryptography APIs](/windows/desktop/SecCNG/cng-reference).</span></span> <span data-ttu-id="66a64-871">Önceki .NET Framework sürümleri, uygulamanın temeli olarak [Windows şifreleme API 'lerinin önceki bir sürümünde](/windows/desktop/SecCrypto/cryptography-portal) tamamıyla güvendi <xref:System.Security.Cryptography?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-871">Previous versions of the .NET Framework have relied entirely on an [earlier version of the Windows Cryptography APIs](/windows/desktop/SecCrypto/cryptography-portal) as the basis for the <xref:System.Security.Cryptography?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="66a64-872">Belirli uygulama kategorileri için önemli olan [modern şifreleme algoritmalarını](/windows/desktop/SecCNG/cng-features#suite-b-support)DESTEKLEDIĞINDEN CNG API 'sini desteklemeye yönelik isteklerdir.</span><span class="sxs-lookup"><span data-stu-id="66a64-872">We have had requests to support the CNG API, since it supports [modern cryptography algorithms](/windows/desktop/SecCNG/cng-features#suite-b-support), which are important for certain categories of apps.</span></span>

    <span data-ttu-id="66a64-873">.NET Framework 4,6, Windows CNG şifreleme API 'Lerini desteklemek için aşağıdaki yeni geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-873">.NET Framework 4.6 includes the following new enhancements to support the Windows CNG cryptography APIs:</span></span>

    - <span data-ttu-id="66a64-874">X509 sertifikaları için `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` ve mümkün olduğunda CAPI tabanlı bir uygulama `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` yerine CNG tabanlı bir uygulama döndüren genişletme yöntemleri kümesi.</span><span class="sxs-lookup"><span data-stu-id="66a64-874">A set of extension methods for X509 Certificates, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` and `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, that return a CNG-based implementation rather than a CAPI-based implementation when possible.</span></span> <span data-ttu-id="66a64-875">(Bazı smartcards, vb. için hala CAPı gerekir ve API geri dönüşü işler).</span><span class="sxs-lookup"><span data-stu-id="66a64-875">(Some smartcards, etc., still require CAPI, and the APIs handle the fallback).</span></span>

    - <span data-ttu-id="66a64-876"><xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType>RSA ALGORITMASıNıN CNG bir uygulamasını sağlayan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="66a64-876">The <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> class, which provides a CNG implementation of the RSA algorithm.</span></span>

    - <span data-ttu-id="66a64-877">Yaygın eylemlerin artık atama gerektirmemesi için RSA API geliştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="66a64-877">Enhancements to the RSA API so that common actions no longer require casting.</span></span> <span data-ttu-id="66a64-878">Örneğin, bir nesne kullanarak verileri şifrelemek, <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> .NET Framework önceki sürümlerinde aşağıdakiler gibi bir kod gerektirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-878">For example, encrypting data using an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> object requires code like the following in previous versions of .NET Framework.</span></span>

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      <span data-ttu-id="66a64-879">.NET Framework 4,6 ' deki yeni şifreleme API 'Lerini kullanan kod, dönüştürmeyi önlemek için aşağıdaki şekilde yeniden yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-879">Code that uses the new cryptography APIs in .NET Framework 4.6 can be rewritten as follows to avoid the cast.</span></span>

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - <span data-ttu-id="66a64-880">**Tarih ve saatleri Unix zamanına veya bu saatten dönüştürmeye yönelik destek**</span><span class="sxs-lookup"><span data-stu-id="66a64-880">**Support for converting dates and times to or from Unix time**</span></span>

    <span data-ttu-id="66a64-881"><xref:System.DateTimeOffset>Tarih ve saat değerlerini UNIX zamanından veya buradan dönüştürmeyi desteklemek için yapıya aşağıdaki yeni yöntemler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="66a64-881">The following new methods have been added to the <xref:System.DateTimeOffset> structure to support converting date and time values to or from Unix time:</span></span>

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - <span data-ttu-id="66a64-882">**Uyumluluk anahtarları**</span><span class="sxs-lookup"><span data-stu-id="66a64-882">**Compatibility switches**</span></span>

    <span data-ttu-id="66a64-883"><xref:System.AppContext>Sınıfı, kitaplık yazıcılarının kullanıcılarına yeni işlevsellik için Tekdüzen bir geri alma mekanizması sağlamasını sağlayan yeni bir uyumluluk özelliği ekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-883">The <xref:System.AppContext> class adds a new compatibility feature that enables library writers to provide a uniform opt-out mechanism for new functionality for their users.</span></span> <span data-ttu-id="66a64-884">Bir geri çevirme isteğini iletmek için bileşenler arasında gevşek olarak bağlanmış bir sözleşme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66a64-884">It establishes a loosely coupled contract between components in order to communicate an opt-out request.</span></span> <span data-ttu-id="66a64-885">Bu özellik, genellikle mevcut işlevlere bir değişiklik yapıldığında önemlidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-885">This capability is typically important when a change is made to existing functionality.</span></span> <span data-ttu-id="66a64-886">Buna karşılık, yeni işlevsellik için zaten örtük bir katılım vardır.</span><span class="sxs-lookup"><span data-stu-id="66a64-886">Conversely, there is already an implicit opt-in for new functionality.</span></span>

    <span data-ttu-id="66a64-887">İle <xref:System.AppContext> , kitaplıklar uyumluluk anahtarlarını tanımlar ve kullanıma sunar, ancak bunlara bağlı olan kod bu anahtarları kitaplık davranışını etkileyecek şekilde ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-887">With <xref:System.AppContext>, libraries define and expose compatibility switches, while code that depends on them can set those switches to affect the library behavior.</span></span> <span data-ttu-id="66a64-888">Varsayılan olarak, kitaplıklar yeni işlevselliği sağlar ve yalnızca, anahtar ayarlanmışsa (yani, önceki işlevleri sağlar) değiştirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-888">By default, libraries provide the new functionality, and they only alter it (that is, they provide the previous functionality) if the switch is set.</span></span>

    <span data-ttu-id="66a64-889">Bir uygulama (veya bir kitaplık), bağımlı bir kitaplığın tanımladığı bir anahtarın (her zaman bir değer olan) değerini bildirebilirler <xref:System.Boolean> .</span><span class="sxs-lookup"><span data-stu-id="66a64-889">An application (or a library) can declare the value of a switch (which is always a <xref:System.Boolean> value) that a dependent library defines.</span></span> <span data-ttu-id="66a64-890">Anahtar her zaman örtük olarak yapılır `false` .</span><span class="sxs-lookup"><span data-stu-id="66a64-890">The switch is always implicitly `false`.</span></span> <span data-ttu-id="66a64-891">Anahtar, izin vermek için ayarlanıyor `true` .</span><span class="sxs-lookup"><span data-stu-id="66a64-891">Setting the switch to `true` enables it.</span></span> <span data-ttu-id="66a64-892">Anahtarı açıkça ayarlamak `false` yeni davranışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-892">Explicitly setting the switch to `false` provides the new behavior.</span></span>

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    <span data-ttu-id="66a64-893">Kitaplığın, bir tüketicinin anahtar değerini bildirdiğinden ve daha sonra uygun şekilde davrandığından emin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="66a64-893">The library must check if a consumer has declared the value of the switch and then appropriately act on it.</span></span>

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

    <span data-ttu-id="66a64-894">Bir kitaplık tarafından kullanıma sunulan resmi bir sözleşme olduklarından, anahtarlar için tutarlı bir biçim kullanmak faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-894">It's beneficial to use a consistent format for switches, since they are a formal contract exposed by a library.</span></span> <span data-ttu-id="66a64-895">Aşağıda iki belirgin biçim verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-895">The following are two obvious formats.</span></span>

    - <span data-ttu-id="66a64-896">*Anahtar*. *ad alanı*. *SwitchName*</span><span class="sxs-lookup"><span data-stu-id="66a64-896">*Switch*.*namespace*.*switchname*</span></span>

    - <span data-ttu-id="66a64-897">*Anahtar*. *kitaplığı*. *SwitchName*</span><span class="sxs-lookup"><span data-stu-id="66a64-897">*Switch*.*library*.*switchname*</span></span>

  - <span data-ttu-id="66a64-898">**Görev tabanlı zaman uyumsuz düzende yapılan değişiklikler (TAP)**</span><span class="sxs-lookup"><span data-stu-id="66a64-898">**Changes to the task-based asynchronous pattern (TAP)**</span></span>

    <span data-ttu-id="66a64-899">.NET Framework 4,6 ' i hedefleyen uygulamalar için <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneler, çağıran iş parçacığının kültürünü ve Kullanıcı Arabirimi kültürünü miras alır.</span><span class="sxs-lookup"><span data-stu-id="66a64-899">For apps that target .NET Framework 4.6, <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects inherit the culture and UI culture of the calling thread.</span></span> <span data-ttu-id="66a64-900">.NET Framework önceki sürümlerini hedefleyen veya .NET Framework belirli bir sürümünü hedefmayan uygulamaların davranışı bundan etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="66a64-900">The behavior of apps that target previous versions of .NET Framework, or that do not target a specific version of .NET Framework, is unaffected.</span></span> <span data-ttu-id="66a64-901">Daha fazla bilgi için, sınıf konusunun "Kültür ve görev tabanlı zaman uyumsuz işlemler" bölümüne bakın <xref:System.Globalization.CultureInfo> .</span><span class="sxs-lookup"><span data-stu-id="66a64-901">For more information, see the "Culture and task-based asynchronous operations" section of the <xref:System.Globalization.CultureInfo> class topic.</span></span>

    <span data-ttu-id="66a64-902"><xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType>Sınıfı, bir yöntemi gibi belirli bir zaman uyumsuz Denetim akışında yerel olan çevresel verileri temsil etmenize olanak tanır `async` .</span><span class="sxs-lookup"><span data-stu-id="66a64-902">The <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> class allows you to represent ambient data that is local to a given asynchronous control flow, such as an `async` method.</span></span> <span data-ttu-id="66a64-903">İş parçacıkları arasında veri kalıcı hale getirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-903">It can be used to persist data across threads.</span></span> <span data-ttu-id="66a64-904">Ayrıca <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> , özellik açıkça değiştiği veya iş parçacığı bir bağlam geçişi ile karşılaştığından, ortam verilerinin her ne zaman değiştiğini belirten bir geri çağırma yöntemi tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-904">You can also define a callback method that is notified whenever the ambient data changes either because the <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> property was explicitly changed, or because the thread encountered a context transition.</span></span>

    <span data-ttu-id="66a64-905"><xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType> Görev tabanlı zaman uyumsuz modele (TAP), belirli bir durumdaki Tamamlanan görevleri döndürmek için,, ve, üç kolay yöntem eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-905">Three convenience methods, <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, have been added to the task-based asynchronous pattern (TAP) to return completed tasks in a particular state.</span></span>

    <span data-ttu-id="66a64-906"><xref:System.IO.Pipes.NamedPipeClientStream>Sınıfı artık, yeni ile zaman uyumsuz iletişimi desteklemektedir <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="66a64-906">The <xref:System.IO.Pipes.NamedPipeClientStream> class now supports asynchronous communication with its new <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>.</span></span> <span data-ttu-id="66a64-907">yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-907">method.</span></span>

  - <span data-ttu-id="66a64-908">**EventSource şimdi olay günlüğüne yazmayı destekliyor**</span><span class="sxs-lookup"><span data-stu-id="66a64-908">**EventSource now supports writing to the Event log**</span></span>

    <span data-ttu-id="66a64-909">Artık, <xref:System.Diagnostics.Tracing.EventSource> makinede oluşturulan mevcut ETW oturumlarına ek olarak yönetim veya işletimsel iletileri olay günlüğüne kaydetmek için sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-909">You now can use the <xref:System.Diagnostics.Tracing.EventSource> class to log administrative or operational messages to the event log, in addition to any existing ETW sessions created on the machine.</span></span> <span data-ttu-id="66a64-910">Geçmişte, bu işlevsellik için Microsoft. Diagnostics. Tracing. EventSource NuGet paketini kullanmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="66a64-910">In the past, you had to use the Microsoft.Diagnostics.Tracing.EventSource NuGet package for this functionality.</span></span> <span data-ttu-id="66a64-911">Bu işlevsellik artık 4,6 .NET Framework yerleşik olarak sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="66a64-911">This functionality is now built-into .NET Framework 4.6.</span></span>

    <span data-ttu-id="66a64-912">Hem NuGet paketi hem de .NET Framework 4,6 aşağıdaki özelliklerle güncelleştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="66a64-912">Both the NuGet package and .NET Framework 4.6 have been updated with the following features:</span></span>

    - <span data-ttu-id="66a64-913">**Dinamik olaylar**</span><span class="sxs-lookup"><span data-stu-id="66a64-913">**Dynamic events**</span></span>

      <span data-ttu-id="66a64-914">Olay yöntemi oluşturmadan "anında" tanımlanan olaylara izin verir.</span><span class="sxs-lookup"><span data-stu-id="66a64-914">Allows events defined "on the fly" without creating event methods.</span></span>

    - <span data-ttu-id="66a64-915">**Zengin yük**</span><span class="sxs-lookup"><span data-stu-id="66a64-915">**Rich payloads**</span></span>

      <span data-ttu-id="66a64-916">Özel olarak öznitelikli sınıfların ve dizilerin yanı sıra yük olarak geçirilecek ilkel türler sağlar</span><span class="sxs-lookup"><span data-stu-id="66a64-916">Allows specially attributed classes and arrays as well as primitive types to be passed as a payload</span></span>

    - <span data-ttu-id="66a64-917">**Etkinlik izleme**</span><span class="sxs-lookup"><span data-stu-id="66a64-917">**Activity tracking**</span></span>

      <span data-ttu-id="66a64-918">, Şu anda etkin olan tüm etkinlikleri temsil eden bir KIMLIK ile aralarında olayları etiketlemek için başlatma ve durdurma olaylarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="66a64-918">Causes Start and Stop events to tag events between them with an ID that represents all currently active activities.</span></span>

    <span data-ttu-id="66a64-919">Bu özellikleri desteklemek için, daha fazla yüklenmiş <xref:System.Diagnostics.Tracing.EventSource.Write%2A> yöntemi <xref:System.Diagnostics.Tracing.EventSource> sınıfına eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-919">To support these features, the overloaded <xref:System.Diagnostics.Tracing.EventSource.Write%2A> method has been added to the <xref:System.Diagnostics.Tracing.EventSource> class.</span></span>

- <span data-ttu-id="66a64-920">**Windows Presentation Foundation (WPF)**</span><span class="sxs-lookup"><span data-stu-id="66a64-920">**Windows Presentation Foundation (WPF)**</span></span>

  - <span data-ttu-id="66a64-921">**HDPı geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="66a64-921">**HDPI improvements**</span></span>

    <span data-ttu-id="66a64-922">WPF 'de HDPı desteği artık .NET Framework 4,6 ' de daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-922">HDPI support in WPF is now better in .NET Framework 4.6.</span></span> <span data-ttu-id="66a64-923">Kenarlıkların bulunduğu denetimlerde kırpma örneklerini azaltmak için yerleşim yuvarlama sırasında değişiklikler yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="66a64-923">Changes have been made to layout rounding to reduce instances of clipping in controls with borders.</span></span> <span data-ttu-id="66a64-924">Varsayılan olarak, bu özellik yalnızca <xref:System.Runtime.Versioning.TargetFrameworkAttribute> .NET Framework 4,6 olarak ayarlandıysa etkindir.</span><span class="sxs-lookup"><span data-stu-id="66a64-924">By default, this feature is enabled only if your <xref:System.Runtime.Versioning.TargetFrameworkAttribute> is set to .NET Framework 4.6.</span></span>  <span data-ttu-id="66a64-925">Framework 'ün önceki sürümlerini hedefleyen ancak .NET Framework 4,6 üzerinde çalışan uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek yeni davranışı kabul edebilir [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) :</span><span class="sxs-lookup"><span data-stu-id="66a64-925">Applications that target earlier versions of the framework but are running on .NET Framework 4.6 can opt in to the new behavior by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app.config file:</span></span>

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    <span data-ttu-id="66a64-926">Farklı DPı ayarlarına (çok DPı Kurulum) sahip birden çok izleyiciden oluşan WPF pencereleri, artık Blacked-Out bölgeleri olmadan tamamen işlenir.</span><span class="sxs-lookup"><span data-stu-id="66a64-926">WPF windows straddling multiple monitors with different DPI settings (Multi-DPI setup) are now completely rendered without blacked-out regions.</span></span> <span data-ttu-id="66a64-927">Bu `<appSettings>` yeni davranışı devre dışı bırakmak için app.config dosyanın bölümüne aşağıdaki satırı ekleyerek bu davranışı geri alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66a64-927">You can opt out of this behavior by adding the following line to the `<appSettings>` section of the app.config file to disable this new behavior:</span></span>

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    <span data-ttu-id="66a64-928">Üzerine DPı ayarı temelinde sağ imleci otomatik olarak yüklemek için destek eklenmiştir  <xref:System.Windows.Input.Cursor?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-928">Support for automatically loading the right cursor based on DPI setting has been added to  <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="66a64-929">**Dokunmatik daha iyidir**</span><span class="sxs-lookup"><span data-stu-id="66a64-929">**Touch is better**</span></span>

    <span data-ttu-id="66a64-930">İletişim [üzerindeki müşteri](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) raporları, .NET Framework 4,6 ' de öngörülemeyen davranış üretir.</span><span class="sxs-lookup"><span data-stu-id="66a64-930">Customer reports on [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) that touch produces unpredictable behavior have been addressed in .NET Framework 4.6.</span></span> <span data-ttu-id="66a64-931">Windows Mağazası uygulamaları ve WPF uygulamaları için çift dokunma eşiği artık Windows 8.1 ve üzeri sürümlerde aynıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-931">The double tap threshold for Windows Store applications and WPF applications is now the same in Windows 8.1 and above.</span></span>

  - <span data-ttu-id="66a64-932">**Saydam alt pencere desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-932">**Transparent child window support**</span></span>

    <span data-ttu-id="66a64-933">.NET Framework 4,6 ' de WPF, Windows 8.1 ve üzeri sürümlerde saydam alt pencereleri destekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-933">WPF in .NET Framework 4.6 supports transparent child windows in Windows 8.1 and above.</span></span> <span data-ttu-id="66a64-934">Bu, üst düzey Windows 'larınızı dikdörtgen olmayan ve şeffaf alt pencereler oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-934">This allows you to create non-rectangular and transparent child windows in your top-level windows.</span></span> <span data-ttu-id="66a64-935">Özelliğini olarak ayarlayarak bu özelliği etkinleştirebilirsiniz <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> `true` .</span><span class="sxs-lookup"><span data-stu-id="66a64-935">You can enable this feature by setting the <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> property to `true`.</span></span>

- <span data-ttu-id="66a64-936">**Windows Communication Foundation (WCF)**</span><span class="sxs-lookup"><span data-stu-id="66a64-936">**Windows Communication Foundation (WCF)**</span></span>

  - <span data-ttu-id="66a64-937">**SSL desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-937">**SSL support**</span></span>

    <span data-ttu-id="66a64-938">WCF, aktarım güvenliği ve istemci kimlik doğrulamasıyla NetTcp kullanılırken SSL 3,0 ve TLS 1,0 özelliklerine ek olarak SSL sürüm TLS 1,1 ve TLS 1,2 ' yi desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="66a64-938">WCF now supports SSL version TLS 1.1 and TLS 1.2, in addition to SSL 3.0 and TLS 1.0, when using NetTcp with transport security and client authentication.</span></span> <span data-ttu-id="66a64-939">Artık hangi protokolün kullanılacağını seçebilir veya eski daha az güvenli protokollerin devre dışı bırakılması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="66a64-939">It is now possible to select which protocol to use, or to disable old lesser secure protocols.</span></span> <span data-ttu-id="66a64-940">Bu, <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> özelliği ayarlanarak veya bir yapılandırma dosyasına aşağıdakiler eklenerek yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-940">This can be done either by setting the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> property or by adding the following to a configuration file.</span></span>

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

  - <span data-ttu-id="66a64-941">**Farklı HTTP bağlantıları kullanarak ileti gönderme**</span><span class="sxs-lookup"><span data-stu-id="66a64-941">**Sending messages using different HTTP connections**</span></span>

    <span data-ttu-id="66a64-942">WCF artık kullanıcıların, farklı temel HTTP bağlantıları kullanılarak belirli iletilerin gönderilmesini sağlamasına izin veriyor.</span><span class="sxs-lookup"><span data-stu-id="66a64-942">WCF now allows users to ensure certain messages are sent using different underlying HTTP connections.</span></span> <span data-ttu-id="66a64-943">Bunu yapmak için iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="66a64-943">There are two ways to do this:</span></span>

    - <span data-ttu-id="66a64-944">**Bağlantı grubu adı ön eki kullanma**</span><span class="sxs-lookup"><span data-stu-id="66a64-944">**Using a connection group name prefix**</span></span>

      <span data-ttu-id="66a64-945">Kullanıcılar, WCF 'nin bağlantı grubu adı için önek olarak kullanacağı bir dize belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-945">Users can specify a string that WCF will use as a prefix for the connection group name.</span></span> <span data-ttu-id="66a64-946">Farklı ön ekleri olan iki ileti, farklı temel HTTP bağlantıları kullanılarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-946">Two messages with different prefixes are sent using different underlying HTTP connections.</span></span> <span data-ttu-id="66a64-947">İletinin özelliğine bir anahtar/değer çifti ekleyerek ön eki ayarlarsınız <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-947">You set the prefix by adding a key/value pair to the message's <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="66a64-948">Anahtar "HttpTransportConnectionGroupNamePrefix"; değer, istenen önekidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-948">The key is "HttpTransportConnectionGroupNamePrefix"; the value is the desired prefix.</span></span>

    - <span data-ttu-id="66a64-949">**Farklı kanal fabrikaları kullanma**</span><span class="sxs-lookup"><span data-stu-id="66a64-949">**Using different channel factories**</span></span>

      <span data-ttu-id="66a64-950">Kullanıcılar ayrıca, farklı kanal fabrikaları tarafından oluşturulan kanallar kullanılarak gönderilen iletilerin farklı temel HTTP bağlantıları kullanmasını sağlayan bir özelliği etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-950">Users can also enable a feature that ensures that messages sent using channels created by different channel factories will use different underlying HTTP connections.</span></span> <span data-ttu-id="66a64-951">Bu özelliği etkinleştirmek için, kullanıcıların şunları yapmak üzere şunları ayarlaması gerekir `appSetting` `true` :</span><span class="sxs-lookup"><span data-stu-id="66a64-951">To enable this feature, users must set the following `appSetting` to `true`:</span></span>

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- <span data-ttu-id="66a64-952">**Windows Workflow Foundation (WWF)**</span><span class="sxs-lookup"><span data-stu-id="66a64-952">**Windows Workflow Foundation (WWF)**</span></span>

  <span data-ttu-id="66a64-953">Artık, isteği zaman aşımından önce bekleyen bir "protokol dışı" yer işareti olduğunda, bir iş akışı hizmetinin bir sıra dışı işlem isteğine açık olacağı saniye sayısını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-953">You can now specify the number of seconds a workflow service will hold on to an out-of-order operation request when there is an outstanding "non-protocol" bookmark before timing out the request.</span></span> <span data-ttu-id="66a64-954">"Protokol dışı" yer işareti, bekleyen alma etkinlikleriyle ilgili olmayan bir yer işaretidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-954">A "non-protocol" bookmark is a bookmark that is not related to outstanding Receive activities.</span></span> <span data-ttu-id="66a64-955">Bazı etkinlikler, kendi uygulamalarında protokol olmayan yer işaretleri oluşturur, bu nedenle protokol olmayan bir yer işaretinin mevcut olduğu açık olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-955">Some activities create non-protocol bookmarks within their implementation, so it may not be obvious that a non-protocol bookmark exists.</span></span> <span data-ttu-id="66a64-956">Bu durum ve seçim dahildir.</span><span class="sxs-lookup"><span data-stu-id="66a64-956">These include State and Pick.</span></span> <span data-ttu-id="66a64-957">Bu nedenle, bir durum makinesi ile uygulanan veya bir çekme etkinliği içeren bir iş akışı hizmetiniz varsa, muhtemelen protokol olmayan yer işaretlerine sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="66a64-957">So if you have a workflow service implemented with a state machine or containing a Pick activity, you will most likely have non-protocol bookmarks.</span></span> <span data-ttu-id="66a64-958">app.config dosyanızın bölümüne aşağıdakine benzer bir satır ekleyerek aralığı belirtirsiniz `appSettings` :</span><span class="sxs-lookup"><span data-stu-id="66a64-958">You specify the interval by adding a line like the following to the `appSettings` section of your app.config file:</span></span>

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  <span data-ttu-id="66a64-959">Varsayılan değer 60 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="66a64-959">The default value is 60 seconds.</span></span> <span data-ttu-id="66a64-960">`value`0 olarak ayarlanırsa, aşağıdaki gibi görünen metin ile bir hata vererek sıra dışı istekler anında reddedilir:</span><span class="sxs-lookup"><span data-stu-id="66a64-960">If `value` is set to 0, out-of-order requests are immediately rejected with a fault with text that looks like this:</span></span>

  ```console
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  <span data-ttu-id="66a64-961">Bu, bir sıra dışı işlem iletisi alındığında ve protokol olmayan yer işaretleri yoksa aldığınız mesajdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-961">This is the same message that you receive if an out-of-order operation message is received and there are no non-protocol bookmarks.</span></span>

  <span data-ttu-id="66a64-962">`FilterResumeTimeoutInSeconds`Öğe değeri sıfır değilse, protokol olmayan yer işaretleri vardır ve zaman aşımı aralığı sona erdiğinde, işlem zaman aşımı iletisiyle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="66a64-962">If the value of the `FilterResumeTimeoutInSeconds` element is non-zero, there are non-protocol bookmarks, and the timeout interval expires, the operation fails with a timeout message.</span></span>

- <span data-ttu-id="66a64-963">**İşlemler**</span><span class="sxs-lookup"><span data-stu-id="66a64-963">**Transactions**</span></span>

  <span data-ttu-id="66a64-964">Artık, öğesinden türetilme özel durumunun oluşturulmasına neden olan işlem için dağıtılmış işlem tanımlayıcıyı ekleyebilirsiniz <xref:System.Transactions.TransactionException> .</span><span class="sxs-lookup"><span data-stu-id="66a64-964">You can now include the distributed transaction identifier for the transaction that has caused an exception derived from <xref:System.Transactions.TransactionException> to be thrown.</span></span> <span data-ttu-id="66a64-965">Bunu, app.config dosyanızın bölümüne aşağıdaki anahtarı ekleyerek yapabilirsiniz `appSettings` :</span><span class="sxs-lookup"><span data-stu-id="66a64-965">You do this by adding the following key to the `appSettings` section of your app.config file:</span></span>

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  <span data-ttu-id="66a64-966">`false` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="66a64-966">The default value is `false`.</span></span>

- <span data-ttu-id="66a64-967">**Ağ**</span><span class="sxs-lookup"><span data-stu-id="66a64-967">**Networking**</span></span>

  - <span data-ttu-id="66a64-968">**Yuva yeniden kullanımı**</span><span class="sxs-lookup"><span data-stu-id="66a64-968">**Socket reuse**</span></span>

    <span data-ttu-id="66a64-969">Windows 10, giden TCP bağlantıları için yerel bağlantı noktalarını yeniden kullanarak makine kaynaklarından daha iyi şekilde yararlanmasına yönelik yeni bir yüksek ölçeklenebilirlik ağ algoritması içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-969">Windows 10 includes a new high-scalability networking algorithm that makes better use of machine resources by reusing local ports for outbound TCP connections.</span></span> <span data-ttu-id="66a64-970">.NET Framework 4,6 yeni algoritmayı destekleyerek, .NET uygulamalarının yeni davranıştan yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-970">.NET Framework 4.6 supports the new algorithm, enabling .NET apps to take advantage of the new behavior.</span></span> <span data-ttu-id="66a64-971">Önceki Windows sürümlerinde, bir hizmetin ölçeklenebilirliğini, yük altında bağlantı noktası tükenmesi olmasına neden olarak sınırlayan yapay bir eşzamanlı bağlantı sınırı (genellikle 16.384) vardı.</span><span class="sxs-lookup"><span data-stu-id="66a64-971">In previous versions of Windows, there was an artificial concurrent connection limit (typically 16,384, the default size of the dynamic port range), which could limit the scalability of a service by causing port exhaustion when under load.</span></span>

    <span data-ttu-id="66a64-972">.NET Framework 4,6 ' de, bağlantı noktası yeniden kullanımını etkinleştirmek için iki API eklenmiştir. Bu, eşzamanlı bağlantılarda 64 KB sınırını etkili bir şekilde kaldırır:</span><span class="sxs-lookup"><span data-stu-id="66a64-972">In .NET Framework 4.6, two APIs have been added to enable port reuse, which effectively removes the 64 KB limit on concurrent connections:</span></span>

    - <span data-ttu-id="66a64-973"><xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType>Sabit listesi değeri.</span><span class="sxs-lookup"><span data-stu-id="66a64-973">The <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> enumeration value.</span></span>

    - <span data-ttu-id="66a64-974"><xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType>Özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-974">The <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="66a64-975">Varsayılan olarak,, <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> `false` `HWRPortReuseOnSocketBind` `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` kayıt defteri anahtarının değeri 0x1 olarak ayarlanmadığı takdirde özelliği olur.</span><span class="sxs-lookup"><span data-stu-id="66a64-975">By default, the <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property is `false` unless the `HWRPortReuseOnSocketBind` value of the `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` registry key is set to 0x1.</span></span> <span data-ttu-id="66a64-976">HTTP bağlantılarında yerel bağlantı noktası yeniden kullanımını etkinleştirmek için <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> özelliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="66a64-976">To enable local port reuse on HTTP connections, set the <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="66a64-977">Bu, tüm giden TCP yuvası bağlantılarının <xref:System.Net.Http.HttpClient> ve <xref:System.Net.HttpWebRequest> yerel bağlantı noktası yeniden kullanımını sağlayan yeni bir Windows 10 yuva seçeneği [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options)kullanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="66a64-977">This causes all outgoing TCP socket connections from <xref:System.Net.Http.HttpClient> and <xref:System.Net.HttpWebRequest> to use a new Windows 10 socket option, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), that enables local port reuse.</span></span>

    <span data-ttu-id="66a64-978">Yalnızca bir yuva uygulaması yazan geliştiriciler, <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> bağlama sırasında giden yuvaların yerel bağlantı noktalarını yeniden kullanabilmesi için gibi bir yöntemi çağırırken seçeneğini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-978">Developers writing a sockets-only application can specify the <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> option when calling a method such as <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> so that outbound sockets reuse local ports during binding.</span></span>

  - <span data-ttu-id="66a64-979">**Uluslararası etki alanı adları ve puni kodu desteği**</span><span class="sxs-lookup"><span data-stu-id="66a64-979">**Support for international domain names and PunyCode**</span></span>

    <span data-ttu-id="66a64-980"><xref:System.Uri.IdnHost%2A> <xref:System.Uri> Uluslararası etki alanı adlarını ve zayıf kodu daha iyi desteklemek için sınıfına yeni bir özellik eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-980">A new property, <xref:System.Uri.IdnHost%2A>, has been added to the <xref:System.Uri> class to better support international domain names and PunyCode.</span></span>

- <span data-ttu-id="66a64-981">**Windows Forms Denetimlerinde yeniden boyutlandırma.**</span><span class="sxs-lookup"><span data-stu-id="66a64-981">**Resizing in Windows Forms controls.**</span></span>

  <span data-ttu-id="66a64-982">Bu özellik .NET Framework 4,6 ' de,,, <xref:System.Windows.Forms.DomainUpDown> <xref:System.Windows.Forms.NumericUpDown> <xref:System.Windows.Forms.DataGridViewComboBoxColumn> <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.ToolStripSplitButton> türlerini ve <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> bir çizerken kullanılan özelliği tarafından belirtilen dikdörtgeni <xref:System.Drawing.Design.UITypeEditor> içermesi için genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-982">This feature has been expanded in .NET Framework 4.6 to include the <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.ToolStripSplitButton> types and the rectangle specified by the <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> property used when drawing a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

  <span data-ttu-id="66a64-983">Bu bir katılım özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-983">This is an opt-in feature.</span></span> <span data-ttu-id="66a64-984">Etkinleştirmek için, `EnableWindowsFormsHighDpiAutoResizing` öğesini `true` uygulama yapılandırma (app.config) dosyasında olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="66a64-984">To enable it, set the `EnableWindowsFormsHighDpiAutoResizing` element to `true` in the application configuration (app.config) file:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- <span data-ttu-id="66a64-985">**Kod sayfası kodlamaları için destek**</span><span class="sxs-lookup"><span data-stu-id="66a64-985">**Support for code page encodings**</span></span>

  <span data-ttu-id="66a64-986">.NET Core öncelikle Unicode kodlamaları destekler ve varsayılan olarak, kod sayfası kodlamaları için sınırlı destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-986">.NET Core primarily supports the Unicode encodings and by default provides limited support for code page encodings.</span></span> <span data-ttu-id="66a64-987">Kod sayfası kodlamalarını yöntemi ile kaydederek .NET Core 'da .NET Framework, ancak desteklenmeyen kod sayfası kodlamaları için destek ekleyebilirsiniz <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-987">You can add support for code page encodings available in .NET Framework but unsupported in .NET Core by registering code page encodings with the <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="66a64-988">Daha fazla bilgi için bkz. <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66a64-988">For more information, see <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="66a64-989">**.NET Native**</span><span class="sxs-lookup"><span data-stu-id="66a64-989">**.NET Native**</span></span>

  <span data-ttu-id="66a64-990">.NET Core 'u hedefleyen ve C# veya Visual Basic yazılmış Windows 10 için Windows uygulamaları, uygulamaları Il yerine yerel koda derleyen yeni bir teknolojiden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-990">Windows apps for Windows 10 that target .NET Core and are written in C# or Visual Basic can take advantage of a new technology that compiles apps to native code rather than IL.</span></span> <span data-ttu-id="66a64-991">Daha hızlı başlatma ve yürütme süreleriyle nitelenen uygulamalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66a64-991">They produce apps characterized by faster startup and execution times.</span></span> <span data-ttu-id="66a64-992">Daha fazla bilgi için bkz. [.NET Native uygulamalar derleme](../net-native/index.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-992">For more information, see [Compiling Apps with .NET Native](../net-native/index.md).</span></span> <span data-ttu-id="66a64-993">Hem JıT derleme hem de NGEN 'ten farklı olan .NET Native genel bir bakış için ve kodunuz için ne anlama geldiğini, bkz. [.NET Native ve derleme](../net-native/net-native-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-993">For an overview of .NET Native that examines how it differs from both JIT compilation and NGEN and what that means for your code, see [.NET Native and Compilation](../net-native/net-native-and-compilation.md).</span></span>

  <span data-ttu-id="66a64-994">Uygulamalarınız, Visual Studio 2015 veya sonraki bir sürümü ile derlerken varsayılan olarak yerel koda derlenir.</span><span class="sxs-lookup"><span data-stu-id="66a64-994">Your apps are compiled to native code by default when you compile them with Visual Studio 2015 or later.</span></span> <span data-ttu-id="66a64-995">Daha fazla bilgi için bkz. [.NET Native kullanmaya](../net-native/getting-started-with-net-native.md)başlama.</span><span class="sxs-lookup"><span data-stu-id="66a64-995">For more information, see [Getting Started with .NET Native](../net-native/getting-started-with-net-native.md).</span></span>

  <span data-ttu-id="66a64-996">.NET Native uygulamalarında hata ayıklamayı desteklemek için, yönetilmeyen hata ayıklama API 'sine bir dizi yeni arabirim ve listeleme eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-996">To support debugging .NET Native apps, a number of new interfaces and enumerations have been added to the unmanaged debugging API.</span></span> <span data-ttu-id="66a64-997">Daha fazla bilgi için bkz. [hata ayıklama (YÖNETILMEYEN API Başvurusu)](../unmanaged-api/debugging/index.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="66a64-997">For more information, see the [Debugging (Unmanaged API Reference)](../unmanaged-api/debugging/index.md) topic.</span></span>

- <span data-ttu-id="66a64-998">**Açık kaynaklı .NET Framework paketleri**</span><span class="sxs-lookup"><span data-stu-id="66a64-998">**Open-source .NET Framework packages**</span></span>

  <span data-ttu-id="66a64-999">Sabit koleksiyonlar, [SIMD API 'leri](https://www.nuget.org/packages/Microsoft.Bcl.Simd)ve ad alanında bulunan gibi ağ API 'leri gibi .NET Core paketleri <xref:System.Net.Http> artık [GitHub](https://github.com/)'da açık kaynak paketleri olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-999">.NET Core packages such as the immutable collections, [SIMD APIs](https://www.nuget.org/packages/Microsoft.Bcl.Simd), and networking APIs such as those found in the <xref:System.Net.Http> namespace are now available as open-source packages on [GitHub](https://github.com/).</span></span> <span data-ttu-id="66a64-1000">Koda erişmek için [GitHub 'da .net](https://github.com/dotnet/runtime)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-1000">To access the code, see [.NET on GitHub](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="66a64-1001">Daha fazla bilgi ve bu paketlere nasıl katkıda bulunabileceğiniz hakkında daha fazla bilgi için bkz. [GitHub 'da .net, .NET ana sayfasına](https://github.com/dotnet/home) [giriş](../../core/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1001">For more information and how to contribute to these packages, see [Introduction to .NET](../../core/introduction.md), [.NET Home Page on GitHub](https://github.com/dotnet/home).</span></span>

<a name="v452"></a>

## <a name="whats-new-in-net-framework-452"></a><span data-ttu-id="66a64-1002">.NET Framework 4.5.2 yenilikleri</span><span class="sxs-lookup"><span data-stu-id="66a64-1002">What's new in .NET Framework 4.5.2</span></span>

- <span data-ttu-id="66a64-1003">**ASP.NET uygulamaları için yeni API 'Ler.**</span><span class="sxs-lookup"><span data-stu-id="66a64-1003">**New APIs for ASP.NET apps.**</span></span> <span data-ttu-id="66a64-1004">Yeni <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> ve <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> yöntemleri yanıt üstbilgilerini ve durum kodunu, yanıt istemci uygulamasına boşaltılmakta olduğundan incelemenizi ve değiştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1004">The new <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> and <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> methods let you inspect and modify response headers and status code as the response is being flushed to the client app.</span></span> <span data-ttu-id="66a64-1005">Ve olayları yerine bu yöntemleri kullanmayı düşünün <xref:System.Web.HttpApplication.PreSendRequestHeaders> <xref:System.Web.HttpApplication.PreSendRequestContent> ; bunlar daha verimli ve güvenilirdir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1005">Consider using these methods instead of the <xref:System.Web.HttpApplication.PreSendRequestHeaders> and <xref:System.Web.HttpApplication.PreSendRequestContent> events; they are more efficient and reliable.</span></span>

  <span data-ttu-id="66a64-1006"><xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType>Yöntemi, küçük arka plan iş öğelerini zamanlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1006">The <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> method lets you schedule small background work items.</span></span> <span data-ttu-id="66a64-1007">ASP.NET bu öğeleri izler ve tüm arka plan iş öğeleri tamamlanana kadar IIS 'nin çalışan işlemini aniden sonlandırmasını önler.</span><span class="sxs-lookup"><span data-stu-id="66a64-1007">ASP.NET tracks these items and prevents IIS from abruptly terminating the worker process until all background work items have completed.</span></span> <span data-ttu-id="66a64-1008">Bu yöntem, ASP.NET tarafından yönetilen bir uygulama etki alanı dışında çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1008">This method can't be called outside an ASP.NET managed app domain.</span></span>

  <span data-ttu-id="66a64-1009">New <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> ve <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> Properties, yanıt üstbilgilerinin yazılıp yazılmadığını belirten Boole değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="66a64-1009">The new <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> and <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> properties return Boolean values that indicate whether the response headers have been written.</span></span> <span data-ttu-id="66a64-1010">Bu özellikleri, <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (üstbilgiler yazılmışsa özel durumlar oluşturur) gibi API 'lere yapılan çağrıların başarılı olacağını doğrulamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1010">You can use these properties to make sure that calls to APIs such as <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (which throw exceptions if the headers have been written) will succeed.</span></span>

- <span data-ttu-id="66a64-1011">**Windows Forms Denetimlerinde yeniden boyutlandırma.**</span><span class="sxs-lookup"><span data-stu-id="66a64-1011">**Resizing in Windows Forms controls.**</span></span> <span data-ttu-id="66a64-1012">Bu özellik genişletildi.</span><span class="sxs-lookup"><span data-stu-id="66a64-1012">This feature has been expanded.</span></span> <span data-ttu-id="66a64-1013">Artık, aşağıdaki ek denetimlerin bileşenlerini yeniden boyutlandırmak için sistem DPı ayarını kullanabilirsiniz (örneğin, Birleşik giriş kutularındaki aşağı açılan ok):</span><span class="sxs-lookup"><span data-stu-id="66a64-1013">You can now use the system DPI setting to resize components of the following additional controls (for example, the drop-down arrow in combo boxes):</span></span>

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  <span data-ttu-id="66a64-1014">Bu bir katılım özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1014">This is an opt-in feature.</span></span> <span data-ttu-id="66a64-1015">Etkinleştirmek için, `EnableWindowsFormsHighDpiAutoResizing` öğesini `true` uygulama yapılandırma (app.config) dosyasında olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="66a64-1015">To enable it, set the `EnableWindowsFormsHighDpiAutoResizing` element to `true` in the application configuration (app.config) file:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- <span data-ttu-id="66a64-1016">**Yeni iş akışı özelliği.**</span><span class="sxs-lookup"><span data-stu-id="66a64-1016">**New workflow feature.**</span></span> <span data-ttu-id="66a64-1017">Yöntemini kullanan bir kaynak yöneticisi <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> (ve bu nedenle <xref:System.Transactions.IPromotableSinglePhaseNotification> arabirimi uygulamak) <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> aşağıdakileri istemek için New metodunu kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="66a64-1017">A resource manager that's using the <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> method (and therefore implementing the <xref:System.Transactions.IPromotableSinglePhaseNotification> interface) can use the new <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> method to request the following:</span></span>

  - <span data-ttu-id="66a64-1018">İşlemi bir Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) işlemine yükseltin.</span><span class="sxs-lookup"><span data-stu-id="66a64-1018">Promote the transaction to a Microsoft Distributed Transaction Coordinator (MSDTC) transaction.</span></span>

  - <span data-ttu-id="66a64-1019"><xref:System.Transactions.IPromotableSinglePhaseNotification> <xref:System.Transactions.ISinglePhaseNotification> Tek aşamalı işlemeleri destekleyen dayanıklı bir kayıt olan ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="66a64-1019">Replace <xref:System.Transactions.IPromotableSinglePhaseNotification> with an <xref:System.Transactions.ISinglePhaseNotification>, which is a durable enlistment that supports single phase commits.</span></span>

  <span data-ttu-id="66a64-1020">Bu, aynı uygulama etki alanı içinde yapılabilir ve yükseltmeyi gerçekleştirmek üzere MSDTC ile etkileşimde bulunmak için ek yönetilmeyen kod gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="66a64-1020">This can be done within the same app domain, and doesn't require any extra unmanaged code to interact with MSDTC to perform the promotion.</span></span> <span data-ttu-id="66a64-1021">Yeni yöntem yalnızca <xref:System.Transactions?displayProperty=nameWithType> <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` , öğesinden promotable kaydı tarafından uygulanan yönteme bekleyen bir çağrı olduğunda çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1021">The new method can be called only when there's an outstanding call from <xref:System.Transactions?displayProperty=nameWithType> to the <xref:System.Transactions.IPromotableSinglePhaseNotification>`Promote` method that's implemented by the promotable enlistment.</span></span>

- <span data-ttu-id="66a64-1022">**Profil oluşturma geliştirmeleri.**</span><span class="sxs-lookup"><span data-stu-id="66a64-1022">**Profiling improvements.**</span></span> <span data-ttu-id="66a64-1023">Aşağıdaki yeni yönetilmeyen profil oluşturma API 'Leri daha sağlam profil oluşturma sağlar:</span><span class="sxs-lookup"><span data-stu-id="66a64-1023">The following new unmanaged profiling APIs provide more robust profiling:</span></span>

  - [<span data-ttu-id="66a64-1024">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="66a64-1024">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [<span data-ttu-id="66a64-1025">COR_PRF_HIGH_MONITOR Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="66a64-1025">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [<span data-ttu-id="66a64-1026">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a64-1026">GetAssemblyReferences Method</span></span>](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [<span data-ttu-id="66a64-1027">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a64-1027">GetEventMask2 Method</span></span>](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [<span data-ttu-id="66a64-1028">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a64-1028">SetEventMask2 Method</span></span>](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [<span data-ttu-id="66a64-1029">AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a64-1029">AddAssemblyReference Method</span></span>](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  <span data-ttu-id="66a64-1030">Önceki `ICorProfiler` uygulamalar bağımlı derlemelerin geç yüklenmesini destekliyordu.</span><span class="sxs-lookup"><span data-stu-id="66a64-1030">Previous `ICorProfiler` implementations supported lazy loading of dependent assemblies.</span></span> <span data-ttu-id="66a64-1031">Yeni profil oluşturma API 'Leri, uygulama tam olarak başlatıldıktan sonra yüklenmesi yerine, profil oluşturucu tarafından doğrudan yüklenebilir olarak eklenen bağımlı derlemeler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1031">The new profiling APIs require dependent assemblies that are injected by the profiler to be loadable immediately, instead of being loaded after the app is fully initialized.</span></span> <span data-ttu-id="66a64-1032">Bu değişiklik, var olan API 'lerin kullanıcılarını etkilemez `ICorProfiler` .</span><span class="sxs-lookup"><span data-stu-id="66a64-1032">This change doesn't affect users of the existing `ICorProfiler` APIs.</span></span>

- <span data-ttu-id="66a64-1033">**Hata ayıklama geliştirmeleri.**</span><span class="sxs-lookup"><span data-stu-id="66a64-1033">**Debugging improvements.**</span></span> <span data-ttu-id="66a64-1034">Aşağıdaki yeni yönetilmeyen hata ayıklama API 'Leri, bir profil Oluşturucu ile daha iyi tümleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1034">The following new unmanaged debugging APIs provide better integration with a profiler.</span></span> <span data-ttu-id="66a64-1035">Artık Profiler tarafından yerleştirilen meta verilere, Ayrıca, döküm hata ayıklaması sırasında derleyici ReJIT istekleri tarafından oluşturulan yerel değişkenlere ve koda erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1035">You can now access metadata inserted by the profiler as well as local variables and code produced by compiler ReJIT requests when dump debugging.</span></span>

  - [<span data-ttu-id="66a64-1036">SetWriteableMetadataUpdateMode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a64-1036">SetWriteableMetadataUpdateMode Method</span></span>](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [<span data-ttu-id="66a64-1037">EnumerateLocalVariablesEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a64-1037">EnumerateLocalVariablesEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [<span data-ttu-id="66a64-1038">GetLocalVariableEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a64-1038">GetLocalVariableEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [<span data-ttu-id="66a64-1039">GetCodeEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a64-1039">GetCodeEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [<span data-ttu-id="66a64-1040">GetActiveReJitRequestILCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a64-1040">GetActiveReJitRequestILCode Method</span></span>](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [<span data-ttu-id="66a64-1041">GetInstrumentedILMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66a64-1041">GetInstrumentedILMap Method</span></span>](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- <span data-ttu-id="66a64-1042">**Olay izleme değişiklikleri.**</span><span class="sxs-lookup"><span data-stu-id="66a64-1042">**Event tracing changes.**</span></span> <span data-ttu-id="66a64-1043">.NET Framework 4.5.2, daha büyük bir yüzey alanı için işlem dışı, Windows için olay Izleme (ETW) tabanlı etkinlik izleme imkanı sunar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1043">.NET Framework 4.5.2 enables out-of-process, Event Tracing for Windows (ETW)-based activity tracing for a larger surface area.</span></span> <span data-ttu-id="66a64-1044">Bu, gelişmiş güç yönetimi (APM) satıcılarının, iş parçacıkları arasındaki bireysel isteklerin ve etkinliklerin maliyetlerini doğru bir şekilde izleyen hafif araçlar sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1044">This enables Advanced Power Management (APM) vendors to provide lightweight tools that accurately track the costs of individual requests and activities that cross threads.</span></span>  <span data-ttu-id="66a64-1045">Bu olaylar yalnızca ETW denetleyicileri etkinleştirilse tetiklenir; Bu nedenle, değişiklikler önceden yazılmış ETW kodunu veya ETW devre dışı ile çalışan kodu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="66a64-1045">These events are raised only when ETW controllers enable them; therefore, the changes don't affect previously written ETW code or code that runs with ETW disabled.</span></span>

- <span data-ttu-id="66a64-1046">**Bir işlemi yükseltme ve dayanıklı bir kayda dönüştürme**</span><span class="sxs-lookup"><span data-stu-id="66a64-1046">**Promoting a transaction and converting it to a durable enlistment**</span></span>

  <span data-ttu-id="66a64-1047"><xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> .NET Framework 4.5.2 ve 4,6 ' ye yeni bir API eklendi:</span><span class="sxs-lookup"><span data-stu-id="66a64-1047"><xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> is a new API added to .NET Framework 4.5.2 and 4.6:</span></span>

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

  <span data-ttu-id="66a64-1048">Yöntemi, yöntemi tarafından daha önce oluşturulmuş bir kayıt tarafından <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> , yöntemine yanıt olarak kullanılabilir <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1048">The method may be used by an enlistment that was previously created by <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> in response to the <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="66a64-1049">Bu `System.Transactions` işlem, işlemi BIR MSDTC işlemine yükseltmeyi ve promotable listesini dayanıklı bir listeye "dönüştürmek" ister.</span><span class="sxs-lookup"><span data-stu-id="66a64-1049">It asks `System.Transactions` to promote the transaction to an MSDTC transaction and to "convert" the promotable enlistment to a durable enlistment.</span></span> <span data-ttu-id="66a64-1050">Bu yöntem başarıyla tamamlandıktan sonra, <xref:System.Transactions.IPromotableSinglePhaseNotification> arabirime artık tarafından başvurulmayacak `System.Transactions` ve gelecekteki tüm bildirimler verilen <xref:System.Transactions.ISinglePhaseNotification> arabirime gönderilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1050">After this method completes successfully, the <xref:System.Transactions.IPromotableSinglePhaseNotification> interface will no longer be referenced by `System.Transactions`, and any future notifications will arrive on the provided <xref:System.Transactions.ISinglePhaseNotification> interface.</span></span> <span data-ttu-id="66a64-1051">Söz konusu kayıt, işlem günlüğü ve kurtarmayı destekleyen dayanıklı bir liste olarak davranmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-1051">The enlistment in question must act as a durable enlistment, supporting transaction logging and recovery.</span></span> <span data-ttu-id="66a64-1052"><xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>Ayrıntılar için bkz..</span><span class="sxs-lookup"><span data-stu-id="66a64-1052">Refer to <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> for details.</span></span> <span data-ttu-id="66a64-1053">Ayrıca, kayıt desteği gerekir <xref:System.Transactions.ISinglePhaseNotification> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1053">In addition, the enlistment must support <xref:System.Transactions.ISinglePhaseNotification>.</span></span>  <span data-ttu-id="66a64-1054">Bu yöntem, *yalnızca* bir çağrı işlenirken çağrılabilir <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1054">This method can *only* be called while processing an <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> call.</span></span> <span data-ttu-id="66a64-1055">Böyle değilse, bir <xref:System.Transactions.TransactionException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="66a64-1055">If that is not the case, a <xref:System.Transactions.TransactionException> exception is thrown.</span></span>

<a name="v451"></a>

## <a name="whats-new-in-net-framework-451"></a><span data-ttu-id="66a64-1056">.NET Framework 4.5.1 yenilikleri</span><span class="sxs-lookup"><span data-stu-id="66a64-1056">What's new in .NET Framework 4.5.1</span></span>

<span data-ttu-id="66a64-1057">**Nisan 2014 güncelleştirmeleri**:</span><span class="sxs-lookup"><span data-stu-id="66a64-1057">**April 2014 updates**:</span></span>

- <span data-ttu-id="66a64-1058">[Visual Studio 2013 güncelleştirme 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) , bu senaryoları desteklemek Için taşınabilir sınıf kitaplığı şablonlarına yönelik güncelleştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-1058">[Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) includes updates to the Portable Class Library templates to support these scenarios:</span></span>

  - <span data-ttu-id="66a64-1059">Windows 8.1, Windows Phone 8,1 ve Windows Phone Silverlight 8,1 ' i hedefleyen taşınabilir kitaplıklarda Windows Çalışma Zamanı API 'Leri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1059">You can use Windows Runtime APIs in portable libraries that target Windows 8.1, Windows Phone 8.1, and Windows Phone Silverlight 8.1.</span></span>

  - <span data-ttu-id="66a64-1060">Windows 8.1 veya Windows Phone 8,1 ' i hedefliyorsanız taşınabilir kitaplıklara XAML (Windows. UI. XAML türleri) ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1060">You can include XAML (Windows.UI.XAML types) in portable libraries when you target Windows 8.1 or Windows Phone 8.1.</span></span> <span data-ttu-id="66a64-1061">Şu XAML şablonları desteklenir: boş sayfa, kaynak sözlüğü, şablonlu denetim ve Kullanıcı denetimi.</span><span class="sxs-lookup"><span data-stu-id="66a64-1061">The following XAML templates are supported:  Blank Page, Resource Dictionary, Templated Control, and User Control.</span></span>

  - <span data-ttu-id="66a64-1062">Windows 8.1 ve Windows Phone 8,1 ' i hedefleyen Mağaza uygulamalarında kullanılmak üzere taşınabilir bir Windows Çalışma Zamanı bileşeni (. winmd dosyası) oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1062">You can create a portable Windows Runtime component (.winmd file) for use in Store apps that target Windows 8.1 and Windows Phone 8.1.</span></span>

  - <span data-ttu-id="66a64-1063">Bir Windows Mağazası veya Windows Phone depolama sınıfı kitaplığını taşınabilir bir sınıf kitaplığı gibi yeniden hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1063">You can retarget a Windows Store or Windows Phone Store class library like a Portable Class Library.</span></span>

  <span data-ttu-id="66a64-1064">Bu değişiklikler hakkında daha fazla bilgi için bkz. [taşınabilir sınıf kitaplığı](../cross-platform/portable-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1064">For more information about these changes, see [Portable Class Library](../cross-platform/portable-class-library.md).</span></span>

- <span data-ttu-id="66a64-1065">.NET Framework içerik kümesi artık, Windows uygulamaları oluşturmaya ve dağıtmaya yönelik bir ön derleme teknolojisi olan .NET Native belgelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1065">The .NET Framework content set now includes documentation for .NET Native, which is a precompilation technology for building and deploying Windows apps.</span></span> <span data-ttu-id="66a64-1066">.NET Native uygulamalarınızı, daha iyi performans için, ara dil (IL) yerine yerel koda doğrudan derler.</span><span class="sxs-lookup"><span data-stu-id="66a64-1066">.NET Native compiles your apps directly to native code, rather than to intermediate language (IL), for better performance.</span></span> <span data-ttu-id="66a64-1067">Ayrıntılar için bkz. [.NET Native uygulamalar derleme](../net-native/index.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1067">For details, see [Compiling Apps with .NET Native](../net-native/index.md).</span></span>

- <span data-ttu-id="66a64-1068">[.NET Framework başvuru kaynağı](https://referencesource.microsoft.com/) yeni bir gözatma deneyimi ve gelişmiş işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1068">The [.NET Framework Reference Source](https://referencesource.microsoft.com/) provides a new browsing experience and enhanced functionality.</span></span> <span data-ttu-id="66a64-1069">Artık .NET Framework kaynak koduna göz atabilir, çevrimdışı görüntüleme [başvurusunu indirebilir](https://referencesource.microsoft.com/download.html) ve hata ayıklama sırasında kaynaklarda (yayama ve güncelleştirmeler dahil) ilerme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1069">You can now browse through the .NET Framework source code online, [download the reference](https://referencesource.microsoft.com/download.html) for offline viewing, and step through the sources (including patches and updates) during debugging.</span></span> <span data-ttu-id="66a64-1070">Daha fazla bilgi için bkz. [.net başvuru kaynağı için yeni bir görünüm](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/)olan blog girişi.</span><span class="sxs-lookup"><span data-stu-id="66a64-1070">For more information, see the blog entry [A new look for .NET Reference Source](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).</span></span>

<span data-ttu-id="66a64-1071">.NET Framework 4.5.1 ' deki temel sınıflardaki yeni özellikler ve geliştirmeler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-1071">New features and enhancements in the base classes in .NET Framework 4.5.1 include:</span></span>

- <span data-ttu-id="66a64-1072">Derlemeler için otomatik bağlama yeniden yönlendirme.</span><span class="sxs-lookup"><span data-stu-id="66a64-1072">Automatic binding redirection for assemblies.</span></span> <span data-ttu-id="66a64-1073">Visual Studio 2013 başlayarak, .NET Framework 4.5.1 hedefleyen bir uygulama derlerken, uygulamanız veya bileşenleri aynı derlemenin birden çok sürümüne başvurduğu zaman bağlama yeniden yönlendirmeleri uygulama yapılandırma dosyasına eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1073">Starting with Visual Studio 2013, when you compile an app that targets .NET Framework 4.5.1, binding redirects may be added to the app configuration file if your app or its components reference multiple versions of the same assembly.</span></span> <span data-ttu-id="66a64-1074">Ayrıca, daha eski .NET Framework sürümlerini hedefleyen projeler için bu özelliği etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1074">You can also enable this feature for projects that target older versions of .NET Framework.</span></span> <span data-ttu-id="66a64-1075">Daha fazla bilgi için bkz. [nasıl yapılır: otomatik bağlama yeniden yönlendirmeyi etkinleştirme ve devre dışı bırakma](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1075">For more information, see [How to: Enable and Disable Automatic Binding Redirection](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).</span></span>

- <span data-ttu-id="66a64-1076">Geliştiricilerin sunucu ve bulut uygulamalarının performansını geliştirmesine yardımcı olmak için tanılama bilgilerini toplama özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1076">Ability to collect diagnostics information to help developers improve the performance of server and cloud applications.</span></span> <span data-ttu-id="66a64-1077">Daha fazla bilgi için, <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> sınıfındaki ve <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> yöntemlerine bakın <xref:System.Diagnostics.Tracing.EventSource> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1077">For more information, see the <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> and <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> methods in the <xref:System.Diagnostics.Tracing.EventSource> class.</span></span>

- <span data-ttu-id="66a64-1078">Çöp toplama sırasında büyük nesne yığınını (LOH) açık bir şekilde sıkıştırabilme.</span><span class="sxs-lookup"><span data-stu-id="66a64-1078">Ability to explicitly compact the large object heap (LOH) during garbage collection.</span></span> <span data-ttu-id="66a64-1079">Daha fazla bilgi için bkz <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> . özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1079">For more information, see the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="66a64-1080">.NET Framework güncelleştirmesinden sonra ASP.NET uygulama askıya alma, çok çekirdekli JıT geliştirmeleri ve daha hızlı uygulama başlatma gibi ek performans geliştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="66a64-1080">Additional performance improvements such as ASP.NET app suspension, multi-core JIT improvements, and faster app startup after a .NET Framework update.</span></span> <span data-ttu-id="66a64-1081">Ayrıntılar için bkz. [.NET Framework 4.5.1 ilanı](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) ve [ASP.net App Suspend](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) blog gönderisi.</span><span class="sxs-lookup"><span data-stu-id="66a64-1081">For details, see the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) and the [ASP.NET app suspend](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) blog post.</span></span>

<span data-ttu-id="66a64-1082">Windows Forms iyileştirmeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="66a64-1082">Improvements to Windows Forms include:</span></span>

- <span data-ttu-id="66a64-1083">Windows Forms Denetimlerinde yeniden boyutlandırma.</span><span class="sxs-lookup"><span data-stu-id="66a64-1083">Resizing in Windows Forms controls.</span></span> <span data-ttu-id="66a64-1084">Uygulamanızın uygulama yapılandırma dosyasında (app.config) bir girdiyle seçerek denetim bileşenlerini yeniden boyutlandırmak için sistem DPı ayarını kullanabilirsiniz (örneğin, bir özellik kılavuzunda görünen simgeler).</span><span class="sxs-lookup"><span data-stu-id="66a64-1084">You can use the system DPI setting to resize components of controls (for example, the icons that appear in a property grid) by opting in with an entry in the application configuration file (app.config) for your app.</span></span> <span data-ttu-id="66a64-1085">Bu özellik şu anda aşağıdaki Windows Forms Denetimlerinde desteklenmektedir:</span><span class="sxs-lookup"><span data-stu-id="66a64-1085">This feature is currently supported in the following Windows Forms controls:</span></span>

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  - <span data-ttu-id="66a64-1086">Uygulamasının bazı yönleri <xref:System.Windows.Forms.DataGridView> (desteklenen ek denetimler için bkz. [4.5.2 sürümündeki yeni özellikler](#v452) )</span><span class="sxs-lookup"><span data-stu-id="66a64-1086">Some aspects of the <xref:System.Windows.Forms.DataGridView> (see [new features in 4.5.2](#v452) for additional controls supported)</span></span>

  <span data-ttu-id="66a64-1087">Bu özelliği etkinleştirmek için \<appSettings> yapılandırma dosyasına (app.config) yeni bir öğe ekleyin ve `EnableWindowsFormsHighDpiAutoResizing` öğeyi şu şekilde ayarlayın `true` :</span><span class="sxs-lookup"><span data-stu-id="66a64-1087">To enable this feature, add a new \<appSettings> element to the configuration file (app.config) and set the `EnableWindowsFormsHighDpiAutoResizing` element to `true`:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

<span data-ttu-id="66a64-1088">Visual Studio 2013 .NET Framework uygulamalarınızın hata ayıklaması sırasında iyileştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="66a64-1088">Improvements when debugging your .NET Framework apps in Visual Studio 2013 include:</span></span>

- <span data-ttu-id="66a64-1089">Visual Studio hata ayıklayıcısındaki değerleri döndürün.</span><span class="sxs-lookup"><span data-stu-id="66a64-1089">Return values in the Visual Studio debugger.</span></span> <span data-ttu-id="66a64-1090">Visual Studio 2013 yönetilen bir uygulamada hata ayıklarken, oto 'Lar penceresi yöntemlerin dönüş türlerini ve değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="66a64-1090">When you debug a managed app in Visual Studio 2013, the Autos window displays return types and values for methods.</span></span> <span data-ttu-id="66a64-1091">Bu bilgiler Masaüstü, Windows Mağazası ve Windows Phone uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1091">This information is available for desktop, Windows Store, and Windows Phone apps.</span></span> <span data-ttu-id="66a64-1092">Daha fazla bilgi için bkz. [Yöntem çağrılarının dönüş değerlerini inceleme](/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="66a64-1092">For more information, see [Examine return values of method calls](/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).</span></span>

- <span data-ttu-id="66a64-1093">64 bit uygulamalar için Düzenle ve devam et.</span><span class="sxs-lookup"><span data-stu-id="66a64-1093">Edit and Continue for 64-bit apps.</span></span> <span data-ttu-id="66a64-1094">Visual Studio 2013 Masaüstü, Windows Mağazası ve Windows Phone 64 bitlik yönetilen uygulamalar için Düzenle ve devam et özelliğini destekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-1094">Visual Studio 2013 supports the Edit and Continue feature for 64-bit managed apps for desktop, Windows Store, and Windows Phone.</span></span> <span data-ttu-id="66a64-1095">Mevcut sınırlamalar hem 32-bit hem de 64-bit uygulamalar için geçerlidir ( [desteklenen kod değişiklikleri (C#)](/visualstudio/debugger/supported-code-changes-csharp) makalesinin son bölümüne bakın).</span><span class="sxs-lookup"><span data-stu-id="66a64-1095">The existing limitations remain in effect for both 32-bit and 64-bit apps (see the last section of the [Supported Code Changes (C#)](/visualstudio/debugger/supported-code-changes-csharp) article).</span></span>

- <span data-ttu-id="66a64-1096">Zaman uyumsuz olarak algılayan hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="66a64-1096">Async-aware debugging.</span></span> <span data-ttu-id="66a64-1097">Visual Studio 2013 zaman uyumsuz uygulamalarda hata ayıklamayı kolaylaştırmak için, çağrı yığını zaman uyumsuz programlamayı desteklemek için derleyiciler tarafından belirtilen altyapı kodunu gizler ve mantıksal program yürütmesini daha açık bir şekilde izleyebilmeniz için mantıksal üst çerçevelerde zincirler.</span><span class="sxs-lookup"><span data-stu-id="66a64-1097">To make it easier to debug asynchronous apps in Visual Studio 2013, the call stack hides the infrastructure code provided by compilers to support asynchronous programming, and also chains in logical parent frames so you can follow logical program execution more clearly.</span></span> <span data-ttu-id="66a64-1098">Bir Görevler penceresi, paralel görevler penceresinin yerini alır ve belirli bir kesme noktasıyla ilgili görevleri görüntüler ve ayrıca, şu anda etkin olan veya uygulamada zamanlanan diğer görevleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="66a64-1098">A Tasks window replaces the Parallel Tasks window and displays tasks that relate to a particular breakpoint, and also displays any other tasks that are currently active or scheduled in the app.</span></span> <span data-ttu-id="66a64-1099">Bu özellik hakkında bilgi edinmek için, [.NET Framework 4.5.1 duyurusunun](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/)"zaman uyumsuz algılayan hata ayıklama" bölümünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1099">You can read about this feature in the "Async-aware debugging" section of the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span></span>

- <span data-ttu-id="66a64-1100">Windows Çalışma Zamanı bileşenleri için daha iyi özel durum desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1100">Better exception support for Windows Runtime components.</span></span> <span data-ttu-id="66a64-1101">Windows 8.1, Windows Mağazası uygulamalarından kaynaklanan özel durumlar, özel duruma neden olan hata hakkındaki bilgileri, dil sınırları boyunca korur.</span><span class="sxs-lookup"><span data-stu-id="66a64-1101">In Windows 8.1, exceptions that arise from Windows Store apps preserve information about the error that caused the exception, even across language boundaries.</span></span> <span data-ttu-id="66a64-1102">Bu özellik hakkında bilgi edinmek için [.NET Framework 4.5.1 duyurusunun](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/)"Windows Mağazası uygulama geliştirme" bölümünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1102">You can read about this feature in the "Windows Store app development" section of the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span></span>

<span data-ttu-id="66a64-1103">Visual Studio 2013 başlayarak, Windows 8. x mağaza uygulamalarını ve masaüstü uygulamalarını en iyi duruma getirmek için [yönetilen profil temelli Iyileştirme aracı 'nı (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1103">Starting with Visual Studio 2013, you can use the [Managed Profile Guided Optimization Tool (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) to optimize Windows 8.x Store apps as well as desktop apps.</span></span>

<span data-ttu-id="66a64-1104">ASP.NET 4.5.1 içindeki yeni özellikler için bkz. [Visual Studio 2013 Sürüm notları ASP.NET and Web Tools](/aspnet/visual-studio/overview/2013/release-notes).</span><span class="sxs-lookup"><span data-stu-id="66a64-1104">For new features in ASP.NET 4.5.1, see [ASP.NET and Web Tools for Visual Studio 2013 Release Notes](/aspnet/visual-studio/overview/2013/release-notes).</span></span>

<a name="v45"></a>

## <a name="whats-new-in-net-framework-45"></a><span data-ttu-id="66a64-1105">.NET Framework 4,5 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="66a64-1105">What's new in .NET Framework 4.5</span></span>

### <a name="base-classes"></a><span data-ttu-id="66a64-1106">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="66a64-1106">Base classes</span></span>

- <span data-ttu-id="66a64-1107">Dağıtım sırasında .NET Framework 4 uygulamalarını algılayıp kapatarak sistem yeniden başlatmaları azaltma özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1107">Ability to reduce system restarts by detecting and closing .NET Framework 4 applications during deployment.</span></span> <span data-ttu-id="66a64-1108">Bkz. [.NET Framework 4,5 yüklemeleri sırasında sistem yeniden başlatmaları azaltma](../deployment/reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1108">See [Reducing System Restarts During .NET Framework 4.5 Installations](../deployment/reducing-system-restarts.md).</span></span>

- <span data-ttu-id="66a64-1109">64-bit platformlarda 2 gigabayttan (GB) daha büyük diziler için destek.</span><span class="sxs-lookup"><span data-stu-id="66a64-1109">Support for arrays that are larger than 2 gigabytes (GB) on 64-bit platforms.</span></span> <span data-ttu-id="66a64-1110">Bu özellik uygulama yapılandırma dosyasında etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1110">This feature can be enabled in the application configuration file.</span></span> <span data-ttu-id="66a64-1111">Nesne boyutu ve dizi boyutu üzerindeki diğer kısıtlamaları da listeleyen [ \<gcAllowVeryLargeObjects> öğesine](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-1111">See the [\<gcAllowVeryLargeObjects> element](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), which also lists other restrictions on object size and array size.</span></span>

- <span data-ttu-id="66a64-1112">Sunucular için arka plan atık toplama ile daha iyi performans.</span><span class="sxs-lookup"><span data-stu-id="66a64-1112">Better performance through background garbage collection for servers.</span></span> <span data-ttu-id="66a64-1113">.NET Framework 4,5 ' de sunucu çöp toplamayı kullandığınızda, arka plan atık toplama otomatik olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1113">When you use server garbage collection in .NET Framework 4.5, background garbage collection is automatically enabled.</span></span> <span data-ttu-id="66a64-1114">[Çöp toplama temelleri](../../standard/garbage-collection/fundamentals.md) konusunun arka plan sunucusu çöp toplama bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-1114">See the Background Server Garbage Collection section of the [Fundamentals of Garbage Collection](../../standard/garbage-collection/fundamentals.md) topic.</span></span>

- <span data-ttu-id="66a64-1115">Arka plan tam zamanında (JıT) derleme, isteğe bağlı olarak, uygulama performansını artırmak için çok çekirdekli işlemcilerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1115">Background just-in-time (JIT) compilation, which is optionally available on multi-core processors to improve application performance.</span></span> <span data-ttu-id="66a64-1116">Bkz. <xref:System.Runtime.ProfileOptimization>.</span><span class="sxs-lookup"><span data-stu-id="66a64-1116">See <xref:System.Runtime.ProfileOptimization>.</span></span>

- <span data-ttu-id="66a64-1117">Normal ifade altyapısının zaman aşımına uğramadan önce normal ifadeyi çözmeyi ne kadar süreyle deneyeceğini sınırlayabilme olanağı. Bkz <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> . özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1117">Ability to limit how long the regular expression engine will attempt to resolve a regular expression before it times out. See the <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="66a64-1118">Bir uygulama etki alanı için varsayılan kültürü tanımlama özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1118">Ability to define the default culture for an application domain.</span></span> <span data-ttu-id="66a64-1119">Sınıfına bakın <xref:System.Globalization.CultureInfo> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1119">See the <xref:System.Globalization.CultureInfo> class.</span></span>

- <span data-ttu-id="66a64-1120">Unicode (UTF-16) kodlaması için konsol desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1120">Console support for Unicode (UTF-16) encoding.</span></span> <span data-ttu-id="66a64-1121">Sınıfına bakın <xref:System.Console> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1121">See the <xref:System.Console> class.</span></span>

- <span data-ttu-id="66a64-1122">Kültürel dize sıralaması ve karşılaştırma verilerinin sürümü oluşturma desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1122">Support for versioning of cultural string ordering and comparison data.</span></span> <span data-ttu-id="66a64-1123">Sınıfına bakın <xref:System.Globalization.SortVersion> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1123">See the <xref:System.Globalization.SortVersion> class.</span></span>

- <span data-ttu-id="66a64-1124">Kaynakları alırken daha iyi performans.</span><span class="sxs-lookup"><span data-stu-id="66a64-1124">Better performance when retrieving resources.</span></span> <span data-ttu-id="66a64-1125">Bkz. [kaynakları paketleme ve dağıtma](../resources/packaging-and-deploying-resources-in-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1125">See [Packaging and Deploying Resources](../resources/packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

- <span data-ttu-id="66a64-1126">Sıkıştırılmış bir dosyanın boyutunu azaltmak için ZIP sıkıştırma geliştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="66a64-1126">Zip compression improvements to reduce the size of a compressed file.</span></span> <span data-ttu-id="66a64-1127">Bkz <xref:System.IO.Compression?displayProperty=nameWithType> . ad alanı.</span><span class="sxs-lookup"><span data-stu-id="66a64-1127">See the <xref:System.IO.Compression?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="66a64-1128">Bir yansıma bağlamını, sınıfı aracılığıyla varsayılan yansıma davranışını geçersiz kılacak şekilde özelleştirebilme <xref:System.Reflection.Context.CustomReflectionContext> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1128">Ability to customize a reflection context to override default reflection behavior through the <xref:System.Reflection.Context.CustomReflectionContext> class.</span></span>

- <span data-ttu-id="66a64-1129">Sınıf Windows 8 ' de kullanıldığında, uygulamalar (ıDNA) standardında uluslararası etki alanı adlarının 2008 sürümü için destek <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1129">Support for the 2008 version of the Internationalized Domain Names in Applications (IDNA) standard when the <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> class is used  on Windows 8.</span></span>

- <span data-ttu-id="66a64-1130">Windows 8 ' de .NET Framework kullanıldığında, Unicode 6,0 uygulayan işletim sistemine dize karşılaştırması temsili.</span><span class="sxs-lookup"><span data-stu-id="66a64-1130">Delegation of string comparison to the operating system, which implements Unicode 6.0, when the .NET Framework is used on Windows 8.</span></span> <span data-ttu-id="66a64-1131">Diğer platformlarda çalışırken .NET Framework, Unicode 5. x uygulayan kendi dize karşılaştırma verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1131">When running on other platforms, the .NET Framework includes its own string comparison data, which implements Unicode 5.x.</span></span> <span data-ttu-id="66a64-1132"><xref:System.String>Sınıfının sınıfı ve açıklamalar bölümüne bakın <xref:System.Globalization.SortVersion> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1132">See the <xref:System.String> class and the Remarks section of the <xref:System.Globalization.SortVersion> class.</span></span>

- <span data-ttu-id="66a64-1133">Her uygulama etki alanı temelinde dizeler için karma kodları hesaplama özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1133">Ability to compute the hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="66a64-1134">Bkz. [ \<UseRandomizedStringHashAlgorithm> öğesi](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1134">See [\<UseRandomizedStringHashAlgorithm> Element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span></span>

- <span data-ttu-id="66a64-1135">Ve sınıfları arasında bölünmüş tür yansıtma desteği <xref:System.Type> <xref:System.Reflection.TypeInfo> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1135">Type reflection support split between <xref:System.Type> and <xref:System.Reflection.TypeInfo> classes.</span></span> <span data-ttu-id="66a64-1136">Bkz. [Windows Mağazası uygulamaları için .NET Framework yansıtma](../reflection-and-codedom/reflection-for-windows-store-apps.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1136">See [Reflection in the .NET Framework for Windows Store Apps](../reflection-and-codedom/reflection-for-windows-store-apps.md).</span></span>

### <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="66a64-1137">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="66a64-1137">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="66a64-1138">.NET Framework 4,5 ' de, Managed Extensibility Framework (MEF) aşağıdaki yeni özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="66a64-1138">In .NET Framework 4.5, the Managed Extensibility Framework (MEF) provides the following new features:</span></span>

- <span data-ttu-id="66a64-1139">Genel türler için destek.</span><span class="sxs-lookup"><span data-stu-id="66a64-1139">Support for generic types.</span></span>

- <span data-ttu-id="66a64-1140">Öznitelikler yerine adlandırma kurallarına göre parçalar oluşturmanıza olanak sağlayan kural tabanlı programlama modeli.</span><span class="sxs-lookup"><span data-stu-id="66a64-1140">Convention-based programming model that enables you to create parts based on naming conventions rather than attributes.</span></span>

- <span data-ttu-id="66a64-1141">Birden çok kapsam.</span><span class="sxs-lookup"><span data-stu-id="66a64-1141">Multiple scopes.</span></span>

- <span data-ttu-id="66a64-1142">Windows 8. x Mağazası uygulamaları oluştururken kullanabileceğiniz MEF alt kümesi.</span><span class="sxs-lookup"><span data-stu-id="66a64-1142">A subset of MEF that you can use when you create Windows 8.x Store apps.</span></span> <span data-ttu-id="66a64-1143">Bu alt küme NuGet galerisinden [indirilebilir bir paket](https://www.nuget.org/packages/Microsoft.Composition) olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1143">This subset is available as a [downloadable package](https://www.nuget.org/packages/Microsoft.Composition) from the NuGet Gallery.</span></span> <span data-ttu-id="66a64-1144">Paketi yüklemek için, projenizi Visual Studio 'da açın, **Proje** menüsünden **NuGet Paketlerini Yönet** ' i seçin ve paketi çevrimiçi olarak arayın `Microsoft.Composition` .</span><span class="sxs-lookup"><span data-stu-id="66a64-1144">To install the package, open your project in Visual Studio, choose **Manage NuGet Packages** from the **Project** menu, and search online for the `Microsoft.Composition` package.</span></span>

<span data-ttu-id="66a64-1145">Daha fazla bilgi için bkz. [Managed Extensibility Framework (MEF)](../mef/index.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1145">For more information, see [Managed Extensibility Framework (MEF)](../mef/index.md).</span></span>

### <a name="asynchronous-file-operations"></a><span data-ttu-id="66a64-1146">Zaman uyumsuz dosya işlemleri</span><span class="sxs-lookup"><span data-stu-id="66a64-1146">Asynchronous file operations</span></span>

<span data-ttu-id="66a64-1147">.NET Framework 4,5 ' de, C# ve Visual Basic dillerine yeni zaman uyumsuz özellikler eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1147">In .NET Framework 4.5, new asynchronous features were added to the C# and Visual Basic languages.</span></span> <span data-ttu-id="66a64-1148">Bu özellikler, zaman uyumsuz işlemleri gerçekleştirmek için görev tabanlı bir model ekler.</span><span class="sxs-lookup"><span data-stu-id="66a64-1148">These features add a task-based model for performing asynchronous operations.</span></span> <span data-ttu-id="66a64-1149">Bu yeni modeli kullanmak için g/ç sınıflarında zaman uyumsuz yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="66a64-1149">To use this new model, use the asynchronous methods in the I/O classes.</span></span> <span data-ttu-id="66a64-1150">Bkz. [zaman uyumsuz dosya g/ç](../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1150">See [Asynchronous File I/O](../../standard/io/asynchronous-file-i-o.md).</span></span>

<a name="tools"></a>

### <a name="tools"></a><span data-ttu-id="66a64-1151">Araçlar</span><span class="sxs-lookup"><span data-stu-id="66a64-1151">Tools</span></span>

<span data-ttu-id="66a64-1152">.NET Framework 4,5 ' de, kaynak dosya Oluşturucu (Resgen.exe), bir .NET Framework derlemesine gömülü bir. resources dosyasından Windows 8. x Mağazası uygulamaları kullanmak için bir. resw dosyası oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1152">In .NET Framework 4.5, Resource File Generator (Resgen.exe) enables you to create a .resw file for use in Windows 8.x Store apps from a .resources file embedded in a .NET Framework assembly.</span></span> <span data-ttu-id="66a64-1153">Daha fazla bilgi için bkz. [Resgen.exe (kaynak dosya Oluşturucu)](../tools/resgen-exe-resource-file-generator.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1153">For more information, see [Resgen.exe (Resource File Generator)](../tools/resgen-exe-resource-file-generator.md).</span></span>

<span data-ttu-id="66a64-1154">Yönetilen profil temelli Iyileştirme (Mpgo.exe), yerel görüntü derlemelerini iyileştirerek uygulama başlangıç süresini, bellek kullanımını (çalışma kümesi boyutu) ve aktarım hızını iyileştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1154">Managed Profile Guided Optimization (Mpgo.exe) enables you to improve application startup time, memory utilization (working set size), and throughput by optimizing native image assemblies.</span></span> <span data-ttu-id="66a64-1155">Komut satırı aracı, yerel görüntü uygulama derlemeleri için profil verileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="66a64-1155">The command-line tool generates profile data for native image application assemblies.</span></span> <span data-ttu-id="66a64-1156">Bkz. [Mpgo.exe (yönetilen profil temelli Iyileştirme aracı)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1156">See [Mpgo.exe (Managed Profile Guided Optimization Tool)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md).</span></span> <span data-ttu-id="66a64-1157">Visual Studio 2013 başlayarak, Windows 8. x mağaza uygulamalarını ve masaüstü uygulamalarını en iyi hale getirebilmeniz için Mpgo.exe kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1157">Starting with Visual Studio 2013, you can use Mpgo.exe to optimize Windows 8.x Store apps as well as desktop apps.</span></span>

<a name="parallel"></a>

### <a name="parallel-computing"></a><span data-ttu-id="66a64-1158">Paralel bilgi işlem</span><span class="sxs-lookup"><span data-stu-id="66a64-1158">Parallel computing</span></span>

<span data-ttu-id="66a64-1159">.NET Framework 4,5, paralel bilgi işlem için çeşitli yeni özellikler ve iyileştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1159">.NET Framework 4.5 provides several new features and improvements for parallel computing.</span></span> <span data-ttu-id="66a64-1160">Bunlar, geliştirilmiş performans, artırılmış denetim, zaman uyumsuz programlama için geliştirilmiş destek, yeni bir veri akışı kitaplığı ve paralel hata ayıklama ve performans analizi için geliştirilmiş destek içerir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1160">These include improved performance, increased control, improved support for asynchronous programming, a new dataflow library, and improved support for parallel debugging and performance analysis.</span></span> <span data-ttu-id="66a64-1161">.NET blogu ile paralel programlamada [.NET Framework 4,5 ' de paralellik için](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) yenilikler bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="66a64-1161">See the entry [What's New for Parallelism in .NET Framework 4.5](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) in the Parallel Programming with .NET blog.</span></span>

<a name="web"></a>

### <a name="web"></a><span data-ttu-id="66a64-1162">Web</span><span class="sxs-lookup"><span data-stu-id="66a64-1162">Web</span></span>

<span data-ttu-id="66a64-1163">Web Forms, WebSocket desteği, zaman uyumsuz işleyiciler, performans geliştirmeleri ve diğer birçok özellik için ASP.NET 4,5 ve 4.5.1 model bağlama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="66a64-1163">ASP.NET 4.5 and 4.5.1 add model binding for Web Forms, WebSocket support, asynchronous handlers, performance enhancements, and many other features.</span></span> <span data-ttu-id="66a64-1164">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="66a64-1164">For more information, see the following resources:</span></span>

- <span data-ttu-id="66a64-1165">[ASP.NET 4,5 ve Visual Studio 2012](/previous-versions/aspnet/hh420390(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="66a64-1165">[ASP.NET 4.5 and Visual Studio 2012](/previous-versions/aspnet/hh420390(v=vs.110))</span></span>

- [<span data-ttu-id="66a64-1166">Visual Studio 2013 için ASP.NET and Web Tools Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="66a64-1166">ASP.NET and Web Tools for Visual Studio 2013 Release Notes</span></span>](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking"></a><span data-ttu-id="66a64-1167">İşlemleri <a name="networking"></a></span><span class="sxs-lookup"><span data-stu-id="66a64-1167">Networking <a name="networking"></a></span></span>

<span data-ttu-id="66a64-1168">.NET Framework 4,5, HTTP uygulamaları için yeni bir programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1168">.NET Framework 4.5 provides a new programming interface for HTTP applications.</span></span> <span data-ttu-id="66a64-1169">Daha fazla bilgi için bkz. yeni <xref:System.Net.Http?displayProperty=nameWithType> ve <xref:System.Net.Http.Headers?displayProperty=nameWithType> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="66a64-1169">For more information, see the new <xref:System.Net.Http?displayProperty=nameWithType> and <xref:System.Net.Http.Headers?displayProperty=nameWithType> namespaces.</span></span>

<span data-ttu-id="66a64-1170">Ayrıca, mevcut ve ilgili sınıfları kullanarak bir WebSocket bağlantısını kabul etmek ve bunlarla etkileşim kurmak için yeni bir programlama arabirimi de mevcuttur <xref:System.Net.HttpListener> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1170">Support is also included for a new programming interface for accepting and interacting with a WebSocket connection by using the existing <xref:System.Net.HttpListener> and related classes.</span></span> <span data-ttu-id="66a64-1171">Daha fazla bilgi için, bkz <xref:System.Net.WebSockets> . yeni ad alanı ve <xref:System.Net.HttpListener> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="66a64-1171">For more information, see the new <xref:System.Net.WebSockets> namespace and the <xref:System.Net.HttpListener> class.</span></span>

<span data-ttu-id="66a64-1172">Ayrıca, .NET Framework 4,5 aşağıdaki ağ geliştirmelerini içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-1172">In addition, .NET Framework 4.5 includes the following networking improvements:</span></span>

- <span data-ttu-id="66a64-1173">RFC uyumlu URI desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1173">RFC-compliant URI support.</span></span> <span data-ttu-id="66a64-1174">Daha fazla bilgi için bkz <xref:System.Uri> . ve ilgili sınıflar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1174">For more information, see <xref:System.Uri> and related classes.</span></span>

- <span data-ttu-id="66a64-1175">Uluslararası etki alanı adı (ıDN) ayrıştırma desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1175">Support for Internationalized Domain Name (IDN) parsing.</span></span> <span data-ttu-id="66a64-1176">Daha fazla bilgi için bkz <xref:System.Uri> . ve ilgili sınıflar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1176">For more information, see <xref:System.Uri> and related classes.</span></span>

- <span data-ttu-id="66a64-1177">E-posta adresi uluslararası duruma getirme (EAı) desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1177">Support for Email Address Internationalization (EAI).</span></span> <span data-ttu-id="66a64-1178">Daha fazla bilgi için bkz <xref:System.Net.Mail> . ad alanı.</span><span class="sxs-lookup"><span data-stu-id="66a64-1178">For more information, see the <xref:System.Net.Mail> namespace.</span></span>

- <span data-ttu-id="66a64-1179">Geliştirilmiş IPv6 desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1179">Improved IPv6 support.</span></span> <span data-ttu-id="66a64-1180">Daha fazla bilgi için bkz <xref:System.Net.NetworkInformation> . ad alanı.</span><span class="sxs-lookup"><span data-stu-id="66a64-1180">For more information, see the <xref:System.Net.NetworkInformation> namespace.</span></span>

- <span data-ttu-id="66a64-1181">Çift modlu yuva desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1181">Dual-mode socket support.</span></span> <span data-ttu-id="66a64-1182">Daha fazla bilgi için bkz <xref:System.Net.Sockets.Socket> . ve <xref:System.Net.Sockets.TcpListener> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="66a64-1182">For more information, see the <xref:System.Net.Sockets.Socket> and <xref:System.Net.Sockets.TcpListener> classes.</span></span>

<a name="client"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="66a64-1183">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="66a64-1183">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="66a64-1184">.NET Framework 4,5 ' de, Windows Presentation Foundation (WPF) aşağıdaki alanlarda değişiklikler ve iyileştirmeler içerir:</span><span class="sxs-lookup"><span data-stu-id="66a64-1184">In .NET Framework 4.5, Windows Presentation Foundation (WPF) contains changes and improvements in the following areas:</span></span>

- <span data-ttu-id="66a64-1185"><xref:System.Windows.Controls.Ribbon.Ribbon>Hızlı erişim araç çubuğu, uygulama menüsü ve sekmeler barındıran bir şerit kullanıcı arabirimi uygulamanıza olanak sağlayan yeni denetim.</span><span class="sxs-lookup"><span data-stu-id="66a64-1185">The new <xref:System.Windows.Controls.Ribbon.Ribbon> control, which enables you to implement a ribbon user interface that hosts a Quick Access Toolbar, Application Menu, and tabs.</span></span>

- <span data-ttu-id="66a64-1186"><xref:System.ComponentModel.INotifyDataErrorInfo>Zaman uyumlu ve zaman uyumsuz veri doğrulamayı destekleyen yeni arabirim.</span><span class="sxs-lookup"><span data-stu-id="66a64-1186">The new <xref:System.ComponentModel.INotifyDataErrorInfo> interface, which supports synchronous and asynchronous data validation.</span></span>

- <span data-ttu-id="66a64-1187">Ve sınıfları için yeni <xref:System.Windows.Controls.VirtualizingPanel> Özellikler <xref:System.Windows.Threading.Dispatcher> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1187">New features for the <xref:System.Windows.Controls.VirtualizingPanel> and <xref:System.Windows.Threading.Dispatcher> classes.</span></span>

- <span data-ttu-id="66a64-1188">Büyük düzeyde gruplandırılmış verilerin görüntülenirken ve Kullanıcı arabirimi olmayan iş parçacıklarında koleksiyonlara erişerek gelişmiş performans.</span><span class="sxs-lookup"><span data-stu-id="66a64-1188">Improved performance when displaying large sets of grouped data, and by accessing collections on non-UI threads.</span></span>

- <span data-ttu-id="66a64-1189">Statik özelliklere veri bağlama, arabirimi uygulayan özel türlere veri bağlama <xref:System.Reflection.ICustomTypeProvider> ve veri bağlama bilgilerinin bir bağlama ifadesinden alınması.</span><span class="sxs-lookup"><span data-stu-id="66a64-1189">Data binding to static properties, data binding to custom types that implement the <xref:System.Reflection.ICustomTypeProvider> interface, and retrieval of data binding information from a binding expression.</span></span>

- <span data-ttu-id="66a64-1190">Değerler değiştiğinde verileri yeniden konumlandırma (canlı şekillendirme).</span><span class="sxs-lookup"><span data-stu-id="66a64-1190">Repositioning of data as the values change (live shaping).</span></span>

- <span data-ttu-id="66a64-1191">Bir öğe kapsayıcısının veri bağlamının bağlantısının kesilmesi olup olmadığını denetleme özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1191">Ability to check whether the data context for an item container is disconnected.</span></span>

- <span data-ttu-id="66a64-1192">Özellik değişiklikleri ve veri kaynağı güncelleştirmeleri arasında geçmesi gereken süre miktarını ayarlama yeteneği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1192">Ability to set the amount of time that should elapse between property changes and data source updates.</span></span>

- <span data-ttu-id="66a64-1193">Zayıf olay desenleri uygulama desteği geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="66a64-1193">Improved support for implementing weak event patterns.</span></span> <span data-ttu-id="66a64-1194">Ayrıca, olaylar artık işaretleme uzantılarını kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1194">Also, events can now accept markup extensions.</span></span>

<a name="windows_communication_foundation"></a>

### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="66a64-1195">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="66a64-1195">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="66a64-1196">.NET Framework 4,5 ' de, Windows Communication Foundation (WCF) uygulamaları yazmayı ve bakımını daha kolay hale getirmek için aşağıdaki özellikler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="66a64-1196">In .NET Framework 4.5, the following features have been added to make it simpler to write and maintain Windows Communication Foundation (WCF) applications:</span></span>

- <span data-ttu-id="66a64-1197">Oluşturulan yapılandırma dosyalarının basitleştirmesi.</span><span class="sxs-lookup"><span data-stu-id="66a64-1197">Simplification of generated configuration files.</span></span>

- <span data-ttu-id="66a64-1198">Sözleşmenin ilk geliştirmesi için destek.</span><span class="sxs-lookup"><span data-stu-id="66a64-1198">Support for contract-first development.</span></span>

- <span data-ttu-id="66a64-1199">ASP.NET uyumluluk modunu daha kolay bir şekilde yapılandırma özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1199">Ability to configure ASP.NET compatibility mode more easily.</span></span>

- <span data-ttu-id="66a64-1200">Varsayılan taşıma özelliği değerlerindeki değişiklikler, bunları ayarlamak için sahip olma olasılığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="66a64-1200">Changes in default transport property values to reduce the likelihood that you will have to set them.</span></span>

- <span data-ttu-id="66a64-1201"><xref:System.Xml.XmlDictionaryReaderQuotas>XML sözlüğü okuyucuları için kotaları el ile yapılandırmak zorunda olma olasılığını azaltmak üzere sınıfına yönelik güncelleştirmeler.</span><span class="sxs-lookup"><span data-stu-id="66a64-1201">Updates to the <xref:System.Xml.XmlDictionaryReaderQuotas> class to reduce the likelihood that you will have to manually configure quotas for XML dictionary readers.</span></span>

- <span data-ttu-id="66a64-1202">Visual Studio tarafından derleme sürecinin bir parçası olarak WCF yapılandırma dosyalarının doğrulanması, böylece uygulamanızı çalıştırmadan önce yapılandırma hatalarını tespit edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1202">Validation of WCF configuration files by Visual Studio as part of the build process, so you can detect configuration errors before you run your application.</span></span>

- <span data-ttu-id="66a64-1203">Yeni zaman uyumsuz akış desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1203">New asynchronous streaming support.</span></span>

- <span data-ttu-id="66a64-1204">Internet Information Services (IIS) ile HTTPS üzerinden bir uç nokta açığa çıkarmak daha kolay hale getirmek için yeni HTTPS protokol eşlemesi.</span><span class="sxs-lookup"><span data-stu-id="66a64-1204">New HTTPS protocol mapping to make it easier to expose an endpoint over HTTPS with Internet Information Services (IIS).</span></span>

- <span data-ttu-id="66a64-1205">Hizmet URL 'sine ekleyerek tek bir WSDL belgesinde meta veri oluşturma yeteneği `?singleWSDL` .</span><span class="sxs-lookup"><span data-stu-id="66a64-1205">Ability to generate metadata in a single WSDL document by appending `?singleWSDL` to the service URL.</span></span>

- <span data-ttu-id="66a64-1206">TCP aktarımına benzer performans özellikleriyle 80 ve 443 bağlantı noktaları üzerinden doğru çift yönlü iletişimi etkinleştirmek için WebSockets desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1206">Websockets support to enable true bidirectional communication over ports 80 and 443 with performance characteristics similar to the TCP transport.</span></span>

- <span data-ttu-id="66a64-1207">Kodda hizmetleri yapılandırmaya yönelik destek.</span><span class="sxs-lookup"><span data-stu-id="66a64-1207">Support for configuring services in code.</span></span>

- <span data-ttu-id="66a64-1208">XML Düzenleyici araç ipuçları.</span><span class="sxs-lookup"><span data-stu-id="66a64-1208">XML Editor tooltips.</span></span>

- <span data-ttu-id="66a64-1209"><xref:System.ServiceModel.ChannelFactory> önbelleğe alma desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1209"><xref:System.ServiceModel.ChannelFactory> caching support.</span></span>

- <span data-ttu-id="66a64-1210">İkili kodlayıcı sıkıştırma desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1210">Binary encoder compression support.</span></span>

- <span data-ttu-id="66a64-1211">Geliştiricilerin "yangın ve unut" iletilerini kullanan hizmetler yazmasını sağlayan bir UDP taşıması desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1211">Support for a UDP transport that enables developers to write services that use "fire and forget" messaging.</span></span> <span data-ttu-id="66a64-1212">İstemci, hizmete bir ileti gönderir ve hizmetten yanıt vermez.</span><span class="sxs-lookup"><span data-stu-id="66a64-1212">A client sends a message to a service and expects no response from the service.</span></span>

- <span data-ttu-id="66a64-1213">HTTP taşıma ve aktarım güvenliği kullanılırken, tek bir WCF uç noktasında birden çok kimlik doğrulama modunu destekleme özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1213">Ability to support multiple authentication modes on a single WCF endpoint when using the HTTP transport and transport security.</span></span>

- <span data-ttu-id="66a64-1214">Uluslararası etki alanı adları (IDNs) kullanan WCF Hizmetleri için destek.</span><span class="sxs-lookup"><span data-stu-id="66a64-1214">Support for WCF services that use internationalized domain names (IDNs).</span></span>

<span data-ttu-id="66a64-1215">Daha fazla bilgi için bkz. [Windows Communication Foundation](../wcf/whats-new.md)yenilikleri.</span><span class="sxs-lookup"><span data-stu-id="66a64-1215">For more information, see [What's New in Windows Communication Foundation](../wcf/whats-new.md).</span></span>

<a name="windows_workflow_foundation"></a>

### <a name="windows-workflow-foundation-wf"></a><span data-ttu-id="66a64-1216">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="66a64-1216">Windows Workflow Foundation (WF)</span></span>

<span data-ttu-id="66a64-1217">.NET Framework 4,5 ' de aşağıdakiler de dahil olmak üzere Windows Workflow Foundation (WF) birkaç yeni özellik eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="66a64-1217">In .NET Framework 4.5, several new features were added to Windows Workflow Foundation (WF), including:</span></span>

- <span data-ttu-id="66a64-1218">İlk olarak .NET Framework 4.0.1 ([.NET Framework 4 platformu güncelleştirme 1](/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)) bir parçası olarak sunulan durum makinesi iş akışları.</span><span class="sxs-lookup"><span data-stu-id="66a64-1218">State machine workflows, which were first introduced as part of .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)).</span></span> <span data-ttu-id="66a64-1219">Bu güncelleştirme, geliştiricilerin durum makinesi iş akışları oluşturmalarına olanak tanıyan birkaç yeni sınıf ve etkinlik içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="66a64-1219">This update included several new classes and activities that enabled developers to create state machine workflows.</span></span> <span data-ttu-id="66a64-1220">Bu sınıflar ve Etkinlikler, 4,5 .NET Framework şunlar için güncelleştirildi:</span><span class="sxs-lookup"><span data-stu-id="66a64-1220">These classes and activities were updated for .NET Framework 4.5 to include:</span></span>

  - <span data-ttu-id="66a64-1221">Durumlar üzerinde kesme noktaları ayarlama yeteneği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1221">The ability to set breakpoints on states.</span></span>

  - <span data-ttu-id="66a64-1222">İş akışı tasarımcısında geçişleri kopyalama ve yapıştırma özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1222">The ability to copy and paste transitions in the workflow designer.</span></span>

  - <span data-ttu-id="66a64-1223">Paylaşılan tetikleyici geçişi oluşturma için tasarımcı desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1223">Designer support for shared trigger transition creation.</span></span>

  - <span data-ttu-id="66a64-1224">:, Ve dahil olmak üzere durum makine iş akışları oluşturma etkinlikleri <xref:System.Activities.Statements.StateMachine> <xref:System.Activities.Statements.State> <xref:System.Activities.Statements.Transition> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1224">Activities for creating state machine workflows, including: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, and <xref:System.Activities.Statements.Transition>.</span></span>

- <span data-ttu-id="66a64-1225">Aşağıdakiler gibi gelişmiş İş Akışı Tasarımcısı Özellikler:</span><span class="sxs-lookup"><span data-stu-id="66a64-1225">Enhanced Workflow Designer features such as the following:</span></span>

  - <span data-ttu-id="66a64-1226">Visual Studio 'da **hızlı bul** ve **dosyalardaki bul** dahil olmak üzere gelişmiş iş akışı arama özellikleri.</span><span class="sxs-lookup"><span data-stu-id="66a64-1226">Enhanced workflow search capabilities in Visual Studio, including **Quick Find** and **Find in Files**.</span></span>

  - <span data-ttu-id="66a64-1227">Bir kapsayıcı etkinliğine ikinci bir alt etkinlik eklendiğinde ve her iki etkinliği de sıralı etkinliğe dahil etmek için otomatik olarak bir dizi etkinliği oluşturma özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1227">Ability to automatically create a Sequence activity when a second child activity is added to a container activity, and to include both activities in the Sequence activity.</span></span>

  - <span data-ttu-id="66a64-1228">Kaydırma çubukları kullanılmadan bir iş akışının görünür bölümünün değiştirilmesini sağlayan kaydırma desteği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1228">Panning support, which enables the visible portion of a workflow to be changed without using the scroll bars.</span></span>

  - <span data-ttu-id="66a64-1229">Bir ağaç stili ana hat görünümündeki bir iş akışının bileşenlerini gösteren ve **Belge anahat** görünümünde bir bileşen seçmenize olanak sağlayan yeni bir **Belge anahat** görünümü.</span><span class="sxs-lookup"><span data-stu-id="66a64-1229">A new **Document Outline** view that shows the components of a workflow in a tree-style outline view and lets you select a component in the **Document Outline** view.</span></span>

  - <span data-ttu-id="66a64-1230">Etkinliklere ek açıklamalar ekleme özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1230">Ability to add annotations to activities.</span></span>

  - <span data-ttu-id="66a64-1231">İş akışı tasarımcısını kullanarak etkinlik temsilcilerini tanımlama ve kullanma yeteneği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1231">Ability to define and consume activity delegates by using the workflow designer.</span></span>

  - <span data-ttu-id="66a64-1232">Durum makinesi ve akış çizelgesi iş akışlarında etkinlikler ve geçişler için otomatik bağlan ve otomatik ekle.</span><span class="sxs-lookup"><span data-stu-id="66a64-1232">Auto-connect and auto-insert for activities and transitions in state machine and flowchart workflows.</span></span>

- <span data-ttu-id="66a64-1233">Bir iş akışı için Görünüm durumu bilgilerini XAML dosyasındaki tek bir öğede depolamak için, Görünüm durumu bilgisini kolayca bulup düzenleyebilmenizi sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1233">Storage of the view state information for a workflow in a single element in the XAML file, so you can easily locate and edit the view state information.</span></span>

- <span data-ttu-id="66a64-1234">Alt etkinliklerin kalıcı olmasını önleyen bir NoPersistScope kapsayıcı etkinliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1234">A NoPersistScope container activity to prevent child activities from persisting.</span></span>

- <span data-ttu-id="66a64-1235">C# ifadeleri için destek:</span><span class="sxs-lookup"><span data-stu-id="66a64-1235">Support for C# expressions:</span></span>

  - <span data-ttu-id="66a64-1236">Visual Basic kullanan iş akışı projeleri Visual Basic ifadelerini kullanır ve C# iş akışı projeleri C# ifadelerini kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="66a64-1236">Workflow projects that use Visual Basic will use Visual Basic expressions, and C# workflow projects will use C# expressions.</span></span>

  - <span data-ttu-id="66a64-1237">Visual Studio 2010 ' de oluşturulan ve Visual Basic ifadelerine sahip c# iş akışı projeleri C# ifadelerini kullanan C# iş akışı projeleriyle uyumludur.</span><span class="sxs-lookup"><span data-stu-id="66a64-1237">C# workflow projects that were created in Visual Studio 2010 and that have Visual Basic expressions are compatible with C# workflow projects that use C# expressions.</span></span>

- <span data-ttu-id="66a64-1238">Sürüm oluşturma geliştirmeleri:</span><span class="sxs-lookup"><span data-stu-id="66a64-1238">Versioning enhancements:</span></span>

  - <span data-ttu-id="66a64-1239"><xref:System.Activities.WorkflowIdentity>Kalıcı bir iş akışı örneği ve onun iş akışı tanımı arasında eşleme sağlayan yeni sınıf.</span><span class="sxs-lookup"><span data-stu-id="66a64-1239">The new  <xref:System.Activities.WorkflowIdentity> class, which provides a mapping between a persisted workflow instance and its workflow definition.</span></span>

  - <span data-ttu-id="66a64-1240">Aynı konakta birden çok iş akışı sürümünün yan yana yürütülmesi (dahil) <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="66a64-1240">Side-by-side execution of multiple workflow versions in the same host, including <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>

  - <span data-ttu-id="66a64-1241">Dinamik güncelleştirmede, kalıcı bir iş akışı örneğinin tanımını değiştirme özelliği.</span><span class="sxs-lookup"><span data-stu-id="66a64-1241">In Dynamic Update, the ability to modify the definition of a persisted workflow instance.</span></span>

- <span data-ttu-id="66a64-1242">Sözleşme-ilk iş akışı hizmeti geliştirme, mevcut bir hizmet sözleşmesiyle eşleşecek şekilde otomatik olarak etkinlik oluşturma desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1242">Contract-first workflow service development, which provides support for automatically generating activities to match an existing service contract.</span></span>

<span data-ttu-id="66a64-1243">Daha fazla bilgi için bkz. [Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md)yenilikleri.</span><span class="sxs-lookup"><span data-stu-id="66a64-1243">For more information, see [What's New in Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).</span></span>

<a name="tailored"></a>

### <a name="net-for-windows-8x-store-apps"></a><span data-ttu-id="66a64-1244">Windows 8.x Mağazası uygulamaları için .NET</span><span class="sxs-lookup"><span data-stu-id="66a64-1244">.NET for Windows 8.x Store apps</span></span>

<span data-ttu-id="66a64-1245">Windows 8. x Mağazası uygulamaları belirli form faktörleri için tasarlanmıştır ve Windows işletim sisteminin gücünden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="66a64-1245">Windows 8.x Store apps are designed for specific form factors and leverage the power of the Windows operating system.</span></span> <span data-ttu-id="66a64-1246">4,5 veya 4.5.1 .NET Framework bir alt kümesi, C# veya Visual Basic kullanarak Windows için Windows 8. x Mağazası uygulamaları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66a64-1246">A subset of .NET Framework 4.5 or 4.5.1 is available for building Windows 8.x Store apps for Windows by using C# or Visual Basic.</span></span> <span data-ttu-id="66a64-1247">Bu alt küme, Windows 8. x Mağazası uygulamaları için .NET olarak adlandırılır ve [genel bakışta](/previous-versions/windows/apps/br230302(v=vs.140))ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="66a64-1247">This subset is called .NET for Windows 8.x Store apps and is discussed in an [overview](/previous-versions/windows/apps/br230302(v=vs.140)).</span></span>

### <a name="portable-class-libraries"></a><span data-ttu-id="66a64-1248">Taşınabilir sınıf kitaplıkları <a name="portable"></a></span><span class="sxs-lookup"><span data-stu-id="66a64-1248">Portable Class Libraries <a name="portable"></a></span></span>

<span data-ttu-id="66a64-1249">Visual Studio 2012 ' deki (ve sonraki sürümlerde) taşınabilir sınıf kitaplığı projesi, birden çok .NET Framework platformda çalışan yönetilen derlemeler yazmanızı ve oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="66a64-1249">The Portable Class Library project in Visual Studio 2012 (and later versions) enables you to write and build managed assemblies that work on multiple .NET Framework platforms.</span></span> <span data-ttu-id="66a64-1250">Taşınabilir bir sınıf kitaplığı projesi kullanarak, hedeflenecek platformları (Windows Phone ve Windows 8. x Mağazası uygulamaları için .NET) seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1250">Using a Portable Class Library project, you choose the platforms (such as Windows Phone and .NET for Windows 8.x Store apps) to target.</span></span> <span data-ttu-id="66a64-1251">Projenizdeki kullanılabilir türler ve Üyeler, bu platformlar genelinde ortak türler ve üyelerle otomatik olarak kısıtlıdır.</span><span class="sxs-lookup"><span data-stu-id="66a64-1251">The available types and members in your project are automatically restricted to the common types and members across these platforms.</span></span> <span data-ttu-id="66a64-1252">Daha fazla bilgi için bkz. [taşınabilir sınıf kitaplığı](../cross-platform/portable-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="66a64-1252">For more information, see [Portable Class Library](../cross-platform/portable-class-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66a64-1253">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66a64-1253">See also</span></span>

- [<span data-ttu-id="66a64-1254">.NET Framework ve Bant Dışı Yayınlar</span><span class="sxs-lookup"><span data-stu-id="66a64-1254">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
- [<span data-ttu-id="66a64-1255">.NET Framework erişilebilirlik yenilikleri</span><span class="sxs-lookup"><span data-stu-id="66a64-1255">What's new in accessibility in .NET Framework</span></span>](whats-new-in-accessibility.md)
- [<span data-ttu-id="66a64-1256">Visual Studio 2019 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="66a64-1256">What's New in Visual Studio 2019</span></span>](/visualstudio/ide/whats-new-visual-studio-2019)
- [<span data-ttu-id="66a64-1257">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66a64-1257">ASP.NET</span></span>](/aspnet)
- [<span data-ttu-id="66a64-1258">Visual Studio 'da C++ yenilikleri</span><span class="sxs-lookup"><span data-stu-id="66a64-1258">What's New for C++ in Visual Studio</span></span>](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
- [<span data-ttu-id="66a64-1259">.NET SDK'yı indirin</span><span class="sxs-lookup"><span data-stu-id="66a64-1259">Download the .NET SDK</span></span>](https://dotnet.microsoft.com/download)
