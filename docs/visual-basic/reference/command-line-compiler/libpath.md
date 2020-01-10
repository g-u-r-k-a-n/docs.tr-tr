---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: 9a5822a097828f818da020735c3822e86eb3236b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716631"
---
# <a name="-libpath"></a>-libpath
Başvurulan derlemelerin konumunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`dirList`|Gerekli. Başvurulan bir derlemenin geçerli çalışma dizininde (derleyicisini çağırmakta olduğunuz dizin) veya ortak dil çalışma zamanının sistem dizininde bulunamaması halinde, derleyicinin aranacağı dizinlerin noktalı virgülle ayrılmış listesi. Dizin adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `-libpath` seçeneği, [-Reference](../../../visual-basic/reference/command-line-compiler/reference.md) seçeneğinin başvurduğu derlemelerin konumunu belirtir.  
  
 Derleyici, aşağıdaki sırada tam olarak nitelenen derleme başvurularını arar:  
  
1. Geçerli çalışma dizini. Bu, derleyicinin çağrıldığı dizindir.  
  
2. Ortak dil çalışma zamanı sistem dizini.  
  
3. `-libpath`tarafından belirtilen dizinler.  
  
4. LıB ortam değişkeni tarafından belirtilen dizinler.  
  
 `-libpath` seçeneği eklenebilir; bir defadan fazla belirtmek önceki değerlere ekler.  
  
 Derleme başvurusunu belirtmek için `-reference` kullanın.  
  
|Visual Studio tümleşik geliştirme ortamında Set-libpath|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Başvurular** sekmesine tıklayın.<br />3. **başvuru yolları...** düğmesine tıklayın.<br />4. **başvuru yolları** iletişim kutusunda dizin adını **klasör:** kutusuna girin.<br />5. **Klasör Ekle**'ye tıklayın.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir. exe dosyası oluşturmak için `T2.vb` derler. Derleyici, C: sürücüsünün kök dizininde ve derleme başvuruları için C: sürücüsünün yeni derlemeler dizininde çalışma dizinine bakar.  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
