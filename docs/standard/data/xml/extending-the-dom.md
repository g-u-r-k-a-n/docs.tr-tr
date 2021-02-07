---
description: "Daha fazla bilgi edinin: DOM 'ı genişletme"
title: DOM Genişletme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
ms.openlocfilehash: 46b721e093b2cf0247ddd7cf145381cdaec75773
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732156"
---
# <a name="extending-the-dom"></a><span data-ttu-id="c465e-103">DOM Genişletme</span><span class="sxs-lookup"><span data-stu-id="c465e-103">Extending the DOM</span></span>

<span data-ttu-id="c465e-104">Microsoft .NET Framework, XML Belge Nesne Modeli (DOM) uygulamasını sağlayan bir temel sınıf kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="c465e-104">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="c465e-105"><xref:System.Xml.XmlNode>Ve türetilmiş sınıfları, BIR XML belgesinin içeriğini ve yapısını gezinmenize, sorgulamanızı ve değiştirebilmeniz için yöntemler ve özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c465e-105">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>

<span data-ttu-id="c465e-106">XML içeriği DOM kullanılarak belleğe yüklendiğinde oluşturulan düğümler düğüm adı, düğüm türü vb. gibi bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="c465e-106">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="c465e-107">Temel sınıfların sağlamadığı belirli düğüm bilgilerinin gerekli olduğu durumlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="c465e-107">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="c465e-108">Örneğin, düğümün satır numarasını ve konumunu görmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c465e-108">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="c465e-109">Bu durumda, var olan DOM sınıflarından yeni sınıflar türetebilir ve ek işlevler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c465e-109">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>

<span data-ttu-id="c465e-110">Yeni sınıflar türetmede iki genel kılavuz vardır:</span><span class="sxs-lookup"><span data-stu-id="c465e-110">There are two general guidelines when deriving new classes:</span></span>

- <span data-ttu-id="c465e-111">Sınıfından hiçbir şekilde türetmeniz önerilir <xref:System.Xml.XmlNode> .</span><span class="sxs-lookup"><span data-stu-id="c465e-111">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="c465e-112">Bunun yerine, ilgilendiğiniz düğüm türüne karşılık gelen sınıftan sınıfları türetmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="c465e-112">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="c465e-113">Örneğin, öznitelik düğümleri hakkında ek bilgi döndürmek istiyorsanız sınıfından türetebilirsiniz <xref:System.Xml.XmlAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c465e-113">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>

- <span data-ttu-id="c465e-114">Düğüm oluşturma yöntemleri hariç, bir işlevi geçersiz kıldığınızda, işlevin temel sürümünü her zaman çağırmanız ve sonra ek işlem eklemeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="c465e-114">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>

## <a name="creating-your-own-node-instances"></a><span data-ttu-id="c465e-115">Kendi düğüm örneklerinizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c465e-115">Creating Your Own Node Instances</span></span>

<span data-ttu-id="c465e-116"><xref:System.Xml.XmlDocument>Sınıfı, düğüm oluşturma yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c465e-116">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="c465e-117">Bir XML dosyası yüklendiğinde, düğümleri oluşturmak için bu yöntemler çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c465e-117">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="c465e-118">Bir belge yüklendiğinde düğüm örneklerinizin oluşturulması için bu yöntemleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c465e-118">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="c465e-119">Örneğin, sınıfı genişlettiyseniz <xref:System.Xml.XmlElement> , sınıfını miras alıp <xref:System.Xml.XmlDocument> yöntemi geçersiz kılabilirsiniz <xref:System.Xml.XmlDocument.CreateElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="c465e-119">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>

<span data-ttu-id="c465e-120">Aşağıdaki örnek, <xref:System.Xml.XmlDocument.CreateElement%2A> sınıfının uygulamanızı döndürmek için yönteminin nasıl geçersiz kılınacağını göstermektedir <xref:System.Xml.XmlElement> .</span><span class="sxs-lookup"><span data-stu-id="c465e-120">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>

