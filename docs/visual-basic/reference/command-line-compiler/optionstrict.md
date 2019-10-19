---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 469e22aef9d746fc55e04ba884d17d60d8baa85a
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583083"
---
# <a name="-optionstrict"></a>-optionstrict

Örtük tür dönüşümlerini kısıtlamak için katı tür semantiğini zorlar.

## <a name="syntax"></a>Sözdizimi

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`  
İsteğe bağlı. @No__t_0 seçeneği örtük tür dönüştürmeyi kısıtlar. Bu seçenek için varsayılan değer `-optionstrict-` ' dır. @No__t_0 seçeneği `-optionstrict` aynıdır. Hem izin veren tür semantiğinin hem de kullanabilirsiniz.

`custom`  
Gerekli. Katı dil semantiklerine uyulmadığında uyar.

## <a name="remarks"></a>Açıklamalar

@No__t_0 yürürlükte olduğunda, yalnızca genişleyen tür dönüştürmeleri örtülü olarak yapılabilir. Bir tamsayı türü nesnesine `Decimal` tür nesnesi atama gibi örtülü daraltma türü dönüştürmeleri hata olarak bildirilir.

Örtük daraltma türü dönüştürmeleri için uyarı oluşturmak üzere `-optionstrict:custom` kullanın. Belirli uyarıları yok saymak için `-nowarn:numberlist` ve belirli uyarıları hata olarak değerlendirmek için `-warnaserror:numberlist` kullanın.

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Visual Studio IDE 'de-OptionStrict öğesini ayarlamak için

1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde Özellikler ' e tıklayın **.**

2. **Derle** sekmesine tıklayın.

3. **Seçenek katı** kutusunda değeri değiştirin.

### <a name="to-set--optionstrict-programmatically"></a>Program aracılığıyla ayarlama-OptionStrict

Bkz. [Option Strict deyimdir](../../../visual-basic/language-reference/statements/option-strict-statement.md).

## <a name="example"></a>Örnek

Aşağıdaki kod, `Test.vb` ' i katı tür semantiğini kullanarak derler.

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [-warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
