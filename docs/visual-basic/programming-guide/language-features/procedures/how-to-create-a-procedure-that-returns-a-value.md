---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: değer döndüren bir yordam oluşturma (Visual Basic)'
title: 'Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: fa2ea50febd1cc4e7aecf1e6f5cca671789b36fd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100467062"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma (Visual Basic)

`Function`Çağırma koduna bir değer döndürmek için bir yordam kullanırsınız.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Bir değer döndüren bir yordam oluşturmak için  
  
1. Diğer herhangi bir yordamın dışında, bir ifadesini ve `Function` ardından bir `End Function` ifadesini kullanın.  
  
2. İfadesinde, `Function` `Function` yordamın adı ile anahtar sözcüğünü ve ardından parantez içindeki parametre listesini izleyin.  
  
3. `As`Döndürülen değerin veri türünü belirtmek için bir yan tümcesiyle ayraçları izleyin.  
  
4. Yordamın kod deyimlerini `Function` ve deyimlerini arasına yerleştirin `End Function` .  
  
5. `Return`Çağırma koduna değeri döndürmek için bir ifade kullanın.  
  
     Aşağıdaki `Function` yordam, iki kenarı için değerler verildiğinde, doğru bir üçgenin en uzun tarafını veya hipotenüsü değerini hesaplar.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     Aşağıdaki örnekte, için tipik bir çağrı gösterilmektedir `hypotenuse` .  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Özellik Yordamları](./property-procedures.md)
- [İşleç Yordamları](./operator-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Function Deyimi](../../../language-reference/statements/function-statement.md)
- [Nasıl yapılır: Bir Yordamdan Değer Döndürme](./how-to-return-a-value-from-a-procedure.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma](./how-to-call-a-procedure-that-returns-a-value.md)
