---
description: "Hakkında daha fazla bilgi edinin: DOM 'daki özniteliklere erişme"
title: DOM Özniteliklerine Erişim
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
ms.openlocfilehash: 6bb8370b101001c46bf10bceb3b9a935d0647293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642714"
---
# <a name="accessing-attributes-in-the-dom"></a><span data-ttu-id="f72ab-103">DOM Özniteliklerine Erişim</span><span class="sxs-lookup"><span data-stu-id="f72ab-103">Accessing Attributes in the DOM</span></span>

<span data-ttu-id="f72ab-104">Öznitelikleri, öğesinin alt öğesi değil, öğesinin özelliklerdir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-104">Attributes are properties of the element, not children of the element.</span></span> <span data-ttu-id="f72ab-105">Bu ayrım, XML Belge Nesne Modeli (DOM) eşdüzey, üst ve alt düğümlerine gitmek için kullanılan yöntemler nedeniyle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-105">This distinction is important because of the methods used to navigate sibling, parent, and child nodes of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="f72ab-106">Örneğin, **previouseşdüzey** ve **nexteşdüzey** Yöntemler bir öğeden bir özniteliğe veya öznitelikler arasında gezinmek için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="f72ab-106">For example, the **PreviousSibling** and **NextSibling** methods are not used to navigate from an element to an attribute or between attributes.</span></span> <span data-ttu-id="f72ab-107">Bunun yerine, bir özniteliği bir öğesinin özelliğidir ve bir öğesi tarafından sahiplenilir ve **ParentNode** özelliğine **sahip** değildir ve farklı gezinme yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-107">Instead, an attribute is a property of an element and is owned by an element, has an **OwnerElement** property and not a **parentNode** property, and has distinct methods of navigation.</span></span>

<span data-ttu-id="f72ab-108">Geçerli düğüm bir öğe olduğunda, öğesiyle ilişkili herhangi bir öznitelik olup olmadığını görmek için **HasAttribute** metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f72ab-108">When the current node is an element, use the **HasAttribute** method to see if there are any attributes associated with the element.</span></span> <span data-ttu-id="f72ab-109">Bir öğenin öznitelikleri olduğu bilindiğinde, özniteliklere erişmek için birden çok yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="f72ab-109">Once it is known that an element has attributes, there are multiple methods for accessing attributes.</span></span> <span data-ttu-id="f72ab-110">Öğesinden tek bir özniteliği almak için, **XmlElement** 'Nin **GetAttribute** ve **GetAttributeNode** yöntemlerini kullanabilirsiniz veya tüm öznitelikleri bir koleksiyonda elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f72ab-110">To retrieve a single attribute from the element, you can use the **GetAttribute** and **GetAttributeNode** methods of the **XmlElement** or you can obtain all the attributes into a collection.</span></span> <span data-ttu-id="f72ab-111">Koleksiyonu yinelemek gerekirse, koleksiyonu almak yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="f72ab-111">Obtaining the collection is useful if you need to iterate over the collection.</span></span> <span data-ttu-id="f72ab-112">Öğesinin tüm özniteliklerini istiyorsanız, tüm özniteliklerini bir koleksiyona almak için öğesinin **Attributes** özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f72ab-112">If you want all attributes from the element, use the **Attributes** property of the element to retrieve all the attributes into a collection.</span></span>

## <a name="retrieving-all-attributes-into-a-collection"></a><span data-ttu-id="f72ab-113">Tüm öznitelikleri bir koleksiyona alma</span><span class="sxs-lookup"><span data-stu-id="f72ab-113">Retrieving All Attributes into a Collection</span></span>

<span data-ttu-id="f72ab-114">Bir öğe düğümünün tüm özniteliklerinin bir koleksiyona yerleştirileceğini istiyorsanız, **XmlElement. Attributes** özelliğini çağırın.</span><span class="sxs-lookup"><span data-stu-id="f72ab-114">If you want all the attributes of an element node put into a collection, call the **XmlElement.Attributes** property.</span></span> <span data-ttu-id="f72ab-115">Bu, bir öğenin tüm özniteliklerini içeren **XmlAttributeCollection** 'ı alır.</span><span class="sxs-lookup"><span data-stu-id="f72ab-115">This gets the **XmlAttributeCollection** that contains all the attributes of an element.</span></span> <span data-ttu-id="f72ab-116">**XmlAttributeCollection** sınıfı **xmlnamednode** eşlemesinden devralır.</span><span class="sxs-lookup"><span data-stu-id="f72ab-116">The **XmlAttributeCollection** class inherits from the **XmlNamedNode** map.</span></span> <span data-ttu-id="f72ab-117">Bu nedenle, koleksiyonda bulunan Yöntemler ve özellikler, **XmlAttributeCollection** sınıfına özgü yöntemlere ve özelliklere ek olarak adlandırılmış bir düğüm eşlemesinde bulunan özellikleri içerir. Örneğin, **ItemOf** özelliği veya **append** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f72ab-117">Therefore, the methods and properties available on the collection include those available on a named node map in addition to methods and properties specific to the **XmlAttributeCollection** class, such as the **ItemOf** property or the **Append** method.</span></span> <span data-ttu-id="f72ab-118">Öznitelik koleksiyonundaki her öğe bir **XmlAttribute** düğümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f72ab-118">Each item in the attribute collection represents an **XmlAttribute** node.</span></span> <span data-ttu-id="f72ab-119">Bir öğedeki öznitelik sayısını bulmak için **XmlAttributeCollection**' ı alın ve koleksiyonda kaç **XmlAttribute** düğümünün olduğunu görmek için **Count** özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f72ab-119">To find the number of attributes on an element, get the **XmlAttributeCollection**, and use the **Count** property to see how many **XmlAttribute** nodes are in the collection.</span></span>

