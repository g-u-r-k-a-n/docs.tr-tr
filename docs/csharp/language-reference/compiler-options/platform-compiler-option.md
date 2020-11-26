---
description: -Platform (C# derleyici seçenekleri)
title: -Platform (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 3fdb030dfc141b011f5faa827a4e4bb45ae38d19
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89466020"
---
# <a name="-platform-c-compiler-options"></a>-Platform (C# derleyici seçenekleri)

Ortak dil çalışma zamanının (CLR) hangi sürümünün derlemeyi çalıştırabileceği belirtir.

## <a name="syntax"></a>Söz dizimi

```console
-platform:string
```

## <a name="parameters"></a>Parametreler

`string` \
anycpu (varsayılan), anycpu32bitpreferred, ARM, x64, x86 veya Itanium.

## <a name="remarks"></a>Açıklamalar

- **anycpu** (varsayılan), derlemenizi herhangi bir platformda çalışacak şekilde derler. Uygulamanız mümkün olduğunda 64 bitlik bir işlem olarak çalışır ve yalnızca bu mod kullanılabilir olduğunda 32 bit 'e geri döner.

- **anycpu32bitpreferred** , derlemenizi herhangi bir platformda çalışacak şekilde derler. Uygulamanız, hem 64 bit hem de 32 bit uygulamaları destekleyen sistemlerde 32 bitlik modda çalışır. Bu seçeneği yalnızca .NET Framework 4,5 veya üstünü hedefleyen projeler için belirtebilirsiniz.

- **ARM** , derlemenizi GELIŞMIŞ bir RISC MAKINESI (ARM) işlemcisi olan bir bilgisayarda çalışacak şekilde derler.

- **ARM64** , derlemenizi, A64 yönerge kümesini destekleyen GELIŞMIŞ bir RISC MAKINESI (ARM) işlemcisi olan bir bilgisayarda 64 bitlik CLR tarafından çalışacak şekilde derler.

- **x64** , derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda 64 bitlik CLR tarafından çalıştırılacak şekilde derler.

- **x86** , derlemenizi 32 bit, x86 uyumlu CLR tarafından çalıştırılacak şekilde derler.

- **Itanium** , derlemenizi Itanium işlemcisi olan bir bilgisayarda 64 bitlik CLR tarafından çalıştırılacak şekilde derler.

64 bitlik bir Windows işletim sisteminde:

- İle derlenen derlemeler **-Platform: x86** , WOW64 altında çalışan 32 bitlik clr üzerinde yürütülür.

- **-Platform: anycpu** ile derlenen bir dll, yüklendiği IŞLEMLE aynı CLR üzerinde yürütülür.

- **-Platform: anycpu** ile derlenen yürütülebilir dosyalar 64 bitlik clr üzerinde yürütülür.

- **-Platform: anycpu32bitpreferred** ile derlenen yürütülebilir dosyalar 32 bit clr üzerinde yürütülür.

**Anycpu32bitpreferred** ayarı yalnızca yürütülebilir dosya için geçerlidir (. EXE) dosyalarını ve .NET Framework 4,5 veya üzeri bir sürümü gerektirir.

Windows 64 bit işletim sisteminde çalışacak bir uygulama geliştirme hakkında daha fazla bilgi için bkz. [64-bit uygulamalar](../../../framework/64-bit-apps.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Projenin **Özellikler** sayfasını açın.

2. **Yapı** özelliği sayfasına tıklayın.

3. **Platform hedefi** özelliğini değiştirin ve .NET Framework 4,5 veya sonraki bir sürümü hedefleyen projeler için **32 bit tercih** et onay kutusunu seçin veya temizleyin.

> [!NOTE]
> `-platform` Visual C# Express 'teki geliştirme ortamında kullanılamaz.

Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A> ..

## <a name="example"></a>Örnek

Aşağıdaki örnek, uygulamanın 64 bitlik bir Windows işletim sisteminde 64 bitlik CLR tarafından çalıştırılması gerektiğini belirtmek için **-Platform** seçeneğinin nasıl kullanılacağını gösterir.

```console
csc -platform:anycpu filename.cs
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
