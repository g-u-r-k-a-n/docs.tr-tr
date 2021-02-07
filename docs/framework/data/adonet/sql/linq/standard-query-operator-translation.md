---
description: 'Daha fazla bilgi edinin: standart sorgu Işleci çevirisi'
title: Standart Sorgu İşleci Çevirisi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: e7e45e8f27f1e7d3c572f00ea014b4edb288b2b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681532"
---
# <a name="standard-query-operator-translation"></a>Standart Sorgu İşleci Çevirisi

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Standart sorgu Işleçlerini SQL komutlarına çevirir. Veritabanının sorgu işlemcisi SQL çevirisi 'nin yürütme semantiğini belirler.

Standart sorgu Işleçleri *sıralara* göre tanımlanır. Bir sıra *sıralanır* ve dizideki her öğe için başvuru kimliğini kullanır. Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

SQL, birincil olarak *sırasız değer kümeleriyle anlaşmalar yapar*. Sıralama genellikle, ara sonuçlar yerine bir sorgunun nihai sonucuna uygulanan, açıkça belirtilmiş, işleme sonrası bir işlemdir. Kimlik, değerler tarafından tanımlanır. Bu nedenle SQL sorguları, *kümeler* yerine çoklu kümeler (*bAdım*) ile uğraşmak üzere anlaşılmıştır.

Aşağıdaki paragraflarda, için SQL Server sağlayıcısı için standart sorgu Işleçleri ve SQL çevirisi arasındaki farklılıklar açıklanır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .

## <a name="operator-support"></a>İşleç desteği

### <a name="concat"></a>Concat

<xref:System.Linq.Enumerable.Concat%2A>Yöntemi, alıcı sırasının ve bağımsız değişkenin sırası aynı olduğu sıralı çoklu kümeler için tanımlanır. <xref:System.Linq.Enumerable.Concat%2A>`UNION ALL`Çoklu kümeler üzerinde olduğu gibi çalışarak ortak sıra kullanılır.

Son adım, sonuçlar üretilmadan önce SQL 'de sıralamaktır. <xref:System.Linq.Enumerable.Concat%2A> bağımsız değişkenlerinin sırasını korumaz. Uygun sıralamayı sağlamak için, sonuçlarını açıkça sipariş etmeniz gerekir <xref:System.Linq.Enumerable.Concat%2A> .

### <a name="intersect-except-union"></a>Intersect, Except, birleşim

<xref:System.Linq.Enumerable.Intersect%2A>Ve <xref:System.Linq.Enumerable.Except%2A> yöntemleri yalnızca kümeler üzerinde iyi tanımlanmış. Multisets semantiği tanımsızdır.

Yöntemi multisets 'ler <xref:System.Linq.Enumerable.Union%2A> için, birden çok küme için tanımlanır (SQL 'DEKI UNıON ALL yan tümcesinin sonucu etkin değildir).

### <a name="take-skip"></a>Al, atla

<xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> yöntemleri yalnızca *sıralı kümelere* karşı iyi tanımlanmış. Sıralanmamış kümeler veya birden çok küme semantiği tanımsızdır.

> [!NOTE]
> <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 ' de sorgularda kullanıldıkları bazı sınırlamalar vardır. Daha fazla bilgi için bkz. [sorun giderme](troubleshooting.md)içindeki "SQL Server 2000 'de özel durumları atla ve al" girişi.

SQL 'de sıralamaya yönelik sınırlamalar nedeniyle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu yöntemlerin bağımsız değişkeninin sıralamasını yöntemin sonucuna taşımaya çalışır. Örneğin, aşağıdaki sorguyu göz önünde bulundurun [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

Bu kod için oluşturulan SQL, aşağıdaki gibi sıralamayı sonuna taşıdır:

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

Belirtilen tüm sıralama, <xref:System.Linq.Enumerable.Take%2A> ve birlikte zincirleme zaman tutarlı hale gelmelidir <xref:System.Linq.Enumerable.Skip%2A> . Aksi takdirde, sonuçlar tanımsızdır.

