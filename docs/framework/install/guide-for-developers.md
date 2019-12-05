---
title: .NET Framework Geliştirici paketini veya yeniden dağıtılabilir yüklemeyi
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework redistributable package, downloading
- .NET Framework, installing
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: daf9d9d5-84ac-4bd9-a864-27665ffd0f5c
ms.openlocfilehash: 6098c2b855e692eef198e388ba9b29a4e8cc8de1
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802217"
---
# <a name="install-the-net-framework-for-developers"></a>Geliştiriciler için .NET Framework yüklemesi

.NET, Windows üzerinde çalışan birçok uygulamanın ayrılmaz bir parçasıdır ve bu uygulamaların çalışması için ortak işlevsellik sağlar. Geliştiriciler için .NET Framework, görsel açıdan etkileyici kullanıcı deneyimleri ve sorunsuz ve güvenli iletişim içeren uygulamalar oluşturmak için kapsamlı ve tutarlı bir programlama modeli sağlar.

> [!NOTE]
> Bu konu, kendi sistemine .NET Framework yüklemek isteyen ya da uygulamalarını uygulamalarıyla yüklemek isteyen **geliştiricilere** yöneliktir. .NET Framework yükleme ile ilgilenen **Kullanıcılar** Için, [Windows 10 ve Windows Server 2016 ' de .NET Framework yükleme](on-windows-10.md)gibi belirli işletim sistemlerine .NET Framework yüklemeyi tartışan ayrı konulara bakın.

Bu makalede, .NET Framework .NET Framework 4,5 ' den bilgisayarınıza .NET Framework 4,8 ' e kadar tüm sürümlerini yükleme bağlantıları sağlanmaktadır. Geliştiriciyseniz, bu bağlantıları karşıdan yüklemek ve .NET Framework ile uygulamalarınızı yeniden dağıtmak için de kullanabilirsiniz. Uygulamanızla .NET Framework bir sürümünü dağıtma hakkında daha fazla bilgi için bkz. [geliştiriciler için .NET Framework dağıtım kılavuzu](../deployment/deployment-guide-for-developers.md).

[!INCLUDE[net-framework-4-versions](../../../includes/net-framework-4x-versions.md)]

.NET Framework sürümleri ve bir bilgisayarda hangi sürümlerin yüklü olduğunu belirleme hakkında daha fazla bilgi için bkz. [sürümler ve bağımlılıklar](../migration-guide/versions-and-dependencies.md) ve [nasıl yapılır: hangi .NET Framework sürümlerinin yükleneceğini belirleme](../migration-guide/how-to-determine-which-versions-are-installed.md).

> [!NOTE]
> 3,5 .NET Framework hakkında daha fazla bilgi için bkz. [Windows 10, Windows 8.1 ve Windows 8 ' de 3,5 .NET Framework](dotnet-35-windows-10.md).

Hızlı bağlantılar için aşağıdaki tabloyu kullanın veya ayrıntılar için okumaya devam edin. Yüklemeden önce .NET Framework sistem gereksinimlerini görüntülemek için bkz. [sistem gereksinimleri](../get-started/system-requirements.md). Sorun giderme konusunda yardım için bkz. [sorun giderme](troubleshoot-blocked-installations-and-uninstallations.md).

|.NET Framework sürümü|Geliştirici yüklemesi|Yeniden dağıtılabilir yükleme|Platform desteği|
|----------------------------|----------------------------|----------------------------------|----------------------|
|**4,8**|[.NET Framework 4,8 Geliştirici paketi](https://go.microsoft.com/fwlink/?linkid=2088517)|[Merkez 4,8 web yükleyicisi 'Ni indirin](https://go.microsoft.com/fwlink/?LinkId=2085155)<br/><br/>[Center 4,8 çevrimdışı yükleyicisi 'Ni indirin](https://go.microsoft.com/fwlink/?linkid=2088631)|**Dahil edilen:**<br/><br/>Windows 10 Mayıs 2019 güncelleştirmesi<br /><br /> **Şunları yükleyebilirsiniz:**<br/><br/>Windows 10 Ekim 2018 güncelleştirmesi<br/>Windows 10 Nisan 2018 güncelleştirmesi<br/>Windows 10 Fall Creators Update<br/>Windows 10 Creators Update <br /> Windows 10 Yıldönümü Güncelleştirmesi<br /> Windows 8.1 ve önceki sürümler<br /> Windows Server 2019<br/>Windows Server, sürüm 1809<br/>Windows Server, sürüm 1803<br /><br/> (tam liste için bkz. [sistem gereksinimleri](../get-started/system-requirements.md))||
|**4.7.2**|[.NET Framework 4.7.2 Geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=874338)|[İndirme Merkezi 4.7.2 Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=863262)<br/><br/>[4.7.2 Center çevrimdışı yükleyicisi 'Ni indirin](https://go.microsoft.com/fwlink/?LinkId=863265)|**Dahil edilen:** <br/><br/>Windows 10 Ekim 2018 güncelleştirmesi<br/>Windows 10 Nisan 2018 güncelleştirmesi<br/>Windows Server 2019<br/>Windows Server, sürüm 1809<br/>Windows Server, sürüm 1803<br /><br /> **Şunları yükleyebilirsiniz:**<br/> <br/>Windows 10 Fall Creators Update<br/>Windows 10 Creators Update <br /> Windows 10 Yıldönümü Güncelleştirmesi<br /> Windows 8.1 ve önceki sürümler<br /> Windows Server, sürüm 1709 ve öncesi<br /><br/> (tam liste için bkz. [sistem gereksinimleri](../get-started/system-requirements.md))||
|**4.7.1**|[NET Framework 4.7.1 Geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=852105)|[4.7.1 Web Yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/?LinkId=852095)<br /><br /> [4.7.1 çevrimdışı yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/?LinkId=852107)|**Dahil edilen:** <br/><br/>Windows 10 Fall Creators Update<br/>Windows Server, sürüm 1709<br /><br /> **Şunları yükleyebilirsiniz:**<br/><br/> Windows 10 Creators Update <br /> Windows 10 Yıldönümü Güncelleştirmesi<br /> Windows 8.1 ve önceki sürümler<br /> Windows Server 2016 ve öncesi<br /> (tam liste için bkz. [sistem gereksinimleri](../get-started/system-requirements.md))||
|**4.7**|[NET Framework 4,7 geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=825319)|[4,7 Web Yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/?LinkId=825299)<br /><br /> [4,7 çevrimdışı yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/?LinkId=825303)|**Dahil edilen:** <br/><br/>Windows 10 Creators Update<br /><br /> **Şunları yükleyebilirsiniz:**<br /><br/> Windows 10 Yıldönümü Güncelleştirmesi<br /> Windows 8.1 ve önceki sürümler<br /> Windows Server 2016 ve öncesi<br /> (tam liste için bkz. [sistem gereksinimleri](../get-started/system-requirements.md))||
|**4.6.2**|[NET Framework 4.6.2 Geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=780617)|[4.6.2 Web Yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/?LinkId=780597)<br /><br /> [4.6.2 çevrimdışı yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/?LinkId=780601)|**Dahil edilen:** <br/><br /> Windows 10 Yıldönümü Güncelleştirmesi<br /><br /> **Şunları yükleyebilirsiniz:**<br /><br/> Windows 10 Kasım güncelleştirmesi <br/> Windows 10 <br /> Windows 8.1 ve önceki sürümler<br /> Windows Server 2012 R2 ve öncesi<br /> (tam liste için bkz. [sistem gereksinimleri](../get-started/system-requirements.md))|
|**4.6.1**|[NET Framework 4.6.1 Geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=690706)|[4.6.1 Web Yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/?LinkId=671729)<br /><br /> [4.6.1 çevrimdışı yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/?LinkId=671744)|**Şunları yükleyebilirsiniz:**<br /><br/> Windows 10 <br /> Windows 8.1 ve önceki sürümler<br /> Windows Server 2012 R2 ve öncesi<br /> (tam liste için bkz. [sistem gereksinimleri](../get-started/system-requirements.md))|
|**4.6**|Visual Studio 2015 ' ye dahildir.<br /><br /> [Microsoft .NET Framework 4,6 hedefleme paketi](https://go.microsoft.com/fwlink/?LinkId=528261)|[4,6 Web Yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/?LinkId=528259)<br /><br /> [4,6 çevrimdışı yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/?LinkId=528233)|**Dahil edilen:** <br/><br /> Windows 10 <br />[Visual Studio 2015](https://my.visualstudio.com/Downloads?q=visual%20studio%202015)<br /><br /> **Ayrıca, üzerine yükleyebilirsiniz:**<br /><br/> Windows 8.1 ve önceki sürümler<br /> Windows Server 2012 R2 ve öncesi<br /> (tam liste için bkz. [sistem gereksinimleri](../get-started/system-requirements.md))|
|**4.5.2**|[Microsoft .NET Framework 4.5.2 Geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=397702)<br /><br /> Visual Studio 2013, Visual Studio 2012 veya diğer Ides ile kullanım için|[4.5.2 Web Yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/p/?LinkId=397703)<br /><br /> [4.5.2 çevrimdışı yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/p/?LinkId=397706)|**Şunları yükleyebilirsiniz:**<br /><br/> Windows 8.1 ve önceki sürümler<br /> Windows Server 2012 R2 ve öncesi<br /> (tam liste için bkz. [sistem gereksinimleri](../get-started/system-requirements.md))|
|**4.5.1**|[Microsoft .NET Framework 4.5.1 Geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=324213)<br /><br /> Visual Studio 2013, Visual Studio 2012 veya diğer Ides ile kullanım için|[4.5.1 Web Yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/p/?LinkId=310158)<br /><br /> [4.5.1 çevrimdışı yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/p/?LinkId=310159)|**Dahil edilen:**<br /> <br/>Windows 8.1<br /> Windows Server 2012 R2<br /> [Visual Studio 2013](https://my.visualstudio.com/Downloads?q=visual%20studio%202013)<br /><br /> **Ayrıca, üzerine yükleyebilirsiniz:**<br /><br/> Windows 8 ve önceki sürümler<br /> [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] ve önceki sürümleri<br />(tam liste için bkz. [sistem gereksinimleri](../get-started/system-requirements.md))|
|**4.5**|Visual Studio 2012 'e dahildir<br /><br /> Windows 8 SDK 'sının bir parçası olarak da kullanılabilir|[4,5 Web Yükleyicisi için indirme sayfası](https://go.microsoft.com/fwlink/p/?LinkId=245484)|**Dahil edilen:** <br/><br /> Windows 8<br /> [!INCLUDE[winserver8](../../../includes/winserver8-md.md)]<br /> [Visual Studio 2012](https://my.visualstudio.com/Downloads?q=visual%20studio%202012)<br /><br /> **Ayrıca, üzerine yükleyebilirsiniz:**<br/><br /> Windows 7 ve daha önceki sürümleri<br /> Windows Server 2008 SP2 ve daha önceki sürümleri<br />(tam liste için bkz. [sistem gereksinimleri](../get-started/system-requirements.md))|

Desteklenen tüm platformlarda, varsa .NET Framework belirli bir sürümü için **Geliştirici paketini** yükleyebilirsiniz.

**Web veya çevrimdışı yükleyiciyi** şu şekilde yükleyebilirsiniz:

- Windows 8.1 ve önceki sürümler

- Windows Server 2012 R2 ve öncesi

Tam liste için bkz. [sistem gereksinimleri](../get-started/system-requirements.md).

Hem kullanıcılar hem de geliştiriciler için .NET Framework genel bir giriş için [bkz. Başlarken](../get-started/index.md). .NET Framework uygulamanıza dağıtma hakkında daha fazla bilgi için bkz. [Dağıtım Kılavuzu](../deployment/deployment-guide-for-developers.md). .NET Framework mimarisi ve temel özellikleri hakkında bilgi edinmek için bkz. [genel bakış](../get-started/overview.md).

## <a name="installation-choices"></a>Yükleme seçimleri

Visual Studio veya başka bir geliştirme ortamında .NET Framework en güncel sürümüne göre geliştirmek üzere bir geliştirici hedefleme paketi yükleyin veya uygulama ya da denetim ile dağıtım için .NET Framework yeniden dağıtılabilir ' i indirin.

### <a name="to-install-the-net-framework-developer-pack-or-targeting-pack"></a>.NET Framework Geliştirici paketini veya hedefleme paketini yüklemek için

*Hedefleme paketi* , Visual Studio 'da geliştirme yaparken uygulamanızın belirli bir .NET Framework sürümünü ve diğer bazı geliştirme ortamlarını hedeflemesini sağlar. Bir *Geliştirici paketi* , ilgili hedefleme paketiyle birlikte .NET Framework ve eşlık eden SDK 'nin belirli bir sürümünü içerir.

.NET Framework 4.5.1 veya 4.5.2 için geliştirici paketi, .NET Framework 4,6 için hedefleme paketi ve .NET Framework 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 veya 4,8 için geliştirici paketi, başvuru derlemelerinin belirli bir .NET Framework sürümünü sağlar, dil Visual Studio gibi tümleşik bir geliştirme ortamında kullanılmak üzere paketler ve IntelliSense dosyaları.  Visual Studio kullanıyorsanız, geliştirici paketi veya hedefleme paketi ayrıca yeni bir proje oluştururken hedef seçeneklere .NET Framework yüklü sürümünü de ekler.  Aşağıdakilerden birini seçin:

- [Microsoft .NET Framework 4,8 Geliştirici paketi](https://go.microsoft.com/fwlink/?linkid=2088517)

- [Microsoft .NET Framework 4.7.2 Geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=874338)

- [Microsoft .NET Framework 4.7.1 Geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=852105)

- [Microsoft .NET Framework 4,7 geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=825319)

- [Microsoft .NET Framework 4.6.2 Geliştirici Paketi](https://go.microsoft.com/fwlink/?LinkId=780617)

- [Microsoft .NET Framework 4.6.1 Geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=690706)

- [Microsoft .NET Framework 4,6 hedefleme paketi](https://go.microsoft.com/fwlink/?LinkId=528261)

- Windows 8.1 veya daha önceki sürümleri, Visual Studio 2013, Visual Studio 2012 veya diğer Ides 'te sürüm 4.5.2 yüklemek için [.NET Framework Geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=397702) .

- Visual Studio 2012 veya diğer Ides 'te sürüm 4.5.1 yüklemek için [4.5.1 Geliştirici paketini .NET Framework](https://go.microsoft.com/fwlink/?LinkId=324213) .

Geliştirici paketi indirme sayfasında **İndir**' i seçin. Ardından, **Çalıştır** veya **Kaydet**' i seçin ve sorulduğunda yönergeleri izleyin. Aşağıdaki şekilde gösterildiği gibi, Visual Studio Yükleyicisi **.net masaüstü geliştirme** iş yükünde isteğe bağlı bileşenlerden seçerek, .NET Framework belirli bir sürümü için Geliştirici paketini veya hedefleme paketini de yükleyebilirsiniz.

   ![.NET masaüstü geliştirme iş yüküyle Visual Studio Yükleyicisi](./media/visual-studio-installer.jpg)

.NET Framework belirli bir sürümünü hedeflediğinizde, uygulamanız söz konusu sürümün geliştirici paketine dahil olan başvuru derlemeleri kullanılarak oluşturulur. Çalışma zamanında, derlemeler genel derleme önbelleğinden çözümlenir ve başvuru derlemeleri kullanılmaz.

Visual Studio 'dan bir uygulama oluştururken veya komut satırından MSBuild 'i kullanırken MSBuild, "Framework *-Version*" çerçevesi için başvuru derlemeleri "hata MSB3644 görüntüleyebilir." Hatayı gidermek için, Geliştirici paketini veya .NET Framework sürümü için hedefleme paketini indirin.

### <a name="to-install-or-download-the-net-framework-redistributable"></a>.NET Framework yeniden dağıtılabilir yükleme veya indirme

Yükleyiciler, .NET Framework sürümlerini hedefleyen bir uygulama veya denetim için .NET Framework bileşenlerini indirir. Bu bileşenler, uygulamanın veya denetimin çalıştığı her bilgisayara yüklenmelidir. Bu yükleyiciler yeniden dağıtılabilir, bu sayede uygulamanızı uygulamanızın Kurulum programına dahil edebilirsiniz.

Karşıdan yükleme sayfası çeşitli dillerde sağlanmaktadır, ancak karşıdan yüklemelerin çoğu yalnızca İngilizce dilinde sağlanır. Ek dil desteği için bir dil paketi yüklemeniz gerekir.

İki yeniden dağıtılabilir yükleyici türü mevcuttur:

- **Web yükleyici** (Web Önyükleyicisi), gerekli bileşenleri ve yükleme bilgisayarının işletim sistemiyle eşleşen dil paketini Web 'den indirir. Bu paket çevrimdışı yükleyiciden daha küçüktür, ancak tutarlı bir Internet bağlantısı gerektirir. Ek dil desteği yüklemek için [tek başına dil paketlerini](#to-install-language-packs) indirebilirsiniz.

- **Çevrimdışı yükleyici** (tek başına yeniden dağıtılabilir) .NET Framework yüklemek için gerekli tüm bileşenleri içerir, ancak dil paketlerini içermez. Bu indirilebilir dosya, web yükleyicisinden daha büyüktür. Çevrimdışı yükleyici Internet bağlantısı gerektirmez. Çevrimdışı yükleyiciyi çalıştırdıktan sonra, dil desteğini yüklemek için [tek başına dil paketlerini](#to-install-language-packs) indirebilirsiniz. Tutarlı bir Internet bağlantısına sahip değilseniz, çevrimdışı yükleyiciyi kullanın.

Hem Web hem de çevrimdışı yükleyiciler x86 tabanlı ve x64 tabanlı bilgisayarlar için tasarlanmıştır (bkz. [sistem gereksinimleri](../get-started/system-requirements.md)), ancak Itanium tabanlı bilgisayarları desteklemez.

1. Yüklemek istediğiniz .NET Framework sürümü için yükleme sayfasını açın:

   - .NET Framework 4,8 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=2085155) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/?linkid=2088631))

   - .NET Framework 4.7.2 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=863262) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=863265))

   - .NET Framework 4.7.1 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=852095) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=852107))

   - .NET Framework 4,7 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=825299) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=825303))

   - .NET Framework 4.6.2 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=780597) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=780601))

   - .NET Framework 4.6.1 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=671729) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=671744))

   - .NET Framework 4,6 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=528259) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=528233))

   - .NET Framework 4.5.2 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/p/?LinkId=397703) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=397706))

   - .NET Framework 4.5.1 ([Web Yükleyicisi](https://go.microsoft.com/fwlink/p/?LinkId=310158) veya [çevrimdışı yükleyici](https://go.microsoft.com/fwlink/p/?LinkId=310159))

   - [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)

1. İndirme sayfası dilini seçin. Bu seçenek, .NET Framework'ün yerelleştirilmiş kaynaklarını karşıdan yüklemez; yalnızca karşıdan yükleme sayfasında görüntülenen metni etkiler.

1. **İndir**' i seçin.

1. İstenirse, sistem mimarinizle eşleşen indirmeyi seçin ve ardından **İleri**' yi seçin.

1. Karşıdan yükleme istemi göründüğünde aşağıdakilerden **birini** yapın:

   - .NET Framework bilgisayarınıza yüklemek istiyorsanız, **Çalıştır**' ı seçin ve ekranınızdaki istemleri izleyin.

   - Yeniden dağıtım için .NET Framework indirmek istiyorsanız **Kaydet**' i seçin ve ekranınızdaki istemleri izleyin.

1. Ek diller için kaynak indirmek isterseniz, bir veya daha fazla dil paketlerini yüklemek için sonraki bölümünde yer alan yönergeleri izleyin.

> [!NOTE]
> Yükleme sırasında herhangi bir sorunla karşılaşırsanız bkz. [sorun giderme](troubleshoot-blocked-installations-and-uninstallations.md).

**Yükleme notları:**

- .NET Framework 4.5.1 ve 4.5.2 ve .NET Framework 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 ve 4,8 .NET Framework 4,5 için yerinde güncelleştirmelerdir.

- .NET Framework 4,5, noktası sürümleri, .NET Framework 4,6 ve nokta sürümleri, .NET Framework 4,7 ve nokta sürümleri ve .NET Framework 4,8 .NET Framework 4 ' ü değiştirir. Bu sürümleri .NET Framework 4 ' ün yüklü olduğu bir sisteme yüklediğinizde, derlemeler değiştirilmez.

- .NET Framework 4,5, noktası sürümleri, .NET Framework 4,6 ve nokta sürümleri, .NET Framework 4,7 ve onun noktası sürümleri kaldırılır ya da .NET Framework 4,8, önceden var olan .NET Framework 4 dosyalarını da kaldırır. .NET Framework 4 ' e geri dönmek istiyorsanız, bu dosyayı ve tüm güncelleştirmeleri yeniden yüklemeniz gerekir. Bkz. [.NET Framework 4](https://go.microsoft.com/fwlink/p/?LinkId=230665)' ü yükleme.

- .NET Framework 4,5, noktası sürümleri, .NET Framework 4,6 ve nokta sürümleri, .NET Framework 4,7 ve nokta sürümü ve .NET Framework 4,8 sürümünü yüklemek için yönetici kimlik bilgilerine sahip olmanız gerekir.

- .NET Framework 4.5 yeniden dağıtılabilir, Microsoft tarafından üretilen ve imzalanan dosyalardaki dijital imzanın süresinin zamanından önce dolmasına neden olan ve bir dijital sertifika üzerinde bulunan hatalı zaman damgasıyla ilgili sorunu gidermek amacıyla 9 Ekim 2012 tarihinde güncellenmiştir. Daha önce 16 Ağustos 2012 tarihli .NET Framework 4,5 yeniden dağıtılabilir paketini yüklediyseniz, [Microsoft Indirme merkezi](https://go.microsoft.com/fwlink/p/?LinkId=245484)'ndeki kopyanızı en son yeniden dağıtılabilir ile güncelleştirmenizi öneririz. Bu sorun hakkında daha fazla bilgi için bkz. [Microsoft Güvenlik Danışmanlığı 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655) ve [bilgi Bankası makalesi 2770445](https://support.microsoft.com/kb/2770445).

## <a name="to-install-language-packs"></a>Dil paketlerini yüklemek için

Dil paketleri, desteklenen diller için yerelleştirilmiş kaynaklar (örneğin, çevrilmiş hata iletileri ve UI metni) içeren çalıştırılabilir dosyalardır. Bir dil paketi yüklemezseniz, .NET Framework hata iletileri ve diğer metinler İngilizce görüntülenir.  Web yükleyicisinin, işletim sisteminize eşleşen dil paketini otomatik olarak kurduğunu, ancak bilgisayarınıza ek dil paketleri yükleyebileceğinize dikkat edin. Çevrimdışı yükleyiciler dil paketlerini içermez.

> [!IMPORTANT]
> Dil paketleri, bir uygulamayı çalıştırmak için gereken .NET Framework bileşenlerini içermezler; bu nedenle bir dil paketi yüklemeden önce web veya çevrimdışı yükleyiciyi çalıştırmanız gerekir. Zaten bir dil paketi yüklediyseniz, uygulamayı kaldırın, .NET Framework yükleyin ve ardından dil paketini yeniden yükleyin.

1. Yüklediğiniz .NET Framework sürümü için dil paketini açın:

    - [.NET Framework 4,8 dil paketleri](https://go.microsoft.com/fwlink/?LinkId=2053984)

    - [.NET Framework 4.7.2 dil paketleri](https://go.microsoft.com/fwlink/?LinkID=863258)

    - [.NET Framework 4.7.1 dil paketleri](https://go.microsoft.com/fwlink/?LinkID=852090)

    - [.NET Framework 4,7 dil paketleri](https://go.microsoft.com/fwlink/?LinkID=825306)

    - [.NET Framework 4.6.2 dil paketleri](https://go.microsoft.com/fwlink/?LinkID=780604)

    - [.NET Framework 4.6.1 dil paketleri](https://go.microsoft.com/fwlink/?LinkID=671747)

    - [.NET Framework 4,6 dil paketleri](https://go.microsoft.com/fwlink/?LinkID=528314)

    - [.NET Framework 4.5.2 dil paketleri](https://go.microsoft.com/fwlink/?LinkId=397701)

    - [.NET Framework 4.5.1 dil paketleri](https://go.microsoft.com/fwlink/?LinkId=322101)

    - [.NET Framework 4,5 dil paketleri](https://go.microsoft.com/fwlink/p/?LinkId=245451)

2. Dil listesinde, indirmek istediğiniz dili seçin ve sayfanın bu dilde yeniden yüklenmesi için birkaç saniye bekleyin.

3. **İndir**' i seçin.

Aşağıdaki tabloda desteklenen diller listelenmiştir.

| Dil              | Kültür |
| --------------------- | :-----: |
| Arapça                | Ar      |
| Çekçe                 | cs      |
| Danca                | da      |
| Felemenkçe                 | nl      |
| Fince               | fi      |
| İngilizce (ABD)         | tr-TR   |
| Fransızca                | fr      |
| Almanca                | de      |
| Yunanca                 | el      |
| İbranice                | LIP      |
| Macarca             | hu      |
| İtalyanca               | it      |
| Japonca              | ja      |
| Korece                | ko      |
| Norveççe             | hayır      |
| Lehçe                | pl      |
| Portekizce (Brezilya)   | pt-BR   |
| Portekizce (Portekiz) | pt-PT   |
| Rusça               | ru      |
| Basitleştirilmiş Çince    | zh-CHS  |
| İspanyolca               | es      |
| İsveççe               | sv      |
| Geleneksel Çince   | zh-CHT  |
| Türkçe               | tr      |

## <a name="next-steps"></a>Sonraki adımlar

- .NET Framework yeni başladıysanız, önemli kavramlara ve bileşenlere giriş için [genel bakış](../get-started/overview.md) bölümüne bakın.

- .NET Framework 4,5 ve sonraki tüm sürümlerindeki yeni özellikler ve geliştirmeler için [bkz. yenilikler](../whats-new/index.md).

- .NET Framework uygulamanıza dağıtma hakkında ayrıntılı bilgi için bkz. [geliştiriciler Için dağıtım kılavuzu](../deployment/deployment-guide-for-developers.md).

- .NET Framework uygulamanıza dağıtımını etkileyen değişiklikler için, bkz. [.NET Framework 4,5 yüklemeleri sırasında sistem yeniden başlatmaları azaltma](../deployment/reducing-system-restarts.md).

- Uygulamanızı .NET Framework 4 ' ten .NET Framework 4,5 ' e veya kendi nokta sürümlerinden birine geçirme hakkında daha fazla bilgi için, [geçiş kılavuzuna](../migration-guide/index.md)bakın.

- Çevrimiçi .NET Framework kaynak koduna gözatmak için [.NET Framework başvuru kaynağı](https://referencesource.microsoft.com/) bölümüne bakın. Başvuru kaynağı [GitHub](https://github.com/Microsoft/referencesource)'da da kullanılabilir. Hata ayıklama sırasında çevrimdışı görüntüleme ve kaynaklar (yayama ve güncelleştirmeler dahil) için [başvuru kaynağını indirebilirsiniz](https://referencesource.microsoft.com/download.html) . Daha fazla bilgi için bkz. [.net başvuru kaynağı için yeni bir görünüm](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/)olan blog girişi.

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiriciler için Dağıtım Kılavuzu](../deployment/deployment-guide-for-developers.md)
- [Yöneticiler için Dağıtım Kılavuzu](../deployment/guide-for-administrators.md)
- [Windows 10, Windows 8.1 ve Windows 8’de .NET Framework 3.5 Yükleme](dotnet-35-windows-10.md)
- [Engellenen .NET Framework yüklemelerinin ve yüklemelerin geri yüklemelerinin sorunlarını giderme](troubleshoot-blocked-installations-and-uninstallations.md)
