---
title: Üst bilgi bilgilerine erişimi olan XML parçalarını akışa alma (C#)
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 5bc10bcadae0e33ee63f953608ca841d44dd6527
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712396"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="08ddb-102">Üst bilgi bilgilerine erişimi olan XML parçalarını akışa alma (C#)</span><span class="sxs-lookup"><span data-stu-id="08ddb-102">How to stream XML fragments with access to header information (C#)</span></span>
<span data-ttu-id="08ddb-103">Bazen rastgele büyük XML dosyalarını okumanız ve uygulamanın bellek parmak izin tahmin edilebilir olması için uygulamanızı yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="08ddb-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="08ddb-104">Bir XML ağacını büyük bir XML dosyası ile doldurmayı denerseniz, bellek kullanımınız dosyanın boyutuyla orantılıdır; yani çok fazla.</span><span class="sxs-lookup"><span data-stu-id="08ddb-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="08ddb-105">Bu nedenle, bunun yerine bir akış tekniği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="08ddb-105">Therefore, you should use a streaming technique instead.</span></span>  
  
<span data-ttu-id="08ddb-106">Bir seçenek <xref:System.Xml.XmlReader>kullanarak uygulamanızı yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="08ddb-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="08ddb-107">Ancak, XML ağacını sorgulamak için LINQ kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08ddb-107">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="08ddb-108">Bu durumda, kendi özel eksen yönteminizi yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08ddb-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="08ddb-109">Daha fazla bilgi için bkz. [LINQ to XML eksen yöntemi yazmaC#()](./how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="08ddb-109">For more information, see [How to write a LINQ to XML axis method (C#)](./how-to-write-a-linq-to-xml-axis-method.md).</span></span>
  
 <span data-ttu-id="08ddb-110">Kendi eksen yönteminizi yazmak için, ilgilendiğiniz düğümlerin birine ulaşıncaya kadar düğümleri okumak için <xref:System.Xml.XmlReader> kullanan küçük bir yöntem yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="08ddb-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="08ddb-111">Daha sonra yöntemi, <xref:System.Xml.XmlReader> okuyan ve bir XML parçasını örnekleyen <xref:System.Xml.Linq.XNode.ReadFrom%2A>çağırır.</span><span class="sxs-lookup"><span data-stu-id="08ddb-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="08ddb-112">Daha sonra, her parçayı özel eksen yönteminizin numaralandırıldığı yönteme `yield return` olarak verir.</span><span class="sxs-lookup"><span data-stu-id="08ddb-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="08ddb-113">Daha sonra özel eksen yönteinizde LINQ sorguları yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08ddb-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="08ddb-114">Akış teknikleri en iyi şekilde, kaynak belgeyi yalnızca bir kez işleyebilmeniz ve öğeleri belge düzeninde işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08ddb-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="08ddb-115"><xref:System.Linq.Enumerable.OrderBy%2A>gibi bazı standart sorgu işleçleri, kaynaklarını yineleyebilir, tüm verileri toplar, sıralar ve son olarak dizideki ilk öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="08ddb-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="08ddb-116">İlk öğeyi bırakmadan önce kaynağını üreten bir sorgu işleci kullanırsanız, küçük bir bellek parmak izini saklayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="08ddb-116">If you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08ddb-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="08ddb-117">Example</span></span>  

<span data-ttu-id="08ddb-118">Bazen sorun biraz daha ilginç olur.</span><span class="sxs-lookup"><span data-stu-id="08ddb-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="08ddb-119">Aşağıdaki XML belgesinde, özel eksen yönteminizin tüketicisi, her öğenin ait olduğu müşterinin adını da bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="08ddb-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="08ddb-120">Bu örnekte geçen yaklaşım ayrıca, bu üstbilgi bilgilerini izlemek, üst bilgi bilgilerini kaydetmek ve ardından hem başlık bilgilerini hem de numaralandırdığınız ayrıntıyı içeren küçük bir XML ağacı oluşturmanızı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="08ddb-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="08ddb-121">Ardından Axis yöntemi bu yeni, küçük XML ağacını verir.</span><span class="sxs-lookup"><span data-stu-id="08ddb-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="08ddb-122">Sorgu daha sonra başlık bilgilerine ve ayrıntı bilgilerine erişimi de vardır.</span><span class="sxs-lookup"><span data-stu-id="08ddb-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="08ddb-123">Bu yaklaşımın küçük bir bellek ayak izi vardır.</span><span class="sxs-lookup"><span data-stu-id="08ddb-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="08ddb-124">Her ayrıntı XML parçası, bir önceki parçaya hiçbir başvuru tutulmazsa ve çöp toplama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08ddb-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="08ddb-125">Bu teknik yığın üzerinde birçok kısa süreli nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="08ddb-125">This technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="08ddb-126">Aşağıdaki örnek, URI tarafından belirtilen dosyadan XML parçalarını akıyan bir özel eksen yönteminin nasıl uygulanacağını ve kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="08ddb-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="08ddb-127">Bu özel eksen, `Customer`, `Name`ve `Item` öğelerine sahip bir belgeyi beklediğinden ve bu öğelerin yukarıdaki `Source.xml` belgesinde olarak düzenlenebilmesini sağlayacak şekilde yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="08ddb-127">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="08ddb-128">Bu bir uyarlaması uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="08ddb-128">It is a simplistic implementation.</span></span> <span data-ttu-id="08ddb-129">Daha sağlam bir uygulama, geçersiz bir belgeyi ayrıştırmaya hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08ddb-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 <span data-ttu-id="08ddb-130">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="08ddb-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  
