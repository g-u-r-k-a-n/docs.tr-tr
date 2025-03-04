---
description: 'Daha fazla bilgi edinin: XSLT uzantı nesneleri'
title: XSLT Genişletme Nesneleri
ms.date: 03/30/2017
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: 5fc4ee8b3828219bc298a3ffc4c81bc342e2f591
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782539"
---
# <a name="xslt-extension-objects"></a>XSLT Genişletme Nesneleri

Uzantı nesneleri stil sayfalarının işlevlerini genişletmek için kullanılır. Uzantı nesneleri sınıfı tarafından korunur <xref:System.Xml.Xsl.XsltArgumentList> .  
  
 Katıştırılmış betik yerine uzantı nesnesi kullanmanın avantajları aşağıda verilmiştir:  
  
- Sınıfların daha iyi kapsüllemesini ve yeniden kullanılmasını sağlar.  
  
- Stil sayfalarının daha küçük ve sürdürülebilir olmasını sağlar.  
  
 XSLT uzantı nesneleri <xref:System.Xml.Xsl.XsltArgumentList> nesnesine yöntemi kullanılarak eklenir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> . Tam ad ve ad alanı URI 'SI, o zaman uzantı nesnesiyle ilişkilendirilir.  
  
> [!NOTE]
> Yöntemi çağırmak için FullTrust izin kümesi gereklidir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> . Daha fazla bilgi için bkz. [kod erişimi güvenliği](../../../framework/misc/code-access-security.md) ve [adlandırılmış izin kümeleri](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Uzantı nesnelerinden döndürülen veri türleri,,, ve ' nin dört temel XPath veri türünden biridir `number` `string` `Boolean` `node set` .  
  
 `params`Belirtilmemiş bir parametre sayısının geçirilmesine izin veren anahtar sözcüğü ile tanımlanmış herhangi bir yöntem, şu anda sınıfı tarafından desteklenmemektedir <xref:System.Xml.Xsl.XslCompiledTransform> . Anahtar sözcükle tanımlanmış herhangi bir yöntemi kullanan XSLT stil sayfaları `params` doğru çalışmaz. Ayrıntılar için bkz. [params](../../../csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>XSLT uzantı nesnesi kullanmak için  
  
1. Bir <xref:System.Xml.Xsl.XsltArgumentList> nesne oluşturun ve yöntemi kullanarak Uzantı nesnesini ekleyin <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .  
  
2. Uzantı nesnesini stil sayfasından çağırın.  
  
3. <xref:System.Xml.Xsl.XsltArgumentList>Nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](xslt-transformations.md)
- [XSLT Güvenlik Konuları](xslt-security-considerations.md)
