---
description: 'Daha fazla bilgi edinin: uzantı Dizin Oluşturucu özelliği (Visual Basic)'
title: Extension Indexer Özelliği
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: ec165836f739db9a74ea266ebba32be5bb42cca6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700331"
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="fce74-103">Extension Indexer Özelliği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fce74-103">Extension Indexer Property (Visual Basic)</span></span>

<span data-ttu-id="fce74-104">Bir koleksiyondaki tek tek öğelere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="fce74-104">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fce74-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fce74-105">Syntax</span></span>  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="fce74-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="fce74-106">Parts</span></span>  
  
|<span data-ttu-id="fce74-107">Süre</span><span class="sxs-lookup"><span data-stu-id="fce74-107">Term</span></span>|<span data-ttu-id="fce74-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="fce74-108">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="fce74-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fce74-109">Required.</span></span> <span data-ttu-id="fce74-110">Sorgulanabilir bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="fce74-110">A queryable collection.</span></span> <span data-ttu-id="fce74-111">Diğer bir deyişle, veya uygulayan bir <xref:System.Collections.Generic.IEnumerable%601> koleksiyon <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="fce74-111">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="fce74-112">(</span><span class="sxs-lookup"><span data-stu-id="fce74-112">(</span></span>|<span data-ttu-id="fce74-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fce74-113">Required.</span></span> <span data-ttu-id="fce74-114">Dizin Oluşturucu özelliğinin başlangıcını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fce74-114">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="fce74-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fce74-115">Required.</span></span> <span data-ttu-id="fce74-116">Koleksiyonun bir öğesinin sıfır tabanlı konumunu belirten bir tamsayı ifadesi.</span><span class="sxs-lookup"><span data-stu-id="fce74-116">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="fce74-117">)</span><span class="sxs-lookup"><span data-stu-id="fce74-117">)</span></span>|<span data-ttu-id="fce74-118">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fce74-118">Required.</span></span> <span data-ttu-id="fce74-119">Dizin Oluşturucu özelliğinin sonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fce74-119">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="fce74-120">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fce74-120">Return Value</span></span>  

 <span data-ttu-id="fce74-121">Koleksiyonda belirtilen konumdan nesne veya `Nothing` Dizin aralık dışında.</span><span class="sxs-lookup"><span data-stu-id="fce74-121">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fce74-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fce74-122">Remarks</span></span>  

 <span data-ttu-id="fce74-123">Bir koleksiyondaki tek tek öğelere erişmek için uzantı Indexer özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fce74-123">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="fce74-124">Bu Indexer özelliği genellikle XML ekseni özelliklerinin çıkışında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fce74-124">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="fce74-125">XML alt ve XML alt öğe ekseni özellikleri, nesne koleksiyonlarını <xref:System.Xml.Linq.XElement> veya bir öznitelik değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fce74-125">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="fce74-126">Visual Basic derleyici, uzantı Dizin Oluşturucu özelliklerini yöntemine yapılan çağrılara dönüştürür `ElementAtOrDefault` .</span><span class="sxs-lookup"><span data-stu-id="fce74-126">The Visual Basic compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="fce74-127">Dizi Indexer 'ın aksine, `ElementAtOrDefault` Yöntem `Nothing` Dizin aralık dışında olduğunda döndürür.</span><span class="sxs-lookup"><span data-stu-id="fce74-127">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="fce74-128">Bu davranış, bir koleksiyondaki öğe sayısını kolayca belirleyene zaman yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="fce74-128">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="fce74-129">Bu Indexer özelliği veya uygulayan koleksiyonlar için bir uzantı özelliği gibidir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> : yalnızca koleksiyonda bir Dizin Oluşturucu veya varsayılan özellik yoksa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fce74-129">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="fce74-130">Bir veya nesneleri koleksiyonundaki ilk öğenin değerine erişmek için <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> XML `Value` özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fce74-130">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="fce74-131">Daha fazla bilgi için bkz. [XML Value özelliği](xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="fce74-131">For more information, see [XML Value Property](xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fce74-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="fce74-132">Example</span></span>  

 <span data-ttu-id="fce74-133">Aşağıdaki örnek, bir nesne koleksiyonundaki ikinci alt düğüme erişmek için uzantı dizin oluşturucunun nasıl kullanılacağını gösterir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="fce74-133">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="fce74-134">Koleksiyonda, nesne içinde adlı tüm alt öğeleri alan alt eksen özelliği kullanılarak erişilir `phone` `contact` .</span><span class="sxs-lookup"><span data-stu-id="fce74-134">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 <span data-ttu-id="fce74-135">Bu kod aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="fce74-135">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="fce74-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fce74-136">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="fce74-137">XML Eksen Özellikleri</span><span class="sxs-lookup"><span data-stu-id="fce74-137">XML Axis Properties</span></span>](index.md)
- [<span data-ttu-id="fce74-138">XML Değişmez Değerleri</span><span class="sxs-lookup"><span data-stu-id="fce74-138">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="fce74-139">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fce74-139">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="fce74-140">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="fce74-140">XML Value Property</span></span>](xml-value-property.md)
