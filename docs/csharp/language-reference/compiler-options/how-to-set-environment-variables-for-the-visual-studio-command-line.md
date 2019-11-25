---
title: Visual Studio komut satırı için ortam değişkenlerini ayarlama
ms.date: 09/29/2017
f1_keywords:
- cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
ms.openlocfilehash: 3b69a92d28663bbbd34245435a69aea80d20fdc9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972836"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Visual Studio komut satırı için ortam değişkenlerini ayarlama

VsDevCmd. bat dosyası, komut satırı yapılarını etkinleştirmek için uygun ortam değişkenlerini ayarlar.

> [!NOTE]
> VsDevCmd. bat dosyası, Visual Studio 2017 ile sunulan yeni bir dosyadır. Visual Studio 2015 ve önceki sürümleri, VSVARS32. bat ' i aynı amaçla kullandı. Bu dosya \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools veya Program Files (x86) \Microsoft Visual Studio\\*Version*\Common7\Tools. ' de depolandı

Visual Studio 'nun geçerli sürümü, Visual Studio 'nun önceki bir sürümüne de sahip olan bir bilgisayarda yüklüyse, VsDevCmd. bat ve VSVARS32 kullanmamalısınız. Aynı komut Istemi penceresindeki farklı sürümlerden BAT. Bunun yerine, her sürüm için komutunu kendi penceresinde çalıştırmalısınız.

### <a name="to-run-vsdevcmdbat"></a>VsDevCmd. BAT dosyasını çalıştırmak için

1. **Başlangıç** menüsünde **VS 2017 için geliştirici komut istemi**açın.  **Visual Studio 2017** klasöründedir.

2. Yüklemenizin \Common7\Tools alt dizinini *sunan*\Common7\Tools veya \Program Files (x86) \Microsoft Visual Studio\\*Sürüm*\\*sunan*\Program Files\Microsoft Visual Studio\\\\*sürümüne* geçin.  (*Sürüm* , geçerli sürüm için *2017* . *Teklif* , *Enterprise*, *Professional* veya *Community*'den biridir.)

3. **Vsdevcmd. bat dosyasını vsdevcmd**yazarak çalıştırın.

    > [!CAUTION]
    > VsDevCmd. bat bilgisayardan bilgisayara farklılık gösterebilir. Eksik veya hasarlı bir VsDevCmd. bat dosyasını başka bir bilgisayardan VsDevCmd. bat ile değiştirmeyin. Bunun yerine, eksik dosyayı yerine koymak için kurulumu yeniden çalıştırın.

### <a name="available-options-for-vsdevcmdbat"></a>VsDevCmd. BAT için kullanılabilir seçenekler

VsDevCmd. BAT için kullanılabilir seçenekleri görmek için, `-help` seçeneğiyle komutunu çalıştırın:

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>Ayrıca bkz.

- [csc.exe Kullanarak Komut Satırı Derleme](./command-line-building-with-csc-exe.md)
