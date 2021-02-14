---
description: ': Nasıl yapılır: XML alt öğelerine erişme (Visual Basic) hakkında daha fazla bilgi edinin'
title: 'Nasıl yapılır: XML Alt Öğelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: fad4d45853006762bc319b0ff8f9143ef13058da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433245"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="f44bc-103">Nasıl yapılır: XML Alt Öğelerine Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f44bc-103">How to: Access XML Child Elements (Visual Basic)</span></span>

<span data-ttu-id="f44bc-104">Bu örnek, bir XML öğesinde belirtilen bir ada sahip tüm XML alt öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f44bc-104">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="f44bc-105">Özellikle, <xref:System.Xml.Linq.XElement.Value%2A> koleksiyonda `name` alt eksen özelliğinin döndürdüğü ilk öğenin değerini almak için özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f44bc-105">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="f44bc-106">`name`Alt eksen özelliği, nesnesinde adlı tüm alt öğeleri alır `phone` `contact` .</span><span class="sxs-lookup"><span data-stu-id="f44bc-106">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="f44bc-107">Bu örnek, `phone` nesnesinde bulunan adlı tüm alt öğelere erişmek için alt eksen özelliğini de kullanır `phone` `contact` .</span><span class="sxs-lookup"><span data-stu-id="f44bc-107">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f44bc-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="f44bc-108">Example</span></span>  

 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="f44bc-109">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="f44bc-109">Compile the code</span></span>  

 <span data-ttu-id="f44bc-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f44bc-110">This example requires:</span></span>  
  
- <span data-ttu-id="f44bc-111"><xref:System.Xml.Linq>Ad alanına başvuru.</span><span class="sxs-lookup"><span data-stu-id="f44bc-111">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f44bc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f44bc-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f44bc-113">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="f44bc-113">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="f44bc-114">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="f44bc-114">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="f44bc-115">Visual Basic'de XML'e Erişme</span><span class="sxs-lookup"><span data-stu-id="f44bc-115">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="f44bc-116">XML</span><span class="sxs-lookup"><span data-stu-id="f44bc-116">XML</span></span>](index.md)
