---
title: Öznitelikleri Uygulama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 14cd6fef80ff9ae3a9d78531785edab0da7cc6b9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130910"
---
# <a name="applying-attributes"></a>Öznitelikleri Uygulama
Kodunuzdaki bir öğeye bir öznitelik uygulamak için aşağıdaki işlemi kullanın.  
  
1. Ad alanını .NET Framework'ten içe aktararak yeni bir öznitelik tanımlayın veya varolan bir özniteliği kullanın.  
  
2. Özniteliği öğenin hemen önüne ekleyerek kod öğesine uygulayın.  
  
     Her dilin kendi öznitelik sözdizimi bulunur. C++ ve C#'de öznitelik, köşeli ayraç içine alınır ve öğeden, satır sonu da içerebilen boşluk ile ayrılır. Visual Basic'te öznitelik, açılı ayraç içine alınır ve aynı mantıksal satırda bulunması gerekir; eğer bir satır sonu isterseniz satır devamı karakteri kullanabilirsiniz.
  
3. Öznitelik için konumsal parametreleri ve adlandırılmış parametreleri belirtin.  
  
     Konumsal parametreler gereklidir ve adlandırılmış parametrelerden önce gelmeleri gerekir; öznitelik oluşturucularından birinin parametrelerine karşılık gelirler. Adlandırılmış parametreler isteğe bağlıdır ve özniteliğin okuma/yazma özelliklerine karşılık gelirler. Ve C++ C#' de, her bir isteğe bağlı parametre için `name`=`value` belirtin; burada `name` özelliğin adıdır. Visual Basic'te, `name`:=`value` belirtin.  
  
 Kodunuzu derlediğinizde öznitelik meta verilere yayılır ve çalışma zamanı yansıma hizmetleri ile ortak dil çalışma zamanı ve herhangi bir özel araç veya uygulama tarafından kullanılabilir olur.  
  
 Kural gereği, tüm öznitelik adları Öznitelik ile biter. Ancak, Visual Basic ve C# gibi çalışma zamanını hedef alan çeşitli diller, bir özniteliğin tam adını belirtmenizi gerektirmez. Örneğin, <xref:System.ObsoleteAttribute?displayProperty=nameWithType>başlatmak istiyorsanız, yalnızca **eski**olarak başvurulmalıdır.  
  
## <a name="applying-an-attribute-to-a-method"></a>Bir Yönteme Öznitelik Uygulama  
 Aşağıdaki kod örneği, kodu eski olarak işaretleyen **System. Kullanımdan kaldırılmış Teattribute**'un nasıl bildirilemeyeceğini gösterir. `"Will be removed in next version"` dizesi özniteliğe geçirilir. Bu öznitelik, özniteliğin açıkladığı kod çağırıldığında geçirilen dizeyi görüntüleyen bir derleyici uyarısına neden olur.  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a>Öznitelikleri Derleme Düzeyinde Uygulama  
 Derleme düzeyinde bir öznitelik uygulamak istiyorsanız, **derleme** (Visual Basic`Assembly`) anahtar sözcüğünü kullanın. Aşağıdaki kod, derleme düzeyinde uygulanan **Assemblytitleözniteliğini** gösterir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 Bu öznitelik uygulandığında `"My Assembly"` dizesi, dosyanın meta veri bölümündeki derleme bildirimine yerleştirilir. Özniteliği, [MSIL Disassembler (ıldadsm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) kullanarak ya da özniteliği almak için özel bir program oluşturarak görüntüleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelikler](../../../docs/standard/attributes/index.md)
- [Özniteliklerde Depolanan Bilgileri Alma](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)
- [Tiren](/cpp/windows/attributed-programming-concepts)
- [Öznitelikler (C#)](../../csharp/programming-guide/concepts/attributes/index.md)
- [Özniteliklere genel bakış (Visual Basic)](../../visual-basic/programming-guide/concepts/attributes/index.md)
