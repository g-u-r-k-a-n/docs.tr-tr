---
title: LINQ to XML vs DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: f6a89bba1ff2753f04406a060beb37bf2bf6552c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344792"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="24dc5-102">LINQ to XML vs DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="24dc5-102">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="24dc5-103">Bu bölümde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve geçerli önceden baskın XML programlama API 'SI, W3C Belge Nesne Modeli (DOM) arasındaki bazı önemli farklılıklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="24dc5-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="24dc5-104">XML ağaçları oluşturmak için yeni yollar</span><span class="sxs-lookup"><span data-stu-id="24dc5-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="24dc5-105">W3C DOM 'da, aşağıdan yukarıya bir XML ağacı oluşturursunuz; diğer bir deyişle, bir belge oluşturur, öğeler oluşturur ve sonra öğeleri belgeye eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="24dc5-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="24dc5-106">Örneğin, aşağıdaki, DOM 'ın Microsoft uygulamasını kullanarak bir XML ağacı oluşturmanın tipik bir yoludur <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="24dc5-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
XmlElement phone1 = doc.CreateElement("Phone");  
phone1.SetAttribute("Type", "Home");  
phone1.InnerText = "206-555-0144";          
XmlElement phone2 = doc.CreateElement("Phone");  
phone2.SetAttribute("Type", "Work");  
phone2.InnerText = "425-555-0145";          
XmlElement street1 = doc.CreateElement("Street1");          
street1.InnerText = "123 Main St";  
XmlElement city = doc.CreateElement("City");  
city.InnerText = "Mercer Island";  
XmlElement state = doc.CreateElement("State");  
state.InnerText = "WA";  
XmlElement postal = doc.CreateElement("Postal");  
postal.InnerText = "68042";  
XmlElement address = doc.CreateElement("Address");  
address.AppendChild(street1);  
address.AppendChild(city);  
address.AppendChild(state);  
address.AppendChild(postal);  
XmlElement contact = doc.CreateElement("Contact");  
contact.AppendChild(name);  
contact.AppendChild(phone1);  
contact.AppendChild(phone2);  
contact.AppendChild(address);  
XmlElement contacts = doc.CreateElement("Contacts");  
contacts.AppendChild(contact);  
doc.AppendChild(contacts);  
```  
  
 <span data-ttu-id="24dc5-107">Bu kodlama stili, XML ağacının yapısı hakkında görsel olarak çok fazla bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="24dc5-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="24dc5-108">, bir XML ağacı oluşturmak için bu yaklaşımı destekler, ancak alternatif bir yaklaşım, *işlevsel oluşturma*da destekler.</span><span class="sxs-lookup"><span data-stu-id="24dc5-108">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="24dc5-109">İşlevsel oluşturma, bir XML ağacı oluşturmak için <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> oluşturucularını kullanır.</span><span class="sxs-lookup"><span data-stu-id="24dc5-109">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="24dc5-110">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel oluşturma kullanarak aynı XML ağacını nasıl oluşturabileceğiniz aşağıda açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="24dc5-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144",   
                new XAttribute("Type", "Home")),  
            new XElement("phone", "425-555-0145",  
                new XAttribute("Type", "Work")),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="24dc5-111">XML ağacını oluşturmak için kodun girintilendiği, temel alınan XML 'nin yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="24dc5-112">Daha fazla bilgi için bkz. [xml ağaçları oluşturmaC#()](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="24dc5-112">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="24dc5-113">Doğrudan XML öğeleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="24dc5-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="24dc5-114">XML ile programlama yaptığınızda, birincil odağınızı genellikle XML öğelerinde ve belki de özniteliklerde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24dc5-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="24dc5-115">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], doğrudan XML öğeleri ve özniteliklerle çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24dc5-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="24dc5-116">Örneğin şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="24dc5-116">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="24dc5-117">Bir belge nesnesi kullanmadan XML öğeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24dc5-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="24dc5-118">Bu, XML ağaçlarının parçaları ile çalışmanız gerektiğinde programlamayı basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="24dc5-119">Nesneleri doğrudan bir XML dosyasından yükleme `T:System.Xml.Linq.XElement`.</span><span class="sxs-lookup"><span data-stu-id="24dc5-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="24dc5-120">`T:System.Xml.Linq.XElement` nesnelerini bir dosyaya veya akışa serileştirme.</span><span class="sxs-lookup"><span data-stu-id="24dc5-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="24dc5-121">Bu, XML belgesinin XML ağacı için bir mantıksal kapsayıcı olarak kullanıldığı W3C DOM ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="24dc5-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="24dc5-122">DOM 'da, öğeler ve öznitelikler dahil XML düğümlerinin bir XML belgesi bağlamında oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="24dc5-123">DOM 'da bir ad öğesi oluşturmak için kodun bir parçası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="24dc5-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="24dc5-124">Birden çok belge genelinde bir öğe kullanmak istiyorsanız düğümleri belgeler arasında içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="24dc5-125">bu karmaşıklık katmanını önler.</span><span class="sxs-lookup"><span data-stu-id="24dc5-125">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="24dc5-126">LINQ to XML kullanırken, yalnızca belgenin kök düzeyinde bir yorum veya işleme yönergesi eklemek istiyorsanız <xref:System.Xml.Linq.XDocument> sınıfını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="24dc5-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="24dc5-127">Adları ve ad alanlarını Basitleştirilmiş olarak Işleme</span><span class="sxs-lookup"><span data-stu-id="24dc5-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="24dc5-128">Adları, ad alanlarını ve ad alanı öneklerini işleme genellikle XML programlamanın karmaşık bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="24dc5-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="24dc5-129">, ad alanı önekleriyle uğraşmak için gereksinimi ortadan kaldırarak adları ve ad alanlarını basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-129">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="24dc5-130">Ad alanı öneklerini denetlemek istiyorsanız, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24dc5-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="24dc5-131">Ancak ad alanı öneklerini açıkça denetistemediğinize karar verirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], gerektiğinde serileştirme sırasında ad alanı öneklerini atayacaktır veya varsayılan ad alanlarını kullanarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="24dc5-132">Varsayılan ad alanları kullanılırsa, sonuçta elde edilen belgede ad alanı önekleri olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="24dc5-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="24dc5-133">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="24dc5-133">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="24dc5-134">DOM ile ilgili başka bir sorun da bir düğümün adını değiştirmenize izin vermez.</span><span class="sxs-lookup"><span data-stu-id="24dc5-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="24dc5-135">Bunun yerine, yeni bir düğüm oluşturmanız ve tüm alt düğümleri buna kopyalamanız ve özgün düğüm kimliğini kaybetmemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="24dc5-136">, bir düğümdeki <xref:System.Xml.Linq.XName> özelliğini ayarlamanıza olanak tanıyarak bu sorunu önler.</span><span class="sxs-lookup"><span data-stu-id="24dc5-136">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="24dc5-137">XML yükleme için statik yöntem desteği</span><span class="sxs-lookup"><span data-stu-id="24dc5-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="24dc5-138">, örnek yöntemleri yerine statik yöntemler kullanarak XML yüklemenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="24dc5-138">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="24dc5-139">Bu, yükleme ve ayrıştırma işlemlerini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="24dc5-140">Daha fazla bilgi için bkz. [XML 'i dosyadan yükleme (C#)](./how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="24dc5-140">For more information, see [How to load XML from a file (C#)](./how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="24dc5-141">DTD yapıları için desteği kaldırma</span><span class="sxs-lookup"><span data-stu-id="24dc5-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="24dc5-142">varlıklar ve varlık başvuruları desteğini kaldırarak XML programlamayı basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-142">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="24dc5-143">Varlıkların yönetimi karmaşıktır ve nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24dc5-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="24dc5-144">Desteğinin kaldırılması performansı artırır ve programlama arabirimini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="24dc5-145">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ağaç doldurulduktan sonra tüm DTD varlıkları genişletilir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="24dc5-146">Parçalar için destek</span><span class="sxs-lookup"><span data-stu-id="24dc5-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="24dc5-147">, `XmlDocumentFragment` sınıfı için bir eşdeğer sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="24dc5-147">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="24dc5-148">Ancak çoğu durumda `XmlDocumentFragment` kavramı, <xref:System.Xml.Linq.XNode><xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Xml.Linq.XElement><xref:System.Collections.Generic.IEnumerable%601> olarak yazılmış bir sorgunun sonucu tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="24dc5-149">XPathNavigator desteği</span><span class="sxs-lookup"><span data-stu-id="24dc5-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="24dc5-150">, <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanındaki genişletme yöntemleri aracılığıyla <xref:System.Xml.XPath.XPathNavigator> için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="24dc5-150">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="24dc5-151">Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="24dc5-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="24dc5-152">Boşluk ve girintileme desteği</span><span class="sxs-lookup"><span data-stu-id="24dc5-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="24dc5-153">, DOM 'dan daha fazla boşluk işler.</span><span class="sxs-lookup"><span data-stu-id="24dc5-153">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="24dc5-154">Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bir bellek içi XML ağacı oluşturmaktır (diğer bir deyişle, beyaz alanı korumadan), XML üzerinde bazı işlemleri gerçekleştirir ve ardından XML 'i girintilemeli olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="24dc5-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="24dc5-155">XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur.</span><span class="sxs-lookup"><span data-stu-id="24dc5-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="24dc5-156">Bu, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="24dc5-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="24dc5-157">Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="24dc5-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="24dc5-158">Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24dc5-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="24dc5-159">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML 'i yüklediğinizde veya ayrıştırdığınızda veya XML 'yi seri hale alırken biçimlendirmeyi devre dışı bıraktığınızda boşluğu koruyarak bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24dc5-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="24dc5-160">, DOM gibi özelleştirilmiş bir <xref:System.Xml.XmlNodeType.Whitespace> düğüm türüne sahip olmak yerine, alanı <xref:System.Xml.Linq.XText> bir düğüm olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="24dc5-160">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="24dc5-161">Ek açıklamalar için destek</span><span class="sxs-lookup"><span data-stu-id="24dc5-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="24dc5-162">öğeleri, genişletilebilir bir ek açıklama kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="24dc5-162">elements support an extensible set of annotations.</span></span> <span data-ttu-id="24dc5-163">Bu, şema bilgileri, öğenin bir kullanıcı arabirimine bağlanıp bağlanmayacağı veya başka bir uygulamaya özgü bilgi türü gibi bir öğeyle ilgili çeşitli bilgileri izlemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="24dc5-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="24dc5-164">Daha fazla bilgi için bkz. [LINQ to XML ek açıklamaları](./linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="24dc5-164">For more information, see [LINQ to XML Annotations](./linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="24dc5-165">Şema bilgileri için destek</span><span class="sxs-lookup"><span data-stu-id="24dc5-165">Support for Schema Information</span></span>  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="24dc5-166">, <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanındaki genişletme yöntemleri aracılığıyla XSD doğrulaması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="24dc5-166">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="24dc5-167">Bir XML ağacının bir XSD ile uyumlu olduğunu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24dc5-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="24dc5-168">XML ağacını şema-doğrulama sonrası bilgi kümesi (PSVı) ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24dc5-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="24dc5-169">Daha fazla bilgi için bkz. XSD ve <xref:System.Xml.Schema.Extensions>[kullanarak doğrulama](./how-to-validate-using-xsd-linq-to-xml.md) .</span><span class="sxs-lookup"><span data-stu-id="24dc5-169">For more information, see [How to validate using XSD](./how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="24dc5-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24dc5-170">See also</span></span>

- [<span data-ttu-id="24dc5-171">Başlarken (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="24dc5-171">Getting Started (LINQ to XML)</span></span>](./linq-to-xml-overview.md)
