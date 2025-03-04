---
title: XML Belgesinde Ad Alanlarını Yönetme
description: Bir XML belgesinde ad alanlarını yönetmeyi öğrenin. XML ad alanları, bir XML belgesindeki öğe ve öznitelik adlarını özel ve önceden tanımlanmış URI 'Ler ile ilişkilendirir.
ms.date: 03/30/2017
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: 120493de430c2372f3f71d1d1498ba880feda3d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720158"
---
# <a name="managing-namespaces-in-an-xml-document"></a>XML Belgesinde Ad Alanlarını Yönetme

XML ad alanları, bir XML belgesindeki öğe ve öznitelik adlarını özel ve önceden tanımlanmış URI 'Ler ile ilişkilendirir. Bu ilişkilendirmeleri oluşturmak için, ad alanı URI 'Leri için ön ekleri tanımlar ve bu önekleri, XML verilerinde öğe ve öznitelik adlarını nitelemek için kullanabilirsiniz. Ad alanları öğe ve öznitelik adı çakışmalarını önler ve aynı ada sahip öğelerin ve özniteliklerin işlenmesini ve farklı şekilde doğrulanmasını etkinleştirir.  
  
<a name="declare"></a>

## <a name="declaring-namespaces"></a>Ad alanlarını bildirme  

 Bir öğe üzerinde bir ad alanı bildirmek için `xmlns:` özniteliğini kullanın:  
  
 `xmlns:<name>=<"uri">`  
  
 Burada `<name>` ad alanı öneki ve `<"uri">` ad ALANıNı tanımlayan URI 'dir. Ön eki bildirdikten sonra, bir XML belgesindeki öğeleri ve öznitelikleri nitelemek ve bunları ad alanı URI 'siyle ilişkilendirmek için kullanabilirsiniz. Ad alanı ön eki bir belge boyunca kullanıldığından, bu değer kısa bir süre olmalıdır.  
  
 Bu örnek iki `BOOK` öğe tanımlar. İlk öğe önek tarafından nitelenir, `mybook` ve ikinci öğe önek tarafından nitelenir `bb` . Her önek farklı bir ad alanı URI 'siyle ilişkilendirilir:  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines" />
</mybook>
```  
  
 Bir öğenin belirli bir ad alanının parçası olduğunu belirtmek için, buna ad alanı öneki ekleyin. Örneğin, bir `Author` öğe `mybook` ad alanına aitse, olarak belirtilir `<mybook:Author>` .  
  
<a name="scope"></a>

## <a name="declaration-scope"></a>Bildirim kapsamı  

 Bir ad alanı, içinde bildirildiği öğenin sonuna kadar bildirim noktasından etkilidir. Bu örnekte, öğesinde tanımlanan ad alanı öğesi gibi `BOOK` öğe dışındaki öğelere uygulanmaz `BOOK` `Publisher` :  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 Ad alanı kullanılmadan önce bildirilmelidir, ancak XML belgesinin en üstünde görünmesini gerekmez.  
  
 Bir XML belgesinde birden çok ad alanı kullandığınızda, temizleyici bir arama belgesi oluşturmak için bir ad alanını varsayılan ad alanı olarak tanımlayabilirsiniz. Varsayılan ad alanı, kök öğesinde bildirilmiştir ve belgedeki tüm nitelenmemiş öğeler için geçerlidir. Varsayılan ad alanları özniteliklere değil yalnızca öğeler için geçerlidir.  
  
 Varsayılan ad alanını kullanmak için, öneki ve öğesindeki bildiriminden iki nokta üst üste atlayın:  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
...
</BOOK>
```  
  
## <a name="managing-namespaces"></a>Ad alanlarını yönetme  

 <xref:System.Xml.XmlNamespaceManager>Sınıfı, bir ad alanı URI 'leri ve bunların ön eklerini depolar ve bu koleksiyonda ad alanlarını arayabilir, eklemenize ve kaldırmanıza olanak tanır. Bazı bağlamlarda, daha iyi XML işleme performansı için bu sınıf gereklidir. Örneğin, <xref:System.Xml.Xsl.XsltContext> sınıfı <xref:System.Xml.XmlNamespaceManager> XPath desteği için kullanır.  
  
 Ad alanı Yöneticisi ad alanları üzerinde herhangi bir doğrulama gerçekleştirmez, ancak ön eklerin ve ad alanlarının zaten doğrulanmış olduğunu varsayar ve [W3C ad](https://www.w3.org/TR/REC-xml-names/) alanları belirtimine uyum sağlar.  
  
> [!NOTE]
> [C#](../../linq/linq-xml-overview.md) ' de LINQ to XML [Visual Basic](../../linq/linq-xml-overview.md) ve <xref:System.Xml.XmlNamespaceManager> ad alanlarını yönetmek için kullanmayın Visual Basic. LINQ to XML kullanırken ad alanlarını yönetme hakkında bilgi için bkz. [XML ad alanları (C#) Ile çalışma](../../linq/namespaces-overview.md) ve LINQ belgelerindeki [XML ad alanları (Visual Basic) ile](../../linq/namespaces-overview.md) çalışma.  
  
 Sınıfı ile gerçekleştirebileceğiniz yönetim ve arama görevlerinin bazıları aşağıda verilmiştir <xref:System.Xml.XmlNamespaceManager> . Daha fazla bilgi ve örnek için, her bir yöntem veya özellik için başvuru sayfasının bağlantılarını izleyin.  
  
|Amaç|Kullanın|  
|--------|---------|  
|Ad alanı Ekle|<xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> yöntemi|  
|Ad alanını kaldır|<xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> yöntemi|  
|Varsayılan ad alanı için URI 'yi bul|<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> özelliði|  
|Bir ad alanı öneki için URI bulma|<xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> yöntemi|  
|Bir ad alanı URI 'sinin önekini bulma|<xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> yöntemi|  
|Geçerli düğümdeki ad alanlarının listesini al|<xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> yöntemi|  
|Ad alanı kapsamı|<xref:System.Xml.XmlNamespaceManager.PushScope%2A> ve <xref:System.Xml.XmlNamespaceManager.PopScope%2A> yöntemleri|  
|Geçerli kapsamda bir ön ek tanımlanıp tanımlanmadığını denetleyin|<xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> yöntemi|  
|Ön ekleri ve URI 'Leri aramak için kullanılan ad tablosunu alın|<xref:System.Xml.XmlNamespaceManager.NameTable%2A> özelliði|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlNamespaceManager>
- [XML belgeleri ve verileri](index.md)
