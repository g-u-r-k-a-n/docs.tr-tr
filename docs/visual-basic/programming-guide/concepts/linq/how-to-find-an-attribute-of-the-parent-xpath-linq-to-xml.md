---
title: 'How to: Find an Attribute of the Parent (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
ms.openlocfilehash: c4cb2f2e52aeaa42fd69b83c19c47fd205d48cbc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352953"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="8de23-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8de23-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="8de23-103">This topic shows how to navigate to the parent element and find an attribute of it.</span><span class="sxs-lookup"><span data-stu-id="8de23-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="8de23-104">The XPath expression is:</span><span class="sxs-lookup"><span data-stu-id="8de23-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="8de23-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8de23-105">Example</span></span>  
 <span data-ttu-id="8de23-106">This example first finds an `Author` element.</span><span class="sxs-lookup"><span data-stu-id="8de23-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="8de23-107">It then finds the `id` attribute of the parent element.</span><span class="sxs-lookup"><span data-stu-id="8de23-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="8de23-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8de23-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()  
  
' LINQ to XML query  
Dim att1 As XAttribute = author.Parent.Attribute("id")  
  
' XPath expression  
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _  
    IEnumerable).Cast(Of XAttribute)().First()  
  
If att1 Is att2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(att1)  
```  
  
 <span data-ttu-id="8de23-109">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="8de23-109">This example produces the following output:</span></span>  
  
```console  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="8de23-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8de23-110">See also</span></span>

- [<span data-ttu-id="8de23-111">LINQ to XML for XPath Users (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8de23-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