```vb
Class LineInfoDocument
    Inherits XmlDocument
        Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
        Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
        Return elem
    End Function 'CreateElement
End Class 'LineInfoDocument
```

```csharp
class LineInfoDocument : XmlDocument
{
    public override XmlElement CreateElement(string prefix, string localname, string nsURI)
    {
        LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);
        return elem;
    }
}
```

## <a name="extending-a-class"></a><span data-ttu-id="c465e-121">Sınıf genişletme</span><span class="sxs-lookup"><span data-stu-id="c465e-121">Extending a Class</span></span>

<span data-ttu-id="c465e-122">Bir sınıfı genişletmek için, varolan DOM sınıflarından birindeki sınıfınızı türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c465e-122">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="c465e-123">Daha sonra, temel sınıftaki sanal yöntemlerin veya özelliklerden birini geçersiz kılabilir ya da kendinizinkini ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c465e-123">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>

<span data-ttu-id="c465e-124">Aşağıdaki örnekte, sınıfını ve arabirimini uygulayan yeni bir sınıf oluşturulur <xref:System.Xml.XmlElement> <xref:System.Xml.IXmlLineInfo> .</span><span class="sxs-lookup"><span data-stu-id="c465e-124">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="c465e-125">Ek yöntemler ve özellikler, kullanıcıların hat bilgilerini toplamasına izin veren tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c465e-125">Additional methods and properties are defined which allows users to gather line information.</span></span>

```vb
Class LineInfoElement
   Inherits XmlElement
   Implements IXmlLineInfo
   Private lineNumber As Integer = 0
   Private linePosition As Integer = 0

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub

   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)
      lineNumber = linenum
      linePosition = linepos
   End Sub

   Public ReadOnly Property LineNumber() As Integer
      Get
         Return lineNumber
      End Get
   End Property

   Public ReadOnly Property LinePosition() As Integer
      Get
         Return linePosition
      End Get
   End Property

   Public Function HasLineInfo() As Boolean
      Return True
   End Function
End Class ' End LineInfoElement class.
```

```csharp
class LineInfoElement : XmlElement, IXmlLineInfo {
   int lineNumber = 0;
   int linePosition = 0;
   internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ) : base( prefix, localname, nsURI, doc ) {
       ( (LineInfoDocument)doc ).IncrementElementCount();
  }
  public void SetLineInfo( int linenum, int linepos ) {
      lineNumber = linenum;
      linePosition = linepos;
  }
  public int LineNumber {
     get {
       return lineNumber;
     }
  }
  public int LinePosition {
      get {
        return linePosition;
      }
  }
  public bool HasLineInfo() {
    return true;
  }
} // End LineInfoElement class.
```

### <a name="example"></a><span data-ttu-id="c465e-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="c465e-126">Example</span></span>

<span data-ttu-id="c465e-127">Aşağıdaki örnek bir XML belgesindeki öğelerin sayısını sayar:</span><span class="sxs-lookup"><span data-stu-id="c465e-127">The following example counts the number of elements in an XML document:</span></span>

```vb
Imports System.Xml
Imports System.IO

Class LineInfoDocument
   Inherits XmlDocument

   Private elementCount As Integer

   Friend Sub New()
      elementCount = 0
   End Sub

   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
      Return elem
   End Function

   Public Sub IncrementElementCount()
      elementCount += 1
   End Sub

   Public Function GetCount() As Integer
      Return elementCount
   End Function
End Class 'End LineInfoDocument class.

Class LineInfoElement
   Inherits XmlElement

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub 'New
End Class 'LineInfoElement
 _ 'End LineInfoElement class.

Public Class Test

   Private filename As [String] = "book.xml"

   Public Shared Sub Main()

      Dim doc As New LineInfoDocument()
      doc.Load(filename)
      Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount())
   End Sub
End Class
```

