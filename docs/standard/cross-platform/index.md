---
title: .NET Framework ile birden çok platform için geliştirme
ms.date: 10/21/2020
ms.technology: dotnet-standard
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
ms.openlocfilehash: 75c33d2d2eb4bda0bcd86e19c5098af4a63863e9
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471975"
---
# <a name="develop-for-multiple-platforms-with-net-framework"></a>.NET Framework ile birden çok platform için geliştirme

.NET Framework ve Visual Studio kullanarak hem Microsoft hem de Microsoft dışı platformlar için uygulamalar geliştirebilirsiniz.

[!INCLUDE [net-framework-future](../../../includes/net-framework-future.md)]

## <a name="options-for-cross-platform-development"></a>Platformlar arası geliştirme seçenekleri

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Birden çok platform için geliştirme yapmak amacıyla kaynak kodu veya ikili dosyaları paylaşabilir ve .NET Framework kodu ve Windows Çalışma Zamanı API 'Leri arasında çağrılar yapabilirsiniz.

|İstiyorsanız...|Kullan...|
|-----------------------|------------|
|Windows Phone 8,1 ve Windows 8.1 uygulamalar arasında kaynak kodu paylaşma|**Paylaşılan projeler** (Visual Studio 2013 Içinde evrensel uygulamalar şablonu, güncelleştirme 2).<br /><br /> -Şu anda Visual Basic desteği yok.<br />-# Deyimlerini kullanarak platforma özgü kodu ayırabilirsiniz `if` .<br /><br /> Ayrıntılar için bkz.<br /><br /> -   [Kodlamaya başlayın](/windows/uwp/get-started/create-uwp-apps)<br />-   [Evrensel xaml uygulamaları (blog gönderisi) oluşturmak Için Visual Studio 'Yu kullanma](https://devblogs.microsoft.com/visualstudio/using-visual-studio-to-build-universal-xaml-apps/)<br />-   [Xaml yakınsanmış uygulamalar oluşturmak Için Visual Studio 'Yu kullanma](https://channel9.msdn.com/Events/Build/2014/3-591) (video)|
|Farklı platformları hedefleyen uygulamalar arasında ikili dosyalar paylaşma|Platform belirsiz olan kod için **taşınabilir sınıf kitaplığı projeleri** .<br /><br /> -Bu yaklaşım genellikle iş mantığını uygulayan kod için kullanılır.<br />-Visual Basic veya C# kullanabilirsiniz.<br />-API desteği platforma göre farklılık gösterir.<br />-Windows 8.1 ve Windows Phone 8,1 ' i hedefleyen taşınabilir sınıf kitaplığı projeleri Windows Çalışma Zamanı API 'Leri ve XAML 'yi destekler. Bu özellikler, taşınabilir sınıf kitaplığının eski sürümlerinde kullanılamaz.<br />-Gerekirse, arabirimleri veya soyut sınıfları kullanarak platforma özgü kodu soyutlamak için kullanabilirsiniz.<br /><br /> Ayrıntılar için bkz.<br /><br /> -   [Taşınabilir sınıf kitaplığı](cross-platform-development-with-the-portable-class-library.md)<br />-   [Taşınabilir sınıf kitaplıklarını sizin Için nasıl çalışır hale getirme](/archive/blogs/dsplaisted/how-to-make-portable-class-libraries-work-for-you) (blog gönderisi)<br />-   [MVVM ile taşınabilir sınıf kitaplığı kullanma](using-portable-class-library-with-model-view-view-model.md) <br />-   [Birden çok platformu hedefleyen kitaplıklar için uygulama kaynakları](app-resources-for-libraries-that-target-multiple-platforms.md) <br />-   [.Net taşınabilirlik Çözümleyicisi](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) (Visual Studio uzantısı)|
|Windows 8.1 ve Windows Phone 8,1 dışındaki platformlar için uygulama arasında kaynak kodu paylaşma|**Bağlantı olarak ekle** özelliği.<br /><br /> -Bu yaklaşım, bazı nedenlerle her iki uygulama için ortak olan ancak taşınmayan uygulama mantığı için uygundur. C# veya Visual Basic kodu için bu özelliği kullanabilirsiniz.<br />     Örneğin, Windows Phone 8 ve Windows 8 Windows Çalışma Zamanı API 'Leri paylaşır, ancak taşınabilir sınıf kitaplıkları bu platformlar için Windows Çalışma Zamanı desteklemez. `Add as link`Bir Windows Phone 8 uygulaması ve Windows 8 ' i hedefleyen bir Windows Mağazası uygulaması arasında ortak Windows çalışma zamanı kodu paylaşmak için ' i kullanabilirsiniz.<br /><br /> Ayrıntılar için bkz.<br /><br /> -   [Kodu farklı Ekle bağlantısı ile paylaşma](/previous-versions/windows/apps/jj714082(v=vs.105))<br />-   [Nasıl yapılır: bir projeye varolan öğeleri ekleme](/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))|
|.NET Framework kullanarak Windows Mağazası uygulamalarını yazma veya .NET Framework koddan Windows Çalışma Zamanı API 'Leri çağırma|.NET Framework C# veya Visual Basic kodunuzda **API 'leri Windows çalışma zamanı** ve Windows Mağazası uygulamaları oluşturmak için .NET Framework kullanın. İki platform arasındaki API farklarından haberdar olmanız gerekir. Ancak, bu farklılıklarla çalışmanıza yardımcı olacak sınıflar vardır.<br /><br /> Ayrıntılar için bkz.<br /><br /> -   [Windows Mağazası uygulamaları ve Windows Çalışma Zamanı için .NET Framework desteği](support-for-windows-store-apps-and-windows-runtime.md) <br />-   [Windows Çalışma Zamanı URI geçirme](passing-a-uri-to-the-windows-runtime.md) <br />-   <xref:System.IO.WindowsRuntimeStreamExtensions><br />-    <xref:System.WindowsRuntimeSystemExtensions>|
|Microsoft dışı platformlar için .NET Framework uygulamalar oluşturun|.NET Framework, **taşınabilir sınıf kitaplığı başvuru derlemeleri** ve bir Visual Studio uzantısı ya da Xamarin gibi üçüncü taraf aracı.<br /><br /> Ayrıntılar için bkz.<br /><br /> -   [Taşınabilir sınıf kitaplığı artık tüm platformlarda kullanılabilir.](https://devblogs.microsoft.com/dotnet/portable-class-library-pcl-now-available-on-all-platforms/) (blog gönderisi)<br />-   [Xamarin belgeleri](/xamarin)|
|Platformlar arası geliştirme için JavaScript ve HTML kullanma|Visual Studio 2013 'de **evrensel uygulama şablonları** , Windows 8.1 ve Windows Phone 8,1 Windows çalışma zamanı API 'lerine karşı geliştirmeye yönelik güncelleştirme 2. Şu anda platformlar arası uygulamalar geliştirmek için JavaScript ve HTML 'ı .NET Framework API 'Leri ile kullanamazsınız.<br /><br /> Ayrıntılar için bkz.<br /><br /> -   [JavaScript proje şablonları](/previous-versions/windows/apps/hh758331(v=win.10))<br />-   [JavaScript kullanarak bir Windows Çalışma Zamanı uygulamasının Windows Phone için taşıma](/previous-versions/windows/apps/dn636144(v=win.10))|
