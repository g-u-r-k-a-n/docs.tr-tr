---
title: XPathNavigator Kullanarak XML Verilerini Kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
ms.openlocfilehash: 062a98a9cc10e6be00f165cf617de2d92d65acbf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710368"
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="0ba56-102">XPathNavigator Kullanarak XML Verilerini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="0ba56-102">Remove XML Data using XPathNavigator</span></span>
<span data-ttu-id="0ba56-103">Sınıfı <xref:System.Xml.XPath.XPathNavigator> , bir XML belgesinden düğümleri ve değerleri kaldırmak için kullanılan bir yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ba56-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="0ba56-104">Bu yöntemleri kullanabilmeniz için <xref:System.Xml.XPath.XPathNavigator> nesnesi düzenlenebilir olmalıdır, yani <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır. `true`</span><span class="sxs-lookup"><span data-stu-id="0ba56-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="0ba56-105"><xref:System.Xml.XPath.XPathNavigator>bir XML belgesini düzenleyebilen nesneler, <xref:System.Xml.XmlDocument.CreateNavigator%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemiyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0ba56-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="0ba56-106"><xref:System.Xml.XPath.XPathNavigator>sınıfı tarafından oluşturulan nesneler salt okunurdur ve bir <xref:System.Xml.XPath.XPathDocument> nesne tarafından oluşturulan <xref:System.NotSupportedException> <xref:System.Xml.XPath.XPathNavigator> nesnenin Editing yöntemlerini kullanma girişimleri bir ile sonuçlanır. <xref:System.Xml.XPath.XPathDocument></span><span class="sxs-lookup"><span data-stu-id="0ba56-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="0ba56-107">Düzenlenebilir <xref:System.Xml.XPath.XPathNavigator> nesneler oluşturma hakkında daha fazla bilgi için bkz. [XPathDocument ve XmlDocument kullanarak XML verilerini okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="0ba56-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="0ba56-108">Düğümler kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="0ba56-108">Removing Nodes</span></span>  
 <span data-ttu-id="0ba56-109"><xref:System.Xml.XPath.XPathNavigator> Sınıfı, bir XML <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> belgesinden düğümleri kaldırmak için yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ba56-109">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="0ba56-110">Düğüm kaldırma</span><span class="sxs-lookup"><span data-stu-id="0ba56-110">Removing a Node</span></span>  
 <span data-ttu-id="0ba56-111">Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> nesne <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> Şu anda bir XML belgesinden konumlandırılmış olan geçerli düğümü silmeye yönelik yöntemi sağlar. <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="0ba56-111">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="0ba56-112">Bir düğüm <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi kullanılarak silindikten sonra, artık <xref:System.Xml.XmlDocument> nesnenin kökünden ulaşılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ba56-112">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="0ba56-113">Düğüm silindikten <xref:System.Xml.XPath.XPathNavigator> sonra, silinen düğümün üst düğümüne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0ba56-113">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="0ba56-114">Silme işlemi, silinen düğümde konumlandırılmış herhangi bir <xref:System.Xml.XPath.XPathNavigator> nesnenin konumunu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="0ba56-114">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="0ba56-115">Bu <xref:System.Xml.XPath.XPathNavigator> nesneler, Silinen alt ağaçta taşıyabilecekleri, ancak <xref:System.Xml.XPath.XPathNavigator> sınıfın normal düğüm kümesi gezinti yöntemleri kullanılarak ana düğüm ağacına taşınamayacak anlamda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0ba56-115">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ba56-116"><xref:System.Xml.XPath.XPathNavigator> Sınıfının <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> yöntemi, bu <xref:System.Xml.XPath.XPathNavigator> nesneleri ana düğüm ağacına veya ana düğüm ağacından Silinen alt ağaca geri taşımak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ba56-116">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="0ba56-117">Aşağıdaki `price` örnekte, `book` `contosoBooks.xml` dosyanın ilk öğesinin öğesi <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi kullanılarak silinir.</span><span class="sxs-lookup"><span data-stu-id="0ba56-117">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="0ba56-118">Öğe silindikten sonra <xref:System.Xml.XPath.XPathNavigator> nesnenin konumu üst `book` öğedir. `price`</span><span class="sxs-lookup"><span data-stu-id="0ba56-118">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="0ba56-119">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="0ba56-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="0ba56-120">Öznitelik düğümünü kaldırma</span><span class="sxs-lookup"><span data-stu-id="0ba56-120">Removing an Attribute Node</span></span>  
 <span data-ttu-id="0ba56-121">Öznitelik düğümleri bir XML belgesinden <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi kullanılarak kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="0ba56-121">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="0ba56-122">Bir öznitelik düğümü silindikten sonra, artık <xref:System.Xml.XmlDocument> nesnenin kök düğümünden ulaşılamaz ve <xref:System.Xml.XPath.XPathNavigator> nesne üst öğe üzerinde konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0ba56-122">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="0ba56-123">Varsayılan öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0ba56-123">Default Attributes</span></span>  
 <span data-ttu-id="0ba56-124">Öznitelikleri kaldırmak için kullanılan yöntemden bağımsız olarak, XML belgesi için DTD veya XML şemasında varsayılan öznitelikler olarak tanımlanan öznitelikleri kaldırmaya ilişkin özel sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="0ba56-124">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="0ba56-125">Ait oldukları öğe da kaldırılmadığı takdirde varsayılan öznitelikler kaldırılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ba56-125">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="0ba56-126">Varsayılan öznitelikler, varsayılan öznitelikleri olan öğeler için her zaman mevcuttur ve sonuç olarak, varsayılan bir özniteliğin silinmesi, öğesine eklenen ve varsayılan değere başlatılan bir değiştirme özniteliğiyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="0ba56-126">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="0ba56-127">Değerler kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="0ba56-127">Removing Values</span></span>  
 <span data-ttu-id="0ba56-128"><xref:System.Xml.XPath.XPathNavigator> Sınıfı, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> bir XML belgesinden <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> türsüz ve yazılan değerleri kaldırmak için ve yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ba56-128">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="0ba56-129">Türsüz değerler kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="0ba56-129">Removing Untyped Values</span></span>  
 <span data-ttu-id="0ba56-130"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi, bir parametre olarak geçirilen `string` türsüz değeri <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olan düğümün değeri olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="0ba56-130">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="0ba56-131"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemine boş bir dize geçirilme, geçerli düğümün değerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0ba56-131">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="0ba56-132">Aşağıdaki `price` örnek, `book` `contosoBooks.xml` <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi kullanılarak dosyasındaki ilk öğenin öğesinin değerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0ba56-132">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="0ba56-133">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="0ba56-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="0ba56-134">Yazılan değerler kaldırılıyor</span><span class="sxs-lookup"><span data-stu-id="0ba56-134">Removing Typed Values</span></span>  
 <span data-ttu-id="0ba56-135">Bir düğümün türü bir W3C XML şeması basit türü olduğunda, <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi tarafından yerleştirilen yeni değer, değer ayarlanmadan önce basit türdeki modellerle denetlenir.</span><span class="sxs-lookup"><span data-stu-id="0ba56-135">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="0ba56-136">Yeni değer, düğüm türüne göre geçerli değilse (örneğin, türü olan bir öğe `-1` üzerinde değerini ayarlamak `xs:positiveInteger`), bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="0ba56-136">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="0ba56-137"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Yöntemi parametre olarak da geçirilemez `null` .</span><span class="sxs-lookup"><span data-stu-id="0ba56-137">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="0ba56-138">Sonuç olarak, yazılan bir düğümün değerinin kaldırılması, düğümün şema türüyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ba56-138">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="0ba56-139">Aşağıdaki örnek, değerini değerine ayarlayarak `price` , `book` `contosoBooks.xml` <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> dosyasındaki ilk öğenin öğesinin değerini kaldırır. `0`</span><span class="sxs-lookup"><span data-stu-id="0ba56-139">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="0ba56-140">Düğümün değeri kaldırılmaz, ancak kitabýn fiyatı, veri türüne göre kaldırılmıştır `xs:decimal`.</span><span class="sxs-lookup"><span data-stu-id="0ba56-140">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a><span data-ttu-id="0ba56-141">Ad alanı düğümleri</span><span class="sxs-lookup"><span data-stu-id="0ba56-141">Namespace Nodes</span></span>  
 <span data-ttu-id="0ba56-142">Ad alanı düğümleri bir <xref:System.Xml.XmlDocument> nesneden silinemez.</span><span class="sxs-lookup"><span data-stu-id="0ba56-142">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="0ba56-143"><xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> Yöntemi kullanarak ad alanı düğümlerini silme girişimleri bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="0ba56-143">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="0ba56-144">InnerXml ve OuterXml özellikleri</span><span class="sxs-lookup"><span data-stu-id="0ba56-144">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="0ba56-145">Sınıfının ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> bir <xref:System.Xml.XPath.XPathNavigator> NESNENIN Şu anda konumlandırılmış olduğu düğümlerin XML işaretlemesini değiştirir. <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="0ba56-145">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="0ba56-146"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliği, belirtilen XML `string`'nin ayrıştırılmış içeriğiyle bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılmış olan alt düğümlerin XML işaretlemesini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0ba56-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="0ba56-147">Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliği de bir <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda bulunduğu alt düğümlerin XML işaretlemesini ve geçerli düğümün kendisini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0ba56-147">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="0ba56-148">Bu konuda açıklanan yöntemlere ek olarak, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri bir XML belgesinden düğümleri ve değerleri kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ba56-148">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="0ba56-149">Düğümleri değiştirmek için <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini kullanma hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak XML verilerini değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="0ba56-149">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="0ba56-150">XML belgesi kaydetme</span><span class="sxs-lookup"><span data-stu-id="0ba56-150">Saving an XML Document</span></span>  
 <span data-ttu-id="0ba56-151">Bu konuda açıklanan yöntemlerin sonucu <xref:System.Xml.XmlDocument> olarak bir nesne üzerinde yapılan değişikliklerin kaydedilmesi, <xref:System.Xml.XmlDocument> sınıfının yöntemleri kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0ba56-151">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="0ba56-152">Bir <xref:System.Xml.XmlDocument> nesne üzerinde yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bkz. [belgeyi kaydetme ve yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="0ba56-152">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ba56-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ba56-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="0ba56-154">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="0ba56-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="0ba56-155">XPathNavigator Kullanarak XML Verileri Ekleme</span><span class="sxs-lookup"><span data-stu-id="0ba56-155">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="0ba56-156">XPathNavigator Kullanarak XML Verilerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="0ba56-156">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
