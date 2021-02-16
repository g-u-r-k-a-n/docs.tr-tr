---
description: 'Daha fazla bilgi edinin: nasıl yapılır: LINQ kullanarak XML dönüştürme (Visual Basic)'
title: "Nasıl yapılır: XML'i LINQ Kullanarak Dönüştürme"
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 67e6f5f94cd71d960f742b660d3f223137bbd6d4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483644"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="71fbc-103">Nasıl yapılır: XML'i LINQ Kullanarak Dönüştürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71fbc-103">How to: Transform XML by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="71fbc-104">[XML değişmez değerleri](../../../language-reference/xml-literals/index.md) , BIR kaynaktan XML okumayı ve bunu yenı bir XML biçimine dönüştürmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="71fbc-104">[XML Literals](../../../language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="71fbc-105">Dönüştürülecek içeriği almak veya varolan bir belgedeki içeriği yeni bir XML biçimiyle değiştirmek için LINQ sorgularından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71fbc-105">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>

<span data-ttu-id="71fbc-106">Bu konudaki örnek, bir XML kaynak belgesinden içeriği bir tarayıcıda görüntülenmek üzere HTML 'ye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="71fbc-106">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-transform-an-xml-document"></a><span data-ttu-id="71fbc-107">Bir XML belgesini dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="71fbc-107">To transform an XML document</span></span>

1. <span data-ttu-id="71fbc-108">Visual Studio 'da, **konsol uygulaması** proje şablonunda yeni bir Visual Basic projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="71fbc-108">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>

2. <span data-ttu-id="71fbc-109">Visual Basic kodunu değiştirmek için projede oluşturulan Module1. vb dosyasını çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="71fbc-109">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="71fbc-110">Aşağıdaki kodu modülün öğesine ekleyin `Sub Main` `Module1` .</span><span class="sxs-lookup"><span data-stu-id="71fbc-110">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="71fbc-111">Bu kod, kaynak XML belgesini bir nesne olarak oluşturur <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="71fbc-111">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>

    ```vb
    Dim catalog =
      <?xml version="1.0"?>
        <Catalog>
          <Book id="bk101">
            <Author>Garghentini, Davide</Author>
            <Title>XML Developer's Guide</Title>
            <Price>44.95</Price>
            <Description>
              An in-depth look at creating applications
              with <technology>XML</technology>. For
              <audience>beginners</audience> or
              <audience>advanced</audience> developers.
            </Description>
          </Book>
          <Book id="bk331">
            <Author>Spencer, Phil</Author>
            <Title>Developing Applications with Visual Basic .NET</Title>
            <Price>45.95</Price>
            <Description>
              Get the expert insights, practical code samples,
              and best practices you need
              to advance your expertise with <technology>Visual
              Basic .NET</technology>.
              Learn how to create faster, more reliable applications
              based on professional,
              pragmatic guidance by today's top <audience>developers</audience>.
            </Description>
          </Book>
        </Catalog>
    ```

     <span data-ttu-id="71fbc-112">[Nasıl yapılır: bir dosyadan, dizeden veya AKıŞTAN XML yükleme](how-to-load-xml-from-a-file-string-or-stream.md).</span><span class="sxs-lookup"><span data-stu-id="71fbc-112">[How to: Load XML from a File, String, or Stream](how-to-load-xml-from-a-file-string-or-stream.md).</span></span>

3. <span data-ttu-id="71fbc-113">Kaynak XML belgesi oluşturma kodundan sonra, \<Book> nesneden tüm öğeleri almak ve bunları BIR HTML belgesine dönüştürmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="71fbc-113">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="71fbc-114">Öğe listesi, \<Book> <xref:System.Xml.Linq.XElement> dönüştürülmüş html içeren nesnelerin bir koleksiyonunu döndüren bir LINQ sorgusu kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="71fbc-114">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="71fbc-115">Kaynak belgeden yeni XML biçiminde değerleri yerleştirmek için katıştırılmış ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71fbc-115">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>

     <span data-ttu-id="71fbc-116">Elde edilen HTML belgesi, yöntemi kullanılarak bir dosyaya yazılır <xref:System.Xml.Linq.XElement.Save%2A> .</span><span class="sxs-lookup"><span data-stu-id="71fbc-116">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>

    ```vb
    Dim htmlOutput =
      <html>
        <body>
          <%= From book In catalog.<Catalog>.<Book>
              Select <div>
                       <h1><%= book.<Title>.Value %></h1>
                       <h3><%= "By " & book.<Author>.Value %></h3>
                        <h3><%= "Price = " & book.<Price>.Value %></h3>
                        <h2>Description</h2>
                        <%= TransformDescription(book.<Description>(0)) %>
                        <hr/>
                      </div> %>
        </body>
      </html>

    htmlOutput.Save("BookDescription.html")
    ```

4. <span data-ttu-id="71fbc-117">Öğesinden `Sub Main` sonra `Module1` , bir `Sub` \<Description> düğümü belirtilen HTML biçimine dönüştürmek için yeni bir Yöntem () ekleyin.</span><span class="sxs-lookup"><span data-stu-id="71fbc-117">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="71fbc-118">Bu yöntem, önceki adımda kod tarafından çağrılır ve öğelerin biçimini korumak için kullanılır \<Description> .</span><span class="sxs-lookup"><span data-stu-id="71fbc-118">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>

     <span data-ttu-id="71fbc-119">Bu yöntem, öğesinin alt öğelerini \<Description> HTML ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="71fbc-119">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="71fbc-120">`ReplaceWith`Yöntemi, alt öğelerin konumunu korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71fbc-120">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="71fbc-121">Öğenin dönüştürülmüş içeriği \<Description> BIR HTML paragraf ( \<p> ) öğesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="71fbc-121">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="71fbc-122"><xref:System.Xml.Linq.XContainer.Nodes%2A>Özelliği, öğesinin dönüştürülmüş içeriğini almak için kullanılır \<Description> .</span><span class="sxs-lookup"><span data-stu-id="71fbc-122">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="71fbc-123">Bu, alt öğelerin dönüştürülmüş içeriğe dahil edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="71fbc-123">This ensures that sub-elements are included in the transformed content.</span></span>

     <span data-ttu-id="71fbc-124">Öğesinden sonra aşağıdaki kodu ekleyin `Sub Main` `Module1` .</span><span class="sxs-lookup"><span data-stu-id="71fbc-124">Add the following code after `Sub Main` of `Module1`.</span></span>

    ```vb
    Public Function TransformDescription(ByVal desc As XElement) As XElement

      ' Replace <technology> elements with <b>.
      Dim content = (From element In desc...<technology>).ToList()

      If content.Count > 0 Then
        For i = 0 To content.Count - 1
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)
        Next
      End If

      ' Replace <audience> elements with <i>.
      content = (From element In desc...<audience>).ToList()

      If content.Count > 0 Then
        For i = 0 To content.Count - 1
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)
        Next
      End If

      ' Return the updated contents of the <Description> element.
      Return <p><%= desc.Nodes %></p>
    End Function
    ```

5. <span data-ttu-id="71fbc-125">Yaptığınız değişiklikleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="71fbc-125">Save your changes.</span></span>

6. <span data-ttu-id="71fbc-126">Kodu çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="71fbc-126">Press F5 to run the code.</span></span> <span data-ttu-id="71fbc-127">Sonuç olarak kaydedilen belge aşağıdakine benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="71fbc-127">The resulting saved document will resemble the following:</span></span>

    ```html
    <?xml version="1.0"?>
    <html>
      <body>
        <div>
          <h1>XML Developer's Guide</h1>
          <h3>By Garghentini, Davide</h3>
          <h3>Price = 44.95</h3>
          <h2>Description</h2>
          <p>
            An in-depth look at creating applications
            with <b>XML</b>. For
            <i>beginners</i> or
            <i>advanced</i> developers.
          </p>
          <hr />
        </div>
        <div>
          <h1>Developing Applications with Visual Basic .NET</h1>
          <h3>By Spencer, Phil</h3>
          <h3>Price = 45.95</h3>
          <h2>Description</h2>
          <p>
            Get the expert insights, practical code
            samples, and best practices you need
            to advance your expertise with <b>Visual
            Basic .NET</b>. Learn how to create faster,
            more reliable applications based on
            professional, pragmatic guidance by today's
            top <i>developers</i>.
          </p>
          <hr />
        </div>
      </body>
    </html>
    ```

## <a name="see-also"></a><span data-ttu-id="71fbc-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71fbc-128">See also</span></span>

- [<span data-ttu-id="71fbc-129">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="71fbc-129">XML Literals</span></span>](../../../language-reference/xml-literals/index.md)
- [<span data-ttu-id="71fbc-130">Visual Basic'de XML'i Düzenleme</span><span class="sxs-lookup"><span data-stu-id="71fbc-130">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
- [<span data-ttu-id="71fbc-131">XML</span><span class="sxs-lookup"><span data-stu-id="71fbc-131">XML</span></span>](index.md)
- [<span data-ttu-id="71fbc-132">Nasıl yapılır: Dosya, Dize veya Akıştan XML Yükleme</span><span class="sxs-lookup"><span data-stu-id="71fbc-132">How to: Load XML from a File, String, or Stream</span></span>](how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="71fbc-133">LINQ</span><span class="sxs-lookup"><span data-stu-id="71fbc-133">LINQ</span></span>](../linq/index.md)
- [<span data-ttu-id="71fbc-134">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="71fbc-134">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
