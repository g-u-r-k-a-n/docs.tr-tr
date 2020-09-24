---
title: Öğe Metni Çıkarımını Yapma
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 7389e24f39902edf041c3cd3502303b17fd008ba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164694"
---
# <a name="inferring-element-text"></a><span data-ttu-id="fd7f0-102">Öğe Metni Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="fd7f0-102">Inferring Element Text</span></span>

<span data-ttu-id="fd7f0-103">Bir öğe metin içeriyorsa ve tablo olarak (öznitelikler veya yinelenen öğeler içeren öğeler gibi) çıkarsmayacak alt öğeleri yoksa, **TableName_Text** adlı yeni bir sütun, öğe için çıkartılan tabloya eklenir.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="fd7f0-104">Öğesinde bulunan metin, tablodaki bir satıra eklenir ve yeni sütunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="fd7f0-105">Yeni sütunun **ColumnMapping** özelliği **MappingType. simpleContent**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="fd7f0-106">Örneğin, aşağıdaki XML 'i göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="fd7f0-107">Çıkarım işlemi, iki sütunlu **Element1** adlı bir tablo oluşturur: **attr1** ve **Element1_Text**.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="fd7f0-108">**Attr1** sütununun **ColumnMapping** özelliği **MappingType. Attribute**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="fd7f0-109">**Element1_Text** sütununun **ColumnMapping** özelliği **MappingType. simpleContent**olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="fd7f0-110">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fd7f0-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fd7f0-111">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="fd7f0-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fd7f0-112">attr1</span><span class="sxs-lookup"><span data-stu-id="fd7f0-112">attr1</span></span>|<span data-ttu-id="fd7f0-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="fd7f0-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="fd7f0-114">value1</span><span class="sxs-lookup"><span data-stu-id="fd7f0-114">value1</span></span>|<span data-ttu-id="fd7f0-115">Text1</span><span class="sxs-lookup"><span data-stu-id="fd7f0-115">Text1</span></span>|  
  
 <span data-ttu-id="fd7f0-116">Bir öğe metin içeriyorsa, ancak aynı zamanda metin içeren alt öğelere sahipse, öğesinde içerilen metni depolamak için tabloya bir sütun eklenmez.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="fd7f0-117">Öğesinde içerilen metin yok sayılır, ancak alt öğelerdeki metin, tablodaki bir satıra dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="fd7f0-118">Örneğin, aşağıdaki XML 'i göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="fd7f0-119">Çıkarım işlemi, **ChildElement1**adlı tek sütunlu **Element1** adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="fd7f0-120">**ChildElement1** öğesinin metni, tablodaki bir satıra dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="fd7f0-121">Diğer metin yok sayılacak.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-121">The other text will be ignored.</span></span> <span data-ttu-id="fd7f0-122">**ChildElement1** sütununun **ColumnMapping** özelliği **MappingType. element**olarak ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="fd7f0-123">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="fd7f0-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="fd7f0-124">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="fd7f0-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="fd7f0-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="fd7f0-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="fd7f0-126">Metin2</span><span class="sxs-lookup"><span data-stu-id="fd7f0-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd7f0-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd7f0-127">See also</span></span>

- [<span data-ttu-id="fd7f0-128">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="fd7f0-128">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="fd7f0-129">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="fd7f0-129">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="fd7f0-130">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="fd7f0-130">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="fd7f0-131">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="fd7f0-131">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="fd7f0-132">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="fd7f0-132">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="fd7f0-133">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fd7f0-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