<span data-ttu-id="f72ab-120">Aşağıdaki kod örneği, bir öznitelik koleksiyonunun nasıl alınacağını ve döngü dizini için **Count** yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-120">The following code example shows how to retrieve an attribute collection and, using the **Count** method for the looping index, iterate over it.</span></span> <span data-ttu-id="f72ab-121">Kod bundan sonra koleksiyondan tek bir özniteliğin nasıl alınacağını ve değerinin nasıl görüntüleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-121">The code then shows how to retrieve a single attribute from the collection and display its value.</span></span>

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As XmlDocument = New XmlDocument()
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _
               "<title>The Handmaid's Tale</title>" & _
               "<price>14.95</price>" & _
               "</book>")

        ' Move to an element.
        Dim myElement As XmlElement = doc.DocumentElement

        ' Create an attribute collection from the element.
        Dim attrColl As XmlAttributeCollection = myElement.Attributes

        ' Show the collection by iterating over it.
        Console.WriteLine("Display all the attributes in the collection...")
        Dim i As Integer
        For i = 0 To attrColl.Count - 1
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)
            Console.Write("{0}", attrColl.ItemOf(i).Value)
            Console.WriteLine()
        Next

        ' Retrieve a single attribute from the collection; specifically, the
        ' attribute with the name "misc".
        Dim attr As XmlAttribute = attrColl("misc")

        ' Retrieve the value from that attribute.
        Dim miscValue As String = attr.InnerXml

        Console.WriteLine("Display the attribute information.")
        Console.WriteLine(miscValue)

    End Sub
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{

    public static void Main()
    {
        XmlDocument doc = new XmlDocument();
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +
                      "<title>The Handmaid's Tale</title>" +
                      "<price>14.95</price>" +
                      "</book>");

        // Move to an element.
        XmlElement myElement = doc.DocumentElement;

        // Create an attribute collection from the element.
        XmlAttributeCollection attrColl = myElement.Attributes;

        // Show the collection by iterating over it.
        Console.WriteLine("Display all the attributes in the collection...");
        for (int i = 0; i < attrColl.Count; i++)
        {
            Console.Write("{0} = ", attrColl[i].Name);
            Console.Write("{0}", attrColl[i].Value);
            Console.WriteLine();
        }

        // Retrieve a single attribute from the collection; specifically, the
        // attribute with the name "misc".
        XmlAttribute attr = attrColl["misc"];

        // Retrieve the value from that attribute.
        String miscValue = attr.InnerXml;

        Console.WriteLine("Display the attribute information.");
        Console.WriteLine(miscValue);

    }
}
```

<span data-ttu-id="f72ab-122">Bu örnek aşağıdaki çıktıyı görüntüler:</span><span class="sxs-lookup"><span data-stu-id="f72ab-122">This example displays the following output:</span></span>

<span data-ttu-id="f72ab-123">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="f72ab-123">**Output**</span></span>

<span data-ttu-id="f72ab-124">Koleksiyondaki tüm öznitelikleri görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="f72ab-124">Display all the attributes in the collection.</span></span>

```console
genre = novel
ISBN = 1-861001-57-5
misc = sale item
Display the attribute information.
sale item
```

<span data-ttu-id="f72ab-125">Bir öznitelik koleksiyonundaki bilgiler, ad veya dizin numarası ile alınabilir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-125">The information in an attribute collection can be retrieved by name or index number.</span></span> <span data-ttu-id="f72ab-126">Yukarıdaki örnekte, verilerin ada göre nasıl alınacağını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-126">The example above shows how to retrieve data by name.</span></span> <span data-ttu-id="f72ab-127">Sonraki örnek, verilerin dizin numarasına göre nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-127">The next example shows how to retrieve data by index number.</span></span>

<span data-ttu-id="f72ab-128">**XmlAttributeCollection** bir koleksiyon olduğundan ve ad ya da dizine göre yinelenebilir olduğundan, bu örnek sıfır tabanlı bir dizin kullanarak koleksiyonun ilk özniteliğini seçmeyi ve giriş olarak **baseuri.xml** aşağıdaki dosyayı kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-128">Because the **XmlAttributeCollection** is a collection and can be iterated over by name or index, this example shows selecting the first attribute out of the collection using a zero-based index and using the following file, **baseuri.xml**, as input.</span></span>

### <a name="input"></a><span data-ttu-id="f72ab-129">Giriş</span><span class="sxs-lookup"><span data-stu-id="f72ab-129">Input</span></span>

```xml
<!-- XML fragment -->
<book genre="novel">
  <title>Pride And Prejudice</title>
