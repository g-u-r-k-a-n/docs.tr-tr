---
title: LINQ to XML kullanarak sözlüklerle çalışma (C#)
description: LINQ to XML kullanarak sözlüklerle nasıl çalışacağınızı öğrenin. Bkz. sözlükleri XML ve XML 'e dönüştürme örnekleri diğer veri yapılarına geri.
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: bdba7a2b3dfc16fab1e239ac804c317dfefb7d9e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302626"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="8b3f9-104">LINQ to XML kullanarak sözlüklerle çalışma (C#)</span><span class="sxs-lookup"><span data-stu-id="8b3f9-104">How to work with dictionaries using LINQ to XML (C#)</span></span>
<span data-ttu-id="8b3f9-105">Çok sayıda veri yapısını XML 'e ve XML 'e diğer veri yapılarına dönüştürmek genellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b3f9-105">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="8b3f9-106">Bu konu, bir XML ve geri dönüştürerek bu genel yaklaşımın belirli bir uygulamasını gösterir <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="8b3f9-106">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b3f9-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b3f9-107">Example</span></span>  
 <span data-ttu-id="8b3f9-108">Bu örnek, bir sorgu projelerinin yeni <xref:System.Xml.Linq.XElement> nesne ve elde edilen koleksiyonun bir bağımsız değişken olarak kök nesnenin oluşturucusuna geçirildiği işlevsel oluşturma formunu kullanır <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="8b3f9-108">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
Dictionary<string, string> dict = new Dictionary<string, string>();  
dict.Add("Child1", "Value1");  
dict.Add("Child2", "Value2");  
dict.Add("Child3", "Value3");  
dict.Add("Child4", "Value4");  
XElement root = new XElement("Root",  
    from keyValue in dict  
    select new XElement(keyValue.Key, keyValue.Value)  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="8b3f9-109">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8b3f9-109">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="8b3f9-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b3f9-110">Example</span></span>  
 <span data-ttu-id="8b3f9-111">Aşağıdaki kod XML 'den bir sözlük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b3f9-111">The following code creates a dictionary from XML.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "Value1"),  
    new XElement("Child2", "Value2"),  
    new XElement("Child3", "Value3"),  
    new XElement("Child4", "Value4")  
);  
  
Dictionary<string, string> dict = new Dictionary<string, string>();  
foreach (XElement el in root.Elements())  
    dict.Add(el.Name.LocalName, el.Value);  
foreach (string str in dict.Keys)  
    Console.WriteLine("{0}:{1}", str, dict[str]);  
```  
  
 <span data-ttu-id="8b3f9-112">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="8b3f9-112">This code produces the following output:</span></span>  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
