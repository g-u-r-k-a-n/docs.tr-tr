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
Indicates that a class or structure member is providing the implementation for a member defined in an interface.  
  
## <a name="remarks"></a>Açıklamalar  
The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md). You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.

If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.

## <a name="reimplementation"></a>Reimplementation  
In a derived class, you can reimplement an interface member that the base class has already implemented. This is different from overriding the base class member in the following respects:

- The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.
- You can reimplement the member with a different name.

The `Implements` keyword can be used in the following contexts:

- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Class Deyimi](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