</book>
```

```vb
Option Explicit On
Option Strict On

Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()
        ' Create the XmlDocument.
        Dim doc As New XmlDocument()
        doc.Load("http://localhost/baseuri.xml")

        ' Display information on the attribute node. The value
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)
        Console.WriteLine("The value of the attribute:  {0}", attr.InnerText)
    End Sub 'Main
End Class 'Sample
```

```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{
  public static void Main()
  {
    // Create the XmlDocument.
    XmlDocument doc = new XmlDocument();

    doc.Load("http://localhost/baseuri.xml");

    // Display information on the attribute node. The value
    // returned for BaseURI is 'http://localhost/baseuri.xml'.
    XmlAttribute attr = doc.DocumentElement.Attributes[0];
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);
    Console.WriteLine("The value of the attribute:  {0}", attr.InnerText);
  }
}
```

## <a name="retrieving-an-individual-attribute-node"></a><span data-ttu-id="f72ab-130">Tek bir öznitelik düğümünü alma</span><span class="sxs-lookup"><span data-stu-id="f72ab-130">Retrieving an Individual Attribute Node</span></span>

<span data-ttu-id="f72ab-131">Bir öğeden tek bir öznitelik düğümü almak için <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f72ab-131">To retrieve a single attribute node from an element, the <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> method is used.</span></span> <span data-ttu-id="f72ab-132">**XmlAttribute** türünde bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="f72ab-132">It returns an object of type **XmlAttribute**.</span></span> <span data-ttu-id="f72ab-133">Bir **XmlAttribute** olduktan sonra, sınıfta bulunan tüm yöntemler ve Özellikler <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> Bu nesne üzerinde bulunur, örneğin **Owner öğesini** bulma.</span><span class="sxs-lookup"><span data-stu-id="f72ab-133">Once you have an **XmlAttribute**, all the methods and properties available in the <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> class are available on that object, such as finding the **OwnerElement**.</span></span>

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As XmlDocument = New XmlDocument()
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _
               "<title>The Handmaid's Tale</title>" & _
               "<price>14.95</price>" & _
               "</book>")

        ' Move to an element.
        Dim root As XmlElement
        root = doc.DocumentElement

        ' Get an attribute.
        Dim attr As XmlAttribute
        attr = root.GetAttributeNode("ISBN")

        ' Display the value of the attribute.
        Dim attrValue As String
        attrValue = attr.InnerXml
        Console.WriteLine(attrValue)

    End Sub
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;

 public class Sample
 {
      public static void Main()
      {
    XmlDocument doc = new XmlDocument();
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +
                   "<title>The Handmaid's Tale</title>" +
                   "<price>14.95</price>" +
                   "</book>");

    // Move to an element.
     XmlElement root = doc.DocumentElement;

    // Get an attribute.
     XmlAttribute attr = root.GetAttributeNode("ISBN");

    // Display the value of the attribute.
     String attrValue = attr.InnerXml;
     Console.WriteLine(attrValue);

    }
}
```

<span data-ttu-id="f72ab-134">Ayrıca, bir önceki örnekte gösterildiği gibi, öznitelik koleksiyonundan tek bir öznitelik düğümü alındığında da yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f72ab-134">You can also do as shown in the previous example, where a single attribute node is retrieved from the attribute collection.</span></span> <span data-ttu-id="f72ab-135">Aşağıdaki kod örneği, **DocumentElement** özelliği olarak da bilinen XML belge ağacının kökünden dizin numarasıyla tek bir özniteliği almak için nasıl bir kod satırı yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f72ab-135">The following code example shows how one line of code can be written to retrieve a single attribute by index number from the root of the XML document tree, also known as the **DocumentElement** property.</span></span>

```csharp
XmlAttribute attr = doc.DocumentElement.Attributes[0];
```

## <a name="see-also"></a><span data-ttu-id="f72ab-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f72ab-136">See also</span></span>

- [<span data-ttu-id="f72ab-137">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="f72ab-137">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
