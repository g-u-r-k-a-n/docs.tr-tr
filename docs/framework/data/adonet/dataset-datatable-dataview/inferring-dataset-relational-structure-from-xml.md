---
description: "Daha fazla bilgi edinin: XML 'den veri kümesi Ilişkisel yapısı"
title: XML’den DataSet İlişkisel Yapısını Çıkarma
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: d89b6a42e7e1bc3d7514f180329e9c1d877a67ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652230"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a><span data-ttu-id="4110e-103">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="4110e-103">Inferring DataSet Relational Structure from XML</span></span>

<span data-ttu-id="4110e-104">Öğesinin ilişkisel yapısı veya şeması <xref:System.Data.DataSet> tablo, sütun, kısıtlama ve ilişkilerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="4110e-104">The relational structure, or schema, of a <xref:System.Data.DataSet> is made up of tables, columns, constraints, and relations.</span></span> <span data-ttu-id="4110e-105"><xref:System.Data.DataSet>XML 'den yükleme yaparken, şema önceden tanımlanmış olabilir veya yüklenen XML 'den açık ya da çıkarım aracılığıyla oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="4110e-105">When loading a <xref:System.Data.DataSet> from XML, the schema can be predefined, or it can be created, either explicitly or through inference, from the XML being loaded.</span></span> <span data-ttu-id="4110e-106">XML 'den bir öğesinin şemasını ve içeriğini yükleme hakkında daha fazla bilgi için <xref:System.Data.DataSet> , bkz. xml 'Den [veri kümesi yükleme](loading-a-dataset-from-xml.md) ve [XML 'Den veri kümesi şema bilgilerini yükleme](loading-dataset-schema-information-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4110e-106">For more information about loading the schema and contents of a <xref:System.Data.DataSet> from XML, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md) and [Loading DataSet Schema Information from XML](loading-dataset-schema-information-from-xml.md).</span></span>  
  
 <span data-ttu-id="4110e-107"><xref:System.Data.DataSet>XML 'den bir şeması oluşturulduysa, tercih edilen yöntem, XML şeması tanım dili (xsd) kullanarak şemayı açıkça belirtmektir ( [XML ŞEMASıNDAN (xsd) DataSet Ilişkisel yapısını türetmede](deriving-dataset-relational-structure-from-xml-schema-xsd.md)açıklandığı gibi) veya AZALTıLMıŞ XML-Data (xdr).</span><span class="sxs-lookup"><span data-stu-id="4110e-107">If the schema of a <xref:System.Data.DataSet> is being created from XML, the preferred method is to explicitly specify the schema using either the XML Schema definition language (XSD) (as described in [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)) or the XML-Data Reduced (XDR).</span></span> <span data-ttu-id="4110e-108">XML 'de XML şeması veya XDR şeması kullanılabilir değilse, öğesinin şeması <xref:System.Data.DataSet> XML öğelerinin ve özniteliklerin yapısından çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="4110e-108">If no XML Schema or XDR schema is available in the XML, the schema of the <xref:System.Data.DataSet> can be inferred from the structure of the XML elements and attributes.</span></span>  
  
 <span data-ttu-id="4110e-109">Bu bölümde <xref:System.Data.DataSet> , XML öğelerini ve özniteliklerini ve bunların yapısını ve ortaya çıkarılan şemayı gösteren şema çıkarımı kuralları açıklanmaktadır <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="4110e-109">This section describes the rules for <xref:System.Data.DataSet> schema inference by showing XML elements and attributes and their structure, and the resulting inferred <xref:System.Data.DataSet> schema.</span></span>  
  
 <span data-ttu-id="4110e-110">Bir XML belgesinde bulunan özniteliklerin hepsi çıkarım işlemine dahil edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4110e-110">Not all attributes present in an XML document should be included in the inference process.</span></span> <span data-ttu-id="4110e-111">Ad alanı nitelikli öznitelikler, XML belgesi için önemli olan ancak şema için önemli olan meta verileri içerebilir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="4110e-111">Namespace-qualified attributes can include metadata that is important for the XML document but not for the <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="4110e-112">Kullanarak <xref:System.Data.DataSet.InferXmlSchema%2A> , çıkarım işlemi sırasında yok sayılacak ad alanlarını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4110e-112">Using <xref:System.Data.DataSet.InferXmlSchema%2A>, you can specify namespaces to be ignored during the inference process.</span></span> <span data-ttu-id="4110e-113">Daha fazla bilgi için bkz. [XML 'Den veri kümesi şema bilgilerini yükleme](loading-dataset-schema-information-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4110e-113">For more information, see [Loading DataSet Schema Information from XML](loading-dataset-schema-information-from-xml.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4110e-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4110e-114">In This Section</span></span>  

 [<span data-ttu-id="4110e-115">DataSet Şema Çıkarımı İşleminin Özeti</span><span class="sxs-lookup"><span data-stu-id="4110e-115">Summary of the DataSet Schema Inference Process</span></span>](summary-of-the-dataset-schema-inference-process.md)  
 <span data-ttu-id="4110e-116">XML 'nin şemasını göstermek için kurallara ilişkin üst düzey bir Özet sağlar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="4110e-116">Provides a high-level summary of the rules for inferring the schema of a <xref:System.Data.DataSet> from XML.</span></span>  
  
 [<span data-ttu-id="4110e-117">Tabloların Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="4110e-117">Inferring Tables</span></span>](inferring-tables.md)  
 <span data-ttu-id="4110e-118">İçinde tablo olarak çıkartılan XML öğelerini açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="4110e-118">Describes the XML elements that are inferred as tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="4110e-119">Sütunların Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="4110e-119">Inferring Columns</span></span>](inferring-columns.md)  
 <span data-ttu-id="4110e-120">Tablo sütunları olarak gösterilen XML öğelerini ve özniteliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4110e-120">Describes the XML elements and attributes that are inferred as table columns.</span></span>  
  
 [<span data-ttu-id="4110e-121">İlişkilerin Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="4110e-121">Inferring Relationships</span></span>](inferring-relationships.md)  
 <span data-ttu-id="4110e-122"><xref:System.Data.DataRelation> <xref:System.Data.ForeignKeyConstraint> İç içe yerleştirilmiş, çıkartılan tablolar için oluşturulan ve nesnelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4110e-122">Describes the <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects created for nested, inferred tables.</span></span>  
  
 [<span data-ttu-id="4110e-123">Öğe Metni Çıkarımını Yapma</span><span class="sxs-lookup"><span data-stu-id="4110e-123">Inferring Element Text</span></span>](inferring-element-text.md)  
 <span data-ttu-id="4110e-124">XML öğelerinde metin için oluşturulan sütunları açıklar ve XML öğelerinde metin yok sayıldığında açıklar.</span><span class="sxs-lookup"><span data-stu-id="4110e-124">Describes the columns that are created for text in XML elements, and explains when text in XML elements is ignored.</span></span>  
  
 [<span data-ttu-id="4110e-125">Çıkarım Sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="4110e-125">Inference Limitations</span></span>](inference-limitations.md)  
 <span data-ttu-id="4110e-126">Şema çıkarımı kısıtlamalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4110e-126">Discusses the limitations of schema inference.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4110e-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="4110e-127">Related Sections</span></span>  

 [<span data-ttu-id="4110e-128">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="4110e-128">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="4110e-129"><xref:System.Data.DataSet>NESNESININ XML verileriyle nasıl etkileşime gireceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4110e-129">Describes how the <xref:System.Data.DataSet> object interacts with XML data.</span></span>  
  
 [<span data-ttu-id="4110e-130">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="4110e-130">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="4110e-131"><xref:System.Data.DataSet>XML şeması tanım dili (xsd) şemasından oluşturulan bir öğesinin ilişkisel yapısını veya şemasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4110e-131">Describes the relational structure, or schema, of a <xref:System.Data.DataSet> that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="4110e-132">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4110e-132">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="4110e-133">ADO.NET mimarisini ve bileşenlerini ve bunların mevcut veri kaynaklarına erişmek ve uygulama verilerini yönetmek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4110e-133">Describes the ADO.NET architecture and components and how to use them to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4110e-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4110e-134">See also</span></span>

- [<span data-ttu-id="4110e-135">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4110e-135">ADO.NET Overview</span></span>](../ado-net-overview.md)
