---
title: Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 12fbd1f4332391b1acdcf12e101d82627ebbeaff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335993"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a><span data-ttu-id="9600f-102">Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9600f-102">Names of Declared XML Elements and Attributes (Visual Basic)</span></span>
<span data-ttu-id="9600f-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span><span class="sxs-lookup"><span data-stu-id="9600f-103">This topic provides Visual Basic guidelines for naming XML elements and attributes in XML literals.</span></span>  <span data-ttu-id="9600f-104">In an XML literal, you can specify a local name or a qualified name.</span><span class="sxs-lookup"><span data-stu-id="9600f-104">In an XML literal, you can specify a local name or a qualified name.</span></span> <span data-ttu-id="9600f-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span><span class="sxs-lookup"><span data-stu-id="9600f-105">A qualified name consists of an XML namespace prefix, a colon, and a local name.</span></span> <span data-ttu-id="9600f-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="9600f-106">For more information about XML namespace prefixes, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9600f-107">Kurallar</span><span class="sxs-lookup"><span data-stu-id="9600f-107">Rules</span></span>  
 <span data-ttu-id="9600f-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span><span class="sxs-lookup"><span data-stu-id="9600f-108">A local name of an element or attribute in Visual Basic must adhere to the following rules.</span></span>  
  
- <span data-ttu-id="9600f-109">It can begin with a namespace.</span><span class="sxs-lookup"><span data-stu-id="9600f-109">It can begin with a namespace.</span></span> <span data-ttu-id="9600f-110">It must begin with an alphabetical character or an underscore (`_`).</span><span class="sxs-lookup"><span data-stu-id="9600f-110">It must begin with an alphabetical character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="9600f-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span><span class="sxs-lookup"><span data-stu-id="9600f-111">It must contain only alphabetical characters, decimal digits, underscores, periods (.), and hyphens (-).</span></span>  
  
- <span data-ttu-id="9600f-112">It must not be more than 1,024 characters long.</span><span class="sxs-lookup"><span data-stu-id="9600f-112">It must not be more than 1,024 characters long.</span></span>  
  
- <span data-ttu-id="9600f-113">Colons that appear in names indicate namespace demarcation.</span><span class="sxs-lookup"><span data-stu-id="9600f-113">Colons that appear in names indicate namespace demarcation.</span></span> <span data-ttu-id="9600f-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span><span class="sxs-lookup"><span data-stu-id="9600f-114">Therefore, you can use colons only to specify an XML namespace for a particular name.</span></span>  
  
 <span data-ttu-id="9600f-115">In addition, you should adhere to the following guideline.</span><span class="sxs-lookup"><span data-stu-id="9600f-115">In addition, you should adhere to the following guideline.</span></span>  
  
- <span data-ttu-id="9600f-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span><span class="sxs-lookup"><span data-stu-id="9600f-116">The XML 1.0 specification reserves all names starting with the string "xml", of any capitalization variation.</span></span> <span data-ttu-id="9600f-117">Therefore, do not use those names for your element and attribute names.</span><span class="sxs-lookup"><span data-stu-id="9600f-117">Therefore, do not use those names for your element and attribute names.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="9600f-118">Name Length Guidelines</span><span class="sxs-lookup"><span data-stu-id="9600f-118">Name Length Guidelines</span></span>  
 <span data-ttu-id="9600f-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span><span class="sxs-lookup"><span data-stu-id="9600f-119">As a practical matter, a name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="9600f-120">This improves the readability of your code and reduces line length and source-file size.</span><span class="sxs-lookup"><span data-stu-id="9600f-120">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="9600f-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span><span class="sxs-lookup"><span data-stu-id="9600f-121">However, your name should not be so short that it does not adequately describe the element or how your code uses it.</span></span> <span data-ttu-id="9600f-122">This is important for the readability of your code.</span><span class="sxs-lookup"><span data-stu-id="9600f-122">This is important for the readability of your code.</span></span> <span data-ttu-id="9600f-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span><span class="sxs-lookup"><span data-stu-id="9600f-123">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, appropriate element names can save time.</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="9600f-124">Case Sensitivity in Names</span><span class="sxs-lookup"><span data-stu-id="9600f-124">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="9600f-125">XML element names are case sensitive.</span><span class="sxs-lookup"><span data-stu-id="9600f-125">XML element names are case sensitive.</span></span> <span data-ttu-id="9600f-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span><span class="sxs-lookup"><span data-stu-id="9600f-126">This means that when the Visual Basic compiler compares two names that differ in alphabetical case only, it interprets them as different names.</span></span> <span data-ttu-id="9600f-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span><span class="sxs-lookup"><span data-stu-id="9600f-127">For example, it interprets `ABC` and `abc` as referring to separate elements.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="9600f-128">XML Namespaces</span><span class="sxs-lookup"><span data-stu-id="9600f-128">XML Namespaces</span></span>  
 <span data-ttu-id="9600f-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span><span class="sxs-lookup"><span data-stu-id="9600f-129">When creating an XML element literal, you can specify the XML namespace prefix for the element name.</span></span> <span data-ttu-id="9600f-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="9600f-130">For more information, see [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9600f-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9600f-131">See also</span></span>

- [<span data-ttu-id="9600f-132">Creating XML in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9600f-132">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="9600f-133">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="9600f-133">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
