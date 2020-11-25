---
title: Var Olan Düğümleri Kopyalama
ms.date: 03/30/2017
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 651e9fc9dc0d1a50a2d15d382b3ca65f7fd4b7fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701438"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="546fc-102">Var Olan Düğümleri Kopyalama</span><span class="sxs-lookup"><span data-stu-id="546fc-102">Copy Existing Nodes</span></span>

<span data-ttu-id="546fc-103">XML Belge Nesne Modeli (DOM), **selectSingleNode**, **ChildNodes [int i]**, **öznitelikler [int i]** gibi bir düğümü seçmek için kullanabileceğiniz birçok yöntem ve özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="546fc-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="546fc-104">Düğüm seçildikten sonra, söz konusu düğüm türü için çalışan INSERT yöntemlerinden birini kullanarak ağaca ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="546fc-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="546fc-105">Ağaca bir düğüm eklemeye yönelik tek kısıtlama, belgenin düğüm eklendikten sonra yine de doğru biçimlendirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="546fc-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="546fc-106">Varolan bir düğüm DOM ağacına eklendiğinde, özgün konumundan kaldırılır ve hedef konumuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="546fc-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="546fc-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="546fc-107">See also</span></span>

- [<span data-ttu-id="546fc-108">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="546fc-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
