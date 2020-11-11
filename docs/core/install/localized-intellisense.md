---
title: Yerelleştirilmiş IntelliSense dosyalarını yükler
description: Geliştirme makinenizi, Visual Studio 'daki .NET 5 + projeleri (.NET Core dahil) için yerelleştirilmiş IntelliSense dosyalarını kullanacak şekilde ayarlamayı öğrenin.
ms.date: 11/06/2020
ms.openlocfilehash: 45eeae12ca79179cacb3d48fca28118de70e0a4f
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506772"
---
# <a name="how-to-install-localized-intellisense-files-for-net"></a>.NET için yerelleştirilmiş IntelliSense dosyalarını nasıl yükleyeceğiniz

[IntelliSense](/visualstudio/ide/using-intellisense) , Visual Studio gibi farklı tümleşik geliştirme ortamlarında (ides) kullanılabilen bir kod tamamlama yardımıdır. Varsayılan olarak, .NET projesi geliştirirken, SDK yalnızca IntelliSense dosyalarının Ingilizce sürümünü içerir. Bu makalede şunları açıklanmaktadır:

- Bu dosyaların yerelleştirilmiş sürümünü nasıl yükleyeceksiniz.
- Visual Studio yüklemesini farklı bir dil kullanacak şekilde değiştirme.

## <a name="prerequisites"></a>Ön koşullar

