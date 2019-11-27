---
title: 'Nasıl yapılır: bir alt öğenin alt öğelerini bulma (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: a958af40-f754-4409-85f9-7746978d4cb3
ms.openlocfilehash: beb949be521bfde70fbcdbcf18cebf49d7cc5a58
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344680"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="1740a-102">Nasıl yapılır: bir alt öğenin alt öğelerini bulma (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1740a-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="1740a-103">Bu konu başlığı altında, bir alt öğenin belirli bir ada sahip öğeleri nasıl alınacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1740a-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="1740a-104">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="1740a-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="1740a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1740a-105">Example</span></span>  
 <span data-ttu-id="1740a-106">Bu örnek, bir sözcük işleme belgesinin XML gösteriminden metin ayıklama sorunlarının benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="1740a-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="1740a-107">Önce tüm `Paragraph` öğelerini seçer ve ardından her bir `Paragraph` öğesinin tüm `Text` alt öğelerini seçer.</span><span class="sxs-lookup"><span data-stu-id="1740a-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="1740a-108">Bu, `Comment` öğesinin alt öğe `Text` öğelerini seçmeyin.</span><span class="sxs-lookup"><span data-stu-id="1740a-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Paragraph>  
            <Text>This is the start of</Text>  
        </Paragraph>  
        <Comment>  
            <Text>This comment is not part of the paragraph text.</Text>  
        </Comment>  
        <Paragraph>  
            <Annotation Emphasis='true'>  
                <Text> a sentence.</Text>  
            </Annotation>  
        </Paragraph>  
        <Paragraph>  
            <Text>This is a second sentence.</Text>  
        </Paragraph>  
    </Root>  
  
' LINQ to XML query  
Dim str1 As String = _  
    root.<Paragraph>...<Text>.Select(Function(ByVal s) s.Value). _  
    Aggregate( _  
        New StringBuilder(), _  
        Function(ByVal s, ByVal i) s.Append(i), _  
        Function(ByVal s) s.ToString())  
  
' XPath expression  
Dim str2 As String = DirectCast(root.XPathEvaluate("./Paragraph//Text/text()"), IEnumerable) _  
    .Cast(Of XText)().Select(Function(ByVal s) s.Value) _  
    .Aggregate( _  
        New StringBuilder(), _  
        Function(ByVal s, ByVal i) s.Append(i), _  
        Function(ByVal s) s.ToString())  
  
If str1 = str2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(str2)  
```  
  
 <span data-ttu-id="1740a-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1740a-109">This example produces the following output:</span></span>  
  
```console  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a><span data-ttu-id="1740a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1740a-110">See also</span></span>

- [<span data-ttu-id="1740a-111">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1740a-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
