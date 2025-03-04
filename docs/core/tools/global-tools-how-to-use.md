---
title: "Öğretici: .NET küresel aracı 'nı yükleyip kullanma"
description: .NET aracını genel araç olarak yüklemeyi ve kullanmayı öğrenin.
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 01b773516da92fb16fb0f67fc6617e0c70d17c9d
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633901"
---
# <a name="tutorial-install-and-use-a-net-global-tool-using-the-net-cli"></a>Öğretici: .NET CLı kullanarak .NET genel aracını yükleyip kullanma

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

Bu öğreticide, genel bir aracın nasıl yükleneceği ve kullanılacağı öğretilir. [Bu serinin ilk öğreticisinde](global-tools-how-to-create.md)oluşturduğunuz bir aracı kullanırsınız.

## <a name="prerequisites"></a>Önkoşullar

* [Bu serinin ilk öğreticisini](global-tools-how-to-create.md)doldurun.

## <a name="use-the-tool-as-a-global-tool"></a>Aracı genel araç olarak kullanma

1. *Microsoft. botsay* proje klasöründeki [DotNet aracı install](dotnet-tool-install.md) komutunu çalıştırarak aracı paketten çalıştırın:

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   `--global`Parametresi, .net CLI 'nın araç ikililerini PATH ortam değişkenine otomatik olarak eklenen varsayılan bir konuma yüklemesini söyler.

   `--add-source`Parametresi, .net CLI 'nın, NuGet paketleri için ek bir kaynak akışı olarak *./nupkg* dizinini geçici olarak kullanmasını söyler. Paketinize, Nuget.org sitesinde değil, yalnızca *./nupkg* dizininde bulunduğunuzdan emin olmak için benzersiz bir ad verirsiniz.

   Çıktı, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösterir:

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Aracı çağır:

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > Bu komut başarısız olursa, yolu yenilemek için yeni bir Terminal açmanız gerekebilir.

1. [DotNet Aracı kaldırma](dotnet-tool-uninstall.md) komutunu çalıştırarak aracı kaldırın:

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>Aracı özel bir konumda yüklü olan küresel bir araç olarak kullanın

1. Aracı paketten yükler.

   Windows'da:

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   Linux veya macOS 'ta:

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   `--tool-path`Parametresi, .net CLI 'nın belirtilen konuma araç ikililerini yüklemesini söyler. Dizin yoksa, oluşturulur. Bu dizin, PATH ortam değişkenine otomatik olarak eklenmez.

   Çıktı, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösterir:

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Aracı çağır:

   Windows'da:

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   Linux veya macOS 'ta:

   ```console
   ~/bin/botsay hello from the bot
   ```

1. [DotNet Aracı kaldırma](dotnet-tool-uninstall.md) komutunu çalıştırarak aracı kaldırın:

   Windows'da:

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   Linux veya macOS 'ta:

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a>Sorun giderme

Öğreticiyi takip ederken bir hata mesajı alırsanız bkz. [.NET araç kullanım sorunlarını giderme](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir aracı bir genel araç olarak yüklediniz ve kullandınız. Aynı aracı yerel bir araç olarak yüklemek ve kullanmak için sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Yerel araçları yükleyip kullanma](local-tools-how-to-use.md)
