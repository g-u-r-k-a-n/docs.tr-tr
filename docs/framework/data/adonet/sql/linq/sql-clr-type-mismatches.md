---
description: 'Hakkında daha fazla bilgi edinin: SQL-CLR tür uyuşmazlığı'
title: SQL-CLR Tür Uyumsuzlukları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 9a2e1d360fc2a54f401572e46d92654f2b9284db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803730"
---
# <a name="sql-clr-type-mismatches"></a>SQL-CLR Tür Uyumsuzlukları

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli ve SQL Server arasındaki çevirinin çoğunu otomatik hale getirir. Bununla birlikte, bazı durumlar tam çeviriyi önler. Bu anahtar, ortak dil çalışma zamanı (CLR) türleri ve SQL Server veritabanı türleri arasındaki uyuşmazlıkları aşağıdaki bölümlerde özetlenmektedir. [SQL-CLR türü eşlemesinde](sql-clr-type-mapping.md) ve [veri türlerinde ve işlevlerde](data-types-and-functions.md)belirli tür eşlemeleri ve işlev çevirisi hakkında daha fazla ayrıntı bulabilirsiniz.

## <a name="data-types"></a>Veri Türleri

CLR ve SQL Server arasında çeviri, bir sorgu veritabanına gönderilirken ve sonuçlar nesne modelinize geri gönderildiğinde oluşur. Örneğin, aşağıdaki Transact-SQL sorgusu iki değer dönüştürmesi gerektirir:

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

Sorgu SQL Server üzerinde yürütülmeden önce Transact-SQL parametresinin değeri belirtilmelidir. Bu örnekte, `id` <xref:System.Int32?displayProperty=nameWithType> `INT` veritabanının değerin ne olduğunu anlayabilmesi için önce parametre değeri bir CLR türünden SQL Server türüne çevrilmelidir. Ardından sonuçları almak için SQL Server `DateOfBirth` sütunu, `DATETIME` nesne modelinde kullanılmak üzere bir SQL Server türünden clr türüne çevrilmelidir <xref:System.DateTime?displayProperty=nameWithType> . Bu örnekte, CLR nesne modeli ve SQL Server veritabanındaki türler doğal eşlemelere sahiptir. Ancak, bu her zaman durum değildir.

### <a name="missing-counterparts"></a>Eksik karşılıkları

Aşağıdaki türlerin makul karşılıkları yoktur.

