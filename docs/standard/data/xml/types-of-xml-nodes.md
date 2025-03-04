---
description: 'Daha fazla bilgi edinin: XML düğümlerinin türleri'
title: XML Düğüm Türleri
ms.date: 03/30/2017
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
ms.openlocfilehash: 6a43d9259bc1798be962ec0c599299a2a663a0d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782890"
---
# <a name="types-of-xml-nodes"></a>XML Düğüm Türleri

Bir XML belgesi, düğüm ağacı olarak belleğe okuna, düğümlerin düğüm türleri düğümler oluşturulduğunda karardır. XML Belge Nesne Modeli (DOM), World Wide Web Konsorsiyumu (W3C) tarafından belirlendiği ve DOM yapı modelinde bölümünde listelenen çeşitli düğüm türleri türlerine sahiptir. Aşağıdaki tabloda düğüm türleri, bu düğüm türüne atanan nesne ve her birinin kısa bir açıklaması listelenmektedir.  
  
|DOM düğüm türü|Nesne|Description|  
|-------------------|------------|-----------------|  
|Belge|<xref:System.Xml.XmlDocument>|Ağaçtaki tüm düğümlerin kapsayıcısı. Her zaman kök öğesiyle aynı olmayan belge kökü olarak da bilinir.|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|Herhangi bir ağaç yapısı olmadan bir veya daha fazla düğüm içeren geçici bir paket.|  
|DocumentType|<xref:System.Xml.XmlDocumentType>|Düğümü temsil eder `<!DOCTYPE…>` .|  
|EntityReference|<xref:System.Xml.XmlEntityReference>|Genişletilmemiş varlık başvuru metnini temsil eder.|  
|Öğe|<xref:System.Xml.XmlElement>|Bir öğe düğümünü temsil eder.|  
|Özniteliği|<xref:System.Xml.XmlAttribute>|, Bir öğesinin özniteliğidir.|  
|Processingyönergesi|<xref:System.Xml.XmlProcessingInstruction>|Bir işleme yönergesi düğümüdür.|  
|Yorum|<xref:System.Xml.XmlComment>|Bir açıklama düğümü.|  
|Metin|<xref:System.Xml.XmlText>|Bir öğeye veya özniteliğe ait metin.|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|CDATA 'ı temsil eder.|  
|Varlık|<xref:System.Xml.XmlEntity>|`<!ENTITY…>`BIR XML belgesindeki bildirimleri, bir iç belge türü tanımı (DTD) alt kümesinden ya da dış DTD 'lerden ve parametre varlıklarından temsil eder.|  
|Gösterim|<xref:System.Xml.XmlNotation>|DTD 'de belirtilen bir gösterimi temsil eder.|  
  
 Bir öznitelik (*ATTR*), W3C DOM Level 1 bölümü 1,2 temel arabirimlerinde bir düğüm olarak listelense de, herhangi bir öğe düğümünün alt öğesi olarak kabul edilmez.  
  
 Aşağıdaki tabloda, W3C tarafından tanımlanmayan ek düğüm türleri gösterilmektedir, ancak bunlar Microsoft .NET Framework nesne modelinde, **XmlNodeType** numaralandırmalar olarak kullanıma sunulmuştur. Bu nedenle, bu düğüm türleri için eşleşen bir DOM düğüm türü sütunu yok.  
  
|Düğüm türü|Description|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|Bildirim düğümünü temsil eder `<?xml version="1.0"…>` .|  
|<xref:System.Xml.XmlSignificantWhitespace>|Karışık içerikte boşluk olan önemli boşluk temsil eder.|  
|<xref:System.Xml.XmlWhitespace>|Bir öğenin içeriğindeki boşluğu temsil eder.|  
|EndElement|**XmlReader** bir öğenin sonuna geldiğinde döndürülür.<br /><br /> Örnek XML: **\</item>**<br /><br /> Daha fazla bilgi için bkz. <xref:System.Xml.XmlNodeType>.|  
|EndEntity|**XmlReader** , çağrısının sonuna geldiğinde bir çağrının sonucunu aldığında döndürülür <xref:System.Xml.XmlReader.ResolveEntity%2A> . Daha fazla bilgi için bkz. <xref:System.Xml.XmlNodeType>.|  
  
 XML 'de okuyan ve düğüm ve içeriği hakkında bilgi yazdırmak için düğüm türlerinde bir Case yapısı kullanan bir kod örneğini görüntülemek için bkz <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A> ..  
  
 Düğüm türlerinin nesne hiyerarşisi ve bunların eşdeğer nesne adı hakkında daha fazla bilgi için bkz. [XML belge nesne modeli (DOM) hiyerarşisi](xml-document-object-model-dom-hierarchy.md). Düğüm ağacında oluşturulan nesneler hakkında daha fazla bilgi için, bkz. [nesne HIYERARŞISINI XML verileriyle eşleme](mapping-the-object-hierarchy-to-xml-data.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
