---
title: Özel Öznitelikler Yazma
description: .NET ' te kendi özel öznitelerinizi tasarlayın. Özel öznitelikler temelde doğrudan veya dolaylı olarak System. Attribute 'dan türetilmiş sınıflardır.
ms.date: 07/17/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
ms.openlocfilehash: 670f34083834b35d26e6018372948022eec17d47
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889198"
---
# <a name="writing-custom-attributes"></a>Özel Öznitelikler Yazma
Kendi özel öznitelerinizi tasarlamak için çok sayıda yeni kavram oluşturmanız gerekmez. Nesne odaklı programlama hakkında bilgi sahibiyseniz ve sınıfların nasıl tasarlanacağını biliyorsanız, daha fazla bilgiye sahip olmanız gerekir. Özel öznitelikler temelde doğrudan veya dolaylı olarak türetilmiş geleneksel sınıflardır <xref:System.Attribute?displayProperty=nameWithType> . Geleneksel sınıflar gibi özel öznitelikler ise verileri depolayan ve alan yöntemler içerir.  
  
 Özel öznitelik sınıflarını doğru şekilde tasarlamak için birincil adımlar şunlardır:  
  
- [AttributeUsageAttribute uygulanıyor](#applying-the-attributeusageattribute)  
  
- [Öznitelik sınıfını bildirme](#declaring-the-attribute-class)  
  
- [Oluşturucu bildirme](#declaring-constructors)  
  
- [Özellikleri bildirme](#declaring-properties)  
  
 Bu bölümde, bu adımların her biri açıklanmakta ve özel bir [öznitelik örneği](#custom-attribute-example)ile sonlanır.  
  
## <a name="applying-the-attributeusageattribute"></a>AttributeUsageAttribute uygulanıyor  
 Özel bir öznitelik bildirimi, <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> öznitelik sınıfınızın bazı anahtar özelliklerini tanımlayan ile başlar. Örneğin, özniteetin diğer sınıfların devralınıp alınmayacağını belirtebilir veya özniteliğin hangi öğeleri uygulanacağını belirtebilirsiniz. Aşağıdaki kod parçası, ' nin nasıl kullanılacağını göstermektedir <xref:System.AttributeUsageAttribute> .  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 , <xref:System.AttributeUsageAttribute> Özel özniteliklerin oluşturulması için önemli olan üç üyeye sahiptir: [AttributeTargets](#attributetargets-member), [devralınan](#inherited-property)ve [AllowMultiple](#allowmultiple-property).  
  
### <a name="attributetargets-member"></a>AttributeTargets üyesi  
 Önceki örnekte, <xref:System.AttributeTargets.All?displayProperty=nameWithType> Bu özniteliğin tüm program öğelerine uygulanabileceğini belirten belirtilmiştir. Alternatif olarak, <xref:System.AttributeTargets.Class?displayProperty=nameWithType> özniteliğiyle yalnızca bir sınıfa uygulanabileceğini veya <xref:System.AttributeTargets.Method?displayProperty=nameWithType> özniteliğiyle yalnızca bir yönteme uygulanabileceğini belirten belirtebilirsiniz. Tüm program öğeleri, bu şekilde özel bir öznitelik tarafından açıklama için işaretlenebilir.  
  
 Ayrıca birden çok değer geçirebilirsiniz <xref:System.AttributeTargets> . Aşağıdaki kod parçası, özel bir özniteliğin herhangi bir sınıfa veya yönteme uygulanabileceğini belirtir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
### <a name="inherited-property"></a>Devralınan Özellik  
 <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType>Özelliği, özniteettiğiniz özniteliğin uygulandığı sınıflardan türetilmiş sınıflar tarafından devralınıp alınmayacağını belirtir. Bu özellik bir `true` (varsayılan) ya da bayrağını alır `false` . Aşağıdaki örnekte, `MyAttribute` varsayılan <xref:System.AttributeUsageAttribute.Inherited%2A> değerine sahiptir `true` , ancak `YourAttribute` <xref:System.AttributeUsageAttribute.Inherited%2A> değerini içerir `false` .  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 Bu iki öznitelik daha sonra temel sınıftaki bir yönteme uygulanır `MyClass` .  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 Son olarak, sınıfı `YourClass` temel sınıftan devralınır `MyClass` . Yöntemi `MyMethod` gösterir `MyAttribute` , ancak değil `YourAttribute` .  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
### <a name="allowmultiple-property"></a>AllowMultiple özelliği  
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType>Özelliği, özniteliğinde birden çok özniteliğin bir öğede mevcut olup olmadığını gösterir. Olarak ayarlanırsa `true` , birden çok örneğe izin verilir; `false` (varsayılan) olarak ayarlandıysa, yalnızca bir örneğe izin verilir.  
  
 Aşağıdaki örnekte, `MyAttribute` varsayılan <xref:System.AttributeUsageAttribute.AllowMultiple%2A> değerine sahiptir `false` , ancak `YourAttribute` değerini içerir `true` .  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 Bu özniteliklerin birden çok örneği uygulandığında `MyAttribute` bir derleyici hatası oluşturur. Aşağıdaki kod örneği, öğesinin geçerli kullanımını `YourAttribute` ve geçersiz kullanımını gösterir `MyAttribute` .  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 Hem <xref:System.AttributeUsageAttribute.AllowMultiple%2A> özelliği hem de <xref:System.AttributeUsageAttribute.Inherited%2A> özelliği olarak ayarlandıysa `true` , başka bir sınıftan devralınan bir sınıf bir özniteliği devralınabilir ve aynı özniteliğin aynı alt sınıfta uygulanan başka bir örneğine sahip olabilir. <xref:System.AttributeUsageAttribute.AllowMultiple%2A>Olarak ayarlanırsa `false` , üst sınıftaki özniteliklerin değerlerinin, alt sınıfta aynı özniteliğin yeni örnekleri tarafından üzerine yazılır.  
  
## <a name="declaring-the-attribute-class"></a>Öznitelik sınıfını bildirme  
 Uygulamasını uyguladıktan sonra <xref:System.AttributeUsageAttribute> , öznitedefinizin ayrıntılarını tanımlamaya başlayabilirsiniz. Bir öznitelik sınıfının bildirimi, aşağıdaki kodda gösterildiği gibi geleneksel bir sınıfın bildirimine benzer şekilde görünür.  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 Bu öznitelik tanımı aşağıdaki noktaları gösterir:  
  
- Öznitelik sınıfları ortak sınıf olarak bildirilmelidir.  
  
- Kural gereği, öznitelik sınıfının adı Word **özniteliğiyle** biter. Gerekli olmasa da, bu kural okunabilirlik için önerilir. Özniteliği uygulandığında, Word özniteliğinin eklenmesi isteğe bağlıdır.  
  
- Tüm öznitelik sınıflarının doğrudan veya dolaylı olarak devralması gerekir <xref:System.Attribute?displayProperty=nameWithType> .  
  
- Microsoft Visual Basic 'de tüm özel öznitelik sınıflarının <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> özniteliği olmalıdır.  
  
## <a name="declaring-constructors"></a>Oluşturucu bildirme  
 Öznitelikler, geleneksel sınıflarla aynı şekilde oluşturucular ile başlatılır. Aşağıdaki kod parçası tipik bir öznitelik oluşturucusunu gösterir. Bu ortak Oluşturucu bir parametre alır ve değerine eşit bir üye değişkenini ayarlar.  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 Oluşturucuyu farklı değer kombinasyonlarını kapsayacak şekilde aşırı yükleyebilirsiniz. Özel öznitelik sınıfınız için bir [özellik](/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120)) de tanımlarsanız, özniteliği başlatırken adlandırılmış ve Konumsal parametrelerin birleşimini kullanabilirsiniz. Genellikle, tüm gerekli parametreleri Konumsal olarak ve tüm isteğe bağlı parametreleri adlandırılmış olarak tanımlarsınız. Bu durumda, öznitelik gerekli parametre olmadan başlatılamaz. Diğer tüm parametreler isteğe bağlıdır. Visual Basic bir öznitelik sınıfı için oluşturucuların bir ParamArray bağımsız değişkeni kullanmamalıdır.  
  
 Aşağıdaki kod örneği, önceki oluşturucuyu kullanan bir özniteliğin isteğe bağlı ve gerekli parametreler kullanılarak nasıl uygulanabileceğini gösterir. Özniteliğin bir zorunlu Boole değeri ve bir isteğe bağlı dize özelliği olduğunu varsayar.  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
## <a name="declaring-properties"></a>Özellikleri bildirme  
 Adlandırılmış bir parametre tanımlamak veya öznitedefinizin tarafından depolanan değerleri döndürmek için kolay bir yol sağlamak istiyorsanız, bir [özellik](/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v=vs.120))bildirin. Öznitelik özellikleri döndürülecek veri türü açıklamasına sahip ortak varlıklar olarak bildirilmelidir. Özelliğin değerini tutacak değişkeni tanımlayın ve **Get** ve **set** yöntemleriyle ilişkilendirin. Aşağıdaki kod örneği, öznitelikinizdeki basit bir özelliğin nasıl uygulanacağını gösterir.  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
## <a name="custom-attribute-example"></a>Özel öznitelik örneği  
 Bu bölüm önceki bilgileri içerir ve bir kod bölümünün yazarı hakkındaki bilgileri belgeleyen basit bir özniteliğin nasıl tasarlanacağını gösterir. Bu örnekteki özniteliği, programcının adını ve düzeyini ve kodun gözden geçirilip geçirilmediğini depolar. Bu, kaydedilecek gerçek değerleri depolamak için üç özel değişken kullanır. Her değişken, değerleri alıp ayarlayan ortak bir özellik tarafından temsil edilir. Son olarak, Oluşturucu iki gerekli parametre ile tanımlanır.  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 Bu özniteliği, aşağıdaki yollarla tam adı, `DeveloperAttribute` veya kısaltılmış adı kullanarak uygulayabilirsiniz `Developer` .  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 İlk örnek, yalnızca gerekli adlandırılmış parametrelerle uygulanan özniteliği gösterir, ikinci örnek, hem gerekli hem de isteğe bağlı parametrelerle uygulanan özniteliği gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.AttributeUsageAttribute?displayProperty=nameWithType>
- [Öznitelikler](index.md)
