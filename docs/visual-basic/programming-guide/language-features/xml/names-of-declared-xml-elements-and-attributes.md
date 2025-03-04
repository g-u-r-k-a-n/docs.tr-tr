---
description: 'Hakkında daha fazla bilgi edinin: belirtilen XML öğelerinin ve özniteliklerin adları (Visual Basic)'
title: Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 0c5d049a7d877a23562b91c5d7b3306d8e68ea3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100422737"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları (Visual Basic)

Bu konu, XML öğelerinin ve özniteliklerin XML sabit değerlerinde adlandırılması için Visual Basic yönergeleri sağlar.  Bir XML sabit değerinde yerel bir ad veya nitelikli bir ad belirtebilirsiniz. Nitelikli bir ad, bir XML ad alanı öneki, iki nokta üst üste ve yerel bir ad içerir. XML ad alanı önekleri hakkında daha fazla bilgi için bkz. [XML öğesi değişmez değeri](../../../language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>Kurallar  

 Visual Basic bir öğenin veya özniteliğin yerel adı aşağıdaki kurallara uymalıdır.  
  
- Bir ad alanı ile başlayabilir. Alfabetik bir karakter veya alt çizgi () ile başlamalıdır `_` .  
  
- Yalnızca alfabetik karakter, ondalık basamak, alt çizgi, nokta (.) ve kısa çizgi (-) içermelidir.  
  
- En fazla 1.024 karakter uzunluğunda olmalıdır.  
  
- Adlarda görünen iki nokta, ad alanı deyonumu gösterir. Bu nedenle, yalnızca belirli bir ad için bir XML ad alanı belirtmek için iki nokta üst üste kullanabilirsiniz.  
  
 Ayrıca, aşağıdaki kılavuza uymalısınız.  
  
- XML 1,0 belirtimi, tüm büyük/küçük harf çeşitlerinin "xml" dizesiyle başlayan tüm adları ayırır. Bu nedenle, bu adları öğe ve öznitelik adları için kullanmayın.  
  
### <a name="name-length-guidelines"></a>Ad uzunluğu yönergeleri  

 Pratik bir şekilde, öğenin yapısını açıkça tanımlarken bir ad mümkün olduğunca kısa olmalıdır. Bu, kodunuzun okunabilirliğini artırır ve satır uzunluğunu ve kaynak dosya boyutunu azaltır.  
  
 Bununla birlikte, adınız, öğeyi veya kodunuzun onu nasıl kullandığını yeterince tanımlamaz. Bu, kodunuzun okunabilirliğini açısından önemlidir. Başka birisi bunu anlamaya çalışıyorsa veya siz onu yazdıktan sonra uzun bir süre arıyorsanız, uygun öğe adları zamandan tasarruf edebilir.  
  
## <a name="case-sensitivity-in-names"></a>Adlarda büyük/küçük harf duyarlılığı  

 XML öğesi adları büyük/küçük harfe duyarlıdır. Bu, Visual Basic derleyici yalnızca alfabetik durumda farklılık gösteren iki adı karşılaştırırken, bunları farklı adlar olarak yorumladığı anlamına gelir. Örneğin, `ABC` ve `abc` ayrı öğelere başvuran olarak yorumlar.  
  
## <a name="xml-namespaces"></a>XML ad alanları  

 XML öğesi değişmez değeri oluştururken, öğe adı için XML ad alanı önekini belirtebilirsiniz. Daha fazla bilgi için bkz. [XML öğesi değişmez değeri](../../../language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de XML Oluşturma](creating-xml.md)
- [XML Öğesi Değişmez Değeri](../../../language-reference/xml-literals/xml-element-literal.md)
