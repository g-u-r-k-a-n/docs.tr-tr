---
title: İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: dc5b81fd06f2860283c8c5fa028af4b945e2b1e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150969"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="c078b-102">İç İçe Geçmiş Şema Öğeleri Arasında Örtük İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="c078b-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="c078b-103">Bir XML Şema tanım dili (XSD) şeması, birbirinin içinde iç içe olan karmaşık türlere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="c078b-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="c078b-104">Bu durumda, eşleme işlemi varsayılan eşleme uygular ve <xref:System.Data.DataSet>aşağıdaki leri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c078b-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="c078b-105">Karmaşık türlerin her biri (üst ve alt) için bir tablo.</span><span class="sxs-lookup"><span data-stu-id="c078b-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="c078b-106">Üst öğede benzersiz bir kısıtlama yoksa, *Tablo Adı*adı verilen tablo başına bir ek birincil anahtar sütunu, Tablo *Adı'nın* ana tablonun adı olduğu _Id.</span><span class="sxs-lookup"><span data-stu-id="c078b-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="c078b-107">Ek sütunu birincil anahtar olarak tanımlayan üst tablodaki birincil anahtar kısıtlaması **(IsPrimaryKey** özelliğini **True**olarak ayarlayarak).</span><span class="sxs-lookup"><span data-stu-id="c078b-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="c078b-108">Kısıtlama, 1,\# \# 2, 3 ve benzeri yerlerde Kısıtlama olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c078b-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="c078b-109">Örneğin, ilk kısıtlama için varsayılan adı Kısıtlama1 olduğunu.</span><span class="sxs-lookup"><span data-stu-id="c078b-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="c078b-110">Alt tablodaki yabancı anahtar kısıtlaması, ek sütunu ana tablonun birincil anahtarına başvuran yabancı anahtar olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c078b-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="c078b-111">Kısıtlama, *ParentTable'ın* üst tablonun adı, *ChildTable'ın* alt tablonun adı olduğu ParentTable_ChildTable adlandırılır. *ParentTable*</span><span class="sxs-lookup"><span data-stu-id="c078b-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="c078b-112">Üst ve alt tablolar arasında bir veri ilişkisi.</span><span class="sxs-lookup"><span data-stu-id="c078b-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="c078b-113">Aşağıdaki **örnekte, OrderDetail'ın** **Sipariş'in**alt öğesi olduğu bir şema gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c078b-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="c078b-114">XML Şema eşleme işlemi **DataSet'te**aşağıdakileri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c078b-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="c078b-115">Sipariş **Order** ve **OrderDetail** tablosu.</span><span class="sxs-lookup"><span data-stu-id="c078b-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="c078b-116">**Sipariş** tablosunda benzersiz bir kısıtlama.</span><span class="sxs-lookup"><span data-stu-id="c078b-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="c078b-117">**IsPrimaryKey** özelliğinin **True**olarak ayarladığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c078b-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="c078b-118">**OrderDetail** tablosunda yabancı anahtar kısıtlaması.</span><span class="sxs-lookup"><span data-stu-id="c078b-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- <span data-ttu-id="c078b-119">**Sipariş** ve **OrderDetail** tabloları arasındaki ilişki.</span><span class="sxs-lookup"><span data-stu-id="c078b-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="c078b-120">Düzen ve **OrderDetail** öğeleri şemada **Order** iç içe olduğundan, bu ilişkinin İç **Içe Geçen** özelliği **True** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c078b-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id
    ChildTable: OrderDetail  
    ChildColumns: Order_Id
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c078b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c078b-121">See also</span></span>

- [<span data-ttu-id="c078b-122">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c078b-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="c078b-123">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="c078b-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="c078b-124">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c078b-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
