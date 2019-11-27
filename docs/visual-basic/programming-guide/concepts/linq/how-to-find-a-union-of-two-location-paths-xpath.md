---
title: 'Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
ms.openlocfilehash: db9ba3f66bfa8643738203ec05a106bab4193fda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352980"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="82c2e-102">Nasıl yapılır: Iki konum yolunun birleşimini bulma (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82c2e-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="82c2e-103">XPath, iki XPath konum yolunun sonuçlarının birleşimini bulmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="82c2e-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="82c2e-104">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="82c2e-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="82c2e-105">Aynı sonuçları, <xref:System.Linq.Enumerable.Concat%2A> standart sorgu işlecini kullanarak elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82c2e-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82c2e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="82c2e-106">Example</span></span>  
 <span data-ttu-id="82c2e-107">Bu örnek, tüm `Category` öğelerini ve tüm `Price` öğeleri bulur ve bunları tek bir koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="82c2e-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="82c2e-108">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgusunun sonuçları sıralamak için <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> çağırdığına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="82c2e-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="82c2e-109">XPath ifadesi değerlendirmesi sonuçları da belge sırasıyla bulunur.</span><span class="sxs-lookup"><span data-stu-id="82c2e-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="82c2e-110">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: sayısal veri (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="82c2e-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="82c2e-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="82c2e-111">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82c2e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82c2e-112">See also</span></span>

- [<span data-ttu-id="82c2e-113">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82c2e-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
