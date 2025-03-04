---
description: 'Hakkında daha fazla bilgi edinin: .NET Native genel sorun giderme'
title: .NET Yerel Genel Sorun Giderme
ms.date: 03/30/2017
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
ms.openlocfilehash: c486b1968036c42ac6d6e565abd9a9f7d795abc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738539"
---
# <a name="net-native-general-troubleshooting"></a>.NET Yerel Genel Sorun Giderme

Bu konuda, .NET Native ile uygulama geliştirirken karşılaşabileceğiniz olası sorunların nasıl giderileceği açıklanmaktadır.

- **Sorun:** Yapı çıkış pencereniz düzgün şekilde güncelleştirilmedi.

  **Çözüm:** Yapı çıkış penceresi, derleme tamamlanana kadar güncellenmez. Derleme süreleri birkaç dakika kadar sürebilir, bu nedenle güncelleştirmeleri görmede bir gecikmeyle karşılaşabilirsiniz.

- **Sorun:** Uygulamanızın ARM için perakende derleme süresi artmıştır.

  **Çözüm:** ARM cihazınıza bir uygulama dağıttığınızda .NET Native altyapısı çağrılır. Bu derleme, yansıma gibi statik olmayan semantiğinin çalışmaya devam etmesini sağlarken çok sayıda iyileştirme gerçekleştirir. Ayrıca, uygulamanın kullandığı .NET Framework bölümü, en iyi performans için ' de statik olarak bağlanır ve yerel koda de derlenmelidir. Bu derleme daha uzun sürer.

  Ancak, derleme süreleri standart bir geliştirme makinesindeki çoğu uygulama için yine de bir dakikalık standart derleme içindedir.  Genellikle, standart bir geliştirme makinesindeki .NET Framework için yerel görüntüleri oluşturmak birkaç dakika sürer.  Oluşturulan kodu ve .NET Framework dahil olmak üzere tüm iyileştirmelerin yanı sıra, uygulama derleme süreleri genellikle bir dakika veya iki olacaktır.

  Çok iş parçacıklı derlemeyi ve diğer iyileştirmeleri inceleyerek derleme performansını geliştirme konusunda çalışmaya devam ediyoruz.

- **Sorun:** Uygulamanızın .NET Native kullanılarak derlendiğini bilemezsiniz.

  **Çözüm:** .NET Native derleyicisi çağrılırsa, daha uzun bir derleme zamanı görürsünüz ve Görev Yöneticisi ILC.exe ve nutc_driver.exe gibi çeşitli .NET Native bileşen süreçlerini gösterir.

  Projenizi .NET Native ile başarılı bir şekilde oluşturduktan sonra, çıktıyı obj \\ *config* \  *Arch* \\ *ProjectName*. ılc\outaltında bulabilirsiniz.  Son yerel paket içerikleri bin \\ *yay* \\ *yapılandırması*\ appxaltında bulunabilir. Uygulamayı dağıttıysanız, son yerel paket içerikleri \Bin \\ *Arch* \\ *config*\appx altındadır.

- **Sorun:** .NET Native derlenen uygulamanız, .NET Native olmadan derlenerek oluşturmadığından, çalışma zamanı özel durumlarını (genellikle [MissingMetadataException](missingmetadataexception-class-net-native.md) veya [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumları) oluşturur.

  **Çözüm:** .NET Native özel durumlar, başka bir deyişle, yansıma aracılığıyla kullanılabilen meta verileri veya uygulama kodunu sağlamadığı için oluşturulur. (Daha fazla bilgi için bkz. [.NET Native ve derleme](net-native-and-compilation.md).) Özel durumu ortadan kaldırmak için, [çalışma zamanı yönergeleri (rd.xml) dosyanıza](runtime-directives-rd-xml-configuration-file-reference.md) bir giriş eklemeniz gerekir, böylece .NET Native araç zinciri, meta veri veya uygulama kodunu çalışma zamanında kullanılabilir hale getirir. Çalışma zamanı yönergeleri dosyanıza eklemek için gerekli girişi oluşturacak iki sorun giderici vardır:

  - Türler için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) .

  - Metotlar için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) .

  Daha fazla bilgi için bkz. [yansıma ve .NET Native](reflection-and-net-native.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma](migrating-your-windows-store-app-to-net-native.md)
