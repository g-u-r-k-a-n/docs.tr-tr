---
description: 'Daha fazla bilgi edinin: XML şema kısıtlamaları ve Ilişkileri'
title: XML Şema Kısıtlamaları ve İlişkileri
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: c7847691537c4b754abcbacdeb367b1d92365ef3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651320"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="50f5a-103">XML Şema Kısıtlamaları ve İlişkileri</span><span class="sxs-lookup"><span data-stu-id="50f5a-103">XML Schema Constraints and Relationships</span></span>

<span data-ttu-id="50f5a-104">Bir XML şeması tanım dili (XSD) şemasında, kısıtlamalar (benzersiz, anahtar ve keyref kısıtlamaları) ve ilişkileri ( **msdata: Relationship** ek açıklaması kullanılarak) belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50f5a-104">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="50f5a-105">Bu konuda bir XML şemasında belirtilen kısıtlamaların ve ilişkilerin, oluşturmak için nasıl yorumlanacağı açıklanmaktadır <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="50f5a-105">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="50f5a-106">Genel olarak, bir XML şemasında, **veri kümesinde** yalnızca ilişkiler oluşturmak istiyorsanız **msdata: Relationship** ek açıklamasını belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50f5a-106">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="50f5a-107">Daha fazla bilgi için bkz. [xml şemasından (xsd) veri kümesi Ilişkileri oluşturma](generating-dataset-relations-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="50f5a-107">For more information, see [Generating DataSet Relations from XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="50f5a-108">**Veri kümesinde** kısıtlamalar oluşturmak istiyorsanız kısıtlamalar (Unique, Key ve keyref) belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50f5a-108">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="50f5a-109">Anahtar ve keyref kısıtlamalarının, bu konunun ilerleyen kısımlarında açıklandığı gibi ilişkiler oluşturmak için de kullanıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="50f5a-109">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="50f5a-110">Anahtar ve keyref kısıtlamalarından bir Ilişki oluşturma</span><span class="sxs-lookup"><span data-stu-id="50f5a-110">Generating a Relationship from key and keyref Constraints</span></span>  

 <span data-ttu-id="50f5a-111">**Msdata: ilişki** ek açıklamasını belirtmek yerıne, XML Şeması eşleme işlemi sırasında yalnızca kısıtlamaları değil, **veri kümesindeki** ilişkiyi değil, anahtar ve keyref kısıtlamalarını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="50f5a-111">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="50f5a-112">Ancak, `msdata:ConstraintOnly="true"` **keyref** öğesinde belirtirseniz, **veri kümesi** yalnızca kısıtlamaları içerir ve ilişkiyi içermez.</span><span class="sxs-lookup"><span data-stu-id="50f5a-112">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="50f5a-113">Aşağıdaki örnek, iç içe olmayan **Order** ve **OrderDetail** öğelerini içeren bir XML şemasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="50f5a-113">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="50f5a-114">Şema ayrıca Key ve keyref kısıtlamalarını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="50f5a-114">The schema also specifies key and keyref constraints.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="50f5a-115">XML Şeması eşleme işlemi sırasında oluşturulan **veri kümesi** **Order** ve **OrderDetail** tablolarını içerir.</span><span class="sxs-lookup"><span data-stu-id="50f5a-115">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="50f5a-116">Ayrıca, **veri kümesi** ilişkiler ve kısıtlamalar içerir.</span><span class="sxs-lookup"><span data-stu-id="50f5a-116">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="50f5a-117">Aşağıdaki örnek bu ilişkileri ve kısıtlamaları gösterir.</span><span class="sxs-lookup"><span data-stu-id="50f5a-117">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="50f5a-118">Şemanın **msdata: ilişki** ek açıklamasını belirtmediğini unutmayın. Bunun yerine, anahtar ve keyref kısıtlamaları ilişkiyi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50f5a-118">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
```text
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 <span data-ttu-id="50f5a-119">Önceki şema örneğinde **Order** ve **OrderDetail** öğeleri iç içe değildir.</span><span class="sxs-lookup"><span data-stu-id="50f5a-119">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="50f5a-120">Aşağıdaki şema örneğinde, bu öğeler iç içe.</span><span class="sxs-lookup"><span data-stu-id="50f5a-120">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="50f5a-121">Ancak, **msdata yok: ilişki** ek açıklaması belirtilmedi; Bu nedenle, örtük bir ilişki varsayılır.</span><span class="sxs-lookup"><span data-stu-id="50f5a-121">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="50f5a-122">Daha fazla bilgi için bkz. [Iç Içe geçmiş şema öğeleri arasında örtük Ilişkileri eşleme](map-implicit-relations-between-nested-schema-elements.md).</span><span class="sxs-lookup"><span data-stu-id="50f5a-122">For more information, see [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="50f5a-123">Şema ayrıca Key ve keyref kısıtlamalarını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="50f5a-123">The schema also specifies key and keyref constraints.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="50f5a-124">XML Şeması eşleme işleminden kaynaklanan **veri kümesi** iki tablo içerir:</span><span class="sxs-lookup"><span data-stu-id="50f5a-124">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="50f5a-125">**Veri kümesi** aynı zamanda iki ilişkiyi de içerir (bir diğeri **msdata: ilişki** ek açıklamasına ve diğeri anahtar ve keyref kısıtlamalarına bağlı olarak) ve çeşitli kısıtlamalara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="50f5a-125">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="50f5a-126">Aşağıdaki örnekte ilişkiler ve kısıtlamalar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="50f5a-126">The following example shows the relations and constraints.</span></span>  
  
```text
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 <span data-ttu-id="50f5a-127">İç içe geçmiş bir tabloya başvuran bir keyref kısıtlaması **msdata: IsNested = "true"** ek açıklamasını Içeriyorsa, **veri kümesi** , keyref kısıtlamasına ve ilgili benzersiz/anahtar kısıtlamasına dayalı tek bir iç içe ilişki oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50f5a-127">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f5a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50f5a-128">See also</span></span>

- [<span data-ttu-id="50f5a-129">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="50f5a-129">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="50f5a-130">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="50f5a-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
