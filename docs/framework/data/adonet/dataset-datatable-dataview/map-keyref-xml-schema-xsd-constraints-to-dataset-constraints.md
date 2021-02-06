---
description: 'Hakkında daha fazla bilgi edinin: keyref XML şeması (XSD) kısıtlamalarını veri kümesi kısıtlamalarına eşleme'
title: Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: f9925cf68e0c8fd1258eeeb509664e0527e58526
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651983"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>Keyref XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme

**Keyref** öğesi bir belge içindeki öğeler arasında bağlantı kurmanıza olanak sağlar. Bu, ilişkisel bir veritabanındaki yabancı anahtar ilişkisine benzerdir. Bir şema **keyref** öğesini belirtiyorsa, öğesi şema eşleme işlemi sırasında, tablolarındaki sütunlarda karşılık gelen bir yabancı anahtar kısıtlamasına dönüştürülür <xref:System.Data.DataSet> . Varsayılan olarak, **keyref** öğesi ilişki üzerinde belirtilen **ParentTable**, **ChildTable**, **ParentColumn** ve **ChildColumn** özellikleriyle da bir ilişki oluşturur.  
  
 Aşağıdaki tabloda, **keyref** öğesinde belirtebileceğiniz **msdata** öznitelikleri özetlenmektedir.  
  
|Öznitelik adı|Description|  
|--------------------|-----------------|  
|**msdata: ConstraintOnly**|Şemada **keyref** öğesinde **ConstraintOnly = "true"** belirtilirse, bir kısıtlama oluşturulur, ancak ilişki oluşturulmaz. Bu öznitelik belirtilmemişse (veya **false** olarak ayarlanırsa), hem kısıtlama hem de Ilişki **veri kümesinde** oluşturulur.|  
|**msdata: ConstraintName**|**ConstraintName** özniteliği belirtilmişse, değeri kısıtlamanın adı olarak kullanılır. Aksi takdirde, şemadaki **keyref** öğesinin **Name** özniteliği, **veri kümesinde** kısıtlama adını sağlar.|  
|**msdata: UpdateRule**|Şemadaki **keyref** öğesinde **UpdateRule** özniteliği belirtilmişse, değeri **veri kümesindeki** **UpdateRule** kısıtlama özelliğine atanır. Aksi takdirde **UpdateRule** özelliği **Cascade** olarak ayarlanır.|  
|**msdata: DeleteRule**|Şemadaki **keyref** öğesinde **DeleteRule** özniteliği belirtilmişse, değeri **veri kümesindeki** **DeleteRule** kısıtlama özelliğine atanır. Aksi takdirde, **DeleteRule** özelliği **Cascade** olarak ayarlanır.|  
|**msdata: AcceptRejectRule**|Bir şemadaki **keyref** öğesinde **AcceptRejectRule** özniteliği belirtilmişse, değeri **veri kümesindeki** **AcceptRejectRule** kısıtlama özelliğine atanır. Aksi takdirde **AcceptRejectRule** özelliği **none** olarak ayarlanır.|  
  
 Aşağıdaki örnek, **Order** öğesinin **OrderNumber** alt öğesi ve **OrderDetail** öğesinin **OrderNo** alt öğesi arasındaki **anahtar** ve **keyref** ilişkilerini belirten bir şema içerir.  
  
 Örnekte, **OrderDetail** öğesinin **OrderNumber** alt öğesi **Order** öğesinin **OrderNo** anahtar alt öğesine başvurur.  
  
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
  
 XML şeması tanım dili (XSD) şema eşleme işlemi aşağıdaki **veri kümesini** iki tabloyla üretir:  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 Ayrıca, **veri kümesi** aşağıdaki kısıtlamaları tanımlar:  
  
- **Order** tablosundaki benzersiz bir kısıtlama.  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- **Order** ve **OrderDetail** tabloları arasındaki ilişki. **Iç içe** geçmiş özelliği **false** olarak ayarlanır çünkü iki öğe şemada iç içe değildir.  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- **OrderDetail** tablosundaki yabancı anahtar kısıtlaması.  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şeması (XSD) Kısıtlamalarını DataSet Kısıtlamaları ile Eşleme](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML Şemasından (XSD) DataSet İlişkileri Oluşturma](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
