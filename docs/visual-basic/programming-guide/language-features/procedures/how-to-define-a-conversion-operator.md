---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: dönüştürme Işleci tanımlama (Visual Basic)'
title: 'Nasıl yapılır: Bir Dönüşüm İşleci Tanımlama'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: c090e183e809974163625c4bfcf33536b1082b66
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481993"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Nasıl yapılır: Bir Dönüşüm İşleci Tanımlama (Visual Basic)

Bir sınıf veya yapı tanımladıysanız, sınıfınızın veya yapınızın türü ile başka bir veri türü (, veya gibi) arasında bir tür dönüştürme işleci tanımlayabilirsiniz `Integer` `Double` `String` .  
  
 Tür dönüşümünü sınıf veya yapı içinde [CType işlev](../../../language-reference/functions/ctype-function.md) yordamı olarak tanımlayın. Tüm dönüştürme yordamları olmalıdır `Public Shared` ve her birinin [genişletme](../../../language-reference/modifiers/widening.md) veya [daraltma](../../../language-reference/modifiers/narrowing.md)belirtmesi gerekir.  
  
 Bir sınıf veya yapı üzerinde işleç tanımlamak, işleci *aşırı yükleme* olarak da adlandırılır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, ve adlı bir yapı arasındaki dönüştürme işleçlerini tanımlar `digit` `Byte` .  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 Yapıyı aşağıdaki kodla test edebilirsiniz `digit` .  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşleç Yordamları](./operator-procedures.md)
- [Nasıl yapılır: İşleç Tanımlama](./how-to-define-an-operator.md)
- [Nasıl yapılır: Bir İşleç Yordamı Çağırma](./how-to-call-an-operator-procedure.md)
- [Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma](./how-to-use-a-class-that-defines-operators.md)
- [Operator Deyimi](../../../language-reference/statements/operator-statement.md)
- [Structure Yapısı](../../../language-reference/statements/structure-statement.md)
- [Nasıl yapılır: Yapıyı Bildirme](../data-types/how-to-declare-a-structure.md)
- [Örtük ve Açık Dönüştürmeler](../data-types/implicit-and-explicit-conversions.md)
- [Genişletme ve Daraltma Dönüşümleri](../data-types/widening-and-narrowing-conversions.md)
