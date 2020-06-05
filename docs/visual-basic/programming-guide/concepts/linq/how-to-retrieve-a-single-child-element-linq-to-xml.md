---
title: 'Nasıl yapılır: Tek Bir Alt Öğe Alma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
ms.openlocfilehash: ab28ddd960374b22f44ac0c8fc7bddfe0608b8c5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397849"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a><span data-ttu-id="4e404-102">Nasıl yapılır: tek bir alt öğe alma (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e404-102">How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="4e404-103">Bu konu, alt öğenin adı verildiğinde tek bir alt öğenin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4e404-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="4e404-104">Alt öğenin adını bildiğiniz ve bu ada sahip yalnızca bir öğe olduğunda, bir koleksiyon yerine yalnızca bir öğe almak kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4e404-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="4e404-105"><xref:System.Xml.Linq.XContainer.Element%2A>Yöntemi, belirtilen ilk alt öğesini döndürür <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="4e404-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="4e404-106">Visual Basic tek bir alt öğe almak istiyorsanız, yaygın bir yaklaşım XML özelliğini kullanmak ve sonra dizi dizin oluşturucu gösterimini kullanarak ilk öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="4e404-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e404-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e404-107">Example</span></span>  
 <span data-ttu-id="4e404-108">Aşağıdaki örnek yönteminin kullanımını gösterir <xref:System.Xml.Linq.XContainer.Element%2A> .</span><span class="sxs-lookup"><span data-stu-id="4e404-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="4e404-109">Bu örnek adlı XML ağacını alır `po` ve adlı ilk öğeyi bulur `Comment` .</span><span class="sxs-lookup"><span data-stu-id="4e404-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="4e404-110">Visual Basic örnek, tek bir öğeyi almak için dizi dizin oluşturucu gösterimini kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e404-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="4e404-111">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4e404-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="4e404-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4e404-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="4e404-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e404-113">Example</span></span>  
 <span data-ttu-id="4e404-114">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e404-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="4e404-115">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4e404-115">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="4e404-116">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında tipik satın alma siparişi](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="4e404-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="4e404-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4e404-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e404-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e404-118">See also</span></span>

- [<span data-ttu-id="4e404-119">LINQ to XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e404-119">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
