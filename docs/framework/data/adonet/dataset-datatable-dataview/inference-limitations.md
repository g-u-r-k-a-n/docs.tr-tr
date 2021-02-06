---
description: 'Hakkında daha fazla bilgi edinin: çıkarım sınırlamaları'
title: Çıkarım Sınırlamaları
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 926e456acfc5eac2598be40490b72523facfd058
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652269"
---
# <a name="inference-limitations"></a><span data-ttu-id="43258-103">Çıkarım Sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="43258-103">Inference Limitations</span></span>

<span data-ttu-id="43258-104">XML 'deki bir şemayı işleme işlemi, <xref:System.Data.DataSet> her BELGEDEKI XML öğelerine bağlı olarak farklı şemalar oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="43258-104">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="43258-105">Örneğin, aşağıdaki XML belgelerini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="43258-105">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="43258-106">Document1</span><span class="sxs-lookup"><span data-stu-id="43258-106">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="43258-107">Document2</span><span class="sxs-lookup"><span data-stu-id="43258-107">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="43258-108">"Document1" için, çıkarım işlemi "DocumentElement" adlı bir **veri kümesi** ve "Element1" de yinelenen bir öğe olduğu Için "Element1" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43258-108">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="43258-109">**Veri kümesi:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="43258-109">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="43258-110">**Tablo:** Element1</span><span class="sxs-lookup"><span data-stu-id="43258-110">**Table:** Element1</span></span>  
  
|<span data-ttu-id="43258-111">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="43258-111">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="43258-112">Text1</span><span class="sxs-lookup"><span data-stu-id="43258-112">Text1</span></span>|  
|<span data-ttu-id="43258-113">Metin2</span><span class="sxs-lookup"><span data-stu-id="43258-113">Text2</span></span>|  
  
 <span data-ttu-id="43258-114">Ancak, "document2" için çıkarım işlemi "NewDataSet" adlı bir **veri kümesi** ve "DocumentElement" adlı bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="43258-114">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="43258-115">"Element1", hiç özniteliği olmadığından ve alt öğeleri bulunmadığından sütun olarak algılanır.</span><span class="sxs-lookup"><span data-stu-id="43258-115">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="43258-116">**Veri kümesi:** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="43258-116">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="43258-117">**Tablo:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="43258-117">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="43258-118">Element1</span><span class="sxs-lookup"><span data-stu-id="43258-118">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="43258-119">Text1</span><span class="sxs-lookup"><span data-stu-id="43258-119">Text1</span></span>|  
  
 <span data-ttu-id="43258-120">Bu iki XML belgesi aynı şemayı üretmeye yönelik olabilir, ancak çıkarım işlemi her belgedeki öğeleri temel alan çok farklı sonuçlar üretir.</span><span class="sxs-lookup"><span data-stu-id="43258-120">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="43258-121">XML belgesinden şema oluştururken oluşabilecek Tutarsızlıklardan kaçınmak için, XML 'den bir **veri kümesi** yüklerken XML şeması tanım DILI (xsd) veya XML-Data AZALTıLMıŞ (xdr) kullanarak bir şemayı açıkça belirtmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="43258-121">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="43258-122">XML şeması ile bir **veri kümesi** şemasını açıkça belirtme hakkında daha fazla bilgi için, bkz. [xml şemasından (xsd) DataSet ilişkisel yapısını türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="43258-122">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43258-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43258-123">See also</span></span>

- [<span data-ttu-id="43258-124">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="43258-124">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="43258-125">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="43258-125">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="43258-126">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="43258-126">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="43258-127">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="43258-127">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="43258-128">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="43258-128">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="43258-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="43258-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
