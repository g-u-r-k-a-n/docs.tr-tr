---
title: Alt öğeleri bulma (XPath-LINQ to XML) (C#)
description: Bir XPath ifadesi kullanarak, belirli bir ada sahip olan alt öğeleri bulmayı öğrenin. Örnek XML dosyası kullanan bir kod örneğini gözden geçirin.
ms.date: 07/20/2015
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: c5a998a05f866203f3b684b8847a4a5647c12e5b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303276"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="6b831-104">Alt öğeleri bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6b831-104">How to find descendant elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="6b831-105">Bu konu, belirli bir ada sahip alt öğelerin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b831-105">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="6b831-106">XPath ifadesi `//Name` .</span><span class="sxs-lookup"><span data-stu-id="6b831-106">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b831-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b831-107">Example</span></span>  
 <span data-ttu-id="6b831-108">Bu örnek adlı tüm alt öğeleri bulur `Name` .</span><span class="sxs-lookup"><span data-stu-id="6b831-108">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="6b831-109">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: birden fazla satın alma siparişi (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6b831-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Root.Descendants("Name");  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="6b831-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6b831-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
