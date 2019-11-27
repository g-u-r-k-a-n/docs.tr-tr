---
title: 'Nasıl yapılır: tek bir öznitelik alma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: 02afbc987cf9f55d16bb56912f3eaf45cd8c9a37
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347558"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="019ae-102">Nasıl yapılır: tek bir öznitelik alma (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="019ae-102">How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="019ae-103">Bu konu, öznitelik adı verilen bir öğenin tek bir özniteliğinin nasıl alınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="019ae-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="019ae-104">Bu, belirli bir özniteliğe sahip bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="019ae-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="019ae-105"><xref:System.Xml.Linq.XElement> sınıfının <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemi, belirtilen ada sahip <xref:System.Xml.Linq.XAttribute> döndürür.</span><span class="sxs-lookup"><span data-stu-id="019ae-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="019ae-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="019ae-106">Example</span></span>  
 <span data-ttu-id="019ae-107">Aşağıdaki örnekte <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemi kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="019ae-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 <span data-ttu-id="019ae-108">Bu örnek, `Phone`adlı ağaçtaki tüm alt öğeleri bulur ve sonra `type`adlı özniteliği bulur.</span><span class="sxs-lookup"><span data-stu-id="019ae-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="019ae-109">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="019ae-109">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="019ae-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="019ae-110">Example</span></span>  
 <span data-ttu-id="019ae-111">Özniteliğin değerini almak istiyorsanız, <xref:System.Xml.Linq.XElement> nesneleriyle yaptığınız gibi, bu özniteliği de çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="019ae-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="019ae-112">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="019ae-112">The following example demonstrates this.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 <span data-ttu-id="019ae-113">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="019ae-113">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="019ae-114">, <xref:System.Xml.Linq.XAttribute> sınıfının `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`ve `GUID?`için açık atama işleçleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="019ae-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="019ae-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="019ae-115">Example</span></span>  
 <span data-ttu-id="019ae-116">Aşağıdaki örnek, bir ad alanında olan bir özniteliği için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="019ae-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="019ae-117">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="019ae-117">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="019ae-118">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="019ae-118">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="019ae-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="019ae-119">See also</span></span>

- [<span data-ttu-id="019ae-120">LINQ to XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="019ae-120">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
