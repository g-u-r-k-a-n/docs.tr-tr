---
title: Implements Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: f114aee75356e59eafd9d3ba6af9c64402cb374f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345867"
---
# <a name="implements-clause-visual-basic"></a>Implements Tümcesi (Visual Basic)
Bir sınıf veya yapı üyesinin, arabirim içinde tanımlanmış bir üye için uygulama sağladığını gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
`Implements` anahtar sözcüğü, [Implements ifadesiyle](../../../visual-basic/language-reference/statements/implements-statement.md)aynı değildir. Bir sınıf veya yapının bir veya daha fazla arabirim uyguladığını belirtmek için `Implements` ifadesini kullanın ve ardından her üye için, hangi arabirimin ve hangi üyenin uyguladığı için `Implements` anahtar sözcüğünü kullanırsınız.

Bir sınıf veya yapı bir arabirim uygularsa, [sınıf](../../../visual-basic/language-reference/statements/class-statement.md) veya [Yapı deyimden](../../../visual-basic/language-reference/statements/structure-statement.md)hemen sonra `Implements` ifadesini içermesi gerekir ve arabirim tarafından tanımlanan tüm üyeleri uygulamalıdır.

## <a name="reimplementation"></a>Yeniden uygulama  
Türetilmiş bir sınıfta, temel sınıfın zaten uygulanmış olduğu bir arabirim üyesini yeniden uygulayabilirsiniz. Bu, aşağıdaki gibi temel sınıf üyesini geçersiz kılmadan farklıdır:

- Temel sınıf üyesinin yeniden uygulanması için [geçersiz kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md) olması gerekmez.
- Üyeyi farklı bir adla yeniden uygulayabilirsiniz.

`Implements` anahtar sözcüğü aşağıdaki bağlamlarda kullanılabilir:

- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
