---
title: Ad Alanı Ön Ek Özelliklerini Değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
ms.openlocfilehash: e6b811d58ef9d98c51e9a45a46a1965c4fa12b55
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711122"
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="1ed79-102">Ad Alanı Ön Ek Özelliklerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="1ed79-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="1ed79-103">**XMLNode** sınıfı, belirli bir düğümle ilişkili ad alanı önekini değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="1ed79-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="1ed79-104">Örneğin, aşağıdaki kod değiştirilmekte olan bir öğenin önekini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ed79-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="1ed79-105">**Output**</span><span class="sxs-lookup"><span data-stu-id="1ed79-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="1ed79-106">Bir düğümün önekini değiştirmek, ad alanını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="1ed79-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="1ed79-107">Ad alanı yalnızca düğüm oluşturulduğunda ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="1ed79-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="1ed79-108">Ağacı kalıcı hale getirdikten sonra, ayarladığınız ön eki karşılamak için yeni ad alanı öznitelikleri kalıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="1ed79-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="1ed79-109">Yeni ad alanı oluşturuoluşturulamadığı takdirde, düğüm yerel adını ve ad alanını koruyabilmesi için önek değişir.</span><span class="sxs-lookup"><span data-stu-id="1ed79-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="1ed79-110">Aşağıdaki örnekte, eklenmekte olan bir ad alanı özniteliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ed79-110">The following example shows a namespace attribute being added.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="1ed79-111">**Output**</span><span class="sxs-lookup"><span data-stu-id="1ed79-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="1ed79-112">Ağaç, belge çağrısının bir sonucu olarak bir dizeye kalıcı yapıldığında **. InnerXml**, `test` öğesinin ad alanını korumak için `xmlns:a='123'` özniteliği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1ed79-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="1ed79-113">`'123'`ve `'123'`kaldı.</span><span class="sxs-lookup"><span data-stu-id="1ed79-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed79-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ed79-114">See also</span></span>

- [<span data-ttu-id="1ed79-115">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="1ed79-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
