---
title: XML Şemalarını Dahil Etme veya İçeri Aktarma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
ms.openlocfilehash: d9a18876d8a5ba3067aa35c617b1e20fce0411f5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710784"
---
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="dd015-102">XML Şemalarını Dahil Etme veya İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="dd015-102">Including or Importing XML Schemas</span></span>
<span data-ttu-id="dd015-103">XML şeması, `<xs:import />` `<xs:include />`, ve `<xs:redefine />` öğelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="dd015-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="dd015-104">Bu şema öğeleri, dahil edilen veya içeri aktaran şemanın yapısını tamamlamak için kullanılabilen diğer XML şemalarına başvurur.</span><span class="sxs-lookup"><span data-stu-id="dd015-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="dd015-105"><xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> Ve <xref:System.Xml.Schema.XmlSchemaRedefine> sınıfları, şema nesne modeli (som) API 'sinde bu öğelerle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="dd015-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="dd015-106">XML şeması ekleme veya Içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="dd015-106">Including or Importing an XML Schema</span></span>  
 <span data-ttu-id="dd015-107">Aşağıdaki kod örneği, adres şeması ile [XML şemaları oluşturma](../../../../docs/standard/data/xml/building-xml-schemas.md) konusunda oluşturulan müşteri şemasını tamamlar.</span><span class="sxs-lookup"><span data-stu-id="dd015-107">The following code example supplements the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="dd015-108">Adres şeması ile müşterinin şeması, adres türlerini müşteri şemasında kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="dd015-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="dd015-109">Adres şeması, olduğu gibi adres şemasının bileşenlerini `<xs:include />` kullanmak `<xs:import />` için ya da öğelerinden birini kullanarak ya da herhangi bir bileşeni, müşteri şemasının ihtiyaçlarına uyacak `<xs:redefine />` şekilde değiştirmek için bir öğe kullanılarak birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="dd015-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="dd015-110">Adres şeması, müşteri şemasından farklı `targetNamespace` bir `<xs:import />` öğesine sahip olduğundan, öğesi ve bu nedenle içeri aktarma semantiği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd015-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="dd015-111">Kod örneği aşağıdaki adımlarda adres şemasını içerir.</span><span class="sxs-lookup"><span data-stu-id="dd015-111">The code example includes the address schema in the following steps.</span></span>  
  
1. <span data-ttu-id="dd015-112">Müşteri şemasını ve adres şemasını yeni <xref:System.Xml.Schema.XmlSchemaSet> bir nesneye ekler ve bunları derler.</span><span class="sxs-lookup"><span data-stu-id="dd015-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="dd015-113">Şemaları okurken veya derlerken karşılaşılan tüm şema doğrulama uyarıları ve hataları <xref:System.Xml.Schema.ValidationEventHandler> temsilci tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="dd015-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="dd015-114">Özelliği üzerinde yineleme <xref:System.Xml.Schema.XmlSchema> yaparak, <xref:System.Xml.Schema.XmlSchemaSet> ' den hem müşteri hem de adres şemaları için derlenmiş nesneleri alır. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A></span><span class="sxs-lookup"><span data-stu-id="dd015-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="dd015-115">Şemaların derlenmesi nedeniyle, şema sonrası derleme-bilgi kümesi (PSCı) özelliklerine erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="dd015-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="dd015-116">Bir <xref:System.Xml.Schema.XmlSchemaImport> nesnesi oluşturur, içeri aktarmanın <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> özelliğini adres şemasının ad alanına ayarlar, içeri aktarmanın <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> özelliğini adres şemasının <xref:System.Xml.Schema.XmlSchema> nesnesine ayarlar ve içeri aktarma özelliğini müşteri şemasının <xref:System.Xml.Schema.XmlSchema.Includes%2A> özelliğine ekler.</span><span class="sxs-lookup"><span data-stu-id="dd015-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4. <span data-ttu-id="dd015-117"><xref:System.Xml.Schema.XmlSchemaSet> Sınıfının <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> ve <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> yöntemlerini kullanarak müşteri şemasının <xref:System.Xml.Schema.XmlSchema> değiştirilen nesnesini yeniden işler ve derler ve konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="dd015-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5. <span data-ttu-id="dd015-118">Son olarak, müşteri şemasına içeri aktarılan tüm şemaları, müşterinin şeması <xref:System.Xml.Schema.XmlSchema.Includes%2A> özelliğini kullanarak konsola özyinelemeli olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="dd015-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="dd015-119"><xref:System.Xml.Schema.XmlSchema.Includes%2A> Özelliği, bir şemaya eklenen tüm içerme, içeri aktarmalar veya tekrar tanımlama işlemleri için erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd015-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="dd015-120">Aşağıda, tüm kod örneği ve konsoluna yazılan müşteri ve adres şemaları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dd015-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 <span data-ttu-id="dd015-121">, `<xs:import />`, Ve `<xs:include />` `<xs:redefine />` öğeleri ve <xref:System.Xml.Schema.XmlSchemaImport> <xref:System.Xml.Schema.XmlSchemaInclude> <xref:System.Xml.Schema.XmlSchemaRedefine> sınıfları hakkında daha fazla bilgi için bkz. [W3C XML şeması](https://www.w3.org/XML/Schema) ve <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı sınıfı başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="dd015-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](https://www.w3.org/XML/Schema) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd015-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd015-122">See also</span></span>

- [<span data-ttu-id="dd015-123">XML Şema Nesne Modeline (SOM) Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dd015-123">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [<span data-ttu-id="dd015-124">XML Şemaları Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="dd015-124">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="dd015-125">XML Şemaları Derleme</span><span class="sxs-lookup"><span data-stu-id="dd015-125">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)
- [<span data-ttu-id="dd015-126">XML Şemalarını Çapraz Geçirme</span><span class="sxs-lookup"><span data-stu-id="dd015-126">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [<span data-ttu-id="dd015-127">XML Şemalarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="dd015-127">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [<span data-ttu-id="dd015-128">Şema Derleme için XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="dd015-128">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
