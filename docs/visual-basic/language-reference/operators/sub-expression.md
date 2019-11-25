---
title: Alt İfade
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: d284e629ea0b0a4e9b6eb9e098612bb07c38723b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350906"
---
# <a name="sub-expression-visual-basic"></a>Alt İfade (Visual Basic)
Declares the parameters and code that define a subroutine lambda expression.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`parameterlist`|İsteğe bağlı. A list of local variable names that represent the parameters of the procedure. The parentheses must be present even when the list is empty. For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Gerekli. A single statement.|  
|`statements`|Gerekli. A list of statements.|  
  
## <a name="remarks"></a>Açıklamalar  
 A *lambda expression* is a subroutine that does not have a name and that executes one or more statements. You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`. For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Lambda İfadesi Sözdizimi  
 The syntax of a lambda expression resembles that of a standard subroutine. The differences are as follows:  
  
- A lambda expression does not have a name.  
  
- A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.  
  
- The body of a single-line lambda expression must be a statement, not an expression. The body can consist of a call to a sub procedure, but not a call to a function procedure.  
  
- In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.  
  
- Optional and `ParamArray` parameters are not permitted in lambda expressions.  
  
- Generic parameters are not permitted in lambda expressions.  
  
## <a name="example"></a>Örnek  
 Following is an example of a lambda expression that writes a value to the console. The example shows both the single-line and multiline lambda expression syntax for a subroutine. For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
- [Gevşek Temsilci Dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
