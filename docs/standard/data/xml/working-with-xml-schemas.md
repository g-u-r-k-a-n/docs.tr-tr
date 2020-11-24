---
title: XML Şemalarıyla Çalışma
ms.date: 03/30/2017
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
ms.openlocfilehash: 0290cd31d9477d2c5a30a6efa907263fed137258
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675496"
---
# <a name="working-with-xml-schemas"></a><span data-ttu-id="9957f-102">XML Şemalarıyla Çalışma</span><span class="sxs-lookup"><span data-stu-id="9957f-102">Working with XML Schemas</span></span>

<span data-ttu-id="9957f-103">Bir XML belgesinin yapısını, öğe ilişkilerini, veri türlerini ve içerik kısıtlamalarını tanımlamak için bir belge türü tanımı (DTD) veya XML şema tanımlama dili (XSD) şeması kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9957f-103">To define the structure of an XML document, as well as its element relationships, data types, and content constraints, you use a document type definition (DTD) or XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="9957f-104">Bir XML belgesi, World Wide Web Konsorsiyumu (W3C) genişletilebilir biçimlendirme dili (XML) 1,0 önerisi tarafından tanımlanan tüm sözdizimsel gereksinimleri karşılıyorsa, her ikisi de doğru biçimlendirilmemiş ve DTD veya şema tarafından tanımlanan kısıtlamalara uygun olmadığı takdirde geçerli kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="9957f-104">Although an XML document is considered to be well-formed if it meets all the syntactical requirements defined by the World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0 Recommendation, it is not considered valid unless it is both well-formed and conforms to the constraints defined by its DTD or schema.</span></span> <span data-ttu-id="9957f-105">Bu nedenle, tüm geçerli XML belgeleri iyi biçimlendirilmiş olsa da, iyi biçimlendirilmiş XML belgelerinin hepsi geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="9957f-105">Therefore, although all valid XML documents are well-formed, not all well-formed XML documents are valid.</span></span>  
  
 <span data-ttu-id="9957f-106">XML hakkında daha fazla bilgi için bkz. [W3C XML 1,0 önerisi](https://www.w3.org/TR/REC-xml/).</span><span class="sxs-lookup"><span data-stu-id="9957f-106">For more information about XML, see the [W3C XML 1.0 Recommendation](https://www.w3.org/TR/REC-xml/).</span></span> <span data-ttu-id="9957f-107">XML şeması hakkında daha fazla bilgi için bkz. [W3C XML şeması Bölüm 1: yapılar önerisi](https://www.w3.org/TR/xmlschema-1/) ve [W3C XML şeması Bölüm 2: veri türleri öneri](https://www.w3.org/TR/xmlschema-2/) önerileri.</span><span class="sxs-lookup"><span data-stu-id="9957f-107">For more information about XML Schema, see the [W3C XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/) and the [W3C XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9957f-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9957f-108">In This Section</span></span>  

 [<span data-ttu-id="9957f-109">XML Şema Nesne Modeli (SOM)</span><span class="sxs-lookup"><span data-stu-id="9957f-109">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)  
 <span data-ttu-id="9957f-110"><xref:System.Xml.Schema?displayProperty=nameWithType>Bir dosyadaki şema tanım dili (xsd) şemasını okumanızı veya programlı olarak bir şemayı bellek içinde oluşturmasını sağlayan bir sınıf kümesi sağlayan ad alanındaki şema nesne modelini (som) açıklar.</span><span class="sxs-lookup"><span data-stu-id="9957f-110">Discusses the Schema Object Model (SOM) in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that provides a set of classes that allows you to read a Schema definition language (XSD) schema from a file or programmatically create a schema in-memory.</span></span>  
  
 [<span data-ttu-id="9957f-111">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="9957f-111">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)  
 <span data-ttu-id="9957f-112"><xref:System.Xml.Schema.XmlSchemaSet>XSD şemalarının depolanabileceği ve doğrulandığı bir önbellek olan sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="9957f-112">Discusses the <xref:System.Xml.Schema.XmlSchemaSet> class that is a cache where XSD schemas can be stored and validated.</span></span>  
  
 [<span data-ttu-id="9957f-113">XmlSchemaValidator Gönderim Temelli Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="9957f-113">XmlSchemaValidator Push-Based Validation</span></span>](xmlschemavalidator-push-based-validation.md)  
 <span data-ttu-id="9957f-114"><xref:System.Xml.Schema.XmlSchemaValidator>XML verilerini, gönderme temelli bir şekılde xsd şemalarına karşı doğrulamak için etkili ve yüksek performanslı bir mekanizma sağlayan sınıfı açıklar.</span><span class="sxs-lookup"><span data-stu-id="9957f-114">Discusses the <xref:System.Xml.Schema.XmlSchemaValidator> class that provides an efficient, high-performance mechanism to validate XML data against XSD schemas in a push-based manner.</span></span>  
  
 [<span data-ttu-id="9957f-115">XML Şemasından Çıkarım Yapma</span><span class="sxs-lookup"><span data-stu-id="9957f-115">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)  
 <span data-ttu-id="9957f-116"><xref:System.Xml.Schema.XmlSchemaInference>Sınıfının BIR XML belgesi yapısından BIR xsd şemasını çıkarması için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9957f-116">Discusses how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XSD schema from the structure of an XML document.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9957f-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="9957f-117">Reference</span></span>  

 <span data-ttu-id="9957f-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="9957f-118"><xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader></span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9957f-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9957f-119">Related Sections</span></span>  

 [<span data-ttu-id="9957f-120">DOM’da XML Belgesi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="9957f-120">Validating an XML Document in the DOM</span></span>](validating-an-xml-document-in-the-dom.md)  
 <span data-ttu-id="9957f-121">Belge Nesne Modeli (DOM) içinde XML 'nin nasıl doğrulandığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9957f-121">Discusses how to validate the XML in the Document Object Model (DOM).</span></span> <span data-ttu-id="9957f-122">XML 'i DOM 'a yüklendiği şekilde doğrulayabilir veya DOM 'da önceden doğrulanmamış bir XML belgesini doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9957f-122">You can validate the XML as it is loaded into the DOM, or validate a previously unvalidated XML document in the DOM.</span></span>  
  
 [<span data-ttu-id="9957f-123">XPathNavigator Kullanarak Şema Doğrulama</span><span class="sxs-lookup"><span data-stu-id="9957f-123">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="9957f-124">Sınıfını kullanarak gezinmekte olan ve düzenlenmiş XML 'in nasıl doğrulandığını açıklar <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="9957f-124">Discusses how to validate XML being navigated and edited using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
