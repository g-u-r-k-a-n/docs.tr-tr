---
title: XAttribute sınıfına genel bakışC#()
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 7a806314664c6319fc45cff0dddedbe38027059d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635671"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="cbfbe-102">XAttribute sınıfına genel bakışC#()</span><span class="sxs-lookup"><span data-stu-id="cbfbe-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="cbfbe-103">Öznitelikler, bir öğesiyle ilişkili ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="cbfbe-104"><xref:System.Xml.Linq.XAttribute> sınıfı XML özniteliklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="cbfbe-105">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="cbfbe-105">Overview</span></span>  
 <span data-ttu-id="cbfbe-106">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] özniteliklerle çalışma, öğelerle çalışmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="cbfbe-107">Oluşturucular benzerdir.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-107">Their constructors are similar.</span></span> <span data-ttu-id="cbfbe-108">Bunların koleksiyonlarını almak için kullandığınız yöntemler benzerdir.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="cbfbe-109">Öznitelik koleksiyonu için LINQ sorgu ifadesi bir öğe koleksiyonu için LINQ sorgu ifadesine çok benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-109">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="cbfbe-110">Öznitelikleri bir öğeye eklenme sırası korunur.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="cbfbe-111">Diğer bir deyişle, özniteliklerde yineleme yaparken, bunları eklendiği sırayla görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="cbfbe-112">XAttribute Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="cbfbe-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="cbfbe-113"><xref:System.Xml.Linq.XAttribute> sınıfının aşağıdaki Oluşturucusu, en sık kullandığınız bir sınıftır:</span><span class="sxs-lookup"><span data-stu-id="cbfbe-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="cbfbe-114">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="cbfbe-114">Constructor</span></span>|<span data-ttu-id="cbfbe-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbfbe-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="cbfbe-116">Oluşturur bir <xref:System.Xml.Linq.XAttribute> nesne.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="cbfbe-117">`name` bağımsız değişkeni özniteliğin adını belirtir; `content` özniteliğin içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="cbfbe-118">Özniteliği olan bir öğe oluşturma</span><span class="sxs-lookup"><span data-stu-id="cbfbe-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="cbfbe-119">Aşağıdaki kod, bir özniteliği içeren bir öğe oluşturma ortak görevini gösterir:</span><span class="sxs-lookup"><span data-stu-id="cbfbe-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="cbfbe-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cbfbe-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="cbfbe-121">Özniteliklerin işlevsel olarak oluşturulması</span><span class="sxs-lookup"><span data-stu-id="cbfbe-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="cbfbe-122"><xref:System.Xml.Linq.XElement> nesnelerinin yapımını aşağıdaki gibi <xref:System.Xml.Linq.XAttribute> nesneleri satır içinde oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cbfbe-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 <span data-ttu-id="cbfbe-123">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cbfbe-123">This example produces the following output:</span></span>  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="cbfbe-124">Öznitelikler düğüm değil</span><span class="sxs-lookup"><span data-stu-id="cbfbe-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="cbfbe-125">Öznitelikler ve öğeler arasında bazı farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="cbfbe-126"><xref:System.Xml.Linq.XAttribute> nesneler XML ağacındaki düğümler değildir.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="cbfbe-127">Bunlar bir XML öğesiyle ilişkili ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="cbfbe-128">Belge Nesne Modeli (DOM) aksine bu, XML yapısını daha yakından yansıtır.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="cbfbe-129"><xref:System.Xml.Linq.XAttribute> nesneler gerçekten XML ağacında düğümler olmasa da, <xref:System.Xml.Linq.XAttribute> nesneleriyle çalışma <xref:System.Xml.Linq.XElement> nesneleriyle çalışmaya çok benzer.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="cbfbe-130">Bu ayrım, birincil olarak yalnızca düğüm düzeyindeki XML ağaçları ile çalışan kod yazan geliştiriciler için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="cbfbe-131">Birçok geliştirici bu ayrım ile ilgilenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbfbe-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbfbe-132">See also</span></span>

- [<span data-ttu-id="cbfbe-133">LINQ to XML programlamaya genel bakışC#()</span><span class="sxs-lookup"><span data-stu-id="cbfbe-133">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
