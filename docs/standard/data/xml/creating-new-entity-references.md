---
title: Yeni Öğe Başvuruları Oluşturma
ms.date: 03/30/2017
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
ms.openlocfilehash: 06052938a4595f45b65eaabf14f1348baf6ee9f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687417"
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="72060-102">Yeni Öğe Başvuruları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="72060-102">Creating New Entity References</span></span>

<span data-ttu-id="72060-103">**CreateEntityReference** yöntemi yeni bir **XmlEntityReference** düğümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72060-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="72060-104">XML Belge Nesne Modeli (DOM), başvurulmakta olan varlık adının zaten bildirilip toplanmadığını görmek için bakar.</span><span class="sxs-lookup"><span data-stu-id="72060-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="72060-105">Varsa, **XmlEntityReference** düğümünün alt düğümleri varlık bildirimi düğümünden kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="72060-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="72060-106">Eşleşen bir varlık bildirimi yoksa, bir boş metin düğümü varlık başvurusu düğümünün tek alt öğesi olarak iliştirilir.</span><span class="sxs-lookup"><span data-stu-id="72060-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="72060-107">**XmlEntityReference** düğümünün alt düğümleri diğer düğümlerin kopyaları olduğundan, bu alt düğümler salt okunurdur ve değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="72060-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="72060-108">Düğümler kopyalandığında, Varlık başvurusunun noktasındaki kapsamda bir ad alanı olabilir.</span><span class="sxs-lookup"><span data-stu-id="72060-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="72060-109">Bu ad alanı, oluşturulan herhangi bir öğe veya öznitelik düğümünün yapılandırmasını etkiler.</span><span class="sxs-lookup"><span data-stu-id="72060-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72060-110">DOM, yalnızca **EntityReference** düğümünü belgeye eklediğinizde alt düğümleri **EntityReference** 'a ekler.</span><span class="sxs-lookup"><span data-stu-id="72060-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="72060-111">Yeni oluşturulan **EntityReference** düğümlerinde alt düğüm yok.</span><span class="sxs-lookup"><span data-stu-id="72060-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="72060-112">**XmlDataDocument** , **XmlDocument**'ın türetilmiş bir sınıfı olsa da, **XmlDataDocument** varlık başvurularının oluşturulmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="72060-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="72060-113">Bunun nedeni, **EntityReference** alt öğelerinden salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="72060-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="72060-114">Bir **EntityReference** düğümünün alt öğeleri birden fazla bölgeye yayılabilirler.</span><span class="sxs-lookup"><span data-stu-id="72060-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="72060-115">Bu durumda, bir **EntityReference** 'ın parçasını içeren Bölgeyle ilişkili bir satırın parçası salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="72060-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72060-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72060-116">See also</span></span>

- [<span data-ttu-id="72060-117">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="72060-117">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
