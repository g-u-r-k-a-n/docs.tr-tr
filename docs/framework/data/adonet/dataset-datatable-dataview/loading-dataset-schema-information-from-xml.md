---
description: "Daha fazla bilgi edinin: XML 'den veri kümesi şema bilgilerini yükleme"
title: XML’den DataSet Schema Bilgilerini Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: dd3a327270d6f8e3086d7206dd6f44290415c55e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652113"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="3282d-103">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="3282d-103">Loading DataSet Schema Information from XML</span></span>

<span data-ttu-id="3282d-104">A <xref:System.Data.DataSet> (tablolarının, sütunlarının, ilişkilerin ve kısıtlamalarının) şeması programlı bir şekilde tanımlanabilir, bir veya BIR XML belgesinden **Fill** ya da **FillSchema** yöntemleriyle oluşturulur <xref:System.Data.Common.DataAdapter> .</span><span class="sxs-lookup"><span data-stu-id="3282d-104">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="3282d-105">Bir XML belgesinden **veri kümesi** şema bilgilerini yüklemek Için, **veri kümesinin** **ReadXmlSchema** veya **InferXmlSchema** yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3282d-105">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="3282d-106">**ReadXmlSchema** , XML şeması tanım DILI (xsd) şeması veya satır Içi XML şemasına sahıp bir XML belgesi Içeren belgeden **veri kümesi** şema bilgilerini yüklemenize veya çıkarmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3282d-106">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="3282d-107">**InferXmlSchema** , BELIRTTIĞINIZ belirli XML ad alanlarını YOKSAYARAK şemayı XML belgesinden çıkarmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3282d-107">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3282d-108">Bir **veri** kümesindeki tablo SıRALAMASı, xsd yapıları (iç içe geçmiş ilişkiler gibi) kullanılarak bellekte oluşturulmuş bir **veri kümesini** aktarmak IÇIN Web Hizmetleri veya XML serileştirme kullandığınızda korunmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3282d-108">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="3282d-109">Bu nedenle, **veri kümesinin** alıcısının bu durumda tablo sıralamasına bağlı olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3282d-109">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="3282d-110">Ancak, aktarılan **veri kümesinin** şeması, bellek içi OLUŞTURULMASı yerine xsd dosyalarından okunmadıysa tablo sıralaması her zaman korunur.</span><span class="sxs-lookup"><span data-stu-id="3282d-110">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="3282d-111">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="3282d-111">ReadXmlSchema</span></span>  

 <span data-ttu-id="3282d-112">Bir veri **kümesinin** şemasını herhangi bir veri yüklemeden bir XML belgesinden yüklemek için, veri **kümesinin** **ReadXmlSchema** yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3282d-112">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="3282d-113">**READXMLSCHEMA** XML şeması tanım DILI (xsd) şeması kullanılarak tanımlanmış **veri kümesi** şeması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3282d-113">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="3282d-114">**ReadXmlSchema** yöntemi bir dosya adı, bir akış veya yüklenecek XML belgesini Içeren bir **XmlReader** değeri alır.</span><span class="sxs-lookup"><span data-stu-id="3282d-114">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="3282d-115">XML belgesi yalnızca şemayı içerebilir veya veri içeren XML öğeleriyle birlikte satır içi şema içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3282d-115">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="3282d-116">Satır içi şemayı XML şeması olarak yazma hakkında daha fazla bilgi için bkz. [xml şemasından (xsd) DataSet Ilişkisel yapısını türetme](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="3282d-116">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="3282d-117">**ReadXmlSchema** ÖĞESINE geçirilen XML belgesi satır içi şema bilgisi Içermiyorsa, **ReadXmlSchema** şemayı XML belgesindeki öğelerden çıkaracaktır.</span><span class="sxs-lookup"><span data-stu-id="3282d-117">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="3282d-118">**Veri kümesi** zaten bir şema içeriyorsa, geçerli şema zaten mevcut değilse yeni tablolar eklenerek genişletilir.</span><span class="sxs-lookup"><span data-stu-id="3282d-118">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="3282d-119">Yeni sütunlar, var olan tablolara eklenmek üzere eklenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="3282d-119">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="3282d-120">Eklenmekte olan bir sütun, **veri kümesinde** zaten varsa ancak XML 'de bulunan sütunla uyumsuz bir türe sahipse, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3282d-120">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="3282d-121">**ReadXmlSchema** 'ın bir XML belgesinden bir şemayı nasıl kullandığını öğrenmek için bkz. [XML 'Den veri kümesi ilişkisel yapısını](inferring-dataset-relational-structure-from-xml.md)anlamak.</span><span class="sxs-lookup"><span data-stu-id="3282d-121">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="3282d-122">**ReadXmlSchema** yalnızca bir **veri kümesinin** şemasını yükler veya bu şemayı sağlasa da, **veri kümesinin** **ReadXml** yöntemi hem şemayı hem de XML belgesinde içerilen verileri yükler ya da bunları anlar.</span><span class="sxs-lookup"><span data-stu-id="3282d-122">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="3282d-123">Daha fazla bilgi için bkz. [XML 'Den veri kümesi yükleme](loading-a-dataset-from-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3282d-123">For more information, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="3282d-124">Aşağıdaki kod örnekleri, bir XML belgesinden veya akışından bir **veri kümesi** şemasının nasıl yükleneceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3282d-124">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="3282d-125">İlk örnek, **ReadXmlSchema** yöntemine GEÇIRILEN bir XML şema dosyası adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3282d-125">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="3282d-126">İkinci örnekte bir **System. IO. StreamReader** gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3282d-126">The second example shows a **System.IO.StreamReader**.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a><span data-ttu-id="3282d-127">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="3282d-127">InferXmlSchema</span></span>  

 <span data-ttu-id="3282d-128">Veri **kümesinin,** **veri kümesinin** **InferXmlSchema** yöntemini kullanarak bir XML belgesinden şemasını çıkarmasını da söyleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3282d-128">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="3282d-129">**InferXmlSchema** **, her ikisi** de de bir **XmlReadMode** for **InferSchema** ( **verileri ve** KERS şeması yükler) ve okunan belge satır içi şema içermiyorsa, her ikisi de aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="3282d-129">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="3282d-130">Ancak, **InferXmlSchema** , şema çıkarsandığınızda yok SAYıLACAK belirli XML ad alanlarını belirtmenize olanak tanıyan ek bir özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="3282d-130">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="3282d-131">**InferXmlSchema** iki gerekli bağımsız değişkeni alır: bir dosya adı, akış veya **XMLREADER** ile belirtilen XML belgesinin konumu. ve işlem tarafından yok sayılacak XML ad alanlarının dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="3282d-131">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="3282d-132">Örneğin, aşağıdaki XML 'i göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3282d-132">For example, consider the following XML:</span></span>  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>
  <Description od:adotype="203">Soft drinks and teas</Description>
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>
  <ReorderLevel od:adotype="3">10</ReorderLevel>
  <Discontinued od:adotype="11">0</Discontinued>
</Products>  
</NewDataSet>  
```  
  
 <span data-ttu-id="3282d-133">Önceki XML belgesindeki öğeler için belirtilen öznitelikler nedeniyle, **ınsecollection** 'ın bir **XmlReadMode** değeri olan **ReadXmlSchema** yöntemi ve **ReadXml** yöntemi, belgedeki her öğe için tablolar oluşturacak: **Kategoriler**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel** ve **Discontinued**.</span><span class="sxs-lookup"><span data-stu-id="3282d-133">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="3282d-134">(Daha fazla bilgi için bkz. [XML 'Den veri kümesi Ilişkisel yapısını](inferring-dataset-relational-structure-from-xml.md)anlamak.) Ancak, daha uygun bir yapı yalnızca **Kategoriler** ve **ürün** tabloları oluşturmak ve ardından **Kategoriler** tablosunda **CategoryID**, **CategoryName** ve **Description** sütunları, **Products** tablosundaki **ProductID**, **ReorderLevel** ve **Discontinued** sütunları oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3282d-134">(For more information, see [Inferring DataSet Relational Structure from XML](inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="3282d-135">Çıkarılan şemanın XML öğelerinde belirtilen öznitelikleri yoksaymasını sağlamak için, **InferXmlSchema** yöntemini kullanın ve aşağıdaki örnekte gösterildiği gibi, **OFFICEVERILERININ** yok sayılacak XML ad alanını belirtin.</span><span class="sxs-lookup"><span data-stu-id="3282d-135">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="3282d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3282d-136">See also</span></span>

- [<span data-ttu-id="3282d-137">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="3282d-137">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="3282d-138">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="3282d-138">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="3282d-139">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="3282d-139">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="3282d-140">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="3282d-140">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="3282d-141">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="3282d-141">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="3282d-142">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3282d-142">ADO.NET Overview</span></span>](../ado-net-overview.md)
