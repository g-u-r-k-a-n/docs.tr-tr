---
description: 'Hakkında daha fazla bilgi edinin: WHERE tümcesi (Visual Basic)'
title: Where Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 11f9a7e586a1fdea826df4fb34a7227747c8cebd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730323"
---
# <a name="where-clause-visual-basic"></a>Where Tümcesi (Visual Basic)

Bir sorgu için filtreleme koşulunu belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>Bölümler  

 `condition`  
 Gereklidir. Koleksiyonda geçerli öğenin değerlerinin çıkış koleksiyonuna dahil edilip edilmeyeceğini belirleyen bir ifade. İfade bir değere veya bir değerin eşdeğeri olarak değerlendirilmelidir `Boolean` `Boolean` . Koşul olarak değerlendirilirse `True` , öğe sorgu sonucuna dahil edilir; Aksi takdirde, öğe sorgu sonucundan çıkarılır.  
  
## <a name="remarks"></a>Açıklamalar  

 `Where`Yan tümcesi yalnızca belirli ölçütlere uyan öğeleri seçerek sorgu verilerini filtrelemenizi sağlar. Değerleri, `Where` yan tümcesinin değerlendirilmesine neden olan öğeler `True` sorgu sonucuna dahil edilir; diğer öğeler hariç tutulur. Bir `Where` yan tümcesinde kullanılan ifade `Boolean` `Boolean` , değeri sıfır olduğunda olarak değerlendirilen bir tamsayı gibi bir veya eşdeğerini vermelidir `False` . ,,,, `Where` Ve gibi mantıksal işleçleri kullanarak bir yan tümcede birden çok ifadeyi birleştirebilirsiniz `And` `Or` `AndAlso` `OrElse` `Is` `IsNot` .  
  
 Varsayılan olarak, sorgu ifadeleri erişilene kadar değerlendirilmez — Örneğin, veri bağladığında veya bir döngüyle aracılığıyla yinelendiğinde `For` . Sonuç olarak, bir `Where` sorgu erişilene kadar yan tümce değerlendirilmez. Yan tümcesinde kullanılan sorguya dış değerler varsa `Where` , `Where` sorgu yürütüldüğü sırada yan tümcesinde uygun değerin kullanıldığından emin olun. Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Bir `Where` yan tümce içindeki işlevleri, koleksiyondaki geçerli öğeden bir değer üzerinde bir hesaplama veya işlem gerçekleştirmek için çağırabilirsiniz. Bir yan tümcedeki bir işlevi çağırmak, `Where` sorgunun ne zaman tanımlanmadığında hemen yürütülmesine neden olabilir. Sorgu yürütme hakkında daha fazla bilgi için, bkz. [Ilk LINQ sorgunuzu yazma](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki sorgu ifadesi, `From` koleksiyondaki her bir nesne için bir Aralık değişkeni bildirmek üzere bir yan tümce kullanır `cust` `Customer` `customers` . `Where`Yan tümcesi, belirtilen bölgedeki müşterilere çıktıyı kısıtlamak için Aralık değişkenini kullanır. `For Each`Döngü, sorgu sonucunda her müşteri için şirket adını görüntüler.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek `And` `Or` , yan tümcesindeki ve mantıksal işleçleri kullanır `Where` .  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [From yan tümcesi](from-clause.md)
- [Select yan tümcesi](select-clause.md)
- [For Each...Next Deyimi](../statements/for-each-next-statement.md)