- [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya [.NET 5 SDK](https://dotnet.microsoft.com/download/dotnet/5.0)gibi sonraki bir sürüm.
- [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya sonraki bir sürümü.

## <a name="download-and-install-the-localized-intellisense-files"></a>Yerelleştirilmiş IntelliSense dosyalarını indirme ve yükleme

> [!IMPORTANT]
> Bu yordam, IntelliSense dosyalarını .NET yükleme klasörüne kopyalamak için yönetici iznine sahip olmanızı gerektirir.

1. [IntelliSense dosyalarını indirme](https://dotnet.microsoft.com/download/intellisense) sayfasına gidin.

1. Kullanmak istediğiniz dil ve sürüm için IntelliSense dosyasını indirin.

1. ZIP dosyasının içeriğini ayıklayın.

1. .NET IntelliSense klasörüne gidin.

   1. .NET yükleme klasörüne gidin. Varsayılan olarak, *%ProgramFiles%\dotnet\packs* altındadır.
   1. IntelliSense 'i yüklemek istediğiniz SDK 'yı seçin ve ilişkili yola gidin. Aşağıdaki seçenekler mevcuttur:

      | SDK türü              | Yol                               |
      |-----------------------|------------------------------------|
      | .NET 5 + ve .NET Core | *Microsoft. NETCore. app. ref*        |
      | Windows Masaüstü       | *Microsoft. WindowsDesktop. app. ref* |
      | .NET Standard         | *NETStandard. Library. ref*          |

   1. Yerelleştirilmiş IntelliSense 'i yüklemek istediğiniz sürüme gidin. Örneğin, *5.0.0*.
   1. *Ref* klasörünü açın.
   1. Bilinen ad klasörünü açın. Örneğin, *net 5.0*.

   Bu nedenle, gittiğiniz yolun tam yolu *C:\Program Files\dotnet\packs\Microsoft.NETCore.app.Ref\5.0.0\ref\net5.0* şuna benzer.

1. Yeni açtığınız bilinen ad klasörünün içinde bir alt klasör oluşturun. Klasörün adı, hangi dili kullanmak istediğinizi belirtir. Aşağıdaki tabloda farklı seçenekler verilmiştir:

   | Dil              | Klasör adı |
   | --------------------- | ----------- |
   | Brezilya Portekizcesi  | *pt-br*     |
   | Çince (Basitleştirilmiş)  | *zh-Hans*   |
   | Çince (Geleneksel) | *zh-Hant*   |
   | Fransızca                | *kesir*        |
   | Almanca                | *seçimini*        |
   | İtalyanca               | *içerdiği*        |
   | Japonca              | *Sofya*        |
   | Korece                | *dili*        |
   | Rusça               | *ru*        |
   | İspanyolca               | *es*        |

1. Adım 3 ' te ayıkladığınız *. xml* dosyalarını bu yeni klasöre kopyalayın. *. Xml* dosyaları SDK klasörleri tarafından bölünür, bu nedenle bunları 4. adımda SEÇTIĞINIZ eşleşen SDK 'ya kopyalayın.

## <a name="modify-visual-studio-language"></a>Visual Studio dilini değiştir

Visual Studio 'nun IntelliSense için farklı bir dil kullanabilmesi için, uygun dil paketini de yüklemelisiniz. Bu, [yükleme sırasında](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) veya daha sonra Visual Studio yüklemesi değiştirilerek yapılabilir. Seçtiğiniz dilde Visual Studio zaten yapılandırılmışsa, IntelliSense yüklemeniz hazırlayın.

### <a name="install-the-language-pack"></a>Dil paketini yükler

İstenen dil paketini kurulum sırasında yüklemediyseniz, dil paketini yüklemek için Visual Studio 'Yu aşağıdaki şekilde güncelleştirin:

> [!IMPORTANT]
> Visual Studio 'Yu yüklemek, güncelleştirmek veya değiştirmek için yönetici iznine sahip bir hesapla oturum açmalısınız. Daha fazla bilgi için bkz. [Kullanıcı izinleri ve Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).

1. Bilgisayarınızda Visual Studio Yükleyicisi bulun.

   Örneğin, Windows 10 çalıştıran bir bilgisayarda **Başlat** ' ı seçin ve ardından **Visual Studio yükleyicisi** olarak listelendiği **V** harfine gidin.

   ![Visual Studio Yükleyicisi Windows 'tan açın](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > Aşağıdaki konumda Visual Studio Yükleyicisi de bulabilirsiniz:
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   Devam etmeden önce yükleyiciyi güncelleştirmeniz gerekebilir. Bu durumda, istemleri izleyin.

1. Yükleyicide, dil paketini eklemek istediğiniz Visual Studio sürümünü bulun ve ardından **Değiştir** ' i seçin.

   ![Visual Studio 'Yu güncelleştirme veya değiştirme](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > Bir **değiştirme** düğmesi görmüyorsanız ancak bunun yerine bir **güncelleştirme** görüyorsanız, yüklemenizi değiştirebilmeniz için Visual Studio 'yu güncelleştirmeniz gerekir.
   > Güncelleştirme tamamlandıktan sonra **Değiştir** düğmesi görünmelidir.

1. **Dil paketleri** sekmesinde, yüklemek veya kaldırmak istediğiniz dilleri seçin veya seçimini kaldırın.

   ![Visual Studio dil paketleri sekmesi](./media/localized-intellisense/vs-modify-language-packs.png)

1. **Değiştir** 'i seçin. Güncelleştirme başlar.

### <a name="modify-language-settings-in-visual-studio"></a>Visual Studio 'da dil ayarlarını değiştirme

İstenen dil paketlerini yükledikten sonra, Visual Studio ayarlarınızı farklı bir dil kullanacak şekilde değiştirin:

1. Visual Studio'yu açın.

1. Başlangıç penceresinde, **kod olmadan devam et** ' i seçin.

1. Menü çubuğunda **Araçlar**  >  **Seçenekler** ' i seçin. Seçenekler iletişim kutusu açılır.

1. **Ortam** düğümü altında **Uluslararası ayarlar** ' ı seçin.

1. **Dil** açılan çubuğunda istediğiniz dili seçin. **Tamam ' ı** seçin.

1. Değişikliklerin etkili olması için Visual Studio 'Yu yeniden başlatmanız gerektiğini bildiren bir iletişim kutusu size bildirir. **Tamam ' ı** seçin.

1. Visual Studio’yu yeniden başlatın.

Bundan sonra, yeni yüklediğiniz IntelliSense dosyalarının sürümünü hedefleyen bir .NET projesi açtığınızda IntelliSense, beklendiği gibi çalışmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da IntelliSense](/visualstudio/ide/using-intellisense)
