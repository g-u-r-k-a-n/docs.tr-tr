---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: değerde değişmez bir değişken oluşturma (Visual Basic)'
title: 'Nasıl yapılır: Değeri Değişmeyen Bir Değişken Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 0392a27249de3bf604a73c8f8aaa16caf6f1c3e2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481941"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Nasıl yapılır: Değeri Değişmeyen Bir Değişken Oluşturma (Visual Basic)

Değerini değiştirolmayan bir değişken kavramı, çelişkili gibi görünebilir. Ancak, bir sabit değer mümkün olmadığında ve sabit bir değere sahip bir değişken olması faydalı olduğunda durumlar vardır. Böyle bir durumda, [salt okunur](../../../language-reference/modifiers/readonly.md) anahtar sözcüğüyle bir üye değişkeni tanımlayabilirsiniz.

[Const ifadesini](../../../language-reference/statements/const-statement.md) aşağıdaki koşullarda bir sabit değer bildirmek ve atamak için kullanamazsınız:

- `Const`İfade, kullanmak istediğiniz veri türünü kabul etmiyor

- Derleme zamanında değeri bilemezsiniz

- Derleme zamanında sabit değeri hesaplayamıyor

### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Değerde değişiklik olmayan bir değişken oluşturmak için

1. Modül düzeyinde, [Dim ifadesiyle](../../../language-reference/statements/dim-statement.md)bir üye değişkeni bildirin ve [salt okunur](../../../language-reference/modifiers/readonly.md) anahtar sözcüğünü ekleyin.

    ```vb
    Dim ReadOnly timeStarted
    ```

    `ReadOnly`Yalnızca bir üye değişkeninde belirtebilirsiniz. Bu, herhangi bir yordamın dışında değişkeni modül düzeyinde tanımlamanız gereken anlamına gelir.

2. Derleme zamanında değeri tek bir ifadede hesapladıysanız, deyimindeki bir başlatma yan tümcesini kullanın `Dim` . Eşittir işareti [](../../../language-reference/statements/as-clause.md) ( `=` ) ve ardından bir ifade gelen as yan tümcesini izleyin. Derleyicinin bu ifadeyi sabit bir değere değerlendirebilmesi için emin olun.

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    Bir değişkene yalnızca bir kez değer atayabilirsiniz `ReadOnly` . Bunu yaptığınızda, herhangi bir kod hiçbir zaman değerini değiştiremez.

    Derleme zamanında değeri bilemezsiniz veya tek bir ifadede derleme zamanında hesapladıysanız, yine de bir oluşturucuda çalışma zamanında atayabilirsiniz. Bunu yapmak için `ReadOnly` değişkeni sınıf veya yapı düzeyinde bildirmeniz gerekir. Bu sınıf veya yapı için oluşturucuda, değişkenin sabit değerini hesaplayın ve oluşturucuyu döndürmeden önce değişkenine atayın.

## <a name="see-also"></a>Ayrıca bkz.

- [WriteOnly](../../../language-reference/modifiers/writeonly.md)
- [Const Deyimi](../../../language-reference/statements/const-statement.md)
