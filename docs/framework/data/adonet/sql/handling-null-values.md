---
title: Null Değerleri İşleme
description: SQL Server için .NET Framework Veri Sağlayıcısı null işleme hakkında bilgi edinin ve null ve SqlBoolean, üç değerli mantığı ve null değerler atamayı okuyun.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 2dda65f605ea9de616f01d6e52eb4e0e5def4db7
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982524"
---
# <a name="handling-null-values"></a><span data-ttu-id="3645a-103">Null Değerleri İşleme</span><span class="sxs-lookup"><span data-stu-id="3645a-103">Handling Null Values</span></span>

<span data-ttu-id="3645a-104">Bir sütundaki değer bilinmiyorsa veya eksik olduğunda, ilişkisel veritabanında null değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3645a-104">A null value in a relational database is used when the value in a column is unknown or missing.</span></span> <span data-ttu-id="3645a-105">Null, boş bir dize (karakter veya tarih saat veri türleri için) veya sıfır değeri (sayısal veri türleri için) değil.</span><span class="sxs-lookup"><span data-stu-id="3645a-105">A null is neither an empty string (for character or datetime data types) nor a zero value (for numeric data types).</span></span> <span data-ttu-id="3645a-106">ANSI SQL-92 belirtimi, tüm null değerleri tutarlı bir şekilde işlenebilmesi için null değeri tüm veri türleri için aynı olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3645a-106">The ANSI SQL-92 specification states that a null must be the same for all data types, so that all nulls are handled consistently.</span></span> <span data-ttu-id="3645a-107"><xref:System.Data.SqlTypes>Ad alanı, arabirimini uygulayarak null semantikler sağlar <xref:System.Data.SqlTypes.INullable> .</span><span class="sxs-lookup"><span data-stu-id="3645a-107">The <xref:System.Data.SqlTypes> namespace provides null semantics by implementing the <xref:System.Data.SqlTypes.INullable> interface.</span></span> <span data-ttu-id="3645a-108">İçindeki veri türlerinin her biri <xref:System.Data.SqlTypes> kendi `IsNull` özelliğine sahiptir ve `Null` Bu veri türü örneğine atanabilecek bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="3645a-108">Each of the data types in <xref:System.Data.SqlTypes> has its own `IsNull` property and a `Null` value that can be assigned to an instance of that data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3645a-109">.NET Framework sürüm 2,0,, programcıların bir değer türünü temel alınan türün tüm değerlerini temsil edecek şekilde genişletmesine izin veren null yapılabilir değer türleri için destek sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="3645a-109">The .NET Framework version 2.0 introduced support for nullable value types, which allow programmers to extend a value type to represent all values of the underlying type.</span></span> <span data-ttu-id="3645a-110">Bu CLR null yapılabilir değer türleri yapının bir örneğini temsil eder <xref:System.Nullable> .</span><span class="sxs-lookup"><span data-stu-id="3645a-110">These CLR nullable value types represent an instance of the <xref:System.Nullable> structure.</span></span> <span data-ttu-id="3645a-111">Bu özellik, özellikle değer türleri kutulanmış ve kutulandığında, nesne türleriyle gelişmiş uyumluluk sağlayan yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="3645a-111">This capability is especially useful when value types are boxed and unboxed, providing enhanced compatibility with object types.</span></span> <span data-ttu-id="3645a-112">ANSI SQL null değeri bir `null` başvuru (veya Visual Basic) ile aynı şekilde davranmadığından, clr null yapılabilir değer türleri veritabanı boş değerlerini depolamak için tasarlanmamıştır `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="3645a-112">CLR nullable value types are not intended for storage of database nulls because an ANSI SQL null does not behave the same way as a `null` reference (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="3645a-113">Veritabanı ANSI SQL null değerleriyle çalışma için yerine null değerleri kullanın <xref:System.Data.SqlTypes> <xref:System.Nullable> .</span><span class="sxs-lookup"><span data-stu-id="3645a-113">For working with database ANSI SQL null values, use <xref:System.Data.SqlTypes> nulls rather than <xref:System.Nullable>.</span></span> <span data-ttu-id="3645a-114">Visual Basic ' de CLR değeri null yapılabilir türleriyle çalışma hakkında daha fazla bilgi için bkz. [Nullable değer türlerini](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)görüntüle ve C# için bkz. [Nullable değer türleri](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="3645a-114">For more information on working with CLR value nullable types in Visual Basic see [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), and for C# see [Nullable value types](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).</span></span>  
  