```csharp
using System;
using System.Xml;
using System.IO;

class LineInfoDocument : XmlDocument {

  int elementCount;
  internal LineInfoDocument():base() {
    elementCount = 0;
  }

  public override XmlElement CreateElement( string prefix, string localname, string nsURI) {
    LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this );
    return elem;
  }

  public void IncrementElementCount() {
     elementCount++;
  }

  public int GetCount() {
     return elementCount;
  }
} // End LineInfoDocument class.

class LineInfoElement:XmlElement {

    internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ):base( prefix,localname,nsURI, doc ){
      ((LineInfoDocument)doc).IncrementElementCount();
    }
} // End LineInfoElement class.

public class Test {

  const String filename = "book.xml";
  public static void Main() {

     LineInfoDocument doc =new LineInfoDocument();
     doc.Load(filename);
     Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount());

  }
}
```

#### <a name="input"></a><span data-ttu-id="c465e-128">Giriş</span><span class="sxs-lookup"><span data-stu-id="c465e-128">Input</span></span>

<span data-ttu-id="c465e-129">book.xml</span><span class="sxs-lookup"><span data-stu-id="c465e-129">book.xml</span></span>

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a><span data-ttu-id="c465e-130">Çıktı</span><span class="sxs-lookup"><span data-stu-id="c465e-130">Output</span></span>

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a><span data-ttu-id="c465e-131">Düğüm olay Işleyicisi</span><span class="sxs-lookup"><span data-stu-id="c465e-131">Node Event Handler</span></span>

<span data-ttu-id="c465e-132">DOM 'ın .NET Framework uygulanması, bir XML belgesindeki düğümler değiştiğinde olayları almanıza ve işleyebilmenizi sağlayan bir olay sistemi de içerir.</span><span class="sxs-lookup"><span data-stu-id="c465e-132">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="c465e-133">Ve sınıflarını kullanarak,,,,, <xref:System.Xml.XmlNodeChangedEventHandler> <xref:System.Xml.XmlNodeChangedEventArgs> `NodeChanged` `NodeChanging` `NodeInserted` `NodeInserting` `NodeRemoved` ve `NodeRemoving` olaylarını yakalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c465e-133">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>

<span data-ttu-id="c465e-134">Olay işleme işlemi, özgün DOM sınıflarında olduğu gibi, türetilen sınıflarda tam olarak aynı şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="c465e-134">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>

<span data-ttu-id="c465e-135">Düğüm olay işleme hakkında daha fazla bilgi için bkz. [Olaylar](../../events/index.md) ve <xref:System.Xml.XmlNodeChangedEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="c465e-135">For more information regarding node event handling, see [Events](../../events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>

## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="c465e-136">Default öznitelikleri ve CreateElement yöntemi</span><span class="sxs-lookup"><span data-stu-id="c465e-136">Default Attributes and the CreateElement Method</span></span>

<span data-ttu-id="c465e-137"><xref:System.Xml.XmlDocument.CreateElement%2A>Türetilmiş bir sınıftaki yöntemi geçersiz kılıyorsa, belgeyi düzenlenirken yeni öğeler oluştururken varsayılan öznitelikler eklenmez.</span><span class="sxs-lookup"><span data-stu-id="c465e-137">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="c465e-138">Bu yalnızca düzenlenirken bir sorundur.</span><span class="sxs-lookup"><span data-stu-id="c465e-138">This is only an issue while editing.</span></span> <span data-ttu-id="c465e-139"><xref:System.Xml.XmlDocument.CreateElement%2A>Yöntemi ' a varsayılan öznitelikler eklemekten sorumlu olduğundan <xref:System.Xml.XmlDocument> , bu işlevselliği yönteminde kodmalısınız <xref:System.Xml.XmlDocument.CreateElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="c465e-139">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="c465e-140"><xref:System.Xml.XmlDocument>Varsayılan öznitelikleri içeren bir yüklüyorsanız, bunlar doğru şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="c465e-140">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="c465e-141">Varsayılan öznitelikler hakkında daha fazla bilgi için bkz. [Dom 'Daki öğeler Için yeni öznitelikler oluşturma](creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="c465e-141">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c465e-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c465e-142">See also</span></span>

- [<span data-ttu-id="c465e-143">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="c465e-143">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
