---
title: XmlReader (C#) öğesinden XML parçalarını akışa alma
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: f7914d33622518f983a685dd2e844a25fd3ca15f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714648"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="231e2-102">XmlReader (C#) öğesinden XML parçalarını akışa alma</span><span class="sxs-lookup"><span data-stu-id="231e2-102">How to stream XML fragments from an XmlReader (C#)</span></span>

<span data-ttu-id="231e2-103">Büyük XML dosyalarını işlemek zorunda olduğunuzda, tüm XML ağacının belleğe yüklenmesi mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="231e2-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="231e2-104">Bu konuda, <xref:System.Xml.XmlReader>kullanarak parçaların nasıl akışının yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="231e2-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="231e2-105"><xref:System.Xml.Linq.XElement> nesneleri okumak için <xref:System.Xml.XmlReader> kullanmanın en etkili yöntemlerinden biri kendi özel eksen yönteminizi yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="231e2-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="231e2-106">Bir Axis yöntemi genellikle bu konudaki örnekte gösterildiği gibi, <xref:System.Xml.Linq.XElement><xref:System.Collections.Generic.IEnumerable%601> gibi bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="231e2-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="231e2-107">Özel eksen yönteminde, <xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemini çağırarak XML parçasını oluşturduktan sonra, `yield return`kullanarak koleksiyonu döndürün.</span><span class="sxs-lookup"><span data-stu-id="231e2-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="231e2-108">Bu, özel eksen yönteminiz için ertelenmiş yürütme semantiğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="231e2-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="231e2-109">Bir <xref:System.Xml.XmlReader> nesnesinden bir XML ağacı oluşturduğunuzda, <xref:System.Xml.XmlReader> bir öğe üzerinde konumlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="231e2-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="231e2-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> yöntemi, öğenin kapanış etiketini okuuncaya kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="231e2-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="231e2-111">Kısmi bir ağaç oluşturmak istiyorsanız, bir <xref:System.Xml.XmlReader>örneği oluşturabilir, okuyucuyu <xref:System.Xml.Linq.XElement> ağacına dönüştürmek istediğiniz düğüme konumlandırabilirsiniz ve sonra <xref:System.Xml.Linq.XElement> nesnesini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="231e2-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="231e2-112">Üst bilgi [bilgilerine erişimi olan XML parçalarının nasıl akışının yapılacağı konusu (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) , daha karmaşık bir belgenin nasıl akışla ilgili bilgi ve bir örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="231e2-112">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="231e2-113">[Büyük XML belgelerinin (C#) akış dönüşümünü gerçekleştirme](./how-to-perform-streaming-transform-of-large-xml-documents.md) konusu, küçük bir bellek parmak izi sağlarken çok büyük XML belgelerini dönüştürmek için LINQ to XML kullanma örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="231e2-113">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="231e2-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="231e2-114">Example</span></span>  
 <span data-ttu-id="231e2-115">Bu örnek bir özel eksen yöntemi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="231e2-115">This example creates a custom axis method.</span></span> <span data-ttu-id="231e2-116">Bir LINQ sorgusu kullanarak bunu sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="231e2-116">You can query it by using a LINQ query.</span></span> <span data-ttu-id="231e2-117">`StreamRootChildDoc`özel eksen yöntemi, bir yinelenen `Child` öğesi olan bir belgeyi okumak için özel olarak tasarlanan bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="231e2-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 <span data-ttu-id="231e2-118">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="231e2-118">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="231e2-119">Bu örnekte, kaynak belge çok küçüktür.</span><span class="sxs-lookup"><span data-stu-id="231e2-119">In this example, the source document is very small.</span></span> <span data-ttu-id="231e2-120">Ancak milyonlarca `Child` öğesi olsa bile, bu örnekte küçük bir bellek ayak izine sahip olmaya devam edersiniz.</span><span class="sxs-lookup"><span data-stu-id="231e2-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
