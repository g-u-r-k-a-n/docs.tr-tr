---
description: ': GetXmlNamespace Işleci hakkında daha fazla bilgi edinin (Visual Basic)'
title: GetXmlNamespace İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 704ac22493a0d6ce1255d171ae3b418313b74f09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665919"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="5e644-103">GetXmlNamespace İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e644-103">GetXmlNamespace Operator (Visual Basic)</span></span>

<span data-ttu-id="5e644-104"><xref:System.Xml.Linq.XNamespace>BELIRTILEN XML ad alanı ön ekine karşılık gelen nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="5e644-104">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e644-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5e644-105">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="5e644-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5e644-106">Parts</span></span>  

 `xmlNamespacePrefix`  
 <span data-ttu-id="5e644-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5e644-107">Optional.</span></span> <span data-ttu-id="5e644-108">XML ad alanı önekini tanımlayan dize.</span><span class="sxs-lookup"><span data-stu-id="5e644-108">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="5e644-109">Sağlanırsa, bu dize geçerli bir XML tanımlayıcısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e644-109">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="5e644-110">Daha fazla bilgi için bkz. [BELIRTILEN XML öğelerinin ve özniteliklerin adları](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5e644-110">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="5e644-111">Hiçbir önek belirtilmemişse, varsayılan ad alanı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5e644-111">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="5e644-112">Varsayılan ad alanı belirtilmemişse boş ad alanı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5e644-112">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e644-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5e644-113">Return Value</span></span>  

 <span data-ttu-id="5e644-114"><xref:System.Xml.Linq.XNamespace>XML ad alanı ön ekine karşılık gelen nesne.</span><span class="sxs-lookup"><span data-stu-id="5e644-114">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e644-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e644-115">Remarks</span></span>  

 <span data-ttu-id="5e644-116">`GetXmlNamespace`İşleci, <xref:System.Xml.Linq.XNamespace> XML ad alanı ön ekine karşılık gelen nesneyi alır `xmlNamespacePrefix` .</span><span class="sxs-lookup"><span data-stu-id="5e644-116">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="5e644-117">XML ad alanı öneklerini doğrudan XML değişmez değerleri ve XML eksen özellikleri içinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e644-117">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="5e644-118">Ancak, `GetXmlNamespace` kodunuzda kullanabilmeniz için bir ad alanı önekini bir nesneye dönüştürmek üzere işlecini kullanmanız gerekir <xref:System.Xml.Linq.XNamespace> .</span><span class="sxs-lookup"><span data-stu-id="5e644-118">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="5e644-119"><xref:System.Xml.Linq.XNamespace>Tam nitelikli bir nesne almak için bir nesneye Nitelenmemiş öğe adı ekleyebilirsiniz <xref:System.Xml.Linq.XName> , bu da birçok [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5e644-119">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e644-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e644-120">Example</span></span>  

 <span data-ttu-id="5e644-121">Aşağıdaki örnek `ns` BIR XML ad alanı öneki olarak içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="5e644-121">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="5e644-122">Daha sonra, bir XML sabit değeri oluşturmak ve nitelenmiş ada sahip ilk alt düğüme erişmek için ad alanının önekini kullanır `ns:phone` .</span><span class="sxs-lookup"><span data-stu-id="5e644-122">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="5e644-123">Daha sonra bu alt düğümü `ShowName` işlecini kullanarak tam adı oluşturan altyordam öğesine geçirir `GetXmlNamespace` .</span><span class="sxs-lookup"><span data-stu-id="5e644-123">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="5e644-124">`ShowName`Altyordam daha sonra <xref:System.Xml.Linq.XNode.Ancestors%2A> üst düğümü almak için tam adı yöntemine geçirir `ns:contact` .</span><span class="sxs-lookup"><span data-stu-id="5e644-124">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="5e644-125">`TestGetXmlNamespace.RunSample()`' İ çağırdığınızda, aşağıdaki metni içeren bir ileti kutusu görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="5e644-125">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="5e644-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e644-126">See also</span></span>

- [<span data-ttu-id="5e644-127">Imports Deyimi (XML Ad Alanı)</span><span class="sxs-lookup"><span data-stu-id="5e644-127">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="5e644-128">Visual Basic'de XML'e Erişme</span><span class="sxs-lookup"><span data-stu-id="5e644-128">Accessing XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/accessing-xml.md)
