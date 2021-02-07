---
description: 'Daha fazla bilgi edinin: IsFalse Işleci (Visual Basic)'
title: IsFalse İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 190399dd29ba2d643bd26dfe4f6191211c9a3740
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665712"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse İşleci (Visual Basic)

Bir ifadenin olup olmadığını belirler `False` .  
  
 `IsFalse`Kodunuzda açıkça çağrı yapılamaz, ancak Visual Basic Derleyicisi bunu yan tümcelerden kod oluşturmak için kullanabilir `AndAlso` . Bir sınıf veya yapı tanımlayabilir ve sonra bir yan tümce içinde bu türden bir değişken kullanırsanız `AndAlso` , `IsFalse` Bu sınıf veya yapıda tanımlamanız gerekir.  
  
 Derleyici, `IsFalse` ve `IsTrue` işleçlerini *eşleşen bir çift* olarak değerlendirir. Diğer bir deyişle, bunlardan birini tanımlarsanız, diğerini de tanımlamanız gerekir.  
  
> [!NOTE]
> `IsFalse`İşleç *aşırı* yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, ve işleçleri için tanımlar içeren bir yapının ana hattını tanımlar `IsFalse` `IsTrue` .  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IsTrue İşleci](istrue-operator.md)
- [Nasıl yapılır: İşleç Tanımlama](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso İşleci](andalso-operator.md)