Her ikisi de <xref:System.Linq.Enumerable.Take%2A> <xref:System.Linq.Enumerable.Skip%2A> , standart sorgu işleci belirtimine göre negatif olmayan, sabit tamsayı bağımsız değişkenleri için iyi tanımlanmıştır.

### <a name="operators-with-no-translation"></a>Çevirisi olmayan işleçler

Aşağıdaki yöntemler tarafından çevrilmez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . En yaygın neden, sıralanmamış çoklu kümeler ve diziler arasındaki farktır.

|İşleçler|Mantığı anladığınızdan|
|---------------|---------------|
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|SQL sorguları diziler üzerinde değil, çoklu kümeler üzerinde çalışır. `ORDER BY` sonuçlara uygulanan son yan tümce olmalıdır. Bu nedenle, bu iki yöntem için genel amaçlı bir çeviri yoktur.|
|<xref:System.Linq.Enumerable.Reverse%2A>|Bu yöntemin çevirisi, sıralı bir küme için mümkündür ancak şu anda tarafından çevrilmez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .|
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|Bu yöntemlerin çevirisi, sıralı bir küme için mümkündür ancak şu anda tarafından çevrilmez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .|
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|SQL sorguları, dizine eklenebilir diziler üzerinde değil, çoklu kümeler üzerinde çalışır.|
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (varsayılan bağımsız değişken ile aşırı yükleme)|Genel olarak, rastgele bir tanımlama grubu için varsayılan bir değer belirtilemez. Dış birleştirmeler aracılığıyla bazı durumlarda, diziler için null değerler mümkündür.|

## <a name="expression-translation"></a>İfade çevirisi

### <a name="null-semantics"></a>Null semantiği

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL 'de null karşılaştırma semantiğini uygulamaz. Karşılaştırma işleçleri, sözdizimsel olarak SQL eşdeğerlerine çevrilir. Bu nedenle, semantik, sunucu veya bağlantı ayarları tarafından tanımlanan SQL semantiğini yansıtır. Örneğin, iki null değer varsayılan SQL Server ayarları altında eşit olarak değerlendirilir, ancak semantiğini değiştirmek için ayarları değiştirebilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları çevirdiğinde sunucu ayarlarını dikkate almaz.

Null değerli bir karşılaştırma, uygun SQL sürümüne ( `is null` veya `is not null` ) çevrilir.

`null`Harmanlama içindeki değeri SQL Server tarafından tanımlanır. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] harmanlamayı değiştirmez.

### <a name="aggregates"></a>Toplamalar

Standart sorgu Işleci toplama yöntemi <xref:System.Linq.Enumerable.Sum%2A> boş bir sıra veya yalnızca null değer içeren bir sıra için sıfır olarak değerlendirilir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, SQL 'in semantiği değişmeden bırakılır ve boş bir <xref:System.Linq.Enumerable.Sum%2A> `null` sıra veya yalnızca null değerleri içeren bir sıra için sıfır yerine olarak değerlendirilir.

Ara sonuçlarda SQL sınırlamaları, içindeki toplamalar için geçerlidir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . <xref:System.Linq.Enumerable.Sum%2A>32 bitlik tamsayı miktarları 64 bit sonuçlar kullanılarak hesaplanmaz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Enumerable.Sum%2A> Standart sorgu işleci uygulamasının karşılık gelen bellek içi dizide taşma olmasına neden olmasa bile, bir çevirisi için taşma gerçekleşebilir.

Benzer şekilde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Enumerable.Average%2A> tamsayı değerlerinin çevirisi bir olarak değil bir olarak hesaplanır `integer` `double` .

### <a name="entity-arguments"></a>Varlık bağımsız değişkenleri

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , ve yöntemlerinde varlık türlerinin kullanılmasını sağlar <xref:System.Linq.Enumerable.GroupBy%2A> <xref:System.Linq.Enumerable.OrderBy%2A> . Bu işleçlerin çevirisinde, bir türün bağımsız değişkeninin kullanımı, bu türün tüm üyelerini belirtmeye eşdeğer olarak kabul edilir. Örneğin, aşağıdaki kod eşdeğerdir:

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a>Equatable/karşılaştırılabilir bağımsız değişkenler

