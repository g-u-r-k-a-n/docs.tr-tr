---
title: XmlNameTable Kullanarak Nesne Karşılaştırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
ms.openlocfilehash: 5e0f5de6fd956bcaaf30b592e04c432a5f824c52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734107"
---
# <a name="object-comparison-using-xmlnametable"></a>XmlNameTable Kullanarak Nesne Karşılaştırma

Oluşturulan **XMLDocuments**, bu belge için özel olarak oluşturulan bir ad tablosuna sahiptir. XML belgeye yüklendiğinde veya yeni öğeler ya da öznitelikler oluşturulduğunda, öznitelik ve öğe adları **XmlNameTable** içine konur. Ayrıca, başka bir belgedeki mevcut bir **NameTable** kullanarak bir **XmlDocument** oluşturabilirsiniz. **XMLDocuments** bir **XmlNameTable** parametresi alan Oluşturucu ile oluşturulduğunda, belge, **XmlNameTable** içinde depolanmış olan düğüm adlarına, ad alanlarına ve öneklere erişebilir. Ad tablosunun adlarla nasıl yüklenediğine bakılmaksızın, adlar tabloda depolandıktan sonra, adlar dize karşılaştırması yerine nesne karşılaştırması kullanılarak hızlı bir şekilde karşılaştırılabilir. Dizeler, kullanılarak ad tablosuna da eklenebilir <xref:System.Xml.NameTable.Add%2A> . Aşağıdaki kod örneği, oluşturulmakta olan bir ad tablosunu ve tabloya eklenen **MyString** dizesini gösterir. Bundan sonra, bu tablo kullanılarak bir **XmlDocument** oluşturulur ve **Myfile.xml** öğe ve öznitelik adları var olan ad tablosuna eklenir.  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 Aşağıdaki kod örneğinde belge oluşturma, belgeye eklenen iki yeni öğe, ayrıca bunları belge adı tablosuna ve adlara göre nesne karşılaştırması gösterilmektedir.  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 İki belge arasında geçirilen bir ad tablosunun yukarıdaki senaryosu, bir XML şeması tanım dili (xsd) şeması veya belge türü tanımı (DTD) ile uyumlu olan ve aynı dizeler tekrarlandığı bir e-ticaret sitesinde sipariş belgeleri gibi, aynı belge türü her zaman sürekli işlendiğinde tipik bir addır. Aynı ad tablosunun kullanılması, birden çok belgede aynı öğe adı gerçekleştiği için bir performans geliştirmesi sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
