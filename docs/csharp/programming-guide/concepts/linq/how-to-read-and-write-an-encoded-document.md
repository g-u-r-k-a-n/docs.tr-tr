---
title: Kodlanmış bir belgeyi okuma ve yazma (C#)
description: XML ağacına XDeclaration ekleyerek ve kodlamayı istenen kod sayfası adına ayarlayarak C# dilinde kodlanmış XML belgesi oluşturmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: ed02b7467f4de71455da516a6c894070337684e7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104315"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a>Kodlanmış bir belgeyi okuma ve yazma (C#)
Kodlanmış bir XML belgesi oluşturmak için, XML ağacına bir ekler ve <xref:System.Xml.Linq.XDeclaration> kodlamayı istenen kod sayfası adına ayarlar.  
  
 Tarafından döndürülen herhangi <xref:System.Text.Encoding.WebName%2A> bir değer geçerli bir değerdir.  
  
 Kodlanmış bir belgeyi okuduğunuzda, <xref:System.Xml.Linq.XDeclaration.Encoding%2A> özelliği kod sayfası adına ayarlanır.  
  
 <xref:System.Xml.Linq.XDeclaration.Encoding%2A>Geçerli bir kod sayfası adı olarak ayarlarsanız, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belirtilen kodlamayla serileştirilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, biri UTF-8 kodlaması ve diğeri UTF-16 kodlaması ile iki belge oluşturur. Daha sonra belgeleri yükler ve kodlamayı konsola yazdırır.  
  
```csharp  
Console.WriteLine("Creating a document with utf-8 encoding");  
XDocument encodedDoc8 = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc8.Save("EncodedUtf8.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
Console.WriteLine("Creating a document with utf-16 encoding");  
XDocument encodedDoc16 = new XDocument(  
    new XDeclaration("1.0", "utf-16", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc16.Save("EncodedUtf16.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc8 = XDocument.Load("EncodedUtf8.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc16 = XDocument.Load("EncodedUtf16.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
Creating a document with utf-8 encoding  
Encoding is:utf-8  
  
Creating a document with utf-16 encoding  
Encoding is:utf-16  
  
Encoded document:  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-8  
  
Encoded document:  
<?xml version="1.0" encoding="utf-16" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-16  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
