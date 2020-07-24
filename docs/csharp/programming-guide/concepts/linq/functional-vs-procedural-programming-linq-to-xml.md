---
title: İşlevsel ve yordamsal programlama (LINQ to XML) (C#)
description: XML işlemek için LINQ to XML hem yordamsal, hem de bellek içi XML ağacı değişikliğini ve bildirim temelli bir yaklaşım kullanan işlevsel oluşturmayı destekler.
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e19f9311c56f4fe2c5e7e5f228aca6c03c6fe04d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103660"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="0be4f-103">İşlevsel ve yordamsal programlama (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0be4f-103">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0be4f-104">Çeşitli türlerdeki XML uygulamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="0be4f-104">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="0be4f-105">Bazı uygulamalar kaynak XML belgelerini alır ve kaynak belgelerden farklı bir şekilde yeni XML belgeleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0be4f-105">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="0be4f-106">Bazı uygulamalar kaynak XML belgelerini alır ve sonuç belgelerini HTML veya CSV metin dosyaları gibi tamamen farklı bir biçimde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0be4f-106">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="0be4f-107">Bazı uygulamalar kaynak XML belgelerini alır ve bir veritabanına kayıt ekler.</span><span class="sxs-lookup"><span data-stu-id="0be4f-107">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="0be4f-108">Bazı uygulamalar, bir veritabanı gibi başka bir kaynaktan veri alır ve bundan XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0be4f-108">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="0be4f-109">Bunlar, XML uygulaması türlerinin hepsi değildir, ancak bunlar bir XML Programlayıcısının uygulamak zorunda olduğu işlevsellik türlerinin temsili bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="0be4f-109">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="0be4f-110">Bu tür uygulamaların tümünde, bir geliştiricinin uygulayabileceğiniz iki yaklaşım vardır:</span><span class="sxs-lookup"><span data-stu-id="0be4f-110">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="0be4f-111">Bildirim temelli bir yaklaşım kullanılarak işlevsel oluşturma.</span><span class="sxs-lookup"><span data-stu-id="0be4f-111">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="0be4f-112">Yordamsal kodu kullanarak bellek içi XML ağacı değişikliği.</span><span class="sxs-lookup"><span data-stu-id="0be4f-112">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="0be4f-113">LINQ to XML her iki yaklaşımı destekler.</span><span class="sxs-lookup"><span data-stu-id="0be4f-113">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="0be4f-114">İşlevsel yaklaşımı kullanırken, kaynak belgeleri alan ve istenen şekle sahip tamamen yeni sonuç belgeleri oluşturan dönüşümler yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="0be4f-114">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="0be4f-115">Bir XML ağacını yerinde değiştirirken, düğüm içi bir XML ağacındaki düğümlerde geçen ve gezinen, düğümleri ekleme, silme ve değiştirme gibi bir kod yazın.</span><span class="sxs-lookup"><span data-stu-id="0be4f-115">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="0be4f-116">LINQ to XML iki yaklaşımla de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0be4f-116">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="0be4f-117">Aynı sınıfları ve bazı durumlarda aynı yöntemleri kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="0be4f-117">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="0be4f-118">Ancak, iki yaklaşımdan oluşan yapı ve hedefler çok farklıdır.</span><span class="sxs-lookup"><span data-stu-id="0be4f-118">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="0be4f-119">Örneğin, farklı durumlarda, bir veya diğer yaklaşım genellikle daha iyi performansa sahip olur ve daha fazla veya daha az bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="0be4f-119">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="0be4f-120">Buna ek olarak, bir veya başka bir yaklaşım daha fazla erişilebilir kod yazmak ve sağlamak daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0be4f-120">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="0be4f-121">Bu iki yaklaşımı görmek için bkz. [bellek ıçı XML ağacı değişikliği ve Işlevsel oluşturma (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0be4f-121">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="0be4f-122">İşlev dönüştürmeleri yazma hakkında bir öğretici için bkz. [XML 'In saf Işlevsel dönüştürmeleri (C#)](./introduction-to-pure-functional-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="0be4f-122">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](./introduction-to-pure-functional-transformations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0be4f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0be4f-123">See also</span></span>

- [<span data-ttu-id="0be4f-124">LINQ to XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="0be4f-124">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
