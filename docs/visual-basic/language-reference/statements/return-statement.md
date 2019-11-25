---
title: Return Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: efc85a3a844898345aa2d16926ba0e35d7346d1b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333009"
---
# <a name="return-statement-visual-basic"></a>Return Deyimi (Visual Basic)
Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a>Part  
 `expression`  
 Required in a `Function`, `Get`, or `Operator` procedure. Expression that represents the value to be returned to the calling code.  
  
## <a name="remarks"></a>Açıklamalar  
 In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.  
  
 In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure. In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement. In an `Operator` procedure, you must use `Return expression`.  
  
 You can include as many `Return` statements as appropriate in the same procedure.  
  
> [!NOTE]
> The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes. A `Return` statement cannot be included in a `Finally` block.  
  
## <a name="example"></a>Örnek  
 The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Get Deyimi](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set Deyimi](../../../visual-basic/language-reference/statements/set-statement.md)
- [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit Deyimi](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
