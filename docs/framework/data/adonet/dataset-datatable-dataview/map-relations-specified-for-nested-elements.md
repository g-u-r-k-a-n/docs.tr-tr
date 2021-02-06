---
description: 'Daha fazla bilgi edinin: Iç Içe öğeler için belirtilen eşleme Ilişkileri'
title: İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: a625ad5bfd590794d0362a991dc22f756f043f2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651944"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="618c9-103">İç İçe Geçmiş Öğeler için Belirtilen İlişkileri Eşleme</span><span class="sxs-lookup"><span data-stu-id="618c9-103">Map Relations Specified for Nested Elements</span></span>

<span data-ttu-id="618c9-104">Şemada, şemadaki iki öğe arasındaki eşlemeyi açıkça belirtmek için bir **msdata: ilişki** ek açıklaması bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="618c9-104">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="618c9-105">**Msdata: Relationship** içinde belirtilen iki öğe şemada iç içe bulunabilir, ancak olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="618c9-105">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="618c9-106">Eşleme işlemi, iki sütun arasında birincil anahtar/yabancı anahtar ilişkisi oluşturmak için şemadaki **msdata: Relationship** kullanır.</span><span class="sxs-lookup"><span data-stu-id="618c9-106">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="618c9-107">Aşağıdaki örnek, **OrderDetail** öğesinin **Order** öğesinin bir alt öğesi olduğu bir XML şemasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="618c9-107">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="618c9-108">**Msdata: Relationship** bu üst-alt ilişkiyi tanımlar ve sonuçta elde edilen **sipariş** tablosunun **OrderNumber** sütununun, sonuçta elde edilen **OrderDetail** tablosunun **OrderNo** sütunuyla ilişkili olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="618c9-108">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
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
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"
                                msdata:parent="Order"
                                msdata:child="OrderDetail"
                                msdata:parentkey="OrderNumber"
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
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
  
 <span data-ttu-id="618c9-109">XML Şeması eşleme işlemi içinde aşağıdakileri oluşturur <xref:System.Data.DataSet> :</span><span class="sxs-lookup"><span data-stu-id="618c9-109">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="618c9-110">Bir **Order** ve **OrderDetail** tablosu.</span><span class="sxs-lookup"><span data-stu-id="618c9-110">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="618c9-111">**Order** ve **OrderDetail** tabloları arasındaki ilişki.</span><span class="sxs-lookup"><span data-stu-id="618c9-111">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="618c9-112">**Order** ve **OrderDetail** öğeleri şemada iç içe yerleştirilmiş olduğundan, bu ilişkinin **iç içe geçmiş** özelliği **true** olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="618c9-112">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="618c9-113">Eşleme işlemi herhangi bir kısıtlama oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="618c9-113">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="618c9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="618c9-114">See also</span></span>

- [<span data-ttu-id="618c9-115">XML Şemasından (XSD) DataSet İlişkileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="618c9-115">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="618c9-116">XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme</span><span class="sxs-lookup"><span data-stu-id="618c9-116">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="618c9-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="618c9-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
