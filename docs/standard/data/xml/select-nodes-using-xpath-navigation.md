---
title: XPath Gezintisi Kullanarak Düğüm Seçme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
ms.openlocfilehash: 85f3ae9ec9f3b4d0949a893dd1e59fbbda139066
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291467"
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="38026-102">XPath Gezintisi Kullanarak Düğüm Seçme</span><span class="sxs-lookup"><span data-stu-id="38026-102">Select Nodes Using XPath Navigation</span></span>
<span data-ttu-id="38026-103">XML Belge Nesne Modeli (DOM), DOM 'daki sorgu bilgilerini kullanarak XML yol dili (XPath) gezintisini kullanmanıza imkan tanıyan yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="38026-103">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="38026-104">XPath 'i tek, belirli bir düğüm bulmak veya bazı ölçütlerle eşleşen tüm düğümleri bulmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38026-104">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="38026-105">XPath seçme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="38026-105">XPath Select Methods</span></span>  
 <span data-ttu-id="38026-106">DOM sınıfları XPath seçimi için iki yöntem sağlar: <xref:System.Xml.XmlNode.SelectSingleNode%2A> yöntemi ve <xref:System.Xml.XmlNode.SelectNodes%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="38026-106">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="38026-107"><xref:System.Xml.XmlNode.SelectSingleNode%2A>Yöntemi, seçim ölçütleriyle eşleşen ilk düğümü döndürür.</span><span class="sxs-lookup"><span data-stu-id="38026-107">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="38026-108"><xref:System.Xml.XmlNode.SelectNodes%2A>Yöntemi, <xref:System.Xml.XmlNodeList> eşleşen düğümleri içeren bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="38026-108">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="38026-109">Aşağıdaki örnek, <xref:System.Xml.XmlNode.SelectSingleNode%2A> `book` yazarın en son adının belirtilen ölçütlere uyan ilk düğümü seçmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="38026-109">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="38026-110">Bu konunun sonunda belirtilen kitaplığı. xml dosyası, giriş dosyası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38026-110">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 <span data-ttu-id="38026-111">Sonraki örnekte, <xref:System.Xml.XmlNode.SelectNodes%2A> fiyatın belirtilen miktardan daha büyük olduğu tüm kitap düğümlerini seçmek için yöntemi kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="38026-111">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="38026-112">Seçili listedeki her bir kitabın fiyatı, daha sonra program aracılığıyla yüzde on oranında azaltılır.</span><span class="sxs-lookup"><span data-stu-id="38026-112">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="38026-113">Son olarak, güncelleştirilmiş dosya konsola yazılır.</span><span class="sxs-lookup"><span data-stu-id="38026-113">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="38026-114">Bu konunun sonunda belirtilen kitaplığı. xml dosyası, giriş dosyası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38026-114">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 <span data-ttu-id="38026-115">Yukarıdaki örneklerde, belge öğesinde XPath sorgusu başlatılır.</span><span class="sxs-lookup"><span data-stu-id="38026-115">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="38026-116">XPath sorgusu için başlangıç noktası ayarlandığında, XPath sorgusunun başlangıç noktası olan bağlam düğümü ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="38026-116">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="38026-117">Belge öğesinde başlamak istemiyorsanız, ancak belge öğesinin ilk alt öğesinden başlamak istiyorsanız, SELECT ifadesini aşağıdaki gibi kodlayın:</span><span class="sxs-lookup"><span data-stu-id="38026-117">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="38026-118">Tüm <xref:System.Xml.XmlNodeList> nesneler, temel alınan belgeyle eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="38026-118">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="38026-119">Bu nedenle, düğüm listesini yineleyebilir ve bir düğümün değerini değiştirirseniz bu düğüm, geldiği belgede de güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="38026-119">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="38026-120">Önceki örnekte, bir düğüm seçili olarak değiştirildiğinde <xref:System.Xml.XmlNodeList> , temel alınan belgede de değişiklik yapıldığında dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="38026-120">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38026-121">Temel alınan belge değiştirildiğinde, seçimi yeniden çalıştırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="38026-121">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="38026-122">Değiştirilen düğüm, düğüm listesine daha önce olmadığında veya düğüm listesinden kaldırılmasına neden olacak şekilde, düğüm listesinin artık doğru olduğundan emin olmak için bir değer olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="38026-122">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="38026-123">XPath Ifadelerinde ad alanları</span><span class="sxs-lookup"><span data-stu-id="38026-123">Namespaces in XPath Expressions</span></span>  
 <span data-ttu-id="38026-124">XPath ifadeleri ad alanı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="38026-124">XPath expressions can include namespaces.</span></span> <span data-ttu-id="38026-125">Ad alanı çözümlemesi, kullanılarak desteklenir <xref:System.Xml.XmlNamespaceManager> .</span><span class="sxs-lookup"><span data-stu-id="38026-125">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="38026-126">XPath ifadesi bir ön ek içeriyorsa, önek ve ad alanı URI çiftinin öğesine eklenmelidir <xref:System.Xml.XmlNamespaceManager> ve, <xref:System.Xml.XmlNamespaceManager> <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> veya <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="38026-126">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="38026-127">Yukarıdaki kod örneklerinin, <xref:System.Xml.XmlNamespaceManager> Kitaplığı. xml belgesinin ad alanını çözümlemek için öğesini kullandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="38026-127">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38026-128">XPath ifadesi bir ön ek içermiyorsa, ad alanı Tekdüzen Kaynak tanımlayıcısı 'nın (URI) boş ad alanı olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="38026-128">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="38026-129">XML 'niz bir varsayılan ad alanı içeriyorsa, ' a bir ön ek ve ad alanı URI 'SI eklemeniz gerekir <xref:System.Xml.XmlNamespaceManager> ; Aksi takdirde hiçbir düğüm seçilmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="38026-129">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="38026-130">Giriş Dosyası</span><span class="sxs-lookup"><span data-stu-id="38026-130">Input File</span></span>  
 <span data-ttu-id="38026-131">Aşağıda, bu konudaki örneklerde bulunan giriş dosyası olarak kullanılan kitaplığı. xml dosyası verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="38026-131">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38026-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38026-132">See also</span></span>

- [<span data-ttu-id="38026-133">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="38026-133">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
