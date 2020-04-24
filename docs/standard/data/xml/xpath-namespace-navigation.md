---
title: XPath Ad Alanı Gezintisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: f35318b1439b762bf7c87cff217ed1787e8d007c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156328"
---
# <a name="xpath-namespace-navigation"></a>XPath Ad Alanı Gezintisi
XML belgeleriyle XPath sorguları kullanmak için, XML ad alanlarını ve ad alanları tarafından içerilen öğeleri doğru bir şekilde ele almanız gerekir. Ad alanları, adlar birden fazla bağlamda kullanıldığında oluşabilecek belirsizlikleri önler; Örneğin, ad `ID` bir XML belgesinin farklı öğeleriyle ilişkili birden fazla tanımlayıcıya başvurabilir. Ad alanı sözdizimi, bir XML belgesinin öğelerini ayırt eden URI 'Leri, adları ve önekleri belirtir.  
  
 Bu konudaki örnekte, ile <xref:System.Xml.XPath.XPathNavigator>bir XML belgesinde gezinme içindeki ön eklerin kullanımı gösterilmektedir. Ad alanları ve sözdizimi hakkında daha fazla bilgi için bkz. [XML Files: XML ad alanlarını anlama](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).  
  
## <a name="namespace-declarations"></a>Ad alanı bildirimleri  
 Ad alanı bildirimleri, bir örneği kullanılırken bir XML belgesinin öğelerini ayırt edilemez ve adreslenebilir hale getirir <xref:System.Xml.XPath.XPathNavigator>. Ad alanı önekleri ad alanlarını adresleme için kısa bir sözdizimi sağlar.  
  
 Ön ekler form tarafından tanımlanır: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` Bu sözdiziminde, "`e`" ön eki, ad alanının biçimsel URI 'si için bir kısaltmadır. `Body` Öğesini, sözdizimini kullanarak `Envelope` ad alanının bir üyesi olarak tanımlayabilirsiniz: `e:Body`.  
  
 Sonraki bölümde gezinti örneğinde olduğu gibi `response.xml` , aşağıdaki XML belgesine başvurulur.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a>Ad alanı ön ekine göre gezinti  
 Bu bölümdeki kod, bir önceki <xref:System.Xml.XPath.XPathNavigator> bölümdeki <xref:System.Xml.XmlNamespaceManager> XML belgesinden `Search` öğeyi seçmek için ve nesnelerini kullanır. Sorgu `xpath` , yoldaki her öğe için ad alanı öneklerini içerir. Her bir öğeyi içeren ad alanlarının kesin kimliğini belirtmek, `Search` <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> yöntemi tarafından öğesine doğru gezinmeyi sağlar.  
  
```csharp  
using (XmlReader reader = XmlReader.Create("response.xml"))  
{  
    XPathDocument doc = new XPathDocument(reader);  
    XPathNavigator nav = doc.CreateNavigator();
  
    XmlNamespaceManager nsmgr = new XmlNamespaceManager(nav.NameTable);  
    nsmgr.AddNamespace("e", @"http://schemas.xmlsoap.org/soap/envelope/");  
    nsmgr.AddNamespace("s", @"http://schemas.microsoft.com/v1/Search");  
    nsmgr.AddNamespace("r", @"http://schemas.microsoft.com/v1/Search/metadata");  
    nsmgr.AddNamespace("i", @"http://www.w3.org/2001/XMLSchema-instance");  
  
    string xpath = "/e:Envelope/e:Body/s:Search";  
  
    XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
    Console.WriteLine("Element Prefix:" + element.Prefix +
    " Local name:" + element.LocalName);  
    Console.WriteLine("Namespace URI: " + element.NamespaceURI);  
}  
```  
  
 Tam nitelikli ad alanları ve adların duyarlığı bir rahatlığından daha fazla. Belge tanımı ve önceki örneklerde bulunan kod içeren küçük bir deneme, tam olarak nitelenen öğe adları olmayan gezinmenin özel durum oluşturduğunu doğrular. Örneğin, öğe tanımı: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, ve sorgu: öğesinde ad alanı `xpath = "/s:Envelope/s:Body/Search";` öneki `Search` olmayan dize `null` `Search` öğesi yerine döner.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XPathNavigator Kullanarak XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
