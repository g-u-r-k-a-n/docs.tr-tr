---
title: Not İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 08b091ccf6c50438b5ad9d6c445510112abe7418
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348301"
---
# <a name="not-operator-visual-basic"></a>Not İşleci (Visual Basic)
`Boolean` ifadesinde mantıksal Olumsuzlaştırma veya sayısal ifadede bit tabanlı Olumsuzlaştırma gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade.  
  
 `expression`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `Boolean` ifadeler için aşağıdaki tabloda `result` nasıl belirlendiği gösterilmektedir.  
  
|`expression`|`result` değeri|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Sayısal ifadeler için `Not` işleci herhangi bir sayısal ifadenin bit değerlerini tersine çevirir ve aşağıdaki tabloya göre `result` karşılık gelen biti ayarlar.  
  
|`expression` bit ise|`result` bit|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
## <a name="data-types"></a>Veri Türleri  
 Boolean Olumsuzlaştırma için sonucun veri türü `Boolean`. Bit düzeyinde olumsuzlama için, sonuç veri türü `expression`ile aynıdır. Ancak, ifade `Decimal`, sonuç `Long`olur.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Not` işleci *aşırı*yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Boolean` ifadesinde mantıksal olumsuzlama gerçekleştirmek için `Not` işlecini kullanır. Sonuç, ifadenin değerinin ters bir kısmını temsil eden bir `Boolean` değeridir.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 Yukarıdaki örnek, sırasıyla `False` ve `True`sonuçları üretir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sayısal bir ifadenin ayrı bitlerini mantıksal olarak gerçekleştirmek için `Not` işlecini kullanır. Sonuç deseninin biti, işaret biti dahil olmak üzere işlenen deseninin karşılık gelen bitin ters olarak ayarlanır.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 Yukarıdaki örnek sırasıyla – 11, – 9 ve – 7 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
