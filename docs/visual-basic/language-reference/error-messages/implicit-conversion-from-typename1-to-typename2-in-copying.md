---
description: "' ' <typename1> <typename2> ByRef ' parametresinin değerini <parametername> eşleşen bağımsız değişkene geri kopyalarken,: BC41999: ' ' ile ' ' arasında örtük dönüştürme hakkında daha fazla bilgi edinin."
title: "'<typename1>' 'ByRef' parametresinin değerini eşleşen bağımsız değişkene geri kopyalarken '<typename2>' türünden '<parametername>' türüne örtük dönüştürme"
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: debe9d248a41d1b5c1f541392a1846b8598c126f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796086"
---
# <a name="bc41999-implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a>BC41999: ' ' \<typename1> \<typename2> ByRef ' parametresinin değerini \<parametername> eşleşen bağımsız değişkene geri kopyalarken ' ' türünden ' ' türüne örtük dönüştürme.

Bir yordam, karşılık gelen parametresinden farklı bir türün [ByRef](../modifiers/byref.md) bağımsız değişkeniyle çağırılır.

 Bir bağımsız değişken geçirirseniz `ByRef` Visual Basic bazen bağımsız değişken değerini bir başvuruyu geçirmek yerine yordamda yerel bir değişkene kopyalar. Böyle bir durumda, yordam döndürüldüğünde Visual Basic, ardından yerel değişken değerini çağıran koddaki bağımsız değişkene geri kopyalamanız gerekir.

 Bir `ByRef` bağımsız değişken değeri yordama kopyalanırsa ve bağımsız değişkeni ve parametresi aynı türde ise, dönüştürme gerekli değildir. Ancak türler farklıysa Visual Basic her iki yönde de dönüştürmeniz gerekir. `CType`Bir yordam bağımsız değişkeninde veya parametresinde diğer dönüştürme anahtar sözcüklerini de kullanamadığı için, bu dönüştürme her zaman örtük olur.

 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **Hata kimliği:** BC41999

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Mümkünse, yordam parametresiyle aynı türde bir çağırma bağımsız değişkeni kullanın, bu nedenle Visual Basic herhangi bir dönüştürme yapması gerekmez.

- Parametre türünden farklı bir bağımsız değişken türü olan yordamı çağırmanız gerekiyorsa, ancak çağıran bağımsız değişkenine bir değer döndürmemelidir, yerine [ByVal](../modifiers/byval.md) olacak parametreyi tanımlayın `ByRef` .

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](../../programming-guide/language-features/procedures/index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [Örtük ve Açık Dönüştürmeler](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
