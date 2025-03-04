---
description: Hakkında daha fazla bilgi edinin:-Resource (Visual Basic)
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 830d89ab4f4063aa12d12a5206b76e49c5355708
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474115"
---
# <a name="-resource-visual-basic"></a>-Kaynak (Visual Basic)

Bir derlemede yönetilen bir kaynak gömer.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

veya  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`filename`|Gereklidir. Çıkış dosyasına eklemek için kaynak dosyasının adı. Varsayılan olarak, `filename` derlemede ortaktır. Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.|  
|`identifier`|İsteğe bağlı. Kaynağın mantıksal adı; yüklemek için kullanılan ad. Varsayılan değer, dosyanın adıdır. İsteğe bağlı olarak, aşağıdaki gibi, derleme bildiriminde kaynağın genel mi yoksa özel mi olduğunu belirtebilirsiniz: `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>Açıklamalar  

 Kaynak `-linkresource` dosyasını çıkış dosyasına yerleştirmeksizin bir kaynağı derlemeye bağlamak için kullanın.  
  
 `filename`Örneğin, [Resgen.exe (kaynak dosya Oluşturucu)](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .NET Framework kaynak dosyası varsa, <xref:System.Resources> ad alanındaki üyelerle erişilebilir ( <xref:System.Resources.ResourceManager> daha fazla bilgi için bkz.). Çalışma zamanında diğer tüm kaynaklara erişmek için aşağıdaki yöntemlerden birini kullanın: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A> , <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> veya <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> .  
  
 Öğesinin kısa biçimi `-resource` `-res` .  
  
 Visual Studio IDE 'de nasıl ayarlanacağı hakkında bilgi için `-resource` bkz. [uygulama kaynaklarını yönetme (.net)](/visualstudio/ide/managing-application-resources-dotnet).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `In.vb` kaynak dosyasını derler ve iliştirir `Rf.resource` .  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [-win32resource](win32resource.md)
- [-linkresource (Visual Basic)](linkresource.md)
- [-target (Visual Basic)](target.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
