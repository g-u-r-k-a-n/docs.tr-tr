---
description: Daha fazla bilgi edinin:-optionfer
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: d45761914612a28788cc5c1a848d92238f05c162
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475922"
---
# <a name="-optioninfer"></a>-optioninfer

Değişken bildirimlerinde yerel tür çıkarımı kullanımını mümkün.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. `-optioninfer+`Yerel tür çıkarımını etkinleştirmek veya engellemek için belirtin `-optioninfer-` . `-optioninfer`Belirtilen değer olmadan seçeneği, ile aynıdır `-optioninfer+` . Anahtar mevcut olmadığında varsayılan değer `-optioninfer` de vardır `-optioninfer+` . Varsayılan değer Vbc. rsp yanıt dosyasında ayarlanır.|  
  
> [!NOTE]
> `-noconfig`Söz konusu seçeneği, vbc. rsp ' de belirtilenler yerine derleyicinin iç varsayılan değerlerini koruma için kullanabilirsiniz. Bu seçenek için varsayılan derleyicidir `-optioninfer-` .  
  
## <a name="remarks"></a>Açıklamalar  

 Kaynak kodu dosyası bir [seçenek çıkarımı bildirisi](../../language-reference/statements/option-infer-statement.md)içeriyorsa, ifade `-optioninfer` komut satırı derleyici ayarını geçersiz kılar.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Visual Studio IDE 'de set-OptionInfer  
  
1. **Çözüm Gezgini** bir proje seçin. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Derle** sekmesinde, **seçenek çıkarımı** kutusunda değeri değiştirin.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `test.vb` Yerel tür çıkarımı etkin ile derlenir.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [-optioncompare](optioncompare.md)
- [-optionexplicit](optionexplicit.md)
- [-optionstrict](optionstrict.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [Option Infer Deyimi](../../language-reference/statements/option-infer-statement.md)
- [Yerel Tür Arabirimi](../../programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [Derleme Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [-noconfig](noconfig.md)
- [Komut Satırından Derleme](building-from-the-command-line.md)
