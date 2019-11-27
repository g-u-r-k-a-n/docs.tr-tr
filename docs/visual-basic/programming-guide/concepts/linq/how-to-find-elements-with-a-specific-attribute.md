---
title: 'Nasıl yapılır: belirli bir özniteliğe sahip öğeleri bulma (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 4bb38d2c-bc7c-4196-8909-aaf41fb86b28
ms.openlocfilehash: ef8dd26d40f15d3d5a27f0ca5d62f7337f2054ca
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343682"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="68df6-102">Nasıl yapılır: belirli bir özniteliğe sahip öğeleri bulma (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68df6-102">How to: Find Elements with a Specific Attribute (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="68df6-103">Bazen belirli bir özniteliğe sahip olan tüm öğeleri bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68df6-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="68df6-104">Özniteliğin içeriğiyle ilgili endişeleriniz yok.</span><span class="sxs-lookup"><span data-stu-id="68df6-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="68df6-105">Bunun yerine, özniteliğinin varlığına göre ' ı seçmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="68df6-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="68df6-106">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="68df6-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="68df6-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="68df6-107">Example</span></span>  
 <span data-ttu-id="68df6-108">Aşağıdaki kod yalnızca `Select` özniteliği olan öğeleri seçer.</span><span class="sxs-lookup"><span data-stu-id="68df6-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
```vb  
Dim doc As XElement = _   
    <Root>  
        <Child1>1</Child1>  
        <Child2 Select='true'>2</Child2>  
        <Child3>3</Child3>  
        <Child4 Select='true'>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    From el In doc.Elements() _  
    Where el.@Select <> Nothing _  
    Select el  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = DirectCast(doc.XPathEvaluate _  
    ("./*[@Select]"), IEnumerable).Cast(Of XElement)()  
  
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
  
 <span data-ttu-id="68df6-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="68df6-109">This example produces the following output:</span></span>  
  
```console
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a><span data-ttu-id="68df6-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68df6-110">See also</span></span>

- [<span data-ttu-id="68df6-111">XPath kullanıcıları için LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68df6-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
