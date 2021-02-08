---
description: 'Daha fazla bilgi edinin: XML verilerini Işleme In-Memory'
title: XML Verilerini Bellek İçinde İşleme
ms.date: 03/30/2017
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 2990a922fa864849e0f46bcfc5d9da017e28495d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783202"
---
# <a name="processing-xml-data-in-memory"></a>XML Verilerini Bellek İçinde İşleme

Microsoft .NET Framework, XML verilerini işlemek için üç model içerir: <xref:System.Xml.XmlDocument> Class, <xref:System.Xml.XPath.XPathDocument> class ve [LINQ to XML (C#)](../../linq/linq-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).  
  
 <xref:System.Xml.XmlDocument>Sınıfı, W3C belge nesne modeli (DOM) düzey 1 çekirdeğini ve çekırdek DOM düzeyi 2 önerilerini uygular. DOM, bir XML belgesinin bellek içi (önbellek) ağaç gösterimidir. <xref:System.Xml.XmlDocument>Ve ilgili sınıfları Ile xml belgeleri oluşturabilir, verileri yükleyebilir ve erişebilir, verileri değiştirebilir ve değişiklikleri kaydedebilirsiniz.  
  
 <xref:System.Xml.XPath.XPathDocument>Sınıfı, XPath veri modelini temel alan salt okunabilir, bellek içi veri deposudur. <xref:System.Xml.XPath.XPathNavigator>Sınıfı, salt okunurdur sınıfının yanı sıra Read-Only sınıfında bulunan XML belgeleri üzerinde bir imleç modeli kullanarak birkaç düzen seçeneği ve gezinti özelliği sunar <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> .  
  
 [LINQ to XML](../../linq/linq-xml-overview.md) , XML verilerini işlemek için .NET Framework sürüm 3,5 ' de tanıtılan bir modeldir. [Dil Ile tümleşik sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)kullanan bellek içi bir modeldir. LINQ, yeni sorgu özellikleri sağlamak için C# ve Visual Basic dil sözdizimini genişletir.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [DOM Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-dom-model.md)  
 <xref:System.Xml.XmlDocument>XML verilerini işlemek için ve ilgili sınıflarının kullanımını açıklar.  
  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)  
 <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathNavigator> XML verilerini işlemek için, ve sınıflarının kullanımını açıklar.  
  
 [LINQ to XML Kullanarak XML Verilerini İşleme](process-xml-data-using-linq-to-xml.md)  
 LINQ to XML kısa bir genel bakış sağlar ve LINQ to XML belgelerine bağlantılar sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [XML belgeleri ve verileri](index.md)
