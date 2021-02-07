---
description: 'Hakkında daha fazla bilgi edinin: Ilişkiler arasında sorgulama'
title: İlişkilerde Sorgulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: a29a24b21cc486f59ae7535db0e5f97831249ee0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695261"
---
# <a name="querying-across-relationships"></a>İlişkilerde Sorgulama

Sınıf tanımlarınızdaki diğer nesne veya diğer nesne koleksiyonları için başvurular doğrudan veritabanındaki yabancı anahtar ilişkilerine karşılık gelir. Bu ilişkileri kullanarak sorgulama özelliklerine erişin ve bir nesneden diğerine gidebilirsiniz. Bu erişim işlemleri, eşdeğer SQL 'de daha karmaşık birleştirmeler veya bağıntılı alt sorgular için çeviri yapar.  
  
 Örneğin, aşağıdaki sorgu, sonuçları yalnızca Londra 'da bulunan müşterilere yönelik siparişlerle sınırlamak için siparişlerden müşterilere gider.  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 İlişki özellikleri yoksa, aşağıdaki kodda olduğu gibi bunları SQL sorgusunda yaptığınız gibi, *birleşim* olarak el ile yazmanız gerekir:  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 *İlişki* özelliğini, bu belirli ilişkiyi bir kez tanımlamak için kullanabilirsiniz. Daha sonra daha kullanışlı bir nokta söz dizimini kullanabilirsiniz. Ancak, etki alanına özgü nesne modelleri genellikle hiyerarşiler veya grafikler olarak tanımlandığından ilişki özellikleri daha önemlisi vardır. Programdığı nesneler diğer nesnelere başvurmuş. Nesne-nesne ilişkilerinin, veritabanlarındaki yabancı anahtar stilli ilişkilerine karşılık geldiği bir rastlantı yalnızca bir gününüz. Özellik erişimi daha sonra birleştirmeleri yazmak için kullanışlı bir yol sağlar.  
  
 Bu konuda açıklandığı gibi, ilişki özellikleri sorgunun bir parçası olarak bir sorgunun sonuçlar tarafında daha önemlidir. Sorgu belirli bir müşteri hakkında veri aldıktan sonra, sınıf tanımı müşterilerin siparişlerinin olduğunu gösterir. Diğer bir deyişle, `Orders` belirli bir müşterinin özelliğinin bu müşterinin tüm siparişleriyle doldurulmuş bir koleksiyon olmasını bekler. Bu şekilde, bu şekilde sınıfları tanımlayarak bildirdiğiniz sözleşmenin olması gerekir. Sorgu sipariş istemese de, bu sipariþlerinizi görmeyi düşünüyorsunuz. Nesne modelinizi, ilgili nesneleri hemen kullanılabilir olan veritabanının bellek içi uzantısı olduğunu bir Yanıan koruyacak şekilde bekleolursunuz.  
  
 Artık ilişkilerimize sahip olduğunuza göre, sınıflarınızda tanımlanan ilişki özelliklerine başvurarak sorgu yazabilirsiniz. Bu ilişki başvuruları, veritabanındaki yabancı anahtar ilişkilerine karşılık gelir. Bu ilişkileri kullanan işlemler, eşdeğer SQL 'de daha karmaşık birleştirmeler için çeviri yapar. Bir ilişki tanımladığınız sürece ( <xref:System.Data.Linq.Mapping.AssociationAttribute> özniteliğini kullanarak), içinde açık bir katılmayı kodlamamalısınız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 Bu yanılsaın korunmasını sağlamak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *ertelenmiş yükleme* adlı bir teknik uygular. Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).  
  
 Çiftler listesini proje için aşağıdaki SQL sorgusunu göz önünde bulundurun `CustomerID` - `OrderID` :  
  
```sql
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Kullanarak aynı sonuçları elde etmek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , `Orders` sınıfında zaten var olan özellik başvurusunu kullanırsınız `Customer` . `Orders`Başvuru, `CustomerID` - `OrderID` aşağıdaki kodda olduğu gibi sorguyu yürütmek ve çiftleri proje için gerekli bilgileri sağlar:  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Ayrıca, tersten de yapabilirsiniz. Diğer bir deyişle, `Orders` `Customer` ilişkili nesneyle ilgili bilgilere erişmek için ilişki başvurusunu sorgulayabilir ve kullanabilirsiniz `Customer` . Aşağıdaki kod, `CustomerID` - `OrderID` önceki ile aynı çiftleri, ancak bunun yerine sorgulanarak bu süreyi sorgular `Orders` `Customers` .  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
