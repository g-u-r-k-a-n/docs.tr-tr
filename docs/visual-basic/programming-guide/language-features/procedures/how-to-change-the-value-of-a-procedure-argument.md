---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir yordam bağımsız değişkeninin değerini değiştirme (Visual Basic)'
title: 'Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: f8ccc80f7a9cb5d2b090fbc6b7f7e3423e5a1cae
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472585"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme (Visual Basic)

Bir yordamı çağırdığınızda, sağladığınız her bağımsız değişken yordamda tanımlanan parametrelerden birine karşılık gelir. Bazı durumlarda, yordam kodu, çağıran koddaki bağımsız değişkenin temelindeki değeri değiştirebilir. Diğer durumlarda yordam, bir bağımsız değişkenin yalnızca yerel kopyasını değiştirebilir.  
  
 Yordamı çağırdığınızda Visual Basic, [ByVal](../../../language-reference/modifiers/byval.md)' ı geçen her bağımsız değişkenin yerel bir kopyasını oluşturur. [ByRef](../../../language-reference/modifiers/byref.md)olarak geçen her bir bağımsız değişken için, Visual Basic yordam koduna, çağıran koddaki bağımsız değişkeni temel alan programlama öğesine doğrudan başvuru verir.  
  
 Çağıran koddaki temeldeki öğe değiştirilebilir bir öğedir ve bağımsız değişkeni geçmişse `ByRef` , yordam kodu, çağıran koddaki öğenin değerini değiştirmek için doğrudan başvurusunu kullanabilir.  
  
## <a name="changing-the-underlying-value"></a>Temel alınan değeri değiştirme  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>Çağıran koddaki yordam bağımsız değişkeninin temel alınan değerini değiştirmek için  
  
1. Yordam bildiriminde, bağımsız değişkenine karşılık gelen parametre için [ByRef](../../../language-reference/modifiers/byref.md) belirtin.  
  
2. Çağıran kodda bağımsız değişken olarak değiştirilebilir bir programlama öğesi geçirin.  
  
3. Çağıran kodda bağımsız değişkeni parantez içine bağımsız değişken listesine eklemeyin.  
  
4. Yordam kodunda, çağıran koddaki temel alınan öğeye bir değer atamak için parametre adını kullanın.  
  
 Tanıtım için örneğe bakın.  
  
## <a name="changing-local-copies"></a>Yerel kopyaları değiştirme  

 Çağıran koddaki temeldeki öğe değiştirilemeyen bir öğe ise veya bağımsız değişken geçirilmemişse `ByVal` yordam, çağıran koddaki değerini değiştiremez. Ancak yordam, böyle bir bağımsız değişkenin yerel kopyasını değiştirebilir.  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>Yordam kodundaki yordam bağımsız değişkeninin kopyasını değiştirmek için  
  
1. Yordam bildiriminde, bağımsız değişkenine karşılık gelen parametre için [ByVal](../../../language-reference/modifiers/byval.md) belirtin.  
  
     -veya-  
  
     Çağıran kodda bağımsız değişkenini bağımsız değişken listesinde parantez içine alın. Bu, karşılık gelen parametre belirtse bile, Visual Basic bağımsız değişkenini değere göre geçirmeye zorlar `ByRef` .  
  
2. Yordam kodunda, bağımsız değişkenin yerel kopyasına bir değer atamak için parametre adını kullanın. Çağıran koddaki temel alınan değer değiştirilmez.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir dizi değişkeni alan ve öğelerinde çalışan iki yordamı gösterir. `increase`Yordam her bir öğeye yalnızca bir tane ekler. `replace`Yordam parametreye yeni bir dizi atar `a()` ve sonra her öğeye bir tane ekler.  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 İlk `MsgBox` çağrı, "Artdıktan sonra (n): 11, 21, 31, 41" görüntüler. Dizi `n` bir başvuru türü olduğundan, `replace` geçirme mekanizması olsa bile üyelerini değiştirebilir `ByVal` .  
  
 İkinci `MsgBox` çağrıda "Replace (n): 101, 201, 301" görüntülenir. `n`Geçirildiği `ByRef` `replace` için, çağıran koddaki değişkeni değiştirebilir `n` ve buna yeni bir dizi atayabilirsiniz. `n`Bir başvuru türü olduğundan, `replace` üyelerini de değiştirebilir.  
  
 Yordamın, çağıran koddaki değişkenin kendisini değiştirmesini engelleyebilirsiniz. Bkz. [nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md).  
  
## <a name="compile-the-code"></a>Kodu derle  

 Bir değişkeni başvuruya göre geçirdiğinizde, `ByRef` Bu mekanizmayı belirtmek için anahtar sözcüğünü kullanmanız gerekir.  
  
 Visual Basic varsayılan değeri, bağımsız değişkenleri değere göre geçirmektir. Ancak, her bir belirtilen parametreye ilişkin [ByVal](../../../language-reference/modifiers/byval.md) veya [ByRef](../../../language-reference/modifiers/byref.md) anahtar sözcüğünü eklemek iyi bir programlama uygulamasıdır. Bu, kodunuzun okunmasını kolaylaştırır.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Bir yordamın, çağıran koddaki bağımsız değişkenin temelindeki değeri değiştirmesine izin vermek için her zaman potansiyel bir risk vardır. Bu değerin değiştirilmesini beklediğinizden ve kullanılmadan önce geçerliliği göz önünde denetlediğinizden emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Değer türleri ve başvuru türleri](../data-types/value-types-and-reference-types.md)
