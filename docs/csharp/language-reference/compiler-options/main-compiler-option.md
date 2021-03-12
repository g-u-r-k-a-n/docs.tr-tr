---
description: -Main (C# derleyici seçenekleri)
title: -Main (C# derleyici seçenekleri)
ms.date: 03/08/2021
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 26ce1f48f9f3f88df8e002e5cf23010864f58290
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190079"
---
# <a name="-main-c-compiler-options"></a>-Main (C# derleyici seçenekleri)

Bu seçenek, birden fazla sınıf bir **Main** yöntemi içeriyorsa programa giriş noktasını içeren sınıfı belirtir.

## <a name="syntax"></a>Söz dizimi

```console
-main:class
```

## <a name="arguments"></a>Bağımsız değişkenler

 `class`  
 **Main** metodunu içeren tür.  
 Belirtilen sınıf adı tam olarak nitelenmiş olmalıdır; sınıfını içeren tam ad alanını ve ardından sınıf adını içermelidir. Örneğin, `Main` yöntemi `Program` `MyApplication.Core` ad alanındaki sınıfının içindeyse, derleyici seçeneğinin olması gerekir `-main:MyApplication.Core.Program` .

## <a name="remarks"></a>Açıklamalar

Derlemeniz bir [ana](../../programming-guide/main-and-command-args/index.md) yöntemle birden fazla tür içeriyorsa, programa giriş noktası olarak kullanmak istediğiniz **ana** yöntemi içeren türü belirtebilirsiniz.

Bu seçenek bir *. exe* dosyası derlenirken kullanım içindir.

> [!NOTE]
> Bu seçenek, bu proje bir veya daha fazla yöntem içerse bile, [en üst düzey deyimler](../../programming-guide/main-and-command-args/top-level-statements.md)içeren bir proje için kullanılamaz `Main` .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Projenin **Özellikler** sayfasını açın.

2. **Uygulama** Özellik sayfasına tıklayın.

3. **Başlangıç nesnesi** özelliğini değiştirin.

    Bu derleyici seçeneğini program aracılığıyla ayarlamak için, bkz <xref:VSLangProj80.ProjectProperties3.StartupObject%2A> ..

### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a>Bu derleyici seçeneğini *. csproj* dosyasını el ile düzenleyerek ayarlamak için

Bu seçeneği,. csproj dosyasını düzenleyerek ve bölümünün içine bir öğe ekleyerek ayarlayabilirsiniz `StartupObject` `PropertyGroup` . Örnek:

```xml
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a>Örnek

`t2.cs`Ve `t3.cs` ' de **Main** yönteminin bulunduğunu belirterek derleyin `Test2` :

```console
csc t2.cs t3.cs -main:Test2
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
