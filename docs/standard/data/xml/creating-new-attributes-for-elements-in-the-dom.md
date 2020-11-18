---
title: DOM Öğeleri için Yeni Öznitelikler Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
ms.openlocfilehash: 1cb37e47bedf955ea2c6f9faad628df2175fb703
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826033"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a><span data-ttu-id="a7471-102">DOM Öğeleri için Yeni Öznitelikler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a7471-102">Creating New Attributes for Elements in the DOM</span></span>

<span data-ttu-id="a7471-103">Yeni özniteliklerin oluşturulması diğer düğüm türlerini oluşturmaktan farklıdır, çünkü öznitelikler düğüm değildir, ancak bir öğe düğümünün özellikleri olduğundan ve öğesiyle ilişkili bir **XmlAttributeCollection** içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="a7471-103">Creating new attributes is different than creating other node types, because attributes are not nodes, but are properties of an element node and are contained in an **XmlAttributeCollection** associated with the element.</span></span> <span data-ttu-id="a7471-104">Bir öznitelik oluşturup bir öğeye iliştirmek için birden çok yol vardır:</span><span class="sxs-lookup"><span data-stu-id="a7471-104">There are multiple ways to create an attribute and attach it to an element:</span></span>

- <span data-ttu-id="a7471-105">Öğe düğümünü alın ve bu öğenin öznitelik koleksiyonuna bir öznitelik eklemek için **SetAttribute** kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7471-105">Get the element node and use **SetAttribute** to add an attribute to the attribute collection of that element.</span></span>

- <span data-ttu-id="a7471-106">**CreateAttribute** metodunu kullanarak bir **XmlAttribute** düğümü oluşturun, öğe düğümünü alın, sonra düğümü bu öğenin öznitelik koleksiyonuna eklemek için **SetAttributeNode** kullanın.</span><span class="sxs-lookup"><span data-stu-id="a7471-106">Create an **XmlAttribute** node using the **CreateAttribute** method, get the element node, then use **SetAttributeNode** to add the node to the attribute collection of that element.</span></span>