Aşağıdaki yöntemlerin uygulanmasında bağımsız değişkenlerin eşitliği gereklidir:

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]*düz* bağımsız değişkenler için eşitlik ve karşılaştırmayı destekler, ancak dizileri olan veya içeren bağımsız değişkenler için değildir. Düz bir bağımsız değişken, bir SQL satırına eşlenebilir bir türdür. Statik olarak belirlenebileceği bir veya daha fazla varlık türünün projeksiyonu düz bir bağımsız değişken olarak kabul edilir.

Düz bağımsız değişkenlerin örnekleri aşağıda verilmiştir:

[!code-csharp[DLinqSQOTranslation#3](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

Aşağıda, düz olmayan (hiyerarşik) bağımsız değişkenlerin örnekleri verilmiştir:

[!code-csharp[DLinqSQOTranslation#4](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a>Visual Basic Işlev çevirisi

Visual Basic Derleyicisi tarafından kullanılan aşağıdaki yardımcı işlevler, karşılık gelen SQL işleçleri ve işlevlerine çevrilir:

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

Dönüştürme yöntemleri:

|||||
|-|-|-|-|
|ToBoolean|ToSByte|ToByte|ToChar|
|ToCharArrayRankOne|ToDate|ToDecimal|ToDouble|
|ToInteger|ToUInteger|ToLong|ToULong|
|ToShort|ToUShort|ToSingle|ToString|

## <a name="inheritance-support"></a>Devralma Desteği

### <a name="inheritance-mapping-restrictions"></a>Devralma eşleme kısıtlamaları

Daha fazla bilgi için bkz. [nasıl yapılır: harita devralma hiyerarşileri](how-to-map-inheritance-hierarchies.md).

### <a name="inheritance-in-queries"></a>Sorgularda devralma

C# yayınları yalnızca projeksiyde desteklenir. Başka bir yerde kullanılan yayınlar çevrilmez ve yok sayılır. SQL işlev adlarından de, SQL aslında yalnızca ortak dil çalışma zamanının (CLR) eşdeğerini uygular <xref:System.Convert> . Diğer bir deyişle, SQL bir tür değerini başka bir türe değiştirebilir. Başka bir türden farklı bitleri yeniden yorumlama kavramı olmadığından, CLR cast ' ın eşdeğeri yoktur. Bunun nedeni, C# cast işlevinin yalnızca yerel olarak çalışmasına neden olur. Bu uzak değildir.

İşleçleri, `is` ve `as` ve yöntemi işleçle `GetType` kısıtlanmaz `Select` . Bunlar aynı zamanda diğer sorgu işleçleri içinde de kullanılabilir.

## <a name="sql-server-2008-support"></a>SQL Server 2008 desteği

.NET Framework 3,5 SP1 ile başlayarak LINQ to SQL, SQL Server 2008 ile tanıtılan yeni tarih ve saat türleriyle eşlemeyi destekler. Ancak, bu yeni türlere eşlenen değerlere karşı çalışırken kullanabileceğiniz LINQ to SQL sorgu işleçleri için bazı sınırlamalar vardır.

### <a name="unsupported-query-operators"></a>Desteklenmeyen sorgu Işleçleri

Aşağıdaki sorgu işleçleri, yeni SQL Server Tarih ve saat türleriyle eşlenen değerlerde desteklenmez: `DATETIME2` , `DATE` , `TIME` , ve `DATETIMEOFFSET` .

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

Bu SQL Server Tarih ve saat türleriyle eşleştirme hakkında daha fazla bilgi için bkz. [SQL-CLR tür eşleme](sql-clr-type-mapping.md).

## <a name="sql-server-2005-support"></a>SQL Server 2005 desteği

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , aşağıdaki SQL Server 2005 özelliklerini desteklemez:

- SQL CLR için yazılan saklı yordamlar.

- Kullanıcı tanımlı tür.

- XML sorgu özellikleri.

## <a name="sql-server-2000-support"></a>SQL Server 2000 desteği

Aşağıdaki SQL Server 2000 sınırlamaları (Microsoft SQL Server 2005 ile karşılaştırıldığında) desteği etkiler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .

### <a name="cross-apply-and-outer-apply-operators"></a>Çapraz uygulama ve dış uygulama Işleçleri

Bu işleçler SQL Server 2000 ' de kullanılamaz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uygun birleştirmelere göre değiştirmek için bir dizi yeniden yazmaya çalışır.

`Cross Apply` ve `Outer Apply` ilişki gezginlerini için oluşturulur. Bu tür yeniden yazar mümkün olan sorgu kümesi iyi tanımlanmamıştır. Bu nedenle, SQL Server 2000 için desteklenen minimum sorgu kümesi ilişki gezintisi içermeyen bir kümesidir.

### <a name="text--ntext"></a>Text/ntext

Veri türleri `text`  /  `ntext` `varchar(max)`  /  `nvarchar(max)` , Microsoft SQL Server 2005 tarafından desteklenen belirli sorgu işlemlerinde kullanılamaz.

Bu sınırlama için hiçbir çözüm yok. Özellikle, `Distinct()` veya sütunlarına eşlenen Üyeler içeren herhangi bir sonuç üzerinde kullanamazsınız `text` `ntext` .

### <a name="behavior-triggered-by-nested-queries"></a>Iç Içe geçmiş sorgular tarafından tetiklenen davranış

SQL Server 2000 (SP4) bağlayıcı, iç içe geçmiş sorgular tarafından tetiklenen bazı idosynyenilere sahiptir. Bu deyimi tetikleyen SQL sorguları kümesi iyi tanımlanmamıştır. Bu nedenle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL Server özel durumlara neden olabilecek sorgu kümesini tanımlayamazsınız.

### <a name="skip-and-take-operators"></a>Atla ve Al Işleçleri

<xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 ' de sorgularda kullanıldıkları bazı sınırlamalar vardır. Daha fazla bilgi için bkz. [sorun giderme](troubleshooting.md)içindeki "SQL Server 2000 'de özel durumları atla ve al" girişi.

## <a name="object-materialization"></a>Nesne Gerçekleştirme

Materialization bir veya daha fazla SQL sorgusu tarafından döndürülen satırlardan CLR nesneleri oluşturur.

- Aşağıdaki çağrılar, materialization 'ın bir parçası olarak *yerel olarak yürütülür* :

  - Oluşturucular

  - `ToString` projeksiylerdeki Yöntemler

  - Yansıtmalarda tür atamaları

- Yöntemi izleyen Yöntemler <xref:System.Linq.Enumerable.AsEnumerable%2A> *yerel olarak yürütülür*. Bu yöntem, hemen yürütmeye neden olmaz.

- Bir `struct` Sorgu sonucunun dönüş türü olarak veya sonuç türünün üyesi olarak ' i kullanabilirsiniz. Varlıkların sınıflar olması gerekir. Anonim türler sınıf örnekleri olarak gerçekleştirilir, ancak adlandırılmış yapılar (varlık olmayan) projeksiyonde kullanılabilir.

- Bir sorgu sonucunun dönüş türünün bir üyesi türünde olabilir <xref:System.Linq.IQueryable%601> . Yerel bir koleksiyon olarak gerçekleştirilmiş olur.

- Aşağıdaki yöntemler, yöntemlerin uygulandığı dizinin *hemen* bir şekilde oluşturulmasına neden olur:

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](reference.md)
- [Dizideki Öğeleri Döndürme veya Atlama](return-or-skip-elements-in-a-sequence.md)
- [İki Diziyi Birleştirme](concatenate-two-sequences.md)
- [İki Dizi Arasındaki Küme Farkını Döndürme](return-the-set-difference-between-two-sequences.md)
- [İki Dizinin Küme Kesişimini Döndürme](return-the-set-intersection-of-two-sequences.md)
- [İki Dizinin Küme Birleşimini Döndürme](return-the-set-union-of-two-sequences.md)
