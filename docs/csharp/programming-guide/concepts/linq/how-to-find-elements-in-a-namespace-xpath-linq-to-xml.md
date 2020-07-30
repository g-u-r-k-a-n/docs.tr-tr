---
title: Bir ad alanında öğeleri bulma (XPath-LINQ to XML) (C#)
description: Bir XPath ifadesi kullanarak bir ad alanındaki öğeleri bulmayı öğrenin. İki ad alanı içeren bir XML ağacını okuyan bir örneğe bakın.
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: 3bf15c4183e3ca339fa7090c21baff83526e37d3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303237"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a><span data-ttu-id="747a9-104">Bir ad alanında öğeleri bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="747a9-104">How to find elements in a namespace (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="747a9-105">XPath ifadeleri, belirli bir ad alanındaki düğümleri bulabilir.</span><span class="sxs-lookup"><span data-stu-id="747a9-105">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="747a9-106">XPath ifadeleri ad alanlarını belirtmek için ad alanı öneklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="747a9-106">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="747a9-107">Ad alanı önekleri içeren bir XPath ifadesini ayrıştırmak için, uygulayan XPath yöntemlerine bir nesne geçirmeniz gerekir <xref:System.Xml.IXmlNamespaceResolver> .</span><span class="sxs-lookup"><span data-stu-id="747a9-107">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="747a9-108">Bu örnekte, kullanılır <xref:System.Xml.XmlNamespaceManager> .</span><span class="sxs-lookup"><span data-stu-id="747a9-108">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>

<span data-ttu-id="747a9-109">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="747a9-109">The XPath expression is:</span></span>

`./aw:*`

## <a name="example"></a><span data-ttu-id="747a9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="747a9-110">Example</span></span>

<span data-ttu-id="747a9-111">Aşağıdaki örnek, iki ad alanı içeren bir XML ağacını okur.</span><span class="sxs-lookup"><span data-stu-id="747a9-111">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="747a9-112"><xref:System.Xml.XmlReader>XML belgesini okumak için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="747a9-112">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="747a9-113">Daha sonra öğesinden <xref:System.Xml.XmlNameTable> <xref:System.Xml.XmlReader> ve arasında bir alır <xref:System.Xml.XmlNamespaceManager> <xref:System.Xml.XmlNameTable> .</span><span class="sxs-lookup"><span data-stu-id="747a9-113">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="747a9-114"><xref:System.Xml.XmlNamespaceManager>Öğeleri seçerken kullanır.</span><span class="sxs-lookup"><span data-stu-id="747a9-114">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>

```csharp
XmlReader reader = XmlReader.Create("ConsolidatedPurchaseOrders.xml");
XElement root = XElement.Load(reader);
XmlNameTable nameTable = reader.NameTable;
XmlNamespaceManager namespaceManager = new XmlNamespaceManager(nameTable);
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com");
IEnumerable<XElement> list1 = root.XPathSelectElements("./aw:*", namespaceManager);
IEnumerable<XElement> list2 =
    from el in root.Elements()
    where el.Name.Namespace == "http://www.adventure-works.com"
    select el;
if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

<span data-ttu-id="747a9-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="747a9-115">This example produces the following output:</span></span>

```output
Results are identical
<aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">
    <aw:ShippingAddress>
      <aw:Name>Chris Preston</aw:Name>
      <aw:Street>123 Main St.</aw:Street>
      <aw:City>Seattle</aw:City>
      <aw:State>WA</aw:State>
      <aw:Zip>98113</aw:Zip>
      <aw:Country>USA</aw:Country>
    </aw:ShippingAddress>
    <aw:BillingAddress>
      <aw:Name>Chris Preston</aw:Name>
      <aw:Street>123 Main St.</aw:Street>
      <aw:City>Seattle</aw:City>
      <aw:State>WA</aw:State>
      <aw:Zip>98113</aw:Zip>
      <aw:Country>USA</aw:Country>
    </aw:BillingAddress>
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>
    <aw:Item PartNum="LIT-01">
      <aw:ProductID>Litware Networking Card</aw:ProductID>
      <aw:Qty>1</aw:Qty>
      <aw:Price>20.99</aw:Price>
    </aw:Item>
    <aw:Item PartNum="LIT-25">
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>
      <aw:Qty>1</aw:Qty>
      <aw:Price>199.99</aw:Price>
    </aw:Item>
  </aw:PurchaseOrder>
```
