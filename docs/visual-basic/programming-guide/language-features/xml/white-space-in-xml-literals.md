---
description: 'Hakkında daha fazla bilgi edinin: XML değişmez değerlerinde boşluk (Visual Basic)'
title: XML Değişmez Değerlerinde Boşluk
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 9b4134626c0ad1f7f4be2923573eb6058fa7687f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428122"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML Değişmez Değerlerinde Boşluk (Visual Basic)

Visual Basic derleyici bir nesne oluşturduğunda yalnızca bir XML sabit değerinden önemli boşluk karakterleri ekler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Önemli boşluk karakterleri dahil değildir.  
  
## <a name="significant-and-insignificant-white-space"></a>Önemli ve çok önemli boşluk  

 XML değişmez değerlerinde boşluk karakterleri yalnızca üç alanda önemlidir:  
  
- Bir öznitelik değeri olduğunda.  
  
- Bir öğenin metin içeriğinin bir parçası olduklarında ve metin diğer karakterleri de içeriyorsa.  
  
- Bir öğenin metin içeriği için gömülü bir ifadede olduklarında.  
  
 Aksi halde, derleyici boşluk karakterlerini önemli olarak değerlendirir ve daha sonra [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] değişmez değer için nesnesine içermez.  
  
 Bir XML sabit değerinde boş bir boşluk eklemek için, boşluk içeren bir dize sabit değeri içeren gömülü bir ifade kullanın.  
  
> [!NOTE]
> `xml:space`Öznitelik BIR XML öğesi değişmez değerinde görünürse, Visual Basic derleyici nesnedeki özniteliği içerir <xref:System.Xml.Linq.XElement> , ancak bu özniteliği eklemek derleyicinin boşluk olarak nasıl davrandığını değiştirmez.  
  
## <a name="examples"></a>Örnekler  

 Aşağıdaki örnek, Outer ve Inner olmak üzere iki XML öğesi içerir. Her iki öğe de metin içeriklerinde boşluk içeriyor. Dış öğedeki boşluk, yalnızca boşluk ve bir XML öğesi içerdiği için çok önemlidir. İç öğedeki boşluk, boşluk ve metin içerdiğinden önemlidir.  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 Çalıştırıldığında, bu kod aşağıdaki metni görüntüler.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de XML Oluşturma](creating-xml.md)