## <a name="nulls-and-three-valued-logic"></a><span data-ttu-id="3645a-115">Null değerler ve Three-Valued mantığı</span><span class="sxs-lookup"><span data-stu-id="3645a-115">Nulls and Three-Valued Logic</span></span>  

 <span data-ttu-id="3645a-116">Sütun tanımlarında null değerlere izin verilmesi, uygulamanıza üç değerli mantık getirir.</span><span class="sxs-lookup"><span data-stu-id="3645a-116">Allowing null values in column definitions introduces three-valued logic into your application.</span></span> <span data-ttu-id="3645a-117">Karşılaştırma, üç koşuldan birini değerlendirebilir:</span><span class="sxs-lookup"><span data-stu-id="3645a-117">A comparison can evaluate to one of three conditions:</span></span>  
  
- <span data-ttu-id="3645a-118">Doğru</span><span class="sxs-lookup"><span data-stu-id="3645a-118">True</span></span>  
  
- <span data-ttu-id="3645a-119">Yanlış</span><span class="sxs-lookup"><span data-stu-id="3645a-119">False</span></span>  
  
- <span data-ttu-id="3645a-120">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="3645a-120">Unknown</span></span>  
  
 <span data-ttu-id="3645a-121">Null değeri bilinmiyor olarak değerlendirildiğinden, birbirleriyle karşılaştırılan iki null değer eşit kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="3645a-121">Because null is considered to be unknown, two null values compared to each other are not considered to be equal.</span></span> <span data-ttu-id="3645a-122">Aritmetik işleçleri kullanan ifadelerde, İşlenenlerden herhangi biri null ise sonuç de null olur.</span><span class="sxs-lookup"><span data-stu-id="3645a-122">In expressions using arithmetic operators, if any of the operands is null, the result is null as well.</span></span>  
  
