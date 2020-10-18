---
title: İsteğe bağlı parametre türleri olarak kullanılan genel parametreler üzerinde sınıf kısıtlaması olmalıdır
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 5e0d4eaf7557eb9a544a8845299f3d69dbb78486
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163226"
---
# <a name="bc32124-generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>BC32124: isteğe bağlı parametre türleri olarak kullanılan genel parametreler sınıf kısıtlı olmalıdır

Bir yordam, bir başvuru türü olarak kısıtlanmış olmayan bir tür parametresi kullanan isteğe bağlı bir parametreyle bildirilmiştir.

 Her isteğe bağlı parametre için her zaman bir varsayılan değer sağlamanız gerekir. Parametresi bir başvuru türü ise, isteğe bağlı değer `Nothing` , herhangi bir başvuru türü için geçerli bir değer olan olmalıdır. Ancak, parametre bir değer türünde ise, bu tür Visual Basic tarafından önceden tanımlanan bir elemensel veri türü olmalıdır. Bunun nedeni, Kullanıcı tanımlı yapı gibi bir bileşik değer türünün geçerli bir varsayılan değer içermez.

 İsteğe bağlı bir parametre için bir tür parametresi kullandığınızda, geçerli bir varsayılan değer olmadan bir değer türü olasılığa engel olmak için bir başvuru türü olduğunu garanti etmeniz gerekir. Bu, tür parametresini `Class` anahtar sözcüğüyle veya belirli bir sınıfın adıyla sınırlandırmalısınız.

 **Hata kimliği:** BC32124

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Tür parametresini yalnızca bir başvuru türünü kabul edecek şekilde sınırlayın veya isteğe bağlı parametre için kullanmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [Tür Listesi](../statements/type-list.md)
- [Class Deyimi](../statements/class-statement.md)
- [İsteğe Bağlı Parametreler](../../programming-guide/language-features/procedures/optional-parameters.md)
- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Yapma](../nothing.md)
