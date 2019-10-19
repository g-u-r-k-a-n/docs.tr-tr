---
title: "'Extension' özniteliği yalnızca 'Module', 'Sub' veya 'Function' bildirimlerine uygulanabilir"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 2ed3a10cdf941bb8d1d7c00379736e04e8cad4d7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583178"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>'Extension' özniteliği yalnızca 'Module', 'Sub' veya 'Function' bildirimlerine uygulanabilir

Visual Basic bir veri türünü genişletmenin tek yolu standart bir modül içinde bir genişletme yöntemi tanımlamaktır. Genişletme yöntemi bir `Sub` yordamı veya bir `Function` yordamı olabilir. Tüm genişletme yöntemlerinin, <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanından `<Extension()>` uzantı özniteliğiyle işaretlenmesi gerekir. İsteğe bağlı olarak, bir genişletme yöntemi içeren bir modül aynı şekilde işaretlenebilir. Uzantı özniteliğinin başka bir kullanımı geçerli değil.

**Hata kimliği:** BC36550

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Uzantı özniteliğini kaldırın.

- Uzantınızı bir kapsayıcı modülünde tanımlanan bir yöntem olarak yeniden tasarlama.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `String` veri türü için bir `Print` yöntemi tanımlar.

```vb
Imports StringUtility
Imports System.Runtime.CompilerServices
Namespace StringUtility
    <Extension()>
    Module StringExtensions
        <Extension()>
        Public Sub Print (ByVal str As String)
            Console.WriteLine(str)
        End Sub
    End Module
End Namespace
```

## <a name="see-also"></a>Ayrıca bkz.

- [Özniteliklere genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Genişletme Yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)