## <a name="nulls-and-sqlboolean"></a><span data-ttu-id="3645a-123">Null değerler ve SqlBoolean</span><span class="sxs-lookup"><span data-stu-id="3645a-123">Nulls and SqlBoolean</span></span>  

 <span data-ttu-id="3645a-124">Aralarında karşılaştırma <xref:System.Data.SqlTypes> , döndürür <xref:System.Data.SqlTypes.SqlBoolean> .</span><span class="sxs-lookup"><span data-stu-id="3645a-124">Comparison between any <xref:System.Data.SqlTypes> will return a <xref:System.Data.SqlTypes.SqlBoolean>.</span></span> <span data-ttu-id="3645a-125">`IsNull`Her biri için işlevi `SqlType` bir döndürür <xref:System.Data.SqlTypes.SqlBoolean> ve null değerleri denetlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3645a-125">The `IsNull` function for each `SqlType` returns a <xref:System.Data.SqlTypes.SqlBoolean> and can be used to check for null values.</span></span> <span data-ttu-id="3645a-126">Aşağıdaki Truth tablolarında, ve, veya DEĞIL işleçlerinin bir null değer varlığı içinde nasıl çalıştığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3645a-126">The following truth tables show how the AND, OR, and NOT operators function in the presence of a null value.</span></span> <span data-ttu-id="3645a-127">(T = true, F = false, ve U = Unknown veya null.)</span><span class="sxs-lookup"><span data-stu-id="3645a-127">(T=true, F=false, and U=unknown, or null.)</span></span>  
  
 <span data-ttu-id="3645a-128">![Truth tablosu](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span><span class="sxs-lookup"><span data-stu-id="3645a-128">![Truth Table](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")</span></span>  
  
### <a name="understanding-the-ansi_nulls-option"></a><span data-ttu-id="3645a-129">ANSI_NULLS seçeneğini anlama</span><span class="sxs-lookup"><span data-stu-id="3645a-129">Understanding the ANSI_NULLS Option</span></span>  

 <span data-ttu-id="3645a-130"><xref:System.Data.SqlTypes> SQL Server ' de ANSI_NULLS seçeneğinin ayarlandığı anlamlarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3645a-130"><xref:System.Data.SqlTypes> provides the same semantics as when the ANSI_NULLS option is set on in SQL Server.</span></span> <span data-ttu-id="3645a-131">Tüm aritmetik işleçler (+,-, \* ,/,%), bit düzeyinde işleçler (~, &, \| ) ve çoğu işlev, özellik hariç, işlenen veya bağımsız değişkenlerden biri null ise null döndürür `IsNull` .</span><span class="sxs-lookup"><span data-stu-id="3645a-131">All arithmetic operators (+, -, \*, /, %), bitwise operators (~, &, \|), and most functions return null if any of the operands or arguments is null, except for the property `IsNull`.</span></span>  
  
 <span data-ttu-id="3645a-132">ANSI SQL-92 standardı, WHERE yan tümcesinde *ColumnName* = null değerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3645a-132">The ANSI SQL-92 standard does not support *columnName* = NULL in a WHERE clause.</span></span> <span data-ttu-id="3645a-133">SQL Server, ANSI_NULLS seçeneği veritabanında hem varsayılan null değer alabilme durumunu hem de null değerlere karşı karşılaştırmalar değerlendirmesini denetler.</span><span class="sxs-lookup"><span data-stu-id="3645a-133">In SQL Server, the ANSI_NULLS option controls both default nullability in the database and evaluation of comparisons against null values.</span></span> <span data-ttu-id="3645a-134">ANSI_NULLS açıksa (varsayılan), null değerleri için test edilirken deyimlerde NULL işleci kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3645a-134">If ANSI_NULLS is turned on (the default), the IS NULL operator must be used in expressions when testing for null values.</span></span> <span data-ttu-id="3645a-135">Örneğin, ANSI_NULLS olduğunda aşağıdaki karşılaştırma her zaman bilinmiyor olarak verir:</span><span class="sxs-lookup"><span data-stu-id="3645a-135">For example, the following comparison always yields unknown when ANSI_NULLS is on:</span></span>  
  
```sql
colname > NULL  
```  
  
 <span data-ttu-id="3645a-136">Null değer içeren bir değişkene karşılaştırma de bilinmeyen bir değer verir:</span><span class="sxs-lookup"><span data-stu-id="3645a-136">Comparison to a variable containing a null value also yields unknown:</span></span>  
  
```sql
colname > @MyVariable  
```  
  
 <span data-ttu-id="3645a-137">Null değer için test etmek üzere null veya NULL koşulunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="3645a-137">Use the IS NULL or IS NOT NULL predicate to test for a null value.</span></span> <span data-ttu-id="3645a-138">Burada WHERE yan tümcesine karmaşıklık eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3645a-138">This can add complexity to the WHERE clause.</span></span> <span data-ttu-id="3645a-139">Örneğin, AdventureWorks Customer tablosundaki TerritoryID sütunu null değerlere izin verir.</span><span class="sxs-lookup"><span data-stu-id="3645a-139">For example, the TerritoryID column in the AdventureWorks Customer table allows null values.</span></span> <span data-ttu-id="3645a-140">Bir SELECT ifadesinin diğer kullanıcılara ek olarak null değerler için test olması gerekiyorsa, bir IS NULL koşulu içermelidir:</span><span class="sxs-lookup"><span data-stu-id="3645a-140">If a SELECT statement is to test for null values in addition to others, it must include an IS NULL predicate:</span></span>  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 <span data-ttu-id="3645a-141">SQL Server ANSI_NULLS devre dışı bırakırsanız, null ile karşılaştırmak için eşitlik işlecini kullanan ifadeler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3645a-141">If you set ANSI_NULLS off in SQL Server, you can create expressions that use the equality operator to compare to null.</span></span> <span data-ttu-id="3645a-142">Ancak, bu bağlantı için farklı bağlantıların null seçeneklerini ayarlamamasını önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3645a-142">However, you can't prevent different connections from setting null options for that connection.</span></span> <span data-ttu-id="3645a-143">Bir bağlantı için ANSI_NULLS ayarlarından bağımsız olarak, null değerler test etmek için using NULL değeri her zaman işe yarar.</span><span class="sxs-lookup"><span data-stu-id="3645a-143">Using IS NULL to test for null values always works, regardless of the ANSI_NULLS settings for a connection.</span></span>  
  
 <span data-ttu-id="3645a-144">ANSI_NULLS OFF ayarı, içinde `DataSet` null değerleri işlemek için her zaman ANSI SQL-92 standardını izleyen bir içinde desteklenmez <xref:System.Data.SqlTypes> .</span><span class="sxs-lookup"><span data-stu-id="3645a-144">Setting ANSI_NULLS off is not supported in a `DataSet`, which always follows the ANSI SQL-92 standard for handling null values in <xref:System.Data.SqlTypes>.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="3645a-145">Null değerler atama</span><span class="sxs-lookup"><span data-stu-id="3645a-145">Assigning Null Values</span></span>  

 <span data-ttu-id="3645a-146">Null değerler özeldir ve depolama ve atama semantiği farklı tür sistemleri ve depolama sistemleri arasında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="3645a-146">Null values are special, and their storage and assignment semantics differ across different type systems and storage systems.</span></span> <span data-ttu-id="3645a-147">`Dataset`, Farklı tür ve depolama sistemleriyle kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3645a-147">A `Dataset` is designed to be used with different type and storage systems.</span></span>  
  
 <span data-ttu-id="3645a-148">Bu bölüm <xref:System.Data.DataColumn> <xref:System.Data.DataRow> , farklı tür sistemlerinde bir içindeki öğesine null değerler atamaya yönelik null semantiğini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="3645a-148">This section describes the null semantics for assigning null values to a <xref:System.Data.DataColumn> in a <xref:System.Data.DataRow> across the different type systems.</span></span>  
  
 `DBNull.Value`  
 <span data-ttu-id="3645a-149">Bu atama herhangi bir tür için geçerlidir `DataColumn` .</span><span class="sxs-lookup"><span data-stu-id="3645a-149">This assignment is valid for a `DataColumn` of any type.</span></span> <span data-ttu-id="3645a-150">Tür uygularsa `INullable` , `DBNull.Value` uygun kesin türü belirtilmiş null değere zorlanır.</span><span class="sxs-lookup"><span data-stu-id="3645a-150">If the type implements `INullable`, `DBNull.Value` is coerced into the appropriate strongly typed Null value.</span></span>  
  
 `SqlType.Null`  
 <span data-ttu-id="3645a-151">Tüm <xref:System.Data.SqlTypes> veri türleri uygular `INullable` .</span><span class="sxs-lookup"><span data-stu-id="3645a-151">All <xref:System.Data.SqlTypes> data types implement `INullable`.</span></span> <span data-ttu-id="3645a-152">Türü kesin belirlenmiş null değer, örtük atama işleçleri kullanılarak sütunun veri türüne dönüştürülebiliyorsanız, atama devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="3645a-152">If the strongly typed null value can be converted into the column's data type using implicit cast operators, the assignment should go through.</span></span> <span data-ttu-id="3645a-153">Aksi takdirde geçersiz bir tür dönüştürme özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3645a-153">Otherwise an invalid cast exception is thrown.</span></span>  
  
 `null`  
 <span data-ttu-id="3645a-154">' Null ' verili veri türü için geçerli bir değer ise `DataColumn` , ilgili `DbNull.Value` veya `Null` `INullable` türü () ile ilişkili olan veya ilişkilendirilen `SqlType.Null`</span><span class="sxs-lookup"><span data-stu-id="3645a-154">If 'null' is a legal value for the given `DataColumn` data type, it is coerced into the appropriate `DbNull.Value` or `Null` associated with the `INullable` type (`SqlType.Null`)</span></span>  
  
 `derivedUdt.Null`  
 <span data-ttu-id="3645a-155">UDT sütunlarında, null değerler her zaman ile ilişkili türüne göre saklanır `DataColumn` .</span><span class="sxs-lookup"><span data-stu-id="3645a-155">For UDT columns, nulls are always stored based on the type associated with the `DataColumn`.</span></span> <span data-ttu-id="3645a-156">`DataColumn`Alt sınıfı yaparken uygulamayana BIR udt ile ilişkili BIR udt durumunu göz önünde bulundurun `INullable` .</span><span class="sxs-lookup"><span data-stu-id="3645a-156">Consider the case of a UDT associated with a `DataColumn` that does not implement `INullable` while its sub-class does.</span></span> <span data-ttu-id="3645a-157">Bu durumda, türetilmiş sınıfla ilişkili kesin olarak belirlenmiş null değeri atanırsa, `DbNull.Value` null depolama her zaman DataColumn 'ın veri türüyle tutarlı olduğundan türsüz olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="3645a-157">In this case, if a strongly typed null value associated with the derived class is assigned, it is stored as an untyped `DbNull.Value`, because null storage is always consistent with the DataColumn's data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3645a-158">`Nullable<T>`Veya <xref:System.Nullable> yapısı ' de şu anda desteklenmemektedir `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="3645a-158">The `Nullable<T>` or <xref:System.Nullable> structure is not currently supported in the `DataSet`.</span></span>  
  
### <a name="multiple-column-row-assignment"></a><span data-ttu-id="3645a-159">Birden çok sütun (satır) ataması</span><span class="sxs-lookup"><span data-stu-id="3645a-159">Multiple Column (Row) Assignment</span></span>  

 <span data-ttu-id="3645a-160">`DataTable.Add`, `DataTable.LoadDataRow` veya bir satıra eşlenmiş bir satırı kabul eden diğer API 'ler <xref:System.Data.DataRow.ItemArray%2A> , ' null ' değerini DataColumn 'ın varsayılan değerine eşleyin.</span><span class="sxs-lookup"><span data-stu-id="3645a-160">`DataTable.Add`, `DataTable.LoadDataRow`, or other APIs that accept an <xref:System.Data.DataRow.ItemArray%2A> that gets mapped to a row, map 'null' to the DataColumn's default value.</span></span> <span data-ttu-id="3645a-161">Dizideki bir nesne `DbNull.Value` veya türü kesin belirlenmiş karşılığı içeriyorsa, yukarıda açıklanan kurallar uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3645a-161">If an object in the array contains `DbNull.Value` or its strongly typed counterpart, the same rules as described above are applied.</span></span>  
  
 <span data-ttu-id="3645a-162">Ayrıca, aşağıdaki kurallar null atamalarının bir örneği için geçerlidir `DataRow.["columnName"]` :</span><span class="sxs-lookup"><span data-stu-id="3645a-162">In addition, the following rules apply for an instance of `DataRow.["columnName"]` null assignments:</span></span>  
  
1. <span data-ttu-id="3645a-163">*Varsayılan* değer, kesin belirlenmiş tür belirlenmiş null sütunlar hariç olmak üzere, kesin türü kesin belirlenmiş null `DbNull.Value` değer olan tüm içindir.</span><span class="sxs-lookup"><span data-stu-id="3645a-163">The *default* value is `DbNull.Value` for all except the strongly typed null columns where it is the appropriate strongly typed null value.</span></span>  
  
2. <span data-ttu-id="3645a-164">XML dosyalarına serileştirme sırasında null değerler hiçbir şekilde yazılmaz ("xsi: Nil" içinde olduğu gibi).</span><span class="sxs-lookup"><span data-stu-id="3645a-164">Null values are never written out during serialization to XML files (as in "xsi:nil").</span></span>  
  
3. <span data-ttu-id="3645a-165">Varsayılanlar dahil tüm null olmayan değerler, XML 'e serileştirilirken her zaman yazılır.</span><span class="sxs-lookup"><span data-stu-id="3645a-165">All non-null values, including defaults, are always written out while serializing to XML.</span></span> <span data-ttu-id="3645a-166">Bu, null bir değer (xsi: Nil) açık ve varsayılan değer örtük (XML 'de yoksa, bir doğrulama ayrıştırıcısı onu ilişkili bir XSD şemasından alabilir) olduğu XSD/XML semantiğinin aksine.</span><span class="sxs-lookup"><span data-stu-id="3645a-166">This is unlike XSD/XML semantics where a null value (xsi:nil) is explicit and the default value is implicit (if not present in XML, a validating parser can get it from an associated XSD schema).</span></span> <span data-ttu-id="3645a-167">Bunun için ters değer true 'dur `DataTable` : null değeri örtük ve varsayılan değer açıktır.</span><span class="sxs-lookup"><span data-stu-id="3645a-167">The opposite is true for a `DataTable`: a null value is implicit and the default value is explicit.</span></span>  
  
4. <span data-ttu-id="3645a-168">XML girişinden okunan satırlar için eksik olan tüm sütun değerlerine NULL atanır.</span><span class="sxs-lookup"><span data-stu-id="3645a-168">All missing column values for rows read from XML input are assigned NULL.</span></span> <span data-ttu-id="3645a-169"><xref:System.Data.DataTable.NewRow%2A>Veya benzer yöntemler kullanılarak oluşturulan satırlara, DataColumn 'ın varsayılan değeri atanır.</span><span class="sxs-lookup"><span data-stu-id="3645a-169">Rows created using <xref:System.Data.DataTable.NewRow%2A> or similar methods are assigned the DataColumn's default value.</span></span>  
  
5. <span data-ttu-id="3645a-170"><xref:System.Data.DataRow.IsNull%2A>Yöntemi hem hem `true` de için `DbNull.Value` döndürür `INullable.Null` .</span><span class="sxs-lookup"><span data-stu-id="3645a-170">The <xref:System.Data.DataRow.IsNull%2A> method returns `true` for both `DbNull.Value` and `INullable.Null`.</span></span>  
  
## <a name="assigning-null-values"></a><span data-ttu-id="3645a-171">Null değerler atama</span><span class="sxs-lookup"><span data-stu-id="3645a-171">Assigning Null Values</span></span>  

 <span data-ttu-id="3645a-172">Herhangi bir örnek için varsayılan değer <xref:System.Data.SqlTypes> null.</span><span class="sxs-lookup"><span data-stu-id="3645a-172">The default value for any <xref:System.Data.SqlTypes> instance is null.</span></span>  
  
 <span data-ttu-id="3645a-173">İçindeki null değerlere <xref:System.Data.SqlTypes> tür özgüdür ve gibi tek bir değerle temsil edilemez `DbNull` .</span><span class="sxs-lookup"><span data-stu-id="3645a-173">Nulls in <xref:System.Data.SqlTypes> are type-specific and cannot be represented by a single value, such as `DbNull`.</span></span> <span data-ttu-id="3645a-174">Null değerleri `IsNull` denetlemek için özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3645a-174">Use the `IsNull` property to check for nulls.</span></span>  
  
 <span data-ttu-id="3645a-175"><xref:System.Data.DataColumn>Aşağıdaki kod örneğinde gösterildiği gibi, null değerler öğesine atanabilir.</span><span class="sxs-lookup"><span data-stu-id="3645a-175">Null values can be assigned to a <xref:System.Data.DataColumn> as shown in the following code example.</span></span> <span data-ttu-id="3645a-176">`SqlTypes`Özel durum tetiklemeden, değişkenlere doğrudan null değerler atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3645a-176">You can directly assign null values to `SqlTypes` variables without triggering an exception.</span></span>  
  
### <a name="example"></a><span data-ttu-id="3645a-177">Örnek</span><span class="sxs-lookup"><span data-stu-id="3645a-177">Example</span></span>  

 <span data-ttu-id="3645a-178">Aşağıdaki kod örneği, <xref:System.Data.DataTable> ve şeklinde tanımlanmış iki sütunlu bir ile <xref:System.Data.SqlTypes.SqlInt32> oluşturur <xref:System.Data.SqlTypes.SqlString> .</span><span class="sxs-lookup"><span data-stu-id="3645a-178">The following code example creates a <xref:System.Data.DataTable> with two columns defined as <xref:System.Data.SqlTypes.SqlInt32> and <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="3645a-179">Kod, bir dizi null değeri olan bilinen değerlerin bir satırını ekler ve sonra, <xref:System.Data.DataTable> değerlerini değişkenlere atayarak ve çıktıyı konsol penceresinde görüntüleyerek ' de dolaşır.</span><span class="sxs-lookup"><span data-stu-id="3645a-179">The code adds one row of known values, one row of null values and then iterates through the <xref:System.Data.DataTable>, assigning the values to variables and displaying the output in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 <span data-ttu-id="3645a-180">Bu örnek aşağıdaki sonuçları görüntüler:</span><span class="sxs-lookup"><span data-stu-id="3645a-180">This example displays the following results:</span></span>  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a><span data-ttu-id="3645a-181">Null değerleri SqlTypes ve CLR türleriyle karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="3645a-181">Comparing Null Values with SqlTypes and CLR Types</span></span>  

 <span data-ttu-id="3645a-182">Null değerleri karşılaştırırken, `Equals` YÖNTEMIN clr türleriyle çalışma yöntemiyle karşılaştırıldığında ' de null değerleri değerlendirme şekli arasındaki farkı anlamak önemlidir <xref:System.Data.SqlTypes> .</span><span class="sxs-lookup"><span data-stu-id="3645a-182">When comparing null values, it is important to understand the difference between the way the `Equals` method evaluates null values in <xref:System.Data.SqlTypes> as compared with the way it works with CLR types.</span></span> <span data-ttu-id="3645a-183">Tüm <xref:System.Data.SqlTypes> `Equals` Yöntemler null değerlerini değerlendirmek için veritabanı semantiğini kullanır: değerlerden biri veya her ikisi null ise, karşılaştırma null değerini verir.</span><span class="sxs-lookup"><span data-stu-id="3645a-183">All of the <xref:System.Data.SqlTypes>`Equals` methods use database semantics for evaluating null values: if either or both of the values is null, the comparison yields null.</span></span> <span data-ttu-id="3645a-184">Öte yandan, `Equals` her ikisi de null ise, clr yönteminin ikisi üzerinde kullanılması <xref:System.Data.SqlTypes> true olur.</span><span class="sxs-lookup"><span data-stu-id="3645a-184">On the other hand, using the CLR `Equals` method on two <xref:System.Data.SqlTypes> will yield true if both are null.</span></span> <span data-ttu-id="3645a-185">Bu, CLR yöntemi gibi bir örnek yöntemi kullanma `String.Equals` ve statik/paylaşılan yöntemi kullanma arasındaki farkı yansıtır `SqlString.Equals` .</span><span class="sxs-lookup"><span data-stu-id="3645a-185">This reflects the difference between using an instance method such as the CLR `String.Equals` method, and using the static/shared method, `SqlString.Equals`.</span></span>  
  
 <span data-ttu-id="3645a-186">Aşağıdaki örnek, `SqlString.Equals` `String.Equals` her biri null değer çifti ve daha sonra boş dizeler çifti geçirildiğinde yöntemi ve yöntemi arasındaki sonuçların farkını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3645a-186">The following example demonstrates the difference in results between the `SqlString.Equals` method and the `String.Equals` method when each is passed a pair of null values and then a pair of empty strings.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 <span data-ttu-id="3645a-187">Kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3645a-187">The code produces the following output:</span></span>  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True
```  
  
## <a name="see-also"></a><span data-ttu-id="3645a-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3645a-188">See also</span></span>

- [<span data-ttu-id="3645a-189">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3645a-189">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="3645a-190">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3645a-190">ADO.NET Overview</span></span>](../ado-net-overview.md)
