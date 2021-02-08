---
description: ': = İşleci hakkında daha fazla bilgi edinin &amp; (Visual Basic)'
title: '&amp;= İşleci'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: ffc4de352ee29f4c7d18a257dd3699b37c668db7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774323"
---
# <a name="amp-operator-visual-basic"></a>&amp;= İşleci (Visual Basic)

Bir `String` ifadeyi bir `String` değişkene veya özelliğe ekler ve sonucu değişkene veya özelliğe atar.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Bölümler  

 `variableorproperty`  
 Gereklidir. Herhangi bir `String` değişken veya özellik.  
  
 `expression`  
 Gereklidir. Herhangi bir `String` ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 İşlecinin sol tarafındaki öğesi `&=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz. İşleci, sol tarafında bulunan `&=` `String` değişkeni ya da özelliği için sağ taraftaki ifadeyi birleştirir `String` ve sonucu, sol tarafındaki değişkene veya özelliğe atar.  
  
## <a name="overloading"></a>Aşırı Yükleme  

 [& işleci](concatenation-operator.md) *aşırı* yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. İşleci aşırı yüklemek `&` işlecin davranışını etkiler `&=` . Kodunuzun `&=` bir sınıf veya yapı üzerinde kullanması durumunda `&` , yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `&=` iki `String` değişkeni birleştirmek ve sonucu ilk değişkene atamak için işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [& Işleci](concatenation-operator.md)
- [+ = İşleci](addition-assignment-operator.md)
- [Atama Işleçleri](assignment-operators.md)
- [Birleştirme İşleçleri](concatenation-operators.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
