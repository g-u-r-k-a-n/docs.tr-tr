---
title: 'Nasıl yapılır: düğüm parçasını dönüştürme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: 56e9ef6031a5736acfa066ed6c068f954bd5af8d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710823"
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="9bd8b-102">Nasıl yapılır: düğüm parçasını dönüştürme</span><span class="sxs-lookup"><span data-stu-id="9bd8b-102">How to: Transform a Node Fragment</span></span>
<span data-ttu-id="9bd8b-103">Bir <xref:System.Xml.XmlDocument> veya <xref:System.Xml.XPath.XPathDocument> nesnesi içindeki verileri dönüştürdüğünüzde XSLT dönüştürmeleri bir belge için bir bütün olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9bd8b-103">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="9bd8b-104">Diğer bir deyişle, belge kök düğümü dışında bir düğüm geçirirseniz, bu, dönüşüm işleminin yüklenen belgedeki tüm düğümlere erişmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="9bd8b-104">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="9bd8b-105">Bir düğüm parçasını dönüştürmek için yalnızca düğüm parçasını içeren ayrı bir nesne oluşturmanız ve bu nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine iletmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9bd8b-105">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="9bd8b-106">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9bd8b-106">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="9bd8b-107">Düğüm parçasını dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="9bd8b-107">To transform a node fragment</span></span>  
  
1. <span data-ttu-id="9bd8b-108">Kaynak belgeyi içeren bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9bd8b-108">Create an object containing the source document.</span></span>  
  
2. <span data-ttu-id="9bd8b-109">Dönüştürmek istediğiniz düğüm parçasını bulun.</span><span class="sxs-lookup"><span data-stu-id="9bd8b-109">Locate the node fragment you wish to transform.</span></span>  
  
3. <span data-ttu-id="9bd8b-110">Yalnızca düğüm parçamı ile ayrı bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9bd8b-110">Create separate object with just the node fragment.</span></span>  
  
4. <span data-ttu-id="9bd8b-111">Düğüm parçasını <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoduna geçirin.</span><span class="sxs-lookup"><span data-stu-id="9bd8b-111">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bd8b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="9bd8b-112">Example</span></span>  
 <span data-ttu-id="9bd8b-113">Aşağıdaki örnek bir düğüm parçasını dönüştürür ve sonuçları konsola verir.</span><span class="sxs-lookup"><span data-stu-id="9bd8b-113">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="9bd8b-114">Giriş</span><span class="sxs-lookup"><span data-stu-id="9bd8b-114">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="9bd8b-115">Books. xml</span><span class="sxs-lookup"><span data-stu-id="9bd8b-115">books.xml</span></span>  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="9bd8b-116">tek. Xsl</span><span class="sxs-lookup"><span data-stu-id="9bd8b-116">single.xsl</span></span>  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="9bd8b-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="9bd8b-117">Output</span></span>  
 <span data-ttu-id="9bd8b-118">Kitap başlığı, güvenirlik Man.</span><span class="sxs-lookup"><span data-stu-id="9bd8b-118">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd8b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bd8b-119">See also</span></span>

- [<span data-ttu-id="9bd8b-120">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="9bd8b-120">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
