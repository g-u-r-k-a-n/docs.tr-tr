---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: değer döndüren bir yordam çağırma (Visual Basic)'
title: 'Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 74c7b6c9340537088ac631fc47f9ebf7b1a203cb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466750"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma (Visual Basic)

`Function`Yordam, çağırma koduna bir değer döndürür. Bunun adını ve bağımsız değişkenlerini atama deyiminin sağ tarafına veya bir ifadeye ekleyerek çağırabilirsiniz.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Bir ifade içindeki bir Işlev yordamını çağırmak için  
  
1. `Function`Yordam adını, bir değişkeni kullandığınız şekilde kullanın. Bir `Function` ifadede değişken veya sabit kullanabileceğiniz her yerde bir yordam çağrısı kullanabilirsiniz.  
  
2. Bağımsız değişken listesini çevrelemek için, parantez ile yordam adını izleyin. Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz. Ancak, parantezleri kullanmak kodunuzun okunmasını kolaylaştırır.  
  
3. Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin. Bağımsız değişkenleri `Function` yordamın ilgili parametreleri tanımladığı sırada girdiğinizden emin olun.  
  
     Alternatif olarak, bir veya daha fazla bağımsız değişkeni ada göre geçirebilirsiniz. Daha fazla bilgi için bkz. [bağımsız değişkenleri konuma ve ada göre geçirme](./passing-arguments-by-position-and-by-name.md).  
  
4. Yordamdan döndürülen değer, bir değişkenin veya sabitin değeri gibi ifadeye katılır.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Atama deyimindeki bir Işlev yordamını çağırmak için  
  
1. `Function`Atama deyimindeki eşittir () işaretinden sonra yordam adını kullanın `=` .  
  
2. Bağımsız değişken listesini çevrelemek için, parantez ile yordam adını izleyin. Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz. Ancak, parantezleri kullanmak kodunuzun okunmasını kolaylaştırır.  
  
3. Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin. Bağımsız değişkenleri, `Function` ilgili parametreleri ada göre geçirmediğiniz takdirde yordamın tanımladığı sırada girdiğinizden emin olun.  
  
4. Yordamdan döndürülen değer, atama ifadesinin sol tarafındaki değişken veya özellikte saklanır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:Microsoft.VisualBasic.Interaction.Environ%2A> bir işletim sistemi ortam değişkeninin değerini almak için Visual Basic çağırır. İlk satır `Environ` bir ifade içinde çağrı ve ikinci satır onu bir atama deyiminde çağırır. `Environ` değişken adını tek bağımsız değişkeni olarak alır. Bu, değişkenin değerini çağıran koda döndürür.  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşlev Yordamları](./function-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Function Deyimi](../../../language-reference/statements/function-statement.md)
- [Nasıl yapılır: Değer Döndüren Bir Yordam Oluşturma](./how-to-create-a-procedure-that-returns-a-value.md)
- [Nasıl yapılır: Bir Yordamdan Değer Döndürme](./how-to-return-a-value-from-a-procedure.md)
- [Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma](./how-to-call-a-procedure-that-does-not-return-a-value.md)
