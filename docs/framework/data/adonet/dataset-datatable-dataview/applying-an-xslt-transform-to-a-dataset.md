---
description: 'Hakkında daha fazla bilgi edinin: bir veri kümesine XSLT dönüşümü uygulama'
title: DataSet’e XSLT Dönüşümü Uygulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: c7fc25441091112f7fbb7e4c1f8dd210d8cd0c5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725122"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a>DataSet’e XSLT Dönüşümü Uygulama

Öğesinin **WriteXml** yöntemi, <xref:System.Data.DataSet> bir **veri kümesinin** içeriğini XML verisi olarak yazmanızı sağlar. Ortak bir görev daha sonra söz konusu XML 'i XSL dönüşümleri (XSLT) kullanarak başka bir biçime dönüştürmeye yönelik olur. Ancak, bir **veri kümesini** ile eşitleme, <xref:System.Xml.XmlDataDocument> ilk olarak **veri** kümesinin içeriğini **WriteXml** kullanarak XML verileri olarak yazmak zorunda kalmadan bir **veri kümesinin** içeriğine bir XSLT stil sayfası uygulamanıza olanak sağlar.  
  
 Aşağıdaki örnek bir **veri kümesini** tablolar ve ilişkiler ile doldurur, **veri kümesini** bir **XmlDataDocument** ile eşitler ve XSLT stil sayfasını kullanarak bir HTML dosyası olarak **veri kümesinin** bir kısmını yazar. XSLT stil sayfasının içerikleri şunlardır:
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
<xsl:template match="CustomerOrders">  
  <HTML>  
  <STYLE>  
  BODY {font-family:verdana;font-size:9pt}  
  TD   {font-size:8pt}  
  </STYLE>  
    <BODY>  
    <TABLE BORDER="1">  
      <xsl:apply-templates select="Customers"/>  
    </TABLE>  
    </BODY>  
  </HTML>  
</xsl:template>  
  
<xsl:template match="Customers">  
    <TR><TD>  
      <xsl:value-of select="ContactName"/>, <xsl:value-of select="Phone"/><BR/>  
    </TD></TR>  
      <xsl:apply-templates select="Orders"/>  
</xsl:template>  
  
<xsl:template match="Orders">  
  <TABLE BORDER="1">  
    <TR><TD valign="top"><B>Order:</B></TD><TD valign="top"><xsl:value-of select="OrderID"/></TD></TR>  
    <TR><TD valign="top"><B>Date:</B></TD><TD valign="top"><xsl:value-of select="OrderDate"/></TD></TR>  
    <TR><TD valign="top"><B>Ship To:</B></TD>  
        <TD valign="top"><xsl:value-of select="ShipName"/><BR/>  
        <xsl:value-of select="ShipAddress"/><BR/>  
        <xsl:value-of select="ShipCity"/>, <xsl:value-of select="ShipRegion"/>  <xsl:value-of select="ShipPostalCode"/><BR/>  
        <xsl:value-of select="ShipCountry"/></TD></TR>  
  </TABLE>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 Aşağıdaki kod, **veri kümesini** doldurur ve XSLT stil sayfasını uygular.  
  
> [!NOTE]
> İlişki içeren bir **veri KÜMESINE** XSLT stil sayfası uyguluyorsanız, iç içe geçmiş her ilişki için ' ın **iç içe** özelliğini <xref:System.Data.DataRelation> **true** olarak ayarlarsanız en iyi performansı elde edersiniz. Bu, hiyerarşide gezinmek için doğal yukarıdan aşağı işleme uygulayan XSLT stil sayfalarını kullanmanıza ve verileri dönüştürmek için performans yoğunluğu olan XPath konum eksenlerini (örneğin, önceki eşdüzey ve stil sayfası düğüm testi ifadelerinde önceki eşdüzey ve aşağıdaki-eşdüzey) kullanmanın aksine kullanır. İç içe geçmiş ilişkiler hakkında daha fazla bilgi için bkz. [Iç Içe geçme istekleri](nesting-datarelations.md).  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)
  
Dim xslTran As XslTransform = New XslTransform  
xslTran.Load("transform.xsl")  
  
Dim writer As XmlTextWriter = New XmlTextWriter( _  
  "xslt_output.html", System.Text.Encoding.UTF8)  
  
xslTran.Transform(xmlDoc, Nothing, writer)  
writer.Close()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
DataSet custDS = new DataSet("CustomerDataSet");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(custDS, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(custDS, "Orders");  
  
connection.Close();  
  
custDS.Relations.Add("CustOrders",  
  custDS.Tables["Customers"].Columns["CustomerID"],  
                     custDS.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(custDS);
  
XslTransform xslTran = new XslTransform();  
xslTran.Load("transform.xsl");  
  
XmlTextWriter writer = new XmlTextWriter("xslt_output.html",
  System.Text.Encoding.UTF8);  
  
xslTran.Transform(xmlDoc, null, writer);  
writer.Close();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataSet ve XmlDataDocument Eşitlemesi](dataset-and-xmldatadocument-synchronization.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