<span data-ttu-id="a7471-107">Aşağıdaki örnek **SetAttribute** yöntemi kullanılarak bir öğeye bir özniteliği nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="a7471-107">The following example shows how to add an attribute to an element using the **SetAttribute** method:</span></span>

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As New XmlDocument()
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _
                    "<title>Pride And Prejudice</title>" & _
                    "</book>")
        Dim root As XmlElement = doc.DocumentElement

        ' Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel")

        Console.WriteLine("Display the modified XML...")
        Console.WriteLine(doc.InnerXml)
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
        var doc = new XmlDocument();
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +
                    "<title>Pride And Prejudice</title>" +
                    "</book>");
        XmlElement root = doc.DocumentElement;

        // Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel");

        Console.WriteLine("Display the modified XML...");
        Console.WriteLine(doc.InnerXml);
    }
}
```

<span data-ttu-id="a7471-108">Aşağıdaki örnek, **CreateAttribute** yöntemi kullanılarak oluşturulan yeni bir özniteliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7471-108">The following example shows a new attribute being created using the **CreateAttribute** method.</span></span> <span data-ttu-id="a7471-109">Daha sonra, **SetAttributeNode** yöntemini kullanarak **Book** öğesinin öznitelik koleksiyonuna eklenen özniteliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7471-109">It then shows the attribute added to the attribute collection of the **book** element using the **SetAttributeNode** method.</span></span>

<span data-ttu-id="a7471-110">Aşağıdaki XML verildiğinde:</span><span class="sxs-lookup"><span data-stu-id="a7471-110">Given the following XML:</span></span>
  
```xml
<book genre='novel' ISBN='1-861001-57-5'>
<title>Pride And Prejudice</title>
</book>
```

<span data-ttu-id="a7471-111">Yeni bir öznitelik oluşturun ve bu değere bir değer verin:</span><span class="sxs-lookup"><span data-stu-id="a7471-111">create a new attribute and give it a value:</span></span>

```vb
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")
attr.Value = "WorldWide Publishing"
```

```csharp
XmlAttribute attr = doc.CreateAttribute("publisher");
attr.Value = "WorldWide Publishing";
```

<span data-ttu-id="a7471-112">ve öğesini öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a7471-112">and attach it to the element:</span></span>

```vb
doc.DocumentElement.SetAttributeNode(attr)
```

```csharp
doc.DocumentElement.SetAttributeNode(attr);
```

<span data-ttu-id="a7471-113">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="a7471-113">**Output**</span></span>

```xml
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">
<title>Pride And Prejudice</title>
</book>
```

<span data-ttu-id="a7471-114">Tam kod örneği adresinde bulunabilir <xref:System.Xml.XmlDocument.CreateAttribute%2A> .</span><span class="sxs-lookup"><span data-stu-id="a7471-114">The full code sample can be found at <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span></span>

<span data-ttu-id="a7471-115">Ayrıca, bir **XmlAttribute** düğümü oluşturabilir ve bunu koleksiyondaki uygun konuma yerleştirmek Için **InsertBefore** veya **InsertAfter** yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7471-115">You can also create an **XmlAttribute** node and use the **InsertBefore** or **InsertAfter** methods to place it in the appropriate position in the collection.</span></span> <span data-ttu-id="a7471-116">Öznitelik koleksiyonunda aynı ada sahip bir öznitelik zaten varsa, var olan **XmlAttribute** düğümü koleksiyondan kaldırılır ve yeni **XmlAttribute** düğümü eklenir.</span><span class="sxs-lookup"><span data-stu-id="a7471-116">If an attribute with the same name is already present in the attribute collection, the existing **XmlAttribute** node is removed from the collection and the new **XmlAttribute** node is inserted.</span></span> <span data-ttu-id="a7471-117">Bu, **SetAttribute** yöntemiyle aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="a7471-117">This performs the same way as the **SetAttribute** method.</span></span> <span data-ttu-id="a7471-118">Bu yöntemler, var olan bir düğümü bir parametre olarak, **InsertBefore** ve **InsertAfter** yapmak için başvuru noktası olarak alır.</span><span class="sxs-lookup"><span data-stu-id="a7471-118">These methods take, as a parameter, an existing node as a reference point to do the **InsertBefore** and **InsertAfter**.</span></span> <span data-ttu-id="a7471-119">Yeni düğümün nereye yerleştirileceğini belirten bir başvuru düğümü sağlamazsanız, **InsertAfter** yöntemi için varsayılan değer, koleksiyonun başlangıcına yeni düğüm eklemek olur.</span><span class="sxs-lookup"><span data-stu-id="a7471-119">If you do not provide a reference node indicating where to insert the new node, the default for the **InsertAfter** method is to insert the new node at the beginning of the collection.</span></span> <span data-ttu-id="a7471-120">Hiçbir başvuru düğümü sağlanmazsa, **InsertBefore** varsayılan konumu koleksiyonun sonunda olur.</span><span class="sxs-lookup"><span data-stu-id="a7471-120">The default position for the **InsertBefore**, if no reference node is provided, is at the end of the collection.</span></span>

<span data-ttu-id="a7471-121">Öznitelikleri için bir **XmlNamedNodeMap** oluşturduysanız, yöntemini kullanarak bir özniteliği ada göre ekleyebilirsiniz <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A> .</span><span class="sxs-lookup"><span data-stu-id="a7471-121">If you created an **XmlNamedNodeMap** of attributes, you can add an attribute by name using the <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A> method.</span></span> <span data-ttu-id="a7471-122">Daha fazla bilgi için bkz. [NamedNodeMaps ve NodeLists Içindeki düğüm koleksiyonları](node-collections-in-namednodemaps-and-nodelists.md).</span><span class="sxs-lookup"><span data-stu-id="a7471-122">For more information, see [Node Collections in NamedNodeMaps and NodeLists](node-collections-in-namednodemaps-and-nodelists.md).</span></span>

## <a name="default-attributes"></a><span data-ttu-id="a7471-123">Varsayılan öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7471-123">Default attributes</span></span>

<span data-ttu-id="a7471-124">Varsayılan bir özniteliğe sahip olarak belirtilen bir öğesi oluşturursanız, varsayılan değeri olan yeni bir varsayılan öznitelik, XML Belge Nesne Modeli (DOM) tarafından oluşturulur ve öğesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="a7471-124">If you create an element that is declared to have a default attribute, then a new default attribute with its default value is created by the XML Document Object Model (DOM) and attached to the element.</span></span> <span data-ttu-id="a7471-125">Varsayılan özniteliğin alt düğümleri de şu anda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a7471-125">The child nodes of the default attribute are also created at this time.</span></span>

## <a name="attribute-child-nodes"></a><span data-ttu-id="a7471-126">Öznitelik alt düğümleri</span><span class="sxs-lookup"><span data-stu-id="a7471-126">Attribute child nodes</span></span>

<span data-ttu-id="a7471-127">Öznitelik düğümünün değeri, alt düğümleri haline gelir.</span><span class="sxs-lookup"><span data-stu-id="a7471-127">The value of an attribute node becomes its child nodes.</span></span> <span data-ttu-id="a7471-128">Yalnızca iki tür geçerli alt düğüm vardır: **XmlText** düğümleri ve **XmlEntityReference** düğümleri.</span><span class="sxs-lookup"><span data-stu-id="a7471-128">There are only two types of valid child nodes: **XmlText** nodes and **XmlEntityReference** nodes.</span></span> <span data-ttu-id="a7471-129">Bunlar, **FirstChild** ve **LastChild** gibi yöntemlerin alt düğümler olarak işlenmesi açısından önemli olan alt düğümlerdir.</span><span class="sxs-lookup"><span data-stu-id="a7471-129">These are child nodes in the sense that methods such as **FirstChild** and **LastChild** process them as child nodes.</span></span> <span data-ttu-id="a7471-130">Alt düğümlere sahip bir özniteliğin bu ayrım özelliği, öznitelikleri veya öznitelik alt düğümlerini kaldırmaya çalışırken önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a7471-130">This distinction of an attribute having child nodes is important when trying to remove attributes or attribute child nodes.</span></span> <span data-ttu-id="a7471-131">Daha fazla bilgi için bkz. [Dom 'daki bir öğe düğümünden öznitelikleri kaldırma](removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="a7471-131">For more information, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7471-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7471-132">See also</span></span>

- [<span data-ttu-id="a7471-133">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="a7471-133">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
