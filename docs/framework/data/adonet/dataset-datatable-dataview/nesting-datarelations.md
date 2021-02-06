---
description: 'Daha fazla bilgi edinin: Iç Içe DataRelation'
title: DataRelations’ı İç İçe Yerleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: d998802a11fbb2bf414aa28b4beee95cac70a819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651762"
---
# <a name="nesting-datarelations"></a>DataRelations’ı İç İçe Yerleştirme

Verilerin ilişkisel bir gösteriminde, tek tek tablolar bir sütun veya sütun kümesi kullanılarak birbirleriyle ilişkili satırları içerir. ADO.NET <xref:System.Data.DataSet> , tablolar arasındaki ilişki bir kullanılarak uygulanır <xref:System.Data.DataRelation> . Bir **DataRelation** oluşturduğunuzda, sütunların üst-alt ilişkileri yalnızca ilişki üzerinden yönetilir. Tablolar ve sütunlar ayrı varlıklardır. XML 'in sağladığı verilerin hiyerarşik gösteriminde, üst-alt ilişkileri iç içe geçmiş alt öğeler içeren üst öğeler tarafından temsil edilir.  
  
 Bir **veri kümesi** , WRITEXML kullanılarak XML verileriyle eşitlendiğinde veya yazılmış olduğunda alt nesnelerin iç içe koyulmasını kolaylaştırmak için <xref:System.Xml.XmlDataDocument> , bir **iç içe geçmiş** özelliği gösterir.  Bir **DataRelation** 'ın **Nested** özelliğini **true** olarak ayarlamak, ilişkinin alt satırlarının XML verisi olarak yazıldığında veya bir **XmlDataDocument** ile eşitlendiğinde üst sütun içinde iç içe olmasına neden olur. **DataRelation** 'ın **Nested** özelliği varsayılan olarak **false 'tur**.  
  
 Örneğin, aşağıdaki **veri kümesini** göz önünde bulundurun.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 Bu **veri** kümesi için **DataRelation** nesnesinin **Nested** özelliği **true** olarak ayarlanmadığından, bu **veri kümesi** XML verisi olarak temsil edildiğinde alt nesneler üst öğeler içinde iç içe değildir. İç içe olmayan veri ilişkileri ile ilgili **veri kümesini** Içeren bir **veri kümesinin** XML gösterimini dönüştürmek, performansın düşmesine neden olabilir. Veri ilişkilerini iç içe etmenizi öneririz. Bunu yapmak için, **Iç Içe geçmiş** özelliği **true** olarak ayarlayın. Ardından, verileri bulmak ve dönüştürmek için yukarıdan aşağı hiyerarşik XPath sorgu ifadelerini kullanan XSLT stil sayfasına kod yazın.  
  
 Aşağıdaki kod örneği, **veri kümesinde** **WriteXml** çağırmanın sonucunu gösterir.  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 **Customers** öğesi ve **Orders** öğelerinin eşdüzey öğeler olarak gösterildiğini unutmayın. **Orders** öğelerinin kendi üst öğelerinin alt öğeleri olarak gösterilmesini Istiyorsanız, **DataRelation** 'ın **Nested** özelliği **true** olarak ayarlanmalıdır ve aşağıdakileri eklemelisiniz:  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 Aşağıdaki kod, elde edilen çıktının nasıl görüneceğine, ilgili üst öğelerinin içine yerleştirilmiş **Orders** öğeleriyle gösterir.  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)
- [DataRelations Ekleme](adding-datarelations.md)
- [DataSets, DataTables ve DataViews](index.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
