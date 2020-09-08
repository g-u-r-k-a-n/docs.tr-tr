---
title: Tek bir alt öğe alma-LINQ to XML
description: Belirtilen ada sahip ilk alt öğeyi alın. C# ' de XContainer. element ' i ve dizi dizin oluşturucu gösterimini Visual Basic ' de kullanabilirsiniz.
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: e557e82e4e5891d6890a0efb4973796050b75349
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553876"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml"></a><span data-ttu-id="1f1e0-104">Tek bir alt öğeyi alma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="1f1e0-104">How to retrieve a single child element (LINQ to XML)</span></span>

<span data-ttu-id="1f1e0-105">Bu makalede, belirli bir ada sahip ilk alt öğe olan tek bir alt öğenin nasıl alınacağını açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f1e0-105">This article explains how to retrieve a single child element, the first child element that has a specified name.</span></span> <span data-ttu-id="1f1e0-106">C# ' de bunu <xref:System.Xml.Linq.XContainer.Element%2A> yöntemiyle yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f1e0-106">In C# you do this with the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="1f1e0-107">Visual Basic, dizi Dizin Oluşturucu gösterimi ile bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f1e0-107">In Visual Basic you do it with array indexer notation.</span></span>

## <a name="example-retrieve-the-first-element-that-has-a-specified-name"></a><span data-ttu-id="1f1e0-108">Örnek: belirtilen ada sahip olan ilk öğeyi alma</span><span class="sxs-lookup"><span data-stu-id="1f1e0-108">Example: Retrieve the first element that has a specified name</span></span>

<span data-ttu-id="1f1e0-109">Aşağıdaki örnek `DeliveryNotes` örnek XML DOSYASıNDAKI XML belgesinden ilk öğeyi alır [: tipik satın alma siparişi](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="1f1e0-109">The following example retrieves the first `DeliveryNotes` element from the XML document in [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
XElement e = po.Element("DeliveryNotes");
Console.WriteLine(e);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim e As XElement = po.<DeliveryNotes>(0)
Console.WriteLine(e)
```

<span data-ttu-id="1f1e0-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1f1e0-110">This example produces the following output:</span></span>

```xml
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>
```

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="1f1e0-111">Örnek: bir ad alanında bulunan XML 'den alma</span><span class="sxs-lookup"><span data-stu-id="1f1e0-111">Example: Retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="1f1e0-112">Aşağıdaki örnek, yukarıdaki ile aynı şeyi yapar, ancak bir ad alanında bulunan XML için.</span><span class="sxs-lookup"><span data-stu-id="1f1e0-112">The following example does the same thing as the one above, but for XML that's in a namespace.</span></span> <span data-ttu-id="1f1e0-113">XML belgesi [örnek xml dosyasını kullanır: bir ad alanında tipik satın alma siparişi](sample-xml-file-typical-purchase-order-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="1f1e0-113">It uses the XML document [Sample XML file: Typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span> <span data-ttu-id="1f1e0-114">Ad alanları hakkında daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1f1e0-114">For more information about namespaces, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
XElement e = po.Element(aw + "DeliveryNotes");
Console.WriteLine(e);
```

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

<span data-ttu-id="1f1e0-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1f1e0-115">This example produces the following output:</span></span>

```xml
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>
```

## <a name="see-also"></a><span data-ttu-id="1f1e0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f1e0-116">See also</span></span>

- [<span data-ttu-id="1f1e0-117">LINQ to XML eksenlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="1f1e0-117">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