- CLR <xref:System> ad alanındaki uyuşmazlıklar:

  - **İşaretsiz tamsayılar**. Bu türler genellikle, taşmamak için daha büyük boyuttaki imzalı karşılıklarına eşlenir. Değişmez değerler, değere göre aynı veya daha küçük olan işaretli bir sayısal değere dönüştürülebilir.

  - **Boole**. Bu türler, bir bit veya daha büyük sayısal ya da dizeye eşlenebilir. Değişmez değer aynı değere değerlendirilen bir ifadeye eşleştirilebilir (örneğin, `1=1` SQL 'de, `True` CLS içinde için).

  - **TimeSpan**. Bu tür, iki değer arasındaki farkı temsil eder `DateTime` ve SQL Server karşılık gelmez `timestamp` . CLR, <xref:System.TimeSpan?displayProperty=nameWithType> bazı durumlarda SQL Server türü ile de eşleşmeyebilir `TIME` . SQL Server `TIME` türü yalnızca 24 saatten daha az pozitif değerler temsil etmek üzere tasarlanmıştır. CLR <xref:System.TimeSpan> 'de çok daha büyük bir Aralık vardır.

  > [!NOTE]
  > İçindeki SQL Server özel .NET Framework türleri <xref:System.Data.SqlTypes> Bu karşılaştırmaya dahil değildir.

- SQL Server uyuşmazlıkları:

  - **Sabit uzunlukta karakter türleri**. Transact-SQL, Unicode ve Unicode olmayan kategoriler arasında ayrım yapar ve her kategoride üç farklı türe sahiptir: sabit uzunluk `nchar` / `char` , değişken uzunluğu `nvarchar` / `varchar` ve daha büyük boyutlu `ntext` / `text` . Sabit uzunluklu karakter türleri, <xref:System.Char?displayProperty=nameWithType> karakterleri almak IÇIN clr türü ile eşleştirilebilir, ancak dönüştürmelerde ve davranıştaki aynı türe karşılık gelmiyor.

  - **Bit**. `bit`Etki alanı aynı sayıda değere sahip olsa da `Nullable<Boolean>` , ikisi farklı türlerdir. `Bit`değerlerini alır `1` ve `0` yerine `true` / `false` Boolean ifadelerine eşdeğer olarak kullanılamaz.

  - **Zaman damgası**. CLR türünden farklı olarak <xref:System.TimeSpan?displayProperty=nameWithType> SQL Server türü, `TIMESTAMP` her bir güncelleştirme için benzersiz olan veritabanı tarafından oluşturulan 8 baytlık bir sayıyı temsil eder ve değerler arasındaki farka göre değildir <xref:System.DateTime> .

  - **Para** ve küçük **para**. Bu türler, ile eşleştirilir <xref:System.Decimal> ancak temelde farklı türlerdir ve sunucu tabanlı işlevlere ve Dönüştürmelere göre değerlendirilir.

### <a name="multiple-mappings"></a>Birden çok eşleme

Bir veya daha fazla CLR veri türüyle eşleyebileceğiniz pek çok SQL Server veri türü vardır. Bir veya daha fazla SQL Server türüne eşleyebileceğiniz birçok CLR türü de vardır. Bir eşlemenin LINQ to SQL tarafından desteklenmesine rağmen, CLR ve SQL Server arasında eşlenen iki türün duyarlık, Aralık ve semantiklerde kusursuz bir eşleşme olduğu anlamına gelmez. Bazı eşlemeler bu boyutların herhangi birinde veya tümünde farkları içerebilir. [SQL-CLR tür eşlemesinde](sql-clr-type-mapping.md)çeşitli eşleme olanakları için bu olası farklılıklar hakkındaki ayrıntıları bulabilirsiniz.

### <a name="user-defined-types"></a>Kullanıcı tanımlı türler

Kullanıcı tanımlı CLR türleri, tür sistem boşluğunu köprülemek için tasarlanmıştır. Bununla birlikte, tür sürümü oluşturma hakkında ilginç sorunlar ortaya alırlar. İstemcideki sürümde bir değişiklik, veritabanı sunucusunda depolanan türdeki bir değişiklik ile eşleşmeyebilir. Böyle bir değişiklik, tür semantiğinin eşleşmediği ve sürüm boşluğunun görünür olma olasılığı olan başka tür uyuşmazlığına neden olur. Devralma hiyerarşileri birbirini izleyen sürümlerde yeniden düzenlenmiş, daha karmaşıklıklar oluşur.

## <a name="expression-semantics"></a>İfade semantikleri

CLR ve veritabanı türleri arasında ikili uyumsuzluğa ek olarak, ifadeler uyuşmazlığa karmaşıklık ekler. İşleç semantiğinin, işlev semantiğinin, örtük tür dönüştürmenin ve öncelik kurallarının uyuşmazlıkları göz önünde bulundurulmalıdır.

Aşağıdaki alt bölümlerde benzer ifadeler arasındaki uyuşmazlık gösterilmektedir. Belirli bir CLR ifadesine anlamsal olarak eşdeğer olan SQL ifadeleri oluşturmak mümkün olabilir. Ancak, benzer ifadeler arasındaki anlam farklılıklarının bir CLR kullanıcısına açık olup olmadığını ve bu nedenle anlamsal denklik için gereken değişikliklerin amaçlanıp düşünülmeyeceğini net değildir. Bir ifade bir değer kümesi için değerlendirildiğinde bu özellikle kritik bir sorundur. Farkın görünürlüğü verilere bağlı olabilir ve kodlama ve hata ayıklama sırasında belirlenmesi zor olabilir.

### <a name="null-semantics"></a>Null Semantikler

SQL ifadeleri, Boole ifadeleri için üç değerli mantığı sağlar. Sonuç doğru, yanlış veya null olabilir. Buna karşılık, CLR null değerleri içeren karşılaştırmalar için iki değerli Boole sonucu belirtir. Aşağıdaki kodu inceleyin:

[!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
[!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]

```sql
-- Assume col1 and col2 are integer columns with null values.
-- Assume that ANSI null behavior has not been explicitly
--  turned off.
Select …
From …
Where col1 = col2
-- Evaluates to null, not true and the corresponding row is not
--   selected.
-- To obtain matching behavior (i -> col1, j -> col2) change
--   the query to the following:
Select …
From …
Where
    col1 = col2
or (col1 is null and col2 is null)
-- (Visual Basic 'Nothing'.)
```

İki değerli sonuçların varsayımıyla ilgili benzer bir sorun oluşur.

[!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
[!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]

```sql
-- Assume col1 and col2 are nullable columns.
-- Assume that ANSI null behavior has not been explicitly
--   turned off.
Select …
From …
Where
    col1 = col2
or col1 != col2
-- Visual Basic: col1 <> col2.

-- Excludes the case where the boolean expression evaluates
--   to null. Therefore the where clause does not always
--   evaluate to true.
```

Önceki durumda, SQL oluşturma ile eşdeğer bir davranış edinebilirsiniz, ancak çeviri amacınız doğru şekilde yansıtmayabilir.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]`null`SQL 'de C# veya Visual Basic `nothing` karşılaştırma semantiğini uygulamaz. Karşılaştırma işleçleri, sözdizimsel olarak SQL eşdeğerlerine çevrilir. Semantik, sunucu veya bağlantı ayarları tarafından tanımlanan SQL semantiğini yansıtır. İki null değer, varsayılan SQL Server ayarları altında eşit olarak değerlendirilir (ancak semantiğini değiştirmek için ayarları değiştirebilirsiniz). Ne olursa olsun, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu çevirisi 'nde sunucu ayarlarını dikkate almaz.

Değişmez değer `null` () ile karşılaştırma `nothing` uygun SQL sürümüne ( `is null` veya `is not null` ) çevrilir.

`null` `nothing` Harmanlama içindeki () değeri SQL Server tarafından tanımlanır; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] harmanlamayı değiştirmez.

### <a name="type-conversion-and-promotion"></a>Tür dönüştürme ve yükseltme

SQL, İfadelerdeki zengin bir örtük dönüştürme kümesini destekler. C# içindeki benzer ifadeler açık bir tür dönüştürme gerektirir. Örneğin:

- `Nvarchar` ve `DateTime` türleri herhangi bir açık yayını olmadan SQL 'de karşılaştırılabilir; C# açık dönüştürme gerektirir.

- `Decimal` örtük olarak SQL 'e dönüştürülür `DateTime` . C# örtük dönüştürmeye izin vermez.

Benzer şekilde, temel alınan türler farklı olduğundan Transact-SQL içindeki tür önceliği C# dilinde farklılık gösterir. Aslında, öncelik listeleri arasında şifresiz bir alt küme/üst küme ilişkisi yoktur. Örneğin, bir ile karşılaştırmak `nvarchar` `varchar` ifadenin örtük dönüştürmesine neden olur `varchar` `nvarchar` . CLR eşdeğer bir yükseltme sağlamaz.

Basit durumlarda bu farklılıklar, CLR deyimlerinin karşılık gelen bir SQL ifadesi için gereksiz olmasına neden olur. Daha da önemlisi, bir SQL ifadesinin ara sonuçları, C# dilinde doğru karşılığı olmayan bir türe örtülü olarak yükseltilebilir ve tam tersi de geçerlidir. Genel, test, hata ayıklama ve bu ifadelerin doğrulanması kullanıcıya önemli bir yük ekler.

### <a name="collation"></a>Harmanlama

Transact-SQL, karakter dize türlerine ek açıklama olarak açık harmanlamaları destekler. Bu harmanlamalar, bazı karşılaştırmaların geçerliliğini tespit edilir. Örneğin, iki sütunu farklı açık harmanlamalarla karşılaştırmak bir hatadır. Çok Basitleştirilmiş CTS dize türü kullanımı bu tür hatalara neden olmaz. Aşağıdaki örneği inceleyin:

```sql
create table T2 (
    Col1 nvarchar(10),
    Col2      nvarchar(10) collate Latin_general_ci_as
)
```

[!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
[!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]

```sql
Select …
From …
Where Col1 = Col2
-- Error, collation conflict.
```

Aslında, harmanlama alt yan tümcesi Substitutable olmayan bir *kısıtlanmış tür* oluşturur.

Benzer şekilde, sıralama düzeni tür sistemleri genelinde önemli ölçüde farklı olabilir. Bu fark sonuçların sıralanmasını etkiler. <xref:System.Guid> lexicographic Order () tarafından tüm 16 baytlara göre sıralanır `IComparable()` , ancak T-SQL GUID 'leri şu sırayla karşılaştırır: düğüm (10-15), saat-SEQ (8-9), zaman-yüksek (6-7), zaman-Orta (4-5), saat-düşük (0-3). Bu sıralama SQL 7,0 ' de, NT tarafından üretilen GUID 'lerde bu tür bir Sekizli sıra olduğunda yapılır. Aynı düğüm kümesinde oluşturulan GUID 'Ler, zaman damgasına göre sıralı sırayla birlikte sağlanır. Yaklaşım ayrıca dizinler oluşturmak için de yararlıdır (rastgele IOs yerine ekleme ekler). Bu sipariş gizlilik sorunları nedeniyle Windows 'da daha sonra karıştırılırsa, ancak SQL 'in uyumluluk koruması gerekir. Bunun yerine bir geçici çözüm kullanılır <xref:System.Data.SqlTypes.SqlGuid> <xref:System.Guid> .

### <a name="operator-and-function-differences"></a>İşleç ve Işlev farklılıkları

Esas olarak karşılaştırılabilir operatörler ve işlevler, daha az farklı semantiklere sahiptir. Örneğin:

- C#, mantıksal işleçler ve, işlenen nesnelerin sözlü sırası temelinde kısa devre semantiğini belirtir `&&` `||` . Diğer taraftan SQL, küme tabanlı sorgulara yöneliktir ve bu nedenle, yürütme sırasına karar vermek için iyileştiricinin daha fazla özgürlüğü sağlar. Bazı etkileri şunlardır:

  - Anlamsal olarak eşdeğer çeviri şunları gerektirir " `CASE` ... `WHEN` … `THEN`"işleneni yürütmenin yeniden sıralanmasını önlemek için SQL 'de oluşturun.

  - `AND` / `OR` C# ifadesi birinci işlenenin değerlendirmesinin sonucuna bağlı olarak ikinci işleneni değerlendirmede kullanıyorsa, işleçlere gevşek çeviri beklenmeyen hatalara neden olabilir.

- `Round()` işlevin .NET Framework ve T-SQL içinde farklı anlamları vardır.

- Dizeler için başlangıç dizini, CLR 'de 0, SQL 'de 1 ' dir. Bu nedenle, dizini olan herhangi bir işlev Dizin çevirisine ihtiyaç duyuyor.

- CLR, kayan noktalı sayılar için mod ('% ') işlecini destekler, ancak SQL desteklemez.

- `Like`İşleci örtük dönüştürmeleri temel alarak otomatik aşırı yüklemeleri etkin bir şekilde alır. `Like`İşleci karakter dize türleri üzerinde çalışmak üzere tanımlansa da, sayısal türlerden veya türlerden örtük dönüştürme, `DateTime` Bu dize olmayan türlerin de aynı zamanda kullanılmasını sağlar `Like` . CTS 'de, karşılaştırılabilir örtük dönüştürmeler yok. Bu nedenle, ek aşırı yüklemeler gereklidir.

    > [!NOTE]
    > Bu `Like` işleç davranışı yalnızca C# için geçerlidir; Visual Basic `Like` anahtar sözcüğü değiştirilmez.

- Taşma her zaman SQL 'de işaretlendi, ancak wraparound kaçınmak için C# içinde (Visual Basic değil) açıkça belirtilmesi gerekiyor. C1 ve C2, C3 (güncelleştirme T kümesi C3 = C1 + C2) içinde depolanıyorsa, C1, C2 ve C3 tamsayı sütunları veriliyor.

    ```sql
    create table T3 (
        Col1      integer,
        Col2      integer
    )
    insert into T3 (col1, col2) values (2147483647, 5)
    -- Valid values: max integer value and 5.
    select * from T3 where col1 + col2 < 0
    -- Produces arithmetic overflow error.
    ```

[!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
[!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]

- SQL, .NET Framework Banker yuvarlama kullandığından, simetrik aritmetik yuvarlama gerçekleştirir. Daha fazla ayrıntı için bkz. Bilgi Bankası makalesi 196652.

- Varsayılan olarak, ortak yerel ayarlarda karakter dizesi karşılaştırmaları SQL 'de büyük/küçük harfe duyarlıdır. Visual Basic ve C# ' de, büyük/küçük harfe duyarlıdır. Örneğin, `s == "Food"` ( `s = "Food"` Visual Basic) ve `s == "Food"` ise farklı sonuçlar verebilir `s` `food` .

    ```sql
    -- Assume default US-English locale (case insensitive).
    create table T4 (
        Col1      nvarchar (256)
    )
    insert into T4 values (‘Food’)
    insert into T4 values (‘FOOD’)
    select * from T4 where Col1 = ‘food’
    -- Both the rows are returned because of case-insensitive matching.
    ```

[!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
[!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]

- SQL 'deki sabit uzunluklu karakter türü bağımsız değişkenlerine uygulanan operatörler/işlevler, CLR 'ye uygulanmış aynı işleçlere/işlevlere göre önemli ölçüde farklı semantiklerdir <xref:System.String?displayProperty=nameWithType> . Bu, türler hakkında bölümünde ele alınan eksik karşılığı sorununun bir uzantısı olarak da görüntülenebilir.

    ```sql
    create table T4 (
        Col1      nchar(4)
    )
    Insert into T5(Col1) values ('21');
    Insert into T5(Col1) values ('1021');
    Select * from T5 where Col1 like '%1'
    -- Only the second row with Col1 = '1021' is returned.
    -- Not the first row!
    ```

     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]

     Dize birleştirme ile benzer bir sorun oluşur.

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

Özet bölümünde, bir genişletilmiş çeviri CLR ifadeleri için gerekli olabilir ve SQL işlevselliğini göstermek için ek işleçler/işlevler gerekebilir.

### <a name="type-casting"></a>Tür atama

C# ve SQL 'de, kullanıcılar açık tür yayınları (ve) kullanarak ifadelerin varsayılan semantiğini geçersiz kılabilir `Cast` `Convert` . Ancak, bu özelliği sistem sınırları genelinde göstermek bir dilimon ma oluşturur. İstenen semantiğini sağlayan bir SQL cast, karşılık gelen bir C# türüne kolayca çevrilemez. Diğer taraftan, bir C# cast tür uyuşmazlıkları, eksik karşılıkları ve farklı tür önceliği hiyerarşileri nedeniyle doğrudan eşdeğer bir SQL türüne çevrilemez. Sistem uyuşmazlığını ortaya çıkaran ve ifadenin önemli kuvvetinin kaybolması arasında bir denge vardır.

Diğer durumlarda, bir ifadenin doğrulanması için her iki etki alanında tür atama gerekmeyebilir ve varsayılan olmayan bir eşlemenin ifadeye doğru bir şekilde uygulandığından emin olmak için gerekli olabilir.

```sql
-- Example from "Non-default Mapping" section extended
create table T5 (
    Col1      nvarchar(10),
    Col2      nvarchar(10)
)
Insert into T5(col1, col2) values (‘3’, ‘2’);
```

[!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
[!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]

```sql
Select *
From T5
Where Col1 + Col2 > 4
-- "Col1 + Col2" expr evaluates to '32'
```

## <a name="performance-issues"></a>Performans Sorunları

Bazı SQL Server CLR tür farklılıkları için hesaplama, CLR ve SQL Server tür sistemleri arasında geçiş yaparken performansın düşmesine neden olabilir. Performansı etkileyen senaryolara örnek olarak şunlar verilebilir:

- Mantıksal ve/veya işleçler için zorlanan değerlendirme sıralaması

- Koşul değerlendirmesi sırasını zorlamak için SQL oluşturmak, SQL iyileştiricinin yeteneğini kısıtlar.

- Tür dönüştürmeleri, bir CLR derleyicisi tarafından veya Object-Relational bir sorgu uygulamasıyla tanıtılıp, dizin kullanımını etkileyebilir.

     Örneğin,

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     İfadenin çevirisini göz önünde bulundurun `(s = SOME_STRING_CONSTANT)` .

    ```sql
    -- Corresponding part of SQL where clause
    Where …
    Col1 = SOME_STRING_CONSTANT
    -- This expression is of the form <varchar> = <nvarchar>.
    -- Hence SQL introduces a conversion from varchar to nvarchar,
    --   resulting in
    Where …
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT
    -- Cannot use the index for column Col1 for some implementations.
    ```

Anlamsal farklılıklara ek olarak, SQL Server ile CLR tür sistemleri arasında geçiş yaparken performansı etkilerini göz önünde bulundurmanız önemlidir. Büyük veri kümeleri için, bu performans sorunları bir uygulamanın dağıtılabilir olup olmadığını belirleyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](background-information.md)
