---
title: Tek bir alt öğe alma (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 0e10cf230a73e6419f2d9c663766f9a24a0930af
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347470"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="339f8-102">Tek bir alt öğe alma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="339f8-102">How to retrieve a single child element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="339f8-103">Bu konu, alt öğenin adı verildiğinde tek bir alt öğenin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="339f8-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="339f8-104">Alt öğenin adını bildiğiniz ve bu ada sahip yalnızca bir öğe olduğunda, bir koleksiyon yerine yalnızca bir öğe almak kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="339f8-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="339f8-105"><xref:System.Xml.Linq.XContainer.Element%2A> yöntemi, belirtilen <xref:System.Xml.Linq.XName>ile ilk alt <xref:System.Xml.Linq.XElement> döndürür.</span><span class="sxs-lookup"><span data-stu-id="339f8-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="339f8-106">Visual Basic tek bir alt öğe almak istiyorsanız, yaygın bir yaklaşım XML özelliğini kullanmak ve sonra dizi dizin oluşturucu gösterimini kullanarak ilk öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="339f8-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="339f8-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="339f8-107">Example</span></span>  
 <span data-ttu-id="339f8-108">Aşağıdaki örnek <xref:System.Xml.Linq.XContainer.Element%2A> yönteminin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="339f8-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="339f8-109">Bu örnek, `po` adlı XML ağacını alır ve `Comment`adlı ilk öğeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="339f8-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="339f8-110">Visual Basic örnek, tek bir öğeyi almak için dizi dizin oluşturucu gösterimini kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="339f8-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="339f8-111">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="339f8-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="339f8-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="339f8-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="339f8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="339f8-113">Example</span></span>  
 <span data-ttu-id="339f8-114">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="339f8-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="339f8-115">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="339f8-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="339f8-116">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında tipik satın alma siparişi](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="339f8-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="339f8-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="339f8-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="339f8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="339f8-118">See also</span></span>

- [<span data-ttu-id="339f8-119">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="339f8-119">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
