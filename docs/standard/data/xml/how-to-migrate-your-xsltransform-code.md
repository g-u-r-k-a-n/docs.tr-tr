---
title: 'Nasıl yapılır: XslTransform Kodunuzu Geçirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
ms.openlocfilehash: 42f721e56c803fb404f7885d126bea9560224f4c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824993"
---
# <a name="how-to-migrate-your-xsltransform-code"></a>Nasıl yapılır: XslTransform Kodunuzu Geçirme
Yeni XSLT sınıfları, mevcut sınıflara çok benzer olacak şekilde tasarlanmıştır. <xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, sınıfının yerini alır <xref:System.Xml.Xsl.XslTransform> . Stil sayfaları yöntemi kullanılarak derlenir <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> . Dönüşümler yöntemi kullanılarak yürütülür <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> . Aşağıdaki yordamlarda ortak XSLT görevleri gösterilmektedir ve sınıfı ile sınıf karşılaştırması kullanılarak kod karşılaştırılır <xref:System.Xml.Xsl.XslTransform> <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a>Bir dosyayı ve çıktıyı bir URI 'ye dönüştürmek için  
  
- Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a>Bir stil sayfası derlemek ve varsayılan kimlik bilgileriyle çözümleyici kullanmak için  
  
- Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a>XSLT parametresi kullanmak için  
  
- Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a>XSLT komut dosyalarını etkinleştirmek için  
  
- Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a>Sonuçları DOM nesnesine yüklemek için  
  
- Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
    > [!NOTE]
    > <xref:System.Xml.Xsl.XslCompiledTransform>Sınıfın, XSLT dönüştürme sonuçlarını nesne olarak döndüren bir yöntemi yoktur <xref:System.Xml.XmlReader> . Ancak, bir XML dosyasına çıktı verebilir ve XML dosyasını başka bir nesneye yükleyebilirsiniz.  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a>Sonuçları başka bir veri deposuna akışa almak için  
  
- Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfından Geçirme](migrating-from-the-xsltransform-class.md)
- [XslCompiledTransform Sınıfını Kullanma](using-the-xslcompiledtransform-class.md)
